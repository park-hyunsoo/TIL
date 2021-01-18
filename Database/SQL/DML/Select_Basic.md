# SELECT
특정 테이블의 칼럼을 조회한다.
```
SELECT [칼럼, 칼럼, ... | * | 표현식 | DISTINCT | AS ]  FROM [TABLE] [WHERE];
```
결과 집합을 흔히 Result Set 이라고 하며 구문 실행 결과 Result Set을 반환한다.
반환 된 행들의 집합을 의미하고 0, 1, 여러 개 행이 될 수도 있다.
테이블에 대한 특정 컬럼, 행에 대한 조회가 될 수 있고 여러 컬럼, 행에 대한 조회가 될 수 있다.

키워드는 보통 대문자로 작성하고 들여 쓰기 등을 해주면 좋다.
마지막에는 ; 를 작성해 주어야 한다. 

# 모든 칼럼 조회 
```
SELECT * 
FROM EMPLOYEE;
```

# 특정 칼럼 조회
```
SELECT EMP_NAME
FROM EMPLOYEE;
```

# 별칭
문자로 시작해야 하고 특수 문자 사용 시 " "를 사용해야 한다. AS는 생략 가능하다.
```
SELECT EMP_NAME AS 이름,
       EMP_NO AS 주민번호,
       SALARY AS "급여(원)",
       DEPT_NO 부서번호
FROM EMPLOYEE;
```

# DISTINCT 
중복 데이터를 제거해 준다.
```
SELECT DISTINCT JOB_ID
FROM EMPLOYEE;
```

# 표현식
컬럼 값에 연산을 할 수 있는데 주의할 것은 컬럼 값에 NULL 이 있으면 연산 시 NULL 이 된다. 
```
SELECT EMP_NAME AS 이름,
       SALARY AS "급여(원)",
       (SALARY + (SALARY * BONUS_PCT)) * 12 AS "연봉(원)"
FROM EMPLOYEE;
```

# 문자열 연결
칼럼 값들을 연결해서 출력할 수 있다.
```
SELECT EMP_NAME || '의' || SALARY
FROM EMPLOYEE;
```

# 더미 컬럼
'' 은 데이터를 의미, ""는 문자열을 의미하고 칼럼을 하나 생성하고 여기에 데이터를 넣어줄 수 있다.
```
SELECT EMP_ID,
       EMP_NAME AS 이름,
       '재직' AS "근무여부"
FROM EMPLOYEE;
```

# WHERE
조건을 부여해서 검색할 수 있고 특정 칼럼, 행에 제한을 줄 수 있다.
```
SELECT *
FROM EMPLOYEE
WHERE DEPT_ID = 90;
```

# 논리 연산자
AND, OR 같은 연산자를 사용할 수 있다.
```
SELECT EMP_NAME,
       DEPT_ID,
       SALARY
FROM EMPLOYEE
WHERE DEPT_ID = 90 AND DEPT_ID = 20;
```

# 연산자
=, >, <, >=, <=, -- <>, !=, ^=
BETWEEN AND,  LIKE / NOT LIKE,  IS NULL / IS NOT NULL, IN

# BETWEEN
상한과 하한의 경계를 포함하고 포함되면 TRUE를 반환
```
SELECT EMP_NAME,
    SALARY
FROM EMPLOYEE
WHERE SALARY BETWEEN 3500000 AND 5500000;

SELECT EMP_NAME,
    SALARY,
FROM EMPLOYEE
WHERE SALARY >= 3500000 
AND SALARY <= 5500000;
```
BETWEEN은 AND로 표현할 수 있다.

# LIKE
비교하려는 값이 지정한 특정 패턴을 만족 시키면 TRUE를 반환, % 임의 문자열, _ 임의 문자 1개
```
SELECT EMP_NAME,
    SALARY
FROM EMPLOYEE
WHERE EMP_NAME LIKE '김%';

SELECT EMP_NAME,
    SALARY
FROM EMPLOYEE
WHERE EMP_NAME NOT LIKE '김%';

SELECT EMP_NAME,
    PHONE
FROM EMPLOYEE
WHERE PHONE LIKE '___9_______';
```

# ESCAPE
LIKE 검색 시 데이터에 _ % 가 포함되어 있고 이 데이터를 사용하려면 ESCAPE를 사용해야 하고 뒤에 나오는 것은 문자로 본다.
```
SELECT *
FROM EMPLOYEE
WHERE EMAIL LIKE '___\_%' ESCAPE '\';
```

# NULL
```
SELECT EMP_NAME, DEPT_ID, BONUS_PCT
FROM EMPLOYEE
WHERE DEPT_ID IS NULL AND BONUS_PCT IS NOT NULL;
```

# IN
OR와 같다.
```
SELECT EMP_NAME,
    DEPT_ID,
    SALARY
FROM EMPLOYEE
WHERE DEPT_ID IN('90', '20');
-- WHERE DEPT_ID IN(90, 20); 자동 형변환이 된다.
```

```
SELECT EMP_NAME,
    SALARY,
    DEPT_ID
FROM EMPLOYEE
WHERE DEPT_ID IN(90, 20) 
AND SALARY > 3000000;
```

# 연산자 우선 순위 
```
SELECT EMP_NAME,
    SALARY,
    DEPT_ID
FROM EMPLOYEE
WHERE (DEPT_ID = 90 OR DEPT_ID = 20)
AND SALARY > 3000000;
```
IN은 ON과 같아서 이렇게 표현할 수 있는데 OR 보다 AND 가 우선순위가 높다 그래서 () 를 사용하면 된다.
