# Chapter 00 — 환경 설정

**기간:** 1주 | **전제:** 없음

이 챕터의 목표는 앞으로 16개 챕터를 진행할 **개발 환경을 만드는 것**입니다. 환경이 꼬이면 나중에 계속 시간을 뺏기므로, 여기서 확실히 잡고 넘어갑니다.

## 학습 목표

- Docker로 ROS2 Humble(Ubuntu 22.04) 개발 환경을 만든다
- VS Code에서 컨테이너 안의 코드를 편집·디버깅할 수 있다
- Gazebo 시뮬레이터를 띄우고 TurtleBot3를 움직여본다
- Git으로 학습 기록을 관리하는 습관을 만든다

## 환경 구성

### 1. Docker 설치

Mac이라면 Docker Desktop을 설치합니다. Windows라면 WSL2 + Docker Desktop, Linux라면 Docker Engine을 설치합니다.

### 2. ROS2 개발용 컨테이너

ROS2 Humble 이미지를 받아서 개발용 컨테이너를 만듭니다. 공식 이미지를 쓰는 것이 가장 간단합니다.

```bash
docker pull osrf/ros:humble-desktop
```

컨테이너를 띄울 때는 GUI(Gazebo, RViz)를 쓸 수 있게 X11 포워딩을 설정해야 합니다. Mac에서는 XQuartz를 설치하고 `xhost`로 접근을 허용한 뒤 실행합니다.

```bash
docker run -it --rm \
  -e DISPLAY=host.docker.internal:0 \
  -v /tmp/.X11-unix:/tmp/.X11-unix \
  -v ~/ros2_ws:/root/ros2_ws \
  --name ros2-dev \
  osrf/ros:humble-desktop
```

컨테이너 안에서 ROS2가 동작하는지 확인합니다.

```bash
source /opt/ros/humble/setup.bash
ros2 --help
```

### 3. 워크스페이스 만들기

ROS2 작업 공간(workspace)을 만들고 빌드 도구를 익힙니다.

```bash
mkdir -p ~/ros2_ws/src
cd ~/ros2_ws
colcon build
source install/setup.bash
```

### 4. VS Code 연결

VS Code의 Dev Containers 확장으로 컨테이너 안에 직접 붙어서 코드를 편집합니다. 확장 없이 해도 되지만, Dev Containers를 쓰면 디버깅과 터미널이 편해집니다.

### 5. Gazebo + TurtleBot3 시뮬레이션

TurtleBot3 시뮬레이션 패키지를 설치하고 Gazebo를 띄워봅니다.

```bash
sudo apt update
sudo apt install -y ros-humble-turtlebot3 ros-humble-turtlebot3-simulations ros-humble-gazebo-ros-pkgs
export TURTLEBOT3_MODEL=waffle_pi
ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py
```

Gazebo 창에 TurtleBot3가 보이면 성공입니다. 다른 터미널에서 로봇을 움직여봅니다.

```bash
ros2 run teleop_twist_keyboard teleop_twist_keyboard
```

방향키로 로봇이 움직이면 환경 설정 완료입니다.

## 실습 과제

1. Docker 컨테이너 안에서 ROS2 Humble이 동작하는 것을 확인하고, `ros2 topic list` 결과를 기록한다
2. TurtleBot3를 Gazebo에서 띄우고 키보드로 1분간 움직여본다
3. VS Code Dev Containers로 컨테이너에 붙어서 `ros2_ws`를 열어본다
4. 이 저장소를 fork/clone하고, `learning-log.md` 파일을 만들어서 오늘 한 일을 한 줄로 적는다 (앞으로 매 챕터 끝마다 여기에 기록합니다)

## AI 활용법

- "Docker로 ROS2 Humble 개발 환경을 만들고 싶어. Mac에서 X11 포워딩까지 포함해서 docker run 명령어를 알려줘"처럼 구체적으로 묻습니다.
- 에러가 나면 에러 메시지 전문 + 실행한 명령어를 함께 붙여넣습니다.
- "colcon build가 뭐야? catkin이랑 뭐가 달라?"처럼 배경 개념을 물어서 이해를 넓힙니다.

## 완료 기준

- [ ] Docker 컨테이너 안에서 `ros2 --help`가 동작한다
- [ ] Gazebo에 TurtleBot3가 뜨고 키보드로 움직인다
- [ ] VS Code로 컨테이너 안의 코드를 편집할 수 있다
- [ ] `learning-log.md`에 첫 기록을 남겼다

## 참고 자료

- ROS2 Humble 공식 문서: https://docs.ros.org/en/humble/
- TurtleBot3 e-Manual: https://emanual.robotis.com/docs/en/platform/turtlebot3/overview/
- Docker 공식 문서: https://docs.docker.com/
