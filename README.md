# 한국어 문장 관계 분류 경진대회

참가자: 장홍선, 박준하, 정진호

---

## Data augmentation

### 2.21
papago API 활용 코드 작성 -> 일일 10000자 제한량 한계..


### 2.23 

crawling의 방법 중 하나로 chrome web driver를 활용하여 papago 번역기 활용하는 back-translation 방법 적용 중

단점 : 1회 translation 당 4초의 긴 시간 ->  10000개의 문장 번역시 11시간의 시간 소모


## Model selection

### 2.24

ROBERTa large model, without CV, epoch= 7, lr = 1e-5에 대해서 0.875의 현재 최고 score 획득

ROBERTa large model 역시 CV = 5로 수행한 모델을 저장하고
ROBERTa base model 역시 CV =5 로 수행할 예정
electra base model의 경우 준하님이 수행해주실 예정
ROBERTa small model은 합칠 경우 좋아지는지 고려해봐야함.

현재 계획은 ROBERTa largeCV5 + ROBERTa baseCV5 + ELECTRA base CV5 + ROBERTa small CV5를 logit emsemble하여 수행해볼 예정 어떤 모델을 합쳤을때 성능이 좋아지는지 비교해볼 것이다.

### 2.26

RoBERTa large model과 roBERTa-base(CV), KoELECTRA(CV)를 적용한 model을 logit emsemble을 통해 0.883(public score) 획득.

Data augmentaion 완료 aug효과를 확인할 예정

roBERTa-large model에 대해 k-fold cross validation 을 적용해서 결과를 볼 예정

### 3.2

Data augmentation 완료 10000개의 train data 추가 및 KoELECTRA의 경우 augmentation된 data를 바탕으로 5-fold cross validation 수행 좀더 모델이 robust 해지는 효과가 있어 score가 조금 상승했다.


최종적으로 roBERTa-large(no CV), roBERTa-base(CV), ELECTRA-base(CV+ data augmentation)
모델 결과를 앙상블하여 최종 결과를 얻었다.

0.886 public, 0.881 private score 를 획득하여 최종순위 33등을 기록했다.

