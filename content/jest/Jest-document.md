---
emoji: π«
title: jest μ¬μ©ν΄λ³΄κΈ°
date: '2022-05-17 14:57:00'
author: Crong
tags: Jest React
categories: Jest React
---

## Testing μ΄λ λ¬΄μμΈκ°

`μννΈμ¨μ΄ νμ€νΈ` λ₯Ό λ§νλ€.

μ νμ΄ μμνλ λλ‘ λμ νλμ§ νμΈνλκ².

## νμ€νΈ νΌλΌλ―Έλ

> E2E Test = UI νμ€νΈ,μ¬μ©μ νμ€νΈ
> Integration Test = ν΅ν© νμ€νΈ(λͺ¨λλ€,ν΄λμ€λ€)
> Unit Test = λ¨μ νμ€νΈ(ν¨μ,λͺ¨λ,ν΄λμ€)

## TDD

TDD(Test-driven development ( νμ€νΈ μ£Όλ κ°λ° )
κ°λ°(μ½λ μμ±)μ  νμ€νΈ μ½λλ₯Ό λ¨Όμ  μμ±

### TDDλ₯Ό μμ±ν΄μΌ νλ μ΄μ 

- κ΅¬ν < μΈν°νμ΄μ€ => μ½λμ νλ¦¬ν° ν₯μ
- μ¬μ©μ μμ₯μμ μ½λλ₯Ό μμ±
- λͺ¨λ  μκ΅¬ μ¬ν­(λͺ©ν)μ λν΄ μ κ²
- μμ€ν μ λ°μ μΈ μ€κ³ ν₯μ
- κ°λ° μ§μ€λ ₯ ν₯μ

## Jest μμλ³΄κΈ°

[JEST κ³΅μλ¬Έμ](https://jestjs.io/)

μλ°μ€ν¬λ¦½νΈ νκ²½μμ νμ€νμ ν μμλ νλ μμν¬μ΄λ€.
νμ€ν λΌμ΄λΈλ¬λ¦¬μ€μμ κ°μ₯ κ°νΈνκ³  μ¬νν λΌμ΄λΈλ¬λ¦¬λΌκ³  ν μμμ.
λ°λ²¨μ μ΄μ©νκ±°λ νμμ€ν¬λ¦½νΈ,μ΅κ·€λ¬,λ·° UIνλ μμν¬μμλ μ¬μ©μ΄ κ°λ₯.

## JEST νμν μ©μ΄

expect : expect κΈ°λ₯μ κ°μ νμ€νΈν λ μ£Όλ‘ μ°μΈλ€
toBe : μ ννκ² μ΄ κ°μ΄μ¬μΌνλ€.
it = 3μΈμΉ­ μ£Όμ΄λΌ λ³Όμμμ
beforeEach = κ°κ° νμ€νΈμ½λλ€μ΄ μ€ννκΈ° μ μ μ€νλ¨
afterEach = ν¨μκ° μνμ΄ λλ€μμ νΈμΆμ΄ λ¨.

<br>
<br>

```toc

```
