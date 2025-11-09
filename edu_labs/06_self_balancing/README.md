This file has been moved to edu_labs.
# 06. 자이로+모터 밸런싱 알고리즘 실습

## 목표
- MPU6050 센서와 모터를 결합하여 자이로카의 밸런싱(자세 유지) 동작 구현
- PID 제어 원리 이해 및 실습

---

## 밸런싱 원리
- 센서로 기울기(각도) 측정
- 각도 변화에 따라 모터 속도/방향 제어
- PID 알고리즘으로 오차 보정

---

## 예제 코드 개요
- MPU6050에서 각도 데이터 읽기
- PID 제어로 모터 속도 계산
- 모터 드라이버에 속도/방향 명령 전달

---

## 실습 예제 코드 (개념)
```cpp
#include <Wire.h>
#include <MPU6050.h>
// PID 라이브러리 필요

MPU6050 mpu;
float angle, target = 0.0;
float pid_output;

void setup() {
  Serial.begin(9600);
  Wire.begin();
  mpu.initialize();
  // 모터 핀 초기화 등
}

void loop() {
  // 1. 센서에서 각도 읽기
  angle = getAngleFromMPU6050();

  // 2. PID 제어로 오차 계산
  pid_output = computePID(target, angle);

  // 3. 모터에 명령 전달
  setMotorSpeed(pid_output);

  // 4. 디버그 출력
  Serial.print("Angle: "); Serial.print(angle);
  Serial.print(" PID: "); Serial.println(pid_output);
  delay(10);
}
```

---

## PID 제어란?
- P(Proportional): 오차에 비례해 제어
- I(Integral): 오차의 누적값 보정
- D(Derivative): 오차 변화율 보정
- 튜닝값(Kp, Ki, Kd) 조절로 동작 최적화

---

## 실습 체크리스트
- 센서 각도값이 정상적으로 출력되는지 확인
- PID 제어 결과에 따라 모터가 반응하는지 확인
- 차가 넘어지지 않고 균형을 유지하는지 실험

---

## 문제 해결
- 각도값이 이상하면 센서/라이브러리 확인
- PID 튜닝값이 맞지 않으면 차가 흔들리거나 넘어질 수 있음
- 모터가 너무 약하면 균형 유지 불가

---

## 다음 단계
- 07_pid_tuning: PID 제어 원리 및 튜닝 실습
