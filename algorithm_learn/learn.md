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