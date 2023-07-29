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
    ```
    if <조건식>:
        if 조건이 참인 경우 실행
    elif <조건식>:
        elif 조건이 참인 경우 실행
    ...
    else:
        위의 조건식에 하나도 부합하지 않는 경우 실행```

## 조건 표현식
true_value if <조건식> else false_value
```
print('True) if 1 < 0 else print('False')
```
와
```python
if 1 < 0:
    print('True')
else:
    print('False)
    ```
    
동일한 의미이다.
