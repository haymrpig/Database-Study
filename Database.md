# 목차

- [데이터베이스의 정의](#데이터베이스의-정의)
- [데이터베이스의 특징](#데이터베이스의-특징)
- [데이터의 유형](#데이터의-유형)
- [파일 시스템을 사용했을 경우의 문제점](#파일-시스템을-사용했을-경우의-문제점)
- [DBMS (Database management system)의 필요성](#데이터베이스-관리시스템dbms의-필요성)
- [MySQL 정리](#mysql-정리)

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

    ![image](https://user-images.githubusercontent.com/71866756/148562610-c5270eb1-8ce4-48f5-8bfb-4df17c1660dc.png)

  - 실수형

    ![image](https://user-images.githubusercontent.com/71866756/148562677-ce8afcbb-7a2e-41b2-a07e-00768521536b.png)

  - 문자형

    다른 데이터 타입과 다르게 (n)으로 몇 바이트인지 지정해준다. 

    ![image](https://user-images.githubusercontent.com/71866756/148562717-81ea8697-a5c1-455e-85fc-909d8759f0f9.png)

    - CHAR(n)

      고정 길이 문자형으로 만약 n=5이고 "ABC"를 저장했다면 나머지 공간 2는 그대로 비어져있다. 

    - VARCHAR(n)

      변동 길이 문자형으로 만약 n=5이고 "ABC"를 저장했다면 나머지 공간 2는 free된다. 

      

    ![image](https://user-images.githubusercontent.com/71866756/148562756-be4cfd60-c50e-4681-9faa-e8f1644c19f0.png)

  - 날짜형 

    ex) 2021-12-15 01:02:03

    ![image](https://user-images.githubusercontent.com/71866756/148562811-da7b604c-d098-4904-a90c-f5b1ccafab08.png)

    

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



- **원하는 데이터 만들기 (정렬)**

  - 정렬하기

    ```mysql
    SELECT name
    FROM mypokemon
    ORDER BY number DESC;	# 내림차순(DESC), 오름차순(ASC) 정렬
    
    # 두개의 칼럼순으로 정렬
    SELECT number, name, attack, defense
    FROM mypokemon
    ORDER BY attack DESC,defense;	
    # attack를 기준으로 내림차순으로 정렬, attack의 값이 같을 경우 defense의 오름차순으로 정렬
    
    SELECT number, name, attack, defense
    FROM mypokemon
    ORDER BY 3 DESC, 4;
    # 1: number, 2: name, 3: attack, 4: defense
    # SELECT의 순서에 따라 번호가 매겨짐
    ```

    

  - 순위 만들기

    ```mysql
    # RANK는 항상 ORDER BY와 쓰인다.
    SELECT name,attack,
    RANK() OVER (ORDER BY attack DESC) AS attack_rank
    FROM pokemon.mypokemon;
    # attack_rank라는 새로운 칼럼으로 순위를 보여준다. 
    
    
    ```

    - RANK, DENSE_RANK, ROW_NUMBER 차이점

    ![image](https://user-images.githubusercontent.com/71866756/148578318-0a125a8d-b6b9-4994-9985-b059b51827a0.png)

  

  - 함수의 사용

    - **문자형 데이터 함수**

      괄호 안에 칼럼명을 넣어서 사용하기도 한다. 

      ![image](https://user-images.githubusercontent.com/71866756/148578359-a570ea89-4c02-4a11-9c8b-784129927f33.png)

    - LOCATE

      1. 문자가 여러개라면 가장 앞의 문자의 위치를 가져온다.
      2. 찾는 문자가 없는 경우 0을 가져온다.

      ```mysql
      SELECT 칼럼명, LOCATE('찾는 문자',칼럼명)
      FROM 데이터베이스명.테이블명;
      ```

      

    - SUBSTRING

      1. 만약 입력한 숫자가 문자열 길이보다 크면 아무것도 가져오지 않는다.

      ```mysql
      SELECT 칼럼명, SUBSTRING(칼럼명,3)
      FROM 데이터베이스명.테이블명;
      ```

    - RIGHT, LEFT

      ```mysql
      SELECT 칼럼명, RIGHT(칼럼명,3), LEFT(칼럼명,3)
      FROM 데이터베이스명.테이블명;
      ```

    - CONCAT

      ```mysql
      SELECT 칼럼명, CONCAT(LEFT(칼럼명,1),RIGHT(칼럼명,1)) AS 새로운 칼럼명
      FROM 데이터베이스명.테이블명;
      # 이런식으로 같이 쓰기도 한다. 
      ```

      

    - **숫자형 데이터 함수**

      ![image](https://user-images.githubusercontent.com/71866756/148578405-50b9c488-1a67-4947-ab95-351ad945e45c.png)

    - **날짜형 데이터 함수**

      ![image](https://user-images.githubusercontent.com/71866756/148578466-77eed0f4-12d4-4267-9ca5-24a6fc51bb9a.png)

      - DATE_FORMAT

      ```mysql
      SELECT DATE_FORMAT('1996-11-06 17:34:58','%Y년 %m월 %d일 %H시 %i분 %s초') AS formatted_date;
      ```

      ![image](https://user-images.githubusercontent.com/71866756/148578533-2f82adb5-8bb2-42d4-8561-95be6d65ad38.png)

  - **실습**

    ```mysql
    DROP DATABASE IF EXISTS pokemon;
    CREATE DATABASE pokemon;
    USE pokemon;
    CREATE TABLE mypokemon (
    number INT,
    name VARCHAR(20),
    type VARCHAR(10),
    attack INT,
    defense INT,
    capture_date DATE
    );
    INSERT INTO mypokemon (number, name, type, attack, defense, capture_date)
    VALUES (10, 'caterpie', 'bug', 30, 35, '2019-10-14'),
    (25, 'pikachu', 'electric', 55, 40, '2018-11-04'),
    (26, 'raichu', 'electric', 90, 55, '2019-05-28'),
    (125, 'electabuzz', 'electric', 83, 57, '2020-12-29'),
    (133, 'eevee', 'normal', 55, 50, '2021-10-03'),
    (137, 'porygon', 'normal', 60, 70, '2021-01-16'),
    (152, 'chikoirita', 'grass', 49, 65, '2020-03-05'),
    (153, 'bayleef', 'grass', 62, 80, '2022-01-01');
    
    SELECT name, defense, RANK() OVER(ORDER BY defense DESC) AS defense_rank
    FROM mypokemon;
    
    SELECT name, DATEDIFF('2022-02-14',capture_date) AS days
    FROM mypokemon;
    ```




- **데이터 그룹화하기**

  - GROUP BY

    ```mysql
    SELECT type
    FROM pokemon.mypokemon
    GROUP BY type;			# 같은 타입끼리 묶여서, 나눠진 타입으로 표가 만들어진다.
    ```

    

  - HAVING

    ```mysql
    SELECT type,name
    FROM pokemon.mypokemon
    WHERE type='normal'					# row에 걸리는 조건
    GROUP BY type
    HAVING name LIKE '%u';				# column에 걸리는 조건
    ```

    

  - COUNT

    ```mysql
    SELECT type,name,COUNT(*)			# COUNT(*)는 전체를 의미, 
    									# COUNT 안에 column명을 넣는다,
    									# COUNT(1)은 하나의 값을 1로 센다.
    FROM pokemon.mypokemon
    WHERE type='normal'					# row에 걸리는 조건
    GROUP BY type
    HAVING name LIKE '%u';				# column에 걸리는 조건
    ```

    

  - SUM

    ```mysql
    SELECT type,attack,SUM(attack)		# 합을 구한다.
    FROM pokemon.mypokemon
    WHERE type='normal'					# row에 걸리는 조건
    GROUP BY type
    HAVING attack>0 ;				# column에 걸리는 조건
    ```

    

  - AVG

    ```mysql
    SELECT type,COUNT(1),attack,SUM(attack)		# 합을 구한다.
    FROM pokemon.mypokemon
    WHERE type='normal'					# row에 걸리는 조건
    GROUP BY type
    HAVING COUNT(1)=2 ;					# column에 걸리는 조건
    ```

  - 실습

    ```mysql
    DROP DATABASE IF EXISTS pokemon;
    CREATE DATABASE pokemon;
    USE pokemon;
    CREATE TABLE mypokemon (
    number int,
    name varchar(20),
    type varchar(10),
    height float,
    weight float
    );
    INSERT INTO mypokemon (number, name, type, height, weight)
    VALUES (10, 'caterpie', 'bug', 0.3, 2.9),
    (25, 'pikachu', 'electric', 0.4, 6),
    (26, 'raichu', 'electric', 0.8, 30),
    (125, 'electabuzz', 'electric', 1.1, 30),
    (133, 'eevee', 'normal', 0.3, 6.5),
    (137, 'porygon', 'normal', 0.8, 36.5),
    (152, 'chikoirita', 'grass', 0.9, 6.4),
    (153, 'bayleef', 'grass', 1.2, 15.8),
    (172, 'pichu', 'electric', 0.3, 2),
    (470, 'leafeon', 'grass', 1, 25.5);
    
    SELECT name,type,AVG(weight) 
    FROM pokemon.mypokemon 
    WHERE LENGTH(name)>5 
    GROUP BY type 
    HAVING AVG(weight)>=20 
    ORDER BY AVG(weight) DESC;
    
    SELECT name,type,MIN(height),MAX(height) 
    FROM pokemon.mypokemon 
    WHERE number<200 
    GROUP BY type 
    HAVING MAX(weight)>=10 and MIN(weight)>=2 
    ORDER BY MIN(height) DESC,MAX(height) DESC;
    
    ```

- **규칙 만들기**

  - IF

    ```mysql
    SELECT name, IF(attack>=60,'strong','weak') AS attack_class
    # 조건식이 참이면 'strong', 거짓이면 'weak' 반환
    FROM pokemon.mypokemon
    ```

  - IFNULL

    ```mysql
    SELECT name, IFNULL(name,'unknwon') AS full_name
    FROM pokemon.mypokemon;
    ```

  - CASE

    ```mysql
    SELECT name,
    CASE
    	WHEN attack>=100 THEN 'very strong'
    	WHEN attack>=60 THEN 'strong'
    	ELSE 'weak'
    END AS attack_class
    FROM pokemon.mypokemon;
    
    
    SELECT name,type
    CASE type
    	WHEN 'bug' THEN 'grass'
    	WHEN 'electric' THEN 'water'	# ELSE 없을 시 NULL 반환
    END AS rival_type
    FROM pokemon.mypokemon;
    
    ```

  - CREATE FUNCTION, DROP FUNCTION

    ```mysql
    SET GLOBAL log_bin_trust_function_creators=1;
    # 사용자 계정에 function create 권한 생성
    DELIMITER//
    # 함수의 시작 지정
    
    CREATE FUNCTION getAbility(attack INT, defense INT)
    		RETURNS INT
    BEGIN
    		DECLARE a INT;
    		DECLARE b INT:
    		DECLARE aility INT;
    		SET a=attack;
    		SET b=defense;
    		SELECT a+b INTO ability;
    		RETURN ability;
    END
    //
    DELIMITER;
    # 함수의 끝 지정
    ```

  - 실습

    ```mysql
    DROP DATABASE IF EXISTS pokemon;
    CREATE DATABASE pokemon;
    USE pokemon;
    CREATE TABLE mypokemon (
    number int,
    name varchar(20),
    type varchar(10),
    attack int,
    defense int
    );
    INSERT INTO mypokemon (number, name, type, attack, defense)
    VALUES (10, 'caterpie', 'bug', 30, 35),
    (25, 'pikachu', 'electric', 55, 40),
    (26, 'raichu', 'electric', 90, 55),
    (125, 'electabuzz', 'electric', 83, 57),
    (133, 'eevee', 'normal', 55, 50),
    (137, 'porygon', 'normal', 60, 70),
    (152, 'chikoirita', 'grass', 49, 65),
    (153, 'bayleef', 'grass', 62, 80),
    (172, 'pichu', 'electric', 40, 15),
    (470, 'leafeon', 'grass', 110, 130);
    
    SET GLOBAL log_bin_trust_function_creators=1;
    DELIMITER //
    CREATE FUNCTION isStrong(attack INT, defense INT)
    		RETURNS VARCHAR(20)
    BEGIN
    		DECLARE a INT;
            DECLARE b INT;
            DECLARE answer VARCHAR(20);
            SET a = attack;
            SET b = defense;
            SELECT CASE
    				WHEN a+b>120 THEN 'very strong'
                    WHEN a+b>90 THEN 'strong'
    				ELSE 'not strong'
                    END INTO answer;
    		RETURN answer;
    END
    //
    DELIMITER ;
    
    SELECT name, isStrong(attack, defense) AS isStrong
    FROM mypokemon;
    ```

    

- **테이블 합치기**

  <img src="../../../AppData/Roaming/Typora/typora-user-images/image-20220110223306896.png" alt="image-20220110223306896" style="zoom:67%;" />

  - JOIN

    ```mysql
    SELECT*
    FROM mypokemon
    INNER JOIN ability			
    ON mypokemon.number=ability.number;
    # mypokemon, ability 테이블에서 number가 같은 애들만 합침
    ```

  - LEFT JOIN, RIGHT JOIN

    ```mysql
    SELECT*
    FROM mypokemon
    LEFT JOIN ability			
    ON mypokemon.number=ability.number;
    
    SELECT*
    FROM mypokemon
    RIGHT JOIN ability			
    ON mypokemon.number=ability.number;
    # 알 수 없는 값들은 NULL로 채워진다.
    ```

  - OUTER JOIN

    ```mysql
    #my SQL은 OUTER JOIN이 없어서 LEFT, RIGHT JOIN을 합친다.
    SELECT*
    FROM mypokemon
    LEFT JOIN ability			
    ON mypokemon.number=ability.number;
    UNION			# 두 쿼리의 결과를 중복없이 합친다. 
    SELECT*
    FROM mypokemon
    RIGHT JOIN ability			
    ON mypokemon.number=ability.number;
    ```

  - CROSS JOIN

    ```mysql
    SELECT*
    FROM mypokemon
    CROSS JOIN ability
    # 조합 생각하면 쉽다. mypokemon이 3개의 row, ability가 4개의 row라면
    # 결과는 총 12개의 row로 나온다.
    ```

  - SELF JOIN

    ```mysql
    SELECT*
    FROM mypokemon AS t1
    INNTER JOIN mypokemon AS t2		
    ON t1.number=t2.number;
    # 두 칼럼이 달라도 된다. 
    ```

  - 실습

    ```mysql
    DROP DATABASE IF EXISTS pokemon
    ;
    
    CREATE DATABASE pokemon
    ;
    
    USE pokemon
    ;
    
    CREATE TABLE mypokemon
    (
    
    number INT,
    name VARCHAR(20),
    type VARCHAR(10)
    );
    INSERT INTO mypokemon (number, name, type)
    VALUES (10, 'caterpie', 'bug'),
    (25, 'pikachu', 'electric'),
    (26, 'raichu', 'electric'),
    (133, 'eevee', 'normal'),
    (152, 'chikoirita', 'grass');
    CREATE TABLE ability (
    number INT,
    height FLOAT,
    weight FLOAT,
    attack INT,
    defense INT,
    speed int
    );
    INSERT INTO ability (number, height, weight, attack, defense, speed)
    VALUES (10, 0.3, 2.9, 30, 35, 45),
    (25, 0.4, 6, 55, 40, 90),
    (125, 1.1, 30, 83, 57, 105),
    (133, 0.3, 6.5, 55, 50, 55),
    (137, 0.8, 36.5, 60, 70, 40),
    (152, 0.9, 6.4, 49, 65, 45),
    (153, 1.2, 15.8, 62, 80, 60),
    (172, 0.3, 2, 40, 15, 60),
    (470, 1, 25.5, 110, 130, 95);
    
    SELECT name, attack, defense
    FROM mypokemon
    LEFT JOIN ability
    ON mypokemon.number = ability.number;
    
    SELECT ability.number, name
    FROM mypokemon
    RIGHT JOIN ability
    ON mypokemon.number = ability.number;
    
    
    ```

- **여러 테이블 한번에 다루기**

  - 합집합 (UNION, UNION ALL)

    ```mysql
    # UNION 중복 제외, UNION ALL 중복 포함 
    SELECT name
    FROM mypokemon	# 쿼리 A
    UNION # UNION ALL
    SELECT name
    FROM friendpokemon
    ORDER BY number;
    # query A의 칼럼으로만 정렬 가능
    # UNION의 경우 만약 동일한 이름이지만, 다른 칼럼의 값이 다를 경우, 중복으로 치지 않는다. 
    
    ```

  - 교집합

    ```mysql
    # 교집합을 확인하고 싶은 컬럼 모두 다 기준으로 두고 합쳐야 한다.(단순 INNER JOIN과 차이점)
    SELECT A.name
    FROM mypokemon AS A
    INNER JOIN friendpokemon AS B
    ON A.name=B.name AND A.number=B.number AND A.type=B.type
    ```

  - 차집합

    ```mysql
    SELECT A.name
    FROM mypokemon AS A
    LEFT JOIN friendpokemon AS B
    ON A.name=B.name
    WHERE B.name IS NULL;
    # 조건을 걸어줘야 한다. 
    
    SELECT A.name
    FROM mypokemon AS A
    LEFT JOIN friendpokemon AS B
    ON A.name=B.name AND A.number=B.number AND A.type=B.type
    # 비교할 칼럼 나열 가능
    WHERE B.name IS NULL;
    ```

  - 실습

    ```mysql
    DROP DATABASE IF EXISTS pokemon;
    CREATE DATABASE pokemon;
    USE pokemon;
    CREATE TABLE mypokemon (
    number int,
    name varchar(20),
    type varchar(10),
    attack int,
    defense int
    );
    CREATE TABLE friendpokemon (
    number int,
    name varchar(20),
    type varchar(10),
    attack int,
    defense int
    );
    INSERT INTO mypokemon (number, name, type, attack, defense)
    VALUES (10, 'caterpie', 'bug', 30, 35),
    (25, 'pikachu', 'electric', 55, 40),
    (26, 'raichu', 'electric', 90, 55),
    (133, 'eevee', 'normal', 55, 50),
    (152, 'chikoirita', 'grass', 49, 65);
    INSERT INTO friendpokemon (number, name, type, attack, defense)
    VALUES (26, 'raichu', 'electric', 80, 60),
    (125, 'electabuzz', 'electric', 83, 57),
    (137, 'porygon', 'normal', 60, 70),
    (153, 'bayleef', 'grass', 62, 80),
    (172, 'pichu', 'electric', 40, 15),
    (470, 'leafeon', 'grass', 110, 130);
    
    SELECT distinct type
    FROM mypokemon
    UNION
    SELECT distinct type
    FROM friendpokemon;
    # distinct 안 써도 됨
    
    SELECT number, name, 'my' AS whose
    FROM mypokemon
    WHERE type='grass'
    UNION ALL
    SELECT number, name, "friend's" AS whose
    FROM friendpokemon
    WHERE type='grass';
    ```

- **조건에 조건 더하기**

  - 서브 쿼리

    <img src="../../../AppData/Roaming/Typora/typora-user-images/image-20220110234213674.png" alt="image-20220110234213674" style="zoom:67%;" />

    ( WHERE절의 연산들 )

    ```mysql
    # SELECT절
    SELECT number, name,
    		(SELECT height FROM ability WHERE number=25) AS height
    FROM mypokemon
    WHERE name = 'pikachu';
    
    # FROM절
    SELECT number, height_rank
    FROM (SELECT number.rank() OVER(ORDER BY height DESC) AS height_rank 		FROM ability) AS A
    WHERE height_rank=3;
    
    # WHERE절
    SELECT number
    FROM ability
    WHERE height<(SELECT AVG(height) FROM ability);
    
    SELECT number
    FROM ability
    WHERE height<ALL(SELECT attack FROM ability WHERE type='electric');
    
    SELECT number
    FROM ability
    WHERE defense>ANY(SELECT attack FROM ability WHERE type='electric');
    
    SELECT number
    FROM ability
    WHERE EXISTS(SELECT * FROM ability WHERE type='bug');
    # type이 bug가 하나라도 있으면 TRUE라서 테이블의 모든 number값을 가져온다. 
    ```

  - 실습

    ```mysql
    DROP DATABASE IF EXISTS pokemon;
    CREATE DATABASE pokemon;
    USE pokemon;
    CREATE TABLE mypokemon (
    number INT,
    name VARCHAR(20)
    );
    INSERT INTO mypokemon (number, name)
    VALUES (10, 'caterpie'),
    (25, 'pikachu'),
    (26, 'raichu'),
    (133, 'eevee'),
    (152, 'chikoirita');
    CREATE TABLE ability (
    number INT,
    type VARCHAR(10),
    height FLOAT,
    weight FLOAT,
    attack INT,
    defense INT,
    speed int
    );
    INSERT INTO ability (number, type, height, weight, attack, defense, speed)
    VALUES (10, 'bug', 0.3, 2.9, 30, 35, 45),
    (25, 'electric', 0.4, 6, 55, 40, 90),
    (26, 'electric', 0.8, 30, 90, 55, 110),
    (133, 'normal', 0.3, 6.5, 55, 50, 55),
    (152, 'grass', 0.9, 6.4, 49, 65, 45);
    
    SELECT number
    FROM ability
    WHERE weight = (SELECT MAX(weight) FROM ability);
    
    SELECT number
    FROM ability
    WHERE speed < ANY(SELECT attack FROM ability WHERE type='electric');
    
    SELECT name
    FROM mypokemon
    WHERE EXISTS(SELECT * FROM ability WHERE attack>defense);
    ```

- **응용편**

  ```mysql
  # 데이터 삭제
  DELETE FROM pokemon.mypokemon
  WHERE attack>50;
  
  # 데이터 수정
  UPDATE pokemon.mypokemon
  SET type='normal'
  WHERE name='chikorita'
  # 치코리타의 타입을 normal로 바꾼다.
  ```

  - 제약 조건

    <img src="../../../AppData/Roaming/Typora/typora-user-images/image-20220110235910507.png" alt="image-20220110235910507" style="zoom:67%;" />

    ```mysql
    CREATE TABLE new_mypokemon(
    			number INT PRIMARY KEY,
    			name VARCHAR(20) UNIQUE,
    			type VARCHAR(10) NOT NULL,
    			attack INT DEFAULT 0,
    			defense INT DEFAULT 100,
    			FOREIGN KEY(number) REFERENCES mypokemon(number)
    );
    ```

  - 권한과 DCL

    <img src="../../../AppData/Roaming/Typora/typora-user-images/image-20220111000243223.png" alt="image-20220111000243223" style="zoom:67%;" />

    ```mysql
    # MYSQL 기본 데이터베이스인 mysql 데이터베이스 선택
    USE mysql;
    # 사용자 목록 조회하기
    SELECT user, host FROM user;
    
    # 사용자 생성하기
    CREATE USER 사용자 이름@ip주소;
    # 비밀번호와 함께 사용자 생성하기
    CREATE USER 사용자 이름@ip주소 IDENTIFIED BY '사용자 비밀번호';
    # 사용자 삭제하기
    DROP USER 사용자 이름;
    
    # 권한 부여하기
    GRANT 권한 ON 데이터베이스 이름.테이블 이름 TO 사용자 이름@ip주소
    # 권한 확인하기
    SHOW GRANTS FOR 사용자 이름@ip주소;
    # 권한 삭제하기
    REVOKE 권한 ON 데이터베이스 이름.테이블 이름 FROM 사용자 이름@ip주소;
    # 권한 적용하기
    FLUSH PRIVILEGES;
    
    # 예시 : newuser@%에게 mydb.mytb에 대한 모든 권한 부여하기
    GRANT ALL PRIVILEGES ON mydb.mytb TO newuser@%;
    # 예시1 : newuser@%에게 모든 데이터베이스, 모든 테이블에 대한 SELECT,INSERT 권한 부여하기
    GRANT SELECT,INSERT ON *.* TO newuser@%;
    
    
    ```

  -  트랜잭션과 TCL

    ```mysql
    # 트랜잭션 시작하기
    START TRANSACTION;
    # 트랜잭션 확정하기
    COMMIT;
    # 트랜잭션 이전으로 돌아가기
    ROLLBACK;
    
    # 세이브포인트 만들기
    SAVEPOINT 세이브포인트 이름;
    # 세이브포인트로 돌아가기
    ROLLBACK TO 세이브포인트 이름;
    
    ```

    



