# NCP. Computing

## Computing 상품

---

기본적인 서버를 생성하고 관리하는 상품

서비스 규모와 사용목적에 적합한 성능의 서버를 선택할 수 있도록 다양한 서버 타입 제공

2v CPU ~ 16v CPU 부터 High Memory 서버, VDS, HPC, GPU 등 다양한 상품 존재

체험용 서버인 마이크로 서버 제공(Classic Only) - 가입일로부터 1년간

G1, G2로 구분하여 제공, VPC 환경에서는 G2

### 요금 구성

---

컴퓨팅, 네트워크, 스토리지 요금이 발생

서버 정지 시 컴퓨팅, 네트웍 요금을 발생하지 않으나 스토리지 비용 발생

서버 정지 시 표준 요금이 적용되는 서버 → GPU, Bare Metal 서버

### SSD, HDD 디스크 타입 제공

---

IO 퍼포먼스 차별화

SSD 사용 시 최대 IOPS 보장

## Server 타입

### Micro 타입

---

**신규가입 후 결제 정보를 등록한 월부터 1년 간 무료로 사용할 수 있는 서버 상품**

Mirco 서버는 서버 비용만 무료이며, 공인 IP 등의 유료 상품 이용시 해당 비용 과금 발생

Classic 서버 : CnetOS, Ubuntu (1vCPU, 1G RAM, 500 HDD)

추천용도 : 서비스 체험용

### Compact 타입

---

**가격 부담을 줄인 저사양 서버로 운영하는 서비스에 성능 이슈가 적고 서버 운영 비용부담을 덜고자할때 적합**

Classic 서버 : CentOS, Ubuntu, Windows (2v~ 16v CPU, 4G~ 32G RAM)

추천용도 : 개발 테스트 서버, 개인 홈페이지, 소규모 웹사이트

### Standard

---

**다양한 IT 비즈니스에 활용할 수 있는 네이버클라우드 플랫폼 서비스의 범용 서버이다.**

균형 잡힌 서버 사양을 제공하고 높은 가용성과 서비스 안정성을 자랑한다.

Classic 서버 : CentOS, Ubuntu, Windows (2v ~ 16v CPU, 4G ~ 32G RAM)

VPC 서버(*Gen2) : CPU와 Memory 비율 1대 4,   ex) 2C8G, 4C16G, 32C128G etc ... 

추천용도 : 중/대규모 모바일 및 웹 서비스와 게임/미디어/금융 서비스 운영

### High Memory

---

**64GB 이상의 고 메모리 서버로서, 높은 성능을 자랑**

메모리 성능에 영향을 많이 받는 데이터 애플리케이션을 운영할때 적합

Classic 서버 : CentOS, Ubuntu, Windows (8v ~ 32v CPU, 64G ~ 256 G RAM)

VPC 서버(*Gen2) : CPU와 Memory의 비율 1대 8.   ex)2C16G,  4C32G,  32C256G etc...

추천용도 : 고성능 데이터베이스 서버 , 대규모 게임 서비스

### CPU intensive

---

**고성능 CPU를 장착하여 많은 연산이 필요한 업무에 최적화된 서버**

Classic 서버 : CentOS, Ubuntu, Windos (20v ~ 32vCPU, 80G ~ 232G RAM, 1~2TB HDD)

추천용도 : 머신러닝 및 딥러닝 처리 및 고성능 웹서버

### Bare Metal Server

---

**단독으로 사용할 수 있는 고성능 물리 서버를 클라우드 형태로 제공**

Classic 환경

- 물리서버에 하이퍼바이저 없이 사용 가능
- 적합한 RAID 구성방식 선택 가능
- 단독 서버를  사용하는 것이기 때문에 성능에 민감한 서비스도 안정적으로 운영가능
- CentOS, ORACLE Linux와 WIndows 제공
- NCP내의 다양한 서비스와 연계 가능
- 서버장애시 Live Migration 불가

VPC 환경

- 물리서버에 하이퍼바이저없이 사용가능
- VPC와 Subnet을 선택하여 구성 (Bare Metal 전용 Subnet 구성가능)
- 적합한 RAID 구성방식을 선택 가능
- CentOS, ORACLE Linux와 RHEL 제공 (WIndows 미제공)
- NCP 내의 다양한 서비스와 연계 가능
- 서버장애시 Live Migration 불가

### GPU Server

