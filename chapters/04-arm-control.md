# Chapter 04 — 로봇팔 제어와 모션 플래닝

**기간:** 2주 | **전제:** Chapter 02, 03

이 챕터의 목표는 **로봇팔을 움직이는 방법**을 배우는 것입니다. 정운동학·역운동학, MoveIt2 모션 플래닝, 경로 계획 알고리즘(RRT·PRM)을 다룹니다. 시뮬레이션 로봇팔로 실습합니다.

## 학습 목표

- Forward Kinematics와 Inverse Kinematics를 설명하고 계산할 수 있다
- DH 파라미터와 Jacobian의 의미를 이해한다
- MoveIt2로 로봇팔의 모션 플래닝을 할 수 있다
- RRT·PRM 같은 샘플링 기반 경로 계획의 원리를 이해한다
- Joint Space와 Cartesian 제어를 구분할 수 있다

## 학습 내용

### 1주차 — 운동학 기초

- **Forward Kinematics (FK):** 각 관절 각도가 주어졌을 때 손끝(End-Effector)의 위치를 구하는 방법
- **Inverse Kinematics (IK):** 손끝 목표 위치가 주어졌을 때 각 관절 각도를 구하는 방법. 해가 여러 개일 수 있음
- **DH 파라미터:** 로봇팔의 링크 구조를 표준화된 파라미터로 표현하는 방법
- **Jacobian:** 관절 속도 → 손끝 속도의 관계를 나타내는 행렬. 특이점(Singularity) 개념
- **실습:** 2링크 평면 로봇팔의 FK·IK를 Python으로 직접 계산해보고, numpy로 검증한다

### 2주차 — MoveIt2와 경로 계획

- **MoveIt2:** ROS2의 모션 플래닝 프레임워크. Move Group, Planning Scene, 충돌 회피 개념
- **RRT (Rapidly-exploring Random Tree):** 무작위 샘플링으로 빠르게 경로를 찾는 방법
- **PRM (Probabilistic Roadmap):** 미리 로드맵을 만들어서 경로를 찾는 방법
- **Joint Space vs Cartesian 제어:** 관절 각도로 움직이는 것과 손끝 위치로 움직이는 것의 차이
- **실습:** Gazebo/RViz에서 로봇팔(Panda 또는 UR5 시뮬레이션 모델)을 띄우고, MoveIt2로 목표 위치까지 팔을 움직인다

## 실습 과제

### 과제 1 — 2링크 로봇팔 FK·IK 계산기

Python + numpy로 2링크 평면 로봇팔의 FK와 IK를 구현합니다. IK는 해석적 해법으로 구하고, FK 결과와 대조해서 검증합니다. 결과를 matplotlib으로 시각화합니다.

### 과제 2 — MoveIt2로 Pick 동작

RViz에서 로봇팔 시뮬레이션 모델을 띄우고, MoveIt2 Python API로 다음을 수행합니다.

1. 팔을 홈 위치에서 목표 위치로 이동
2. 그리퍼 열기·닫기
3. 물체를 잡고 다른 위치로 옮기기

### 과제 3 — 장애물 회피 경로

테이블 위에 장애물을 놓고, MoveIt2의 Planning Scene에 장애물을 추가한 뒤, 충돌을 피해서 목표까지 가는 경로를 계획합니다. RRT와 PRM 중 어떤 플래너를 썼는지 기록합니다.

## AI 활용법

- "역운동학이 뭐야? 2링크 로봇팔 예시로 숫자를 넣어서 계산 과정을 보여줘"처럼 구체적인 숫자로 물어봅니다.
- "MoveIt2에서 Planning Scene이 뭐야? 왜 장애물을 추가해야 해?"처럼 개념을 물어봅니다.
- "내 MoveIt2 코드가 플래닝에 실패해. 이 에러 로그를 봐줘"라고 구체적으로 물어봅니다. 플래닝 실패는 시작 자세, 목표 자세, 충돌 설정 중 하나가 원인인 경우가 많습니다.
- "RRT랑 PRM 차이가 뭐야? 언제 어떤 걸 써?"처럼 비교 질문을 합니다.

## 완료 기준

- [ ] 2링크 로봇팔의 FK·IK를 코드로 계산하고 검증할 수 있다
- [ ] MoveIt2로 로봇팔을 목표 위치까지 움직일 수 있다
- [ ] Planning Scene에 장애물을 추가하고 충돌 회피 경로를 만들 수 있다
- [ ] FK와 IK, Joint Space와 Cartesian 제어의 차이를 설명할 수 있다
- [ ] `learning-log.md`에 이번 챕터 내용을 정리했다

## 참고 자료

- MoveIt2 공식 문서: https://moveit.picknik.ai/humble/index.html
- Modern Robotics (무료 교재): https://modernrobotics.northwestern.edu/
- OMPL (모션 플래닝 라이브러리): https://ompl.kavrakilab.org/
