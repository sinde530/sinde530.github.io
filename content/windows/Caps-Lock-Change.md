---
emoji: 🎐
title: Window 한/영 Caps-Lock 으로 변경하기
date: '2022-05-01 16:26:00'
author: Crong
tags: Windows Key Changes
categories: 블로그 featured
---

## Window Key 변경하기

1. 윈도우 키 + R 실행창 (Run dialog box)를 눌러 `레지스트리 편집기`를 검색 한다.
2. control + f 를 눌러 `\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Keyboard Layout` // 경로를 찾아준다.
3. Keyboard Layout → 2진수 파일을 생성해주고, FileName = “ Scancode Map “ 으로 저장한다.

![https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fa636d38c-352a-482d-b571-24263acae6a7%2FUntitled.png?table=block&id=13c10a06-a8de-491e-86d7-82097fd6730d&spaceId=f08f49e0-d5e2-4c6e-9785-524d05da8a03&width=1450&userId=00f35be7-f598-4c28-bec1-5ca4b2e59847&cache=v2](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fa636d38c-352a-482d-b571-24263acae6a7%2FUntitled.png?table=block&id=13c10a06-a8de-491e-86d7-82097fd6730d&spaceId=f08f49e0-d5e2-4c6e-9785-524d05da8a03&width=1450&userId=00f35be7-f598-4c28-bec1-5ca4b2e59847&cache=v2)

4. Scancode Map 2진수 표현은 보는거와 같이 작성을 해준다.

![https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F6a52f8bf-8e21-49f7-9707-ff202a7d3432%2FUntitled.png?table=block&id=db1266b1-9a4d-41f4-aa1d-48019de5fd70&spaceId=f08f49e0-d5e2-4c6e-9785-524d05da8a03&width=1450&userId=00f35be7-f598-4c28-bec1-5ca4b2e59847&cache=v2](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F6a52f8bf-8e21-49f7-9707-ff202a7d3432%2FUntitled.png?table=block&id=db1266b1-9a4d-41f4-aa1d-48019de5fd70&spaceId=f08f49e0-d5e2-4c6e-9785-524d05da8a03&width=1450&userId=00f35be7-f598-4c28-bec1-5ca4b2e59847&cache=v2)

5. 설정이 완료 되면 재부팅후 Caps Lock 키가 변경이 되었는지 확인을 한다.
