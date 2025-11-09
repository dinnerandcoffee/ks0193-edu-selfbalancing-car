This file has been moved to edu_labs.
# 09. 문제 해결 및 Q&A

## 자주 발생하는 문제와 해결 방법

### 1. 아두이노 업로드 오류
- USB 케이블/포트 변경, 보드/포트 설정 확인
- 드라이버 재설치, 아두이노 리셋

### 2. 모터가 움직이지 않음
- 배선/핀번호/전원 확인
- PWM 값이 너무 낮으면 모터가 안 움직일 수 있음
- 모터 드라이버 고장 여부 확인

### 3. 센서 인식 오류
- SCL/SDA 연결 확인
- 라이브러리 재설치
- 센서 고정 및 진동 최소화

### 4. 밸런싱 불안정
- PID 튜닝값(Kp, Ki, Kd) 조절
- 센서 데이터 노이즈 확인
- 모터 출력 부족 시 배터리 교체

### 5. 블루투스 통신 오류
- 페어링 비밀번호/APP/모듈 확인
- TX/RX 핀 교차 여부 확인
- 통신 속도(baudrate) 일치 확인

---

## 실습 중 자주 묻는 질문

**Q. 차가 계속 넘어져요!**
- PID 값 조절, 센서 위치/고정 확인, 모터 출력 확인

**Q. 센서 값이 이상하게 나와요!**
- 배선/핀번호/라이브러리 확인, 센서 초기화 코드 추가

**Q. APP에서 명령이 안 먹혀요!**
- 블루투스 페어링/통신 속도/핀 연결 확인

**Q. 예제 코드가 컴파일 안 돼요!**
- 라이브러리 설치, 코드 오타 확인

---

## 추가 참고 자료
- [Keyestudio 공식 GitHub](https://github.com/keyestudio/KS0193-Self-balancing-Car-Kit)
- [아두이노 PID 라이브러리](https://playground.arduino.cc/Code/PIDLibrary/)
- [MPU6050 센서 정보](https://components101.com/sensors/mpu6050-gyro-accelerometer)
- [L298N 모터 드라이버 정보](https://components101.com/modules/l298n-motor-driver-module)

---

## 커뮤니티/질문
- GitHub Issues, 네이버 카페, 유튜브 댓글 등에서 질문 가능
- 실습 중 궁금한 점은 README에 추가하거나 커밋 메시지로 남겨주세요!
