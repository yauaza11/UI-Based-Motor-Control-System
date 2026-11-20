# UI 기반 모터 제어 시스템
(UI-Based Motor Control System)

## 1. 프로젝트 개요 (Overview)

Qt 기반 사용자 인터페이스, Raspberry Pi 기반 통신 게이트웨이,
STM32 기반 모터 제어기를 연동한 모터 속도 제어 및
실시간 모니터링 시스템입니다.

상위 제어 소프트웨어와 하위 제어기 간 통신 인터페이스를
구현하고, 센서 피드백을 기반으로 모터 속도를 제어하였습니다.

[시연 영상 (Demo Video)](https://www.youtube.com/watch?v=cuFv07TlypM)

## 2. 주요 기능 (Features)

- Qt 기반 모터 속도 제어 및 상태 모니터링
- Raspberry Pi 기반 UDP-CAN 통신 게이트웨이
- 엔코더 피드백 기반 PID 모터 속도 제어
- CSV 기반 제어 데이터 로깅 및 성능 분석
- CSI 카메라 기반 UDP 영상 스트리밍

## 3. 시스템 아키텍처 (System Architecture)

- **Application Layer (PC)**
  - C++/Qt 기반 사용자 인터페이스
  - 멀티스레드 기반 데이터 처리

- **Gateway Layer (Raspberry Pi)**
  - Linux SocketCAN 및 UDP 기반 데이터 중계

- **Control Layer (STM32)**
  - STM32 HAL 기반 주변장치 제어
  - 엔코더 데이터 수집 및 PID 모터 속도 제어

## 4. 기술 스택 (Tech Stack)

| Category | Technologies |
| --- | --- |
| Language | C, C++ |
| OS | Linux |
| Framework & Library | Qt, STM32 HAL |
| Communication | UDP, CAN |
| Hardware | STM32F103, Raspberry Pi 4, CSI Camera, L298N |

## 5. 주요 설계 및 개발 성과 (Key Achievements)

### 5.1. 이종 플랫폼 간 통신 연동

- Raspberry Pi를 통신 게이트웨이로 활용
- UDP와 CAN 간 데이터 중계 구현
- 상위 제어 SW와 하위 MCU 간 통신 연동

### 5.2. 멀티스레드 기반 실행 구조 설계

- 영상 스트리밍과 제어 데이터 처리 간 간섭 최소화
- 영상 스트리밍 및 제어 데이터 처리 스레드 분리
- GUI, 영상 스트리밍 및 제어 데이터 처리의
  독립적 실행 구조 확보

### 5.3. PID 기반 모터 속도 제어

- 엔코더 피드백 기반 PID 제어 알고리즘 구현
- CSV 기반 제어 데이터 분석 및 PID 게인 튜닝
- 목표 RPM 대비 오차율 5% 이내 달성
