# Chapter 06 — VLA 입문: 모방학습과 Diffusion Policy

**기간:** 2주 | **전제:** Chapter 03, 04

이 챕터의 목표는 **로봇이 사람 시연을 보고 배우는 방법**을 배우는 것입니다. Behavior Cloning(모방학습), Diffusion Policy, VLA 모델 구조, OpenVLA와 RT-2의 개념을 다룹니다.

## 학습 목표

- Behavior Cloning의 원리와 한계를 설명할 수 있다
- Imitation Learning 데이터가 어떻게 구성되는지 이해한다
- Diffusion Policy의 개념을 설명할 수 있다
- VLA 모델의 구조(비전 + 언어 + 액션)를 이해한다
- OpenVLA·RT-2가 무엇인지 설명할 수 있다

## 학습 내용

### 1주차 — 모방학습 기초

- **Behavior Cloning:** 전문가 시연 데이터(상태 → 행동 쌍)로 지도학습을 해서 정책을 만드는 방법
- **데이터 수집:** 시연 데이터를 어떻게 모으는지. 상태(카메라 이미지, 관절 각도), 행동(관절 속도·목표 위치)의 쌍
- **Covariate Shift:** 학습 데이터와 다른 상황에서 정책이 틀어지는 문제. 왜 모방학습만으로는 부족한지
- **DAgger:** 전문가에게 추가 시연을 요청해서 데이터 분포를 넓히는 방법 (개념만)
- **실습:** 시뮬레이션에서 간단한 Pick 동작의 시연 데이터를 모으고, Behavior Cloning으로 정책을 학습시켜본다

### 2주차 — Diffusion Policy와 VLA

- **Diffusion Policy:** 행동을 생성하는 과정을 노이즈 제거 과정으로 모델링하는 방법. 멀티모달 행동(여러 가능한 동작)을 잘 표현함
- **VLA 모델 구조:** 비전 인코더 + 언어 인코더 + 액션 디코더가 어떻게 연결되는지
- **OpenVLA:** 오픈소스 VLA 모델. 구조와 사용 방법
- **RT-2:** Google의 VLA 모델. 웹 데이터로 학습한 비전-언어 모델을 로봇 행동에 전이한 개념
- **실습:** OpenVLA의 추론 코드를 읽어보고, 어떤 입력(이미지 + 언어 지시)이 어떤 출력(행동)으로 바뀌는지 파악한다

## 실습 과제

### 과제 1 — Behavior Cloning Pick 정책

Gazebo 시뮬레이션에서 로봇팔 Pick 동작의 시연 데이터를 수집합니다. 키보드나 스크립트로 로봇팔을 움직여서 물체를 집는 과정을 20~30회 반복하고, 각 스텝의 상태(이미지, 관절 각도)와 행동(관절 목표 각도)을 기록합니다. 이 데이터로 간단한 Behavior Cloning 정책(MLP)을 학습시키고, 학습된 정책으로 Pick을 수행해봅니다. 성공률을 측정합니다.

### 과제 2 — Diffusion Policy 개념 정리

Diffusion Policy 논문의 핵심 아이디어를 읽고 정리합니다. 왜 행동 생성에 Diffusion을 쓰는지, Behavior Cloning과 비교해서 어떤 장점이 있는지 자기 말로 정리합니다. (논문 전체를 읽을 필요는 없습니다. 초록과 그림만으로 핵심을 파악합니다.)

### 과제 3 — OpenVLA 추론 코드 읽기

OpenVLA 저장소를 클론하고 추론 코드를 읽습니다. 입력이 어떻게 전처리되고, 모델이 어떤 출력을 내는지 파악합니다. 실제로 모델을 돌리는 것은 무겁기 때문에, 코드 읽기와 구조 파악이 목표입니다. GPU가 있다면 작은 입력으로 추론을 시도해봅니다.

## AI 활용법

- "Behavior Cloning이 뭐야? 지도학습이랑 뭐가 달라?"처럼 개념을 물어봅니다.
- "Covariate Shift가 로봇 모방학습에서 왜 문제야? 구체적인 예시로 설명해줘"처럼 실전 문제를 물어봅니다.
- "Diffusion Policy가 행동을 만든다는 게 무슨 뜻이야? 이미지 생성하는 Diffusion이랑 어떻게 연결돼?"처럼 비유를 요청합니다.
- "OpenVLA 구조를 설명해줘. 비전 인코더는 뭐고 액션 디코더는 뭐야?"처럼 아키텍처를 물어봅니다.

## 완료 기준

- [ ] Behavior Cloning으로 Pick 정책을 학습시키고 성공률을 측정할 수 있다
- [ ] Covariate Shift와 그 대응 방법을 설명할 수 있다
- [ ] Diffusion Policy의 핵심 아이디어를 설명할 수 있다
- [ ] OpenVLA·RT-2의 구조와 역할을 설명할 수 있다
- [ ] `learning-log.md`에 이번 챕터 내용을 정리했다

## 참고 자료

- Diffusion Policy 논문: https://arxiv.org/abs/2303.04137
- OpenVLA: https://github.com/moojink/openvla
- RT-2 논문: https://arxiv.org/abs/2307.15818
- Imitation Learning 서베이: "A Survey of Imitation Learning" (arXiv)
