## **네트워크 모델의 종류**

### **네트워크 계층 모델**

- TCP/IP 모델
    - TCP: 전송 제어 프로토콜(Transmission Control Protocol)
        - 한 기기에서 다른 기기로 데이터 전송하는 것을 담당
    - IP: 인터넷 프로토콜(Internet Protocol)
        - 데이터의 조각을 최대한 빨리 대상 IP 주소로 보내는 역할을 표시
    - 1980년대 초 프로토콜 모델로 공개
    - 현재의 인터넷에서 컴퓨터들이 서로 정보를 주고받는데 쓰이는 통신 규약(프로토콜)의 모음
    - 계층별 프로토콜
        - 4계층: 응용
        - 3계층: 전송
        - 2계층: 네트워크
        - 1계층: 네트워크 인터페이스
- `OSI 7계층`
    - OSI: 개방형 시스템 상호 연결(Open Systems Interconnection Reference Model)
    - 상이한 컴퓨터 시스템이 서로 통신할 수 있는 표준 제공(컴퓨터 네트워킹의 범용 언어)
    - 1984년 네트워크 통신을 체계적으로 다루는 ISO에서 표준으로 지정한 모델
    - 데이터를 주고받을 때 데이터 자체의 흐름을 각 구간별로 나눠놓은 것
    - 계층별 프로토콜
        - 7계층: 응용 - `HTTP`, SSH 등
        - 6계층: 표현 - SMB, AFP, XDR
        - 5계층: 세션 - NetBIOS
        - 4계층: 전송 - `TCP`, `UDP` 등
        - 3계층: 네트워크 - `IP`, `ICMP`, `ARP` 등
        - 2계층: 데이터 링크 - `이더넷`, ISDN, 무선랜 등
        - 1계층: 물리 - 전선, 전파, 광섬유, 모뎀 등

### 두 모델 비교
- 공통점
    - 계층적 네트워크 모델
    - 계층간 역할 정의
- 차이점
    - 계층의 수 차이
        - 4 응용 = 5 세션, 6 표현, 7 응용
        - 3 전송 = 4 전송
        - 2 네트워크 = 3 네트워크
        - 1 네트워크 인터페이스 = 1 물리, 2 데이터 링크
    - OSI는 역할 기반, TCP/IP는 프로토콜 기반
    - OSI는 통신 전반에 대한 표준
    - TCP/IP는 데이터 전송기술 특화
    - OSI: 논리적, 기능별, TCP/IP: 실무적

## **네트워크를 통해 전달되는 데이터, 패킷**

- 패킷이란?
    - 네트워크 상에서 전달되는 데이터를 통칭하는 말
    - 네트워크에서 전달하는 데이터의 형식화된 블록
    - 패킷은 `제어 정보`와 `사용자 데이터`로 이루어짐
    - 사용자 데이터는 페이로드라고도 함
    - `여러 프로토콜로 캡슐화 됨(순서가 있음)`
        - 헤더 -> 페이로드 -> 풋터(잘 사용하지 않음)
        - 마트료시카와 유사함
        - 여러 번 포장된 택배상자
        - 예시: Ethernet -> IPv4 -> TCP -> HTTP

- 패킷을 이용한 통신과정 - 캡슐화(인캡슐레이션)
  - 여러 프로토콜을 이용해서 최종적으로 `보낼 때` 패킷을 만드는 과정
  - 데이터를 보낼 때 프로토콜을 하나씩 붙이는 과정
      - TCP: 헤더, 데이터: 페이로드
      - IPv4: 헤더, TCP+데이터: 페이로드
      - Ethernet: 헤더, IPv4+TCP+데이터: 페이로드
      - 상위 계층 -> 하위 계층 순서(같은 계층끼리도 가능하나 순서가 있음)
- 패킷을 이용한 통신과정 - `디캡슐화(디캡슐레이션)`
  - 캡슐을 받을 때 패킷을 만드는 과정
  - 캡슐화의 역순
      - 하위 계층 -> 상위 계층 순서

- 계층별 패킷의 이름 PDU(프로토콜 데이터 단위: Protocol Data Unit)
    - 4계층의 PDU: 세그먼트
    - 3계층의 PDU: 패킷(다른 의미의 패킷)
    - 2계층의 PDU: 프레임(정확하게 얘기할 때 자주 쓰임)

## 2계층

### 2계층에서 하는 일
- 2계층의 기능
    - `하나의 네트워크 대역` 즉, `같은 네트워크 상`에 존재하는 여러 장비들 중에서 `어떤 장비`가 `어떤 장비`에게 보내는 데이터를 전달
    - 추가적으로 `오류 제어`(오류 체크), `흐름 제어`(누가 누구에게 데이터를 보내는지) 수행
- 2계층의 네트워크 크기
    - 2계층은 `하나의 네트워크 대역 LAN`에서만 통신할 때 사용한다.
    - 다른 네트워크와 통신할 때는 항상 `3계층`이 도와주어야 한다.
    - 3계층의 주소와 3계층의 프로토콜을 이용하여야만 다른 네트워크와 통신이 가능하다.

