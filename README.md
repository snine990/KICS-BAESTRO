# 6G-Guardian: ISAC-based Contactless Athlete Protection System
### 6G ISAC 기반 비접촉 실시간 선수 생체 및 부상 방지 AI 에이전트

![Status](https://img.shields.io/badge/Status-Idea%20Research-blue) ![Tech](https://img.shields.io/badge/Tech-6G%20THz%20%7C%20ISAC%20%7C%20Micro--Doppler-orange)

## 📖 Project Overview (프로젝트 개요)
**6G-Guardian**은 차세대 통신 기술인 **6G(Sixth Generation)**의 핵심 기능인 **ISAC(Integrated Sensing and Communication, 통신-센싱 융합)** 기술을 활용한 스포츠 헬스케어 솔루션입니다.

기존의 웨어러블 센서(Wearable Sensors)가 가진 한계(착용 불편함, 충돌 시 파손 위험, 배터리 문제)를 극복하기 위해, **6G 통신망 자체를 거대한 3D 바이오 스캐너로 활용**합니다. 선수의 신체에 아무것도 부착하지 않은 상태(Device-free)에서 **골격(Skeleton), 근육 미세 떨림(Tremor), 바이탈 사인**을 실시간으로 감지하여 부상을 사전에 예방하는 AI Agent 시스템입니다.

---

## 🏗️ System Architecture (시스템 구조)
본 프로젝트는 **Sensing - Processing - Action**의 3단계 파이프라인으로 구성됩니다.

1.  **Infrustructure:** 경기장에 분산 배치된 **Cell-Free Massive MIMO** 안테나와 사각지대 해소를 위한 **RIS(지능형 반사 표면)**.
2.  **Sensing Layer:** 6G THz 대역의 초광대역 특성을 이용한 **High-Resolution Radar Imaging**.
3.  **Edge AI:** 수집된 데이터를 **MEC(Mobile Edge Computing)**에서 0.1ms 이내 초저지연 처리.
4.  **AI Agent:** Digital Twin 모델과 실시간 데이터를 비교하여 부상 위험도(Risk Score) 산출 및 경기 중단 판단.

---

## 📡 Technical Specification: Sensing Layer
> 본 프로젝트의 핵심 기술인 **6G 기반 생체 데이터 측정 원리**에 대한 기술 명세입니다.

### 1. Target Parameters (측정 데이터)

| Category | Description | Key Metrics |
| :--- | :--- | :--- |
| **Skeletal Kinematics** | 3D 골격 및 운동학적 데이터 | 19개 주요 관절 좌표 $(x,y,z)$, 관절 꺾임 각도, 비대칭성 |
| **Muscle Micro-Tremor** | 근육 미세 떨림 및 표면 변형 | 8~12Hz 대역의 미세 진동(Tremor), 피부 표면 부피 변화 |
| **Vital Signs** | 비접촉 생체 신호 | 흉곽 변위를 통한 호흡수, 피부 미세 진동을 통한 심박수 |

### 2. Methodologies & Principles (핵심 기술 및 원리)

#### A. High-Resolution CSI Sensing (공간 분해능 극대화)
6G의 광대역폭을 활용하여 수신된 신호의 **CSI(Channel State Information)**를 분석, 인체의 3D 형상을 복원합니다.

* **Physics:** 레이더의 거리 분해능($\Delta R$)은 대역폭($B$)에 반비례합니다.
    $$\Delta R = \frac{c}{2B}$$
    *(Here, $c$ is speed of light, $B$ is Bandwidth)*
    * **LTE (20MHz):** 분해능 ~7.5m (식별 불가)
    * **6G THz (10GHz+):** 분해능 **~1.5cm** (관절 및 손가락 마디 식별 가능)

#### B. Micro-Doppler Analysis (속도 성분 분해)
선수의 이동(Global Motion)과 근육의 떨림(Local Motion)이 만드는 주파수 변이(Doppler Shift)를 분리합니다.

* **Model:**
    $$f_{D,i}(t) = \frac{2 v_i(t)}{\lambda} \cos \theta_i(t)$$
    이를 통해 STFT(Short-Time Fourier Transform) 기반 **Spectrogram**을 생성, 근육 경련의 고유 패턴(Signature)을 AI로 분류합니다.

#### C. Phase-based Displacement Tracking (위상 기반 변위 추적)
테라헤르츠파의 짧은 파장($\lambda \approx 1mm$)을 이용하여 거리 측정보다 정밀한 **위상(Phase) 변화**를 측정합니다.

* **Sensitivity:**
    $$\Delta \phi = \frac{4\pi \Delta d}{\lambda}$$
    근육이 **0.1mm($\Delta d$)**만 떨려도, 위상은 약 **72도($\Delta \phi$)** 변하므로 광학 카메라로 보이지 않는 미세 떨림을 명확하게 감지합니다.

---

## 📚 Key References (관련 연구 및 근거)
본 아이디어는 다음의 선행 연구 및 기술적 타당성(Feasibility)에 기반합니다.

* **Pose Estimation:** *RF-Pose: 3D Human Pose Estimation Across Occlusions (MIT CSAIL, CVPR 2018)*
* **3D Mesh:** *mmMesh: Towards 3D Real-Time Body Mesh Reconstruction Using mmWave Radar (MobiSys 2021)*
* **Tremor Detection:** *Non-contact Tremor Detection via mmWave Radar*
* **Gait Analysis:** *Human Gait Recognition Using Micro-Doppler Radar Signatures (IEEE Sensors)*

---

## 🚀 Expected Effect (기대 효과)
* **Objective Decision:** 인간 심판의 주관적 판단이 아닌, 데이터 기반의 객관적 부상 위험도 판정.
* **Prevention:** 사고 발생 후 조치가 아닌, **전조 증상(Precursor) 감지를 통한 사전 예방**.
* **Zero-Interference:** 선수 경기력에 영향을 주지 않는 완전 비접촉(Device-free) 방식.

---

### 📝 Author & License
* **Project Lead:** [본인 영문 이름] (Kyungpook National Univ. Mobile Engineering)
* **Contact:** [이메일 주소]
* **License:** This project is licensed under the MIT License.
