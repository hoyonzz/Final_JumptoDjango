# **Pybo: Django 기반 게시판 프로젝트**

[![Python](https://img.shields.io/badge/Python-3.12-blue?logo=python&logoColor=white)](https://www.python.org) [![Django](https://img.shields.io/badge/Django-5.2-green?logo=django&logoColor=white)](https://www.djangoproject.com/) [![PostgreSQL](https://img.shields.io/badge/PostgreSQL-blue?logo=postgresql&logoColor=white)](https://www.postgresql.org/) [![AWS](https://img.shields.io/badge/AWS%20Lightsail-orange?logo=amazon-aws&logoColor=white)](https://aws.amazon.com/lightsail/)

'점프 투 장고' 교재를 기반으로 기초부터 실전 배포까지 체계적으로 학습하며 구축한 게시판 웹 애플리 케이션입니다. 실무적인 프로젝트 설계와 End-to-End 배포 프로세스까지 직접 경험한 백엔드 프로젝트입니다.

**🚀 배포된 웹사이트 URL:** `http://13.209.106.188`

## ✨ 주요 기능

*   **사용자 시스템:**
    *   일반 회원가입, 로그인, 로그아웃 (`django.contrib.auth`)
    *   Google 소셜 로그인 (`django-allauth`)
    *   사용자 프로필(자기소개, 생년월일, 프로필 사진) 조회 및 수정
*   **게시판 (CRUD):**
    *   **계층 구조:** 질문 - 답변 - 댓글의 3단계 계층 구조 구현
    *   **CRUD:** 질문, 답변, 댓글에 대한 생성(Create), 조회(Read), 수정(Update), 삭제(Delete) 기능
    *   **권한 관리:** 작성자 본인만 게시물을 수정/삭제할 수 있는 권한 제어 로직 구현
*   **상호작용 기능:**
    *   **추천:** 질문과 답변에 대한 추천 기능 (`ManyToManyField` 활용)
    *   **조회수:** IP 주소 기반 중복 방지 조회수 기능 구현
*   **편의 기능:**
    *   **카테고리:** 게시물 카테고리별 분류 및 조회 기능
    *   **검색 및 정렬:** 키워드 검색(`Q` 객체) 및 최신순/추천순/인기순 정렬(`annotate`) 기능
    *   **페이지네이션:** 질문 및 답변 목록 페이지네이션 기능 (`Paginator` 활용)
    *   **서식:** `Markdown`을 활용한 게시물 서식 적용

## 💡 핵심 경험 및 기술적 특징

### **1. 실무 지향적 프로젝트 구조 설계**
단일 파일에 모든 코드를 작성하는 방식을 지양하고, 프로젝트의 유지보수성과 확장성을 최우선으로 고려하여 설계했습니다.
*   **환경 분리:** `settings.py`를 `base`, `local`(개발), `prod`(운영)으로 분리하고 `python-dotenv`를 활용하여 민감 정보를 안전하게 관리했습니다.
*   **앱 분리:** 사용자(`common`)와 게시판(`pybo`) 앱을 분리하여 각 앱의 독립성을 확보했습니다.
*   **View 모듈화:** `views.py`를 `question_views`, `answer_views` 등 기능 단위로 모듈화하여 코드의 가독성과 관리 효율을 극대화했습니다.

### **2. Django Signals를 이용한 프로필 자동 생성**
Django의 `post_save` 시그널을 활용하여, 새로운 `User`가 생성될 때마다 해당 유저와 1:1로 연결된 `Profile` 객체가 **자동으로 생성**되도록 구현했습니다. 이를 통해 모델 간의 결합도를 낮추고 비즈니스 로직을 자동화하는 경험을 쌓았습니다.

### **3. IP 기반의 정교한 조회수 기능 구현**
단순히 카운트를 증가시키는 방식을 넘어, 별도의 `QuestionView` 모델을 설계하여 사용자의 IP 주소를 기록함으로써 **동일한 사용자에 의한 중복 조회수 증가를 방지**하는 정교한 로직을 구현했습니다.

### **4. 개발부터 배포까지, 전체 파이프라인 경험**
로컬 환경에서의 개발로 끝나지 않고, 사용자가 실제 접속할 수 있는 서비스를 직접 배포하며 전체 인프라 구축 과정을 경험했습니다.
*   **Cloud:** AWS Lightsail을 사용하여 가상 서버를 구축했습니다.
*   **Infra:** `Gunicorn`(WSGI)과 `Nginx`(Web Server)를 연동하여 정적/동적 요청을 효율적으로 처리하는 안정적인 서비스 환경을 구성했습니다.
*   **Database:** `PostgreSQL`을 도입하여 운영 데이터베이스를 관리했습니다.
*   **Logging:** 운영 환경에서의 에러 추적 및 분석을 위해 Django의 로깅 시스템을 커스터마이징하여 파일 기반의 로그를 기록하도록 구현했습니다.

## 🛠️ 기술 스택

*   **Backend:** Python, Django
*   **Database:** PostgreSQL, SQLite
*   **Infra & Deployment:** AWS Lightsail, Gunicorn, Nginx
*   **Frontend:** HTML, CSS, Bootstrap, JavaScript
*   **Libraries:** django-allauth, Pillow, python-dotenv, markdown2
*   **Version Control:** Git, GitHub

## 🚀 시작하기 (로컬 개발 환경)

```bash
# 1. 프로젝트 복제
git clone https://github.com/hoyonzz/Final_JumptoDjango.git
cd Final_JumptoDjango

# 2. 가상환경 생성 및 활성화
python -m venv venv
source venv/Scripts/activate

# 3. 의존성 설치
pip install -r requirements.txt

# 4. .env 파일 설정 (루트 디렉토리에 생성)
# SECRET_KEY=your_secret_key
# DATABASE_PASSWORD=your_db_password

# 5. 데이터베이스 마이그레이션
python manage.py migrate

# 6. 개발 서버 실행
python manage.py runserver
```
