# Chapter 14 — VLA와 Foundation Model 실전

**기간:** 3주 | **전제:** Chapter 03, 06, 08

이 챕터의 목표는 **VLA와 로봇 Foundation Model을 실제로 다루는 것**입니다. VLA 모델 파인튜닝, Multi-modal Learning, Robot Foundation Model, 실제 로봇 Policy 배포, 성능 평가·최적화를 다룹니다.

## 학습 목표

- VLA 모델을 파인튜닝할 수 있다
- Multi-modal Learning의 개념을 이해한다
- Robot Foundation Model의 개념을 이해한다
- 학습한 Policy를 실제 로봇 환경에 배포하는 흐름을 이해한다
- 성능을 평가하고 최적화할 수 있다

## 학습 내용

### 1주차 — VLA 파인튜닝

- **VLA 파인튜닝:** 사전 학습된 VLA 모델(OpenVLA 등)을 내 작업 데이터로 추가 학습시키는 방법
- **데이터 형식:** VLA 학습 데이터는 어떻게 구성되는지. 이미지 + 언어 지시 + 행동 궤적의 쌍
- **LoRA 파인튜닝:** 전체 파라미터가 아니라 일부만 학습시켜서 효율적으로 파인튜닝하는 방법
- **실습:** OpenVLA의 파인튜닝 코드를 읽고, 데이터 형식을 파악한다. 작은 데이터셋으로 파인튜닝을 시도해본다 (GPU 필요. 없으면 코드 읽기와 데이터 준비까지만 한다)

### 2주차 — Multi-modal Learning과 Foundation Model

- **Multi-modal Learning:** 이미지, 언어, 깊이, 촉각 등 여러 모달리티를 함께 학습하는 방법
- **Robot Foundation Model:** 다양한 로봇 작업에 공통으로 쓸 수 있는 대규모 사전 학습 모델의 개념
- **RT-X:** 여러 로봇의 데이터를 모아서 학습한 데이터셋. Foundation Model이 가능해진 배경
- **실습:** RT-X 데이터셋의 구조를 살펴보고, 어떤 로봇·작업 데이터가 포함되어 있는지 파악한다

### 3주차 — Policy 배포와 성능 평가

- **Policy Deployment:** 학습한 정책을 로봇 시스템에 통합하는 방법. ROS2 노드로 래핑해서 배포
- **성능 평가:** 성공률, 수행 시간, 실패 원인을 측정하고 분석하는 방법
- **최적화:** 추론 속도 개선 (양자화, TensorRT), 정책 안정성 개선
- **실습:** Chapter 06에서 만든 Behavior Cloning 정책을 ROS2 노드로 래핑하고, Gazebo에서 Pick & Place 미션을 수행하면서 성공률을 측정한다. 실패 케이스를 분석하고 개선 방향을 정리한다

## 실습 과제

### 과제 1 — VLA 파인튜닝 시도

OpenVLA 파인튜닝 파이프라인을 파악하고, Chapter 06에서 수집한 시연 데이터를 VLA 학습 형식으로 변환합니다. GPU가 있으면 작은 규모로 파인튜닝을 시도합니다. GPU가 없으면 데이터 변환과 학습 설정까지만 하고, 클라우드 GPU에서 돌릴 수 있게 준비합니다.

### 과제 2 — Policy 배포와 평가

Chapter 06의 Behavior Cloning 정책을 ROS2 노드로 만들어서 Gazebo Pick & Place 미션에 배포합니다. 20회 시도해서 성공률을 측정하고, 실패한 케이스의 원인을 분석합니다. (물체 위치, 조명, 초기 자세 등)

### 과제 3 — 성능 개선 보고서

과제 2의 결과를 바탕으로 성능 개선 보고서를 작성합니다. 성공률, 실패 원인 분석, 개선 방향(데이터 추가, Reward 조정, 파인튜닝)을 정리합니다. 이 보고서는 Chapter 15 최종 프로젝트의 참고 자료가 됩니다.

## AI 활용법

- "LoRA 파인튜닝이 뭐야? 전체 파인튜닝보다 뭐가 좋아?"처럼 효율화 기법을 물어봅니다.
- "VLA 학습 데이터는 어떻게 생겼어? 이미지·언어·행동이 어떻게 짝지어져?"처럼 데이터 형식을 물어봅니다.
- "Policy 배포할 때 ROS2 노드로 어떻게 래핑해? 구조를 알려줘"처럼 통합 방법을 물어봅니다.
- "내 정책 성공률이 60%야. 실패 케이스를 분석해줘"라고 구체적인 실패 로그와 함께 물어봅니다.

## 완료 기준

- [ ] VLA 파인튜닝 파이프라인을 파악하고 데이터를 준비할 수 있다
- [ ] Behavior Cloning 정책을 ROS2 노드로 배포하고 성공률을 측정했다
- [ ] 성능 개선 보고서를 작성했다
- [ ] Robot Foundation Model의 개념을 설명할 수 있다
- [ ] `learning-log.md`에 이번 챕터 내용을 정리했다

## 참고 자료

- OpenVLA: https://github.com/moojink/openvla
- RT-X 논문: https://arxiv.org/abs/2310.08864
- LoRA 논문: https://arxiv.org/abs/2106.09685
