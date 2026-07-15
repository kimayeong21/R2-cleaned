# R2 로보테크 AI 프로젝트 정리

융합 로보테크 AI 자율주행로봇 개발자 과정 2기에서 진행한 실습과 팀 프로젝트를 모아둔 저장소입니다.

기초 Python 프로젝트부터 데이터 분석, TCP 통신, 로봇 관제 GUI, Arduino 기반 안전 모듈, ROS2와 Spring Boot를 연동한 공기청정 로봇, 군집 협업 피킹·운반 로봇 프로젝트까지 직접 구현한 결과물을 프로젝트별로 정리했습니다.

각 프로젝트는 서로 다른 학습 주제와 구현 목표를 가지고 있어, 아래처럼 프로젝트별로 나누어 확인할 수 있도록 구성했습니다.

## 과정 정보

이 저장소의 프로젝트들은 `융합 로보테크 AI 자율주행로봇 개발자 과정 2기`를 진행하며 작성한 결과물입니다. 과정은 미래융합교육원과 트위니에서 운영되었고, 기간은 2025.12.30부터 2026.07.16까지입니다.

## 다룬 기술

Python을 중심으로 파일 입출력, 객체지향 구조, GUI 구현을 학습했고, pandas를 활용해 CSV 데이터를 전처리하고 분석하는 실습을 진행했습니다.

네트워크 파트에서는 TCP Socket을 이용해 클라이언트와 서버가 통신하는 구조를 구현했으며, 여러 사용자가 동시에 접속하는 상황을 처리하기 위해 멀티스레딩도 함께 다뤘습니다.

로봇 제어 영역에서는 TurtleBot3 제어, 경로 탐색, 센서 연동을 실습했습니다. ROS와 ROS2의 Topic, Service, Action, Navigation 개념도 프로젝트 흐름 안에서 함께 학습했습니다.

임베디드 파트에서는 Arduino와 ESP8266을 활용해 센서 데이터를 수집하고, PyQt5 GUI로 실시간 모니터링 화면을 구성했습니다. 추가 프로젝트에서는 MQTT, Spring Boot, MySQL, Thymeleaf를 함께 사용해 로봇 데이터를 웹 대시보드로 연결했고, OpenCV ArUco와 엔코더 오도메트리를 결합해 다중 로봇 추종 시스템도 구현했습니다.

## 프로젝트 구성

이 저장소는 다음 7개의 프로젝트로 나뉩니다.

