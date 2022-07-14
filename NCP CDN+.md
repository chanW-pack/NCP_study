# NCP CDN+

---

AWS에서의 CDN 서비스는 CloudFront이고,
NCP에서는 CDN+라는 이름으로 서비스되고 있다.

AWS에서의 실습에서는 S3를 생성 후 이를 배포하는 형식으로 진행하였는데
이처럼 NCP에서도 오브젝트 스토리지를 생성하여 이를 CDN+로 배포하는 실습을 진행하겠다.

## CDN+ 란?

---

**CDN+는 NCP의 CDN 서비스**로,
여러 사용자에게 콘텐츠를 빠르고 안전하게 전달하는 서비스이다.

**강화된 콘텐츠 전달 속도**와 **안정성**을 가자고 있어, 다양한 콘텐츠를 지**리적 제한 없이
빠르게 전송**하거나 끊김 없이 스트리밍하고 **안전하게 다운로드**하는데 최적이다.

### CDN 특징

- **콘텐츠별 웹 캐싱 및 다운로드**
: 이미지, 영상 등 여러 종류의 콘텐츠에 대한 웹 캐싱과 다운로드 서비스를 제공한다.
- **간단한 신청과 활용**
: 웹 기반 콘솔에서 CDN 서비스를 생성하고 설정할 수 있다.
- **타서비스와 연동 가능**
: NCP에서 제공하는 Object Storage, Server를 원본 서버로 설정할 수 있고, 
Live Station의 경우 CDN과 자동으로 연계되어 생중계 서비스가 가능하다.
- **안정적인 전송과 효율적인 비용 관리** 
: 안정적인 콘텐츠 전송을 보장하며, 대규모 트래픽을 소화할수 있는 서버 플랫폼을
직접 구축할 필요 없이 저렴한 비용으로 활용할 수 있다.

## CDN+ 상세 기능

---

### 1. 콘텐츠 보안 기능

다음과 같은 콘텐츠 보안 기능을 제공하여 안전하게 콘텐츠를 전송한다.

- HTTPS 전송 지원 (SSL 인증서 설정 기능 포함)
- 등록된 도메인 기준 접근 허용 기능
- Secure-Token 기반 보안 URL 생성 기능
- 원본 서버와 HTTPS를 통한 콘텐츠 연동을 지원

### 2. HTTP/2 프로토콜을 활용한 전송 지원

전통적인 웹 표준 프로토콜인 HTTP1.0과 HTTP1.1은 물론 2015 상반기 표준화 IETF에 의해
제정된 HTTP/2 프로토콜을 지원한다.

### 3. 웹 캐싱 및 다운로드 기능

웹 캐싱 및 다운로드와 같은 일반적인 CDN 서비스 속성을 웹 기반의 콘솔에서 간편하게 실행
가능하다. HTTP, HTTPS, HTTP2 프로토콜로 서비스를 제공한다.

### 4. CDN 통계 및 모니터링 기능

CDN 및 원본에 대한 다음 항목을 기본으로 제공한다.
모니터링을 통해 서비스의 전반적인 상태를 쉽게 파악할 수 있다.

- CDN 이용량 (전송량/요청수)
- 요청 수 대비 Hit ratio
- 응답 코드별 통계
- 원본 전송량

### 5. 콘텐츠 별 로그 제공

콘텐츠 요청에 대한 접근 로그를 제공하여 콘텐츠 전송 및 사용 패턴 분석을 지원한다.
추출된 로그는 Object Stoage와 연동되어 주기적으로 자동 저장된다.

### 6. 다양한 원본 서버 지원

HTTP, HTTPS, HTTP2 프로토콜을 통해 다양한 원본 서버와의 콘텐츠 연동 지원

## CDN+ 상세 스펙

---

![Untitled](https://user-images.githubusercontent.com/84123877/178859677-f5f3e19c-3230-465a-b56d-71f0f550645b.png)

## CDN+ 요금 안내

---

![Untitled 1](https://user-images.githubusercontent.com/84123877/178859679-827eb7fc-46d9-473b-870d-d178e8599083.png)


## CDN+ 배포 실습

---

AWS에서 S3를 생성하여 CloudFront로 배포하듯,
NCP에서도 Object Storage를 생성하여 CDN+로 배포 실습을 진행해보겠다.

![Untitled 2](https://user-images.githubusercontent.com/84123877/178859681-159627a3-d1d8-484f-84b3-6f766ba891d7.png)

> Object Storage를 생성하였다. CDN+ 사용을 위해 버킷과 모든 파일 권한을 열어주었다.
> 

![Untitled 3](https://user-images.githubusercontent.com/84123877/178859685-5297f30d-86e2-4594-9a2c-8e183d03916f.png)

> NCP VPC탭에서 CDN+ 서비스를 선택하고 신청을 진행한다.
> 

![Untitled 4](https://user-images.githubusercontent.com/84123877/178859688-a561e281-8303-4ea0-b37f-64da2197b9cf.png)

> 서비스 이름을 입력하고, Object Storage와 연동하기 위해 서비스 프로토콜을 
“HTTPS”로 설정합니다.
> 

![Untitled 5](https://user-images.githubusercontent.com/84123877/178859690-4f1b916d-ff3c-42c5-93df-df99c3594d07.png)

![Untitled 6](https://user-images.githubusercontent.com/84123877/178859691-a54c8700-75ad-4ca7-b67d-135a44364ce8.png)

> 원본 서버를 선택한다. 생성했던 Object Storage를 선택했다.
> 

![Untitled 7](https://user-images.githubusercontent.com/84123877/178859693-a52a0fc1-afa5-42f5-845d-fd211e3ccc7e.png)

> CDN 서비스 캐싱을 설정한다.
> 

Cache Hit률을 높이기 위해 캐싱 설정에서 
'Ignore Query String(쿼리스트링 무시)', 'Remove Vary Header' 설정을 적용하는 것이 좋습니다. 
(자세한 옵션 설명은  [?] 버튼을 클릭하면 자세히 나오므로 도움말을 참고하면 좋다.)

![Untitled 8](https://user-images.githubusercontent.com/84123877/178859695-76c1b080-1827-49c0-9056-69aed8b293f7.png)

> CDN+ 생성이 완료되었다. 상태가 운영중으로 변경될때까지 기다린다.
> 

![Untitled 9](https://user-images.githubusercontent.com/84123877/178859696-6243685a-e01d-42d8-a8c5-cb578f46407f.png)

> CDN URL을 통하여 페이지 호출 완료
> 

CDN 서비스 도메인 + Object Storage의 버킷에 저장된 파일 상태 경로를 호출하면 
위과 같이 Object Storage의 파일을 CDN을 통해서 서비스 할 수 있다.

“CDN 서비스 도메인/index1234.html” 으로 접속하여 index1234.html 페이지가 나타났다.

---
