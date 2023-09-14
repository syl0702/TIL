# Machine Learning 관련 기록
## 회귀식
1. 회귀식은 기본 지식적인 것으로 실제로 많이 쓰이지는 않는다.
2. 2~4차 다항식 이상은 과적합이 될 가능성이 높다.
3. MAE와 MSE 중 후자가 수학적으로 표현이 옳다.
- 수학적으로 오류 항목은 서로 아무 관련 없는 쪽이 더 좋다는 것 참고.

### 데이터의 전체적인 흐름 알아두기
1. 데이터를 로드
```python
df = pd.read_csv('./data/example.csv')
```

2. 데이터 전처리: 전처리를 위해 x_data와 y_data를 정의할 것.
    - `train_test_split()`을 통해 일정 비율로 나누어 줘야 함.
        - 이때, 분류의 경우에는 `stratify`가 필요할 수 있다.
        - `stratify`는 test와 train으로 나눌 때 샘플이 한 쪽으로 편향되지 않게 도와준다.
    - `sklearn.preprocessing`에서 필요한 것을 import

3. 모델 생성: `KNeighborsClassifier` 등의 모델을 생성해야 함.

4. 이후 이 모델에 x_train 및 y_train을 훈련 시킨다.
```python
result = model.fit(x_train, y_train)
```

5. 모델 검증
`model.score()`을 통해 train과 test를 각각 검증한다.
- 일반적으로 train과 test는 어느 정도의 차이가 나며, train과 test가 너무 다를 경우에는 test sample이 train에 이미 들어 있었을 가능성을 의심하고 이를 피해야 한다.

6. 개발 이후 모델 예측
- x 실제 값을 부여하고 y의 예측값을 알아본다.

### 이상치 처리
1. boxplot을 통해 이상치의 위치 등을 파악하고,
2. rev_range 즉 제거 범위 조절 변수를 변경해 가며 box_plot이 원하는 대로 깨끗해 지는 것을 테스트 해야 한다.

### 인코딩
문자열로 구성된 데이터를 숫자로 라벨링하는 작업.
#### 레이블 인코딩
1. `from sklearn.preprocessing import LabelEncoder,OrdinalEncoder` 사용
2. LabelEncoder를 객체로 생성 후 fit과 transform으로 label 인코딩
3. 이 객체로 생성한 후에 **절대** 실제 데이터에서 fit을 사용해서는 안된다. Only `transform`만 호출해야 같은 객체를 사용할 수 있음!!
4. `.apply()` 함수로 특정 함수를 일괄 적용할 수 있다.
```python
le = LabelEncoder()
train_df['item_label'] = train_df[['item']].apply(le.fit_transform)
train_df
```