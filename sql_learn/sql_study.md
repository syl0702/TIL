# 1. 데이터 베이스
- 데이터 베이스란 구조화된 데이터의 모임.
- 테이블이라는 정보로 구조화됨.
- 테이블은 행(observation), 열(feature)로 구성.
- 각 테이블은 특정 열(feature)의 조합으로 구성됨.

## 1. 데이터베이스와 서버
- 예시: 전자 상거래 사이트 -> 웹 서버 -> DB 서버
- 고객이 상품 조회를 요청시 페이지에서 웹 서버에 데이터를 요청
- 서버에서 반환한 정보를 우리가 사용하는 페이지에서 확인 가능
- 이 정보들이 DB 서버에 기록됨.

## 2. 서버, GUI
### 1. 서버
- 우리가 사용하는 컴퓨터.
- 특정 목적을 가지는 컴퓨터를 서버라고 부름.
- 클라우드 서비스: 사용자 환경 밖에서 서비스, 컴퓨터 자원을 사용하고, 이에 대한 비용을 지불하는 서비스.
    - 트래픽에 따라 유동적으로 메모리, CPU 등의 자원을 조절할 수 있음.
    - 초기 막대한 인프라 구축 비용을 줄일 수 있음.

# 2. SQL 문법
## 1. SELECT
```sql
SELECT 상품 번호
FROM DB명.PRODUCT;
```

### AVG, SUM, COUNT
```sql
SELECT SUM(AMOUNT),
COUNT(CHECKNUMBER)
FROM CLASSICMODELS.PAYMENTS;
```
### AS: 특정 칼럼의 칼럼 명을 변경해 조회
- classicmodels.products의 productCode의 개수를 구하고, 칼럼 명을 n_products로 변경
```sql
SELECT COUNT(PRODUCTCODE) AS N_PRODUCTS,
COUNT(PRODUCTCODE) N_PRODUCTS
FROM CLASSICMODELS.PRODUCTS;
``` 

### DISTINCT: 중복을 제외하고 데이터 조회
```sql
SELECT DISTINCT 제조 국가
FROM DB 명.상품 테이블;
```

### WHERE: 조건 생성
```sql
SELECT 상품 번호
FROM DB 명.PRODUCT
WHERE 판매 국가 = '미국';
```

### BETWEEN: 조건절에서 자주 사용
```sql
SELECT *
FROM DB 명.테이블 명
WHERE 칼럼 BETWEEN 시작점 AND 2014;
```

### 대소 관계
```sql
SELECT 상품 번호
FROM DB 명.PRODUCT
WHERE 출시 연도 < 2010;
```
- `<>`는 같지 않다는 의미.

### IN
```sql
SELECT CUSTOMERNUMBER
FROM CLASSICMODELS.CUSTOMERS
WHERE COUNTRY IN ('USA', 'CANADA');
```

### NOT IN
```sql
SELECT CUSTOMERNUMBER
FROM CLASSICMODELS.CUSTOMERS
WHERE COUNTRY NOT IN ('USA', 'CANADA')
```
### IS NULL: 특정 값이 비어 있는 데이터 출력
```sql
SELECT EMPLOYEENUMBER
FROM CLASSICMODELS.EMPLOYEES
WHERE REPOSRTSTO IS NULL;
```
### LIKE '%TEXT%'
- 주거지가 부산인 고객 정보 출력하기
```sql
SELECT *
FROM DB 명.CUSTOMERS
WHERE 주소 LIKE '%부산%';
```

### GROUP BY
- classicmodesl.customers 테이블을 이용해 국가, 도시별 고객 수 구하기
```sql
SELECT COUNTRY,
CITY,
COUNT(CUSTOMERNUMBER) N_CUSTOMERS
FROM CLASSICMODELS.CUSTOMERS
GROUP
BY COUNTRY,
CITY
```

### JOIN: 테이블 결합 함수
#### LEFT JOIN(LEFT OUTER JOIN): 특정 테이블 정보를 기준으로 타 테이블을 결합
- ON: 어떤 키값으로 데이터를 결합할지 입력.
```sql
SELECT *
FROM TABLE_A
LEFT 
JOIN TABLE_B
ON TABLE_A.Column 1 = TABLE_B.Column 2
```