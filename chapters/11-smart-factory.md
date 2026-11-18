# Chapter 11 — 스마트 팩토리와 공정 자동화

**기간:** 2주 | **전제:** Chapter 10

이 챕터의 목표는 **로봇이 공장에서 어떻게 쓰이는지**를 배우는 것입니다. PLC·SCADA 연동, MES·ERP 시스템, OPC UA 프로토콜, Factory Automation Workflow, Digital Twin 기초를 다룹니다. 산업용 하드웨어가 없으므로 개념과 시뮬레이션 중심으로 진행합니다.

## 학습 목표

- PLC와 SCADA의 역할을 설명할 수 있다
- MES와 ERP가 공장에서 무슨 일을 하는지 이해한다
- OPC UA 프로토콜의 개념을 이해한다
- Factory Automation Workflow를 설명할 수 있다
- Digital Twin의 개념을 이해한다

## 학습 내용

### 1주차 — PLC·SCADA·MES·ERP

- **PLC (Programmable Logic Controller):** 공장 설비를 제어하는 산업용 컴퓨터. 센서 입력 → 로직 → 액추에이터 출력의 흐름
- **SCADA:** 공장 전체를 모니터링하고 제어하는 시스템. PLC들의 상태를 한 화면에서 보는 구조
- **MES (Manufacturing Execution System):** 생산 실행 시스템. 작업 지시, 실적 수집, 품질 관리
- **ERP (Enterprise Resource Planning):** 전사 자원 관리. 주문, 재고, 생산 계획을 통합 관리
- **계층 구조:** 현장(PLC) → SCADA → MES → ERP로 올라가는 자동화 피라미드 개념
- **실습:** 공장 자동화 피라미드를 그림으로 그리고, 각 계층에서 로봇이 어디에 위치하는지 정리한다

### 2주차 — OPC UA와 Digital Twin 기초

- **OPC UA:** 산업용 통신 프로토콜. 서로 다른 제조사의 설비가 데이터를 주고받는 표준
- **OPC UA 서버·클라이언트:** Python `opcua` 라이브러리로 간단한 OPC UA 서버를 만들고 데이터를 주고받는 실습
- **Digital Twin 기초:** 실제 공장을 가상 공간에 똑같이 만들어서 시뮬레이션하는 개념. 왜 만드는지, 어디에 쓰는지
- **실습:** Python으로 OPC UA 서버를 띄우고, 가상의 생산 라인 데이터(온도, 생산량, 설비 상태)를 퍼블리시하고 클라이언트로 읽어본다. ROS2와 연결해서 로봇 상태도 함께 OPC UA로 내보내본다

## 실습 과제

### 과제 1 — 공장 자동화 계층 정리

자동화 피라미드(PLC → SCADA → MES → ERP)를 정리하고, 각 계층에서 다루는 데이터의 종류와 주기를 표로 만듭니다. 로봇(ROS2)이 이 계층에서 어디와 연결되는지 표시합니다.

### 과제 2 — OPC UA 서버·클라이언트

Python `opcua` 라이브러리로 OPC UA 서버를 만듭니다. 가상의 생산 라인 노드(설비 온도, 생산 카운트, 설비 상태)를 만들고, 클라이언트에서 주기적으로 읽어서 출력합니다. 값을 바꾸면 클라이언트에도 반영되는지 확인합니다.

### 과제 3 — ROS2 + OPC UA 연동

TurtleBot3의 상태(위치, 배터리, 작업 상태)를 OPC UA 서버의 노드로 내보냅니다. OPC UA 클라이언트에서 로봇 상태를 읽을 수 있는지 확인합니다. 이렇게 하면 공장의 MES가 로봇 상태를 볼 수 있는 구조가 됩니다.

## AI 활용법

- "PLC가 뭐야? 일반 컴퓨터랑 뭐가 달라?"처럼 기초 개념을 물어봅니다.
- "OPC UA가 왜 필요해? Modbus랑 뭐가 달라?"처럼 프로토콜 비교를 물어봅니다.
- "MES랑 ERP 차이가 뭐야? 공장에서 각각 무슨 일을 해?"처럼 시스템 역할을 물어봅니다.
- "Digital Twin이 시뮬레이션이랑 뭐가 달라?"처럼 개념 차이를 물어봅니다.

## 완료 기준

- [ ] 공장 자동화 피라미드를 설명할 수 있다
- [ ] OPC UA 서버·클라이언트를 만들고 데이터를 주고받을 수 있다
- [ ] ROS2 로봇 상태를 OPC UA로 내보낼 수 있다
- [ ] Digital Twin의 개념과 쓰임새를 설명할 수 있다
- [ ] `learning-log.md`에 이번 챕터 내용을 정리했다

## 참고 자료

- OPC UA Python 라이브러리: https://github.com/FreeOpcUa/python-opcua
- OPC UA 공식 문서: https://opcfoundation.org/
- ISA-95 (자동화 계층 표준) 개요
