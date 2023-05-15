---
emoji: 🏹
title: digital mbti troubleShooting
date: '2023-05-15 17:16:00'
author: Crong
tags: React
categories: React
---

# mbti를 만들면서의 트러블슈팅 및 정리

## App.tsx

기존 route에서 해당하는 유형의 타입을 뽑아 url에 넣는 형식으로 해야 깔끔할꺼라 생각하여, path 설정을 바꿔보았다.

```typescript
// before
function App() {
  return (
    <Routes>
      <Route path="/" element={<Home />} />
      <Route path="/test" element={<HomeTest />} />
      <Route path="/mbti/quiz" element={<Quiz />} />
      <Route path="/mbti/results" element={<Results />} />
      <Route path="/*" element={<NotFound />} />
    </Routes>
  );
}

// after
function App() {
  return (
    <Routes>
      <Route path="/" element={<Home />} />
      <Route path="/test" element={<HomeTest />} />
      <Route path="/mbti/quiz" element={<Quiz />} />
      <Route path="/mbti/results/:mbtiType" element={<Results />} />
      <Route path="/*" element={<NotFound />} />
    </Routes>
  );
}
```

<br>

## Quiz.tsx

코드의 해당 로직에 필요한 result쪽의 데이터를 Quiz Component에서 불러오는 형식으로 진행해야 얼추 맞을꺼란 생각이 들었다. 기존의 로직에서는 코드를 배열에 저장하여, 최종결과를 계산하기 위해 논리적인 결과를 하지 않고, Result Component에서 해당 부분을 전부 해, 맞는 유형을 찾는 짓거리를 했었다. (결과만 빨리 보기 위해서.)

<br>

Result Page에선 이전 코드를 기반으로 조건부로 렌더링 된 함수내에서 호출하는 되었다. 이 조건부 함수 호출 조합은 함수가 필요할 때 항상 호출되도록 보장하지 못할수있었다. 코드를 전부 뜯어내고 나서야, 변경 사항을 수신해주는 Hooks를 사용하여 모든 질문에 답변했는지에 대해 확인하고, 상태를 true로 설정한 다음 3초 지연 후 결과 페이지로 이동할수있게 수정을 해줬다.

<br>

