# 목차

- [데이터베이스의 정의](#데이터베이스의-정의)
- [데이터베이스의 특징](#데이터베이스의-특징)
- [데이터의 유형](#데이터의-유형)
- [파일 시스템을 사용했을 경우의 문제점](#파일-시스템을-사용했을-경우의-문제점)
- [DBMS (Database management system)의 필요성](#DBMS-Database-management-system-의-필요성)
- [MySQL 정리](#MySQL-정리)

# 데이터베이스의 정의

특정 조직의 여러 사용자가 공유하여 사용할 수 있도록 통합해서 저장한 **운영데이터의 집합**

ex) 은행 : 계좌정보, 입출금 내역 등 / 항공사 : 예약정보, 비행기 스케쥴링



# 데이터베이스의 특징

- **실시간 접근 가능**

- **계속적으로 변화**

- **동시 공유가 가능**

- **저장된 주소가 아닌 내용으로 참조 가능**

  데이터가 위치한 위치가 아닌 의미있는 내용으로 조회가 가능하다. 



# 데이터의 유형

- **정형 데이터 (structured data)**

  ex) 엑셀의 스프레드시트, 관계데이터베이스의  테이블

- **반정형 데이터 (semi-structured data)**

  ex) self-describing data : HTML, XML, JSON

- **비정형 데이터 (unstructured data)**

  정해진 구조가 없이 저장된 데이터

  ex) text, 멀티미디어 데이터(이미지, 영상 등)



# 파일 시스템을 사용했을 경우의 문제점

- **데이터 중복성 문제 : 공간 낭비**

- **업데이트 및 데이터 일관성 유지에 어려움**

- **데이터 무결성 (data integrity constraints) 유지 어려움**

  응용프로그램이 모두 체크해야 한다. (ex. 나이 > 0 )

- **데이터 종속성**

  응용프로그램이 파일 데이터 구조에 종속적이다. 

  파일구조가 바뀔 때마다 응용프로그램을 교체해야 한다. 

- **동시성 (Concurrency) 제공이 어려움**

  여러 사용자가 동시에 접근할 때 문제해결에 어려움

- **원자성 (Atomicity) 제공 어려움**

  파일 변경 중에 시스템 장애가 발생했을 때 처리 어려움

- **보안 (Security) 제공 이슈**

  사용자별 파일 안의 일부 데이터 읽기 권한 제어가 어려움



# 데이터베이스 관리시스템(DBMS)의 필요성

파일 시스템을 사용했을 경우의 문제점을 해결하기 위한 방법으로 응용프로그램과 데이터 연결을 도와주며 **데이터 관리와 데이터에 대한 기본 처리를 담당**하는 추가적인 소프트웨어이다. 

![image](https://user-images.githubusercontent.com/71866756/148538150-cb2c1431-792c-4cf8-9703-c3a78ecc4940.png)



- **특징**

  - **응용프로그램과 데이터 파일 분리**

    프로그램은 DBMS를 통해서 파일시스템의 파일에 저장한 데이터에 접근한다. 

  - **데이터베이스의 생성과 관리를 담당**

  - **모든 응용프로그램은 데이터베이스 공유 가능, DBMS를 통해 데이터 삽입, 수정, 검색**

    EX) Oracle, MS SQL Server, Sap HANA, MySQL, PostgreSQL

  

- **기능**

  - 정의 기능 : 데이터베이스 구조를 정의하거나 수행
  - 조작 기능 : 데이터를 삽입, 삭제, 수정, 검색하는 연산 수행
  - 제어 기능 : 데이터를 항상 정확하고 안전하게 유지하는 기능



- **장점**
  - 파일시스템의 데이터 중복 문제 해결
  - 데이터 독립성 확보 (데이터 구조가 바뀌어도 응용프로그램을 바꿀 필요 없음)
  - 데이터 동시 공유 (Concurrency control)
  - 데이터 보안 향상 - 사용자 별 접근 가능한 데이터베이스 영역 제한 가능
  - 데이터 무결성 유지
  - 표준화 방식으로 데이터에 접근 (with 데이터베이스 언어)
  - 장애 발생 후 회복 시 데이터 일관성과 무결성 유지 - 트랜잭션 가능
  - 응용 프로그램 개발 비용이 줄어듬
- **단점**
  - 응용 프로그램 개발 비용은 줄지만, DBMS 구매 비용이 증가한다. 
  - 응용프로그램이 DBMS를 통해 데이터에 접근하기 때문에 추가적인 오버헤드가 있다. 
  - 응용 프로그래머가 DBMS가 어떻게 동작하는지와 표준 데이터 언어에 대한 지식 필요
  - DBMS 장애가 발생할 때 모든 응용프로그램 장애가 발생함



- **용어 정리**

  - **Data Dictionary (System catalog)**

    DBMS는 database와 함께 metadata을 저장한다.

    데이터 정의어 (DDL)에 의해 생성된다. 

    

  - **Metadata**

    각 데이터에 접근할 수 있는 데이터의 이름 (테이블, 컬럼 이름 등)

    스토리지에 데이터가 저장된 위치

    보안을 위한 제약 (security constraint) : 누가 어떤 데이터를 접근할 수 있나

    무결성을 위한 제약 (integrity constraint) : 어떤 값이 데이터에 유효하다. 



# MySQL 정리

- **용어정리**
  - query 
  
    사용자가 DBMS에 내리는 명령
  
  - table 
  
    데이터베이스에서 데이터를 형테를 정해 모아놓은 저장 공간 (행과 열로 이루어진 데이터 표)
  
  - column(열)
  
    데이터를 저장하기 위한 틀
  
    1) 컬럼의 이름과 데이터 타입은 테이블을 만들 때 미리 정해진다.
    2) 컬럼의 이름은 동일한 테이블 내에서 중복될 수 없다.
    3) 테이블은 반드시 1개 이상의 컬럼을 가진다.
  
  - 값
  
    컬럼에 속한 실제 데이터의 값
  
    1) 컬럼의 데이터 타입만을 값으로 가질 수 있다. 
  
  - row(행)
  
    관계된 값의 리스트
  
    1) 하나의 로우는 하나의 관계된 데이터를 의미한다.
  
       ex) 하나의 로우가 한 사람의 데이터
  
    2) 같은 테이블 안에서 로우는 항상 동일한 구조를 가진다.
  
    3) 로우를 단위로 데이터를 삽입한다. 
  
  
  
