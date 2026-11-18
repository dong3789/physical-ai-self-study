# Chapter 03 — AI 모델 기초와 로봇 AI 입문

**기간:** 2주 | **전제:** Chapter 02

이 챕터의 목표는 로봇에 들어가는 **AI 모델의 기초**를 배우는 것입니다. CNN과 Transformer의 원리를 이해하고, PyTorch로 모델을 돌려보며, VLM과 VLA가 무엇인지 개념을 잡습니다. Jetson Orin 실습도 포함합니다.

## 학습 목표

- CNN과 Transformer의 동작 원리를 설명할 수 있다
- PyTorch로 간단한 모델을 학습·추론할 수 있다
- Hugging Face에서 사전 학습 모델을 가져와 쓸 수 있다
- VLM과 VLA의 개념과 차이를 설명할 수 있다
- Jetson Orin에서 모델을 실행하는 흐름을 이해한다

## 학습 내용

### 1주차 — CNN·Transformer·PyTorch

- **CNN:** 합성곱이 이미지에서 특징을 뽑는 원리. 커널, 스트라이드, 풀링
- **Transformer:** 어텐션 메커니즘이 문맥을 파악하는 원리. 셀프 어텐션의 직관
- **PyTorch 기초:** 텐서, autograd, DataLoader, 학습 루프 작성
- **전이학습:** 사전 학습된 모델을 가져와서 내 데이터에 맞게 파인튜닝하는 흐름
- **실습:** 사전 학습된 ResNet으로 이미지 분류를 돌려보고, 작은 데이터셋으로 파인튜닝해본다

### 2주차 — VLM·VLA와 Hugging Face, Jetson

- **VLM (Vision-Language Model):** 이미지와 언어를 함께 이해하는 모델. 예: "빨간 컵을 찾아줘"라는 지시를 이미지와 연결하는 방식
- **VLA (Vision-Language-Action):** VLM에 행동(Action)까지 붙인 모델. 언어 지시 → 이미지 인식 → 로봇 행동을 하나의 모델로 처리하는 개념
- **Hugging Face:** 모델 허브에서 사전 학습 모델을 가져와 추론하는 방법 (`transformers` 라이브러리)
- **Jetson Orin:** 엣지 디바이스에서 AI 모델을 실행하는 흐름. TensorRT로 최적화하는 개념
- **실습:** Hugging Face의 VLM 모델로 이미지에 대한 질문에 답하게 해보고, 그 결과를 ROS2 토픽으로 퍼블리시한다

## 실습 과제

### 과제 1 — PyTorch 이미지 분류

CIFAR-10 같은 작은 데이터셋으로 CNN 분류기를 학습시킵니다. 학습 곡선을 그리고, 정확도를 측정합니다. 사전 학습 모델을 가져와서 전이학습을 해보고 처음부터 학습한 것과 비교합니다.

### 과제 2 — VLM으로 장면 이해

Hugging Face의 VLM(예: BLIP) 모델로 Gazebo 카메라 이미지에 대해 질문합니다. "이미지에 뭐가 있어?", "빨간 물체는 어디에 있어?" 같은 질문에 답하게 하고, 결과를 ROS2 토픽으로 내보냅니다.

### 과제 3 — Jetson 실습 (선택)

Jetson Orin이 있다면, 위 VLM 추론을 Jetson에서 돌려보고 속도를 측정합니다. Jetson이 없다면 Docker에서 TensorRT 최적화 개념만 정리하고 넘어갑니다. 이 과제는 선택 사항입니다.

## AI 활용법

- "CNN에서 합성곱이 이미지 특징을 뽑는다는 게 무슨 뜻이야? 구체적인 숫자 예시로 보여줘"처럼 원리를 숫자로 물어봅니다.
- "Transformer의 어텐션은 CNN의 합성곱이랑 뭐가 달라?"처럼 비교 질문을 하면 이해가 깊어집니다.
- "VLM이랑 VLA 차이가 뭐야? 로봇에서 각각 어디에 쓰여?"라고 물어서 로봇 맥락으로 연결합니다.
- PyTorch 에러가 나면 에러 메시지 + 코드 + 텐서 shape을 함께 줍니다. shape mismatch는 가장 흔한 에러입니다.

## 완료 기준

- [ ] PyTorch로 이미지 분류 모델을 학습시키고 평가할 수 있다
- [ ] Hugging Face 모델을 가져와 추론할 수 있다
- [ ] VLM과 VLA의 개념과 차이를 설명할 수 있다
- [ ] VLM 추론 결과를 ROS2 토픽으로 내보낼 수 있다
- [ ] `learning-log.md`에 이번 챕터 내용을 정리했다

## 참고 자료

- PyTorch 공식 튜토리얼: https://pytorch.org/tutorials/
- Hugging Face 문서: https://huggingface.co/docs
- BLIP 모델: https://huggingface.co/Salesforce/blip-image-captioning-base
- Jetson AI Lab: https://www.jetson-ai-lab.com/
