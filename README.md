# RandomForestClassifier_Hyperparameter_Optimization_using_Genetic_Algorithm(RandomForestClassifier_GA_HPO.ipynb)
Genetic Algorithm(GA)를 이용해 RandomForestClassifier의 HyperParameter를 최적화

('[DACON 모델 튜닝 챌린지 : 월간 데이콘 파일럿](https://dacon.io/competitions/official/236229/overview/description)'에서 제시하는 HyperParameter, 평가지표, 데이터를 사용하였습니다.)
![데이콘](https://github.com/user-attachments/assets/e9ca1f6f-1ca3-46f9-82c8-c2546e4766fb)
https://dacon.io/competitions/official/236229/overview/description


<hr/>

## Model : RandomForestClassifier

## 최적화할 HyperParameter(10개)
- n_estimators:
<br> 기본값: 10
<br> 범위: 10 ~ 1000 사이의 양의 정수. 일반적으로 값이 클수록 모델 성능이 좋아지지만, 계산 비용과 시간도 증가합니다.

- criterion:
<br> 기본값: 'gini'
<br> 옵션: 'gini', 'entropy'. 'gini'는 진니 불순도를, 'entropy'는 정보 이득을 기준으로 합니다.

- max_depth:
<br> 기본값: None
<br> 범위: None 또는 양의 정수. None으로 설정하면 노드가 모든 리프가 순수해질 때까지 확장됩니다. 양의 정수를 설정하면 트리의 최대 깊이를 제한합니다.

- min_samples_split:
<br> 기본값: 2
<br> 범위: 2 이상의 정수 또는 0과 1 사이의 실수 (비율을 나타냄, (0, 1] ). 내부 노드를 분할하기 위해 필요한 최소 샘플 수를 지정합니다.

- min_samples_leaf:
<br> 기본값: 1
<br> 범위: 1 이상의 정수 또는 0과 0.5 사이의 실수 (비율을 나타냄, (0, 0.5] ). 리프 노드가 가져야 하는 최소 샘플 수를 지정합니다.

- min_weight_fraction_leaf:
<br> 기본값: 0.0
<br> 범위: 0.0에서 0.5 사이의 실수. 리프 노드에 있어야 하는 샘플의 최소 가중치 비율을 지정합니다.

- max_features:
<br> 기본값: 'auto'
<br> 옵션: 'auto', 'sqrt', 'log2', None 또는 양의 정수/실수. 최적의 분할을 찾기 위해 고려할 특성의 수 또는 비율을 지정합니다. 'auto'는 모든 특성을 사용함을 의미하며, 'sqrt'와 'log2'는 각각 특성의 제곱근과 로그2를 사용합니다. None은 'auto'와 동일하게 모든 특성을 의미합니다.

- max_leaf_nodes:
<br> 기본값: None
<br> 범위: None 또는 양의 정수. 리프 노드의 최대 수를 제한합니다. None은 무제한을 의미합니다.

- min_impurity_decrease:
<br> 기본값: 0.0
<br> 범위: 0.0 이상의 실수. 노드를 분할할 때 감소해야 하는 불순도의 최소량을 지정합니다.

- bootstrap:
<br> 기본값: True
<br> 옵션: True, False. True는 부트스트랩 샘플을 사용하여 개별 트리를 학습시킵니다. False는 전체 데이터셋을 사용하여 각 트리를 학습시킵니다.

## 평가 Metric: AUC (Area Under the ROC Curve)

<hr/>

## 해 표현
- DataFrame의 열(column)을 하이퍼파라미터로 생성했을 때 각 행 값을 갖는 RandomForestClassifier 모델
![해표현](https://github.com/user-attachments/assets/f6176ce6-bcab-4dbe-a873-a0085d3ed4ab)
<br>-> 위 데이터프레임의 한 행에서 마지막 score를 제외한 모든 HyperParameter를 갖는 RandomForestClassifier 모델이 하나의 해이다.

## [Class] RandomForestClassifier_GA_Optimizer()
기능: Genetic Algorithm(GA)를 이용해 RandomForestClassifier의 하이퍼파라미터를 최적화하는 클래스 객체

### 작동 과정
1. 초기해 생성(Initialize Population)
2. 선택 후 교배(Selection & Crossover)
3. 돌연변이(Mutation)
4. Population 갱신(Update Population)
-> 최대 세대수까지 Step 2~4 반복

## [Function] Optimize_RFC_HP
기능: RandomForestClassifier가 학습할 Train, Test(Valid) 데이터와 HyperParameter의 Searching Area, 평가지표, GA에 필요한 Parameter 등을 입력받고<br>
RandomForestClassifier_GA_Optimizer()를 객체로 불러와 최적화를 수행하여 최적화된 모델과 최적 HyperParameter, Score 시각화를 제공

- 참고설명 file: RandomForestClassifier GA HPO 작동 과정 설명 및 구현.pdf

<hr/>

## 실험방법
많이 사용되는 최적화 알고리즘과 구현한 GA_HPO 최적화 알고리즘과 성능 비교

### 비교할 최적화 알고리즘
- Grid Search
- Random Search
- Optuna

### 결과 요약
![결과요약](https://github.com/user-attachments/assets/f750ad03-f7b7-4f02-ac5b-fa5443ebdf5e)
※ 수상 기준 : LeaderBoard(private score) 1, 2, 3, 4, 5등

- 참고설명 file: HyperParameter Searching area 개선 및 결과.pdf



