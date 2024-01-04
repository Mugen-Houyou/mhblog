--
title: 스터디 노트 1월 2일 - Probono + Spring
layout: post
date:   2024-01-02 20:22:52 +0900
categories: test_1 test_2
---

# Probono 프로젝트에 Spring 적용하기
1. 분석
2. 구조
    rest api 개발은 주로 비동기로 개발
    jsp도 추가 개발 하면서 동기방식으로도 처리하는 기술 추가 학습
    1. 순수 자바    
        - dao / service / controller 기능
    2. entity
    3. controller 기능
        1. ProbonoController.java
            - spring으로 동기 방식으로 개발
                client요청 -> html -> controller -> jsp -> client에게 응답
            - 요청 객체, 요청 객체에 데이터 담아서 jsp로 출력 위임
            - Servlet API
                HttpServletRequest
                    setAttribute(key, value)
                    Object getAttribute(key)
                
                요청객체.getRequestDispatcher("jsp").forward(요청, 응답);
                
            
        2. ProbonoRestController
            - spring으로 비동기 방식으로 개발
                client요청 -> html -> Rest API로 구현된 controller(json)
                    -> 요청 page인 html 응답
            - controller가 json 문자열 포멧으로 바로 즉답 응답
                메소드 반환타입 
                    
            - rest api 사용시에는 http method 자체가 기능 표현
            - get방식 : 데이터 검색
            - post방식 : 데이터 저장 또는 수정
            - delete방식 : 데이터 삭제       
                    
                client요청 -> html -> controller -> jsp -> 요청 page인 html 응답
                
    4. jsp
        - spring 근본
            1. 가급적 spring 에게 의지해라
            2. 개발자는 순수하게 개발하는 코드 최소화
                - 표준화(글로벌)
            3. 객체 생성 즉 관리는 spring 내부에서 하겠다
                - spring 자체가 관리하는 객체 - spring bean
                - controller / service / repository(dao) 다 spring bean으로 활용
            4. 객체 수 자동 제어
                - 서버의 메모리 절약, 실행 속도 향상
                - 리소스 절약 및 개발 측면에서 짱 !!!
                
            5. jsp는 가급적 미적용 권장
                - spring 자체적인 tag존재
                - html 파일에 작업
                - 저장 위치 resources/templates
                    spring tag 실행 엔진이 구동되는 영역
                - 현 추세
                    js 로 화면단 처리 
                    - back end 언어의 종속성 없음
                    - back end 모든 언어와 소통
                    - vue.js or react.js
        
            6. jsp를 사용시
                - jsp 개발 위치를 생성해야 하는 시대
                - spring은 jsp 개발시 보안을 고려(최초 spring 기준)
                    - 정통 일반 실행 구조
                        - project명/WEN-INF
                                        -classes
                                            - *.class
                                        -lib
                                            - *.jar
                                        -web.xml : project환경설정 파일
                                                (애노테이션으로 처리하는시대라 생략 가능)
                                    /*.html, *.jsp, 이미지, *.js, *.css
                                    
                                    
                    - spring만 가능하게한  정통 일반 실행 구조
                        - project명/WEN-INF
                                      - *.jsp 개발 가능한 구조
                                        :  설정에 WEB-INF에 jsp 개발하겠다는 설정 필수
                                        : 왜? 보안
4. 소스 분석
    1. application.yml  or application.properties
        - spring project의 설정 정보
        - jsp 위치
        - db접속 정보
        - context명
        - port번호
        ... 설정에 필요한 모든 정보 
