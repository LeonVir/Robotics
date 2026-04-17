# 교통 표지판 인식 및 모델 경량화를 위한 지식 증류 (Knowledge Distillation)

## 📋 프로젝트 요약 (Overview)
자율주행 및 로보틱스의 핵심 기술인 **교통 표지판 인식(GTSRB)** 성능을 극대화하고, 실제 로봇 환경의 제한된 리소스를 고려한 **모델 경량화**를 수행한 프로젝트입니다. 고성능 거대 모델(Teacher)의 지식을 경량 모델(Student)에 전수하는 **지식 증류(Knowledge Distillation)** 기법을 적용하여 연산 효율성과 정확도의 최적점을 연구했습니다.

## 🛠 사용 기술 (Tech Stack)
- **Language:** Python
- **Framework:** PyTorch, Torchvision
- **Architecture:** CNN, Knowledge Distillation (KD) 파이프라인
- **Dataset:** GTSRB (German Traffic Sign Recognition Benchmark)
- **Concepts:** Model Compression, Robotic Perception, Embedded AI

## 💡 주요 연구 및 엔지니어링 내용 (Key Features)

### 1. 지식 증류(Knowledge Distillation) 파이프라인 구현
- **Teacher-Student 학습:** 복잡한 구조의 Teacher 모델로부터 추출한 Soft Label을 활용해 Student 모델의 학습을 가이드했습니다.
- **손실 함수 최적화:** KD Loss를 직접 구현하여 경량 모델이 단순히 정답값만 배우는 것이 아니라, 클래스 간의 관계(Dark Knowledge)까지 학습하도록 설계했습니다.

### 2. 로봇 지각 시스템 최적화 분석 (`34212-Lab-S-Report.pdf`)
- **State-of-the-Art 분석:** 현대 로보틱스 내 DNN 트렌드와 Annotation Scarcity(데이터 부족), Domain Shift 문제를 심도 있게 분석했습니다.
- **시각적-의미적 구조 분석:** 모델이 오분류하는 원인을 시각적 유사성과 의미적 구조 관점에서 해석하여, 안전이 최우선인 로봇 시스템의 신뢰성 확보 방안을 제시했습니다.

### 3. 특정 클래스 특화 성능 개선
- **속도 제한(Speed Limit) 집중 분석:** 자율주행에서 가장 중요한 0~120km/h 속도 제한 표지판들에 대한 성능 지표를 별도로 관리했습니다.
- **성능 향상:** KD 적용을 통해 일반 경량 모델 대비 속도 제한 클래스에서 유의미한 정확도(pp) 향상을 정량적으로 검증했습니다.

## 🔥 핵심 엔지니어링 역량

### 1. 온디바이스 AI를 위한 모델 경량화 (Model Compression)
- 리소스가 제한된 하드웨어(임베디드/로봇)에서도 실시간 추론이 가능하도록 모델 사이즈를 줄이면서도 성능 저하를 최소화하는 전략을 성공적으로 수행했습니다.

### 2. 정밀한 모델 평가 및 디버깅
- 단순 Accuracy 측정을 넘어, 클래스별 오차 행렬(Confusion Matrix) 분석과 시각적 구조 분석을 통해 모델의 취약점을 파악하고 기술적 해결책을 도출했습니다.

## 📊 실험 결과 및 분석
- **Teacher Model:** 고도의 복잡성을 통한 높은 정확도 확보
- **Standard Student:** 낮은 연산량이나 정확도 한계 발생
- **KD Student:** **Standard 대비 높은 정확도 달성**, 자율주행 필수 클래스(속도 제한 등)에서 뛰어난 복합 추론 성능 확인