- **MySQL에서 많이 사용하는 데이터 타입**

  - 정수형

    <img src="../../../AppData/Roaming/Typora/typora-user-images/image-20220107203754897.png" alt="image-20220107203754897" style="zoom:67%;" />

  - 실수형

    <img src="../../../AppData/Roaming/Typora/typora-user-images/image-20220107203737076.png" alt="image-20220107203737076" style="zoom:67%;" />

  - 문자형

    다른 데이터 타입과 다르게 (n)으로 몇 바이트인지 지정해준다. 

    <img src="../../../AppData/Roaming/Typora/typora-user-images/image-20220107203836347.png" alt="image-20220107203836347" style="zoom:67%;" />

    - CHAR(n)

      고정 길이 문자형으로 만약 n=5이고 "ABC"를 저장했다면 나머지 공간 2는 그대로 비어져있다. 

    - VARCHAR(n)

      변동 길이 문자형으로 만약 n=5이고 "ABC"를 저장했다면 나머지 공간 2는 free된다. 

      

    <img src="../../../AppData/Roaming/Typora/typora-user-images/image-20220107204053999.png" alt="image-20220107204053999" style="zoom:67%;" />

  - 날짜형 

    ex) 2021-12-15 01:02:03

    <img src="../../../AppData/Roaming/Typora/typora-user-images/image-20220107204126933.png" alt="image-20220107204126933" style="zoom:67%;" />

    