```typescript
// before
import etc...

export default function Quiz() {
  const [currentQuestion, setCurrentQuestion] = useState<number>(0);
  const [answers, setAnswers] = useState<number[]>([]);
  const navigate = useNavigate();

  const handleOptionClick = (optionIndex: number): void => {
    const newAnswers = [...answers];
    newAnswers[currentQuestion] = optionIndex;
    setAnswers(newAnswers);
    setCurrentQuestion(currentQuestion + 1);

    const selectedOption = QuizData[currentQuestion].options[optionIndex];
    console.log(`type: ${selectedOption.type}, point: ${selectedOption.point}`);
    console.log('answers:', answers);
  };

  const renderOptions = () => {
    const { options } = QuizData[currentQuestion];
    return options.map((option, index) => (
      <Button type="button" key={option.answer} onClick={() => handleOptionClick(index)}>
        {option.answer}
        <WrapperCheckBox>
          <CheckBox type="checkbox" />
        </WrapperCheckBox>
      </Button>
    ));
  };

  const renderQuestion = () => {
    const { question } = QuizData[currentQuestion];
    return (
      <>
        {/* <h2>{`Question ${currentQuestion + 1}`}</h2> */}
        <BigTest2>Q. {question}</BigTest2>
        <WrapperButton>{renderOptions()}</WrapperButton>
      </>
    );
  };

  const renderStageBar = () => {
    const stageBarItems = QuizData.map((data, index) => {
      const isAnswered = answers[index] !== undefined;
      const questionText = isAnswered ? data.question : `Question ${index + 1}`;

      return <StageBarItem key={data.id} isAnswered={isAnswered} title={questionText} />;
    });

    return <StageBar>{stageBarItems}</StageBar>;
  };

  const navigateToResult = () => {
    navigate('/mbti/results', {
      state: { quizData: QuizData, answers },
    });
  };

  const renderResult = () => {
    setTimeout(() => {
      navigateToResult();
    }, 3000);
    return (
      <LoadingContainer>
        <img src="https://dummyimage.com/600x400/000/fff&text=Loading..." alt="error" />
      </LoadingContainer>
    );
  };

  return (
    <Container>
      <QuestionText>/question process indicator</QuestionText>
      <Box>
        {renderStageBar()}
        {currentQuestion < QuizData.length ? renderQuestion() : renderResult()}
      </Box>
    </Container>
  );
}

// after
import etc...

export default function Quiz() {
    const [currentQuestion, setCurrentQuestion] = useState<number>(0);
    const [answers, setAnswers] = useState<number[]>([]);
    const [loading, setLoading] = useState<Boolean>(false);
    const navigate = useNavigate();

    const totalResults = useMemo(() => {
        const typeScores: Record<string, number> = {
            N: 0,
            A: 0,
            P: 0,
            C: 0,
            T: 0,
            W: 0,
            O: 0,
            F: 0,
        };
        QuizData.forEach((question: any, index: number) => {
            const answerIndex = answers[index];
            if (answerIndex !== undefined) {
                const { type, point, answer } = question.options[answerIndex];
                console.log(
                    `Question ${index}: ${answer} (${type}, ${point} points)`,
                );
                typeScores[type] += point;
            }
        });
        const mbtiType = [
            typeScores.N > typeScores.A ? 'N' : 'A',
            typeScores.P > typeScores.C ? 'P' : 'C',
            typeScores.T > typeScores.W ? 'T' : 'W',
            typeScores.O > typeScores.F ? 'O' : 'F',
        ].join('');
        const results = [{ type: mbtiType, score: 1 }];
        return results;
    }, [answers]);

    const handleOptionClick = (optionIndex: number): void => {
        const newAnswers = [...answers];
        newAnswers[currentQuestion] = optionIndex;
        setAnswers(newAnswers);
        setCurrentQuestion(currentQuestion + 1);

        const selectedOption = QuizData[currentQuestion].options[optionIndex];
        console.log(
            `type: ${selectedOption.type}, point: ${selectedOption.point}`,
        );
        console.log('answers:', answers);
    };

    const renderOptions = () => {
        const { options } = QuizData[currentQuestion];
        return options.map((option, index) => (
            <Button
                type="button"
                key={option.answer}
                onClick={() => handleOptionClick(index)}
            >
                {option.answer}
                <WrapperCheckBox>
                    <CheckBox type="checkbox" />
                </WrapperCheckBox>
            </Button>
        ));
    };

    const renderQuestion = () => {
        const { question } = QuizData[currentQuestion];
        return (
            <>
                <BigTest2>Q. {question}</BigTest2>
                <WrapperButton>{renderOptions()}</WrapperButton>
            </>
        );
    };

    const renderStageBar = () => {
        const stageBarItems = QuizData.map((data, index) => {
            const isAnswered = answers[index] !== undefined;
            const questionText = isAnswered
                ? data.question
                : `Question ${index + 1}`;

            return (
                <StageBarItem
                    key={data.id}
                    isAnswered={isAnswered}
                    title={questionText}
                />
            );
        });

        return <StageBar>{stageBarItems}</StageBar>;
    };

    const renderResult = () => {
        if (loading) {
            return (
                <LoadingContainer>
                    <img
                        src="https://dummyimage.com/600x400/000/fff&text=Loading…"
                        alt="error"
                    />
                </LoadingContainer>
            );
        }
        return null;
    };

    // currentQuestion 변경될 때 결과 페이지로 이동하는 로직 추가
    useEffect(() => {
        if (currentQuestion >= QuizData.length) {
            setLoading(true);
            setTimeout(() => {
                const mbtiType = totalResults[0]?.type;
                if (mbtiType) {
                    navigate(`/mbti/results/${mbtiType}`);
                }
            }, 3000);
        }
    }, [currentQuestion, totalResults, navigate]);

    return (
        <Container>
            <QuestionText>/question process indicator</QuestionText>
            <Box>
                {renderStageBar()}
                {currentQuestion < QuizData.length
                    ? renderQuestion()
                    : renderResult()}
            </Box>
        </Container>
    );
}

```

<br>

## Result.tsx

`useMemo`를 사용하여 `totalResults`를 계산하고 있지만, `quizData`와 `answer`가 변경될 때마다 재계산되지 않고, 이전에 계산한 값을 재사용한다. 전에 코드는 성능상의 이점을 발생하게 하여 문제가 되었었다.

<br>

이후의 수정된 코드는 `useParams`를 사용하여 URL에서 `mbtiType`을 가져오고, `AnswersResult`에서 해당 유형의 결과를 찾아 출력하는 방식으로 변경하였다. 또한, `NotFound` 컴포넌트를 사용하여 결과를 찾지 못했을 때의 처리도 추가.

