# 오답 노트
- `.sort()`는 해당 함수 자체를 바꾸기 때문에 `function.sort`를 호출하면 None이 나온다.
- `.reverse()` 또한 마찬가지.
## 1차원을 2차원으로 변환하기
- num_list를 n개씩 묶인 2차원 배열로 만들고자 함.
```python
num_list = [1, 2, 3, 4, 5]
answer = []
for i in range(0, len(num_list), n)
    answer.append(num_list[i:i+n])
```

## 369 게임
- 3, 6, 9 숫자가 나올 때마다 박수 쳐야 할 때 order에 따른 횟수 구하기
- solution으로 주어지는 변수에 대해 반드시 타입을 파악해야!
- `in`을 사용하기 위해서는 `string`이어야 하므로 `str(order)`로 변환이 필수적.
```python
for num in str(order):
    if num in ['3', '6', '9']:
        answer += 1
```

## 모스부호
- `.split()`은 **문자열**에서 사용 가능하다.
- dictionary와 list를 비교
```python
for i in range(len(temp)):
    for key in list(morse.keys()):
        if temp[i] == key :
            answer += morse[key]
```

## 배열 회전시키기 **중요**
- [1,2,3,4,5]에 대해 오른쪽으로 한 칸 씩 옮기기
- slicing을 통해 해결 가능.
```python
if direction == "right":
    answer = [numbers[-1]] + numbers[:-1]
elif dirction == "left":
    answer = numbers[1:] + [numbers[0]]
```
## 공 던지기 (위와 같은 유형)
- 회전 할 때 slicing을 가장 먼저 생각해볼 것
```python
temp = []
    if len(numbers) % 2 == 0:
        players = numbers[0::2]
    else:
        players = numbers[0::2] + numbers[1::2]

    answer = players[k % len(players) -1]
    
    return answer
```

## 문자열 밀기(같은 유형)
- 다시 풀 것
- 회전하면서 계속 잘라 붙이기
```python
def solution(A, B):
    
    i = 0
    if A == B:
        return 0
    else:
        while i < len(A):
            i += 1
            A = A[-1] + A[:-1]
            if A == B:
                return i
    return -1
```

## 피자 나눠먹기 (2)
- n명이 모두 같은 수의 피자를 먹을 수 있게 하는 피자 판의 수.
- 최소 공배수 이용!
```python
for i in range(max(n, 6), n*6+1):
    if i % n == 0 and i % 6 == 0:
        answer = int(i/6)
        return answer
```

## 합성수 찾기
- 10까지의 수 중에서 합성수 찾기!
- 약수가 3개 이상인 수들을 세야 함.
```python
for num in range(n+1):
    count = 0
    for i in range(1, num+1):
        if num % i == 0:
            count += 1
    if count >= 3:
        answer += 1
return answer
```

## 자연수 뒤집어 배열로 (**빈출**)
- 12345라는 정수가 주어지고 이를 뒤집은 배열로 만들어야 함.
- 12345 자체를 문자열로 인식 시킨 뒤 각각에 대해 int 적용을 시켜서 `list`로 만들어야 한다.
```python
temp = list(map(int, str(n)))
temp.reverse()
answer = temp

return answer
```

## 숨어있는 숫자의 덧셈(2)
- 연속된 숫자를 리스트로 추출하기 위한 새 함수.
```python
import re
numbers = my_string
numbers = re.findall(r'\d+', numbers)
numbers = list(map(int, numbers))
answer = sum(numbers)
```

## 가까운 수 
- **다시 풀 것**
- 가장 처음에 할 것은 분류!
- 분류를 통해 가장 작은 값부터 적용하여 자연스럽게 절대 값은 같지만 더 작은 수를 택하게 만든다.
```python
def solution(array, n):
    answer = 0
    array.sort()
    # print(array)
    k = 1000
    for num in array:
        if abs(num - n) < k:
            k = abs(num - n)
            answer = num
    return answer
```

## k의 개수 
- **다시 풀 것**
- 있는지 없는지를 간단히 확인 후 세는  방법을 사용할 것.
- 각 변수가 문자인지 숫자인지 등을 파악 필요
```python
def solution(i, j, k):
    answer = 0
    for n in range(i, j+1):
        if str(k) in str(n):
            answer += str(n).count(str(k))
    return answer
```

