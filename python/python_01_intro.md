# 01. Intro

## 단축키
- `ctrl + enter` : 지금 셀 실행
- `shift + enter` : 지금 셀 실행 & 아래로 이동
- `alt + enter` : 지금 셀 실행 & 아래에 새로운 셀 추가
- `ctrl + /` : 주석

## 주의 사항
1. Apple/apple은 다르다.
2. git add ./git add.는 다른 명령어이다.
3. message/massage는 다르다.
<!-- 주석을 나타냄 -->

# 1. 변수
변수 이름 = 값
- 변수 이름은 어떤 이름이든 상관 없음.
- 다만 영어, 숫자, _를 이용하여 선언.
- 키워드는 사용 불가

## 1.1 Number
- integer : 정수 e.g. 100000
- float : 실수 e.g. 1.1
- complex : 복합 e.g. 1-4j
    - c.imag : 허수부
    - c.real : 실수부

## 1.2 Boolean
True, False로 이루어진 타입

## 1.3 None
공백

## 1.4 String
- 문자열은 `'`, `"`를 이용하여 표현
- 단, 통일성을 위해 둘 중 하나를 택하여 사용할 것
- 중복하여 `'`를 사용할 때에 하나를 `"`로 사용하거나 앞 뒤에 `\'`를 사용.
    - e.g. print('안녕하세요? \'이서연\' 입니다.')
