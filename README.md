<div align="center">

# ☁️ Naver Cloud Platform 프로젝트

### Naver Cloud 기반 인프라 및 웹 서비스 구축

<br>

![Naver Cloud](https://img.shields.io/badge/Naver_Cloud-03C75A?style=for-the-badge&logo=naver&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=flask&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)

</div>

<br>

> 📅 2026년 6월 24일 현재 공개된 티스토리 게시물을 기준으로 정리했습니다.

<br>

---

## 🛒 1. 신규 쇼핑몰 인프라 구축 프로젝트

신규 쇼핑몰 서비스를 운영하기 위해 Naver Cloud Platform에 Web, WAS, DB가 분리된 3-Tier 인프라를 구축하고, Flask 기반의 간단한 쇼핑몰 웹 애플리케이션을 구현한 프로젝트입니다.

<br>

<div align="center">

![Naver Cloud](https://img.shields.io/badge/Naver_Cloud-03C75A?style=flat-square&logo=naver&logoColor=white)
![Rocky Linux](https://img.shields.io/badge/Rocky_Linux-10B981?style=flat-square&logo=rockylinux&logoColor=white)
![Apache](https://img.shields.io/badge/Apache-D22128?style=flat-square&logo=apache&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-000000?style=flat-square&logo=flask&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)

</div>

### ✨ 주요 기능

- 외부 접속이 필요한 서버와 내부에서만 사용하는 서버를 분리하여 네트워크를 구성했습니다.
- 사용자 요청이 Web Server, Flask WAS, MySQL DB 순서로 전달되도록 3-Tier 환경을 구축했습니다.
- 여러 서버에 사용자 요청을 분산하기 위해 ALB와 NLB를 적용했습니다.
- 외부에 공개되지 않은 내부 서버도 인터넷을 사용할 수 있도록 NAT Gateway를 구성했습니다.
- 관리자가 내부 서버에 안전하게 접속할 수 있도록 SSL VPN과 SSH 접속 환경을 설정했습니다.
- Apache가 사용자 요청을 Flask 애플리케이션으로 전달하도록 Reverse Proxy를 설정했습니다.
- 서버가 재부팅되어도 Flask 애플리케이션이 자동으로 실행되도록 systemd 서비스를 등록했습니다.
- 서버 저장 공간을 확장하기 위해 추가 Block Storage를 연결하고 자동 마운트를 설정했습니다.
- Flask와 Jinja 템플릿을 이용해 상품 목록을 보여주는 간단한 쇼핑몰 화면을 구현했습니다.

### 🛠️ 사용 기술

- **Cloud:** Naver Cloud Platform
- **Backend:** Python, Flask, Jinja
- **Web·DB:** Apache, MySQL
- **Infrastructure:** Rocky Linux, systemd, SSH

<br>

---

## 🖼️ 2. 이미지 변환 웹 서비스 프로젝트

사용자가 업로드한 이미지를 원하는 규격으로 변환하고, 사용자별 이미지 변환 이력까지 관리할 수 있도록 구현한 Naver Cloud Platform 기반 웹 서비스입니다.

<br>

<div align="center">

![Naver Cloud](https://img.shields.io/badge/Naver_Cloud-03C75A?style=flat-square&logo=naver&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-000000?style=flat-square&logo=flask&logoColor=white)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![HyperCLOVA X](https://img.shields.io/badge/HyperCLOVA_X-7B61FF?style=flat-square)

</div>

### ✨ 주요 기능

- Flask 웹 페이지에서 이미지를 업로드하고 변환 결과를 확인할 수 있도록 구현했습니다.
- 업로드된 원본 이미지를 NCP Object Storage에 저장했습니다.
- Image Optimizer와 Global Edge를 이용해 변환된 이미지를 제공했습니다.
- 회원가입과 로그인 기능을 구현하고 비밀번호를 해시하여 저장했습니다.
- 사용자별 이미지 업로드 및 변환 이력을 관리할 수 있도록 구현했습니다.
- MySQL에 사용자 정보와 이미지 메타데이터를 저장했습니다.
- Cloud Insight를 이용해 서버 상태를 모니터링하고 이벤트 알림을 설정했습니다.
- HyperCLOVA X를 연동해 사용자 질문에 응답하는 챗봇 기능을 구현했습니다.
- Object Storage Lifecycle과 Cloud Functions를 이용해 이미지 삭제와 데이터베이스 상태 동기화를 자동화했습니다.

### 🛠️ 사용 기술

- **Cloud:** Naver Cloud Platform
- **Backend:** Python, Flask
- **Frontend:** HTML, CSS, JavaScript
- **Database:** MySQL
- **AI:** HyperCLOVA X

<br>

---

<div align="center">

☁️ **Naver Cloud Project**

</div>
