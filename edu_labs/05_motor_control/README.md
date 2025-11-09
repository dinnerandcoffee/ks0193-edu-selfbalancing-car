This file has been moved to edu_labs.
# 05. 모터 드라이버 제어 실습

## 목표
- L298N 모터 드라이버를 통해 DC 모터를 제어
- 아두이노에서 모터 방향/속도 변경 실습

---

## 회로 연결
- IN1, IN2, IN3, IN4: 아두이노 디지털 핀(D4~D7 등)
- ENA, ENB: PWM 핀(D5, D6 등)
- OUT1, OUT2, OUT3, OUT4: DC 모터 2개 연결
- VCC, GND: 배터리 박스 연결

---

## 예제 코드
```cpp
#define IN1 4
#define IN2 5
#define IN3 6
#define IN4 7
#define ENA 9
#define ENB 10

void setup() {
  pinMode(IN1, OUTPUT); pinMode(IN2, OUTPUT);
  pinMode(IN3, OUTPUT); pinMode(IN4, OUTPUT);
  pinMode(ENA, OUTPUT); pinMode(ENB, OUTPUT);
}

void loop() {
  // 전진
  digitalWrite(IN1, HIGH); digitalWrite(IN2, LOW);
  digitalWrite(IN3, HIGH); digitalWrite(IN4, LOW);
  analogWrite(ENA, 200); analogWrite(ENB, 200);
  delay(2000);

  // 후진
  digitalWrite(IN1, LOW); digitalWrite(IN2, HIGH);
  digitalWrite(IN3, LOW); digitalWrite(IN4, HIGH);
  analogWrite(ENA, 200); analogWrite(ENB, 200);
  delay(2000);

  // 정지
  analogWrite(ENA, 0); analogWrite(ENB, 0);
  delay(1000);
}
```

---

## 실습 체크리스트
- 모터가 전진/후진/정지 동작하는지 확인
- 속도(PWM 값) 변경 시 반응 확인

---

## 문제 해결
- 모터가 움직이지 않으면 배선/핀번호/전원 확인
- PWM 값이 너무 낮으면 모터가 안 움직일 수 있음

---

## 다음 단계
- 06_self_balancing: 자이로+모터로 밸런싱 알고리즘 실습