- `\n` : 다음 줄
- `\t` : 들여쓰기
- `sep = '\t\` : 나열되어 있는 항목의 구별이 들여쓰기를 통해 구성됨.

### string interpolation
1. %-formatting e.g. print('홍길동은 %s 살입니다.' % age) 
2. str.format() e.g. print('홍길동은 {}살입니다.' .format(age))
3. f-string e.g. print(f'홍길동은 {age}살입니다.')

# 2. 연산자
## 2.1 산술 연산자
- `print(a + b)` : a에서 b 더하기
- `print(a - b)` : a에서 b 빼기
- `print(a * b)` : a 곱하기 b
- `print(a / b)` : a 나누기 b
- `print(a ** b)` : a의 b 거듭제곱
- `print(a // b)` : a를 b로 나눈 몫
- `print(a % b)` : a를 b로 나눈 나머지
- `print(divmod(a,b))` : a를 b로 나눈 몫과 나머지

## 2.2 비교 연산자
- `print(a > b)`
- `print(a < b)`
- `print(a >= b)`
- `print(a <= b)`
- `print(a == b)`
- `print(a != b)`

## 2.3 논리 연산자
- `and` : 양쪽 모두 True일 때, True를 반환
- `or` : 양쪽 모두 False일 때, False를 반환
- `not` : 값을 반대로 전환

### 단축평가 (and)
- 두 숫자가 나왔을 때 이를 TF처럼 인식하여 결과값을 내는 방법.
- `and`의 경우 앞이 F이면 무조건 F이지만, 앞이 T라면 뒤의 값을 파악해야 함.
- 그에 따라 파이썬에서는 앞에 0이 나왔을 때는 무조건 그 값인 0을 출력하고 0이 아닌 숫자가 나왔을 때는 뒤의 값이 결정한다고 인식하여 뒤의 값을 출력하게 됨.
`print(3 and 5)` : 5 출력
`print(3 and 0)` : 0 출력
`print(0 and 5)` : 0 출력
`print(0 and 0)` : 0 출력

### 단축평가 (or)
- `or`의 경우 앞이 T면 무조건 T가 나오고 앞이 F면 뒤의 값에 따라 결정되어 출력된다.
`print(3 and 5)` : 3 출력
`print(3 and 0)` : 3 출력
`print(0 and 5)` : 5 출력
`print(0 and 0)` : 0 출력

## 2.4 복합연산자
`a = a + b` : a += b
`a = a - b` : a -= b
`a = a * b` : a *= b
`a = a / b` : a /= b
`a = a // b` : a //= b
`a = a % b` : a %= b
`a = a ** b` : a **= b

## 2.5 기타 연산자
- concatenation (순차)
`a = 'hi' b= 'hello'일 때 a+b` : hihello 출력

- containment (포함) : in
`print ('a' in apple)` : True 출력

- identity
```python
a = 1
b = 1
print(a is b)
print(id(a))
print(id(b))
```
 - 이 경우 True와 함께 둘의 id는 일치하는 것으로 나옴.
 - 0~256까지의 숫자들은 파이썬 내부에 저장되어 있어서 id가 지정되어 있음.

```python
a = 123123
b = 123123
print(a is b)
print(id(a))
print(id(a))
```
   - 이 경우 **False**가 생성됨. 둘의 id는 별개로 나옴.
   - 파이썬 내부에 저장된 숫자가 아니기 때문에 숫자를 호출할 때마다 id가 새로 생성되는 것.


### 우선순위
0. ()를 통해 그룹
1. **
2. 산술연산자 (*,/)
3. 산술연산자 (+.-)
4. 비교연산자, in, is
5. not
6. and
7. or

# 3. 형 변환
## 3.1 암시적 형 변환
```python
a = True
b = False
c = 1
print(a+c)
print(b+c)
```
: 2와 1 출력
- True와 False를 각각 1과 0으로 인식하여 계산함.

## 3.2 명시적 형 변환
- int() : string, float를 int로 변환
- float() : string, int를 float로 변환
- str() : int, float 등을 string으로 변환
- bool() : int, list 등을 boolean으로 변환

# 4. 시퀀스(Sequence) 자료형
시퀀스는 데이터의 순서대로 나열된 자료 구조. (순서대로 나열되었다는 것은 정렬된 것과 다르다)
1. 리스트
2. 튜플
3. 레인지
4. 문자열

## 4.1 List
- 선언 : 변수이름 = [value1, value2, value3 ...]
- 접근 : 변수이름[index]
- 컴퓨터에서는 늘 **0**이 시작 지점이라는 것을 잊지 말기!
- 이미 location에 '서울', '대구', '대전'이 있을 때, `location[1] = '부산'`이라고 한 뒤 출력하면 '서울', '부산', '대전'으로 수정됨.

## 4.2 Tuple
- 선언: 변수이름 = (value1, value2, value3)
- 접근 : 변수이름[index]
- 리스트와 유사하지만 수정이 불가능(immutable)하다.
- 수정이 불가능하다는 것은 .append/rm 등이 불가능함을 의미.

> ### Tips
> 리스트와 튜플 차이 알아보기 [list and tuple](https://bigdaheta.tistory.com/8)


## 4.3 range
- range(n) : 0부터 n-1까지 범위
- range(n, m) : n부터 m-1까지 범위
- range(n, m, s) : n부터 m-1까지 +s만큼 증가하는 범위

## 4.4 String
기본 데이터 구조 참고

## 4.5 시퀀스에서 활용 가능한 연산/함수
- indexing : 호출
- slicing : a 이상 b 미만의 수 호출
    ```python
    my_list = [1, 2, 3, 4, 5]
    my_tuple = (1, 2, 3, 4, 5)
    my_range = range(1, 100)
    my_string = '12345'

    print(my_list[1:3])
    print(my_tule[1:3])
    print(my_range[1:3])
    print(my_string[1:3])
    ```
 - 결과 값 각각 [2, 3]/(2,3)/range(2,4)/23

- slicing (k 간격으로)
    ```python
    list(my_range[2:6:2])
    ```
 - 결과 값 [3, 5]

- `len` : 항목의 길이 (갯수)
- `min` : 항목에서의 최솟값
- `max` : 항목에서의 최댓값
- `func.count(n)` : func에서 n이라는 항목이 몇 번 나왔는지 횟수 호출

# 5. 시퀀스 데이터가 아닌 자료 구조
## 5.1 Set
수학에서 사용하는 집합과 동일하게 처리 (중복된 값이 없음)
- 선언: 변수이름 = {value1, value2, value3...}
- `-` : 차집합
- `|` : 합집합 (중복은 나타나지 않음)
- `&` : 교집합

## 5.2 Dictionary
- 선언 : 변수이름 = {key1:value1, key2:value2,...}
- 접근 : 변수이름[key]
- dictionary는 key와 value가 쌍으로 이루어져 있다.
- key에는 immutable한 모든 것을 사용 가능 (불변값: string, integer/자료형)
- value에는 모든 데이터 가능(list, dictionary도 가능)

# 데이터 타입
1. Number
2. Boolean
3. String

# 자료구조
- 시퀀스 자료형
1. [List] : mutable
2. (Tuple) : immutable
3. range() : immutable
4. 'String' : immutable
> ### Tips
> Mutable과 Immutable 더 알아보기 [mutable과 immutable] (https://velog.io/@chobe1/%ED%8C%8C%EC%9D%B4%EC%8D%AC-%EA%B8%B0%EC%B4%88-Mutable-vs-Immutable-Objects)

- 시퀀스가 아닌 자료형
1. {Set} : mutable
2. {Dictionary} : mutable