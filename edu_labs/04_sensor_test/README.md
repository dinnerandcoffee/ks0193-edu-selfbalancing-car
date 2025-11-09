This file has been moved to edu_labs.
# 04. 자이로센서(MPU6050) 테스트

## 목표
- MPU6050 자이로/가속도 센서가 정상적으로 동작하는지 확인
- 센서 데이터를 시리얼 모니터로 출력

---

## 준비물
- 아두이노 보드
- MPU6050 센서
- 점퍼선

---

## 회로 연결
- VCC → 3.3V 또는 5V
- GND → GND
- SCL → A5
- SDA → A4

---

## 라이브러리 설치
1. Arduino IDE에서 [도구] → [라이브러리 관리]
2. "MPU6050" 또는 "Adafruit MPU6050" 검색 후 설치

---

## 예제 코드 업로드
```cpp
#include <Wire.h>
#include <MPU6050.h>

MPU6050 mpu;

void setup() {
  Serial.begin(9600);
  Wire.begin();
  mpu.initialize();
  Serial.println("MPU6050 테스트 시작");
}

void loop() {
  Serial.print("가속도 X: "); Serial.print(mpu.getAccelerationX());
  Serial.print(" Y: "); Serial.print(mpu.getAccelerationY());
  Serial.print(" Z: "); Serial.println(mpu.getAccelerationZ());
  delay(500);
}
```

---

## 시리얼 모니터 확인
- 9600 baudrate로 시리얼 모니터 실행
- X, Y, Z 값이 실시간으로 출력되면 성공

---

## 문제 해결
- 값이 0 또는 이상하면 배선/핀번호/라이브러리 확인
- 센서 인식 오류 시 SCL/SDA 연결 및 라이브러리 재설치

---

## 다음 단계
- 05_motor_control: 모터 드라이버 제어 실습