## 내적 (다시 풀기)
- 두 리스트 간의 곱
- zip으로 해결
```python
temp = [x*y for x,y in zip(a, b)]
```

## 진료 순서 정하기 (다시 풀기)
- sort한 list를 새로 만들고 이를 역순으로 배치.
이후 그 리스트의 index에 +1한 것을 빈 리스트에 삽입.
```python
emergency_set = sorted(emergency)
    emergency_set.reverse()
    for i in emergency:
        
        answer.append(emergency_set.index(i)+1)
    return answer
```
## 한번만 등장한 문자 (다시)
- 각 문자별로 갯수를 구하고 이에 따라 조건을 만들어 주면 됨.
```python 
s1 = sorted(s)
    for i in s1:
        if s1.count(i) == 1:
            answer += i
```

## 이진수 더하기
- 십진수 만드는 법 기억하기
- `int(변수, 2)`
- 이진수로 만들기는 `bin(a)`.
- slicing 활용력 높이기

## 3진법 뒤집기
- 이진수와는 다르게 직접 코드를 짜야 함.
- 몫과 나머지를 구하는 `divmod(a, b)` 필요.
```python
def solution(n):
    answer = 0
    three_base = ''
    while n > 0:
        n, mod = divmod(n, 3)
        three_base += str(mod)
    print(three_base)
    answer = int(three_base, 3)
    return answer
```

## 컨트롤제트 (다시 풀기)
- `.split()`: 띄어쓰기에 맞춰서 문자열을 나누어 줌.
- `.pop()`은 마지막 항목 삭제
```python
s1 = s.split()
    for n in s1:
        if n == 'Z':
            temp.pop()
            continue
        
        temp.append(int(n))
    answer = sum(temp)
```

## 소인수 분해
- 소수로 구성되어야 하며 중복되는 값은 리스트에 포함되지 말아야 한다.
- 소수로 나눈 뒤의 몫에서 다시 새로 나누어야 함.
```python
d = 2
    while d <= n:
        if n % d == 0:
            if d not in answer:
                answer.append(d)
            n = n / d
        else:
            d += 1
    return answer
```

## 7의 개수
- array은 현재 list.
- array 각 항목을 str로 변환 하고 이를 모두 붙여야 한다.
- 이후 문자열이 된 곳에 `count`를 사용하면 답이 나올 수 있다.
```python
 a = ''.join(map(str,array))
    answer = a.count('7')
    return answer
```
## 약수의 개수와 덧셈
- 다시 풀 것
- 리스트를 새로 만들어서 이후 갯수를 세기 보다는 바로 갯수 세는 것 연습 필요
- 범위의 의미를 스스로 인지하고 코드를 써야 함.
```python
for n in range(left, right+1):
        count = 0
        for i in range(1, n+1):
            if n % i == 0:
                count += 1
        if count % 2 == 0:
            answer += n
        else:
            answer -= n
```

## 잘라서 배열로 저장하기
- 다시 풀것
- range도 띄어서 볼 수 있음
```python
for i in range(0, len(my_str), n):
        answer.append(my_str[i:i+n])
    return answer
```

## 영어가 싫어요
- 다시 풀것
- enumerate() 복습
- 이미 있는 리스트에 **대체**하는 방법도 기억할 것.
```python
def solution(numbers):
    alph_num = ['zero', 'one', 'two','three', 'four', 'five', 'six', 'seven', 'eight', 'nine']
    for key, value in enumerate(alph_num):
            numbers = numbers.replace(value, str(key))
            
    return int(numbers)
```

## 문자열 계산하기
- 다시!
- eval() 함수 기억하기
- eval 없이 푸는 법도 기억
```python
def solution(my_string):
    my_strings = my_string.split()
    answer = int(my_strings[0])
    for i in range(1, len(my_strings),2):
        if my_strings[i] == '+':
            answer += int(my_strings[i+1])
        else:
            answer -= int(my_strings[i+1])
    
    return answer
```