```typescript
// before
import { useMemo } from 'react';
import { useLocation } from 'react-router-dom';
import ResultType from 'src/types/resultType';

export default function Results() {
  const { state } = useLocation();
  const { quizData = [], answers = [] } = state || {};

  const totalResults: ResultType[] = useMemo(() => {
    const typeScores: Record<string, number> = {
      N: 0,
      A: 0,
      P: 0,
      C: 0,
      T: 0,
      W: 0,
      O: 0,
      F: 0,
    };
    quizData.forEach((question: any, index: number) => {
      const answerIndex = answers[index];
      if (answerIndex !== undefined) {
        const { type, point, answer } = question.options[answerIndex];
        console.log(`Question ${index}: ${answer} (${type}, ${point} points)`);

        typeScores[type] += point;
      }
    });

    const mbtiType = [
      typeScores.N > typeScores.A ? 'N' : 'A',
      typeScores.P > typeScores.C ? 'P' : 'C',
      typeScores.T > typeScores.W ? 'T' : 'W',
      typeScores.O > typeScores.F ? 'O' : 'F',
    ].join('');

    const results = [{ type: mbtiType, score: 1 }];

    return results;
  }, [quizData, answers]);

  const largestType = { N: 0, P: 0, T: 0, O: 0 };

  totalResults.forEach((result) => {
    const { type } = result;
    const { score } = result;

    if (type.includes('N') && score > largestType.N) {
      largestType.N = score;
    } else if (type.includes('P') && score > largestType.P) {
      largestType.P = score;
    } else if (type.includes('T') && score > largestType.T) {
      largestType.T = score;
    } else if (type.includes('O') && score > largestType.O) {
      largestType.O = score;
    }
  });

  return (
    <div>
      <h2>Results</h2>
      <ul>
        {totalResults.map((result) => (
          <li key={result.type}>{result.type}</li>
        ))}
      </ul>

      <br />

      {quizData.map((question: any, index: number) => {
        const answerIndex = answers[index];
        if (answerIndex !== undefined) {
          const { type, point, answer } = question.options[answerIndex];
          return (
            <p key={index}>
              Question {index + 1}: {question.question}
              <br />
              Answer: {answer}
              <br />
              Type: {type}
              <br />
              Points: {point}
            </p>
          );
        }
        return null;
      })}
    </div>
  );
}

// after
import { useLocation, useParams } from 'react-router-dom';
import AnswersResult from 'src/__mocks__/answer';
import NotFound from '../NotFound';

export default function Results() {
  const { state } = useLocation();
  const { quizData = [], answers = [] } = state || {};
  const { mbtiType } = useParams();

  const result = AnswersResult.find((item) => item.type === mbtiType);

  return (
    <div>
      {result ? (
        <>
          <h2>Results</h2>
          <h3>해당 유형의 id: {result.id}</h3>
          <h3>해당 유형의 type: {result.type}</h3>
          <h3>해당 유형의 title:{result.title}</h3>
          <h3>해당 유형과 어울리는 type: {result.matchedType}</h3>
          <h3>해당 유형과 어울리는 type의 title: {result.matchedTitle}</h3>
        </>
      ) : (
        NotFound()
      )}

      {quizData.map((question: any, index: number) => {
        const answerIndex = answers[index];
        if (answerIndex !== undefined) {
          const { type, point, answer } = question.options[answerIndex];
          const questionKey = `question_${question.id}`;

          return (
            <p key={questionKey}>
              Question {index + 1}: {question.question}
              <br />
              Answer: {answer}
              <br />
              Type: {type}
              <br />
              Points: {point}
            </p>
          );
        }
        return null;
      })}
    </div>
  );
}
```

### 결과계산.

퀴즈 결과를 정확하게 계산하고 처리하는것이 매우 중요하다. `useMemo` 상태가 변경될 때마다 각 유형의 총점을 계산할 수 있도록 Hooks를 사용하는 것이 좋은 판단이였다. 메모리 누수도 막을겸.
<br>
<br>

### 결과 페이지로 이동

내 코드는 hooks를 이용하여 `useEffect`모든 질문에 답 했을때 자동으로 탐색이 가능하게 한다. 조건부 렌더링에만 의존하는 것보다 더 신뢰할수있는 방안이였다.
<br>
탐색이 필요할 때 항상 발생하도록 하여 사용자의 경험을 개선하기 위해 코드를 수정을 했음.

### 요약본.

요약하자면, React에서 상태변경 및 부작용을 올바르게 처리하는것을 중요시 보여주고, `useMemo` 및 `useEffect` 코드가 더 안정적으로 이해하기 쉽게 작성을 하였다.

```toc

```
