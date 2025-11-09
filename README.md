<a id="top"></a>
# **KS0193 keyestudio Self-balancing Car Kit**

![](media/ed976d4f7f20a281b531b76a84cbf80c.jpeg)

# 목차

- [1. 개요](#overview)
- [2. 작동 원리](#principle)
- [3. 밸런스 카 매개변수](#params)
- [4. 키트 목록](#kit)
- [5. 조립 단계](#assembly)
- [6. 프로젝트 (1–14)](#projects)
  - [프로젝트 1: 아두이노 시작하기](#project-1)
  - [프로젝트 2: 버튼과 버저](#project-2)
  - [프로젝트 3: TB6612 모터 구동](#project-3)
  - [프로젝트 4: 홀 인코더 테스트](#project-4)
  - [프로젝트 5: 내부 타이머 인터럽트](#project-5)
  - [프로젝트 6: 블루투스 테스트](#project-6)
  - [프로젝트 7: MPU6050 테스트](#project-7)
  - [프로젝트 8: 기울기 각도 및 각속도 계산](#project-8)
  - [프로젝트 9: PID 원리](#project-9)
  - [프로젝트 10: 직립 루프 조정](#project-10)
  - [프로젝트 11: 속도 루프 조정](#project-11)
  - [프로젝트 12: 조향 루프 제어](#project-12)
  - [프로젝트 13: 블루투스 제어](#project-13)
  - [프로젝트 14: 균형 각도 조정 및 블루투스 제어](#project-14)
- [7. 모든 리소스 다운로드](#resources)

<a id="readme"></a>
# 먼저 읽어보세요

**링크에서 APP, 코드 및 라이브러리를 다운로드하세요: <https://fs.keyestudio.com/KS0193>**

<a id="overview"></a>
# 1.개요

직접 미니 밸런스 카를 DIY하는 방법은 무엇인가요? 이 밸런스 카 키트는 아두이노 개발 플랫폼을 기반으로 합니다. 우리는 주로 Keyestudio V4.0 (Black) 메인 컨트롤 보드를 코어로 사용하고, 내장된 MPU-6050이 있는 밸런스 실드를 드라이브 보드로 사용하여 카 바디 자세를 테스트합니다.

밸런스 실드는 블루투스 인터페이스가 함께 제공되며, 블루투스 XBee 모듈과 완전히 호환됩니다 (안드로이드 시스템만 호환).

블루투스에 연결하면 블루투스 APP으로 밸런스 카의 이동 방향을 쉽게 제어할 수 있어 다양한 독특한 자세를 만들 수 있습니다.

작동 제어를 용이하게 하기 위해 블루투스 APP에는 키와 중력 제어 모드가 모두 있습니다.

또한, 밸런스 각도와 PID 매개변수를 조정하는 기능을 추가하여 완벽하게 밸런스 카를 조정하고 제어할 수 있습니다.

어떻게 플레이할지 걱정하지 마세요. 우리는 모든 조립 구성품을 제공할 수 있으며, 해당 설치, 디버깅 방법 및 프로그램도 제공합니다.

<a id="principle"></a>
# 2.작동 원리

자체 밸런싱 카는 카 바디의 힘을 사용하여 상대적인 밸런스를 유지하며, 이는 동적 밸런스의 과정입니다.

카의 밸런스를 유지하는 힘은 바퀴의 운동에서 비롯되며, 두 개의 DC 모터에 의해 구동됩니다.

카의 바디 제어는 다음과 같은 세 가지 제어 작업으로 나눌 수 있습니다:

**1. 밸런스 제어:** 카의 바퀴 전진 및 후진 회전을 제어하여 카를 똑바로 유지하고 밸런스를 맞춥니다.

**2. 속도 제어:** 카의 기울기를 제어하여 전후 이동 및 속도 제어를 실현합니다. 실제로 모터 속도를 제어하여 이루어집니다.

**3. 방향 제어:** 카의 두 모터 사이의 회전 속도 차이를 제어하여 방향 전환을 실현합니다.

이렇게 하면 세 가지 제어 작업을 이해하는 것이 상대적으로 간단합니다.

그러나 최종 제어 과정에서는 세 가지 작업이 서로 결합되어 서로 간섭합니다.

핵심은 카의 밸런스를 제어하는 것이며, 속도와 방향 제어는 가능한 한 부드럽게 해야 합니다.

<a id="params"></a>
# 3.밸런스 카 매개변수

**모터 매개변수:**

작동 전압: DC12V

감속비: 1:30

무부하 전류: ≤100mA

무부하 속도: 247rpm

정격 토크: 1.4 Kg.cm

정격 토크: 137.3mN.m

정격 속도: 160rpm

정격 전류: ≤0.45A

정지 토크: 5.5 Kg.cm

정지 전류: 2.4A

감속기 길이: 22mm

작동 전압: DC 9-12V

모터 드라이브 칩: TB6612FNG

바디 자세 감지: MPU-6050

전원 제어 스위치 포함

블루투스 통신 제어를 위한 블루투스 제어 스위치 포함

**특별히 주의하세요:**

밸런스 실드는 블루투스 통신을 제어하는 슬라이드 스위치가 함께 제공됩니다.

소스 코드를 업로드할 때 반드시 슬라이드 스위치를 OFF로 설정하세요; 그렇지 않으면 코드 업로드가 실패합니다.

블루투스 모듈에 연결할 때 슬라이드 스위치를 ON으로 설정해야 합니다.

![](media/ca17b05327464d5ccfe69be52cd49bb6.png)

<a id="kit"></a>
# 4.키트 목록

키트 패키징에는 이 자체 밸런싱 카에 대한 모든 전자 구성품이 포함되어 있습니다. 각 프로젝트를 진행하면서 카를 제어하는 방법을 배우게 됩니다.

| 번호 | 구성품 | 수량 | 사진 |
| ---- | ------------------------------------------------------------ | -------- | :----------------------------------------------------------: |
| 1 | 이중 패스 M3*45MM 육각 구리 기둥 | 4 | ![img](./media/wps1.png) |
| 2 | 이중 패스 M3*10MM 육각 구리 기둥 | 4 | ![img](./media/wps22.png) |
| 3 | 검은색 M4*6 십자 나사 | 2 | ![img](./media/wps333.png) |
| 4 | M3*6MM 둥근 머리 나사 | 6 | ![img](./media/wps4.png) |
| 5 | M3*8MM 둥근 머리 나사 | 10 | ![img](./media/wps5.png) |
| 6 | M3*8MM 평평한 머리 십자 나사 | 4 | ![img](./media/wps6.png) |
| 7 | M3*12MM 평평한 머리 십자 나사 | 2 | ![img](./media/wps7.png) |
| 8 | M3*12MM 둥근 머리 나사 | 10 | ![img](./media/wps8.png) |
| 9 | M3 니켈 도금 너트 | 12 | ![img](./media/wps9.png) |
| 10 | 아크릴 판 팩 2pcs | 1 | ![img](./media/wps21.png) |
| 11 | 검은색+파란색 외경 68mm 두께 26mm 바퀴 | 2 | ![img](./media/wps23.png) |
| 12 | DC 기어 모터 홀 인코더 12V，1：30， | 2 | ![img](./media/wps24.png) |
| 13 | 6MM 구멍*18MM 길이 구리 육각 커플러 | 2 | ![img](./media/wps25.png) |
| 14 | 이중 헤드 6핀 PH2.030CM 커넥터 와이어 | 2 | ![img](./media/wps26.png) |
| 15 | 노란색-검은색 핸들 3*40MM 필립스 드라이버 | 1 | ![img](./media/wps28.png) |
| 16 | 타입 L M2 니켈 도금 내부 육각 렌치 | 1 | ![img](./media/wps29.png) |
| 17 | 18650 3셀 AA 배터리+플러그(18650 배터리 미포함) | 1 | ![img](./media/wps30.png) |
| 18 | Keyestudio 밸런스 실드 V3 (검은색 및 친환경) | 1 | ![img](./media/wps31.png) |
| 19 | Keyestudio v4.0 메인 컨트롤 보드 | 1 | ![img](./media/wps32.jpeg) |
| 20 | AM/BM 투명 파란색 OD:5.0 L=50cm USB 케이블 | 1 | ![img](./media/wps33.png) |
| 21 | Keyestudio 블루투스 XBee HC-06 | 1 | ![img](./media/wps34.png) |
| 22 | 모터 철 홀더 | 1 | ![img](./media/wps35.png) |
| 23 | 검은색 와인딩 튜브 | 1 | ![img](./media/wps36.jpg) |

<a id="assembly"></a>
# 5.조립 단계

**⑴** 아래에 표시된 모든 구성품을 준비하세요.

![](media/b5617b03012f591e915031216dafed40.jpeg)

![](media/93d98b25cca1a4818006f8a69d59e8ab.png)

**⑵** 먼저, 아래 아크릴 판을 설치합니다.

![](media/dec4c84f37e4ab50fecfea53373b6261.jpeg)

다음 부품을 찾아보세요:

- 아래 아크릴 판

- 이중 패스 M3\*10MM 육각 구리 기둥 x 4pcs

- M3\*8MM 나사 x 4pcs

- M3\*12MM 평평한 머리 나사 x 2pcs

- M3 니켈 도금 너트 x 2pcs

- 배터리 케이스

배터리 케이스와 구리 기둥을 아크릴 판에 장착합니다.

4pcs M3\*10MM 구리 기둥을 4pcs M3\*8MM 나사로 아크릴 판에 고정하세요.

![](media/ba542135eb736aa0edd7cab10139b8f1.jpeg)

그 다음, 2pcs M3\*12MM 평평한 머리 나사와 2pcs M3 니켈 도금 너트로 배터리 케이스를 아크릴 판에 장착하세요.

![](media/9d62646249ba348a458b8ba00cd351dd.jpeg)

![](media/dfcb07bace0b5ba332bb9373a59e5142.jpeg)

**⑶** 다음으로, 아래 아크릴 판에 모터와 바퀴를 설치합니다.

다음 부품을 찾아보세요:

- 배터리 케이스가 장착된 아래 아크릴 판
- M3\*12MM 둥근 머리 나사 x 8pcs
- M3 니켈 도금 너트 x 8pcs
- M4\*6MM 검은색 나사 x 2pcs
- 두 개의 바퀴
- 두 개의 검은색 커넥터
- 두 개의 모터
- 두 개의 구리 육각 커플러
- M2 렌치 타입 L

![](media/381d37ae3bab9c04276f426f6a254f33.jpeg)

8pcs M3\*12MM 둥근 머리 나사와 8pcs M3 니켈 도금 너트로 두 개의 검은색 커넥터를 아크릴 판에 장착하세요. 아래에 표시됩니다.

![](media/5d79b03196991a5bb8f702e95b0cb9ad.jpeg)

각 모터에는 가방에 6개의 나사가 있습니다. 나사를 사용하여 두 개의 모터를 검은색 커넥터에 장착하세요.

![](media/fe987b19b5de94b5f264fa6d9a37b410.jpeg)

![](media/870d6c7b8bfa58b251a0c24c1b051e4e.jpeg)

각 구리 육각 커플러를 두 개의 나사로 조이세요. 그런 다음 렌치를 사용하여 두 개의 육각 커플러를 두 개의 모터에 고정하세요.

![](media/028702031b4e21b3871a4e2e4798927b.jpeg)

![](media/d213e3c8379078e2693e879c2793cdf1.jpeg)

마지막으로, 2pcs M4\*6MM 검은색 나사를 사용하여 두 개의 바퀴를 두 개의 구리 육각 커플러에 고정하세요.

![](media/3b6b8a394e30efc92cd1a0a9da7a3169.jpeg)

![](media/173a5e9757a5df4e9f146bf5fa31dbc8.jpeg)

![](media/ed6fbb3987cb766a9ffa0b70293ae7fc.jpeg)

지금까지 아래 모터 바퀴가 잘 설치되었습니다!

**⑷** 마지막 단계는 컨트롤 보드와 위 아크릴 판을 설치하는 것입니다.

![](media/b43ff4417ad0890b1ad8f8f198de7f24.jpeg)

- 위 아크릴 판

- V4.0 컨트롤 보드

- keyestudio 밸런스 실드

- 블루투스 XBee 모듈 HC-06

- M3\*6MM 둥근 머리 나사 x 3pcs

- M3\*45MM 구리 기둥 x 4pcs

- M3\*8MM 둥근 머리 나사 x 8pcs

- 6핀 30CM 커넥터 와이어 x 2pcs

3pcs M3\*6MM 둥근 머리 나사로 V4.0 컨트롤 보드를 아크릴 판에 장착된 4pcs M3\*10MM 구리 기둥에 고정하세요.

![](media/3b2b69724aeaaf40334572d46cb089a3.jpeg)

그 다음, keyestudio 밸런스 실드를 V4.0 컨트롤 보드에 쌓고, 블루투스 XBee 모듈 HC-06을 밸런스 실드에 꽂으세요.

![](media/1aa06f4d7152f9f9bfd865f79b7aad59.jpeg)

6핀 PH2.0 30CM 커넥터 와이어를 사용하여 모터를 밸런스 실드에 연결하세요. 모터를 가장 가까운 모터 커넥터에 연결하세요.

![](media/72513a28bc92107c9bae3e65a29db59b.jpeg)

![](media/b8368175fb4f0abb514ae7b1f5fe1911.jpeg)

그 후, 4pcs M3\*45MM 구리 기둥을 아크릴 판에 4pcs M3\*8MM 둥근 머리 나사로 고정하고, V4.0의 DC 블랙 잭에 배터리 플러그를 잘 연결하세요.

![](media/542910ede8494a06a126a09104425817.jpeg)

뒷면은 아래에 표시됩니다:

![](media/7bbab9da7f512230d481fda44886c5ce.jpeg)

마지막 부분은 4pcs M3\*45MM 구리 기둥에 4pcs M3\*8MM 둥근 머리 나사로 위 아크릴 판을 설치하는 것입니다.

![](media/3465955d0c9cf3934abf5c22f6146ae4.jpeg)

축하합니다! 밸런스 카가 잘 설치되었습니다.

![](media/ed976d4f7f20a281b531b76a84cbf80A.jpg)

<a id="projects"></a>
# 6.프로젝트

<a id="project-1"></a>
## 프로젝트 1: 아두이노 시작하기
[맨 위로](#top)

**V4.0 컨트롤 보드**

플랫폼으로 시작할 때 V4.0은 전자 및 코딩을 시작하는 데 가장 좋은 보드입니다. 이 플랫폼을 처음 접하는 경우 V4.0은 가지고 놀 수 있는 가장 견고한 보드입니다.

![](media/88e350302076928641bee474abbfd7f3.jpeg)

V4.0 보드를 살펴보겠습니다.

![](media/709d9ef695f98e63ee0501030b455a69.jpeg)

**밸런스 카 실드**

밸런스 실드는 이 밸런스 카의 중요한 부분입니다. 이를 통해 밸런스 카를 더 간단하게 DIY할 수 있습니다.

V4.0 보드와 완전히 호환됩니다; 컨트롤 보드에 쌓기만 하면 됩니다.

밸런스 실드는 6612FNG 칩으로 두 개의 DC 모터를 구동하고, 두 개의 흰색 커넥터로 DC 모터를 연결하며, 밸런스 실드와 V4.0에 전원을 공급하는 DC 전원 잭을 포함합니다;

또한 큰 슬라이드 스위치로 전원 스위치를 제어하고, MPU-6050로 자세를 테스트하며, XBEE 블루투스 인터페이스로 블루투스 모듈과 통신하며, 블루투스 모듈의 통신을 제어하는 작은 슬라이드 스위치를 포함합니다.

또한 버튼과 액티브 버저가 있습니다.

실드의 컨트롤 핀은 모두 여성 헤더로 실드에 가져오고, 시리얼 포트와 I2C 통신 핀은 핀 헤더로 가져옵니다.

**참고:** 모터를 실드의 모터 커넥터에 연결하세요.

![image-20230510085238394](media/image-20230510085238394.png)

**핀아웃:**

![](media/e9497ec95579d3b4a2e863fc8ac7a24f.jpeg)

**아두이노 IDE 설치**

![](/media/ide.png)

**소프트웨어를 다운로드하고, 드라이버를 설치하고, 코드를 업로드하고, 라이브러리 파일을 설치하는 방법을 배우기 위해 링크를 클릭하세요.**

**[https://getting-started-with-arduino.readthedocs.io](https://getting-started-with-arduino.readthedocs.io/en/latest/Arduino%20IDE%20Tutorial.html)**

<a id="project-2"></a>
## 프로젝트 2: 버튼과 버저
[맨 위로](#top)

**설명:**

이전 프로젝트에서 아두이노 소프트웨어 환경을 사용하는 방법을 배웠습니다.

시도해 보겠습니까? 좋습니다. 이 프로젝트는 아두이노 프로그래밍 세계에 들어가는 기본 프로그램을 제공합니다.

![](media/4503905b43c71037a46a28ccd8efe8ee.jpeg)

keyestudio 밸런스 카 실드에는 KEY_13 버튼과 액티브 버저가 있습니다. 구체적으로 버튼은 V4.0의 핀 D13으로 제어되고, 액티브 버저는 V4.0의 핀 D11으로 제어됩니다.

![](media/ca17b05327464d5ccfe69be52cd49bb6.png)

실험에서 버튼으로 버저를 제어합니다. 버튼을 누르면 버저가 울립니다.

![](media/f680ff553db7faf1f0b681fb2c8f6996.png)

액티브 버저에는 진동 회로가 있습니다. 사실, 핀 D11을 HIGH로 설정하면 버저가 울립니다. 우리는 패시브 버저의 설정 방법을 시뮬레이션합니다. 액티브 버저가 다른 소리를 출력하도록 다른 스퀘어 웨이브를 설정합니다.

**소스 코드:**

```c
const int buz = 11;    // 버저 핀 설정
const int btn = 13;    // 버튼 핀 설정
int button;    // 버튼 변수

void setup() 
{
  pinMode(btn,INPUT);       // INPUT 상태로 설정
  pinMode(buz,OUTPUT);       // OUTPUT 상태로 설정
}

void loop() 
{
  button = digitalRead(btn);       // 버튼 값을 변수 button에 할당
  if(button == 0)    // 버튼을 누르면
  {
    delay(10);    // 지연 시간
    if(button == 0)     // 다시 판단, 버튼이 눌렸으면
    {
      buzzer();  // 버저 서브함수 실행
    }
  }
  else        // 버튼이 눌리지 않음
  {
    digitalWrite(buz,LOW);    // 버저가 울리지 않음
  }
}

//버저가 틱 소리를 냄
void buzzer()      
{
    for(int i=0;i<50;i++)
    {
    digitalWrite(buz,HIGH);
    delay(1);
    digitalWrite(buz,LOW);
    delay(1);
    }
    delay(50);
    for(int i=0;i<50;i++)
    {
    digitalWrite(buz,HIGH);
    delay(1);
    digitalWrite(buz,LOW);
    delay(1);
    }
}
```

**테스트 결과**

밸런스 카를 잘 설치하고, 소스 코드를 업로드하고 전원을 켜세요; 슬라이드 스위치를 ON으로 설정하고 실드의 KEY_13 버튼을 누르세요.

밸런스 실드의 액티브 버저가 울립니다; 그렇지 않으면 울리지 않습니다.

<a id="project-3"></a>
## 프로젝트 3: TB6612 모터 구동
[맨 위로](#top)

**설명:**

프로젝트에서 우리는 오른쪽 모터의 방향을 V4.0의 핀 D8 D12로 제어하고, 속도는 핀 D10으로 제어합니다. 왼쪽 모터의 방향은 V4.0의 핀 D7 D6으로 제어하고, 속도는 핀 D9로 제어합니다.

![](media/a6ae40878065311168a15a0ed46c607e.jpeg)

**지정된 제어 방법은 아래 표를 참조하세요:**

| D8   | D12  | D10/PWM | 오른쪽 모터 | D7   | D6   | D9/PWM | 왼쪽 모터 |
|------|------|---------|-------------|------|------|--------|------------|
| HIGH | LOW  | 0-255   | 전진        | HIGH | LOW  | 0-255  | 전진       |
| LOW  | HIGH | 0-255   | 후진        | LOW  | HIGH | 0-255  | 후진       |
| HIGH | HIGH | /       | 정지        | HIGH | HIGH | /      | 정지       |
| LOW  | LOW  | /       | 정지        | LOW  | LOW  | /      | 정지       |

D9 D10은 PWM 핀으로, 디지털 출력 또는 아날로그 출력으로 사용할 수 있습니다.

아날로그 출력으로 사용할 때 ARDUINO의 analogWrite() 함수를 호출해야 하며, 이 analogWrite() 함수는 0-255 범위로 제어됩니다.

analogWrite(255)를 호출하면 100% 듀티 사이클(항상 켜짐)을 요청하고, analogWrite(127)는 50% 듀티 사이클(반 시간 켜짐)입니다.

코드에서 D9와 D10에 설정된 PWM 값이 클수록 두 모터의 속도가 빨라집니다.

아래에서 우리는 두 모터를 전진과 후진으로만 간단히 설정합니다.

**소스 코드:**

```c
//TB6612 핀
const int right_R1=8;    
const int right_R2=12;
const int PWM_R=10;
const int left_L1=7;
const int left_L2=6;
const int PWM_L=9;

void setup() 
{
  Serial.begin(9600);          // 보드레이트를 9600으로 설정
  
  pinMode(right_R1,OUTPUT);     // 모든 TB6612핀을 OUTPUT으로 설정
  pinMode(right_R2,OUTPUT);
  pinMode(PWM_R,OUTPUT);
  pinMode(left_L1,OUTPUT);
  pinMode(left_L2,OUTPUT);
  pinMode(PWM_L,OUTPUT);
}

void loop() 
{
  // 두 모터 전진
  digitalWrite(right_R1,HIGH);
  digitalWrite(right_R2,LOW);
  digitalWrite(left_L1,HIGH);
  digitalWrite(left_L2,LOW);
  analogWrite(PWM_R,100);   // PWM 값 0~255 쓰기（속도）
  analogWrite(PWM_L,100);
}
```

**테스트 결과**

밸런스 카를 잘 설치하고, 소스 코드를 업로드하고 전원을 켜세요; 슬라이드 스위치를 ON으로 설정하세요.

두 왼쪽과 오른쪽 모터가 전진합니다.

![](media/a6ae40878065311168a15a0ed46c607e.jpeg)

<a id="project-4"></a>
## 프로젝트 4: 홀 인코더 테스트
[맨 위로](#top)

**설명:**

이전에서 D9 D10의 PWM 값으로 모터 속도를 설정하는 방법을 소개했습니다.

그러나 지정된 속도를 얻는 방법은 무엇인가요? 홀 인코더를 사용하여 테스트할 수 있습니다.

![](media/2c63ece82b926aa57e36a5d4f8a5b5e5.png)

![image-20230510090657965](media/image-20230510090657965.png)

이 프로젝트에서 100ms 내에 홀 인코더에서 얻은 펄스 수로 지정된 속도를 계산하는 방법을 배웁니다.

**소스 코드:**

```c
//TB6612 핀
const int right_R1=8;    
const int right_R2=12;
const int PWM_R=10;
const int left_L1=7;
const int left_L2=6;
const int PWM_L=9;

const int PinA_left = 5;    // 왼쪽 모터의 펄스 핀을 D5로 설정
const int PinA_right = 4;    // 오른쪽 모터의 펄스 핀을 D4로 설정

int times=0,newtime=0,d_time=100;   // 시간, 새 시간, 시간 간격
int valA=0,valB=0,flagA=0,flagB=0;    // 펄스 수를 계산하는 변수 valA와 valB

void setup() 
{
  Serial.begin(9600);
  
  pinMode(right_R1,OUTPUT);    // TB6612 핀을 OUTPUT으로 설정
  pinMode(right_R2,OUTPUT);
  pinMode(PWM_R,OUTPUT);
  pinMode(left_L1,OUTPUT);
  pinMode(left_L2,OUTPUT);
  pinMode(PWM_L,OUTPUT);

  pinMode(PinA_left,INPUT);    // 펄스 핀을 INPUT으로 설정
  pinMode(PinA_right,INPUT);

}

void loop() 
{
  //두 모터 전진
  digitalWrite(right_R1,HIGH);
  digitalWrite(right_R2,LOW);
  digitalWrite(left_L1,HIGH);
  digitalWrite(left_L2,LOW);
  analogWrite(PWM_R,100);   // PWM 값 0~255 쓰기（속도）
  analogWrite(PWM_L,200);

  newtime=times=millis();     // newtime과 times를 프로그램이 여기까지 실행한 시간으로 같게 만듦
  while((newtime-times)<d_time)    // 설정 d_time보다 작으면 항상 루프
  {
    if(digitalRead(PinA_left)==HIGH&&flagA==0)   // HIGH 감지 시
    {
      valA++;      // valA 1 증가
      flagA=1;
    }
    if(digitalRead(PinA_left)==LOW&&flagA==1)    // LOW 시
    {
      valA++;     // valA 1 증가
      flagA=0;
    }
    
    if(digitalRead(PinA_right)==HIGH&&flagB==0)
    {
      valB++;
      flagB=1;
    }
    if(digitalRead(PinA_right)==LOW&&flagB==1)
    {
      valB++;
      flagB=0;
    }
    newtime=millis();        // newtime은 프로그램이 여기까지 실행한 시간
  }
  Serial.println(valA);      // 시리얼 모니터에 valA와 B 값 출력
  Serial.println(valB);
  valA=valB=0;             // 0으로 설정
}
```

**테스트 결과**

밸런스 카를 잘 설치하고, 소스 코드를 업로드하고 전원을 켜세요; 슬라이드 스위치를 ON으로 설정하세요.

아두이노 IDE를 열고 보드레이트를 9600으로 설정하세요. 시리얼 모니터가 100ms 내에 홀 인코더에서 얻은 펄스 수를 팝업합니다 (왼쪽과 오른쪽 모터에 해당).

아래 그림을 참조하세요.

![](media/d41314adde529353adc5efe78c535192.png)

<a id="project-5"></a>
## 프로젝트 5: 내부 타이머 인터럽트
[맨 위로](#top)

**설명:**

이전에서 홀 인코더의 펄스 수를 100ms 내에 얻는 방법을 배웠습니다.

이제 V4.0 보드의 내장 내부 타이머(timer2)를 사용합니다. 홀 인코더에서 얻은 펄스 수로 100ms 내에 지정된 속도를 계산합니다.

**소스 코드:**

테스트하기 전에 해당 라이브러리를 추가하세요.

아래 링크의 방법을 참조하세요:

<https://wiki.keyestudio.com/How_to_Install_Arduino_Library>

```c
#include <MsTimer2.h>

//TB6612 핀
const int right_R1=8;    
const int right_R2=12;
const int PWM_R=10;
const int left_L1=7;
const int left_L2=6;
const int PWM_L=9;

const int PinA_left = 5;        // 왼쪽 모터의 펄스 핀을 D5로 설정
const int PinA_right = 4;       // 오른쪽 모터의 펄스 핀을 D4로 설정

int times=0,newtime=0,d_time=100;   // 시간, 새 시간, 시간 간격
int valA=0,valB=0,flagA=0,flagB=0;   // 펄스 수를 계산하는 변수 valA와 valB

void setup() 
{
  Serial.begin(9600);
  
  pinMode(right_R1,OUTPUT);     // TB6612 핀을 OUTPUT으로 설정
  pinMode(right_R2,OUTPUT);
  pinMode(PWM_R,OUTPUT);
  pinMode(left_L1,OUTPUT);
  pinMode(left_L2,OUTPUT);
  pinMode(PWM_L,OUTPUT);

  pinMode(PinA_left,INPUT);      // 펄스 핀을 INPUT으로 설정
  pinMode(PinA_right,INPUT);
  
  MsTimer2::set(100, inter); // 100ms마다 인터럽트 트리거
  MsTimer2::start();    // 인터럽트 시작
}

void loop() 
{
  //두 모터 전진
  digitalWrite(right_R1,HIGH);
  digitalWrite(right_R2,LOW);
  digitalWrite(left_L1,HIGH);
  digitalWrite(left_L2,LOW);
  analogWrite(PWM_R,100);    // PWM 값 0~255 쓰기（속도）
  analogWrite(PWM_L,200);

  if(digitalRead(PinA_left)==HIGH&&flagA==0)     // 펄스 값 계산
    {
      valA++;
      flagA=1;
    }
    if(digitalRead(PinA_left)==LOW&&flagA==1)
    {
      valA++;
      flagA=0;
    }
    
    if(digitalRead(PinA_right)==HIGH&&flagB==0)
    {
      valB++;
      flagB=1;
    }
    if(digitalRead(PinA_right)==LOW&&flagB==1)
    {
      valB++;
      flagB=0;
    }
    
}

//인터럽트 함수
void inter()    
{
    sei();    // 전체 인터럽트 허용
    Serial.print("valA = ");     // 시리얼 모니터에 펄스 값 출력
    Serial.println(valA);
    Serial.print("valB = ");
    Serial.println(valB);
    valA = valB = 0;
}
```

**테스트 결과**

밸런스 카를 설치하고 전원을 켜고 소스 코드를 업로드하세요;

슬라이드 스위치를 ON으로 설정하세요.

아두이노 IDE의 모니터를 열고 보드레이트를 9600으로 설정하세요.

시리얼 모니터가 100ms 내에 홀 인코더에서 얻은 펄스 수를 팝업합니다 (왼쪽과 오른쪽 모터에 해당).

아래 그림을 참조하세요.

![](media/41e4099873055457571d638252b9c665.png)

<a id="project-6"></a>
## 프로젝트 6: 블루투스 테스트
[맨 위로](#top)

**설명:**

![](media/949c3308572221676761f2f9afe9bf68.png)

키트에는 블루투스 XBee 모듈이 포함되어 있으며, 안드로이드 시스템과 호환됩니다.

Keyestudio Bluetooth XBee 무선 모듈 HC-06에는 컴팩트한 크기, XBEE 실드와 호환, 다양한 3.3V MCU 시스템에 적합한 기능이 있습니다. 또한 효율적인 온보드 안테나가 있습니다.

더 많은 내용은 여기 링크를 확인하세요.

<https://wiki.keyestudio.com/Ks0144_keyestudio_XBee_Bluetooth_Wireless_Module_HC-06>

이 프로젝트에서 안드로이드 블루투스와 밸런스 카가 통신하도록 블루투스 APP를 사용하는 방법을 배웁니다. 블루투스 APP를 사용하여 밸런스 카 이동을 무작위로 제어할 수 있습니다.

![](media/e43a43d30d7fa6c0b880a55872573b4b.jpeg)

**참고:**

keyestudio 밸런스 실드에는 블루투스 통신을 제어하는 슬라이드 스위치가 있습니다.

소스 코드를 업로드할 때 반드시 스위치를 OFF로 설정하세요; 그렇지 않으면 코드 업로드가 실패합니다.

블루투스 모듈에 연결할 때 스위치를 ON으로 설정해야 합니다.

**블루투스 APP를 사용하는 방법?**

- 밸런스 카를 설치하고, 소스 코드를 업로드하고 전원을 켜세요; 전원 스위치를 ON으로 설정하세요; 블루투스 스위치를 ON으로 설정하세요.
    
- 블루투스 APP를 설치하세요. 그러면 휴대폰에 아래 아이콘이 표시됩니다.

![image-20230510091355397](media/image-20230510091355397.png)

APP를 다운로드하려면 아래 링크를 클릭하세요:

<https://drive.google.com/open?id=1L69xdfmOvfhg0Wjh_p2FrtRkhs1h0fEu>

- APP를 열어 아래 인터페이스를 보세요.

![](media/c9025f5cc50b1c07224b747d3b8a75c8.png)

![](media/1f4c2a18315a5113785e94e790e7c6e8.png)

- 블루투스 아이콘을 탭하세요![image-20230426163821621](media/image-20230426163821621.png); 블루투스 검색 및 페어링 인터페이스로 들어가세요.

![image-20230510091436455](media/image-20230510091436455.png)

- HC-06을 탭하세요 (처음 검색 시 주소이므로 주소를 탭하세요); PIN은 1234입니다.

![image-20230510091459462](media/image-20230510091459462.png)

- 마지막으로 페어된 장치를 보게 됩니다.

![image-20230510091516036](media/image-20230510091516036.png)

- 휴대폰에서 HC-06에 연결하세요; 이제 APP의 블루투스 연결 아이콘을 탭하세요 ![image-20230426163848425](media/image-20230426163848425.png).

![](media/b3fdf12f728b45fd74de8911e22a0a36.png)

- 그런 다음 APP에 표시된 ![image-20230426163912972](media/image-20230426163912972.png)를 탭하세요. 이제 블루투스가 성공적으로 연결되었습니다.
- 블루투스가 연결되면 APP의 키 ![image-20230426163936649](media/image-20230426163936649.png)를 탭하세요. 두 모터가 전진합니다;
- 키 ![image-20230426163944987](media/image-20230426163944987.png)를 탭하세요. 두 모터가 정지합니다;
- 키 ![image-20230426163957010](media/image-20230426163957010.png)를 탭하세요. 두 모터가 후진합니다.

**소스 코드:**

```c
//TB6612 핀
const int right_R1=8;    
const int right_R2=12;
const int PWM_R=10;
const int left_L1=7;
const int left_L2=6;
const int PWM_L=9;
char val;   // 블루투스 변수

void setup() 
{
  Serial.begin(9600);
  
  pinMode(right_R1,OUTPUT);   // TB6612 핀을 OUTPUT으로 설정
  pinMode(right_R2,OUTPUT);
  pinMode(PWM_R,OUTPUT);
  pinMode(left_L1,OUTPUT);
  pinMode(left_L2,OUTPUT);
  pinMode(PWM_L,OUTPUT);
}

void loop() 
{
  if(Serial.available())    // 시리얼 버퍼 값이 사용 가능하면
  {
    val = Serial.read();      // 시리얼 포트에서 읽은 값을 val에 할당
    Serial.println(val);
    switch(val)             // 스위치 문
    {
      case 'F': front(); break;     // 모터 전진
      case 'B': back(); break;       // 후진
      case 'S': Stop();break;    // 정지
    }
  }
}

//전진
void front()
{
  digitalWrite(right_R1,HIGH);
  digitalWrite(right_R2,LOW);
  digitalWrite(left_L1,HIGH);
  digitalWrite(left_L2,LOW);
  analogWrite(PWM_R,100);
  analogWrite(PWM_L,100);
}
//후진
void back()
{
  digitalWrite(right_R1,LOW);
  digitalWrite(right_R2,HIGH);
  digitalWrite(left_L1,LOW);
  digitalWrite(left_L2,HIGH);
  analogWrite(PWM_R,100);
  analogWrite(PWM_L,100);
}
//정지
void Stop()
{
  digitalWrite(right_R1,LOW);
  digitalWrite(right_R2,HIGH);
  digitalWrite(left_L1,LOW);
  digitalWrite(left_L2,HIGH);
  analogWrite(PWM_R,0);
  analogWrite(PWM_L,0);
}
```

<a id="project-7"></a>
## 프로젝트 7: MPU6050 테스트
[맨 위로](#top)

**설명:**

밸런스 카를 DIY할 때 먼저 자세를 얻어야 합니다. 가장 많이 사용되는 것은 가속도계와 자이로스코프를 통해입니다.

이론적으로 두 축 가속도계만 필요합니다 (직선 방향의 Z축과 카 이동 방향의 Y축). 그리고 카 바퀴의 X축 방향 각속도를 계산하는 단일 축 자이로스코프.

![image-20230510091703291](media/image-20230510091703291.png)

이 프로젝트에서 keyestudio 밸런스 실드의 내장 MPU-6050 칩을 사용하여 3축 가속도계와 3축 자이로스코프의 데이터를 테스트하고, 시리얼 모니터에 인쇄합니다.

가속도 범위는 +-2g; 자이로스코프 범위는 +-250°/S입니다.

**소스 코드:**

```c
#include <Wire.h>
 
long accelX, accelY, accelZ;      // 전체 변수로 설정; 함수 내부에서 직접 사용할 수 있음.
float gForceX, gForceY, gForceZ;
 
long gyroX, gyroY, gyroZ;
float rotX, rotY, rotZ;
 
void setup() {
  Serial.begin(9600);
  Wire.begin();
  setupMPU();
}
 
void loop() {
  recordAccelRegisters();
  recordGyroRegisters();
  printData();
  delay(100);
}
 
void setupMPU(){
  // REGISTER 0x6B/REGISTER 107:Power Management 1
  Wire.beginTransmission(0b1101000); //This is the I2C address of the MPU (b1101000/b1101001 for AC0 low/high datasheet Sec. 9.2)
  Wire.write(0x6B); //Accessing the register 6B/107 - Power Management (Sec. 4.30) 
  Wire.write(0b00000000); //Setting SLEEP register to 0, using the internal 8 Mhz oscillator
  Wire.endTransmission();
 
  // REGISTER 0x1b/REGISTER 27:Gyroscope Configuration
  Wire.beginTransmission(0b1101000); //I2C address of the MPU
  Wire.write(0x1B); //Accessing the register 1B - Gyroscope Configuration (Sec. 4.4) 
  Wire.write(0x00000000); //Setting the gyro to full scale +/- 250deg./s (转化为rpm:250/360 * 60 = 41.67rpm) ;The highest can be converted to 2000deg./s 
  Wire.endTransmission();
  
  // REGISTER 0x1C/REGISTER 28:ACCELEROMETER CONFIGURATION
  Wire.beginTransmission(0b1101000); //I2C address of the MPU
  Wire.write(0x1C); //Accessing the register 1C - Acccelerometer Configuration (Sec. 4.5) 
  Wire.write(0b00000000); //Setting the accel to +/- 2g（if choose +/- 16g，the value would be 0b00011000）
  Wire.endTransmission(); 
}
 
void recordAccelRegisters() {
  // REGISTER 0x3B~0x40/REGISTER 59~64
  Wire.beginTransmission(0b1101000); //I2C address of the MPU
  Wire.write(0x3B); //Starting register for Accel Readings
  Wire.endTransmission();
  Wire.requestFrom(0b1101000,6); //Request Accel Registers (3B - 40)
 
  // 왼쪽 시프트 <<와 비트 연산 | 사용  Wire.read() 한 번 읽기 1바이트，다음 호출 시 다음 주소의 데이터를 자동으로 읽음.
  while(Wire.available() < 6);  // 슬레이브 머신에서 6바이트 데이터가 모두 전송될 때까지 기다림（읽기 전에 버퍼에 모든 데이터가 저장되었는지 확인해야 함）
  accelX = Wire.read()<<8|Wire.read(); //첫 두 바이트를 accelX에 저장（정의된 긴 값으로 자동 저장）
  accelY = Wire.read()<<8|Wire.read(); //중간 두 바이트를 accelY에 저장
  accelZ = Wire.read()<<8|Wire.read(); //마지막 두 바이트를 accelZ에 저장
  processAccelData();
}
 
void processAccelData(){
  gForceX = accelX / 16384.0;     //float = long / float
  gForceY = accelY / 16384.0; 
  gForceZ = accelZ / 16384.0;
}
 
void recordGyroRegisters() 
{
  // REGISTER 0x43~0x48/REGISTER 67~72
  Wire.beginTransmission(0b1101000); //I2C address of the MPU
  Wire.write(0x43); //Starting register for Gyro Readings
  Wire.endTransmission();
  Wire.requestFrom(0b1101000,6); //Request Gyro Registers (43 ~ 48)
  while(Wire.available() < 6);
  gyroX = Wire.read()<<8|Wire.read(); //첫 두 바이트를 accelX에 저장
  gyroY = Wire.read()<<8|Wire.read(); //중간 두 바이트를 accelY에 저장
  gyroZ = Wire.read()<<8|Wire.read(); //마지막 두 바이트를 accelZ에 저장
  processGyroData();
}
 
void processGyroData() {
  rotX = gyroX / 131.0;
  rotY = gyroY / 131.0; 
  rotZ = gyroZ / 131.0;
}
 
void printData() {
  Serial.print("Gyro (deg)");
  Serial.print(" X=");
  Serial.print(rotX);
  Serial.print(" Y=");
  Serial.print(rotY);
  Serial.print(" Z=");
  Serial.print(rotZ);
  Serial.print(" Accel (g)");
  Serial.print(" X=");
  Serial.print(gForceX);
  Serial.print(" Y=");
  Serial.print(gForceY);
  Serial.print(" Z=");
  Serial.println(gForceZ);
}
```

**테스트 결과**

밸런스 카를 잘 설치하고, 소스 코드를 업로드하고 전원을 켜세요; 슬라이드 스위치를 ON으로 설정하세요.

아두이노 IDE를 열고 보드레이트를 9600으로 설정하세요. 시리얼 모니터가 값을 팝업합니다.

![](media/d868cb52acefe42eec83c99967b0f7f3.png)

<a id="project-8"></a>
## 프로젝트 8: 기울기 각도 및 각속도 값 계산
[맨 위로](#top)

**설명:**

이전 프로젝트에서 MPU-6050 칩으로 카의 자세를 얻는 방법을 배웠습니다.

이 레슨에서 MPU-6050 칩으로 측정된 데이터를 사용하여 밸런스 카의 자세를 직접 얻습니다.

밸런스 카에 의해 감지된 기울기 각도와 각속도 값을 계산하는 방법을 배우고, 시리얼 모니터에 테스트 결과를 표시합니다.

**소스 코드:**

**참고:**

테스트하기 전에 해당 라이브러리를 추가하세요.

아래 링크의 방법을 참조하세요:

<https://wiki.keyestudio.com/How_to_Install_Arduino_Library>

```c
#include <MPU6050.h>      //MPU6050 라이브러리
#include <Wire.h>        //IIC 통신 라이브러리

MPU6050 mpu6050;     //MPU6050 객체 인스턴스화; 이름 mpu6050
int16_t ax, ay, az, gx, gy, gz;     //3축 가속도, 3축 자이로스코프 변수 정의

float Angle;   //각도 변수
int16_t Gyro_x;   //각속도 변수

void setup() 
{
  // I2C 버스 가입
  Wire.begin();                            //I2C 버스 시퀀스 가입
  Serial.begin(9600);                       //시리얼 모니터 열기, 보드레이트 9600 설정
  delay(1500);
  mpu6050.initialize();                       //MPU6050 초기화
  delay(2);
}

void loop() 
{
  mpu6050.getMotion6(&ax, &ay, &az, &gx, &gy, &gz);     //IIC로 MPU6050 6축 데이터 ax ay az gx gy gz 얻기
  Angle = -atan2(ay , az) * (180/ PI);           //방사형 회전 각도 계산 공식; 음수 부호는 방향 처리
  Gyro_x = -gx / 131;              //자이로스코프로 계산된 X축 각속도; 음수 부호는 방향 처리
  Serial.print("Angle = ");
  Serial.print(Angle);
  Serial.print("   Gyro_x = ");
  Serial.println(Gyro_x);
}
```

**테스트 결과**

밸런스 카를 잘 설치하고, 소스 코드를 업로드하고 전원을 켜세요; 슬라이드 스위치를 ON으로 설정하세요.

아두이노 IDE를 열고 보드레이트를 9600으로 설정하세요. 시리얼 모니터가 값을 팝업합니다.

![](media/6c828cc1a4d67fcc4ab5d7ea62c76cf3.png)

**칼만 필터를 사용하여 각도를 계산하는 방법?**

**칼만 필터란 무엇인가?**

칼만 필터링은 입력과 출력의 선형 시스템 상태 방정식을 사용하여 시스템의 상태를 추정하는 알고리즘입니다.

관측 데이터에는 시스템의 노이즈와 간섭 효과가 포함되므로 최적 추정도 필터링 과정으로 볼 수 있습니다.

![](media/0bb60c33d5b04090245004b5623b884e.jpeg)

가속도계 데이터가 항상 100% 신뢰할 수 없는 이유?

가속도계는 중력력에 의해 발생하는 관성력을 측정합니다 (이상적으로 중력만). 그러나 장치의 가속 (운동)에 의해서도 발생할 수 있습니다.

따라서 가속도계가 상대적으로 안정된 상태라도 진동과 기계적 노이즈에 매우 민감합니다.

즉, 3축 가속도 값만 사용하여 얻은 개별 기울기 각도는 오류가 있으며, 오류가 큽니다. 칼만 필터링을 사용하여 가속도로 계산된 기울기 각도와 자이로스코프의 측정 각속도 값을 필터링해야 합니다.

**하지만 어떻게 이 작업을 수행할 수 있나요? 자이로스코프에 노이즈가 없나요?**

자이로스코프는 회전을 측정하므로 가속도계가 겪는 선형 기계적 운동 (노이즈 유형)에 덜 민감합니다.

그러나 자이로스코프에는 다른 유형의 문제, 예를 들어 회전이 중지될 때 제로 속도 값으로 돌아가지 않는 드리프트가 있습니다.

그럼에도 불구하고 가속도계와 자이로스코프의 데이터를 평균화하여 가속도계 데이터만 사용하여 현재 장치의 기울기 각도를 얻는 것보다 더 나은 추정을 얻을 수 있습니다.

따라서 가속도로 계산된 기울기 각도와 자이로스코프의 측정 각속도 값에 칼만 필터링을 수행하여 더 작고 안정적인 각도를 얻어야 합니다.

이 프로젝트에서 칼만 필터를 사용하여 밸런스 카의 밸런스 각도와 각속도를 계산하고, 시리얼 모니터에 테스트 데이터를 표시합니다.

**소스 코드:**

**참고:**

테스트하기 전에 해당 라이브러리를 추가하세요.

아래 링크의 방법을 참조하세요:

<https://wiki.keyestudio.com/How_to_Install_Arduino_Library>

```c
#include <MPU6050.h>      //MPU6050 라이브러리
#include <Wire.h>        //IIC 통신 라이브러리

MPU6050 mpu6050;     //MPU6050 객체 인스턴스화; 이름 mpu60500
int16_t ax, ay, az, gx, gy, gz;     //3축 가속도, 3축 자이로스코프 변수 정의
float Angle;
float Gyro_x,Gyro_y,Gyro_z;  //자이로스코프로 각 축의 각속도 계산

///////////////////////Kalman_Filter////////////////////////////
float Q_angle = 0.001;  //자이로스코프 노이즈 공분산
float Q_gyro = 0.003;    //자이로스코프 드리프트 노이즈 공분산
float R_angle = 0.5;    //가속도계 공분산
char C_0 = 1;
float dt = 0.005; //dt 값은 필터 샘플링 시간입니다.
float K1 = 0.05; //최적 추정의 편차를 계산하는 칼만 게인을 포함하는 함수입니다.
float K_0,K_1,t_0,t_1;
float angle_err;
float q_bias;    //자이로스코프 드리프트

float accelz = 0;
float angle;
float angleY_one;
float angle_speed;

float Pdot[4] = { 0, 0, 0, 0};
float P[2][2] = {{ 1, 0 }, { 0, 1 }};
float  PCt_0, PCt_1, E;

//////////////////////Kalman_Filter/////////////////////////
void setup() 
{
  // I2C 버스 가입
  Wire.begin();                            //I2C 버스 시퀀스 가입
  Serial.begin(9600);                       //시리얼 모니터 열기, 보드레이트 9600 설정
  delay(1500);
  mpu6050.initialize();                       //MPU6050 초기화
  delay(2);
}

void loop() 
{
  Serial.print("Angle = ");
  Serial.print(Angle);
  Serial.print("  K_angle = ");
  Serial.println(angle);
  Serial.print("Gyro_x = ");
  Serial.print(Gyro_x);
  Serial.print("  K_Gyro_x = ");
  Serial.println(angle_speed);

  mpu6050.getMotion6(&ax, &ay, &az, &gx, &gy, &gz);     //IIC로 MPU6050 6축 ax ay az gx gy gz 얻기
  angle_calculate(ax, ay, az, gx, gy, gz, dt, Q_angle, Q_gyro, R_angle, C_0, K1);      //각도와 칼만 필터 얻기
}

/////////////////////////////angle calculate///////////////////////
void angle_calculate(int16_t ax,int16_t ay,int16_t az,int16_t gx,int16_t gy,int16_t gz,float dt,float Q_angle,float Q_gyro,float R_angle,float C_0,float K1)
{
  Angle = -atan2(ay , az) * (180/ PI);           //방사형 회전 각도 계산 공식; 음수 부호는 방향 처리
  Gyro_x = -gx / 131;              //자이로스코프로 계산된 X축 각속도; 음수 부호는 방향 처리
  Kalman_Filter(Angle, Gyro_x);            //칼만 필터
}

///////////////////////////////KalmanFilter/////////////////////
void Kalman_Filter(double angle_m, double gyro_m)
{
  angle += (gyro_m - q_bias) * dt;          //사전 추정
  angle_err = angle_m - angle;
  
  Pdot[0] = Q_angle - P[0][1] - P[1][0];    //방위각 오차 공분산 미분
  Pdot[1] = - P[1][1];
  Pdot[2] = - P[1][1];
  Pdot[3] = Q_gyro;
  
  P[0][0] += Pdot[0] * dt;    //사전 추정 오차 공분산 미분 적분
  P[0][1] += Pdot[1] * dt;
  P[1][0] += Pdot[2] * dt;
  P[1][1] += Pdot[3] * dt;
  
  //행렬 곱셈의 중간 변수
  PCt_0 = C_0 * P[0][0];
  PCt_1 = C_0 * P[1][0];
  //분모
  E = R_angle + C_0 * PCt_0;
  //게인 값
  K_0 = PCt_0 / E;
  K_1 = PCt_1 / E;
  
  t_0 = PCt_0;  //행렬 곱셈의 중간 변수
  t_1 = C_0 * P[0][1];
  
  P[0][0] -= K_0 * t_0;    //사후 추정 오차 공분산
  P[0][1] -= K_0 * t_1;
  P[1][0] -= K_1 * t_0;
  P[1][1] -= K_1 * t_1;
  
  q_bias += K_1 * angle_err;    //사후 추정
  angle_speed = gyro_m - q_bias;   //출력 값의 미분 값; 최적 각속도 작업
  angle += K_0 * angle_err; ////사후 추정; 최적 각도 작업
}
```

**테스트 결과**

밸런스 카를 잘 설치하고, 소스 코드를 업로드하고 전원을 켜세요; 슬라이드 스위치를 ON으로 설정하세요.

아두이노 IDE를 열고 보드레이트를 9600으로 설정하세요. 시리얼 모니터가 값을 팝업합니다.

![](media/11aa2cabab2af5ca81c489696100ffcf.png)

<a id="project-9"></a>
## 프로젝트 9: PID 원리
[맨 위로](#top)

**설명:**

비례, 적분 및 미분은 선형으로 결합되어 제어 양을 형성하며, 제어 객체를 이 제어 양으로 제어합니다. 이러한 컨트롤러를 PID 컨트롤러라고 합니다.

아날로그 제어 시스템에서 컨트롤러의 가장 일반적인 제어 법칙은 PID 제어입니다.

**일반 아날로그 PID 제어 시스템의 블록 다이어그램은 아래에 표시됩니다.**

![](media/c94475c08788e733e7400057d2c753d1.png)

시스템은 아날로그 PID 컨트롤러와 제어되는 객체로 구성됩니다.

그림에서 **r(t)**는 주어진 값; **y(t)**는 시스템의 실제 출력 값;

제어 편차 **e(t)**는 주어진 값에서 실제 출력 값을 뺍니다.

$$
e(t) = r(t) − y(t)
$$
**e(t)**는 PID 제어의 입력;

**u(t)**는 PID 컨트롤러의 출력이자 제어되는 객체의 입력.

**따라서 아날로그 PID 컨트롤러의 제어 법칙은 다음과 같습니다:**

![](media/99cdbd2999397eeb77e86575d30b3f41.png)

**Kp:** 컨트롤러의 비례 계수;

**Ti:** 컨트롤러의 적분 시간, 적분 계수라고도 함;

**Td:** 컨트롤러의 미분 시간, 미분 계수라고도 함.

**(1) 비례 부분**

비례 부분의 수학 공식은: **Kp×e(t)**

아날로그 PID 컨트롤러에서 비례 링크는 편차 순간에 반응합니다.

편차가 발생하면 컨트롤러는 즉시 제어 동작을 생성하여 제어 양이 편차를 감소시키는 방향으로 변경되도록 합니다.

제어 강도는 비례 계수 **Kp**에 따라 다릅니다.

비례 계수 **Kp**가 클수록 제어 효과가 강해지고, 전이 과정이 빨라지고, 제어 과정의 정적 편차가 작아집니다.

그러나 **Kp**가 클수록 진동이 발생하기 쉽고 시스템 안정성을 파괴할 수 있습니다.

따라서 비례 계수 **Kp**의 선택은 적절해야 하며, 작은 전이 시간과 작은 안정 정적 차이를 달성해야 합니다.

**(2) 적분 부분**

적분 부분의 수학 공식은:

![](media/e0a17789364e36b86625dd1e17965eef.png)

적분 부분의 공식에서 편차가 있는 한 그 제어 효과는 계속 증가합니다.

편차 **e(t)=0**일 때만 적분이 상수가 되고 제어 효과가 증가하지 않습니다.

적분 링크의 조정 기능은 시스템의 정적 편차를 제거할 수 있음을 알 수 있습니다.

적분 링크는 시스템 응답 속도를 감소시키지만 시스템의 오버슈트를 증가시킵니다.

적분 계수 **Ti**가 클수록 적분 축적량이 약해집니다. 이 때 시스템은 전이 중에 진동하지 않습니다.

적분 계수 **Ti**를 증가시키면 정적 편차 제거 과정에 필요한 시간이 길어집니다; 그러나 오버슈트 양을 줄이고 시스템 안정성을 향상시킬 수 있습니다.

따라서 **Ti**는 실제 제어의 특정 요구 사항에 따라 결정되어야 합니다.

**(3) 미분 부분**

미분 부분의 수학 공식은:

![](media/7759577762ff26ecdc60051be97634eb.png)

정적 편차를 제거하는 것 외에도 실제 제어 시스템은 가속화된 조정 과정을 요구합니다.

편차가 발생하거나 편차 변화 순간에 (비례 링크의 역할) 즉각적인 응답뿐만 아니라 편차 값이 더 커지기 전에 적절한 수정을 제공해야 합니다.

이를 위해 미분 링크를 PI 컨트롤러에 추가하여 PID 컨트롤러를 형성할 수 있습니다.

미분 링크의 역할은 편차 변화에 대해 제어합니다. 편차가 빠르게 변할수록 PID 컨트롤러의 출력이 커지고, 편차 값이 더 커지기 전에 수정을 할 수 있습니다.

미분 동작을 도입하면 오버슈트를 줄이고 진동을 억제하며 시스템을 안정화시키는 데 도움이 됩니다. 특히 고차 시스템의 경우 시스템의 추적 속도를 가속화합니다.

그러나 미분의 효과는 입력 신호의 노이즈에 민감합니다.

노이즈가 높은 시스템의 경우 미분 신호를 사용하지 않거나 미분 동작 전에 입력 신호를 필터링하는 것이 좋습니다.

미분 부분의 효과는 미분 시간 상수 **Td**에 의해 결정됩니다.

**Td**가 클수록 편차 **e(t)**의 변동을 억제하는 효과가 강합니다;

**Td**가 작을수록 편차 **e(t)**에 대한 저항 효과가 약합니다.

미분 부분은 분명히 시스템 안정성에 큰 영향을 미칩니다.

적절한 미분 계수 **Td**를 선택하여 미분 동작을 최적화해야 합니다.

<a id="project-10"></a>
## 프로젝트 10: 직립 루프 조정
[맨 위로](#top)

**설명:**

이전 프로젝트에서 PD를 사용하여 거의 수평면에서 카의 각도를 조정하여 밸런스를 맞추는 방법을 소개했습니다.

그러나 외부 힘에 의해 또는 경사면에서 카가 밸런스를 유지할 수 없습니다. 속도에 오류가 있기 때문입니다. 따라서 밸런스를 위해 카의 속도를 조정해야 합니다.

따라서 속도 측정 모듈이 필요합니다.

**우리가 사용한 모터에는 속도 측정을 위한 홀 인코더가 함께 제공됩니다.**

이전 레슨을 기반으로 속도를 조정하기 위해 PI (비례 및 적분)를 추가합니다. 이렇게 하면 경사면에서도 카가 밸런스를 유지할 수 있습니다.

여기 속도 루프는 양의 피드백입니다. 즉, 카가 뒤로 가고 있다면 카가 더 빠르게 앞으로 가는 것을 의미합니다.

구체적으로 손으로 카를 살짝 밀면 카의 바퀴가 밀리는 방향으로 가속되며, 즉 카가 기울어진 방향으로 가속됩니다. 그러면 카의 기울기 각도가 반대 방향으로 역전되며, 즉 밀리는 방향과 반대로 됩니다; 카가 기울어진 방향으로 가속되며 속도가 가속됩니다.

속도의 PI 조정은 이전에 생성된 기울기 각도를 오프셋하여 초기 평형점 근처로 돌아가며 떨어지지 않습니다.

**PI 규제의 원리와 기능:**

**PI_pwm = ki_speed \* (setp0 - positions) + kp_speed \* (setp0 - speeds_filter);** // 속도 루프 제어

비례 매개변수 **(** **kp_speed )**로 속도를 조정하여 카가 필요한 속도에 빠르게 접근하도록 합니다;

적분 매개변수 **(ki_speed)**로 속도 오류의 누적 값을 조정하여 정적 오류를 제거합니다.

![](media/06ad11db8db6c0c75411d8f6ccd38a4a.jpeg)

**예를 들어:**

물이 1미터 높이로 유지되는 물통이 있다고 가정합니다.

초기 물 높이가 0.2미터라고 가정하면 현재 물 높이와 목표 물 높이 사이에 오류가 있습니다. 오류는 0.8m입니다.

이 때 물 높이를 제어하기 위해 물을 추가한다고 가정합니다.

단순히 비례 제어 알고리즘을 사용하면 추가되는 물 양 **(u)**는 오류에 비례합니다. 즉, **u=kp\*error**

**kp=0.5**, **t=1** (첫 번째 물 추가), **u=0.5\*0.8=0.4**, 0.4m 물 양을 추가해야 합니다; 현재 물 높이는 **0.2m+0.4m=0.6m**가 됩니다.

그 다음 **t=2** (두 번째 물 추가), 물 높이 0.6m, 오류 0.4m, 추가해야 할 물 양 **u=0.5\*0.4=0.2 ;** 현재 물 높이는 **0.6m+0.2m=0.8m**가 됩니다.

계속 이 계산으로 물 높이가 1m에 도달합니다.

그러나 이러한 단일 비례 제어에는 몇 가지 단점이 있습니다. 그 중 하나는 – **정적 오류!**

위의 예에서 kp 값에 따라 시스템이 결국 1미터에 도달하지만 정적 오류 없이.

그러나 또 다른 상황을 고려합니다. 물통에 물이 새고 있다고 가정합니다. 매번 물을 추가할 때 0.1m 높이의 물이 누출된다고 가정합니다.

**kp=0.5**라고 가정하면 여러 번 물을 추가한 후 물통의 물 높이가 0.8m에 도달하고 더 이상 변하지 않습니다! 왜냐하면 물 높이가 0.8m일 때 **error =1-0.8=0.2m**이기 때문입니다.

따라서 물통에 추가되는 물 양은 **u=0.5\*0.2=0.1m**입니다.

동시에 물통에서 0.1m의 물이 매번 흘러나옵니다. 추가된 물이 누출된 물을 상쇄하므로 물 높이가 변하지 않습니다!

즉, 목표 물 높이는 1m이지만 시스템은 결국 0.8m에 도달하고 변하지 않습니다. 시스템이 안정에 도달했습니다. 결과 오류는 정적 오류입니다.

따라서 단일 비례 제어만으로는 많은 경우 요구 사항을 충족하지 않습니다. 적분 제어 알고리즘을 도입해야 합니다.

위의 예에서 개별 비례 제어만 사용할 때 시스템이 정적 오류에 갇히는 것을 찾을 수 있습니다. 그래서 적분 제어 알고리즘을 도입합니다.

제어에서 오류의 적분에 비례하는 구성 요소를 도입합니다.

**따라서 비례 + 적분 제어 알고리즘은:**

**u=kp\*error+ ki∗∫error**

여기서 다시 위의 예를 사용합니다.

첫 번째 오류는 0.8, 두 번째 오류는 0.4. 이 시점에서 오류의 적분 (이산의 경우 적분은 실제로 누적임)

![image-20230426164915487](media/image-20230426164915487.png)

이 시점의 제어 양은 비례 부분 외에 이 적분 항에 계수 **ki**를 곱한 부분도 있습니다.

이 적분 항이 이전 오류를 누적하기 때문에 정적 오류를 잘 제거할 수 있습니다.

(단순 비례 항만 있을 때 위의 예에서 시스템이 정적 오류에 갇히는 경우를 가정하면 적분 항의 추가로 인해 입력이 증가하여 물통의 물 높이가 0.8보다 커지고 점차 목표 1.0에 도달합니다.)

이것이 적분 항의 기능입니다.

**소스 코드:**

```c
#include <MsTimer2.h>        //내부 타이머 2
#include <PinChangeInt.h>    //이 라이브러리 파일은 UNO 보드의 모든 핀을 외부 인터럽트로 만들 수 있습니다.
#include <MPU6050.h>      //MPU6050 라이브러리
#include <Wire.h>        //IIC 라이브러리

MPU6050 mpu6050;     //MPU6050 객체 인스턴스화; 이름 mpu6050
int16_t ax, ay, az, gx, gy, gz;     //3축 가속도, 3축 자이로스코프 변수 정의

//TB6612 핀
const int right_R1=8;    
const int right_R2=12;
const int PWM_R=10;
const int left_L1=7;
const int left_L2=6;
const int PWM_L=9;

///////////////////////angle parameters//////////////////////////////
float angle_X; //가속도로 X축의 기울기 각도 변수 계산
float angle_Y; //가속도로 Y축의 기울기 각도 변수 계산
float angle0 = 1; //실제 측정 각도 (이상적으로 0도)
float Gyro_x,Gyro_y,Gyro_z;  //자이로스코프로 각속도 계산
///////////////////////angle parameters//////////////////////////////

///////////////////////Kalman_Filter////////////////////////////
float Q_angle = 0.001;  //자이로스코프 노이즈 공분산
float Q_gyro = 0.003;    //자이로스코프 드리프트 노이즈 공분산
float R_angle = 0.5;    //가속도계 공분산
char C_0 = 1;
float dt = 0.005; //dt 값은 필터 샘플링 시간입니다.
float K1 = 0.05; //최적 추정의 편차를 계산하는 칼만 게인을 포함하는 함수입니다.
float K_0,K_1,t_0,t_1;
float angle_err;
float q_bias;    //자이로 드리프트

float accelz = 0;
float angle;
float angleY_one;
float angle_speed;

float Pdot[4] = { 0, 0, 0, 0};
float P[2][2] = {{ 1, 0 }, { 0, 1 }};
float  PCt_0, PCt_1, E;
//////////////////////Kalman_Filter/////////////////////////

//////////////////////PID parameters///////////////////////////////
double kp = 34, ki = 0, kd = 0.62;                   //각도 루프 매개변수
double kp_speed = 3.6, ki_speed = 0.080, kd_speed = 0;   //속도 루프 매개변수
double setp0 = 0; //각도 밸런스 포인트
int PD_pwm;  //각도 출력
float pwm1=0,pwm2=0;

//////////////////Interrupt speed measurement/////////////////////////////
#define PinA_left 5  //외부 인터럽트
#define PinA_right 4   //외부 인터럽트
volatile long count_right = 0;//홀 인코더로 계산된 펄스 값을 계산하는 데 사용 (volatile long 유형은 값이 유효하도록 보장)
volatile long count_left = 0;
int speedcc = 0;
//////////////////////pulse calculation/////////////////////////
int lz = 0;
int rz = 0;
int rpluse = 0;
int lpluse = 0;
int pulseright,pulseleft;
////////////////////////////////PI variable parameters//////////////////////////
float speeds_filterold=0;
float positions=0;
int flag1;
double PI_pwm;
int cc;
int speedout;
float speeds_filter;

void setup() 
{
  //모터의 핀을 OUTPUT으로 설정
  pinMode(right_R1,OUTPUT);       
  pinMode(right_R2,OUTPUT);
  pinMode(left_L1,OUTPUT);
  pinMode(left_L2,OUTPUT);
  pinMode(PWM_R,OUTPUT);
  pinMode(PWM_L,OUTPUT);

  //초기 상태 값 할당
  digitalWrite(right_R1,1);
  digitalWrite(right_R2,0);
  digitalWrite(left_L1,0);
  digitalWrite(left_L2,1);
  analogWrite(PWM_R,0);
  analogWrite(PWM_L,0);

  pinMode(PinA_left, INPUT);  //속도 코드 휠 입력
  pinMode(PinA_right, INPUT);

  //I2C 버스 가입
  Wire.begin();                            //I2C 버스 시퀀스 가입
  Serial.begin(9600);                       //시리얼 모니터 열기, 보드레이트 9600 설정
  delay(1500);
  mpu6050.initialize();                       //MPU6050 초기화
  delay(2);

  //5ms; 타이머2를 사용하여 타이머 인터럽트 설정 (참고：타이머2 사용은 핀3 핀11의 PWM 출력에 영향을 미침)
  MsTimer2::set(5, DSzhongduan);    //5ms ; DSzhongduan 함수를 한 번 실행
  MsTimer2::start();    //인터럽트 시작
}

void loop() 
{
  Serial.println(angle);
  delay(100);
  //Serial.println(PD_pwm);
  //Serial.println(pwm1);
  //Serial.println(pwm2);
  //Serial.print("pulseright = ");
  //Serial.println(pulseright);
  //Serial.print("pulseleft = ");
  //Serial.println(pulseleft);
  //Serial.println(PI_pwm);
  //Serial.println(speeds_filter);
  //Serial.println (positions);
  
  //5ms마다 바퀴 속도를 계산하는 외부 인터럽트
  attachPinChangeInterrupt(PinA_left, Code_left, CHANGE);          //PinA_left 레벨 변경 트리거 외부 인터럽트; 서브함수 Code_left 실행
  attachPinChangeInterrupt(PinA_right, Code_right, CHANGE);       //PinA_right 레벨 변경 트리거 외부 인터럽트; 서브함수 Code_right 실행
}

/////////////////////Hall calculation/////////////////////////
//왼쪽 속도 코드 휠 카운트
void Code_left() 
{
  count_left ++;
} 
//오른쪽 속도 코드 휠 카운트
void Code_right() 
{
  count_right ++;
} 
////////////////////pulse calculation///////////////////////
void countpluse()
{
  lz = count_left;     //코드 휠이 카운트한 값을 lz에 할당
  rz = count_right;

  count_left = 0;     //코드 카운터 클리어
  count_right = 0;

  lpluse = lz;
  rpluse = rz;

  if ((pwm1 < 0) && (pwm2 < 0))                     //이동 방향 판단; 뒤로（PWM, 즉 모터 전압이 음수）, 펄스 수는 음수
  {
    rpluse = -rpluse;
    lpluse = -lpluse;
  }
  else if ((pwm1 > 0) && (pwm2 > 0))                 //앞으로（PWM, 즉 모터 전압이 양수）, 펄스 수는 양수
  {
    rpluse = rpluse;
    lpluse = lpluse;
  }
  else if ((pwm1 < 0) && (pwm2 > 0))                 //카의 회전 방향 판단; 왼쪽으로 회전; 오른쪽 펄스 수는 양수; 왼쪽 펄스 수는 음수.
  {
    rpluse = rpluse;
    lpluse = -lpluse;
  }
  else if ((pwm1 > 0) && (pwm2 < 0))               //카의 회전 방향 판단; 오른쪽으로 회전; 오른쪽 펄스 수는 음수; 왼쪽 펄스 수는 양수.
  {
    rpluse = -rpluse;
    lpluse = lpluse;
  }

  //5ms마다 인터럽트 입력; 펄스 수 중첩
  pulseright += rpluse;
  pulseleft += lpluse;
}

/////////////////////////////////interrupts////////////////////////////
void DSzhongduan()
{
  sei();  //전체 인터럽트 허용
  countpluse();        //펄스 중첩 서브함수
  mpu6050.getMotion6(&ax, &ay, &az, &gx, &gy, &gz);     //IIC로 MPU6050 6축 데이터 ax ay az gx gy gz 얻기
  angle_calculate(ax, ay, az, gx, gy, gz, dt, Q_angle, Q_gyro, R_angle, C_0, K1);      //각도와 칼만 필터링 얻기
  PD();         //각도 루프 PD 제어
  anglePWM();

  cc++;
  if(cc>=8)     //5*8=40，40ms마다 속도 PI 알고리즘 입력
  {
    speedpiout();   
    cc=0;  //클리어
  }
}
///////////////////////////////////////////////////////////

/////////////////////////////angle calculation///////////////////////
void angle_calculate(int16_t ax,int16_t ay,int16_t az,int16_t gx,int16_t gy,int16_t gz,float dt,float Q_angle,float Q_gyro,float R_angle,float C_0,float K1)
{
  float Angle = -atan2(ay , az) * (180/ PI);           //방사형 회전 각도 계산 공식; 음수 부호는 방향 처리
  Gyro_x = -gx / 131;              //자이로스코프로 계산된 X축 각속도; 음수 부호는 방향 처리
  Kalman_Filter(Angle, Gyro_x);            //칼만 필터링
  //회전 각도 Z축 매개변수
  Gyro_z = -gz / 131;                      //Z축 각속도
  //accelz = az / 16.4;

  float angleAx = -atan2(ax, az) * (180 / PI); //X축과의 각도 계산
  Gyro_y = -gy / 131.00; //Y축 각속도
  Yiorderfilter(angleAx, Gyro_y); //1차 필터링
}
////////////////////////////////////////////////////////////////

///////////////////////////////KalmanFilter/////////////////////
void Kalman_Filter(double angle_m, double gyro_m)
{
  angle += (gyro_m - q_bias) * dt;          //사전 추정
  angle_err = angle_m - angle;
  
  Pdot[0] = Q_angle - P[0][1] - P[1][0];    //방위각 오차 공분산 미분
  Pdot[1] = - P[1][1];
  Pdot[2] = - P[1][1];
  Pdot[3] = Q_gyro;
  
  P[0][0] += Pdot[0] * dt;    //사전 추정 오차 공분산 미분 적분
  P[0][1] += Pdot[1] * dt;
  P[1][0] += Pdot[2] * dt;
  P[1][1] += Pdot[3] * dt;
  
  //행렬 곱셈의 중간 변수
  PCt_0 = C_0 * P[0][0];
  PCt_1 = C_0 * P[1][0];
  //분모
  E = R_angle + C_0 * PCt_0;
  //게인 값
  K_0 = PCt_0 / E;
  K_1 = PCt_1 / E;
  
  t_0 = PCt_0;  //행렬 곱셈의 중간 변수
  t_1 = C_0 * P[0][1];
  
  P[0][0] -= K_0 * t_0;    //사후 추정 오차 공분산
  P[0][1] -= K_0 * t_1;
  P[1][0] -= K_1 * t_0;
  P[1][1] -= K_1 * t_1;
  
  q_bias += K_1 * angle_err;    //사후 추정
  angle_speed = gyro_m - q_bias;   //출력 값의 미분 값; 최적 각속도 작업
  angle += K_0 * angle_err; ////사후 추정; 최적 각도 작업
}

/////////////////////1차 필터링/////////////////
void Yiorderfilter(float angle_m, float gyro_m)
{
  angleY_one = K1 * angle_m + (1 - K1) * (angleY_one + gyro_m * dt);
}

//////////////////angle PD////////////////////
void PD()
{
  PD_pwm = kp * (angle + angle0) + kd * angle_speed; //PD 각도 루프 제어
}

//////////////////speed PI////////////////////
void speedpiout()
{
  float speeds = (pulseleft + pulseright) * 1.0;      //차량 속도  펄스 값
  pulseright = pulseleft = 0;      //클리어
  speeds_filterold *= 0.7;         //1차 보완 필터링
  speeds_filter = speeds_filterold + speeds * 0.3;
  speeds_filterold = speeds_filter;
  positions += speeds_filter;
  positions = constrain(positions, -3550,3550);    //적분 포화 방지
  PI_pwm = ki_speed * (setp0 - positions) + kp_speed * (setp0 - speeds_filter);      //속도 루프 제어 PI
}
//////////////////speed PI////////////////////


////////////////////////////PWM end value/////////////////////////////
void anglePWM()
{
  pwm2=-PD_pwm - PI_pwm ;           //최종 PWM 값을 모터에 할당
  pwm1=-PD_pwm - PI_pwm ;
  
  if(pwm1>255)             //PWM 값이 255보다 크지 않도록 제한
  {
    pwm1=255;
  }
  if(pwm1<-255) 
  {
    pwm1=-255;
  }
  if(pwm2>255)
  {
    pwm2=255;
  }
  if(pwm2<-255)
  {
    pwm2=-255;
  }

  if(angle>80 || angle<-80) //밸런스 카의 기울기 각도가 45°보다 크면 모터가 정지합니다.
  {
    pwm1=pwm2=0;
  }

 if(pwm2>=0)//PWM의 양수와 음수에 따라 모터의 방향과 속도를 결정
  {
    digitalWrite(left_L1,LOW);
    digitalWrite(left_L2,HIGH);
    analogWrite(PWM_L,pwm2);
  }
  else
  {
    digitalWrite(left_L1,HIGH);
    digitalWrite(left_L2,LOW);
    analogWrite(PWM_L,-pwm2);
  }

  if(pwm1>=0)
  {
    digitalWrite(right_R1,LOW);
    digitalWrite(right_R2,HIGH);
    analogWrite(PWM_R,pwm1);
  }
  else
  {
    digitalWrite(right_R1,HIGH);
    digitalWrite(right_R2,LOW);
    analogWrite(PWM_R,-pwm1);
  }
}
```

**테스트 결과**

밸런스 카를 잘 설치하고, 소스 코드를 업로드하고 전원을 켜세요; 전원 스위치를 ON으로 설정하세요.

밸런스 카가 책상 위에 똑바로 서 있습니다.

아두이노 IDE를 열고 보드레이트를 9600으로 설정하세요. 시리얼 모니터가 밸런스 카의 기울기 값을 팝업합니다.

![](media/f0773cc27ba2cb214458b74c9c06f7a4.png)

USB 케이블을 제거하고 밸런스 카를 바닥에 똑바로 세우세요.



<a id="project-11"></a>
## 프로젝트 11: 속도 루프 조정
[맨 위로](#top)

![](media/d36824f1d6537907e3426bddcc8eca98.jpeg)

**설명:**

앞선 프로젝트에서 PD 제어로 거의 수평한 바닥에서 각도를 맞춰 차를 세울 수 있다고 설명했습니다.

하지만 외력이 가해지거나 경사면에서는 속도 오차 때문에 균형을 유지하지 못합니다. 따라서 균형 유지를 위해 속도 제어가 필요합니다.

이를 위해 속도 측정 모듈이 필요합니다.

**사용하는 모터에는 속도 측정을 위한 홀(홀 이펙트) 인코더가 내장되어 있습니다.**

이전에 배운 내용을 바탕으로 속도에 PI(비례+적분) 제어를 추가합니다. 이렇게 하면 경사면에서도 균형을 유지하도록 제어할 수 있습니다.

여기서 속도 루프는 양의 피드백입니다. 즉, 차가 뒤로 밀리면 앞으로 더 빨리 움직이도록 합니다.

구체적으로, 차를 손으로 살짝 밀면 바퀴가 밀린 방향(차가 기울어진 방향)으로 가속합니다. 그 결과 차의 기울기 각이 반대 방향으로 되돌아가며, 기울어진 방향으로 가속해 초기 균형점으로 복귀합니다.

속도에 대한 PI 보정은 이전에 발생한 기울기(딥) 각을 상쇄하여 넘어지지 않고 초기 균형점 근처로 돌아오게 합니다.

**PI 제어의 원리와 역할:**

**PI_pwm = ki_speed \* (setp0 - positions) + kp_speed \* (setp0 - speeds_filter);** // 속도 루프 제어

비례 이득 **(kp_speed)** 으로 속도를 조정해 목표 속도에 신속히 접근시키고,

적분 이득 **(ki_speed)** 으로 속도 오차의 누적값을 보정해 정상상태 오차를 제거합니다.

![](media/06ad11db8db6c0c75411d8f6ccd38a4a.jpeg)

**예시:**

수조의 수위를 항상 1m로 유지하고 싶다고 합시다.

초기 수위가 0.2m라면 목표와 현재의 오차는 0.8m입니다. 물을 보충해 수위를 제어합니다.

비례 제어만 사용하면 보충량 **u** 는 오차에 비례합니다. 즉 **u = kp\*error** 입니다.

예를 들어 **kp=0.5**, 첫 번째 보충(**t=1**)에서 **u=0.5\*0.8=0.4** 이므로 0.4m를 보충해 수위가 **0.6m** 가 됩니다. 두 번째(**t=2**)에는 오차가 0.4이므로 **u=0.2** 를 보충해 **0.8m** 가 됩니다. 이런 식으로 수위는 1m에 수렴합니다.

하지만 실제로는 누수 등으로 인해 비례 제어만으로는 **정상상태 오차** 가 생길 수 있습니다. 예를 들어 매번 0.1m가 새면, 어느 시점 이후에는 보충량과 누수가 같아져 수위가 **0.8m** 에 머물게 됩니다. 목표는 1m인데 0.8m에서 안정되어 버리는 것이죠.

따라서 많은 경우 비례 제어만으로는 부족하며, 오차의 누적을 보상하는 적분 제어가 필요합니다.

즉, 비례+적분 제어식은 다음과 같습니다.

**u = kp\*error + ki\*∫error**

앞서 든 예시를 계속 사용해 보겠습니다.

첫 번째 시점의 오차는 0.8, 두 번째 시점의 오차는 0.4입니다. 이때 오차의 적분(이산계에서는 실제로 누적 합계)을 고려합니다.

![image-20230426164915487](media/image-20230426164915487.png)

이때 제어량은 비례 항에 더해, 오차 적분 항에 계수 **ki** 를 곱한 항이 추가됩니다.

적분 항이 과거의 오차를 누적하므로 정상상태 오차를 효과적으로 제거할 수 있습니다.

(비례 제어만으로는 위 예에서처럼 0.8 근처에 머물 수 있지만, 적분 항을 더하면 입력이 증가하여 수위가 0.8을 넘어 목표 1.0에 점차 도달합니다.)

이것이 적분 항의 역할입니다.

**소스 코드:**

```c
#include <MsTimer2.h>        // 내부 타이머 2
#include <PinChangeInt.h>    // UNO 보드의 모든 핀을 외부 인터럽트로 사용 가능
#include <MPU6050.h>      // MPU6050 라이브러리
#include <Wire.h>        // IIC 라이브러리

MPU6050 mpu6050;     // MPU6050 객체 인스턴스
int16_t ax, ay, az, gx, gy, gz;     // 3축 가속도/3축 자이로 변수

//TB6612 핀
const int right_R1=8;    
const int right_R2=12;
const int PWM_R=10;
const int left_L1=7;
const int left_L2=6;
const int PWM_L=9;

///////////////////////angle parameters//////////////////////////////
float angle_X; //Calculate the tilt angle variable about the X axis from the acceleration
float angle_Y; // 가속도로 Y축 기울기 각 계산 변수
float angle0 = 1; // 실제 측정 각(이상적으로 0도)
float Gyro_x,Gyro_y,Gyro_z;  // 자이로 기반 각속도
///////////////////////angle parameters//////////////////////////////

///////////////////////Kalman_Filter////////////////////////////
float Q_angle = 0.001;  // 자이로 노이즈 공분산
float Q_gyro = 0.003;    // 자이로 드리프트 노이즈 공분산
float R_angle = 0.5;    // 가속도계 공분산
char C_0 = 1;
float dt = 0.005; // 필터 샘플링 시간 
float K1 = 0.05; // 칼만 이득 관련 함수(최적 추정 편차 계산)
float K_0,K_1,t_0,t_1;
float angle_err;
float q_bias;    // 자이로 드리프트

float accelz = 0;
float angle;
float angleY_one;
float angle_speed;

float Pdot[4] = { 0, 0, 0, 0};
float P[2][2] = {{ 1, 0 }, { 0, 1 }};
float  PCt_0, PCt_1, E;
//////////////////////Kalman_Filter/////////////////////////

//////////////////////PID 파라미터///////////////////////////////
double kp = 34, ki = 0, kd = 0.62;                   // 각도 루프 파라미터
double kp_speed = 3.6, ki_speed = 0.080, kd_speed = 0;   // 속도 루프 파라미터
double setp0 = 0; // 각도 균형점
int PD_pwm;  // 각도 출력
float pwm1=0,pwm2=0;

//////////////////속도 측정을 위한 인터럽트/////////////////////////////
#define PinA_left 5  //외부 인터럽트
#define PinA_right 4   //외부 인터럽트
volatile long count_right = 0;//홀 인코더가 계산한 펄스 값을 저장(volatile long은 값의 유효성을 보장)
volatile long count_left = 0;
int speedcc = 0;
//////////////////////pulse calculation/////////////////////////
int lz = 0;
int rz = 0;
int rpluse = 0;
int lpluse = 0;
int pulseright,pulseleft;
////////////////////////////////PI variable parameters//////////////////////////
float speeds_filterold=0;
float positions=0;
int flag1;
double PI_pwm;
int cc;
int speedout;
float speeds_filter;

void setup() 
{
  // 모터 관련 핀을 출력으로 설정
  pinMode(right_R1,OUTPUT);       
  pinMode(right_R2,OUTPUT);
  pinMode(left_L1,OUTPUT);
  pinMode(left_L2,OUTPUT);
  pinMode(PWM_R,OUTPUT);
  pinMode(PWM_L,OUTPUT);

  // 초기 상태 값 설정
  digitalWrite(right_R1,1);
  digitalWrite(right_R2,0);
  digitalWrite(left_L1,0);
  digitalWrite(left_L2,1);
  analogWrite(PWM_R,0);
  analogWrite(PWM_L,0);

  pinMode(PinA_left, INPUT);  //속도 코드휠 입력
  pinMode(PinA_right, INPUT);

  // I2C 버스 시작
  Wire.begin();                            //I2C 버스 참가
  Serial.begin(9600);                       //시리얼 모니터 보드레이트 9600 설정
  delay(1500);
  mpu6050.initialize();                       //MPU6050 초기화
  delay(2);

  // 5ms 주기 타이머2 인터럽트 설정 (참고: 타이머2 사용 시 3,11번 핀 PWM에 영향)
  MsTimer2::set(5, DSzhongduan);    // 5ms마다 DSzhongduan 실행
  MsTimer2::start();    // 인터럽트 시작
}

void loop() 
{
  Serial.println(angle);
  delay(100);
  //Serial.println(PD_pwm);
  //Serial.println(pwm1);
  //Serial.println(pwm2);
  //Serial.print("pulseright = ");
  //Serial.println(pulseright);
  //Serial.print("pulseleft = ");
  //Serial.println(pulseleft);
  //Serial.println(PI_pwm);
  //Serial.println(speeds_filter);
  //Serial.println (positions);
  
  // 바퀴 속도 계산용 외부 인터럽트
  attachPinChangeInterrupt(PinA_left, Code_left, CHANGE);          //PinA_left 레벨 변화 시 Code_left 실행
  attachPinChangeInterrupt(PinA_right, Code_right, CHANGE);       //PinA_right 레벨 변화 시 Code_right 실행
}

/////////////////////홀 계산/////////////////////////
// 왼쪽 속도 코드휠 카운트
void Code_left() 
{
  count_left ++;
} 
// 오른쪽 속도 코드휠 카운트
void Code_right() 
{
  count_right ++;
} 
////////////////////펄스 계산///////////////////////
void countpluse()
{
  lz = count_left;     //코드휠이 센 값을 lz에 대입
  rz = count_right;

  count_left = 0;     //카운터 초기화
  count_right = 0;

  lpluse = lz;
  rpluse = rz;

  if ((pwm1 < 0) && (pwm2 < 0))                     // 이동 방향 판별; 후진이면(모터 전압 음수) 펄스는 음수
  {
    rpluse = -rpluse;
    lpluse = -lpluse;
  }
  else if ((pwm1 > 0) && (pwm2 > 0))                 // 전진이면(모터 전압 양수) 펄스는 양수
  {
    rpluse = rpluse;
    lpluse = lpluse;
  }
  else if ((pwm1 < 0) && (pwm2 > 0))                 // 좌회전: 오른쪽 펄스 양수, 왼쪽 펄스 음수
  {
    rpluse = rpluse;
    lpluse = -lpluse;
  }
  else if ((pwm1 > 0) && (pwm2 < 0))               // 우회전: 오른쪽 펄스 음수, 왼쪽 펄스 양수
  {
    rpluse = -rpluse;
    lpluse = lpluse;
  }

  // 5ms마다 인터럽트 진입; 펄스 누적
  pulseright += rpluse;
  pulseleft += lpluse;
}

/////////////////////////////////interrupts////////////////////////////
void DSzhongduan()
{
  sei();  // 전역 인터럽트 허용
  countpluse();        // 펄스 누적 처리
  mpu6050.getMotion6(&ax, &ay, &az, &gx, &gy, &gz);     // IIC로 MPU6050 6축 데이터 읽기
  angle_calculate(ax, ay, az, gx, gy, gz, dt, Q_angle, Q_gyro, R_angle, C_0, K1);      // 각도 계산 및 칼만 필터링
  PD();         // 각도 루프 PD 제어
  anglePWM();

  cc++;
  if(cc>=8)     // 5*8=40 → 40ms마다 속도 PI 알고리즘 실행
  {
    speedpiout();   
    cc=0;  // 초기화
  }
}
///////////////////////////////////////////////////////////

/////////////////////////////각도 계산///////////////////////
void angle_calculate(int16_t ax,int16_t ay,int16_t az,int16_t gx,int16_t gy,int16_t gz,float dt,float Q_angle,float Q_gyro,float R_angle,float C_0,float K1)
{
  float Angle = -atan2(ay , az) * (180/ PI);           // 회전 각도 계산(부호는 방향 보정)
  Gyro_x = -gx / 131;              // 자이로 기반 X축 각속도(부호로 방향 보정)
  Kalman_Filter(Angle, Gyro_x);            // 칼만 필터링
  // Z축 파라미터
  Gyro_z = -gz / 131;                      // Z축 각속도
  //accelz = az / 16.4;

  float angleAx = -atan2(ax, az) * (180 / PI); // X축 각도 계산
  Gyro_y = -gy / 131.00; // Y축 각속도
  Yiorderfilter(angleAx, Gyro_y); // 1차 필터
}
////////////////////////////////////////////////////////////////

///////////////////////////////칼만 필터/////////////////////
void Kalman_Filter(double angle_m, double gyro_m)
{
  angle += (gyro_m - q_bias) * dt;          // 사전 추정
  angle_err = angle_m - angle;
  
  Pdot[0] = Q_angle - P[0][1] - P[1][0];    // 방위 오차 공분산의 미분
  Pdot[1] = - P[1][1];
  Pdot[2] = - P[1][1];
  Pdot[3] = Q_gyro;
  
  P[0][0] += Pdot[0] * dt;    // 사전 추정 오차 공분산 적분
  P[0][1] += Pdot[1] * dt;
  P[1][0] += Pdot[2] * dt;
  P[1][1] += Pdot[3] * dt;
  
  // 행렬 곱 중간 변수
  PCt_0 = C_0 * P[0][0];
  PCt_1 = C_0 * P[1][0];
  // 분모
  E = R_angle + C_0 * PCt_0;
  // 이득
  K_0 = PCt_0 / E;
  K_1 = PCt_1 / E;
  
  t_0 = PCt_0;  // 행렬 곱 중간 변수
  t_1 = C_0 * P[0][1];
  
  P[0][0] -= K_0 * t_0;    // 사후 추정 오차 공분산
  P[0][1] -= K_0 * t_1;
  P[1][0] -= K_1 * t_0;
  P[1][1] -= K_1 * t_1;
  
  q_bias += K_1 * angle_err;    // 사후 추정
  angle_speed = gyro_m - q_bias;   // 최적 각속도
  angle += K_0 * angle_err; // 사후 추정으로 최적 각도
}

/////////////////////1차 필터/////////////////
void Yiorderfilter(float angle_m, float gyro_m)
{
  angleY_one = K1 * angle_m + (1 - K1) * (angleY_one + gyro_m * dt);
}

//////////////////angle PD////////////////////
void PD()
{
  PD_pwm = kp * (angle + angle0) + kd * angle_speed; //PD angle loop control
}

//////////////////speed PI////////////////////
void speedpiout()
{
  float speeds = (pulseleft + pulseright) * 1.0;      //Vehicle speed  pulse value
  pulseright = pulseleft = 0;      //Clear
  speeds_filterold *= 0.7;         // 1차 보완 필터링
  speeds_filter = speeds_filterold + speeds * 0.3;
  speeds_filterold = speeds_filter;
  positions += speeds_filter;
  positions = constrain(positions, -3550,3550);    //Anti-integral saturation
  PI_pwm = ki_speed * (setp0 - positions) + kp_speed * (setp0 - speeds_filter);      // 속도 루프 PI 제어
}
//////////////////speed PI////////////////////


////////////////////////////PWM end value/////////////////////////////
void anglePWM()
{
  pwm2=-PD_pwm - PI_pwm ;           //assign the final value of PWM to motor 
  pwm1=-PD_pwm - PI_pwm ;
  
  if(pwm1>255)             //limit PWM value not greater than 255
  {
    pwm1=255;
  }
  if(pwm1<-255) 
  {
    pwm1=-255;
  }
  if(pwm2>255)
  {
    pwm2=255;
  }
  if(pwm2<-255)
  {
    pwm2=-255;
  }

  if(angle>80 || angle<-80) // the inclined angle of balance car is greater than 45°, motor will stop. 
  {
    pwm1=pwm2=0;
  }

 if(pwm2>=0)// determine the motor’s steering and speed according to the positive and negative of PWM
  {
    digitalWrite(left_L1,LOW);
    digitalWrite(left_L2,HIGH);
    analogWrite(PWM_L,pwm2);
  }
  else
  {
    digitalWrite(left_L1,HIGH);
    digitalWrite(left_L2,LOW);
    analogWrite(PWM_L,-pwm2);
  }

  if(pwm1>=0)
  {
    digitalWrite(right_R1,LOW);
    digitalWrite(right_R2,HIGH);
    analogWrite(PWM_R,pwm1);
  }
  else
  {
    digitalWrite(right_R1,HIGH);
    digitalWrite(right_R2,LOW);
    analogWrite(PWM_R,-pwm1);
  }
}
```

**테스트 결과**

밸런스 카를 잘 설치한 뒤 소스 코드를 업로드하고 전원을 켭니다(스위치 ON).

밸런스 카는 책상 위에서 똑바로 서게 됩니다.

아두이노 IDE를 열고 보드레이트를 9600으로 설정하면, 시리얼 모니터에 밸런스 카의 기울기 값이 표시됩니다.

![](media/de2cefbcbd5c24b84c9472fc5e03cf8b.png)

USB 케이블을 제거하고 바닥에서 똑바로 세워 보세요.

손으로 살짝 밀면 차는 민 방향으로 진행하지만, 기울기 각은 반대 방향으로 형성되어 넘어지지 않고 균형점으로 복귀합니다.

<a id="project-12"></a>
## 프로젝트 12: 조향 루프 제어
[맨 위로](#top)

**설명:**

조향 역시 PD로 조정합니다.

밸런스 로봇은 좌우 모터의 속도 차로 주행 중심선에서의 편차를 줄입니다. 전진하면서 방향을 조금씩 조정해 중심선과의 거리 차이를 점진적으로 없앱니다.

이 과정은 기본적으로 비례(P) 제어 과정이므로, 일반적으로는 단순 비례 제어만으로도 방향 제어가 가능합니다.

하지만 배터리 등 무게물로 관성 모멘트가 커서 조정 중 오버슈트가 발생할 수 있습니다. 억제하지 않으면 과도 조향으로 넘어질 수 있습니다.

앞서 각도·속도 제어 경험에 비추어, 방향 제어의 오버슈트를 줄이기 위해 각도에 대한 미분(D) 제어를 추가하는 것이 필요합니다.

![](media/a690085f6bf92344a8fd907f7d755461.png)



<a id="project-13"></a>
## 프로젝트 13: 블루투스 제어
[맨 위로](#top)

**설명:**

지금까지 로봇을 직립 상태로 세우는 방법과 블루투스 앱으로 제어하는 방법을 배웠습니다.

이제 두 기능을 결합해보겠습니다. 먼저 로봇을 직립시키고, 안드로이드 블루투스로 전후좌우 동작을 제어합니다.

![](media/f040a9f803dbb510ff82ce1fb9454b4e.png)

다만 조립 오차나 MPU6050 오차 등으로, 너무 빨라 쉽게 넘어지거나, 회복이 느리거나, 제대로 움직이지 않는 현상이 있을 수 있습니다. 해결 방법은 프로젝트 12와 아래 2절을 참고하세요.

**주의:**

밸런스 실드에는 블루투스 통신용 슬라이드 스위치가 있습니다. 테스트용 코드를 업로드할 때는 반드시 스위치를 OFF로 두세요. 그렇지 않으면 업로드가 실패합니다.

블루투스 모듈에 연결할 때는 스위치를 ON으로 둡니다.

**소스 코드:**

**참고:**

소스 코드를 테스트하기 전에 필요한 라이브러리를 먼저 설치하세요.

설치 방법은 아래 링크를 참고하세요.

<https://wiki.keyestudio.com/How_to_Install_Arduino_Library>

```c
#include <MsTimer2.h>        // 내부 타이머 2
#include <PinChangeInt.h>    // UNO의 모든 핀을 외부 인터럽트로 사용 가능하게 하는 라이브러리
#include <MPU6050.h>      // MPU6050 라이브러리 
#include <Wire.h>        // IIC 통신 라이브러리 

MPU6050 mpu6050;     // MPU6050 객체 인스턴스
int16_t ax, ay, az, gx, gy, gz;     // 3축 가속도, 3축 자이로 변수 정의

//TB6612 핀
const int right_R1=8;    
const int right_R2=12;
const int PWM_R=10;
const int left_L1=7;
const int left_L2=6;
const int PWM_L=9;

///////////////////////각도 파라미터//////////////////////////////
float angle_X; // 가속도로 X축 기울기 각 계산 변수  
float angle_Y; // 가속도로 Y축 기울기 각 계산 변수
float angle0 = 1; // 실제 측정 각(이상적으로 0도)
float Gyro_x,Gyro_y,Gyro_z;  // 자이로 기반 각속도 
///////////////////////각도 파라미터//////////////////////////////

///////////////////////Kalman_Filter////////////////////////////
float Q_angle = 0.001;  // 자이로 노이즈 공분산
float Q_gyro = 0.003;    // 자이로 드리프트 노이즈 공분산
float R_angle = 0.5;    // 가속도계 공분산
char C_0 = 1;
float dt = 0.005; // 필터 샘플링 시간
float K1 = 0.05; // 칼만 이득을 포함한 함수(최적 추정의 편차 계산)
float K_0,K_1,t_0,t_1;
float angle_err;
float q_bias;    // 자이로 드리프트

float accelz = 0;
float angle;
float angleY_one;
float angle_speed;

float Pdot[4] = { 0, 0, 0, 0};
float P[2][2] = {{ 1, 0 }, { 0, 1 }};
float  PCt_0, PCt_1, E;
//////////////////////칼만 필터/////////////////////////

//////////////////////PID 파라미터///////////////////////////////
double kp = 34, ki = 0, kd = 0.62;                   // 각도 루프 파라미터
double kp_speed = 3.6, ki_speed = 0.080, kd_speed = 0;   // 속도 루프 파라미터
double kp_turn = 24, ki_turn = 0, kd_turn = 0.08;       // 조향 루프 파라미터
double setp0 = 0; // 각도 균형점
int PD_pwm;  // 각도 출력
float pwm1=0,pwm2=0;

////////////////// 속도 카운트 인터럽트 /////////////////////////////
#define PinA_left 5  // 외부 인터럽트
#define PinA_right 4   // 외부 인터럽트 
volatile long count_right = 0;// 홀 인코더가 계산한 펄스 값을 저장(volatile long은 값의 유효성을 보장)
volatile long count_left = 0;
int speedcc = 0;
////////////////////// 펄스 카운트 /////////////////////////
int lz = 0;
int rz = 0;
int rpluse = 0;
int lpluse = 0;
int pulseright,pulseleft;
//////////////////////////////// PI 변수 파라미터 //////////////////////////
float speeds_filterold=0;
float positions=0;
int flag1;
double PI_pwm;
int cc;
int speedout;
float speeds_filter;

////////////////////////////// 조향 PD ///////////////////
int turnmax,turnmin,turnout; 
float Turn_pwm = 0;
int zz=0;
int turncc=0;

//Bluetooth//
int front = 0;// 전진 변수
int back = 0;// 후진 변수
int left = 0;// 좌회전
int right = 0;// 우회전
char val;

void setup() 
{
  // 모터 제어 핀을 출력으로 설정
  pinMode(right_R1,OUTPUT);       
  pinMode(right_R2,OUTPUT);
  pinMode(left_L1,OUTPUT);
  pinMode(left_L2,OUTPUT);
  pinMode(PWM_R,OUTPUT);
  pinMode(PWM_L,OUTPUT);

  // 초기 상태 값 설정
  digitalWrite(right_R1,1);
  digitalWrite(right_R2,0);
  digitalWrite(left_L1,0);
  digitalWrite(left_L2,1);
  analogWrite(PWM_R,0);
  analogWrite(PWM_L,0);

  pinMode(PinA_left, INPUT);  // 속도 엔코더 입력
  pinMode(PinA_right, INPUT);

  // I2C 버스 시작
  Wire.begin();                            // I2C 버스 참가 
  Serial.begin(9600);                       // 시리얼 모니터 보드레이트 9600 설정
  delay(1500);
  mpu6050.initialize();                       // MPU6050 초기화
  delay(2);

  // 5ms 주기 타이머2 인터럽트 설정 (참고: 타이머2 사용 시 3,11번 핀 PWM에 영향)
  MsTimer2::set(5, DSzhongduan);    // 5ms마다 DSzhongduan 실행
  MsTimer2::start();    // 인터럽트 시작
}

void loop() 
{
  Serial.print(angle_speed);
  Serial.print("     ");
  Serial.println(Gyro_x);
  
  //Serial.println(angle);
  //delay(100);
  //Serial.println(PD_pwm);
  //Serial.println(pwm1);
  //Serial.println(pwm2);
  //Serial.print("pulseright = ");
  //Serial.println(pulseright);
  //Serial.print("pulseleft = ");
  //Serial.println(pulseleft);
  //Serial.println(PI_pwm);
  //Serial.println(speeds_filter);
  //Serial.println (positions);
  //Serial.println(Turn_pwm);
  //Serial.println(Gyro_z);
  //Serial.println(Turn_pwm);
  

  if(Serial.available())
  {
    val = Serial.read();      // 시리얼에서 읽은 값을 val에 저장
    //Serial.println(val);
    switch(val)             // switch 문
    {
      case 'F': front=250; break;       // 'F' 수신: 전진
      case 'B': back=-250; break;       // 후진
      case 'L': left=1; break;          // 좌회전
      case 'R': right=1; break;         // 우회전
      case 'S': front=0,back=0,left=0,right=0;break;    // 정지
      case 'D': Serial.print(angle);break;    // 'D' 수신: 각도 값을 APP으로 전송
    }
  }
  
  // 바퀴 속도 계산용 외부 인터럽트
  attachPinChangeInterrupt(PinA_left, Code_left, CHANGE);          // PinA_left 레벨 변화 시 Code_left 실행
  attachPinChangeInterrupt(PinA_right, Code_right, CHANGE);        // PinA_right 레벨 변화 시 Code_right 실행
}

///////////////////// 홀 카운트 /////////////////////////
// 왼쪽 속도 엔코더 카운트
void Code_left() 
{
  count_left ++;
} 
// 오른쪽 속도 엔코더 카운트
void Code_right() 
{
  count_right ++;
} 
//////////////////// 펄스 카운트 ///////////////////////
void countpluse()
{
  lz = count_left;     // 엔코더가 센 값을 lz에 대입
  rz = count_right;

  count_left = 0;     // 카운터 초기화
  count_right = 0;

  lpluse = lz;
  rpluse = rz;

  if ((pwm1 < 0) && (pwm2 < 0))                     // 이동 방향 판별; 후진이면(모터 전압 음수) 펄스는 음수
  {
    rpluse = -rpluse;
    lpluse = -lpluse;
  }
  else if ((pwm1 > 0) && (pwm2 > 0))                 // 전진이면(모터 전압 양수) 펄스는 양수
  {
    rpluse = rpluse;
    lpluse = lpluse;
  }
  else if ((pwm1 < 0) && (pwm2 > 0))                 // 좌회전: 오른쪽 펄스 양수, 왼쪽 펄스 음수
  {
    rpluse = rpluse;
    lpluse = -lpluse;
  }
  else if ((pwm1 > 0) && (pwm2 < 0))               // 우회전: 오른쪽 펄스 음수, 왼쪽 펄스 양수
  {
    rpluse = -rpluse;
    lpluse = lpluse;
  }

  // 5ms마다 인터럽트 진입; 펄스 누적
  pulseright += rpluse;
  pulseleft += lpluse;
}

///////////////////////////////// 인터럽트 ////////////////////////////
void DSzhongduan()
{
  sei();  // 전역 인터럽트 허용
  countpluse();        // 펄스 카운트 처리
  mpu6050.getMotion6(&ax, &ay, &az, &gx, &gy, &gz);     // IIC로 MPU6050 6축 데이터 읽기
  angle_calculate(ax, ay, az, gx, gy, gz, dt, Q_angle, Q_gyro, R_angle, C_0, K1);      // 각도 계산 및 칼만 필터링
  PD();         // 각도 루프 PD 제어 
  anglePWM();

  cc++;
  if(cc>=8)     // 5*8=40 → 40ms마다 속도 PI 실행
  {
    speedpiout();   
    cc=0;  // 초기화
  }
  turncc++;         
  if(turncc>4)       // 20ms마다 조향 PI 실행
  {
    turnspin();
    turncc=0;     // 초기화
  }
}
///////////////////////////////////////////////////////////

///////////////////////////// 기울기 각 계산 ///////////////////////
void angle_calculate(int16_t ax,int16_t ay,int16_t az,int16_t gx,int16_t gy,int16_t gz,float dt,float Q_angle,float Q_gyro,float R_angle,float C_0,float K1)
{
  float Angle = -atan2(ay , az) * (180/ PI);           // 회전 각도 계산(부호는 방향 보정)
  Gyro_x = -gx / 131;              // 자이로 기반 X축 각속도(부호로 방향 보정)
  Kalman_Filter(Angle, Gyro_x);            // 칼만 필터
  // Z축 각속도
  Gyro_z = -gz / 131;                      // Z축 속도 
  //accelz = az / 16.4;

  float angleAx = -atan2(ax, az) * (180 / PI); // X축 각도 계산 
  Gyro_y = -gy / 131.00; // Y축 각속도 
  Yiorderfilter(angleAx, Gyro_y); // 1차 필터링
}
////////////////////////////////////////////////////////////////

///////////////////////////////KalmanFilter/////////////////////
void Kalman_Filter(double angle_m, double gyro_m)
{
  angle += (gyro_m - q_bias) * dt;          //prior estimate
  angle_err = angle_m - angle;
  
  Pdot[0] = Q_angle - P[0][1] - P[1][0];    // 사전 추정 오차 공분산의 미분 
  Pdot[1] = - P[1][1];
  Pdot[2] = - P[1][1];
  Pdot[3] = Q_gyro;
  
  P[0][0] += Pdot[0] * dt;    // 사전 추정 오차 공분산 미분의 적분
  P[0][1] += Pdot[1] * dt;
  P[1][0] += Pdot[2] * dt;
  P[1][1] += Pdot[3] * dt;
  
  // 행렬 곱 중간 변수
  PCt_0 = C_0 * P[0][0];
  PCt_1 = C_0 * P[1][0];
  // 분모
  E = R_angle + C_0 * PCt_0;
  // 이득 값
  K_0 = PCt_0 / E;
  K_1 = PCt_1 / E;
  
  t_0 = PCt_0;  // 행렬 곱 중간 변수 
  t_1 = C_0 * P[0][1];
  
  P[0][0] -= K_0 * t_0;    // 사후 추정 오차 공분산 
  P[0][1] -= K_0 * t_1;
  P[1][0] -= K_1 * t_0;
  P[1][1] -= K_1 * t_1;
  
  q_bias += K_1 * angle_err;    // 사후 추정
  angle_speed = gyro_m - q_bias;   // 출력 값의 미분 → 최적 각속도
  angle += K_0 * angle_err; // 사후 추정 → 최적 각도
}

///////////////////// 1차 필터링 //////////////////
void Yiorderfilter(float angle_m, float gyro_m)
{
  angleY_one = K1 * angle_m + (1 - K1) * (angleY_one + gyro_m * dt);
}

//////////////////angle PD////////////////////
void PD()
{
  PD_pwm = kp * (angle + angle0) + kd * angle_speed; // PD 각도 루프 제어 
}

//////////////////speed PI////////////////////
void speedpiout()
{
  float speeds = (pulseleft + pulseright) * 1.0;      // 속도 펄스 값  
  pulseright = pulseleft = 0;      // 초기화 
  speeds_filterold *= 0.7;         // 1차 보완 필터링
  speeds_filter = speeds_filterold + speeds * 0.3;
  speeds_filterold = speeds_filter;
  positions += speeds_filter;
  positions += front;             // 전진 제어 융합
  positions += back;              // 후진 제어 융합
  positions = constrain(positions, -3550,3550);    // 적분 포화 방지
  PI_pwm = ki_speed * (setp0 - positions) + kp_speed * (setp0 - speeds_filter);      // 속도 루프 PI 제어
}
//////////////////speed PI////////////////////

///////////////////////////steering/////////////////////////////////
void turnspin()
{
  int flag = 0;      //
  float turnspeed = 0;
  float rotationratio = 0;
  
  if (left == 1 || right == 1)
  {
    if (flag == 0)                             //judge the speed before turning; increase the car’s flexibility.
    {
      turnspeed = ( pulseright + pulseleft);                      //current speed of car; pulse expression
      flag=1;
    }
    if (turnspeed < 0)                                 //Absolute value of the car's current speed
    {
      turnspeed = -turnspeed;
    }
    if(left==1||right==1)         //if press left key or right key
    {
     turnmax=3;          //maximum value of turning
     turnmin=-3;         // minimum value of turning
    }
    rotationratio = 5 / turnspeed;          //set the value by speed
    if (rotationratio < 0.5)
    {
      rotationratio = 0.5;
    }
     
    if (rotationratio > 5)
    {
      rotationratio = 5;
    }
  }
  else
  {
    rotationratio = 0.5;
    flag = 0;
    turnspeed = 0;
  }
  if (left ==1)//plus by direction parameter
  {
    turnout += rotationratio;
  }
  else if (right == 1 )//plus by direction parameter
  {
    turnout -= rotationratio;
  }
  else turnout = 0;
  if (turnout > turnmax)   turnout = turnmax;//the max value setting of amplitude
  if (turnout < turnmin)   turnout = turnmin;//the min value setting of amplitude 

  Turn_pwm = -turnout * kp_turn - Gyro_z * kd_turn;//The rotation PD algorithm controls the fusion speed and Z axis rotation positioning
}
/////////////////////////// 조향 //////////////////////////////////

////////////////////////////PWM end value/////////////////////////////
void anglePWM()
{
  pwm2=-PD_pwm - PI_pwm + Turn_pwm;           //assign the end value of PWM to motor
  pwm1=-PD_pwm - PI_pwm - Turn_pwm;
  
  if(pwm1>255)             //limit the PWM value not more than 255
  {
    pwm1=255;
  }
  if(pwm1<-255) 
  {
    pwm1=-255;
  }
  if(pwm2>255)
  {
    pwm2=255;
  }
  if(pwm2<-255)
  {
    pwm2=-255;
  }

  if(angle>80 || angle<-80)      //if tilt angle is greater than 45° , motor will stop.
  {
    pwm1=pwm2=0;
  }

 if(pwm2>=0)         //motor’s turning and speed are determined by the positive or negative of PWM
  {
    digitalWrite(left_L1,LOW);
    digitalWrite(left_L2,HIGH);
    analogWrite(PWM_L,pwm2);
  }
  else
  {
    digitalWrite(left_L1,HIGH);
    digitalWrite(left_L2,LOW);
    analogWrite(PWM_L,-pwm2);
  }

  if(pwm1>=0)
  {
    digitalWrite(right_R1,LOW);
    digitalWrite(right_R2,HIGH);
    analogWrite(PWM_R,pwm1);
  }
  else
  {
    digitalWrite(right_R1,HIGH);
    digitalWrite(right_R2,LOW);
    analogWrite(PWM_R,-pwm1);
  }
}
```

**사용 방법:**

① 밸런스 로봇을 조립하고 테스트 코드를 업로드합니다.

② USB 케이블을 분리한 뒤, 실드의 전원 스위치를 ON으로 켭니다.

③ 밸런스 실드에 있는 블루투스 스위치를 ON으로 전환합니다. 블루투스 모듈 연결 방법은 프로젝트 6을 참고하세요.

④ 앱을 열어 블루투스에 연결합니다. 연결이 되면 로봇을 바닥에 세워 직립시키고, 버튼 키를 눌러 전/후/좌/우 아이콘으로 이동을 제어합니다. ![image-20230510093100134](media/image-20230510093100134.png)

![](media/c9025f5cc50b1c07224b747d3b8a75c8.png)

⑤ ![image-20230510093127734](media/image-20230510093127734.png) 키를 누르면 휴대폰의 중력 센서를 이용해 로봇 이동을 제어할 수도 있습니다.

**블루투스 앱으로 균형 각과 PID 조정**

**설명:**

앞선 프로젝트까지 로봇을 직립시키고 이동을 제어할 수 있었습니다.

하지만 조립 오차나 MPU6050 오차로 인해 기계적 균형 각이 수평면에 대해 완전한 수직이 아닐 수 있습니다.

그 결과 블루투스로 전/후 이동을 줄 때 기울기 각이 작아 바퀴가 거의 돌지 않거나 느리게 움직이기도 하고,

반대로 기울기 각이 너무 커 바퀴 속도가 과도하게 빨라 일정 거리 가속 후 넘어질 수도 있습니다.

![](media/85a352579f8f2a9fb2ada98cbab3804c.png)

이러한 오차를 줄이기 위해, 모바일 앱으로 기계적 균형 각과 PID 주요 파라미터를 조정합니다.

**블루투스 앱 사용 방법**

① 앞에서와 같이 코드를 업로드해 밸런스 카를 제어할 수 있게 합니다.

② 기울기 각을 설정합니다. 전/후 주행 시 속도가 같지 않아 편차가 생길 수 있습니다. ![image-20230510093304290](media/image-20230510093304290.png) 키를 눌러 기울기 각 값을 얻습니다.

![](media/fa3bb54a9c70e43446817767b86b4d45.png)

음수가 나온 경우 변경 바 ![](media/image-20230510093341512.png)에 양수를 입력해 합이 0에 가깝도록 맞춥니다.

그 다음 ![](media/image-20230510093405779.png) 키를 눌러 주행시키며 상태를 관찰합니다.

③ 블루투스 앱의 PID ![image-20230510093426650](media/image-20230510093426650.png) 버튼을 눌러 PID 파라미터 설정 화면으로 이동한 뒤, 키들을 눌러 파라미터를 조정해 안정적인 상태를 찾습니다.

![](media/ae53906b471507cc4721fb6a913be783.png)

설정을 마친 후 ![image-20230510093449645](media/image-20230510093449645.png) 키로 제어 화면으로 돌아갑니다.

**소스 코드:**

**참고:**

소스 코드를 테스트하기 전에 필요한 라이브러리를 먼저 설치하세요.

설치 방법은 아래 링크를 참고하세요.

<https://wiki.keyestudio.com/How_to_Install_Arduino_Library>

```c
#include <MsTimer2.h>        // 내부 타이머 2
#include <PinChangeInt.h>    // UNO의 모든 핀을 외부 인터럽트로 사용 가능
#include <MPU6050.h>      // MPU6050 라이브러리
#include <Wire.h>        // IIC 통신 라이브러리

MPU6050 mpu6050;     //Instantiate an MPU6050 object; name mpu6050
int16_t ax, ay, az, gx, gy, gz;     //Define three-axis acceleration, three-axis gyroscope variables

//TB6612 pins
const int right_R1=8;    
const int right_R2=12;
const int PWM_R=10;
const int left_L1=7;
const int left_L2=6;
const int PWM_L=9;

///////////////////////angle parameters//////////////////////////////
float angle_X; //calculate the inclined angle variable of X-axis by accelerometer
float angle_Y; //calculate the inclined angle variable of Y-axis by accelerometer
int angle0 = 0; //Actual measured angle (ideally 0 degrees) 
float Gyro_x,Gyro_y,Gyro_z;  //Angular angular velocity for gyroscope calculation 
///////////////////////angle parameters//////////////////////////////

///////////////////////Kalman_Filter////////////////////////////
float Q_angle = 0.001;  //Covariance of gyroscope noise
float Q_gyro = 0.003;    //Covariance of gyroscope drift noise
float R_angle = 0.5;    //Covariance of accelerometer
char C_0 = 1;
float dt = 0.005; //The value of dt is the filter sampling time
float K1 = 0.05; // a function containing the Kalman gain; used to calculate the deviation of the optimal estimate
float K_0,K_1,t_0,t_1;
float angle_err;
float q_bias;    //gyroscope drift

float accelz = 0;
float angle;
float angleY_one;
float angle_speed;

float Pdot[4] = { 0, 0, 0, 0};
float P[2][2] = {{ 1, 0 }, { 0, 1 }};
float  PCt_0, PCt_1, E;
//////////////////////Kalman_Filter/////////////////////////

//////////////////////PID parameters///////////////////////////////
double kp = 34.00, ki = 0, kd = 0.62;                   //angle loop parameter
double kp_speed = 3.60, ki_speed = 0.08, kd_speed = 0;   // speed loop parameter
double kp_turn = 24.00, ki_turn = 0, kd_turn = 0.08;                 // steering loop parameter
double setp0 = 0; //angle balance point
int PD_pwm;  //angle output
float pwm1=0,pwm2=0;

//////////////////interrupt speed count/////////////////////////////
#define PinA_left 5  //external interrupt
#define PinA_right 4   //external interrupt
volatile long count_right = 0;//Used to calculate the pulse value calculated by the Hall encoder (the volatile long type is to ensure that the value is valid）
volatile long count_left = 0;
int speedcc = 0;
//////////////////////pulse count/////////////////////////
int lz = 0;
int rz = 0;
int rpluse = 0;
int lpluse = 0;
int pulseright,pulseleft;
////////////////////////////////PI variable parameter//////////////////////////
float speeds_filterold=0;
float positions=0;
int flag1;
double PI_pwm;
int cc;
int speedout;
float speeds_filter;

//////////////////////////////steering PD///////////////////
int turnmax,turnmin,turnout; 
float Turn_pwm = 0;
int zz=0;
int turncc=0;

//Bluetooth//
int front = 0;//backward variable
int back = 0;//forward variable
int left = 0;//turn left
int right = 0;//turn right
char val;

int TT;

void setup() 
{
  //set the control pins of motor to OUTPUT
  pinMode(right_R1,OUTPUT);       
  pinMode(right_R2,OUTPUT);
  pinMode(left_L1,OUTPUT);
  pinMode(left_L2,OUTPUT);
  pinMode(PWM_R,OUTPUT);
  pinMode(PWM_L,OUTPUT);

  //assign the initial value
  digitalWrite(right_R1,1);
  digitalWrite(right_R2,0);
  digitalWrite(left_L1,0);
  digitalWrite(left_L2,1);
  analogWrite(PWM_R,0);
  analogWrite(PWM_L,0);

  pinMode(PinA_left, INPUT);  //speed encoder input
  pinMode(PinA_right, INPUT);

  // join I2C bus
  Wire.begin();                            //join I2C bus sequence
  Serial.begin(9600);                       //open the serial monitor, set the baud rate to 9600
  delay(1500);
  mpu6050.initialize();                       //initialize MPU6050
  delay(2);

  //5ms; use timer2 to set timer interruption (note：using timer2 will affect the PWM output of pin3 pin11)
  MsTimer2::set(5, DSzhongduan);    //5ms;  execute the function DSzhongduan once
  MsTimer2::start();    //start interrupt
}

void loop() 
{
  //Serial.println(angle);
  //delay(100);
  //Serial.println(PD_pwm);
  //Serial.println(pwm1);
  //Serial.println(pwm2);
  //Serial.print("pulseright = ");
  //Serial.println(pulseright);
  //Serial.print("pulseleft = ");
  //Serial.println(pulseleft);
  //Serial.println(PI_pwm);
  //Serial.println(speeds_filter);
  //Serial.println (positions);
  //Serial.println(Turn_pwm);
  //Serial.println(Gyro_z);
  //Serial.println(Turn_pwm);
  

  if(Serial.available())
  {
    val = Serial.read();      //assign the value read from serial port to val
    //Serial.println(val);
    switch(val)             //switch statement
    {
      case 'F': front=250; break;       //if vale equals F，front=250，go front
      case 'B': back=-250; break;       //go back
      case 'L': left=1; break;    //turn left
      case 'R': right=1; break;                         //turn right
      case 'S': front=0,back=0,left=0,right=0;break;    //stop
      case 'Q': Serial.print(angle);break;    //receiving‘D’，send the value of variable angle to APP
      case 'P': kp=kp+0.5,Serial.print(kp);break;
      case 'O': kp=kp-0.5,Serial.print(kp);break;
      case 'I': kd=kd+0.02,Serial.print(kd);break;
      case 'U': kd=kd-0.02,Serial.print(kd);break;
      case 'Y': kp_speed=kp_speed+0.05,Serial.print(kp_speed);break;
      case 'T': kp_speed=kp_speed-0.05,Serial.print(kp_speed);break;
      case 'G': ki_speed=ki_speed+0.01,Serial.print(ki_speed);break;
      case 'H': ki_speed=ki_speed-0.01,Serial.print(ki_speed);break;
      case 'J': kp_turn=kp_turn+0.4,Serial.print(kp_turn);break;
      case 'K': kp_turn=kp_turn-0.4,Serial.print(kp_turn);break;
      case 'N': kd_turn=kd_turn+0.01,Serial.print(kd_turn);break;
      case 'M': kd_turn=kd_turn-0.01,Serial.print(kd_turn);break;
    }
    if(val=='F'||val=='B'||val=='L'||val=='R'||val=='S'||val=='Q'||val=='P'||val=='O'||val=='I'||val=='U'||val=='Y'||val=='T'||val=='G'||val=='H'||val=='J'||val=='K'||val=='N'||val=='M')
    {
      TT = angle0;
    }
    else
    {
      TT = val;
      angle0=TT;
    }
    //Serial.println(angle0);
    
  }
  
  //external interrupt; used to calculate the wheel speed
  attachPinChangeInterrupt(PinA_left, Code_left, CHANGE);          //PinA_left Level change triggers external interrupt; execute subfunction Code_left
  attachPinChangeInterrupt(PinA_right, Code_right, CHANGE);       //PinA_right Level change triggers external interrupt; execute Code_right
}

/////////////////////Hall count/////////////////////////
//left speed encoder count
void Code_left() 
{
  count_left ++;
} 
//right speed encoder count
void Code_right() 
{
  count_right ++;
} 
////////////////////pulse count///////////////////////
void countpluse()
{
  lz = count_left;     //assign the value counted by encoder to lz
  rz = count_right;

  count_left = 0;     //Clear the count quantity
  count_right = 0;

  lpluse = lz;
  rpluse = rz;

  if ((pwm1 < 0) && (pwm2 < 0))                     //judge the car’s moving direction; if backward (PWM /motor voltage is negative), pulse is a negative number.
  {
    rpluse = -rpluse;
    lpluse = -lpluse;
  }
  else if ((pwm1 > 0) && (pwm2 > 0))                 //if backward (PWM /motor voltage is positive), pulse is a positive number.
  {
    rpluse = rpluse;
    lpluse = lpluse;
  }
  else if ((pwm1 < 0) && (pwm2 > 0))                 //judge the car’s moving direction; if turn left, the right pulse is positive; left pulse is negative. 
  {
    rpluse = rpluse;
    lpluse = -lpluse;
  }
  else if ((pwm1 > 0) && (pwm2 < 0))               //judge the car’s moving direction; if turn right, the right pulse is negative ; left pulse is positive. 
  {
    rpluse = -rpluse;
    lpluse = lpluse;
  }

  //entering interrupt per，pulse plus
  pulseright += rpluse;
  pulseleft += lpluse;
}

/////////////////////////////////interrupt////////////////////////////
void DSzhongduan()
{
  sei();  //allow overall interrupt
  countpluse();        //pulse plus subfunction
  mpu6050.getMotion6(&ax, &ay, &az, &gx, &gy, &gz);     //IIC to get MPU6050 six-axis data ax ay az gx gy gz
  angle_calculate(ax, ay, az, gx, gy, gz, dt, Q_angle, Q_gyro, R_angle, C_0, K1);      //get angle and Kalman filtering
  PD();         // PD control of angle loop
  anglePWM();

  cc++;
  if(cc>=8)     //5*8=40，that is, execute the PI calculation of speed once per 40ms
  {
    speedpiout();   
    cc=0;  //Clear
  }
  turncc++;         
  if(turncc>4)       //20ms, that is, execute the PD calculation of steering once per 40ms
  {
    turnspin();
    turncc=0;     //Clear
  }
}
///////////////////////////////////////////////////////////

/////////////////////////////tilt angle calculation ///////////////////////
void angle_calculate(int16_t ax,int16_t ay,int16_t az,int16_t gx,int16_t gy,int16_t gz,float dt,float Q_angle,float Q_gyro,float R_angle,float C_0,float K1)
{
  float Angle = -atan2(ay , az) * (180/ PI);           //Radial rotation angle calculation formula ; negative sign is direction processing
  Gyro_x = -gx / 131;              //The X-axis angular velocity calculated by the gyroscope ; the negative sign is the direction processing
  Kalman_Filter(Angle, Gyro_x);            //Kalman Filter
  //Rotation angle Z-axis parameter 
  Gyro_z = -gz / 131;                      //angle speed of Z-axis
  //accelz = az / 16.4;

  float angleAx = -atan2(ax, az) * (180 / PI); //calculate the inclined angle of X-axis
  Gyro_y = -gy / 131.00; //angle speed of Y-axis 
  Yiorderfilter(angleAx, Gyro_y); //first-order filtering
}
////////////////////////////////////////////////////////////////

///////////////////////////////KalmanFilter/////////////////////
void Kalman_Filter(double angle_m, double gyro_m)
{
  angle += (gyro_m - q_bias) * dt;          //prior estimate
  angle_err = angle_m - angle;
  
  Pdot[0] = Q_angle - P[0][1] - P[1][0];    //The differential of the covariance of the prior estimate error
  Pdot[1] = - P[1][1];
  Pdot[2] = - P[1][1];
  Pdot[3] = Q_gyro;
  
  P[0][0] += Pdot[0] * dt;    //A priori estimation error covariance differential integral
  P[0][1] += Pdot[1] * dt;
  P[1][0] += Pdot[2] * dt;
  P[1][1] += Pdot[3] * dt;
  
  //Intermediate variables in matrix multiplication
  PCt_0 = C_0 * P[0][0];
  PCt_1 = C_0 * P[1][0];
  //denominator
  E = R_angle + C_0 * PCt_0;
  //gain value
  K_0 = PCt_0 / E;
  K_1 = PCt_1 / E;
  
  t_0 = PCt_0;  //Intermediate variables in matrix multiplication
  t_1 = C_0 * P[0][1];
  
  P[0][0] -= K_0 * t_0;    //Posterior estimation error covariance 
  P[0][1] -= K_0 * t_1;
  P[1][0] -= K_1 * t_0;
  P[1][1] -= K_1 * t_1;
  
  q_bias += K_1 * angle_err;    //Posterior estimate
  angle_speed = gyro_m - q_bias;   //The differential of the output value; get the optimal angular velocity
  angle += K_0 * angle_err; ////Posterior estimation; get the optimal angle
}

/////////////////////first-order filtering/////////////////
void Yiorderfilter(float angle_m, float gyro_m)
{
  angleY_one = K1 * angle_m + (1 - K1) * (angleY_one + gyro_m * dt);
}

//////////////////angle PD////////////////////
void PD()
{
  PD_pwm = kp * (angle + angle0) + kd * angle_speed; //PD angle loop control
}

//////////////////speed PI////////////////////
void speedpiout()
{
  float speeds = (pulseleft + pulseright) * 1.0;      //speed; pulse value
  pulseright = pulseleft = 0;      //Clear
  speeds_filterold *= 0.7;         //first-order complementary filtering
  speeds_filter = speeds_filterold + speeds * 0.3;
  speeds_filterold = speeds_filter;
  positions += speeds_filter;
  positions += front;             //Forward control fusion
  positions += back;              //Backward control fusion
  positions = constrain(positions, -3550,3550);    //Anti-integral saturation
  PI_pwm = ki_speed * (setp0 - positions) + kp_speed * (setp0 - speeds_filter);      //speed loop control PI
}
//////////////////speed PI////////////////////

///////////////////////////turning/////////////////////////////////
void turnspin()
{
  int flag = 0;      // 상태 플래그
  float turnspeed = 0;
  float rotationratio = 0;
  
  if (left == 1 || right == 1)
  {
    if (flag == 0)                             // 회전 전 현재 속도 평가(유연성 증가)   
    {
      turnspeed = ( pulseright + pulseleft);                      // 현재 속도(펄스)
      flag=1;
    }
    if (turnspeed < 0)                                 // 현재 속도의 절대값
    {
      turnspeed = -turnspeed;
    }
    if(left==1||right==1)         // 좌/우 키가 눌린 경우
    {
     turnmax=5;          // 조향 최대값
     turnmin=-5;         // 조향 최소값
    }
    rotationratio = 5 / turnspeed;          // 차량 속도에 따른 비율
    if (rotationratio < 0.5)
    {
      rotationratio = 0.5;
    }
     
    if (rotationratio > 5)
    {
      rotationratio = 5;
    }
  }
  else
  {
    rotationratio = 0.5;
    flag = 0;
    turnspeed = 0;
  }
  if (left ==1)// 방향 파라미터에 따른 증가
  {
    turnout += rotationratio;
  }
  else if (right == 1 )// 방향 파라미터에 따른 증가
  {
    turnout -= rotationratio;
  }
  else turnout = 0;
  if (turnout > turnmax)   turnout = turnmax;// 진폭 최대 제한
  if (turnout < turnmin)   turnout = turnmin;// 진폭 최소 제한 

  Turn_pwm = -turnout * kp_turn - Gyro_z * kd_turn;// 회전 PD: 융합 속도 + Z축 회전 위치 제어
}
/////////////////////////// 조향 //////////////////////////////////

//////////////////////////// PWM 최종 값 /////////////////////////////
void anglePWM()
{
  pwm2=-PD_pwm - PI_pwm + Turn_pwm;           // PWM 최종값을 모터에 할당
  pwm1=-PD_pwm - PI_pwm - Turn_pwm;
  
  if(pwm1>255)             // PWM 상한 255 제한
  {
    pwm1=255;
  }
  if(pwm1<-255) 
  {
    pwm1=-255;
  }
  if(pwm2>255)
  {
    pwm2=255;
  }
  if(pwm2<-255)
  {
    pwm2=-255;
  }

  if(angle>80 || angle<-80)      // 기울기 각이 45°를 넘으면 모터 정지
  {
    pwm1=pwm2=0;
  }

 if(pwm2>=0)         // PWM 부호로 모터 회전 방향/속도 결정
  {
    digitalWrite(left_L1,LOW);
    digitalWrite(left_L2,HIGH);
    analogWrite(PWM_L,pwm2);
  }
  else
  {
    digitalWrite(left_L1,HIGH);
    digitalWrite(left_L2,LOW);
    analogWrite(PWM_L,-pwm2);
  }

  if(pwm1>=0)
  {
    digitalWrite(right_R1,LOW);
    digitalWrite(right_R2,HIGH);
    analogWrite(PWM_R,pwm1);
  }
  else
  {
    digitalWrite(right_R1,HIGH);
    digitalWrite(right_R2,LOW);
    analogWrite(PWM_R,-pwm1);
  }
}
```

![](media/4431f0b71eb2d293ebcce752dfa32515.jpeg)



<a id="project-14"></a>
## 프로젝트 14: 균형 각도 조정 및 블루투스 제어
[맨 위로](#top)

**설명:**

위 프로젝트에서는 먼저 블루투스를 연결한 다음 블루투스 APP에서 차의 균형 각도를 조정합니다.

이제 먼저 손으로 차의 균형 각도를 조정합니다; 그런 다음 안드로이드 블루투스를 연결하여 블루투스 APP을 통해 차의 이동을 제어합니다.

**주의사항:**

①　균형 실드에는 블루투스 통신을 위한 슬라이드 스위치가 있습니다. 테스트 코드를 업로드할 때 스위치를 OFF로 전환하세요, 그렇지 않으면 업로드가 실패합니다.

②　블루투스 모듈에 연결할 때 스위치를 ON으로 전환하세요. 

③　이 프로젝트의 소스 코드를 사용하여 시작할 때마다 한 번만 조정할 수 있습니다; 먼저 각도를 조정하세요, 그렇지 않으면 차가 균형을 유지할 수 없습니다. 

**소스 코드:**

**참고:**

소스 코드를 테스트하기 전에 해당 라이브러리를 추가해야 합니다.

아래 링크의 방법을 참조하세요:

<https://wiki.keyestudio.com/How_to_Install_Arduino_Library>

```c
#include <MsTimer2.h>        //내부 타이머 2
#include <PinChangeInt.h>    //이 라이브러리 파일은 UNO 보드의 모든 핀을 외부 인터럽트로 만들 수 있습니다. 3축 가속도, 3축 자이로스코프 변수를 정의합니다
#include <MPU6050.h>      //MPU6050 라이브러리
#include <Wire.h>        //IIC 통신 라이브러리

MPU6050 mpu6050;     //MPU6050 객체를 인스턴스화합니다; 이름 mpu6050
int16_t ax, ay, az, gx, gy, gz;     //3축 가속도, 3축 자이로스코프 변수를 정의합니다

//TB6612 핀 정의
const int right_R1=8;    
const int right_R2=12;
const int PWM_R=10;
const int left_L1=7;
const int left_L2=6;
const int PWM_L=9;

const int buz = 11;
const int btn = 13;

///////////////////////각도 파라미터//////////////////////////////
float angle_X; //가속도계로 X축의 기울어진 각도 변수를 계산합니다
float angle_Y; //가속도계로 Y축의 기울어진 각도 변수를 계산합니다
float angle0 = 0; //기계적 균형 각도 (이상적으로 0도)
float Gyro_x,Gyro_y,Gyro_z;  //자이로스코프 계산으로 각도 각속도
///////////////////////각도 파라미터//////////////////////////////

///////////////////////칼만 필터////////////////////////////
float Q_angle = 0.001;  //자이로스코프 노이즈의 공분산
float Q_gyro = 0.003;    //자이로스코프 드리프트 노이즈의 공분산
float R_angle = 0.5;    //가속도계의 공분산
char C_0 = 1;
float dt = 0.005; //dt 값은 필터 샘플링 시간입니다
float K1 = 0.05; //칼만 게인을 포함하는 함수; 최적 추정의 편차를 계산하는 데 사용됩니다
float K_0,K_1,t_0,t_1;
float angle_err;
float q_bias;    //자이로스코프 드리프트

float accelz = 0;
float angle;
float angleY_one;
float angle_speed;

float Pdot[4] = { 0, 0, 0, 0};
float P[2][2] = {{ 1, 0 }, { 0, 1 }};
float  PCt_0, PCt_1, E;
//////////////////////칼만 필터/////////////////////////

//////////////////////PID 파라미터///////////////////////////////
double kp = 34, ki = 0, kd = 0.62;                   //각도 루프 파라미터
double kp_speed = 3.56, ki_speed = 0.072, kd_speed = 0;   //속도 루프 파라미터
double kp_turn = 24, ki_turn = 0, kd_turn = 0.08;                 //조향 루프 파라미터
double setp0 = 0; //각도 균형점
int PD_pwm;  //각도 출력
float pwm1=0,pwm2=0;

//////////////////인터럽트 속도 카운트/////////////////////////////
#define PinA_left 5  //외부 인터럽트
#define PinA_right 4   //외부 인터럽트
volatile long count_right = 0;//홀 인코더로 계산된 펄스 값을 계산하는 데 사용됩니다 (volatile long 타입은 값이 유효하도록 보장합니다)
volatile long count_left = 0;
int speedcc = 0;
//////////////////////펄스 카운트/////////////////////////
int lz = 0;
int rz = 0;
int rpluse = 0;
int lpluse = 0;
int pulseright,pulseleft;
////////////////////////////////PI 변수 파라미터//////////////////////////
float speeds_filterold=0;
float positions=0;
int flag1;
double PI_pwm;
int cc;
int speedout;
float speeds_filter;

//////////////////////////////조향 PD///////////////////
int turnmax,turnmin,turnout; 
float Turn_pwm = 0;
int zz=0;
int turncc=0;

//블루투스//
int front = 0;//전진 변수
int back = 0;//후진
int left = 0;//좌회전
int right = 0;//우회전
char val;

int i,button;

void setup() 
{
  //모터 제어 핀을 OUTPUT으로 설정
  pinMode(right_R1,OUTPUT);       
  pinMode(right_R2,OUTPUT);
  pinMode(left_L1,OUTPUT);
  pinMode(left_L2,OUTPUT);
  pinMode(PWM_R,OUTPUT);
  pinMode(PWM_L,OUTPUT);

  //초기 상태 값을 할당
  digitalWrite(right_R1,1);
  digitalWrite(right_R2,0);
  digitalWrite(left_L1,0);
  digitalWrite(left_L2,1);
  analogWrite(PWM_R,0);
  analogWrite(PWM_L,0);

  pinMode(PinA_left, INPUT);  //속도 인코더 입력
  pinMode(PinA_right, INPUT);

  pinMode(btn,INPUT);
  pinMode(buz,OUTPUT);

  // I2C 버스에 조인
  Wire.begin();                            //I2C 버스 시퀀스에 조인
  Serial.begin(9600);                       //시리얼 모니터를 열고 전송 속도를 9600으로 설정
  delay(1500);
  mpu6050.initialize();                       //MPU6050 초기화
  delay(2);

  //5ms; timer2를 사용하여 타이머 인터럽트를 설정 (참고: timer2를 사용하면 pin3 pin11의 PWM 출력에 영향을 줄 수 있음)
  MsTimer2::set(5, DSzhongduan);    //5ms; DSzhongduan 함수를 한 번 실행
  MsTimer2::start();    //인터럽트 시작
}

 //부저
void buzzer()
{
    for(int i=0;i<50;i++)
    {
    digitalWrite(buz,HIGH);
    delay(1);
    digitalWrite(buz,LOW);
    delay(1);
    }
    delay(50);
    for(int i=0;i<50;i++)
    {
    digitalWrite(buz,HIGH);
    delay(1);
    digitalWrite(buz,LOW);
    delay(1);
    }
}

void loop() 
{
  //Serial.println(angle0);
  //Serial.print("angle= ");
  //Serial.println(angle);
  //delay(1);
  //Serial.println(PD_pwm);
  //Serial.println(pwm1);
  //Serial.println(pwm2);
  //Serial.print("pulseright = ");
  //Serial.println(pulseright);
  //Serial.print("pulseleft = ");
  //Serial.println(pulseleft);
  //Serial.println(PI_pwm);
  //Serial.println(speeds_filter);
  //Serial.println (positions);
  //Serial.println(Turn_pwm);
  //Serial.println(Gyro_z);
  //Serial.println(Turn_pwm);

  while(i<1)
  {
    button = digitalRead(btn);
    if(button == 0)
    {
      angle0=-angle;
      //Serial.println(angle0);
      buzzer();
      i++;
    }
  }
  if(Serial.available())
  {
    val = Serial.read();      //시리얼 포트에서 읽은 값을 val에 할당
    //Serial.println(val);
    switch(val)             //스위치 문
    {
      case 'F': front=250; break;       //val이 F와 같으면，front=250，차가 전진
      case 'B': back=-250; break;       //후진
      case 'L': left=1; break;    //좌회전
      case 'R': right=1; break;                         //우회전
      case 'S': front=0,back=0,left=0,right=0;break;    //정지
      case 'D': Serial.print(angle);break;
    }
  }
  
  //외부 인터럽트; 바퀴 속도를 계산하는 데 사용
  attachPinChangeInterrupt(PinA_left, Code_left, CHANGE);          //PinA_left 레벨 변경이 외부 인터럽트를 트리거; Code_left 서브함수 실행
  attachPinChangeInterrupt(PinA_right, Code_right, CHANGE);       //PinA_right 레벨 변경이 외부 인터럽트를 트리거; Code_right 실행
}

/////////////////////홀 카운트/////////////////////////
//왼쪽 속도 인코더 카운트
void Code_left() 
{
  count_left ++;
} 
//오른쪽 속도 인코더 카운트
void Code_right() 
{
  count_right ++;
} 
////////////////////pulse count///////////////////////
void countpluse()
{
  lz = count_left;     //인코더로 계산된 값을 lz에 할당
  rz = count_right;

  count_left = 0;     //카운트 수량 클리어
  count_right = 0;

  lpluse = lz;    
  rpluse = rz;

  if ((pwm1 < 0) && (pwm2 < 0))                     //차의 이동 방향을 판단; 후진 시 (PWM 즉 모터 전압이 음수), 펄스가 음수.
  {
    rpluse = -rpluse;
    lpluse = -lpluse;
  }
  else if ((pwm1 > 0) && (pwm2 > 0))                 //후진 시 (PWM 즉 모터 전압이 양수), 펄스가 양수.
  {
    rpluse = rpluse;
    lpluse = lpluse;
  }
  else if ((pwm1 < 0) && (pwm2 > 0))                 //차의 이동 방향을 판단; 좌회전 시, 우 펄스는 양수; 좌 펄스는 음수.
  {
    rpluse = rpluse;
    lpluse = -lpluse;
  }
  else if ((pwm1 > 0) && (pwm2 < 0))               //차의 이동 방향을 판단; 우회전 시, 우 펄스는 음수; 좌 펄스는 양수.
  {
    rpluse = -rpluse;
    lpluse = lpluse;
  }

  // 5ms마다 인터럽트 들어옴，펄스 수량 더함
  pulseright += rpluse;
  pulseleft += lpluse;
}

/////////////////////////////////interrupt ////////////////////////////
void DSzhongduan()
{
  sei();  //전체 인터럽트 허용
  countpluse();        //펄스 더함 서브함수
  mpu6050.getMotion6(&ax, &ay, &az, &gx, &gy, &gz);     //IIC로 MPU6050 6축 데이터 ax ay az gx gy gz 가져옴
  angle_calculate(ax, ay, az, gx, gy, gz, dt, Q_angle, Q_gyro, R_angle, C_0, K1);      //각도와 칼만 필터링 가져옴
  PD();         //각도 루프 PD 제어
  anglePWM();

  cc++;
  if(cc>=8)     //5*8=40，40ms마다 속도 PI 알고리즘 들어옴
  {
    speedpiout();   
    cc=0;  //클리어
  }
  turncc++;         
  if(turncc>4)       //20ms; 조향 PD 알고리즘 들어옴
  {
    turnspin();
    turncc=0;     //클리어
  }
}
///////////////////////////////////////////////////////////

/////////////////////////////기울기 계산///////////////////////
void angle_calculate(int16_t ax,int16_t ay,int16_t az,int16_t gx,int16_t gy,int16_t gz,float dt,float Q_angle,float Q_gyro,float R_angle,float C_0,float K1)
{
  float Angle = -atan2(ay , az) * (180/ PI);           //방사형 회전 각도 계산 공식; 음수 부호는 방향 처리
  Gyro_x = -gx / 131;              //자이로스코프에 의해 계산된 X축 각속도; 음수 부호는 방향 처리
  Kalman_Filter(Angle, Gyro_x);            //칼만 필터
  //Z축 회전 각도 파라미터
  Gyro_z = -gz / 131;                      //Z축 각속도
  //accelz = az / 1604;

  float angleAx = -atan2(ax, az) * (180 / PI); //X축과의 기울기 각도 계산
  Gyro_y = -gy / 131.00; //Y축 각속도
  Yiorderfilter(angleAx, Gyro_y); //1차 필터링
}
////////////////////////////////////////////////////////////////

///////////////////////////////칼만 필터/////////////////////
void Kalman_Filter(double angle_m, double gyro_m)
{
  angle += (gyro_m - q_bias) * dt;          //사전 추정
  angle_err = angle_m - angle;
  
  Pdot[0] = Q_angle - P[0][1] - P[1][0];    //사전 추정 오차의 공분산 미분
  Pdot[1] = - P[1][1];
  Pdot[2] = - P[1][1];
  Pdot[3] = Q_gyro;
  
  P[0][0] += Pdot[0] * dt;    //사전 추정 오차 공분산 미분의 적분
  P[0][1] += Pdot[1] * dt;
  P[1][0] += Pdot[2] * dt;
  P[1][1] += Pdot[3] * dt;
  
  //행렬 곱셈의 중간 변수
  PCt_0 = C_0 * P[0][0];
  PCt_1 = C_0 * P[1][0];
  //분모
  E = R_angle + C_0 * PCt_0;
  //이득 값
  K_0 = PCt_0 / E;
  K_1 = PCt_1 / E;
  
  t_0 = PCt_0;  //행렬 곱셈의 중간 변수
  t_1 = C_0 * P[0][1];
  
  P[0][0] -= K_0 * t_0;    //사후 추정 오차 공분산
  P[0][1] -= K_0 * t_1;
  P[1][0] -= K_1 * t_0;
  P[1][1] -= K_1 * t_1;
  
  q_bias += K_1 * angle_err;    //사후 추정
  angle_speed = gyro_m - q_bias;   //출력 값의 미분이 최적 각속도를 제공
  angle += K_0 * angle_err; ////사후 추정; 최적 각도를 얻음
}

/////////////////////1차 필터/////////////////
void Yiorderfilter(float angle_m, float gyro_m)
{
  angleY_one = K1 * angle_m + (1 - K1) * (angleY_one + gyro_m * dt);
}

//////////////////각도 PD////////////////////
void PD()
{
  PD_pwm = kp * (angle + angle0) + kd * angle_speed; //PD 각도 루프 제어
}

//////////////////속도 PI////////////////////
void speedpiout()
{
  float speeds = (pulseleft + pulseright) * 1.0;      //속도 펄스 값
  pulseright = pulseleft = 0;      //초기화
  speeds_filterold *= 0.7;         //1차 보완 필터링
  speeds_filter = speeds_filterold + speeds * 0.3;
  speeds_filterold = speeds_filter;
  positions += speeds_filter;
  positions += front;             //전진 제어 융합
  positions += back;              //후진 제어 융합
  positions = constrain(positions, -3550,3550);    //적분 포화 방지
  PI_pwm = ki_speed * (setp0 - positions) + kp_speed * (setp0 - speeds_filter);      //속도 루프 제어 PI
}
//////////////////속도 PI////////////////////

///////////////////////////회전/////////////////////////////////
void turnspin()
{
  int flag = 0;      //
  float turnspeed = 0;
  float rotationratio = 0;
  
  if (left == 1 || right == 1)
  {
    if (flag == 0)                             //회전 전 속도를 판단하여 유연성을 높임
    {
      turnspeed = ( pulseright + pulseleft);                      //현재 속도; 펄스로 표현
      flag=1;
    }
    if (turnspeed < 0)                                 //속도 절대값
    {
      turnspeed = -turnspeed;
    }
    if(left==1||right==1)         //왼쪽 키 또는 오른쪽 키를 누르면
    {
     turnmax=3;          //최대 회전 값
     turnmin=-3;         //최소 회전 값
    }
    rotationratio = 5 / turnspeed;          //속도 설정 값
    if (rotationratio < 0.5)
    {
      rotationratio = 0.5;
    }
     
    if (rotationratio > 5)
    {
      rotationratio = 5;
    }
  }
  else
  {
    rotationratio = 0.5;
    flag = 0;
    turnspeed = 0;
  }
  if (left ==1)//방향 파라미터에 따라 더함
  {
    turnout += rotationratio;
  }
  else if (right == 1 )//방향 파라미터에 따라 더함
  {
    turnout -= rotationratio;
  }
  else turnout = 0;
  if (turnout > turnmax)   turnout = turnmax;//진폭의 최대 값
  if (turnout < turnmin)   turnout = turnmin;//진폭의 최소 값

  Turn_pwm = -turnout * kp_turn - Gyro_z * kd_turn;//회전 PD 알고리즘 제어
}
///////////////////////////회전/////////////////////////////////

////////////////////////////PWM 최종 값/////////////////////////////
void anglePWM()
{
  pwm2=-PD_pwm - PI_pwm + Turn_pwm;           //모터에 PWM 최종 값을 할당
  pwm1=-PD_pwm - PI_pwm - Turn_pwm;
  
  if(pwm1>255)             //PWM 값이 255를 초과하지 않도록 제한
  {
    pwm1=255;
  }
  if(pwm1<-255) 
  {
    pwm1=-255;
  }
  if(pwm2>255)
  {
    pwm2=255;
  }
  if(pwm2<-255)
  {
    pwm2=-255;
  }

  if(angle>45 || angle<-45)      //기울기 각도가 45°보다 크면 모터가 정지
  {
    pwm1=pwm2=0;
  }

   if(pwm2>=0)         //PWM의 음수와 양수에 따라 모터 조향과 속도를 결정
  {
    digitalWrite(left_L1,LOW);
    digitalWrite(left_L2,HIGH);
    analogWrite(PWM_L,pwm2);
  }
  else
  {
    digitalWrite(left_L1,HIGH);
    digitalWrite(left_L2,LOW);
    analogWrite(PWM_L,-pwm2);
  }

  if(pwm1>=0)
  {
    digitalWrite(right_R1,LOW);
    digitalWrite(right_R2,HIGH);
    analogWrite(PWM_R,pwm1);
  }
  else
  {
    digitalWrite(right_R1,HIGH);
    digitalWrite(right_R2,LOW);
    analogWrite(PWM_R,-pwm1);
  }
}
```

**사용 방법 ?**

①균형 로봇을 잘 설치하고 테스트 코드를 업로드하세요;

②USB 케이블을 뽑고 실드의 전원 제어 스위치를 켜세요. 차의 균형을 유지하세요; 모터가 회전할 때 버튼 키 13을 누르면 부저가 "딱" 소리를 냅니다. 이 경우 차가 잘 조정되었습니다.

③위에서 언급한 블루투스 제어 방법을 따르세요; 블루투스 모듈을 연결하여 APP으로 균형 로봇을 실행하세요.  

블루투스 모듈 연결 방법은 프로젝트 6을 참조하세요.

![](media/dc310dcc455c5e90b283b05285c5f89a.jpeg)










<a id="resources"></a>
# 7.모든 리소스 다운로드

**https://fs.keyestudio.com/KS0193** 

---

# 용어집 (Glossary)

- 각도 루프(Angle loop): PD 제어로 기울기 각과 각속도를 이용해 직립을 유지하는 루프.
- 속도 루프(Speed loop): PI 제어로 전후 속도/위치(적분)를 보정해 경사나 외란에서도 균형을 유지하는 루프.
- 조향 루프(Steering loop): PD 제어로 좌우 바퀴 속도 차와 Z축 각속도를 이용해 방향을 제어하는 루프.
- 칼만 필터(Kalman filter): 가속도/자이로 센서 융합으로 각도와 각속도를 추정하는 필터(사전/사후 추정, 공분산 업데이트 포함).
- 1차(보완) 필터(First-order complementary filter): 저주파(가속도)와 고주파(자이로)를 간단히 융합하는 필터.
- 공분산(Covariance): 오차 분포의 상관을 나타내는 값. 필터의 신뢰도/이득 계산에 사용.
- 사전/사후 추정(Prior/Posterior estimate): 필터 업데이트 전/후의 상태 추정.
- 이득(Gain): 관측/오차 공분산에 기반해 계산되는 업데이트 계수(예: 칼만 이득, PID 이득).
- 외부 인터럽트(External interrupt): 엔코더 펄스 등 외부 신호 변화에 즉시 반응하는 인터럽트.
- 적분 포화 방지(Anti-integral saturation): 적분 항이 과도하게 누적되지 않도록 제한하는 기법.
- 코드휠/엔코더(Code wheel/Encoder): 바퀴 회전을 펄스로 변환해 속도/거리 측정에 사용되는 센서.
