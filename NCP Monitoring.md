# Monitoring

---

AWS 의 리소스 상태 모니터링 기능인 Cloudwatch를 학습했었는데,

NCP를 공부하면서 이와 같은 기능을 가지고 있는 서비스가 있을까 찾아보니

컴퓨팅 자원 상태 모니터링 및 이벤트 발생 시 통보까지 하는 

**NCP Monitoring** 기능이 있었다.

리소스 상태 모니터링 뿐만 아니라

Web service Monitoring, Network Traffic Monitoring, Security Monitoring 등

여러 기능들에 대한 상태 모니터링 서비스가 각각 구비되어 있는 듯 했다.

나는 AWS Cloudwatch와 대응되는 Monitoring 서비스로 

NCP Server의 CPU 사용률을 모니터링하여, 일정 수치가 넘게되면

이메일로 경고알람을 전송하는 실습을 진행하겠다.

## Monitoring 특징

---

1. **컴퓨팅 자원의 안정적인 운영 가능**
: 기본 모니터링 기능을 통해 CPU 사용률, 디스크 사용률, 메모리 사용률 등 
시스템 관련 지표를 확인할 수 있다. 이벤트 설정, 컴퓨팅 자원별 비교 등 상세 모니터링
기능도 활용 가능하다.

1. **다양한 정보 수집 및 세분화된 설정 항목**
: 8개 분류 내 36개의 세부 항목에 대한 모니터링 성능 정보를 수집하고
12개 분류 내 57개의 세부 항목과 관련된 이벤트 경보를 설정할 수 있다.
이를 통해 보다 세밀한 모니터링이 가능하다.

1. **그래프 및 통계 활용**
: REStful API 방식의 HTTP GET/POST 메소드를 통해 모니터링 데이터를 다양한 형태로
활용할 수 있다. 사용자가 직접 API를 활용하여 실시간 데이터를 수집하기너,
일단위에 통계 데이터를 분석할 수 있어 비즈니스 목적에 맞게 활용 가능하다.

1. **다양한 서비스에 대한 모니터링**
: Server, Auto Scaling 등 네이버 클라우드 플랫폼에서 제공하는 다양한 서비스의 컴퓨팅 
자원 상태를 살필 수 있다.

1. **사용자 맞춤형 모니터링**
: 사용자가 원하는 형태로 차트와 대시보드를 직접 생성하여 운영할 수 있다.
또한, 서버를 그룹별로 분류하여 모니터링하는 기능을 사용 가능하다.

1. **손쉬운 이벤트 설정**
: 몇 번의 클릭만으로 간편하게 이벤트와 관련된 다양한 설정을 할 수 있는
플랫폼을 제공한다.

![Untitled](https://user-images.githubusercontent.com/84123877/176134364-e77600e0-c428-404e-b500-a793bf0757bd.png)

> 상세기능 | 모니터링 항목 및 주기 설정이다.
> 

## Monitoring 설정 및 알람 전송 실습

---

![Untitled 1](https://user-images.githubusercontent.com/84123877/176134324-bbdd96e4-56f1-4ff6-ae52-a760cfd10ce2.png)

> Monitoring 실습 전용 서버를 하나 생성하였다. (Ubuntu Linux)
> 

![Untitled 2](https://user-images.githubusercontent.com/84123877/176134332-27973c47-9b04-4c71-950d-78e490cd8851.png)

> 상태가 운영중인 서버 상단에 모니터링을 선택한다.
> 

![Untitled 3](https://user-images.githubusercontent.com/84123877/176134337-c22ff1b8-23a1-4bab-be50-e2c3982a36c6.png)

> 서버 기본 모니터링 화면이 출력된다.
기본적으로 CPU 사용률, 네트워크 트래픽, 메모리 사용률, 스왑메모리 사용률, 디스크 사용률,
디스크 I/O 가 표시된다.
> 

<aside>
💡 Server 말고도 로드밸런서도 모니터링이 가능하다.
기본적으로 현재 접속자수, 초당 접속자, 트래픽을 확인할 수 있다.

</aside>

![Untitled 4](https://user-images.githubusercontent.com/84123877/176134338-b8f22a5e-f390-4f92-ba8f-eab804e04654.png)

> 로드밸런서 기본 모니터링 화면
> 

### 통보대상 설정

이벤트 발생 시 통보를 받기 위한 사용자 정보를 설정한다.

![Untitled 5](https://user-images.githubusercontent.com/84123877/176134340-8f6a16c5-6d75-4bc1-bbbe-24ceb9c89df8.png)

> 기본적으로 계정의 본인 확인된 이메일이 생성되어 있다.
NCP 콘솔에서 Mangement → Monitoring → Notification Recipient 항목으로 이동한다.
대상자 추가 버튼을 선택한다.
> 
> 
![Untitled 6](https://user-images.githubusercontent.com/84123877/176134342-6cd3639d-4f18-436f-b36a-0b85660ebd2c.png)

> 대상자 이름, 연락받을 이메일, 휴대폰 번호를 입력한 후 “등록”을 선택한다.
> 

![Untitled 7](https://user-images.githubusercontent.com/84123877/176134345-4598f689-9516-4623-9c78-a3a3eb5343e4.png)

> 대상자가 추가된 것을 확인할 수 있다.
> 

![Untitled 8](https://user-images.githubusercontent.com/84123877/176134347-8a29bf19-255f-42a8-9db6-9aedb29b9080.png)

> 서버 상세 모니터링을 사용하기 위해 콘솔의 Server 항목에서
대상 서버를 선택하고 마우스 오른쪽 버튼을 클릭한다.
”상세 모니터링 설정 변경” 을 선택한다.
> 

![Untitled 9](https://user-images.githubusercontent.com/84123877/176134350-81300fa0-74a2-4543-a43c-18c6fe64ea95.png)

![Untitled 10](https://user-images.githubusercontent.com/84123877/176134353-007ba705-fd22-46dc-a6b4-22a5a9d037bf.png)

> 상세 모니터링 신청 후 이벤트 알람을 설정하겠다.
콘솔화면에서 Monitoring → Configureation → New Observation 을 선택한다.
서버를 선택한 뒤 ”감시 설정”을 선택한다.
(사진에서는 서버 이미지가 안보인다. 서버 이미지를 생성하고 진행하여야 한다. )
> 

![Untitled 11](https://user-images.githubusercontent.com/84123877/176134355-5d88dafb-0088-4f75-aab1-8af1175fcfdc.png)

> 서버의 CPU 사용률 임계치를 30%로 설정하였다.
> 

![Untitled 12](https://user-images.githubusercontent.com/84123877/176134358-038f3594-87a5-4945-866c-76d5eecebe09.png)

> 알람을 보내는 목적지이다. AWS랑 다르게 SMS도 추가할 수 있다.
> 

![Untitled 13](https://user-images.githubusercontent.com/84123877/176134360-68b20b3d-64d2-42b0-85a2-46f1ada58831.png)

![Untitled 14](https://user-images.githubusercontent.com/84123877/176134361-62ae048a-408a-4758-9599-dfe63eabf1a2.png)

> CPU 사용률이 임계치를 넘어서니 알람 메일이 전송되었다.
> 

---
