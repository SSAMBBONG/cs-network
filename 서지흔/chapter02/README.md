# 02 물리 계층과 데이터 링크 계층

## 02-1 이더넷

- 물리계층과 데이터링크 계층은 서로 밀접하게 연관됨 → 이더넷이라는 공통된 기술 사용됨
- 이더넷 : 현대 LAN, 특히 유선 LAN환경에서 가장 대중적으로 사용되는 기술
- 케이블(통신매체) : 컴퓨터끼리 정보주고받기 위함
    <!-- ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/31d0c992-6369-498c-a415-56672e6260da/Untitled.png) -->

### 이더넷 표준

- 유선 LAN 환경을 구축했다면 십중팔구 물리 계층에서는 이더넷 규격 케이블을 사용했을 것이고, 데이터 링크 계층에서 주고받는 프레임은 이더넷 프레임의 형식을 따를 것
- IEEE 802.3
  - 이더넷 관련 다양한 표준들의 모음
  - 이더넷 표준화 작업을 위한 IEEE의 전문가 단체, 이른바 이더넷 작업 그룹의 이름
  - 이더넷 표준에 따라 지원되는 네트워크 장비, 통신매체의 종류와 전송속도 등이 달라질 수 있음

### 통신매체표기형태

<!-- ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/f3a43ed1-0f18-4a6f-9c4f-7d2f52b0d9fa/Untitled.png) -->

- 전송속도
  - 숫자만 있으면 Mbps, G붙으면 : Gbps
    <!-- ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/5f6e754d-0378-48ee-b5c6-33e34d51ebc1/Untitled.png)
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/301b69ed-8ce5-498f-b59d-3b5aa2732fa0/Untitled.png) -->
- BASE
  - 베이스밴드의 약자 : 변조타입 의미
  - 변조타입 : 비트 신호로 변환된 데이터를 통신매체로 전송하는 방법 ( 대부분 이더넷 통신매체 base 사용)
- 추가특성
  - 통신매체의 특성 명시
    - 전송가능한 최대 거리 : 10BASE-2
    - 물리계층인코딩방식 : 데이터가 비트신호로 전환되는 방식
    - 레인수 : 비트신호 옮길 수 있는 전송로 수
    <!-- ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/3de02133-13d5-4f9c-af4d-4b47c2befa9c/Untitled.png) -->

### 통신 매체 종류

- C, T, S, L
    <!-- ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/ea9124d3-f3bc-42d2-aab6-fb3961ab5f2b/Untitled.png)
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/10510229-d77f-4f7d-af8f-ad8582f5c8cb/Untitled.png) -->
- 이더넷 표준과 이를 기반으로 하는 통신매체 일부예시 (항상 일대일 대응은 아님 참고)
    <!-- ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/242ae8cb-d35f-4570-a08a-76ced7625c3f/Untitled.png) -->

### 이더넷 프레임

- 이더넷 네트워크에서 주고받는 프레임
- 상위계층으로부터 받아들인 정보에 헤더와 트레일러 추가하는 캡슐화과정을 통해 생성
- 이더넷 프레임 헤더 : 프리앰블, 수신시 MAC주소, 송신지 MAC주소, 타입/길이로 구성
  - 프리앰블
    - 프레임 시작을 알리는 8바이트(64비트)크기의 정보
    - 첫 7바이트 10101010, 마지막 바이트 10101011
    - 수신지는 이 프리앰블 통해 이더넷 프레임이 오고있음 알아차림
    - 송수신지간의 동기화 위해 사용
        <!-- ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/0b29abfe-78fe-4e5b-a831-82a42475c166/Untitled.png) -->
  - 수신시 MAC주소, 송신지 MAC주소
    - **MAC** 주소 : 네트워크 인터페이스마다 부여되는 6바이트(48비트)길이의 주소, LAN내의 수신지 송신지 특정 가능(일반적으로 고유값, 일반적으로 변경x)
    - **NIC**(network interface controller)가 네트워크 인터페이스를 담당 (MAC주소가 부여되는 곳) → 한 컴터에 NIC여러개면 MAC주소도 여러개 있을 수 있음)
  - 타입/길이
    - 타입, 길이 올 수 있음
    - 필드 명시 크기 1500이하일 경우 프레임의 크기(길이) 나타냄 // 1536이상일 경우 타입 나타내는데 사용
    - 이더타입 : 이더넷 프레임이 어떤 정보를 캡슐화했는지 나타내는 정보
    - 프로토콜에 따라 다름(IPv4면 16진수 0800)
        <!-- ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/52bfcea3-3bee-4e6f-b094-459ca202f3bd/Untitled.png) -->
