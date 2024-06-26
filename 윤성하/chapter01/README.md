# **Network**

> 여러 개의 장치가 서로 연결되어 정보를 주고받을 수 있는 통신망

# **Internet**

> Inter(~간의) + net(네트워크) 즉, 여러개의 네트워크가 연결된 것

<hr>

## **Network의 구조**

> Network는 [[그래프]] 의 형태를 띠고 있으며, 메시지를 통해 정보를 주고받는다.

![Pasted image 20240504141433.png](../img/Pasted%20image%2020240504141433.png)

### 노드

> 네트워크에 참여하는 디바이스

노드는 크게 호스트(Host)와 네트워크 장비로 나눌 수 있다.

Host는 정보를 최초로 생성 및 송신하고, 최종적으로는 수신한다.

그렇기에 호스트를 종단 시스템(end system)이라고도 부른다.

이를 고려해보면 왜 휴대폰을 단말기(끝 장치)라고 부르는지 이해할 수 있다.

호스트는 수행하는 역할에 따라 다르게 부르기도 하는데 그 중 대표적인것이 서버/클라이언트 이다.

- 서버(server)는 어떠한 **서비스를 제공**하는 호스트
- 클라이언트(client)는 서버에게 어떠한 **서비스를 요청**하고 서버의 **응답을 제공받는** 호스트

호스트들이 통신하기 위해서는 중간에 노드를 거쳐가기도 한다.

이를 ‘중간 노드(네트워크 장비)’라고 부르며 대표적인 예로는 이더넷 허브, 스위치, 라우터, 공유기가 있다.

이러한 장비들은 정보가 수신지까지 안정적이고 안전하게 전송될 수 있도록 한다.

```
호스트, 네트워크 장비, 서버, 클라이언트와 같은 용어는 노드의 역할에 따라 분류한 것 일 뿐, 하나의 노드가 여러 역할을 수행할 수 있다.
ex) 클라이언트가 아파트 데이터를 요청 -> 서버는 공공데이터 포털에 api 요청을 보내고 그 응답을 클라이언트에게 전달.
이 예시에서 서버는 공공데이터 포털에 요청을 보내므로 클라이언트이기도 하다.

TMI
Tor 브라우저를 사용하면 자신의 컴퓨터가 중간 노드의 역할도 수행한다.
그렇기에 다른 사람이 보낸 해킹 공격을 내가 보낸 공격으로 서버가 인식해버릴 수 있으니 주의하자
```

### 링크

> 노드를 연결하는 통신 매체

통신 매체는 유선 매체와 무선 매체로 분류할 수 있다.

ex) 랜선 / WIFI

### 메시지

> 노드가 주고받는 정보

웹 페이지, 파일, 메일 등

<hr>

## **Network 분류**

### 범위에 따른 분류

![Pasted image 20240504184653.png](../img/Pasted%20image%2020240504184653.png)

- LAN(Local Area Network)
  - 가까운 지역을 연결한 근거리 통신망
  - 가정, 기업, 학교처럼 한정된 공간에서의 네트워크를 의미
- WAN(Wide Area Network)
  - 먼 지역을 연결하는 광역 통신망
  - 멀리 떨어진 LAN을 연결하는 네트워크(=네트워크의 네트워크=인터넷)
    - 인터넷 ==> WAN, WAN =/=> 인터넷
  - 다른 LAN에 속한 호스트와 통신해야 할 때 사용
  - ISP(Internet Service Provider)가 구축 및 관리

![Pasted image 20240504185048.png](../img/Pasted%20image%2020240504185048.png)

### 메시지 교환 방식에 따른 분류

- 회선 교환

  - 호스트들이 통신을 하기 전, 연결을 확보해야 한다

    → 두 호스트 간 통신만 하기 때문에 비교적 전송되는 정보의 양이 일정하다.

  - 회선 스위치를 통해 호스트 사이 일대일 전송로를 확보한다.

    ![Pasted image 20240504232737.png](../img/Pasted%20image%2020240504232737.png)

  - 한 번 연결이 설정되면 연결된 전송로를 통해서만 통화가 가능하다

    → 회선을 점유하고 있기에 회선의 이용 효율이 낮다 (메시지를 주고받지 않으면서 점유한다면?)

- 패킷 교환

  - 회선을 점유한다는 회선 교환의 문제점을 해결하기 위해 메시지를 [[패킷]]이라는 단위로 나누어 전송

  - 정해진 경로가 없음
    - 다양한 중간 노드(패킷 스위치)를 거쳐 전송된다
    - 중간 노드는 패킷이 수신지까지 올바르게 도달할 수 있도록 최적의 경로를 결정
    - 네트워크 장비: 라우터, 스위치
      ![Pasted image 20240504234334.png](../img/Pasted%20image%2020240504234334.png)

<hr>

## 프로토콜(Protocol)

> 노드 간에 정보를 올바르게 주고받기 위해 합의된 규칙이나 방법

