This file has been moved to edu_labs.
# 02. 회로 연결 및 테스트

## 목표
- 모든 부품을 아두이노에 올바르게 연결
- 전원 공급 및 기본 동작 확인

## 회로 연결 가이드

### 1. 모터 드라이버(L298N) 연결
- IN1, IN2, IN3, IN4: 아두이노 디지털 핀(D4~D7 등)
- ENA, ENB: PWM 핀(D5, D6 등)
- OUT1, OUT2, OUT3, OUT4: DC 모터 2개 연결
- VCC, GND: 배터리 박스 연결

### 2. MPU6050 자이로/가속도 센서 연결
- VCC: 3.3V 또는 5V
- GND: GND
- SCL: 아두이노 A5
- SDA: 아두이노 A4

### 3. 아두이노 전원 연결
- USB 또는 배터리 박스(6~9V)

### 4. 기타 부품
- 블루투스 모듈(옵션): TX/RX 핀 연결

---

## 회로도 참고
- [공식 회로도 PDF](https://github.com/keyestudio/KS0193-Self-balancing-Car-Kit/tree/main/02.%20libraries)
- [MPU6050 연결 예시](https://components101.com/sensors/mpu6050-gyro-accelerometer)
- [L298N 연결 예시](https://components101.com/modules/l298n-motor-driver-module)

---

## 테스트 방법
1. 모든 배선이 올바른지 재확인
2. 아두이노에 USB 연결 후 전원 공급
3. 예제 코드 업로드(다음 챕터에서 진행)
4. 모터/센서가 정상적으로 동작하는지 확인

---

## 문제 해결
- 모터가 움직이지 않으면 배선/전원/핀 번호 확인
- 센서 인식 오류 시 SCL/SDA 연결 및 라이브러리 확인

---

## 다음 단계
- 03_arduino_basics: 아두이노 IDE 설치 및 기본 예제