---

**병렬처리에 최적화된 GPU서버의 고성능 컴퓨팅 파워 제공**

Classic 환경

- NVIDA P40, V100 장착
- NVIDA GRID 기술이 아닌 Pass Through 제공
- 서버 당 최대 2장의 CPU
- P40 : 4vCPU, 30GB Memory 당 GPU 1개, 24GB GPU 메모리 제공
- V100 : 8vCPU, 90GB Memory 당 GPU 1개, 32GB GPU 메모리 제공
- 사용가능 OS : CentOS, Ubuntu, Windows Server

VPC 환경

- NVIDA P40, V100 장착
- NVIDA GRID 기술이 아닌 Pass Through 제공
- V100은 서버 당 최대 4장의 GPU, T4는 서버 당 최대 2장의 GPU
- T4 : 8vCPU, 40GB Memory 당 GPU 1개, 16GB GPU 메모리 제공
- V100 : 8vCPU, 90GB Memory 당 GPU 1개, 32GB GPU 메모리 제공
- 사용가능 OS : CentOS, Ubuntu

## 서버 Operation

---

우선 서버 작동 방법은 크게 3가지가 있다.

웹콘솔, CLI, API 이다.

웹 콘솔의 경우 [ncloud.com](http://ncloud.com) 콘솔을 이용하여 다양한 오퍼레이션이 가능하다.

CLI Operation도 가능한데 CLI툴을 설치하여 명령 프롬프트에서 명령어를 이용한다.

마지막으로 NCP에서 제공하는 API를 이용하여 Opreration 할 수 있다.

또한 다양한 서버동작을 위한 기능들이 있다.

### 서버이미지, 스냅샷, 유사서버

---

각각은 이미지를 만들어놓고 손쉽게 나중에 유사 혹은 같은 이미지를 생성하는 기능이다.

Classi 과 VPC 에서 공통적으로 사용할 수 있다.

서버이미지는 서버OS + 추가볼륨을, 스냅샷은 볼륨을, 유사서버는 서버OS를 대상으로 한다.

서버이미지와 스냅샷의 경우 리전간 이미지를 공유한다.

서버 이미지 빌더란?

Packer를 활용하여 내 서버 이미지를 생성하는 서비스를 말한다.

서버 이미지 생성 시, Linux, Windows 모두 패스워드 초기화가 필요하며, Windows의 경우 SID 변경이 필요하다.

![Untitled](https://user-images.githubusercontent.com/84123877/172820690-d483c858-ceb0-4697-9795-ef6a2b4b92bd.png)

### Init Script

---

서버 생성시 실행되는 스크립트를 지정하는 것을 말한다.

Classic과 VPC에서 공통적으로 사용할 수 있다.

서버 생성시 최초 1회에 한하여 실행한다.

보통 같은 용도 서버를 여러 대 일괄로 생성할 경우 많이 사용한다.

Init Script 로 할 수 있는 것들 : 패스워드 초기화, NAS 마운트, 프로그램 설치 및 설정

## ACG (Access Control Group)

---

서버 방화벽 역할을 한다.

Default ACG와 Custom ACG로 구분된다.

Classic 과 VPC 에서 공통적으로 사용할 수 있다.

프로토콜은 TCP,UDP,ICMP 중 선택할 수 있고, 접근 소스는 IP(CIDR), ACG Group 설정이 가능하다.

Classic의 경우 계정당 최대 100개의 ACG, VPC는 VPC당 500개

적용대상은 클래식은 서버, VPC는 서버 NIC

적용 ACG 개수는 클래식은 5개, VPC는 NIC 당 3개

클래식의 경우 인바운드만 가능하지만 VPC는 인바운드, 아웃바운드 둘 다 설정 가능하다.

### 추가스토리지 구성

---

마지막으로 추가스토리지 구성이 가능하다.

Classic과 VPC에서 공통적으로 사용할 수 있다.

OS영역인 50GB에 추가로 더 큰 로컬 스토리지 용량이 필요한 경우 사용한다.

스토리지당 10G ~ 2T 까지 생성할 수 있다.

단일서버에 최대 15개의 추가 스토리지가 가능하고 기존 OS까지 포함하면 총 16개가 된다.

![Untitled 1](https://user-images.githubusercontent.com/84123877/172820699-7f851e89-d860-4f24-bed4-e4317929897e.png)

---
