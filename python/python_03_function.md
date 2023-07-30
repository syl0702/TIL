# 함수 (function)
## 함수의 선언과 호출
- 함수의 선언
```python
def func_name(parameter1, parameter2...):
    code1
    code2
    ...
    return value
```
- 함수의 호출(실행)
```python
func_name(parameter1, parameter2)
```
example
```python
def rectangle(height, width):
    area = height * width
    perimeter = (height + width) * 2
    print(f'직사각형의 둘레는 {area}, 면적은 {perimeter}입니다.')
```

## 함수의 return
- 함수가 return을 만나면 해당 값을 반환하고 함수를 종료
- 만약 return이 없다면 None을 자동으로 반환
- return은 오직 하나의 객체만 반환
```python
def my_list_max(list_a, list_b):
    if sum(list_a) > sum(list_b):
        return list_a
    else:
        return list_b
```

## 함수의 인수
### 위치 인수
기본적으로 함수는 인수의 위치로 판단합니다.
```python
def cylinder(r, h):
    return 3.14 * r**2 * h
print(cylinder(10, 5))
print(cylinder(5, 10))
```

### 기본값
```python
def func(p1 = v1):
    return v1
```
- 기본 값을 설정했을 때는 반드시 뒤에 있어야 한다.
```python
def greeting(name = '익명')
    return f'{name}님 반갑습니다.'
print(greeeting('서연'))
print(greeting())
```

example
```python
def greeting(age, name = '익명')
    return f'{name}님은 {age}살 입니다.'
print(greeting(10, '홍길동'))
print(greeting(20))
```
결과 값
```shell
홍길동님은 10살 입니다.
익명님은 20살 입니다.
```

### 키워드 인자
함수를 호출(실행)할 때 내가 원하는 위치에 직접적으로 특정 인자를 전달 가능
example
```python
def greeeting(age, name = '익명'):
    return f'{name}님은 {age}살 입니다.'

print(greeting(10, '홍길동'))
print(greeting(name = '홍길동', age = 10))
```
example2
```python
print('안녕')
print('안녕', '하세요', 'hi', 'hello', sep = '!', end = '?')
```
결과 값
```shell
안녕
안녕!하세요!hi!hello?
```

### 가변 인자 리스트
```python
def funct(*params):
    pass
```
example
```python
def my_print(*words):
    print(words)
    print(type(words))

my_print('hi', 'hello', '안녕', '하세요')
```

example2
```python
def my_max(*numbers):
    result = numbers[0]
    for number in numbers:
        if result < number:
            result = number
    return result
```

### 정의되지 않은 키워드 인자 처리하기
```python
def func(**kwargs):
    pass
```
example
```python
def fake_dict(**kwargs):
    for key, value in kwargs.items():
        print(f'{key}는 {value}입니다.')

fake_dict(korean = '안녕', english = 'hello')
```
결과값
```shell
korean는 안녕입니다.
english는 hello입니다. 
```

### 딕셔너리를 인자로 넣기(unpacking)
example
```python
def sign_up(username, password, password_confirmation):
    if password == password_confirmation:
        print(f'{username}님 회원가입이 완료되었습니다.')
    else:
        print(f'비밀번호가 일치하지 않습니다.')


my_account = {
    'username': 'asdf1234',
    'password': '1q2w3e4r',
    'password_confirmation': '1q2w3e4r',
}

sign_up(**my_account)
```

### lambda 표현식
```python
lambda parameter: expression
```
- 효율성이 떨어지지만 알고리즘 테스트 등에서 간단한 표현을 위해 사용하는 편.
example
```python
(lambda a, b: a + b)(1, 2)
```
- 같은 속성끼리 더할 수 있다.

### 타입 힌트
```python
def my_sum(num1: int, num2: int) -> int:
    '''
    두 수의 합을 구하는 함수입니다.
    매개변수 num1, num2를 받아서 num1 + num2를 리턴합니다.
    '''
    return num1 + num2

my_sum(1, 2)
```
### 이름공간 (scope)
파이썬에서 사용되는 이름들은 이름공간(namespace)에 저장되어 있습니다.
- Local space : 정의된 함수 내부
- Enclosed scope : 상위 함수
- Global scope : 함수 밖의 변수 혹은 import된 모듈
- Build-in scope : 파이썬이 기본적으로 가지고 있는 함수 혹은 변수

example
```python
a = 1
def localscope(a):
    print(a)
localscope(5)
```
결과
```shell
5
```
example2
```python
num = 10
def scope():
    global num
    num = 20
    print(num)

scope()
print(num)
```
결과값
```shell
20
20
```
### 재귀 (recursive)
재귀 함수는 함수 내부에서 자기 자신을 호출하는 함수를 의미한다.
```python
# 팩토리얼
def fact(n):
    result = 1

    while n > 1:
        result = result * n
        n = n - 1
    
    return result
```

```python
def factorial(n):
    if n <= 1:
        return 1
    else:
        return factorial(n-1) * n

factorial(5)
```

### 피보나치 수열
F(0) = F(1) = 1
F(n) = F(n-1) + F(n-2)

```python
# 반복문
def fib_loop(n):
    result = [1, 1]

    for i in range (1, n):
        end1 = result[-1]
        end2 = result[len(result)-2]
        fib_num = end1 +end2

        result.append(fib_num)
    return result[-1]

fib_loop(10)
```

```python
# 재귀문
def fib_rec(n):
    if n == 0 or n == 1:
        return 1
    else:
        return fib_rec(n-1) + fib_rec(n-2)

fib_rec(10)
```