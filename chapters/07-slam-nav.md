# Chapter 07 — SLAM과 자율주행 기초

**기간:** 2주 | **전제:** Chapter 01, 02

이 챕터의 목표는 **로봇이 지도를 만들고 자기 위치를 아는 방법**을 배우는 것입니다. SLAM, Occupancy Grid Map, AMCL, Nav2 Navigation Stack, 경로 계획을 다룹니다.

## 학습 목표

- SLAM의 원리를 설명할 수 있다
- Occupancy Grid Map을 이해하고 만들 수 있다
- AMCL로 로봇 위치를 추정할 수 있다
- Nav2로 자율주행 내비게이션을 수행할 수 있다
- A*·Dijkstra 경로 계획의 원리를 이해한다
- Costmap과 장애물 회피의 개념을 이해한다

## 학습 내용

### 1주차 — SLAM 기초

- **SLAM (Simultaneous Localization and Mapping):** 지도를 만들면서 동시에 자기 위치를 추정하는 문제
- **LiDAR SLAM vs Visual SLAM:** LiDAR 기반과 카메라 기반의 차이
- **Occupancy Grid Map:** 공간을 격자로 나누고 각 셀의 점유 확률을 저장하는 지도 표현
- **Scan Matching:** LiDAR 스캔을 맞춰서 로봇의 이동을 추정하는 방법
- **Loop Closure:** 이미 방문한 장소를 인식해서 누적 오차를 보정하는 개념
- **실습:** TurtleBot3로 Gazebo 환경에서 SLAM을 돌려서 지도를 만든다 (slam_toolbox 사용)

### 2주차 — Nav2 내비게이션

- **AMCL (Adaptive Monte Carlo Localization):** 파티클 필터로 로봇 위치를 추정하는 방법
- **Nav2 Navigation Stack:** ROS2의 내비게이션 프레임워크. 플래너, 컨트롤러, Costmap의 역할
- **Path Planning:** A*와 Dijkstra 알고리즘의 원리와 차이
- **Costmap:** 장애물과 위험도를 격자에 표현한 지도. Global Costmap과 Local Costmap
- **Obstacle Avoidance:** 주행 중 동적 장애물을 피하는 방법
- **실습:** 만든 지도를 이용해 TurtleBot3가 목표 지점까지 자율주행하도록 한다

## 실습 과제

### 과제 1 — SLAM으로 지도 만들기

Gazebo 환경에서 TurtleBot3를 수동으로 조종하면서 SLAM(slam_toolbox)을 돌려 지도를 만듭니다. 만든 지도를 저장하고 RViz에서 확인합니다. 지도의 품질(벽이 똑바로 그려졌는지, 왜곡은 없는지)을 평가합니다.

### 과제 2 — Nav2 자율주행

과제 1에서 만든 지도를 이용해 Nav2를 설정하고, RViz에서 목표 지점을 찍으면 TurtleBot3가 스스로 주행하도록 합니다. 여러 목표 지점을 순서대로 방문하게 합니다.

### 과제 3 — 동적 장애물 회피

주행 경로에 움직이는 장애물(다른 로봇이나 사람 역할)을 놓고, TurtleBot3가 Costmap을 이용해 장애물을 피해서 주행하는지 확인합니다. 회피가 안 되면 Costmap 파라미터를 조정합니다.

## AI 활용법

- "SLAM이 뭐야? 지도를 만들면서 위치를 안다는 게 어떻게 가능해?"처럼 원리를 물어봅니다.
- "AMCL에서 파티클이 뭐야? 파티클이 어떻게 로봇 위치를 추정해?"처럼 알고리즘 직관을 물어봅니다.
- "Nav2에서 플래너랑 컨트롤러 역할이 뭐가 달라?"처럼 구조를 물어봅니다.
- "내 Nav2가 목표까지 안 가. 이 로그를 봐줘"라고 구체적인 로그와 함께 물어봅니다.

## 완료 기준

- [ ] SLAM으로 Gazebo 환경의 지도를 만들고 저장할 수 있다
- [ ] Nav2로 목표 지점까지 자율주행할 수 있다
- [ ] 여러 목표 지점을 순서대로 방문할 수 있다
- [ ] A*와 Dijkstra의 차이를 설명할 수 있다
- [ ] `learning-log.md`에 이번 챕터 내용을 정리했다

## 참고 자료

- slam_toolbox 문서: https://github.com/SteveMacenski/slam_toolbox
- Nav2 공식 문서: https://navigation.ros.org/
- AMCL 설명: https://navigation.ros.org/configuration/packages/amcl/index.html
- Probabilistic Robotics (Thrun, Burgard, Fox) — SLAM의 바이블
