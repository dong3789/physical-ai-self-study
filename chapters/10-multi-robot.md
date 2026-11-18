# Chapter 10 — 다중 로봇과 Fleet 관리

**기간:** 2주 | **전제:** Chapter 07, 09

이 챕터의 목표는 **여러 대의 로봇을 함께 운영하는 방법**을 배우는 것입니다. Multi-Robot Coordination, Fleet Management, Task Allocation, ROS2 DDS·Zenoh, Multi-Agent Communication을 다룹니다.

## 학습 목표

- 다중 로봇 협업의 개념을 설명할 수 있다
- Fleet Management의 역할을 이해한다
- Task Allocation(작업 할당) 방법을 이해한다
- ROS2 DDS와 Zenoh의 차이를 이해한다
- 여러 로봇이 통신하는 구조를 설계할 수 있다

## 학습 내용

### 1주차 — 다중 로봇 협업과 Fleet 관리

- **Multi-Robot Coordination:** 여러 로봇이 충돌하지 않고 협력하는 방법
- **Fleet Management:** 로봇들의 상태를 모니터링하고 작업을 배분하는 시스템
- **Task Allocation:** 어떤 로봇에게 어떤 작업을 줄지 정하는 방법 (경매 방식, 우선순위 방식)
- **네임스페이스:** ROS2에서 여러 로봇을 구분하는 방법 (네임스페이스와 TF prefix)
- **실습:** Gazebo에 TurtleBot3 두 대를 띄우고, 각각 다른 네임스페이스로 구분해서 동시에 움직인다

### 2주차 — ROS2 DDS·Zenoh와 Multi-Agent 통신

- **DDS (Data Distribution Service):** ROS2의 기본 통신 미들웨어. 노드끼리 데이터를 주고받는 방식
- **Zenoh:** ROS2와 함께 쓸 수 있는 경량 통신 프로토콜. 대규모·분산 환경에서 유리한 점
- **Multi-Agent Communication:** 로봇끼리 정보를 주고받는 패턴 (공유 지도, 작업 상태 공유)
- **실습:** 두 대의 로봇이 각자의 위치를 공유하고, 한 로봇이 목표 지점에 가면 다른 로봇이 다음 작업을 시작하는 간단한 협업 시나리오를 구현한다

## 실습 과제

### 과제 1 — 두 대의 로봇 동시 운영

Gazebo에 TurtleBot3 두 대를 띄웁니다. 각 로봇에 네임스페이스를 부여하고, 각각 다른 목표 지점으로 동시에 주행하게 합니다. 두 로봇이 충돌하지 않도록 경로를 조정합니다.

### 과제 2 — 작업 할당 시나리오

세 개의 배송 작업이 있을 때, 두 대의 로봇에게 작업을 할당하는 로직을 만듭니다. 각 로봇의 현재 위치와 작업 위치 사이의 거리를 계산해서 가까운 로봇에게 할당하는 간단한 규칙을 구현합니다. 할당 결과를 출력합니다.

### 과제 3 — 로봇 간 위치 공유

두 로봇이 각자의 위치(`/odom`)를 공유 토픽으로 퍼블리시하고, 서로의 위치를 받아서 RViz에 함께 표시합니다. 한 로봇이 다른 로봇과 1m 이내로 가까워지면 정지하는 안전 로직을 추가합니다.

## AI 활용법

- "ROS2에서 여러 로봇을 띄울 때 네임스페이스는 왜 필요해? 안 쓰면 뭐가 문제야?"처럼 개념을 물어봅니다.
- "DDS랑 Zenoh 차이가 뭐야? 언제 Zenoh를 써?"처럼 비교 질문을 합니다.
- "Task Allocation을 경매 방식으로 한다는 게 무슨 뜻이야? 간단한 예시로 설명해줘"처럼 알고리즘을 물어봅니다.
- "두 대의 로봇을 띄웠는데 TF가 충돌해. 이 에러를 봐줘"라고 구체적으로 물어봅니다.

## 완료 기준

- [ ] 두 대의 로봇을 네임스페이스로 구분해서 동시에 운영할 수 있다
- [ ] 작업 할당 로직을 구현할 수 있다
- [ ] 로봇 간 위치 공유와 안전 정지 로직을 구현할 수 있다
- [ ] DDS와 Zenoh의 차이를 설명할 수 있다
- [ ] `learning-log.md`에 이번 챕터 내용을 정리했다

## 참고 자료

- ROS2 네임스페이스 문서: https://docs.ros.org/en/humble/Concepts/About-Namespaces.html
- Zenoh ROS2 문서: https://github.com/eclipse-zenoh/zenoh-plugin-ros2dds
- Open-RMF (Fleet Management): https://github.com/open-rmf/rmf