모든 프로토콜에는 저마다의 목적과 특징이 있다

프로토콜마다 목적과 특징이 다르기에 헤더에 포함되는 정보가 달라질 수 있다

→ 프로토콜마다 패킷의 헤더 내용이 달라질 수 있다

→ 헤더가 없는 프로토콜도 존재(검색해봐도 안나오는데…)
![Pasted image 20240505002635.png](../img/Pasted%20image%2020240505002635.png)

<hr>

## 네트워크 참조(계층) 모델

> 통신이 일어나는 각 과정을 계층으로 나눈 구조

![Pasted image 20240505010538.png](../img/Pasted%20image%2020240505010538.png)

### OSI 모델

- 네트워크를 이론적으로 기술(이상적)

![Pasted image 20240505004134.png](../img/Pasted%20image%2020240505004134.png)

| 계층 이름        | 기능                                                                                                                                                                                  | 단위(PDU)                        |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------- |
| 응용 계층        | - 최종 사용자와의 인터페이스를 제공하고 응용 프로그램 간의 통신을 관리                                                                                                                | 메시지 또는 데이터               |
| 표현 계층        | - 데이터를 암호화, 압축 또는 변환하여 네트워크로 전송 가능한 형식으로 변환                                                                                                            | 데이터                           |
| 세션 계층        | - 통신 세션을 설정, 유지 및 해제하여 데이터 교환을 관리                                                                                                                               | 데이터                           |
| 전송 계층        | - 종단 간 통신을 관리하고 데이터 전달의 신뢰성과 순서를 보장(흐름 제어)<br>- 포트를 통해 응용 프로그램 식별                                                                           | 세그먼트(TCP)<br>데이터그램(UDP) |
| 네트워크 계층    | - 라우팅과 패킷 전달을 담당하며, 데이터를 최종 목적지로 전송<br>- IP주소를 통해 통신하고자 하는 수신지 호스트와 네트워크를 식별<br>- 원하는 수신지에 도달하기 위한 최적의 경로를 결정 | 패킷                             |
| 데이터 링크 계층 | - 물리적인 매체를 통해 신뢰성 있는 데이터 전송을 제공하고, 오류를 검출 및 수정<br>- MAC 주소를 통해 네트워크 내 송수신지를 특정                                                       | 프레임                           |
| 물리 계층        | - 실제 데이터 비트를 전송하는 물리적 매체를 다룬다<br>- 주소 개념이 없다                                                                                                              | 비트                             |

### TCP/IP

- 구현에 중점을 둔 네트워크 참조 모델 (실용적)

  ![Pasted image 20240505005956.png](../img/Pasted%20image%2020240505005956.png)

| 계층 이름            | 기능                                                       |
| -------------------- | ---------------------------------------------------------- |
| 응용 계층            | 응용 프로그램과 네트워크 간의 통신을 관리                  |
| 전송 계층            | 종단 간 통신을 관리하고 데이터 전달의 신뢰성과 순서를 보장 |
| 인터넷 계층          | 패킷의 경로 선택 및 전송을 담당                            |
| 네트워크 액세스 계층 | 네트워크에 연결되어 있는 하드웨어와의 통신을 담당          |

<hr>

## 캡슐화 / 역캡슐화

![Pasted image 20240505011514.png](../img/Pasted%20image%2020240505011514.png)

## 캡슐화

- 송신 과정에서 헤더 및 트레일러를 추가해 나가는 과정
- 각 계층에서는 상위 계층으로부터 내려받은 패킷을 페이로드로 삼아, 프로토콜에 걸맞은 헤더(혹은 트레일러)를 덧붙인 후 하위 계층으로 전달 (상위 계층의 패킷은 하위 계층에서의 페이로드로 간주)

  ![Pasted image 20240505011845.png](../img/Pasted%20image%2020240505011845.png)

## 역캡슐화

- 수신할 때 캡슐화 과정에서 붙였던 헤더(및 트레일러)를 각 계층에서 확인한 뒤 제거하는 과정

![Pasted image 20240505011317.png](../img/Pasted%20image%2020240505011317.png)

<hr>

## 네트워크 성능 지표

### 처리율

> 단위 시간당 네트워크를 통해 전송되는 정보량

실시간성이 강조된 지표

단위: bps, Mbps, Gbps, pps등 (byte가 아니라 bit다!)

### 대역폭

> 단위 시간 동안 통신 매체를 통해 송수신할 수 있는 최대 정보량

신호 처리 영역에서의 대역폭의 정의(주파수의 범위)와 헷갈리지 말자

단위: bps, Mbps, Gbps

### 패킷 손실

> 송수신되는 패킷이 손실된 상황

높은 트래픽으로 인해 노드가 순간적으로 처리해야 할 패킷이 너무 많아지거나 네트워크상에 예기치 못한 장애가 발생하여 생길 수 있음

(유실된 패킷 / 전체 패킷 \* 100)을 주로 사용

ping
