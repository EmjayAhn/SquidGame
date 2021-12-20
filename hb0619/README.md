
No.456 HeungBae LEE TIL

### 2021.10.18 (월)
1. rabbitMQ 튜토리얼 공부
        - 기본적인 AMQP 통신 정리 및 broker, consumer 개념 정리
        - 간단한 RPC 모듈 작성 및 로컬환경에서 docker로 배포 및 테스트

2. FastCampus NLP 강의 절이
        - 기본적인 NLP 전체 흐름 정리



### 2021.10.21 (목)
- Upstage에서 강의한 파라미터 수가 많은 거대한 언어 모델을 빠르고 효과적으로 학습하는 방법인 MoE(Mixed Of Experts) 개념 정리 1일차

- Microsoft에서 공개한 MoE를 사용하여 GPT3에 버금가는 고성능의 다국어 모델 review
    - Scalable and Efficient MoE Training for Multitask Multilingual Models

- Microsoft의 GPU 분산 학습 라이브러리 DeepSpeed 사용법 튜토리얼 정리(진행중)
    - toy project 및 업무에서 사용가능하게 boilerplate로 class code 작성
    - 실제 huggingFace의 분산처리 학습 라이브러리 Accelerator와의 비교 및 장단점 살펴보기


### 2021.10.23 (금~토)
- Upstage에서 강의한 파라미터 수가 많은 거대한 언어 모델을 빠르고 효과적으로 학습하는 방법인 MoE(Mixed Of Experts) 개념 정리 2일차

- intent classification and detection에 사용할 데이터셋 구축 및 전처리
    - mecab shell script 및 wakati를 사용한 pipeline 라인 구축
    - Spider를 통한 비동기 scraping 구축 


### 2021.10.24 (일)
- intent classification and detection에 사용할 데이터셋 구축 및 전처리
    - siame Network를 이용한 few-shot learner 코드 작성 및 학습


### 2021.10.26 (화)
- intent classification and detection에 사용할 model 설계
    - siame Network를 이용한 few-shot learner baseline model 코드 작성


### 2021.10.26 (목)
- 패캠 강의 및 NER의 이해를 위한 CRF 개념 정리 1일차

- AI HUB Shopping AS 데이터 전처리작업


### 2021.10.31 (일)
- 패캠 강의 및 NER의 이해를 위한 CRF 개념 정리 2일차 

### 2021.11.01 (월)
- 패캠 강의 및 NER의 이해를 위한 CRF 개념 정리 3일차

### 2021.11.03 (수)
- intent classification and detection에 사용할 model 설계
    - siame Network를 이용한 few-shot learner baseline model 모델 구조 변경코드 작성

### 2021.11.05 (금)
- intent classification and detection에 사용할 model 고도화
    - siame Network를 이용한 few-shot learner baseline model 모델 테스트 결과 비교 및 고도화를 위한 tripletloss 구조 추가

### 2021.11.07 (일)
- few-shot metric learning 기법 
    - few-shot의 contrastive learning 기법 추가 조사 

### 2021.11.09 (화)
- few-shot metric learning 기법
    - few-shot의 tripletloss를 통한 성능 고도화

### 2021.11.10 (수)
- contrastive learning 기법
    - contrastive learning의 전반적인 개념 review
    - bert 기반의 few-shot에 대한 자료 조사

### 2021.11.13 (토)
- few-shot learner loss들을 비교하며 학습셋 재구축

### 2021.11.14 (일)
-knowledge graph를 구축하기 위한 elastic search 공부 1일차

### 2021.11.16 (화)
-knowledge graph를 구축하기 위한 elastic search 공부 2일차

### 2021.11.18 (목)
- uwsgi+nginx+Django 에서의 memory leak 및 model의 multiprocessing을 위한 환경인 gunicorn을 활용한 환경 구축 공부 1일차

### 2021.11.19 (금)
- uwsgi+nginx+Django 에서의 memory leak 및 model의 multiprocessing을 위한 환경인 gunicorn을 활용한 환경 구축 공부 2일차
- 환경 구축(실습진행)

### 2021.11.21 (일)
- few-shot baseline 모델 고도화 및 테스트 검증

### 2021.11.23 (화)
- 의도분류를 위한 few-shot baseline 모델설계시 학습데이터 활용 방안 검토

### 2021.11.26 (금)
- Deview2021세션 중 챗봇 및 intente detection에 관련한 세션들 보고 정리하기

### 2021.11.28 (일)
- Naver에서 제안한 UNICORN 구조를 사용하기 위한 실험 환경 설정 및 사용된 개념 파악하기

### 2021.11.23 (월)
- BERT를 가이드할 수 있는 보조적인 수단(Auxiliary Representation) 수단을 추가하여 먼저 실험 및 검증 

### 2021.12.04 (토)
- BERT와 GPT로 알아보는 트랜스포머 원리 및 구현 책 정리 1일차

### 2021.12.05 (일)
- BERT와 GPT로 알아보는 트랜스포머 원리 및 구현 책 정리 2일차

### 2021.12.07 (화)
- BERT와 GPT로 알아보는 트랜스포머 원리 및 구현 책 정리 3일차

### 2021.12.08 (수)
- BERT와 GPT로 알아보는 트랜스포머 원리 및 구현 책 정리 4일차
- transformer에 대한 자료 정리 및 colab에 정리

### 2021.12.20 (월)
- deep metric learning
- 1) prototypical, metric based, model based tree map 정리 및 SimCSE method 적용한 Unicorn 아키텍쳐 inference code 작성
