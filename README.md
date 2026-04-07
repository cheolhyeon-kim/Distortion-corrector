# Distortion-corrector
Correct distorted images using OpenCV

## 개요 (Features)
본 프로그램은 카메라의 고유 파라미터를 추정하고, 광각 렌즈에서 발생하는 왜곡을 수학적으로 보정하기 위해 개발되었습니다.
영상 기반 프레임 추출: 동영상 파일에서 체스보드가 잘 검출되는 최적의 프레임을 수동으로 선택할 수 있습니다.

카메라 캘리브레이션: 선택된 이미지들을 분석하여 초점 거리($f_x, f_y$), 주점($c_x, c_y$), 왜곡 계수($k_1, k_2, \dots$)를 산출합니다. 
실시간 왜곡 보정: 산출된 카메라 매트릭스를 적용하여 왜곡된 영상을 평평하게 펴주는 정교화(Rectification) 작업을 수행합니다. 

### 카메라 캘리브레이션 결과 스마트폰 광각 모드(0.5x)로 촬영된 영상을 분석한 결과이며, 
### 총 11장의 이미지가 사용되었습니다. 

### 추출된 파라미터
<img width="1053" height="179" alt="image" src="https://github.com/user-attachments/assets/56e40bcb-3515-4c09-8b86-ad58eb94434b" />
RMS error = 0.91300450265738 

K = np.array([[1.09732511e+03, 0, 5.93988134e+02],
              [0, 1.08699723e+03, 2.65455875e+02],
              [0, 0, 1]]) # Derived from `calibrate_camera.py`
              
dist_coeff = np.array([-0.81089462, 1.5163688, 0.02975743, 0.01103372, -3.78697131])

-Before-
<img width="1454" height="898" alt="image" src="https://github.com/user-attachments/assets/9375cbc9-0b06-4b37-ba3f-fd0b7eb11f15" />
-After-
<img width="1592" height="865" alt="image" src="https://github.com/user-attachments/assets/282988f1-4bc2-4fe8-9461-983c5110d2f0" />

렌즈 왜곡 보정 데모 광각 렌즈 특유의 볼록한 왜곡이 보정 후 직선으로 바르게 펴진 것을 확인할 수 있습니다.
원본 영상 (Original)설명: 화면 가장자리의 체스보드 선들이 렌즈 바깥쪽으로 둥글게 휘어 보임
보정 영상 (Rectified)설명: 캘리브레이션 결과를 적용하여 곡선으로 보이던 체스보드 격자가 직선으로 보정됨.


## 실행 환경 및 방법
Language: Python 3.10.0
Library: OpenCV, NumPy

