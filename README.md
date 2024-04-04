## 🙌 소득 예측 AI 해커톤 테스트용 코드

![title](https://dacon.s3.ap-northeast-2.amazonaws.com/competition/236229/card_cpt.jpg?20220808)   

안녕하세요, 해당 코드는 데이콘에서 운영하는 소득 예측 AI 해커톤을 소개하는 코드입니다.


## 🙋‍♀️ 실행 환경

해당 프로젝트를 제작한 환경은 아래와 같습니다.
- Jupyter
- Python 3


##  📌 코드 설명


이 코드는 스태킹(stacking) 방법을 사용하여 여러 기계학습 모델의 예측을 결합하여 개인의 소득 수준을 예측하는 과정을 보여줍니다. 스태킹은 여러 기본 모델(base models)의 예측을 입력으로 사용하여 최종 예측을 생성하는 메타 모델(meta model)을 훈련시키는 앙상블 학습 방법입니다. 주요 단계는 다음과 같습니다

- train_data에서 예측에 사용할 특성(X)과 타겟 변수(y, 소득)를 분리합니다.
- 'ID'와 'Income' 열을 제외한 나머지 데이터로 특성을 구성합니다.
- pd.get_dummies 함수를 사용하여 범주형 변수를 원-핫 인코딩으로 변환합니다.
- StandardScaler를 사용하여 특성 데이터를 스케일링합니다. 이는 모델의 성능을 향상시킬 수 있습니다.
- RandomForestRegressor와 GradientBoostingRegressor 모델에 대한 하이퍼파라미터 그리드를 정의합니다.
- KFold를 사용하여 교차 검증을 위한 설정을 합니다.
- GridSearchCV를 사용하여 각 기본 모델에 대한 최적의 하이퍼파라미터를 찾습니다.
- 메타 모델로 Ridge 회귀 모델을 사용합니다.
- 각 기본 모델을 훈련시키고, 훈련 데이터와 테스트 데이터에 대한 예측을 수행합니다.
- 이러한 예측들을 메타 모델의 훈련 데이터로 사용하여 메타 모델을 훈련시킵니다.
- 메타 모델을 사용하여 최종 예측을 생성합니다.
- 최종 예측 결과를 DataFrame에 저장하고, 'ID'와 함께 'stacked_submission_with_improvements.csv' 파일로 출력합니다.
