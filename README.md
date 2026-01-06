# 🏋️‍♂️ **AI Smart Gym Project🥈**
> Pose Estimation 기반 운동 인식과 EMG·IMU 센서 융합 분석을 통해
> 실시간 자세 평가와 피드백을 제공하는 AI Smart Gym 시스템


## 📌 1. 프로젝트 목표

- 운동 동작의 **정확한 분류 및 실시간 분석**  
- IMU, EMG 등 센서를 통한 **정량적 운동 데이터 수집**  
- AI 기반 **운동 수행 평가 알고리즘 및 피드백 제공**  
- **Raspberry Pi / Hailo-8 경량화 및 실시간 처리**

---

## 🎬 2. 시연 영상

https://github.com/user-attachments/assets/f4ce4fb4-64c6-46c4-88ab-7b38399b903d

---
 

## 🧠 3. 시스템 아키텍처

<img width="839" height="430" alt="image" src="https://github.com/user-attachments/assets/97e1d978-0dcd-4460-b81d-8fe5502806a3" />
<img width="861" height="485" alt="image" src="https://github.com/user-attachments/assets/eeaca896-b994-43b9-892b-fadff9362e0d" />
 
---
## 🔧 4.핵심 기능

### 🖥 UI (운영)
- PySide6 기반 실시간 오버레이 UI 구성  
- 운동 인식 결과(운동 종류, 카운트, 점수) 즉시 시각화  
- 세션 종료 시 운동 요약 정보 표시 (총 횟수, 평균 점수)
- 
### ⚙️ Analysis (인식 / 분석)
- YOLOv8-Pose(ONNX) 기반 포즈 키포인트 추출 (COCO17)
- 무릎·힙 관절 각도 계산 및 스무딩/클램프 처리로 안정화
- 각도 기반 FSM 카운트 로직 설계 및 점수 산출
- TCN 기반 시퀀스 모델을 통한 운동 동작 인식
- OpenCV 영상 전처리 및 실시간 결과 출력 파이프라인 구성
- Hailo-8 가속 환경에서 실시간 추론 성능(FPS·지연) 고려한 처리 구조 설계

### 🗃 Data (기록)
- 운동 세션별 카운트·점수 요약 데이터 SQLite 저장
- 최소 컬럼 구조로 기록해 추후 분석·확장 가능하도록 설계
- 데모 시나리오 기준(3회 수행) 데이터 로깅 흐름 구현

 ---
## 🛠 5. 기술 요약
- **UI**: PySide6 (Qt for Python), OpenCV Overlay  
- **AI / Vision**: YOLOv8-Pose, TCN, PyTorch, ONNX  
- **Sensor**: IMU, EMG, BLE 통신  
- **Data**: SQLite
- **Embedded**: Raspberry Pi 5, Hailo-8, Linux
