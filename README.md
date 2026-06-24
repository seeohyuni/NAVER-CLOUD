
# Naver Cloud 프로젝트

### 📌 프로젝트 기록

프로젝트 진행 과정과 구현 내용은 아래 티스토리 게시물에 정리했습니다.
- [NAVER-CLOUD 프로젝트 정리](https://mystory21594.tistory.com/)

---

### 1. 신규 쇼핑몰 인프라 구축 프로젝트

신규 쇼핑몰 서비스를 운영하기 위해 Naver Cloud를 사용하여 Web, WAS, DB가 분리된 3-Tier 인프라를 구축 및 Flask 기반의 간단한 쇼핑몰 웹 구현

### [ System Architecture ]

<p align="center"> <img src="E-shop_3-Tier.png" alt="신규 쇼핑몰 프로젝트" width="400"> </p>

#### ✨ 주요 기능

- 외부 접속이 필요한 서버와 내부에서만 사용하는 서버를 분리하여 네트워크 구성
- 사용자 요청이 Web Server, Flask WAS, MySQL DB 순서로 전달되도록 3-Tier 환경 구축
- 여러 서버에 사용자 요청을 분산하기 위해 ALB와 NLB 적용
- 외부에 공개되지 않은 내부 서버도 인터넷을 사용할 수 있도록 NAT Gateway 구성
- 관리자가 내부 서버에 안전하게 접속할 수 있도록 SSL VPN과 SSH 접속 환경 설정
- Apache가 사용자 요청을 Flask 애플리케이션으로 전달하도록 Reverse Proxy 설정
- 서버가 재부팅되어도 Flask 애플리케이션이 자동으로 실행되도록 systemd 서비스 등록
- 서버 저장 공간을 확장하기 위해 추가 Block Storage를 연결하고 자동 마운트 설정
- Flask와 Jinja 템플릿을 이용해 상품 목록을 보여주는 간단한 쇼핑몰 화면 구현

#### 🛠️ 사용 기술

- **Cloud:** Naver Cloud Platform
- **Backend:** Python, Flask, Jinja
- **Web·DB:** Apache, MySQL
- **Infrastructure:** Rocky Linux, systemd, SSH

#### 🟥 진행 중 문제 사항 및 해결 과정
- Web-WAS 연동 문제
  - Apache에서 받은 요청이 Flask까지 정상적으로 전달되지 않음
  - ALB와 NLB의 Target Group 및 Health Check를 설정하고, Apache에 ProxyPass와 ProxyPassReverse를 적용한 다음 연결 상태 확인

- CSS 502 오류
  - 정적 파일 요청까지 Flask WAS로 전달되면서 CSS가 정상적으로 적용되지 않음
  - static 요청은 Apache가 직접 처리하도록 ProxyPass 제외 설정과 Alias를 추가

- 서비스 및 스토리지 유지 문제
  - 서버 재부팅 후 Flask 애플리케이션이 종료되고 추가 스토리지의 마운트 해제
  - Flask를 systemd 서비스로 등록하고, 추가 스토리지를 등록해 자동 실행과 자동 마운트를 설정

---

### 2. 이미지 변환 웹 서비스 프로젝트

사용자가 업로드한 이미지를 인스타 스토리 규격으로 변환하고, 사용자별 이미지 변환 이력까지 관리하고 챗봇으로 해시태그 제

### [ System Architecture ]

<p align="center"> <img src="Image-Conversion.png" alt="이미지 변환 프로젝트" width="700"> </p>

#### ✨ 주요 기능

- Flask 웹 페이지에서 이미지를 업로드하고 변환 결과를 확인할 수 있도록 구현
- 업로드된 원본 이미지를 NCP Object Storage에 저장
- Image Optimizer와 Global Edge를 이용해 변환된 이미지를 제공
- 회원가입과 로그인 기능을 구현하고 비밀번호를 해시하여 저장
- 사용자별 이미지 업로드 및 변환 이력을 관리할 수 있도록 구현
- MySQL에 사용자 정보와 이미지 메타데이터를 저장
- Cloud Insight를 이용해 서버 상태를 모니터링하고 이벤트 알림 설정
- HyperCLOVA X를 연동해 사용자 질문에 응답하는 챗봇 기능 구현
- Object Storage Lifecycle과 Cloud Functions를 이용해 이미지 삭제와 데이터베이스 상태 동기화 자동화

#### 🛠️ 사용 기술

- **Cloud:** Naver Cloud Platform
- **Backend:** Python, Flask
- **Frontend:** HTML, CSS, JavaScript
- **Database:** MySQL
- **AI:** HyperCLOVA X

#### 🟥 진행 중 문제 사항 및 해결 과정
- Cloud Insight 메트릭 경고
  - 이벤트 규칙 설정 중 일부 서버에 선택한 메트릭이 존재하지 않는다는 안내 표시
  - 서버 설정에서 상세 모니터링을 활성화하여 필요한 CPU, 메모리, 디스크 메트릭을 수집하도록 해결

- Object Storage와 DB 상태 불일치
  - Lifecycle 설정으로 이미지가 삭제되어도 DB에는 이미지 이력이 남아 있는 문제 확인 
  - metadata 테이블에 상태 컬럼을 추가하고, Object Storage에서 파일 존재 여부를 확인하여 삭제된 파일은 deleted 상태로 변경하고, 이력 화면에서도 삭제된 이미지로 표시하도록 수정

#### ✅ 최종 웹사이트 

<p align="center"> <img src="Image-Conversion-final1.png" alt="최종 웹사이트1" width="700"> </p>

<p align="center"> <img src="Image-Conversion-final2.png" alt="최종 웹사이트2" width="600"> </p>