## 외계어 사전
- 다시 풀 것.
- sort해서 서로 비교하기!
- 나중에 set로도 시도해볼 것.
```python
def solution(spell, dic):
    answer = 0
    for d in dic:
        if sorted(d) == sorted(spell):
            return 1
        else:
            answer = 2
    return answer
```

## 캐릭터의 좌표
- 이전의 좌표에 대한 기본 컨셉.
- 제한치를 먼저 설정하고 그것에 적합할 경우에만 실행될 수 있게 해야.
- 겁 먹지 말기.
```python
def solution(keyinput, board):
    answer = []
    x, y = 0, 0
    xlim = board[0]//2
    ylim = board[1]//2
    
    for key in keyinput:
        if key == "right":
            if x >= xlim:
                x = xlim
            else:
                x += 1
        elif key == "left":
            if x <= -xlim:
                x = -xlim
            else:
                x -= 1
        elif key == "up":
            if y >= ylim:
                y = ylim
            else:
                y += 1
        elif key == "down":
            if y <= -ylim:
                y = -ylim
            else:
                y -= 1
    answer = [x, y]
```

## 로그인 성공?
- 다시 풀 것
- return과 answer의 차이 명확하지 않음.
- 왜 특정 사례에서만 실패가 뜨는지 모르겠음.


## 등수 매기기
- 다시 풀 것
- 순위 매기는 것에 대한 논리 숙지 할 것! (**빈출**)
```python
for i in range(len(score)):
        temp.append(sum(score[i]) / 2)
        sorted_temp = sorted(temp, reverse = True)
        answer = [sorted_temp.index(s)+1 for s in temp]
```

## 치킨 쿠폰
- 다시 풀 것
- 규칙 잘/빠르게 파악해야 함.

## 유한 소수 판별하기
- 다시 풀 것
- return과 answer 정의한 후 return이 여전히 헷갈림. 질문 필수

## 저주의 숫자 3
- 다시 풀 것
- while과 if문의 차이에 대한 설명을 들어야 할 듯

## 특이한 정렬
- 다시 풀 것!
- `lambda x:`에 대한 개념 공부!
- `lambda x:` 이후의 기준을 통해 리스트가 정렬될 수 있다.
- **중요**
```python
def solution(numlist, n):
    answer = sorted(numlist, reverse = True)
    answer = sorted(numlist, key = lambda x: (abs(n-x), n-x))
    return answer

print(solution([1, 2, 3, 4, 5, 6], 4))
```
- 4를 기준으로 차이가 적게 나는 순서로 배열하기.

## 다항식 더하기
- **다시 풀 것**
- `.isnumeric()` 사용 필요!
- 각각의 타입과 원리 기억할 것!
- x 연산과 n의 연산을 따로 만들어야 함.

## 비밀지도
- 질문 필수!
- 리스트를 n개씩 나누는 코드 이해 필요(39번째 줄)
- 띄어쓰기가 안 보여서 그냥 두 칸으로 했는데 왜 정답이 되었는지 답변 필요.

## 두 개 뽑아서 더하기
- 질문 필수!
- 내가 한 sol2.py에서 어떤 문제가 있어서 예외 케이스가 발생하는지 답변 필요

## 최빈값 구하기
- 다시 풀어 보는 것이 좋음
- dictionary와 최댓값이 여러 개일 때의 코드 기억해 두어야 함.
```python
temp1 = [k for k,v in a_dict.items() if max(a_dict.values()) == v]
```

## 소수 만들기
- 다시 풀 것.
- 한 함수 안에 들어갈 수 없다면 새로운 함수를 만들고 적용시키는 연습 필요!

## 실패율
- 다시 풀 것.
- 한 기준점으로 해결이 되지 않는다면 다른 것을 기준으로 잡아서 시도할 것.
- lambda 연습 필수.

## 다트 게임
- 다시 풀 것.
- 문제 길이에 겁내지 말고 무엇을 해야 하는 지에 집중 할 것.
- 10의 경우 replace를 통해 문자화 한 뒤에 temp에 추가할 때 숫자로 재전환 시키는 방법 생각 할 것.

## 안전지대
- 다시 풀 것.
- 좌표 값을 dx, dy로 나누어서 표현.
- 범위 정의 주의!
