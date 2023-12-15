---
title: 스터디 노트 12월 11일 (1)
layout: post
date:   2023-12-11 23:18:17 +0900
categories: test_1 test_2
---

# 애노테이션

1. 수업 시간에 다룬 애노테이션들
@NoArgsConstructor
@AllArgsConstructor
@Getter
@Setter
@ToString

@RequiredArgsConstructor 
	- 원하는 멤버 변수들만 초기화 가능한 동적 생성자.
@NonNull
	- @NotNull과는 다름. 
	- @RequiredArgsConstructor와 매핑, 선언된 멤버 변수들만 초기화하는 생성자를 만듦.

@Slf4j
	- 로깅에 필요한 추상화된 기능을 제공.
@Builder
	- 다양한 용도의 생성자와 흡사한 메서드를 동적으로 생성.

@Test
	- JUnit에서 제공
	- 개발자를 위한 단위 테스트용.

@Override
	- 부모 클래스나 인터페이스의 메서드를 재정의함을 명시.

# 람다 (Lambda)
	- JDK 1.8부터 지원
	- Lambda 표현식: @FunctionalInterface의 구현체로 구성되는 instance.
	- 메서드를 직접 구현하지 않고 하나의 식으로 표현.
	- 코드 간소화, 가독성 향상, 타언어와의 문법 경계 최소화
	- 동적 로직을 바로 적용 가능 ==> 확장성 및 생산성 향상
	
# 기능적 인터페이스
	- *.java 파일 종류:
		- 자바 클래스 (기본)
		- enum: 데이터 자체를 상수화하여 명확성 부여
		- interface
	- 인터페이스
		- 클래스의 스펙을 정함
		- 구조: 상수, 주석, 메서드 선언구 (미완성)
		- 강제되는 사항: 스펙에 맞게 메서드를 재정의해야 함.
		- 가장 대표적인 구조: DB 연동 드라이버

## 익명 이너 클래스
	- 장점: 메서드의 로직을 재정의하면서 새로운 객체를 생성
	- 방법 2가지: 기존 방식, 람다 방식.
	
## 특별한 기능을 보유한 마킹 인터페이스
	- java.io.Serializable
		- 자바 객체를 네트워크로 송수신 시 데이터 유실 방지하고자 하는 설정
		- 마킹만 해서 기능 적용
		- 메서드가 없기 때문에 재정의도 불필요
		- 주로 DTO에 적용됨
	- @FunctionalInterface
		- 람다 표현식의 타겟으로 사용됨
		- 강제사항: 메서드 하나만 제시
		