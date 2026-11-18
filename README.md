# Physical AI 독학 커리큘럼

> KANT 피지컬 AI 부트캠프 커리큘럼을 AI와 함께하는 독학 로드맵으로 재구성했습니다.
> 부트캠프에 가지 않고, AI를 튜터 삼아 로봇 엔지니어가 되는 길.

[![Chapters](https://img.shields.io/badge/chapters-17-blue)](#로드맵)
[![Duration](https://img.shields.io/badge/duration-~40%20weeks-green)](#로드맵)
[![ROS2](https://img.shields.io/badge/ROS2-Humble-blue)](https://docs.ros.org/en/humble/)
[![License](https://img.shields.io/badge/license-MIT-lightgrey)](LICENSE)

## 시작하기

1. [Chapter 00](chapters/00-setup.md)부터 순서대로 진행합니다. 앞 챕터가 뒤 챕터의 전제 조건입니다.
2. 각 챕터는 **개념 → 실습 → 완료 기준**으로 구성되어 있습니다. 실습을 끝내고 다음 챕터로 넘어가세요.
3. 진행 상황은 [learning-log.md](learning-log.md)에 기록합니다.

**대상:** 프로그래밍 경험이 있는 개발자 (특히 백엔드 개발자). Python 기초가 있으면 더 빠르게 갑니다.
**방식:** 챕터별로 배우고, 각 챕터 끝에 직접 만드는 실습 프로젝트로 마무리합니다.
**소요:** 주 10~15시간 기준, 전체 약 40주(9~10개월). 풀타임으로 하면 더 빨리 끝낼 수 있습니다.

## 로드맵

### Phase 1 — 기초 (7주)

| 챕터 | 주제 | 기간 |
|---|---|---|
| [00](chapters/00-setup.md) | 환경 설정 — Docker, ROS2, Gazebo, VS Code | 1주 |
| [01](chapters/01-python-ros2.md) | Python·Linux·ROS2 기초 | 2주 |
| [02](chapters/02-3d-perception.md) | 3D 공간 인식과 좌표 변환 | 2주 |
| [03](chapters/03-ai-basics.md) | AI 모델 기초와 로봇 AI 입문 | 2주 |

### Phase 2 — 로봇 제어와 인식 (8주)

| 챕터 | 주제 | 기간 |
|---|---|---|
| [04](chapters/04-arm-control.md) | 로봇팔 제어와 모션 플래닝 | 2주 |
| [05](chapters/05-3d-vision.md) | 3D 비전과 포인트 클라우드 | 2주 |
| [06](chapters/06-vla-intro.md) | VLA 입문 — 모방학습·Diffusion Policy | 2주 |
| [07](chapters/07-slam-nav.md) | SLAM과 자율주행 기초 | 2주 |

### Phase 3 — AI 심화와 시스템 (8주)

| 챕터 | 주제 | 기간 |
|---|---|---|
| [08](chapters/08-robot-ai-rl.md) | 로봇 AI 심화 — VLM·VLA·강화학습 | 2주 |
| [09](chapters/09-driving-project.md) | 자율주행 실전 프로젝트 | 2주 |
| [10](chapters/10-multi-robot.md) | 다중 로봇과 Fleet 관리 | 2주 |
| [11](chapters/11-smart-factory.md) | 스마트 팩토리와 공정 자동화 | 2주 |

### Phase 4 — 실전과 포트폴리오 (17주)

| 챕터 | 주제 | 기간 |
|---|---|---|
| [12](chapters/12-digital-twin.md) | Digital Twin과 시뮬레이션 | 3주 |
| [13](chapters/13-sim-to-real.md) | Sim-to-Real과 강화학습 심화 | 3주 |
| [14](chapters/14-vla-foundation.md) | VLA와 Foundation Model 실전 | 3주 |
| [15](chapters/15-final-project.md) | 최종 프로젝트 — 나만의 Physical AI 시스템 | 6주 |
| [16](chapters/16-portfolio.md) | 포트폴리오와 취업 준비 | 2주 |

## AI와 함께 배우는 법

이 커리큘럼은 AI를 **튜터**로 쓰는 것을 전제로 합니다. 각 챕터마다 "AI 활용법"이 적혀 있습니다. 공통 원칙은 다섯 가지입니다.

1. **개념은 AI에게 묻고, 손으로 확인합니다.** "ROS2 Topic이 뭐야?"라고 묻고, 답을 들은 뒤 직접 노드를 짜서 돌려봅니다. 코드만 받고 이해하지 않으면 남는 게 없습니다.
2. **에러는 그대로 붙여넣습니다.** 에러 메시지 + 내가 한 일을 함께 주면 AI가 원인을 짚어줍니다. "안 돼"가 아니라 "이 명령을 쳤더니 이 에러가 났어"라고 구체적으로 말합니다.
3. **구현은 AI와 페어로 합니다.** "이 기능을 구현하고 싶은데, 먼저 설계를 같이 짜보자"라고 시작합니다. AI가 짠 코드는 한 줄씩 읽고 이해한 뒤에 씁니다.
4. **매 챕터 끝에는 AI 없이 복습합니다.** 핵심 개념을 AI 도움 없이 자기 말로 정리해봅니다. 설명할 수 없으면 아직 모르는 것입니다.
5. **막히면 범위를 좁혀서 질문합니다.** "SLAM이 안 돼"가 아니라 "Gazebo에서 TurtleBot3로 SLAM을 돌렸는데 맵이 안 그려져. 이 로그가 나와"처럼 좁혀서 묻습니다.

## 환경

| 항목 | 내용 |
|---|---|
| OS | Ubuntu 22.04 (ROS2 Humble 기준). Mac에서는 Docker로 Ubuntu 컨테이너를 띄워서 진행합니다. |
| 필수 | Docker, VS Code, Git, Python 3.10+ |
| 시뮬레이터 | Gazebo (기본), RViz (시각화) |
| 선택 | NVIDIA GPU가 있는 PC 또는 클라우드 GPU (Isaac Sim을 쓸 때만 필요) |
| 실물 로봇 (없어도 됨) | TurtleBot3, Jetson Orin NX, LiDAR, RGB-D 카메라. 없어도 시뮬레이션으로 전 과정을 진행할 수 있습니다. |

자세한 환경 설정은 [Chapter 00](chapters/00-setup.md)을 보세요.

## 원본 커리큘럼과의 차이

- **Isaac Sim → Gazebo 대안:** Mac(Apple Silicon)에서는 Isaac Sim이 안 돌아갑니다. 12~14챕터는 Gazebo 기반으로 진행하고, GPU가 생기면 Isaac Sim으로 갈아탈 수 있게 구조를 잡았습니다.
- **기업 연계 프로젝트 → 자기주도 최종 프로젝트:** 실제 기업 과제는 없으므로, 15챕터에서 스스로 문제를 정의하고 Physical AI 시스템을 만듭니다. 포트폴리오용으로 충분한 규모입니다.
- **PLC·SCADA 실습 → 개념 + 시뮬레이션:** 산업용 하드웨어가 없으므로 개념과 OPC UA 시뮬레이션으로 진행합니다.
- **속도:** 부트캠프는 풀타임 9개월이지만, 이 로드맵은 주 10~15시간을 가정한 40주입니다.

## 참고 자료

- KANT 피지컬 AI 로봇 엔지니어 코스: https://kant-ai-campus.com/ai-physical
- ROS2 공식 문서: https://docs.ros.org/en/humble/
- TurtleBot3 공식 문서: https://emanual.robotis.com/docs/en/platform/turtlebot3/overview/
- NVIDIA Isaac Sim 문서: https://docs.isaacsim.omniverse.nvidia.com/
- OpenVLA: https://github.com/moojink/openvla

## 라이선스

MIT License. 자유롭게 사용하고 수정하세요.
