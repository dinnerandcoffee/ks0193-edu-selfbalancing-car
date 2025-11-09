This file has been moved to edu_labs.
# 07. PID 제어 원리 및 튜닝 실습

## 목표
- PID 제어의 원리 이해
- Kp, Ki, Kd 값 튜닝을 통해 밸런싱 성능 최적화

---

## PID 제어란?
- P(Proportional): 오차에 비례해 제어
- I(Integral): 오차의 누적값 보정
- D(Derivative): 오차 변화율 보정
- PID 공식: `output = Kp*error + Ki*integral + Kd*derivative`

---

## 튜닝 방법
1. **Kp(비례값)만 먼저 조절**
   - 값이 너무 낮으면 반응이 느림
   - 값이 너무 높으면 흔들림/진동 발생
2. **Kd(미분값) 추가**
   - 흔들림/진동을 줄임
3. **Ki(적분값) 추가**
   - 오차가 장기적으로 남을 때 보정

---

## 실습 예제 코드 (개념)
```cpp
float Kp = 20.0, Ki = 0.5, Kd = 1.0;
float error, prev_error, integral, derivative, output;

void loop() {
  error = target - angle;
  integral += error;
  derivative = error - prev_error;
  output = Kp*error + Ki*integral + Kd*derivative;
  setMotorSpeed(output);
  prev_error = error;
}
```

---

## 실습 체크리스트
- Kp, Ki, Kd 값을 변경하며 차의 반응 관찰
- 흔들림/진동/넘어짐 현상에 따라 값 조절
- 최적의 밸런싱 동작 찾기

---

## 문제 해결
- 흔들림 심하면 Kp/Kd 값 조절
- 균형 유지 안되면 Kp 증가, Ki/Kd 조절
- 오차가 누적되면 Ki 값 증가

---

## 참고 자료
- [PID 튜닝 가이드](https://www.arduino.cc/reference/en/libraries/pid_v1/)
- [자이로카 PID 실습 영상](https://www.youtube.com/results?search_query=arduino+self+balancing+car+pid)

---

## 다음 단계
- 08_app_control: 스마트폰 APP 연동 및 무선 제어
