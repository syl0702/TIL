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

