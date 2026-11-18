# Chapter 13 — Sim-to-Real과 강화학습 심화

**기간:** 3주 | **전제:** Chapter 08, 12

이 챕터의 목표는 **시뮬레이션에서 학습한 AI를 실제 로봇으로 옮기는 방법**을 배우는 것입니다. Sim-to-Real Transfer, Domain Adaptation, 강화학습 심화, Policy Optimization, 실제 배포 전략을 다룹니다.

## 학습 목표

- Sim-to-Real Gap이 무엇인지 설명할 수 있다
- Sim-to-Real Transfer 방법을 이해한다
- Domain Adaptation의 개념을 이해한다
- 강화학습 심화 기법을 이해한다
- Policy Optimization 방법을 이해한다
- 실제 로봇 배포 전략을 수립할 수 있다

## 학습 내용

### 1주차 — Sim-to-Real Gap과 Transfer

- **Sim-to-Real Gap:** 시뮬레이션과 실제 환경의 차이. 물리 정확도, 센서 노이즈, 지연, 마찰 등의 차이
- **Sim-to-Real Transfer 방법:**
  - Domain Randomization (Chapter 12에서 배운 방법)
  - System Identification: 실제 로봇의 물리 파라미터를 측정해서 시뮬레이션에 반영
  - Sim-to-Real via Fine-tuning: 시뮬레이션에서 학습한 뒤 실제 데이터로 소량 추가 학습
- **실습:** Gazebo 시뮬레이션에서 학습한 간단한 정책(예: TurtleBot3 장애물 회피)을, 물리 파라미터(마찰, 노이즈)를 바꿔가며 테스트하고 성능이 어떻게 달라지는지 측정한다

### 2주차 — 강화학습 심화

- **Policy Optimization:** PPO 심화. 클리핑, GAE(Generalized Advantage Estimation)의 역할
- **Sample Efficiency:** 적은 데이터로 학습하는 방법. 오프폴리시 학습(SAC)의 장점
- **Reward Shaping 심화:** Chapter 08에서 배운 Reward 설계를 더 깊게. 잠재적 보상(Potential-based Shaping)
- **Curriculum Learning:** 쉬운 작업부터 어려운 작업으로 점진적으로 학습시키는 방법
- **실습:** Chapter 08의 CartPole을 넘어서, Gazebo TurtleBot3의 목표 지점 도달 작업을 PPO로 학습시키는 설계를 한다. Reward 함수를 구현하고, 학습 설정을 문서화한다. GPU가 있으면 실제로 학습을 돌려본다

### 3주차 — 실제 배포 전략

- **Real-world Deployment 전략:** 시뮬레이션 정책을 실제 로봇에 올릴 때의 단계별 접근
  1. 시뮬레이션에서 충분히 검증
  2. 실제 로봇에서 안전장치(속도 제한, 긴급 정지)와 함께 테스트
  3. 점진적으로 자율성을 높임
- **안전장치:** 실제 로봇 배포 시 필수인 안전 로직. 속도 제한, 충돌 감지 시 정지, 원격 정지
- **모니터링:** 실제 로봇의 상태를 모니터링하고 로그를 남기는 방법
- **실습:** 실물 로봇이 없다면, 시뮬레이션에서 "실제 배포"를 가정한 안전장치를 구현한다. 속도 제한, 긴급 정지 토픽, 상태 모니터링 노드를 만들고, 이상 상황에서 로봇이 안전하게 정지하는지 테스트한다

## 실습 과제

### 과제 1 — Sim-to-Real Gap 측정

Chapter 08에서 만든 TurtleBot3 목표 도달 정책을 Gazebo에서 돌립니다. 물리 파라미터(바닥 마찰, LiDAR 노이즈)를 바꿔가며 성공률이 어떻게 달라지는지 측정하고 표로 정리합니다. 어떤 파라미터가 성능에 가장 큰 영향을 미치는지 파악합니다.

### 과제 2 — 강화학습 설계 문서

TurtleBot3의 자율주행 작업을 PPO로 학습시키는 전체 설계를 문서로 작성합니다. 상태 공간, 행동 공간, Reward 함수, 학습 하이퍼파라미터, Curriculum 단계를 모두 포함합니다. 이 문서는 Chapter 15 최종 프로젝트의 참고 자료가 됩니다.

### 과제 3 — 안전장치 구현

ROS2 안전장치 노드를 만듭니다. 속도 제한(최대 속도 초과 시 클램프), 긴급 정지 토픽(정지 명령을 받으면 즉시 정지), 충돌 감지 시 정지(LiDAR 전방 거리가 임계값 이하일 때 정지)를 구현하고, 시뮬레이션에서 테스트합니다.

## AI 활용법

- "Sim-to-Real Gap이 왜 생겨? 시뮬레이션이 아무리 정확해도 실제랑 다른 이유가 뭐야?"처럼 원인을 물어봅니다.
- "Domain Randomization이 Sim-to-Real Gap을 어떻게 줄여? 직관적으로 설명해줘"처럼 직관을 물어봅니다.
- "PPO에서 클리핑이 왜 필요해? 안 하면 뭐가 문제야?"처럼 알고리즘 디테일을 물어봅니다.
- "내 강화학습이 보상이 안 올라. Reward 함수랑 학습 곡선을 봐줘"라고 구체적인 자료와 함께 물어봅니다.

## 완료 기준

- [ ] Sim-to-Real Gap을 측정하고 어떤 파라미터가 영향을 미치는지 파악했다
- [ ] 강화학습 설계 문서를 작성했다
- [ ] 안전장치 노드를 구현하고 테스트했다
- [ ] Sim-to-Real Transfer 방법을 설명할 수 있다
- [ ] `learning-log.md`에 이번 챕터 내용을 정리했다

## 참고 자료

- Sim-to-Real 서베이: "Sim-to-Real Transfer in Deep Reinforcement Learning" (arXiv)
- Domain Randomization 논문: https://arxiv.org/abs/1703.06907
- Stable Baselines3 PPO 문서: https://stable-baselines3.readthedocs.io/en/master/modules/ppo.html
