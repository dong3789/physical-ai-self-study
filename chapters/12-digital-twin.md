# Chapter 12 — Digital Twin과 시뮬레이션

**기간:** 3주 | **전제:** Chapter 02, 05, 11

이 챕터의 목표는 **가상 환경에서 로봇을 학습·검증하는 방법**을 배우는 것입니다. NVIDIA Isaac Sim, USD, PhysX 물리 시뮬레이션, Synthetic Data Generation, Domain Randomization을 다룹니다.

> **환경 주의:** Isaac Sim은 NVIDIA GPU + CUDA가 필수입니다. Mac(Apple Silicon)에서는 Isaac Sim이 안 돌아갑니다. 이 챕터는 두 가지 경로로 진행합니다.
> - **경로 A (GPU 있음):** Isaac Sim으로 진행합니다. 게이밍 PC나 클라우드 GPU가 필요합니다.
> - **경로 B (GPU 없음):** Gazebo로 진행합니다. Isaac Sim의 개념(USD, Domain Randomization)은 이해하고, 실습은 Gazebo에서 동등한 수준으로 수행합니다. GPU가 생기면 Isaac Sim으로 갈아탈 수 있습니다.

## 학습 목표

- Digital Twin의 개념과 구축 방법을 이해한다
- Isaac Sim(또는 Gazebo)으로 물리 시뮬레이션 환경을 만들 수 있다
- USD의 개념을 이해한다
- Synthetic Data를 생성할 수 있다
- Domain Randomization의 개념을 이해한다

## 학습 내용

### 1주차 — Digital Twin과 Isaac Sim (또는 Gazebo 심화)

- **Digital Twin:** 실제 환경을 가상 공간에 재현한 것. 단순 시뮬레이션과 달리 실제 데이터와 동기화되는 것이 특징
- **Isaac Sim:** NVIDIA의 로봇 시뮬레이터. Omniverse 기반, PhysX 물리 엔진, USD 장면 표현
- **USD (Universal Scene Description):** 3D 장면을 표현하는 표준 포맷. 로봇, 물체, 조명, 카메라를 하나의 파일로 정의
- **Gazebo 심화 (경로 B):** SDF 포맷으로 환경을 정의하고, 플러그인으로 센서와 물리를 확장하는 방법
- **실습:** 간단한 제조 공장 환경을 시뮬레이터에 만든다. 컨베이어, 로봇팔, 상자를 배치하고, 물리(중력, 충돌)가 동작하는지 확인한다

### 2주차 — 물리 시뮬레이션과 Synthetic Data

- **PhysX 물리 시뮬레이션:** 강체 동역학, 충돌, 마찰이 시뮬레이션에서 어떻게 계산되는지
- **Synthetic Data Generation:** 시뮬레이션에서 학습 데이터를 자동으로 만드는 방법. 이미지, 깊이, 세그멘테이션 마스크를 렌더링해서 데이터셋을 구축
- **Domain Randomization:** 조명, 질감, 물체 위치를 무작위로 바꿔서 학습 데이터의 다양성을 늘리는 방법
- **실습:** 시뮬레이션 환경에서 물체의 위치·조명을 바꿔가며 이미지 데이터셋 100장을 자동 생성한다. 생성된 이미지를 확인하고 라벨(바운딩 박스)이 맞는지 검증한다

### 3주차 — Digital Twin 환경 설계 실습

- **제조 공장 Digital Twin 설계:** Chapter 09의 물류 창고와 Chapter 11의 공장 개념을 합쳐서, 가상의 제조 공장 Digital Twin을 설계한다
- **복잡한 Manipulation Task 구성:** 로봇팔이 수행할 작업 시나리오를 시뮬레이션에 구성한다
- **실습:** 설계한 Digital Twin 환경에서 로봇팔 Pick & Place 시나리오를 구성하고, 시뮬레이션으로 동작을 검증한다. 결과를 영상으로 기록한다

## 실습 과제

### 과제 1 — 제조 공장 시뮬레이션 환경 구축

Isaac Sim(경로 A) 또는 Gazebo(경로 B)에 제조 공장 환경을 만듭니다. 컨베이어 벨트, 로봇팔 1대, 상자 5개, 작업대를 배치합니다. 물리 시뮬레이션이 동작하는지 확인합니다.

### 과제 2 — Synthetic Data 자동 생성

과제 1의 환경에서 Domain Randomization을 적용해서 이미지 데이터셋을 자동 생성합니다. 물체 위치, 조명 밝기, 카메라 각도를 무작위로 바꿔가며 100장을 생성합니다. YOLO로 학습할 수 있는 형태(바운딩 박스 라벨 포함)로 저장합니다.

### 과제 3 — Digital Twin 설계 문서

과제 1의 환경을 Digital Twin 관점에서 문서화합니다. 실제 공장이라면 어떤 센서 데이터를 동기화할지, 어떤 부분을 시뮬레이션으로 검증할지 정리합니다. 이 문서는 Chapter 15 최종 프로젝트의 설계 자료로 씁니다.

## AI 활용법

- "Isaac Sim이랑 Gazebo 차이가 뭐야? 언제 어떤 걸 써?"처럼 비교 질문을 합니다.
- "USD가 뭐야? URDF랑 뭐가 달라?"처럼 포맷 차이를 물어봅니다.
- "Domain Randomization이 왜 필요해? 그냥 실제 데이터로 학습하면 안 돼?"처럼 필요성을 물어봅니다.
- "내 시뮬레이션에서 물체가 공중에 떠 있어. 뭐가 문제일까?"처럼 구체적인 현상과 함께 물어봅니다.

## 완료 기준

- [ ] 시뮬레이터에 제조 공장 환경을 만들고 물리가 동작하는 것을 확인했다
- [ ] Domain Randomization으로 Synthetic Data 100장을 자동 생성했다
- [ ] Digital Twin 설계 문서를 작성했다
- [ ] `learning-log.md`에 이번 챕터 내용을 정리했다

## 참고 자료

- Isaac Sim 문서: https://docs.isaacsim.omniverse.nvidia.com/
- Isaac Sim 튜토리얼: https://github.com/isaac-sim/IsaacSim
- Gazebo 문서: https://gazebosim.org/docs
- USD 공식 문서: https://openusd.org/
