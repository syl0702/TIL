# 제어문
## 조건문 (if문)
1. `if`문은 반드시 일정한 참/거짓을 판단할 수 있는 `조건식`과 함께 사용한다. (`if <조건식>:`)
2-1. `<조건식>`이 참인 경우 `:` 이후의 문장을 실행한다.
2-2. `<조건식>`이 거짓인 경우 `else:` 이후의 문장을 실행한다.

### if문
    if <조건식>:
        if의 조건식이 참인 경우 실행하는 코드
    else:
        if의 조건식이 거짓인 경우 실행하는 코드

- `func = input`의 경우 input은 문자로 인식되기 때문에 숫자 입력임을 확인하기 위해서는 `func = int(input())`로 정의를 시작해야 함.

### elif
``` python  
if <조건식>:
        if 조건이 참인 경우 실행

elif <조건식>:
        elif 조건이 참인 경우 실행
    ...

else:
        위의 조건식에 하나도 부합하지 않는 경우 실행
```

## 조건 표현식
`true_value if <조건식> else false_value`

```python
print('True') if 1 < 0 
else print('False')
```
와

```python
if 1 < 0:
    print('True')
else:
    print('False)
```

는 같은 의미다.

## 반복문
### while 문
```python
while <조건식>:
        실행할 코드
```
예시
```python
a = 0

while a < 5:
    print(a)
    a += 1
```
### for
정해진 범위 내의 반복 (작업량을 할당)
```python
for variable in sequence:
    code
```
example
```python
numbers = [1, 2, 3, 4, 5]
for number in numbers:
    print(number)
```

example 2
```python
# for문을 사용해서 사용자가 입력한 데이터를 한 글자씩 출력하는 코드
word = input('단어를 입력하세요: ')

for char in word:
    print(char)
```

example 3
```python
#  1~30까지 숫자 중에서 홀수만 담긴 리스트 출력
numbers = range(31)
result = []

for number in numbers:
    if number % 2 == 1:
        result.append(number)
print(result)
```

example 4
```python
menus = ['라면', '김밥', '돈까스']
for idx, menu in enumerate(menus):
    print(idx)
    print(menu)
```
> ### Tips
> enumerate 함수란? [enumerate 함수] (https://www.entity.co.kr/entry/512-%ED%8C%8C%EC%9D%B4%EC%8D%AC%EC%9D%98-Enumerate-%ED%95%A8%EC%88%98-%EB%A3%A8%ED%94%84-%ED%8A%9C%ED%94%8C-%EB%AC%B8%EC%9E%90%EC%97%B4
)

## dictionary 반복
1. for key in dict:
2. for key in dict.keys():
3. for value in dict.values():
4. for key, value in dict.items():

- for key in dict:
```python
info = {
    'name' : 'seoyon'
    'location': 'seoul'
    'phone' : '010-2222-2222'
}

for i in info:
    print(i)
    print(info[i])
```
결과 값:
```shell
name
seoyon
location
seoul
phone
010-2222-2222
```
- for key in dict.keys():
```python
blood_type = {
    'A' : 5,
    'B' : 4,
    'O' : 2,
    'AB' : 3,
}

print('혈액형 목록은 다음과 같습니다.')
for key in blood_type:
    print(key)
```

- for value in dict.values()
```python
result = 0

for value in blood_type.values():
    result = result + value
print(f'총 인원은 {result} 명 입니다.')
```

- for key, value in dict.items()
```python
for key, value in blood_type.items():
    print(f'{key}는 {value}명 입니다.')
```

- dict.items()
```python
blood_type.items()
```
결과값
```shell
dict_items([('A', 5), ('B', 4), ('O', 2), ('AB', 3)])
```

## break
반복문을 종료 시키는 키워드
example
```python
for i in range(100):
    if i > 10:
        print('10 넘었어')
        break
    print(i)
```

example 2
```python
rice = ['보리','보리','보리','쌀','보리','보리']

for r in rice:
    if r == '쌀':
        print('잡았다!')
        break
    print(r)
```

## continue
continue 이후의 코드를 실행하지 않고 다음 반복을 진행.

example
```python
for i in range(10):
    if i % 2:
        continue
    print(i)
```

example 2
```python
age = [10, 35, 20, 18, 9, 40]

for a in age:
    if a > 20:
        continue
    print('성인입니다.')
```

## else
else문은 끝까지 반복이 진행된 후 실행됩니다.
example
```python
for i in range(100):
    if i > 100:
        break
    print(i)
else:
    print('break 못 만남')
```

example 2
```python
numbers = [1, 3, 5, 7, 9]
target = 11

for number in numbers:
    if number == target:
        print('True')
        break
else:
    print('False')
```

## pass
```python
if True:
    pass
```

## match
```python
match value:
    case 조건:
        code
    case 조건:
        code
    case _:
        code
```

example
```python
status = 404

match status:
    case 400:
        print('Bad Request')
    case 404:
        print('Not Found')
    case _:
        print('Something is Wrong)
```