- 이더넷 프레임 페이로드 : 데이터
  - 데이터
    - 상위계층에서 전달받거나 상위계층으로 전달해야할 내용
    - 네트워크 계층의 데이터와 헤더를 합친 PDU 포함됨
    - 최대 크기 1500 바이트, 반드시 (46바이트 이상)이어야함
    - 그 이하의 데이터면 padding해야함(0으로패딩)
- 이더넷 프레임 페이로드 : FCS
  - FCS
    - 수신한 이더넷 프레임에 오류가 있는지 확인
    - 데이터링크 계층에서 오류 검출이 이루어지기도 하는데 바로 여기서 오류 검출 이루어짐
    - CRC(Cyclic Reduntancy Check) 즉 순환 중복 검사라고 불리는 오류 검출용 값 들어감
    - 송신지는 프리앰블을 제외한 나머지 필드 값들을 바탕으로 CRC 값을 계산한 후, 이 값을 FCS 필드에 명시
    - 수신지는 수신한 프레임에서 프리앰블과 FCS 필드를 제외한 나머지 필드 값들을 바탕으로 CRC 값을 계산한 뒤, 이 값을 FCS 필드 값과 비교
        <!-- ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/125a6e72-2cc7-410f-a0cc-8f107a820abb/Untitled.png) -->
    <!-- ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/7fe5eeb5-42fa-4a32-a160-33140474f98e/Untitled.png) -->

### 토큰링

- 호스트들이 링 형태로 연결
- 호스트끼리 돌아가며 토큰 정보 주고받음
- 네트워크 내 다른 호스트에게 메시지 송신하려면 반드시 토큰 가지고 있어야함
    <!-- ![C는 전송못함, A가 b나 c로 토큰 전송해주고 거쳐받아야 송신가능](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/59b0a13c-18bd-4857-bf71-fa0d657ea8ef/Untitled.png) -->
  C는 전송못함, A가 b나 c로 토큰 전송해주고 거쳐받아야 송신가능

## 02-2 NIC와 케이블

- 케이블 : NIC에 연결되는 물리계층의 유선 통신 매체
  - 유선
    - 트위스트페어케이블
    - 광섬유케이블

### NIC

- = 네트워크 인터페이스 카드, 네트워크 어댑터, LAN 카드, 네트워크 카드, 이더넷 카드
- 호스트와 유/무선통신매체 연결, MAC주소 부여되는 네트워크 장비(대화에서 귀와 입 얘네가 있어야 비로소 대화 가능)
- 호스트를 네트워크(LAN)에 연결하기 위한 하드웨어
- USB로 연결하는 NIC도 있고, 마더보드에 내장된 NIC도 있음 만약 추가 장치를 연결하지 않고도 네트워크에 연결되는 컴퓨터를 사용하고 있다면 높은 확률로 마더보드에 내장된 NIC를 사용 중

### 트위스티드 페어 케이블

- 구리선으로 전기신호를 주고받는 통신매체
- 케이블 본체 + 커넥터(RJ-45)
- 노이즈 : 구리선에 전자적 간섭 생길 수 있음(전기신호 왜곡 가능성)
- 차폐 : 노이즈를 방지하기 위해 구리선을 철사(브레이드실드), 포일(포일실드)로 감쌈
- STP(Shielded Twisted Pair) : 브레이드 실드로 노이즈를 감소 시킨 트위스티트 페어 케이블
- FTP(Foil Twisted Pair) : 포일 실드로 노이즈를 감소 시킨 트위스티트 페어 케이블
- UTP(unshielded Twisted Pair) : 아무것도 안 감싼 트위스티트 페어 케이블
- XX에는 케이블 외부를 감싸는 실드의 종류 명시(겉)
- Y에는 꼬인 구리선을 감싸는 실드의 종류 명시(속에 꼬인 구리선쌍)
    <!-- ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/2b7f1795-1cde-4810-abab-3979864a1102/Untitled.png)
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/96a65617-2cd0-4949-9fd0-eac746d3a6a7/Untitled.png) -->
- 카테고리에 따른 트위스티드 페어 케이블의 분류
  - 카테고리 : 트위스티드 페어 케이블 성능의 등급 구분 역할, 높은 카테고리일수록 높은 성능
  - Cat이라는 표기로 줄여 표현하는 경우 많음
    <!-- ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/eaaf5042-836b-4774-b30c-eea49a186365/Untitled.png) -->