- **기본적인 데이터 다루기**

  - 데이터끼리 연산 가능

    

  - CONCAT

    두 데이터 합치기

    ```mysql
    SELECT 1+2,80-12;
    ```

    문자형 데이터의 경우 ""나 ''와 함께 쓰여야 한다. 그렇지 않을 경우 데이터베이스/테이블/컬럼의 이름으로 인식된다.

    

  - CAST (숫자를 문자로 변환)

    ```mysql
    SELECT CAST(123 AS CHAR(5));
    ```

  - CONVERT (문자를 숫자로 변환)

    ```mysql
    SELECT CONVERT('1004',INT);
    ```

    

  - DATE_FORMAT (문자를 날짜로 변환)

    ```mysql
    SELECT DATE_FORMAT('20210128','%Y-%m-%d')
    ```

    

  - **데이터베이스 만들기**

    ```mysql
    CREATE DATABASE customer; # 데이터베이스 이름
    ```

  - **데이터베이스 지우기**

    ```mysql
    DROP DATABASE customer; # 데이터베이스 이름
    DROP DATABASE IF EXISTS customer; # 데이터베이스 이름
    ```

  - **데이터베이스 목록 보기**

    ```mysql
    SHOW DATABASES;
    ```

  - **데이터베이스 사용하기**

    ```mysql
    USE[데이터베이스 이름];
    ```

  - **테이블 만들기**

    ```mysql
    CREATE TABLE idol(name VARCHAR(20),
                    age INT,
                    group VARCHAR(50)
                    );
    ```

  - **테이블 이름 변경하기**

    ```mysql
    ALTER TABLE customer RENAME customers; # 테이블 이름, 테이블 이름
    ```

  - **새로운 컬럼 추가하기**

    ```mysql
    ALTER TABLE customers ADD COLUMN age INT; # 테이블 이름, 컬럼이름, 데이터타입
    ```

  - **기존 컬럼 타입 변경하기**

    ```mysql
    ALTER TABLE customers MODIFY COLUMN age FLOAT; # 테이블 이름, 컬럼이름, 데이터타입
    ```

  - **기존 컬럼 이름과 타입 변경하기**

    ```mysql
    ALTER TABLE customers CHANGE COLUMN age new_age FLOAT; # 테이블 이름, 기존 컬럼 이름, 새로운 컬럼 이름, 데이터 타입
    ```

  - **컬럼 지우기**

    ```mysql
    ALTER TABLE customers DROP COLUMN age # 테이블 이름, 컬럼 이름 
    ```

  - **테이블 지우기**

    ```mysql
    DROP TABLE customers; # 테이블 이름
    DROP TABLE IF EXISTS customers; # 존재한다면 삭제
    ```

  - **테이블 값만 지우기**

    ```mysql
    TRUNCATE TABLE customers; # 테이블 이름
    ```

  - **데이터 하나 삽입하기**

    ```mysql
    INSERT INTO customers (name, age, group) # 컬럼1, 컬럼2, 컬럼3
    VALUES ("goo",25,"university"); # 컬럼1값, 컬럼2값, 컬럼3값
    
    # 값을 여러개 넣고 싶은 경우
    INSERT INTO customers (name, age, group)
    VALUES ("goo",25,"university"),
    	   ("hoo",26,"highschool");
    ```

  - **데이터 일부 삭제하기**

    ```mysql
    DELETE FROM customers
    WHERE 조건 값;
    ```

  - **데이터 일부 수정하기**

    ```mysql
    UPDATE customers
    SET age=22
    WHERE 조건 값;
    ```



