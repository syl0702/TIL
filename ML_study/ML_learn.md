# Machine Learning 관련 기록
## 회귀식
1. 회귀식은 기본 지식적인 것으로 실제로 많이 쓰이지는 않는다.
2. 2~4차 다항식 이상은 과적합이 될 가능성이 높다.
3. MAE와 MSE 중 후자가 수학적으로 표현이 옳다.
- 수학적으로 오류 항목은 서로 아무 관련 없는 쪽이 더 좋다는 것 참고.
4. r 계수에 대한 결정은 domain 지식이 필요하다.
- 예를 들어 소득 별로 정치적 지향성을 판단하는 것은 회귀 계수가 맞기 힘들다.
- 따라서 r 계수 혹은 도메인 지식이 필요.

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
3. 결측값 제거는 항상 하는 것이 좋지만, 중복값 제거는 신중해야 한다.
4. test 파일의 경우 의도된 것이라면 결측값이나 중복값 등의 제거는 안하는 것이 좋다.

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

### 분류 결정 임곗값
- Recall와 Precision 서로 trade-off이다.
- Threshold 낮추면 Positive로 예측될 확률이 커짐 -> Recall이 높아진다.
- Threshold 높으면 Negative로 예측될 확률이 커짐 -> FP 감소/잘 맞춘 TP도 낮아질 수 있다 -> Precision이 높아진다. 이때 전반적으로 작아질 수 있다.

- FP를 0으로 만들면 정밀도 100%가 됨. -> Threshold 1.0으로 확 높이기.
- 확실하지 않으면 0으로 예측함.

- Threshold 0으로 만들면 재현율 100% 됨.
- 음성으로 잘못 예측한게 없어짐. TP랑 FP가 쭉 올라감.
- FP 올라가면 정밀도는 낮아지고 재현율 높아져.

## 앙상블
- 여러 모델들을 함께 사용하는 방법
- Voting, Bagging, Boostingdl 있음
- Bagging 대표적 예시는 랜덤 포레스트
- 단일 모델의 약점을 다수의 모델들을 결합하여 보완.
- 성능이 떨어지더라도(과대적합/과소적합) 서로 다른 유형의 모델을 섞는 것이 오히려 전체 성능에 도움이 됨.
- Voting, Bagging은 여러 개의 분류기가 투표를 통해 최종 예측 결과를 결정하는 방식
- Voting은 서로 다른 알고리즘을 가진 분류기를 결합
- Bagging은 같은 알고리즘을 가진 분류기를 결합하지만 데이터 샘플링을 서로 다르게 수행하여 Voting 수행
- Soft Voting은 predic_proba 가지고 있는 모델들만 가능하다.
- Hard Voting은 어디든 다 가능

### Random Forest
- n_estimators: 랜덤 포레스트에서 결정 트리의 개수를 지정. 기본은 100개
    - 이것만 조절하는 것 추천
- max_features
- max_depth, min_samples_leaf

### Boosting
- 약한 학습기를 순차적으로 학습-예측한 데이터나 학습 트리에 **가중치 부여**를 통해 오류를 개선해 나가면서 학습하는 방식
- GBM: 점진적으로 최적의 가중치 구하는 방식

### GBM
- loss: 경사 하강법에서 사용할 손실 함수 지정. 디폴트는 deviance
- learning_rate: 0~1 사이 값
    - 미분 값을 제어하여 경사를 완만하게 내려가게 해
    - 가장 왼쪽이 최적 지점: 미분값이 0인 지점
    - 너무 작은 값 적용하면 업데이트 되는 값이 작아짐.
    - 값 못 찾고 수렴함
    - 너무 큰 값은 오히려 발산한다.