### 광섬유케이블

- 빛(광신호)을 이용해 정보 주고받는 케이블
- 전기신호 이용하는 케이블에 비해 속도 빠르고, 먼 거리 전송 가능 노이즈 간섭 영향 적음
- 대륙 간 네트워크 연결에도 사용
- LC, SC, FC, ST
    <!-- ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/edaa24d0-474d-47fa-942d-9f77c9df27b8/Untitled.png) -->
- 코어 : 광섬유의 중심 , 실질적으로 빛이 흐르는 부분
- 클래딩 : 빛이 코어 안쪽에서만 흐르도록 빛을 가두는 역할(굴절률 차이)
    <!-- ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/c31d0afa-74a8-48b2-9d31-44a1b30dc036/Untitled.png) -->
- 싱글모드 광섬유 케이블(SMF : Single Mode Fiber)
  - 코어 지름 : 8~10mm (멀티모드 광섬유 케이블 보다 작음) → 빛이 이동할 수 있는 경로 적음 → 빛 이동경로 하나 이상 갖기 힘들고 mode가 single이라 표현
      <!-- ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/3b27c2de-0b1f-4f06-9d80-021463ff04f2/Untitled.png) -->
  - 신호손실 적어 장거리 전송 적합, 멀티모드보다 비용 높음
  - 장파장 사용
- 멀티모드 광섬유 케이블(MMF : Multi Mode Fiber)
  - 코어 지름 : 50 ~ 62.5mm
  - 빛 여러 경로 이동 가능 → mode가 multi
      <!-- ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/a703b9f4-7038-4d91-8efb-6a75d42b31e2/Untitled.png) -->
  - 장거리 전송 부적합
  - 멀티모드 케이블 : 일반적으로 수백미터, 길어야 수킬로미터 전송 가능, 근거리 연결

<!-- ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/d2dee2f0-4836-46d8-9659-08b55ed3712a/Untitled.png) -->

## 02-3 허브

통신매체를 통해 송수신되는 메시지는 다른 호스트에게 전달되는 과정에서 네트워크 장비를 거칠 수 있음

물리계층 : 허브

데이터링크계층 : 스위치

허브의 동작 방식 : 반이중 모드

↔ 전이중 모드

허브 충돌문제 해결 위한 프로토콜 CSMA/CD 학습

<!-- ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/f686c331-679c-4777-9471-a7ece02e0464/Untitled.png) -->

### 주소 개념이 없는 물리 계층

- 송수신지를 특정할 수 있는 주소는 데이터 링크 계층부터 존재
- 물리계층에서는 단지 호스트와 통신매체 간의 연결과 통신 매체 상의 송수신이 이루어질 뿐
- 물리계층의 네트워크 장비는 송수신되는 정보에 대한 어떠한 조작이나 판단하지 않음
- 데이터 링크계층은 주소 개념 존재 : MAC주소 → 데이터 링크 계층의 장비나 그 이상 계층의 장비는 송수신지 특정 가능, 주소 바탕으로 송수신되는 정보에 대한 조작과 판단 가능
    <!-- ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/5004059f-9171-484a-8218-182cae519aab/Untitled.png) -->

### 허브

- 물리계층에서 여러대의 호스트를 연결하는 장치
- 리피터 허브라 불리기도 하며 이더넷 네트워크 허브는 이더넷 허브라 불림
- 포트(port) : 커넥터를 연결할 수 있는 네 개의 연결지점
    <!-- ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/4a690d01-d0e1-45d4-a2d4-e20a2ed9e455/Untitled.png) -->
- 오늘날 인터넷 환경에서 잘 사용되지 않음 but 두가지 특징이 너무 중요
  1. 전달받은 신호를 다른 모든 포트로 그대로 다시 내보낸다
  - 신호 전달받으면 어떠한 조작, 판단하지 않고 송신지를 제외한 모든 포트에 내보냄
  - 허브를 통해 신호 전달받은 호스트는 데이터링크 계층에서 프레임 MAC주소 확인 후 자신과 관련없는 프레임 폐기
      <!-- ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/a8e7acfb-a3b7-4abf-9187-d727fdbc145b/Untitled.png) -->
  1. 반이중 모드로 통신
  - 1차선 도로처럼 송수신을 번갈아하면서하는 통신방식
      <!-- ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/e3504fc7-31c8-48ce-861a-6b3086ffb967/Untitled.png) -->
