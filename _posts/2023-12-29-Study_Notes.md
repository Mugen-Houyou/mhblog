---
title: 스터디 노트 12월 29일 (1)
layout: post
date:   2023-12-20 20:22:52 +0900
categories: test_1 test_2
---

# Spring 및 Spring Boot

## Web Apps
1. 서버
	ip - 시스템 자체의 구분 통신 주소, 시스템별 하나
	port - 하나의 시스템에 여러개 보유 가능
        
2. 서버에서 서비스 시 접속 시 URL
	`http://ip:port/context/path?web쿼리스트링`
        `ip:port` : 사용자 편의성을 고려한 domain으로 변환해서 서비스  
        `context` : project명을 의미하기도 하고 설정으로 이름을 지정하기도 함   
        `path` : 파일이 있는 접속 경로           
		`key=value&key2=v` : 웹 쿼리 스트링
        예시: http://localhost:8080
		
		
2. 개인 로컬 시스템에 사용했던 port
    1. window - tomcat : 8080
    2. linux 
        - mysql : 3306
        - oracle : 1521
    3. 실습시
        window <   -  >   linux
            linux의 private한 네트웍 설정을 public으로 변환
            - nat 
        
3. tomcat
    1. port 수정시
        server.xml의 http 통신 port 수정 영역
    2. spring boot의 내장 서버
        - 대부분의 설정을 표준화 
        - application.properties에 작업 유도
		

		
1. web 서비스 개발시 고려 사항
    1. url
    2. get or post
    3. client 전송 데이터 처리(요청)
    4. client 응답 데이터 처리
    ..
2. servlet 관점
    url구성 - servlet당 하나만 구성 
        @WebServlet("url매핑값")
        class 선언구
3. Spring 관점
    하나의 일반 클래스에 다수의 url 구성 가능       
    메소드별 처리 기능이 다 다름
    질문 : url매핑 정보 위치도 메소드 선언구
    
4. Spring 장점
    1. 일반 자바 클래스를 애노테이션 설정으로 http 통신이 가능한 servlet 형식화
    2. 설정을 하는 애노테이션이 직관적
    
5. 주요 애노테이션
    1. @Controller : controller 기능의 클래스 의미
    2. @RestController 
        - 비동기용 controller
        - 요청응답 모두 하나의 메소드 처리
        - 반환 타입이 client에게 직접 응답하는 데이터
        
    3. @RequestMapping
        - 요청 방식과 url 매핑 
    4. @GetMapping
        - get처리 메소드 매핑
        - url 매핑정보 필수
    5. @PostMapping
        - post처리 메소드 매핑
        - url 매핑정보 필수
    6. @ParamValue ..?
        - client 가 입력한 데이터를 getParameter("key") 로 반환했던 코드의 대체
        
    7. @Service
        - 서비스 기능으로 구현하고자 하는 class에 선언하는 애노테이션
        - 기능
            객체로 사용 + service 로직이란 의미 부여
    8. @Repository
        - DAO 개발 클래스 선언구
        - 단어 뜻이 직관적인 의미
        
    9. @Autowired
        - 자동 객체 생성 
        - 멤버 변수 초기화 또는 setXxx() 호출로 멤버 변수 초기화
        - 생성자를 통한 멤버 변수 초기화 
        - 권장 위치
            멤버 변수에 선언시 자동으로 초기화
			
	10. @ExceptionHandler
		- 자바의 단점? 예외 처리가 필수, boilerplate 양산.
		- Spring에서 구조를 개선했음: 예외 처리는 필수, 단 중복 코드 제거 가능.
		- 예외 전담하는 처리 메서드 구현했음 ==> 그게 바로 @ExceptionHandler.
    
* DTO=VO=Bean
	- Spring Bean?
		- 클래스의 구조에 제한 없이 Spring 자체가 객체를 관리 및 생성.
		- @RestController, @Repository, @Service이 선언된 클래스들은 ==> 무적권 Spring Bean.
		- @RestController 선언된 객체의 생성 시점: 서버 시작 시.
		- @Repository 선언된 객체의 생성 시점: @Autowired 선언된 영역의 코드 실행 시. 즉 개발자가 지정할 수 있다.
	