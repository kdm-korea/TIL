# 데이터베이스 정리

## 데이터베이스의 정의
### 통합된 데이터(Integrated Data) 
- 검색의 효율성을 위해 중복이 최소화된 데이터

### 저장 데이터(Stored Data)
- 컴퓨터가 접근 가능한 저장 매체에 저장된 데이터

### 운영 데이터(Operational Date)
- 조직 목적을 위해 존재 가치가 확실하고 반드시 필요한 데이터

### 공유 데이터(Shared Data)
- 여러 응용 프로그램들이 공동으로 사용하는 데이터

## 데이터베이스의 특징
### 실시간 접근성(Real Time Accessibility)
- 사용자의 질의에 대해 직시 처리하여 응답하는 특징

### 계속적인 변화(Continuous Evolution)
- 삽입, 삭제, 갱신을 통하여 항상 최근의 데이터를 유지하는 특징

### 동시 공유(Concurrent Sharing)
- 데이터베이스에 있는 데이터 참조시 사용자의 요구에 따라 참조하는 특징

### 내용에 의한 참조(Content Reference)
- 여러 사용자가 동시에 요구하는 데이터 내용에 따라 참조하는 특징

### 데이터의 독립성(Independence)
- 논리적 독립성
    - 응용프로그램과 데이터베이스를 분리시켜 논리적 구조를 변경하여도 응용프로그램은 변화되지 않음
- 물리적 독립성
    - 응용프로그램과 물리적 장치를 분리시켜 새로 디스크를 추가하더라도 응용프로그램은 변화되지 않음

## 데이터 언어
### DDL (Data Definition Language 데이터 정의어)
- 데이터베이스 구조, 형시그 접근방식 등 데이터베이스를 변경하는 목적의 언어
- DDL이 컴파일 후 Data Dictionary에 저장
- DDL 기능
    - 데이터베이스의 논, 물리적 구조 정의 및 변경
    - 스키마에 사용되는 제약 조건 정의
        - 스키마는 데이터베이스 제약조건에 대한 명세
    - 데이터의 물리적 순서를 정함
    - DDL로 정의된 내용은 메타데이터(Meta Data)가 되며 시스템 카탈로그(System Catalog)에 저장

### DML (Data Manipulation Language 데이터 조작어)
- 응용프로그램과 DBMS간의 언어
- 검색, 삽입, 삭제, 갱신 연산 등 데이터 처리를 위해 존재

### DCL (Data Control Language 데이터 제어어)
- 보안 및 권한제어, 무결성의 언어
- DCL의 기능
    - 데이터 보안
        - 권한이 없는 접근에서 데이터베이스 보호
    - 데이터 무결성
        - DML에 대하여 데이터가 제약 조건에 검사
    - 데이터 회복
        - 시스템 오류 등에서 복구
    - 병행 제어
        - 여러 사용자가 동시접근 및 공유 가능

## 데이터베이스 사용자
### 데이터베이스 관리자(DBA - DataBase Adminustrator)
- DDL와 DCL을 통해 데이터베이스를 정의, 제어하는 사람

### 데이터 관리자(Data Administrator)
- 데이터에 대한 총괄, 계획수립 및 관리, 통제하는 사람

### 데이터 설계자(Data Architect)
- 데이터 구조를 체계적으로 관리하는 사람

### 응용 프로그래머(Application Programmer)
- 프로그램 언어에 DML을 삽입하여 데이터베이스에 접근하는 사람

### 일반 사용자(End User)
- 질의어(Query Language)로 DBMS에 접근하는 사람

## 데이터베이스 관리 시스템 (Database Management System)
### 데이터베이스와 사용자 간 사용자의 지시에 따라 정보를 생성하고 관리하는 소프트웨어

### 기존 파일 시스템은 문제점
- 데이터 종속성으로 인한 문제점
<br> 데이터 접근방법 변경시 응용 프로그램도 같이 변화해야 함

- 데이터 중복성으로 인한 문제점
<br> 분산으로 데이터 확장성이나 무결성을 유지할수 없음

### DBMS 기능 3가지
- 정의 기능(Definition Facility)
    - Create
        - 스키마, 도메인, 테이블, 뷰, 인덱스 정의
        - 스키마 정의
        <br> 1. ID가 선생님인 사용자의 스키마 '학교'를 정의
        
                CREATE SCHEMA 학교 AUTHORIZATION 선생님;

        - 도메인 정의
        <br> 1. 군필/미필을 Y 혹은 N으로만 표기되는 도메인 ARMY를 정의

                CREATE DOMAIN ARMY CHAR(1)  
                    DEFAULT 'YES'
                    CONSTRAINT ARMY CHECK (VALUE IN('Y', 'N'));

        - 테이블 정의
        <br> 1. 학생 테이블 정의
        <br> 2. 학과의 학과코드를 참조하는 학생의 전공은 외래키로 사용
        <br> 3. 생년월일은 1980-01-01'부터 입력가능, 제약조건명은 생년월일제약
        <br> 4. 학과 테이블에서 삭제가 일어나면 관련된 튜플의 전공값을 Null로 변경
        <br> 5. 학과 테이블에서 학과코드가 변경되면 전공 값도 같은 값으로 변경
            
                CREATE TABLE 학생 
                (이름 VARCHAR(15) NOT NULL,
                    학번 CHAR(8),
                    전공 CHAR(5),
                    성별 SEX,
                    생년월일 DATE,
                    PRIMARY KEY(학번),
                    FOREGIN KEY(전공) REFERENCES 학과(학과코드)

                            ON DELETE SET NULL

                            ON UPDATE CASCADE,

                    CONSTRAINT 생년월일제약
                        CHECK(생년월일>='1980-01-01'));
            
            - 가변길이 문자열 - VARCHAR
            - 고정길이 문자열 - CHAR

    - Alter
        - 테이블에 대한 정의 변경
        - ADD : 새로운 속성추가
                
                ALTER TABLE STUDENT ADD GRADE VARCHAR(3) DEFAULT '1';
        
        - ALTER : 기본값 변경

                ALTER TABLE STUDENT ALTER GRADE SET DEFAULT '2';
        
        - DROP COLUMN : 속성 제거

                ALTER TABLE STUDENT DROP COLUMN GRADE;
    - Drop
        - 스키마, 도메인, 뷰, 인덱스, 트리거 제거
        - Drop 제거 옵션
            - CASCADE
                - 제거할 개체를 참조하는 모든 개체 제거
            - RESTRICT
                - 개체가 참조중인 경우 명령 취소

        - SCHEMA 제거

                DROP SCHEMA 스키마명;

        - DOMAIN 제거

                DROP DOMAIN 도메인명;

        - TABLE 제거

                DROP TABLE 테이블명;

        - VIEW 제거

                DROP VIEW 뷰명;

        - INDEX 제거

                DROP INDEX 인덱스명;

        - TRIGGER 제거

                DROP TRIGGER 트리거명;

        - CONSTRAINT 제거

                DROP CONSTRAINT 제약조건명;

- 조작기능(Manipulation Facility)
    - Select
    - Insert
    - Delete
    - Update

- 제어기능(Control Facility)
    - Commit
    - Rollback
    - Grant
    - Revoke