- 리피터 : 허브 이외의 대표적인 장비
  - 트위스티드 페어 케이블에서 전송거리 길 수록 전기신호 감소 → 전기신호 증폭시켜주는 장비 (판단조작x 그저 증폭) 허브에 리피터 기능 포함하는 경우 많음
- 콜리전 도메인
  - 충돌 발생 가능 영역
  - 허브는 반이중 통신 지원 → 한 호스트가 허브에 송신하는 동안 다른 호스트는 기다림 → 만약 동시에 송신 신호 보낸다면? → 충돌 발생
    <!-- ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/545a9428-eec4-4629-a768-760619e08826/Untitled.png) -->
  - 해결하기 위해 CSMA/CD 프로토콜 사용하거나 스위치 장비 사용해야함

### CSMA/CD

- 허브 충돌발생 근본 이융 : 반이중 모드
- Carrier Sense Multiple Access with Collision Detection
- Carrier Sense : 캐리어 감지
  - 현재 통신매체의 사용 가능 여부 검사
- Multiple Access : 다중접근
  - 복수의 호스트가 네트워크에 접근하려는 상황
- Collision Detection : 충돌 검출
  - 충돌발생시 검출 → 감지하면 전송 중단, 충돌 검출한 호스트는 다른 이들에게 충돌발생 알리고자 **잼신호(Jam signal)** 보냄 → 임의 시간 기다린 뒤 다시 전송

① 먼저 현재 전송이 가능한 상태인지를 확인하고,

② 다른 호스트가 전송 중이지 않을 때 메시지를 전송합니다.

③ 만일 부득이하게 다수의 호스트가 접근하여 충돌이 발생하면 임의의 시간만큼 대기한 후에 다시 전송

## 02-4 스위치

- 애초에 전이중모드를 지원하는 네트워크 장비
- 스위치는 MAC주소 학습 가능 → 전달받은 신호를 원하는 포트로만 보낼 수 있음

### 스위치

- 데이터링크계층의 네트워크 장비
- 2계층에 사용해서 L2스위치라고도 불림
- 여러 호스트 연결 가능(허브와 달리 MAC 주소 학습해 특정 MAC 주소 가진 호스트에만 프레임 전달 가능, 전이중 통신 지원) → 포트별로 콜리전 도메인 나뉘고 전이중모드 통신하므로 CSMA/CD 프로토콜 필요x
    <!-- ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/881622fc-e010-4043-8d61-4b85b7e36248/Untitled.png) -->
- 스위치 특징
  - MAC 주소 학습
    - 특정포트와 해당 포트에 연결된 호스트 MAC주소와의 관계 기억
    - 원하는 호스트에만 프레임 전달 가능
  - MAC 주소 테이블
    - MAC 주소 학습을 위해 포트와 연결된 호스트의 MAC 주소 간의 연관 관계를 메모리에 표 형태로 기억
      <!-- ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/fc8832e5-5b37-4ccb-8663-77c7b5894a7c/Untitled.png)
      
      ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/2239ee03-a3dc-45f8-ae10-631555b8da72/Untitled.png) -->

### MAC 주소 학습

- MAC 주소 테이블이 채워지고 유지되는 방법 ( 스위치의 3가지 기능)

1. 플러딩 : 스위치는 마치 허브처럼 송신지 포트를 제외한 모든 포트로 프레임을 전송
2. 포워딩과 필터링
   1. 포워딩 : 프레임이 전송될 포트에 실제로 프레임을 내보내는 것
   2. 필터링 : 전달받은 프레임을 어디로 내보내고 어디로 내보내지 않을지 결정하는 스위치의 기능
3. 에이징 : MAC 주소 테이블에 등록된 특정 포트에서 일정 시간 동안 프레임을 전송받지 못했다면 해당항목은 삭제

A → C로 프레임 전송

<!-- ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/97662d90-ce41-495b-8c68-630ff6f54792/Untitled.png)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/3045c0b5-b928-40c4-b4fd-f2b782ce31f0/Untitled.png)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/939a4e3a-3242-4723-acb1-6a73bfbcf2e6/Untitled.png)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/a94cd58f-7eb1-44ab-9c66-9af74017d791/Untitled.png)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/2111f04f-be7f-4734-b08c-f9d778eb8b57/Untitled.png)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/36d07b17-050a-452e-83b8-0a567a20c195/Untitled.png) -->

