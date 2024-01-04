---
title: 스터디 노트 12월 19일 (1)
layout: post
date:   2023-12-19 20:22:52 +0900
categories: test_1 test_2
---

# 

## Sequence (Oracle) 및 AUTO_INCREMENT (MySQL) 이해
1. RDBMS에 직접 스키마를 구성 시
	- Sequence를 통해 번호 매기기
		1단계: Sequence 생성
		2단계: 테이블 생성
		3단계: INSERT 시 컬럼값에 sequence를 적용		
	```sql
	CREATE SEQUENCE fisa_no_seq;
	CREATE TABLE fisa (
		no long primary key,
		name varchar2(10) not null
	);
	INSERT INTO fisa VALUES ( fisa_no_seq.nextval, ...);
	```
	
	- AUTO_INCREMENT를 통해 번호 매기기
		1단계: AUTO_INCREMENT를 명시한 테이블 생성
		2단계: INSERT 시 해당 컬럼값을 명시하지 않음
	```sql
	CREATE TABLE fisa (
		no long primary key AUTO_INCREMENT,
		name varchar2(10) not null
	);
	INSERT INTO fisa (name, ...) VALUES (...);
	```	

2. JPA를 통해 스키마 자동 생성 시
```java
@SequenceGenerator(name = "team4_seq", sequenceName = "team4_seq_id",
				   initialValue = 1, allocationSize = 50)
@Entity
public class Team4 {
	@Id
	@GeneratedValue(strategy = GenerationType.SEQUENCE, generator = "team4_seq")
	@Column(name = "team_id")
	private long teamId;
```

	1. name 속성 : 해당 entity에서 선언 및 사용하겠다는 sequence 기능 선언 및 이름 부여. 이름이 있다는 건 차후 불리어질 예정이라는 것.
	2. sequenceName
		: oracle db내에 생성할 sequence명
	3. allocationSize - db로 부터 insert마다 sequence 적용해야 하나
		seq명.currval : 현 시퀀스값 검색 
		단 entity 생성시에 필요, 경우에 따라 entity commit 안 할수도 있음
		seq명.currval  의미가 없음
		이런일 발생 가능 및 db접속의 효율성을 위한 사전에 미리 시퀀스값 만들어서 자바단 메모리에 저장해 놓고
		사용하겠다는 설정
		50개 초과시 51 시퀀스값 요청시 50 추가 생성 51~100 즉 50 증가치
	4. generator
		: 컬럼에 선언
		: @SequenceGenerator(name = "team4_seq") 속성값으로 해당 컬럼에 해당 시퀀스 매핑


## 
1. 

2.
