---
title: 스터디 노트 12월 11일 (2)
layout: post
date:   2023-12-11 23:28:17 +0900
categories: test_1 test_2
---
# Java의 Stream API 학습 내용

## 1. Stream API 소개
- **Java 8부터 도입된 기능**
- **컬렉션의 요소를 함수형 방식으로 처리**할 수 있게 해줌
- 데이터를 추상화하여 다양한 연산을 편리하게 수행
- 주로 **컬렉션 프레임워크**와 함께 사용되어 데이터 처리 작업을 간소화

## 2. Stream 생성 방법
- `Collection.stream()`: 컬렉션의 스트림 생성
- `Stream.of()`: 개별 요소로부터 스트림 생성
- `Arrays.stream()`: 배열로부터 스트림 생성
- `IntStream.range()`, `LongStream.range()`: 숫자 범위로 스트림 생성

## 3. 주요 스트림 연산
### 중간 연산 (Intermediate Operations):
- `filter`: 조건에 맞는 요소만 추출
- `map`: 요소를 다른 형태로 변환
- `sorted`: 요소를 정렬
- `distinct`: 중복 제거
### 최종 연산 (Terminal Operations):
- `forEach`: 각 요소에 대해 작업 수행
- `collect`: 결과를 다른 형태로 수집
- `reduce`: 모든 요소를 하나로 줄임
- `sum`, `max`, `min`, `average`: 수치 연산 결과 반환

## 4. 스트림의 장점
- 선언적으로 데이터를 처리할 수 있음
- 가독성 및 유지보수성 향상
- 병렬 처리를 통한 성능 개선 가능 (`.parallelStream()` 사용)

## 5. 주의점
- 스트림은 한 번 사용하면 **재사용할 수 없음** (새 스트림 필요)
- 상태를 변경하는 연산이나 외부 변수 사용을 피해야 함 (함수형 프로그래밍 원칙 준수)
- 무한 스트림 생성 시 주의 필요 (적절한 종료 조건 설정)