### 브리지

<!-- ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/192b4bd8-3dc5-4b03-aafe-6caf27ef7cbb/Untitled.png) -->

- 데이터링크 계층 스위치와 유사한 장비
- 네트워크 영역을 구획하여 콜리전 도메인을 나누거나 네트워크를 확장하는 용도
- MAC 주소 학습 가능, 특정 호스트 가 연결되어 있는 포트로 프레임 포워딩, 필터링 가능
- but, 단일 장비로서의 브리지는 대중화된 스위치보다 사용빈도 줄어드는 추세 브리지를 이용한 네트워크 구획 및 확장은 스위치 통해 얼마든지 가능. 프레임 처리능력도 스위치가 우수

### VLAN(Virtual LAN)

- 한 대의 스위치로 가상의 LAN을 만드는 방법
    <!-- ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/85844ec7-5fde-47c3-a9f5-f9f1b63c8559/Untitled.png) -->
  - VLAN 구성하지 않으면 서로 메시지 주고받을 일 적거나 브로드케스트 메시지 받을 필요 없어서 굳이 같은 네트워크 속할 필요없는 호스트 있을 수도 있음 (송신지 제외한 포트로 다 전송하기 때문)
  - 이를 분리하고자 매번 새로운 스위치 장비 구비는 비효율적
    <!-- ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/f2abc190-6cdd-445d-917e-64394db371a8/Untitled.png) -->
  - VLAN을 구성하면 한 대의 물리적 스위치라 해도 여러 대의 스위치가 있는 것처럼 논리적인 단위로 LAN을 구획
  - VLAN 구성하면 VLAN1에 속한 호스트 A, B, C, D는 서로 동일한 LAN에 있는 것으로 인식하지만, 다른 VLAN에 속한 호스트 E, F, G, H, I는 물리적인 거리와 관계없이 다른 LAN에 있는 것처럼 인식
  - 만약 VLAN1에 속한 호스트가 VLAN2에 속한 호스트와 통신하고자 한다면 데이터 링크 계층의 장비가 아니라 네트워크 계층 이상의 상위 계층 장비가 필요
    <!-- ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/7da0c0e9-7b58-42bb-8dee-54e8a1b7f38f/Untitled.png) -->
- 포트기반 VLAN
  - 스위치의 포트가 VLAN을 결정하는 방식
  - 사전에 특정 포트에 VLAN 할당 후 해당 포트에 호스트를 연결함으로써 VLAN에 포함 가능
      <!-- ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/3388604d-ea4d-481a-be72-8a9f9e71bad8/Untitled.png) -->
  - 한대의 스위치만으로 포트기반 VAN 나누면 문제 발생 → 포트 수 부족
  - ex VLAN1 호스트 4개, VLAN2 호스트 3개, VLAN3 호스트 3개를 포트가 8개인 하나의 스위치에 연결하기는 어렵습니다. 물론 다음 그림처럼 VLAN 스위치 여러 대를 구비해 같은 VLAN 포트끼리 연결하여 VLAN을 확장하는 방법도 있지만, 이 또한 포트의 낭비
      <!-- <!-- ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/13188f03-bc25-42f8-8156-7d1b2b4f519e/Untitled.png) -->
    <!-- ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/ee46e185-e2f3-4efa-9ea6-9424bb2250ae/Untitled.png) --> -->
  - VLAN 트렁킹 : 두 대 이상의 VLAN 스위치를 효율적으로 연결하여 확장하는 방법
  - 트렁크포트 : 스위치간의 통신을 위한 특별한 포트에 VLAN스위치 서로 연결
  - 낭비되는 포트 최소하는 동시에 같은 스위치 연결되어 있지 않아도 LAN에 속하게 네트워크 구성 가능
    <!-- ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/6f634ca0-ca29-4cbb-b373-3b6a0dd39d2d/Untitled.png)
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/2cdfad60-29be-4ce4-9f38-b6c54a42fbb1/75afce55-4aa9-4ce3-958c-4d901e007da9/Untitled.png) -->
- MAC 기반 VLAN
  - 포트가 VLAN을 결정하느 것이 아니라 송수신하는 프레임 속 MAC 주소가 호스트가 속할 VLAN 결정하는 방식
  - 호스트 A의 MAC 주소가 VLAN3에 할당되었다면 어떤 포트에 연결되는 호스트 A는 VLAN3에 속한 호스트로 동작
