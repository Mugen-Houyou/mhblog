---
title: 스터디 노트 12월 12일
layout: post
date:   2023-12-12 20:29:17 +0900
categories: test_1 test_2
---
# Java의 Optional API 학습 내용

## 1. Optional API란?
- **Java -부터 도입된 기능**
- NULL 처리를 대신하기 위해 만들어진 새로운 코어 라이브러리 데이터 타입
- 주의: 실행 시 NULL 예외 발생 ==> 코드의 품질이 나쁘다.

## 2. Optional 클래스 사용 방법
- Optional 클래스에서는 3가지 정적 팩토리 메서드를 제공
	- .empty() ==> 빈 Optional 객체를 생성.	
	- .of(val) ==> NULL이 넘어오면 NullPointerException 발생.
	- .ofNullable(val) ==> NULL이 넘어오면 그냥 무시.

- 객체의 메서드들
	- ifPresent(val) ==> null 아닐 경우에만 반환
	- orElse(val) ==> null일 경우 orElse 메서드의 파라미터값을 반환, null 아닐 경우는 객체값을 반환.
	- orElseThrow(val) ==> null일 경우 orElseThrow 메소드의 parameter로 들어간 Exception 발생

## 4. 주의점
- 