- **데이터 가져오기**

  - **가져올 데이터 선택하기**

    ```mysql
    SELECT 123;		# 123
    SELECT 1+2+3; 	# 6
    SELECT "abc"; 	# abc
    
    # 값을 가져올 COLUMN 선택하기
    SELECT age					# 컬럼 이름
    FROM customers.customer;	# 데이터베이스 이름.테이블 이름
    							# 만약 USE를 통해 데이터베이스를 선택했다면
    							# 데이터베이스 이름 생략 가능
    # 컬럼 여러개 선택
    SELECT age, name			# 컬럼 이름
    FROM customers.customer;	# 데이터베이스 이름.테이블 이름
    
    # 표 전체 가져오기
    SELECT *					
    FROM customers.customer;	# 데이터베이스 이름.테이블 이름
    ```

  - **Reference**

    컬럼 이름을 별명처럼 가져온다. 실제 테이블에서의 컬럼 이름은 바뀌지 않는다. 

    ```mysql
    SELECT age AS age_temp		# 컬럼 이름, 컬럼 별명
    FROM customer;				# 테이블 이름
    ```

  - **데이터 일부만 가져오기**

    ```mysql
    SELECT age, name			# 컬럼 이름
    FROM customers.customer		# 데이터베이스.테이블 이름
    LIMIT 2;					# 가져올 row 수 (상위 2개의 row만 가져온다.)
    ```

  - **중복 제거하기**

    ```mysql
    SELECT DISTINCT age			# 컬럼이름
    FROM customers.customer;	# 데이터베이스.테이블 이름
    
    # 만약 해당 컬럼 내의 중복된 값이 있으면 하나만 가져온다. 
    ```

  - **실습**

    ```mysql
    DROP DATABASE IF EXISTS pokemon;
    CREATE DATABASE pokemon;
    USE pokemon;
    CREATE TABLE mypokemon(number INT,
    name VARCHAR(20),
    type VARCHAR(20),
    height FLOAT,
    weight FLOAT,
    attack FLOAT,
    defense FLOAT,
    speed FLOAT);
    INSERT INTO mypokemon(number,name,type,height,weight,attack,defense,speed)
    VALUES (10,"caterpie","bug",0.3,2.9,30,35,45),
    (25,"pikachu","electric",0.4,6,55,40,90),
    (26,"raichu","electric",0.8,30,90,55,110),
    (133,"eevee","normal",0.3,6.5,55,50,55),
    (152,"chikorita","grass",0.9,6.4,49,65,45);
    
    SELECT name,height,weight
    FROM mypokemon;
    
    SELECT name,attack,defense,speed 
    FROM mypokemon;
    
    SELECT name AS new_name, attack+defense+speed AS total 
    FROM mypokemon;
    ```



- **조건에 맞는 데이터 가져오기**

  - **조건 설정하기**

    - BETWEEN, IN

    ```mysql
    SELECT age,name		# 컬럼 이름
    FROM customer		# 테이블 이름
    WHERE NOT age=22;		# 조건 
    
    # BETWEEN A AND B는 A<=컬럼 AND 컬럼<= B과 같다.
    # 컬럼 이름 IN (A,B,C) 는 컬럼에 해당하는 값이 A,B,C에 속하면 True
    SELECT age,name				# 컬럼 이름
    FROM customer				# 테이블 이름
    WHERE age IN (22,23,43);	# 조건 
    
    ```

  - **와일드 카드**

    % : 0개 이상의 문자

    _ : 1개의 문자

    ex) 

    '%e' : e로 끝나는 문자열

    'e%' : e로 시작하는 문자열

    '%e%' : e를 포함하는 문자열

    

    '_e' : e로 끝나고 e 앞에 1개의 문자가 있는 문자열

    '%_e' : e로 끝나고 e앞에 1개 이상의 문자가 있는 문자열

    '%_e _%' : e 앞 뒤로 각각 1개 이상의 문자가 있는 문자열

    

    - LIKE

      ```mysql
      SELECT name
      FROM mypokemon
      WHERE name LIKE '%chu';		# 'chu'로 끝나는 문자열 찾기
      
      SELECT name
      FROM mypokemon
      WHERE name LIKE '%a_%';		# a를 포함하지만 a로 끝나지 않는 문자열 찾기
      							# %a_%나 %a%_나 같은 의미이다. 
      ```

      

  - **NULL인지 확인하기**

    0이나 공백과는 다른 값이 없음을 나타냄

    ```mysql
    SELECT name
    FROM mypokemon
    WHERE number IS NULL;	
    #WHERE number IS NOT NULL;
    ```

    

  

