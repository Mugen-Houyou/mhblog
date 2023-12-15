---
title: 스터디 노트 12월 15일 (1)
layout: post
date:   2023-12-15 20:22:52 +0900
categories: test_1 test_2
---

# JPA 및 JPA에서 쓰이는 XML 문서

## JPA: Java Persistence API
1. 기 설계된 RDBMS 구조를 자동 생성
	- 권장사항
		- 복잡한 테이블 관계 형성 및 생성은 순수한 SQL문으로 하자.
		- 매우 복잡한 SQL문은 JPA의 API로는 해결 잘 안되는 경우가 있음.
			- 이럴 때는, JDBC API + 순수 SQL문 + JPA + ...
2. 순수 자바 코드로 DDL (Create, Drop, Alter), DML () 처리 가능.
	- 각각의 기능 수행 가능 메서드가 존재.

## 특징
1. 잦은 요구사항 변동에 기민한 대응이 가능.
	- 전통적 방식: DROP TABLE ... ==> CREATE TABLE ... ==> 데이터 이관 ==> 자바 소스 수정 ==> 컴파일 ...
	- JPA는, 그냥 entity 클래스의 변수들 수정하여 테이블 구조 관리 가능.
2. persistence.xml
	- DB 서버의 접속 정보 (DB 서버 드라이버, URL, 크레덴셜, ...)
	- 실행될 SQL문 종류 지정, 가독성 고려, 부연 설명
		예시: XML 요소 중 'create': DDL, 운영 서버에서는 쓰지 말라. 'none': DML+Select만, 운영 서버에서는 이게 기본.
	- Table와 1:1 매핑되는, 즉 table 구조를 결정해주는 Java의 entity 클래스 등록
		- Eclipse에서 설정 방법:
			- persistence.xml 선택 ==> 마우스우클릭 ==> JPA Tools ==> Synchronize Class List
			- Spring로 넘어가면 이런 것도 자동화 가능.	

## 주요 애노테이션들
1. @Entity
	- Table과 1:1 매핑
	- Entity의 클래스를 의미. 클래스 이름이 table 이름으로 자동 적용.
	- 1개의 Entity 객체가 table의 1개의 row와 대응.
	
2. @Column
	- table의 컬럼명을 의미
	- 해당 변수명이 컬럼명으로 자동으로 대응.
	- 단, 수정도 가능 - name 변수명이 아니라 user_name 이름의 컬럼명으로 생성.
		@Column(name="user_name")
		private String name; 

3. @GeneratedValue
	- MySQL에서의 AUTO_INCREMENT 또는 Oracle의 Sequence에 대응.
	- 서버의 dialect마다 방식이 다름.
		예시: MySQL에서는 @GeneratedValue(strategy=GenerationType.IDENTITY)

4. @Id
	- PK 등 설정.
	- DB의 테이블에는 PK가 없을 수도 있음에도 이건 생략 불가능.
	- 참고: 요즘은 주로 long 타입을 사용한다더라.
	
## DBUtil.java의 3개 패키지: EntityManager, EntityManagerFactory, Persistence.
1. 접속수 제어 / Connection 객체 생성 및 삭제 관리
2. 단 API이름이 순수 JDBC와 달리 Entity용어 매핑된 API명으로 제시
4. 참고: EntityManagerFactory?
	- EntityManager를 만드는 공장.
	- 접속객체 수 관리, 접속객체 전반적인 관리.
	- 어떠한 DB에 어떤 ID/PW 등으로 접속하는지 등 정보를 보유하는 객체.
	- Factory pattern 객체 생성 및 관리하는 구조의 형식	.
	
## 참고사항: 용어 정리
1. Framework vs. library
	- Framework는 구조 및 형식을 제시, 그에 맞게 개발해야 함.
	- Library는 기능들의 모음. 구조 제약 없이 메서드들을 필요할 때 호출

2. JDBC 보유 ==> Hibernate (ORM의 원조) ==> JPA ==> Spring Data JPA

## 1. XML 문서의 개요
1. XML 문서란?

2. XML 문서의 specification을 보는 방법

3. JPA의 persistence.xml
	- 스펙 적용을 위한 확인 시 표현법 중 일부
		- 선언 횟수: + (1회~무한대), * (0회~무한대), ? (0회 또는 1회)

