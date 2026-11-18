# Chapter 01 — Python·Linux·ROS2 기초

**기간:** 2주 | **전제:** Chapter 00

이 챕터의 목표는 ROS2로 로봇을 움직이는 **기본 문법**을 익히는 것입니다. ROS2의 핵심 개념(노드, 토픽, 서비스, 액션)을 이해하고, TurtleBot3를 코드로 직접 움직여봅니다.

## 학습 목표

- Python으로 ROS2 노드를 작성할 수 있다
- Topic / Service / Action의 차이를 설명할 수 있다
- rclpy로 퍼블리셔와 서브스크라이버를 만들 수 있다
- TurtleBot3를 코드로 움직이고 센서 값을 읽을 수 있다

## 학습 내용

### 1주차 — Python 복습과 Linux·Git

- Python 기초 문법 복습: 자료구조(list, dict), 함수, 클래스, 예외 처리
- Python에서 자주 쓰는 패턴: 콜백, 데코레이터, context manager
- Linux 명령어: 파일 조작, 프로세스 확인, 권한, 파이프·리다이렉션
- Git: branch, commit, push, pull, merge conflict 해결
- VS Code 단축키와 디버깅 기초

> 이미 Python에 익숙하다면 이 부분은 2~3일로 줄이고 ROS2로 빨리 넘어가도 됩니다.

### 2주차 — ROS2 핵심 개념과 rclpy

- **ROS2 아키텍처:** 노드(Node), 토픽(Topic), 서비스(Service), 액션(Action), 파라미터
- **DDS와 미들웨어:** ROS2가 노드끼리 어떻게 통신하는지 개념만 이해합니다
- **rclpy 노드 작성:** `rclpy.init()`, 노드 생성, 스핀(spin)의 의미
- **퍼블리셔 / 서브스크라이버:** 메시지를 보내고 받는 가장 기본 패턴
- **서비스 / 액션:** 요청-응답(Service)과 장시간 작업 피드백(Action)의 차이
- **launch 파일:** 여러 노드를 한 번에 띄우는 방법
- **ros2 CLI:** `ros2 topic list`, `ros2 topic echo`, `ros2 node list`, `ros2 service list`로 시스템을 들여다보기

## 실습 과제

### 과제 1 — TurtleBot3를 코드로 움직이기

키보드가 아니라 코드로 로봇을 움직이는 노드를 만듭니다. `geometry_msgs/Twist` 메시지를 `/cmd_vel` 토픽으로 퍼블리시해서 로봇을 전진·회전시킵니다.

- 직진 2초 → 제자리 회전 90도 → 직진 2초를 순서대로 수행하는 노드를 작성합니다
- `ros2 topic echo /cmd_vel`로 내가 보낸 메시지를 확인합니다

### 과제 2 — 센서 값 읽기

TurtleBot3의 LiDAR(`/scan`)나 오도메트리(`/odom`)를 서브스크라이브해서 값을 출력하는 노드를 만듭니다.

- 전방 장애물까지의 거리를 읽어서 0.5m 이내면 정지하는 노드를 만듭니다
- 이걸 과제 1의 이동 노드와 합쳐서 "앞에 벽이 있으면 멈추는" 로봇을 만듭니다

### 과제 3 — 서비스로 LED/상태 제어

간단한 서비스를 만들어서 외부에서 로봇의 상태를 바꿔봅니다. 예를 들어 "멈춰" 서비스를 호출하면 로봇이 정지합니다.

## AI 활용법

- "ROS2에서 Topic이랑 Service랑 Action 차이가 뭐야? 각각 언제 써?"라고 물어서 개념을 정리합니다.
- 코드를 짤 때는 "TurtleBot3를 전진시키는 rclpy 퍼블리셔 코드를 짜줘. 한 줄씩 설명도 해줘"라고 요청합니다.
- "내가 짠 노드가 안 움직여. 이 코드랑 이 에러를 봐줘"라고 구체적으로 물어봅니다.
- 개념이 헷갈리면 "ROS2 노드를 식당에 비유해서 설명해줘"처럼 비유를 요청하면 이해가 빨라집니다.

## 완료 기준

- [ ] rclpy로 퍼블리셔와 서브스크라이버를 각각 만들 수 있다
- [ ] TurtleBot3를 코드로 움직이고, 센서 값으로 멈추게 할 수 있다
- [ ] Topic / Service / Action의 차이를 자기 말로 설명할 수 있다
- [ ] `learning-log.md`에 이번 챕터에서 배운 것을 정리했다

## 참고 자료

- ROS2 Humble 튜토리얼: https://docs.ros.org/en/humble/Tutorials.html
- rclpy API 문서: https://docs.ros2.org/latest/api/rclpy/
- TurtleBot3 ROS2 예제: https://github.com/ROBOTIS-GIT/turtlebot3
