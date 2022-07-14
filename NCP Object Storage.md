# Object Storage

AWS의 Cloudwatch에 대응되는 서비스가 NCP Monitoring 이라면,

AWS의 S3에 대응되는 서비스는 Object Storage이다.

Object Storate는 인터넷상에서 여러 사용자가 원하는 데이터를 저장하고

공유할 수 있도록 오브젝트 형태로 저장되는 스토리지이다.

사용량을 예측하기 어려운 서비스에 효율적으로 대응하며(S3와 같다)

데이터 저장공간을 GB단위에서 PB단위까지 확장 가능한 대용량 저장소로도 사용 가능하다.

## Object Storage 특징

---

1. **데이터 무결성 및 복원력 보장**
= HTTPS를 통해 데이터가 암호화되어 있으며, 여러 단계의 보안 장비를 비롯해
데이터 유실 방지에 초점을 맞춰 설계된 시스템이 데이터 내구성 및 복원력 보장

1. **초대용량 데이터 저장 가능**
= 데이터 저장 공간을 사업 규모에 따라 GB 단위에서 PB 단위까지 확장할 수 있어
비즈니스 민첩성과 유연성을 향상할 수 있다.

1. **콘솔을 통한 데이터 저장**
= 네이버 클라우드 플랫폼의 콘솔을 통해 오브젝트 스토리지에 데이터를 직접
저장하거나 Restful API로 서버와 오브젝트 스토리지를 연결하여 데이터를 저장
및 활용할 수 있다.

1. **우수한 데이터 검색**
= 오브젝트 스토리지는 데이터를 오브젝트 단위로 저장하며 오브젝트 별로 고유
식별자와 메타데이터를 부여한다.

## Object Storage 시작

---

Object Storage는 이용신청이 필요하므로 NCP 콘솔 창에서 이용 신청을 진행한다.

![Untitled](https://user-images.githubusercontent.com/84123877/178858730-e4bfb222-f2de-462c-89c9-241870fb09e7.png)

> 콘솔창에서 Object Storage를 선택한다.
> 

![Untitled 1](https://user-images.githubusercontent.com/84123877/178858711-cc854aeb-182d-457a-ab80-d9c3532f6c2d.png)

> 안내사항 확인 후 이용을 신청한다.
> 

### 버킷 생성하기

Objcet Storage를 실제 사용하기 위해서는 기본적으로 스토리지의 정책이나 권한

등의 설정을 담고 있는 단위인 “버킷”을 먼저 생성해야 한다.

![Untitled 2](https://user-images.githubusercontent.com/84123877/178858716-3c1f3172-6631-4283-aa3f-02ec4e91e4e7.png)

> 버킷 생성을 선택한다.
> 

![Untitled 3](https://user-images.githubusercontent.com/84123877/178858717-be5907e1-aecf-448d-9a5c-b808666ffd79.png)

> 버킷의 이름을 설정한다. (본인은 ’cwncpcool’ 로 생성하였다.)
* 생성된 버킷의 이름은 변경 불가, 버킷 이름은 객체에 대한 도메인에 
활용되므로 신중하게 선택한다.

* 버킷 이름은 네이버 클라우드 플랫폼 리전 내에서 유일해야한다.
> 

이후 버킷의 공개 여부를 선택한다.

버킷 내 파일/폴더 리스트만 공개, 파일에 대한 공개 여부는 개별 파일에서 설정한다.

![Untitled 4](https://user-images.githubusercontent.com/84123877/178858718-14fa2c8e-0456-468c-99ec-ef7473b3f324.png)

> 버킷을 NCP의 다른 계정에 공유할 수 있다.
버킷에 대한 목록 조회, 업로드, ACL 조회, ACL 수정 권환 중 일부/전부 를 선택하여 부여 가능
> 

이후 최종 확인 후 버킷을 생성한다.

### 파일 업로드/다운로드

![Untitled 5](https://user-images.githubusercontent.com/84123877/178858720-22b824fe-f4c2-4b14-8333-b751e44ec127.png)

> 파일 업로드할 버킷을 지정 후 해당 버킷에 파일을 업로드
> 

콘솔을 이용한 업로드의 경우 최대 파일 크기는 2GB이며, API를 사용하면 5TB까지 지원한다.

파일에 대한 권한을 부여할 경우, 파일 올리기 설정에서 설정하면 편리하게 동일한 권한을 부여 가능

![Untitled 6](https://user-images.githubusercontent.com/84123877/178858721-ea3e57cd-2dfd-47c2-977f-a3555253818e.png)

> 파일을 단독 선택하면 파일에 대한 상세 정보를 확인 가능
> 

파일을 선택하면 다운로드 버튼이 활성화된다.

### API 인증키

API를 통해 Object Storage를 이용할 경우 업로드 파일 용량을 5TB까지 지원할 수 있다.

API 인증 키는 마이페이지 > 계정관리 > 인증키 관리 메뉴에서 만들 수 있다.

![Untitled 7](https://user-images.githubusercontent.com/84123877/178858722-5240a51f-87ac-4d7e-9599-b7d5853126a4.png)

> 인증키 관리를 선택한다.
> 

![Untitled 8](https://user-images.githubusercontent.com/84123877/178858724-9657aa3e-bd95-4ae7-a3c1-89ba064250a0.png)

> 신규 API 인증키 생성을 선택한다.
> 

API 인증키는 계정당 2개까지 생성 가능하다.

### *활용팁*

Object Storage의 API는 Amazon S3와 완벽 호환되므로, 

S3를 사용하는 프로그램을 Object Storage에서도 그대로 사용할 수 있다.

1. 최신 버전의 “S3 Browser”를 다운로드하여 설치한다.

[Download S3 Browser](https://s3browser.com/download.aspx)

1. S3 Browser를 실행하고 Menu → Account → Add New Account에서 다음과 깉이 설정한다.

![Untitled 9](https://user-images.githubusercontent.com/84123877/178858726-a89d9d5f-f050-4d73-a7ac-40d98b9d8619.png)

- Account Type: S3 Compatible Storage
- REST Endpoint: kr.object.ncloudstorage.com
- Access Key ID : access key
- Secret Access Key : 위 API 인증키와 연결된 secret key를 입력한다.
- use secure transfer(SSL/TLS): 선택

1. Task 탭에서 정상적으로 연결이 되는지 확인한다.

![Untitled 10](https://user-images.githubusercontent.com/84123877/178858728-186e593b-3b08-4b81-b484-759a3ee6822d.png)

> NCP 계정연동 완료
> 

버킷 생성/삭제, 파일 업로드/다운로드, 폴더 생성/삭제 가 가능하다.

권한 부여는 네이버 클라우드 콘솔 및 관련 API로 제어하는 것을 권장한다.

(각 기능 실습 이미지는 미첨부하였다. 간단하므로 직접 해보세용)

### 사용요금

Object Storage 요금은 데이터 저장량 요금 + API 요청 수 요금 + 네트워크 전송 요금
으로 구성되어 있다.

- 데이터 저장량 요금 
: 고객의 파일이 실제로 Object Storage에 저장된 데이터 저장량과 저장 시간에 따른 요금
- API 요청 수 요금 
: Object Storage를 사용하기 위한 목록 조회, 업로드, 다운로드 요청 등의 API 요청에 따른 요금
- 네트워크 전송 요금
: 파일 다운로드에 따른 요금

<aside>
💡 Object Storage와 CDN+ Gloabal CDN 상품 간에 발생하는 
네트워크 전송 요금은 무 과금 처리된다.

</aside>

---