1. [탑뷰 미로 탈출 게임](#project-01)
2. [지역별 교통사고 건수 분석 프로그램](#project-02)
3. [TCP 소켓 기반 마피아 게임](#project-03)
4. [로봇 경로 탐색 통합 관제 GUI](#project-04)
5. [자율주행자동차 보조안전모듈](#project-05)
6. [공기질 연동 자율주행 공기청정 로봇](#project-06)
7. [군집 협업 자율 피킹·운반 로봇](#project-07)

---

<a id="project-01"></a>

## 프로젝트 01. 탑뷰 미로 탈출 게임

### 프로젝트 개요

텍스트 파일로 구성된 맵을 불러와 플레이어가 미로를 탐색하는 Python 콘솔 게임입니다. 맵, 몬스터, 플레이어, 아이템 기능을 모듈로 나누어 구현했고, 단순 출력형 게임 안에서도 상태 변화와 이벤트 처리가 자연스럽게 이어지도록 구성했습니다.

### 주요 구현 내용

- 20x20 텍스트 맵 로드
- 플레이어 이동 및 공격 처리
- 몬스터 랜덤 이동
- 회복, 공격력, 방어막 아이템 적용
- 스테이지 클리어 및 종료 조건 처리

### 사용 기술

Python, File I/O, 객체지향 프로그래밍, 콘솔 UI

### 관련 폴더

`Game/`

---

<a id="project-02"></a>

## 프로젝트 02. 지역별 교통사고 건수 분석 프로그램

### 프로젝트 개요

교통사고 공공데이터를 읽어 지역별 사고 건수를 확인하고, PyQt5 화면에서 조회 및 수정할 수 있도록 만든 데이터 분석 프로그램입니다. 데이터 전처리와 GUI 구성을 함께 다루며, 분석 결과를 사용자가 확인하기 쉬운 형태로 정리하는 데 중점을 두었습니다.

### 주요 구현 내용

- CSV 파일 로드 및 전처리
- 지역별 사고 건수 조회
- PyQt5 기반 데이터 표시 화면 구성
- 데이터 수정 인터페이스 구현
- 분석 결과 시각화

### 사용 기술

Python, PyQt5, pandas, CSV

### 관련 폴더

`Data/`

---

<a id="project-03"></a>

## 프로젝트 03. TCP 소켓 기반 마피아 게임

### 프로젝트 개요

여러 사용자가 서버에 접속해 함께 진행하는 터미널 기반 마피아 게임입니다. TCP 소켓 통신과 멀티스레딩을 활용해 클라이언트 접속, 역할 배정, 낮/밤 페이즈, 투표와 처형 흐름을 관리했습니다.

### 주요 구현 내용

- TCP 서버/클라이언트 구조 설계
- 다중 클라이언트 접속 처리
- 마피아, 시민, 경찰 등 역할 기능 구현
- 낮/밤 페이즈 전환
- 투표, 처형, 채팅 이벤트 처리

### 사용 기술

Python, TCP Socket, 멀티스레딩, 서버/클라이언트 구조

### 관련 폴더

`TCP/`

---

<a id="project-04"></a>

## 프로젝트 04. 로봇 경로 탐색 통합 관제 GUI

### 프로젝트 개요

TurtleBot3를 제어하고 경로 탐색 결과를 확인할 수 있는 로봇 관제 프로그램입니다. Flask API, MySQL, PyQt5 GUI를 연결해 로봇 상태와 경로 정보를 관리할 수 있도록 구성했습니다.

### 주요 구현 내용

- TurtleBot3 제어 흐름 구성
- ROI 기반 경로 탐색 기능 협업
- 장애물 감지 기능 연동
- Flask REST API 서버 구성
- MySQL 기반 데이터 저장
- PyQt5 관제 화면 구성

### 사용 기술

Python, Flask, HTTP REST API, MySQL, PyQt5, TurtleBot3, ROS

### 관련 폴더

`TB3/`

---

<a id="project-05"></a>

## 프로젝트 05. 자율주행자동차 보조안전모듈

### 프로젝트 개요

Arduino와 ESP8266을 활용해 차량 주변의 거리와 환경 정보를 감지하는 보조 안전 시스템입니다. 초음파 센서, 온습도 센서, 조도 센서, 소음 센서에서 받은 값을 PC GUI로 전송하고, 위험 상황을 LCD, LED, 부저로 알릴 수 있도록 구성했습니다.

### 주요 구현 내용

- 초음파 센서 기반 거리 측정
- 온도, 습도, 조도, 소음 데이터 감지
- Arduino 보드 3개 연동
- WiFi 기반 UDP / HTTP 통신
- PyQt5 실시간 모니터링 화면 구성
- LCD, LED, 부저 경보 출력

### 시스템 구성

Board1은 4방향 근접 거리를 측정하고 UDP로 데이터를 전송합니다. Board2는 온도, 습도, 조도, 소음 데이터를 감지해 환경 상태를 확인하는 역할을 합니다. Board3는 LCD, LED, 부저를 이용해 위험 상황을 물리적으로 알립니다. Python GUI는 각 보드에서 전달된 데이터를 받아 실시간으로 보여주는 모니터링 화면입니다.

### 사용 기술

Arduino Uno, ESP8266, HC-SR04, DHT11, LDR, Sound Sensor, Python, PyQt5, UDP, HTTP

### 관련 폴더

`Arduino+UDP/`

---

<a id="project-06"></a>

## 프로젝트 06. 공기질 연동 자율주행 공기청정 로봇

### 프로젝트 개요

미세먼지 센서 데이터와 TurtleBot3 자율주행을 연결해 오염 구역을 찾아가고, 공기청정 동작과 상태 모니터링까지 이어지도록 만든 통합 로봇 시스템입니다. ROS2는 로봇 이동과 센서 흐름을 담당하고, Spring Boot 웹 서버는 로봇 상태와 미세먼지 정보를 대시보드로 보여주는 역할을 맡습니다.

원본 TBPJ 프로젝트의 핵심은 `센서 수집 -> MQTT 전달 -> ROS2 판단 -> 자율주행 -> 웹 대시보드 확인` 흐름입니다. ESP01과 PMS7003 센서가 미세먼지 값을 전달하면, ROS2 노드가 오염도를 분석하고 TurtleBot3가 오염 구역으로 이동합니다. 웹에서는 로봇 위치, 배터리, 이동 경로, 구역별 PM1.0 / PM2.5 / PM10 정보를 확인할 수 있도록 구성했습니다.

### 주요 구현 내용

- PMS7003과 ESP01에서 수집한 미세먼지 데이터를 MQTT 브로커로 전달
- ROS2 `air_clean_robot`, `dust_mapping` 패키지로 센서 데이터와 로봇 제어 흐름 구성
- A* 경로 탐색과 Pure Pursuit 기반 TurtleBot3 자율주행
- AMCL, LiDAR, SLAM 맵을 활용한 위치 추정과 경로 생성
- PM2.5 기준에 따라 이동·청정·복귀를 수행하는 FSM 구성
- Spring Boot 대시보드에서 로봇 위치, 배터리, 경로, 구역별 PM 데이터 표시
- MySQL과 Thymeleaf 기반의 로봇 상태 조회 및 명령 전달 기능

### 사용 기술

ROS2 Humble, TurtleBot3 Waffle Pi, Python, Nav2, Cartographer SLAM, AMCL, MQTT, Mosquitto, Spring Boot, Java 21, MySQL, Thymeleaf, ROSBridge, Three.js, Cloudflare Tunnel

### 관련 폴더

`TBPJ/`

---

<a id="project-07"></a>

## 프로젝트 07. 군집 협업 자율 피킹·운반 로봇

### 프로젝트 개요

PACK(Precise Picking · Autonomous Arm · Collaborative Convoy · Kit)은 리더 로봇 1대와 팔로워 로봇 2대가 역할을 나누어 피킹과 운반을 수행하는 최종 프로젝트입니다. TurtleBot3 Waffle Pi 기반 리더는 자율주행으로 적재 위치까지 이동하고, eye-in-hand 카메라와 6축 로봇팔을 이용해 물체를 집어 팔로워에게 적재합니다. F1과 F2 팔로워는 앞차의 ArUco 마커를 추종하다가, 적재가 끝난 뒤에는 각자 지정된 위치까지 독립적으로 이동하도록 구성했습니다.

이 프로젝트는 고가의 로봇팔을 여러 대 배치하기 어려운 환경을 가정하고, 로봇팔이 달린 리더는 피킹을 담당하며 저가형 팔로워는 운반을 맡는 구조로 설계했습니다. 고정 컨베이어 중심의 자동화가 아니라, 이동 로봇이 직접 찾아가고 집고 나르는 흐름을 목표로 했습니다.

전체 미션은 `FORMATION_WAIT -> GO_TO_LOAD_1 -> F1 적재 -> F1 단독 이동 -> F2 A* 접근 -> 2차 적재 -> 리더 복귀 -> MISSION_COMPLETE` 흐름으로 동작합니다. 리더의 자율주행, 로봇팔 피킹, 팔로워 추종, A* 경로 계획, 웹 대시보드 관제를 하나의 통합 시나리오로 연결했습니다.

### 주요 구현 내용

- TurtleBot3 Waffle Pi 기반 리더 자율주행과 미션 상태머신 구성
- eye-in-hand 카메라 색상 검출과 IK 기반 6축 로봇팔 자동 피킹
- Arduino Uno, PCA9685, Raspberry Pi, MQTT, USB Serial을 연결한 로봇팔 제어
- 벽면 ArUco 마커와 OpenCV solvePnP를 활용한 공용 좌표계 위치 추정
- 쿼드러처 엔코더 오도메트리와 마커 측위를 결합한 팔로워 위치 보정
- F1은 리더 후면 마커를 추종하고, F2는 F1 후면 마커를 추종하는 군집 대형 구성
- F2의 접근·복귀 구간에 A* 경로 계획과 Pure Pursuit 기반 주행 적용
- mode manager와 command mux를 사용해 로봇별 명령이 충돌하지 않도록 제어
- Flask와 rosbridge 기반 웹 대시보드에서 3대 로봇 상태와 미션 제어 화면 제공
- 마커 맵, 로봇 위치, 주행 궤적을 확인할 수 있는 PC 모니터링 도구 구성

### 시스템 구성

| 구성 | 역할 | 주요 내용 |
| --- | --- | --- |
| 리더 TB3 | 자율주행, 피킹, 미션 지휘 | TurtleBot3 Waffle Pi, 6축 로봇팔, Pi Camera, ROS2 Nav2 |
| F1 팔로워 | 리더 추종 후 단독 이동 | Arduino 4WD, 쿼드러처 엔코더, Raspberry Pi, ArUco 추종 |
| F2 팔로워 | F1 추종 후 A* 경로 이동 | Arduino 4WD, A* Planner, command mux, 재타겟 추종 |
| 웹 대시보드 | 상태 관제와 미션 제어 | Flask, rosbridge, JavaScript, map view |

### 사용 기술

ROS2 Humble, Python, OpenCV, ArUco, solvePnP, TurtleBot3 Waffle Pi, Nav2, A*, Pure Pursuit, Arduino Uno, Arduino 4WD, PCA9685, Raspberry Pi, MQTT, Mosquitto, USB Serial, Flask, rosbridge, JavaScript, SLAM, YAML

### 관련 폴더

`PACK/`

---

## 저장소 구조

```text
R2-cleaned/
├── README.md
├── Game/
│   └── Game/
├── Data/
│   └── Data/
├── TCP/
│   └── TCP/
├── TB3/
│   └── RB/
├── Arduino+UDP/
│   └── Arduino+UDP/
├── TBPJ/
│   ├── ros2/
│   │   ├── air_clean_robot/
│   │   └── dust_mapping/
│   └── spring-boot/
└── PACK/
    ├── final_ws/
    │   └── src/final_mission_robot/
    ├── from_tb3/
    ├── from_f1/
    │   └── encoder_bridge/
    ├── from_f2/
    │   └── encoder_bridge/
    ├── robot_dashboard_flask/
    ├── images/
    ├── RobotArmCase.ino
    ├── auto_pick.py
    ├── f1_car.ino
    ├── map_pose_viewer_pc.py
    └── mqtt_gateway_lite.py
```