### 2계층에서 사용하는 주소
- 물리적 주소
- LAN에서 통신할 때 사용하는 MAC 주소(12자리의 16진수로 이루어짐, 6바이트)
    - OUI + 고유번호
        - OUI: IEEE에서 부여하는 일종의 제조회사 식별 ID 6자리
        - 고유번호: 제조사에서 부여한 고유번호 6자리

### 2계층의 프로토콜
- Ethernet 프로토콜: LAN에서 통신할 때 사용하는 Ethernet 프로토콜
    - Ethernet II Header
  ### 헤더는 다음과 같이 이루어짐
  - Preamble 4Byte
  - Preamble(Continued) 4Byte
  - `Destination Address`(목적지 주소) 4Byte
  - `Destination Address(Continued) + Source Address`(출발지 주소) 2Byte + 2Byte
  - `Source Address(Continued)` 4Byte
  - `Ethernet Type(헤더) + DATA(페이로드)` 2Byte + 2Byte
  - Ethernet Type
      - 상위 프로토콜을 미리 알려줌
      - 알려주지 않으면 알 수 없음

## **3계층 프로토콜**

#### **3계층에서 하는 일**

- 2계층은 MAC 주소를 이용하여 스위치에 등록된 컴퓨터에게 데이터를 보낼 수 있었음
- 3계층은 서로 다른 네트워크 대역, 즉 **멀리 떨어진 곳에 존재하는 네트워크까지 어떻게 데이터를 전달**할지 제어하는 일을 담당
    - **LAN과 LAN을 연결하기 위해서는 라우터와 같은 3계층 장비가 필요**
        - 라우터(Router): 컴퓨터 네트워크 간에 데이터 패킷을 전송하는 네트워크 장치
- **발신에서 착신까지의 패킷의 경로를 제어**
#### **3계층에서 쓰는 주소**

- 네트워크 장비들은 모두 MAC 주소를 가지고 있는데, 멀리 있는 네트워크와 연결하기 위해서는 IP(Internet Protocol) 주소 또한 필요함

**IPv4 주소**

- 인터넷 공간에서 각 PC를 구별하기 위한 고유한 식별자
- 특별한 경우가 아닌 이상 IP 주소는 IPv4 주소
- IP 주소의 범위는 0~255 (0.0.0.0 ~ 255.255.255.255)로 총 32bit (8bit(1byte) * 4)
    - IPv6은 총 128비트

**서브넷 마스크**

- IP 주소에 대한 네트워크의 대역을 나눠 주는데 사용하는 값
- IP 주소를 서브넷 마스크를 이용해 표기하는 방법을 서브넷 마스크 표기법이라 함
- IP 주소 체계는 서브넷 마스크로 네트워크 ID와 호스트 ID를 구분

**게이트웨이**

- 라우터와 같은 말이며, 소프트웨어 측면을 강조할 때 사용
- 한 네트워크에서 다른 네트워크로 이동하기 위해 거쳐야 하는 지점 (서로 다른 네트워크를 연결)
- 서로 프로토콜이 다를 경우 중재하는 역할

### **3계층 프로토콜 목록**

**ARP(Address Resolution Protocol)**

- 논리적인 IP 주소를 물리적인 MAC 주소로 바꾸어 주는 역할을 하는 주소 해석 프로토콜

**IPv4**

- 네트워크 상에서 데이터를 교환하기 위한 프로토콜

**ICMP(Internet Control Message Protocol)**

- 라우터에서 발생한 오류를 송신측으로 전송하는데 사용하는 프로토콜 (서로가 통신되는지 확인)

### **일반적인 IP 주소**

### **Classful**
- IP 주소의 범위를 클래스 별로 나누어 클래스에 맞게 사용하던 것이 초창기의 IP
### **Classless**
- 과거 PC의 보급이 적게 되던 때, IP 주소의 낭비가 심했음 (호스트 필드를 모두 사용하지 못했기 때문)
- 서브넷 마스크를 이용해 네트워크 대역을 어디서부터 구분할 것인지 지정

**IPv4의 주소 고갈 문제를 해결하기 위해 제안된 방법**

- 서브넷팅(Subnetting)
    - 네트워크를 다시 여러 개의 작은 네트워크(서브넷)으로 나누는 기법
- 슈퍼넷팅(Supernetting)
    - 여러 개의 네트워크를 하나의 네트워크로 합치는 기법

### **사설 IP와 공인 IP**
- Classless 하게 사용했음에도 IP 주소 부족 문제가 발생해서 도입

**공인 IP (Public IP)**

- 인터넷 사용자의 로컬 네트워크를 식별하기 위해 ISP(인터넷 서비스 공급자)가 제공하는 IP 주소
- 외부에 공개되어 있어 다른 PC로부터의 접근 가능
- 네이버에 '내 ip 주소'를 검색하여 확인 가능

**사설 IP (Private IP)**

- IPv4의 주소 부족으로 만들어진 개념으로 라우터에 의해 할당된 IP 주소
- 사설 IP 주소만으로는 인터넷에 직접 연결 불가능

### **특수한 IP 주소**

**0.0.0.0**

- 나머지 모든 IP를 의미

**127.0.0.1**

- 로컬 루프백 인터페이스를 나타내는 IP 주소이며 로컬 머신에서만 접근 가능

**게이트웨이 주소**

- 일반적으로 공유기의 IP 사용