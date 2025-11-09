This file has been moved to edu_labs.
# 08. 스마트폰 APP 연동 및 무선 제어

## 목표
- 블루투스 모듈을 이용해 스마트폰 APP으로 자이로카를 무선 제어
- 기본 APP 사용법 및 아두이노 코드 연동 실습

---

## 준비물
- HC-06/HC-05 블루투스 모듈
- 스마트폰(Android/iOS)
- 블루투스 제어용 APP (예: "Bluetooth RC Car", "Arduino Bluetooth Controller")

---

## 회로 연결
- HC-06 VCC → 5V
- HC-06 GND → GND
- HC-06 TX → 아두이노 RX
- HC-06 RX → 아두이노 TX

---

## APP 설치 및 페어링
1. 스마트폰에서 블루투스 APP 설치
2. 블루투스 모듈 전원 연결 후 페어링
   - 기본 비밀번호: 1234 또는 0000

---

## 아두이노 예제 코드 (개념)
```cpp
#include <SoftwareSerial.h>
SoftwareSerial BTSerial(2, 3); // RX, TX

void setup() {
  Serial.begin(9600);
  BTSerial.begin(9600);
}

void loop() {
  if (BTSerial.available()) {
    char cmd = BTSerial.read();
    if (cmd == 'F') forward();
    else if (cmd == 'B') backward();
    else if (cmd == 'L') left();
    else if (cmd == 'R') right();
    else stop();
  }
}
```

---

## 실습 체크리스트
- APP에서 버튼을 누르면 차가 원하는 방향으로 움직이는지 확인
- 페어링/통신 오류 시 모듈/배선/APP 설정 확인

---

## 문제 해결
- 페어링 실패: 비밀번호/APP/모듈 확인
- 명령이 전달되지 않으면 TX/RX 핀 교차 여부 확인
- 통신 속도(baudrate) 일치 확인

---

## 참고 자료
- [Bluetooth RC Car APP](https://play.google.com/store/apps/details?id=braulio.calle.bluetoothRCcontroller)
- [아두이노 블루투스 제어 예제](https://www.instructables.com/Arduino-Bluetooth-Controlled-Car/)

---

## 다음 단계
- 09_troubleshooting: 문제 해결 및 Q&A
