# **Pybo: Full-Stack Q&A 게시판 (Django)**

### Django 학습의 A to Z: 기획부터 설계, 개발, 배포까지 1인 Full-Cycle 개발 프로젝트

[![Python](https://img.shields.io/badge/Python-3.12-blue?logo=python&logoColor=white)](https://www.python.org) [![Django](https://img.shields.io/badge/Django-5.2-green?logo=django&logoColor=white)](https://www.djangoproject.com/) [![PostgreSQL](https://img.shields.io/badge/PostgreSQL-blue?logo=postgresql&logoColor=white)](https://www.postgresql.org/) [![AWS](https://img.shields.io/badge/AWS%20Lightsail-orange?logo=amazon-aws&logoColor=white)](https://aws.amazon.com/lightsail/)

**`단순히 따라 치는 코딩을 넘어, 모든 개념을 손으로 직접 기록하고 파고들며 Django의 동작 원리를 체화했습니다.`**

본 프로젝트는 '점프 투 장고' 교재를 기반으로, 백엔드 개발의 기초부터 실무적인 배포 프로세스까지 **웹 개발의 전체 사이클(Full-Cycle)을 1인 개발**로 완수한 포트폴리오입니다. 3개월간의 학습 과정을 통해 마주한 모든 기술적 과제와 해결 과정을 `학습 아카이브`에 투명하게 기록하며 완성했습니다.

**🚀 실제 운영 중인 웹사이트:** `http://<신호용님-서버-IP>`  
**(⬆️ 위 링크를 클릭하여 모든 기능을 직접 테스트해보실 수 있습니다.)**

---

## 🎬 주요 기능 시연 (GIF)

프로젝트의 핵심 기능들을 시연 영상으로 준비했습니다.

| 회원가입 및 로그인 | 게시글 CRUD | 답변 및 댓글 기능 |
| :---: | :---: | :---: |
| *(회원가입 GIF)* | *(게시글 CRUD GIF)* | *(답변/댓글 GIF)* |
| **추천 기능** | **검색 및 정렬** | **오류 페이지** |
| *(추천 GIF)* | *(검색/정렬 GIF)* | *(404 스크린샷)* |

---

## 🏛️ 시스템 아키텍처

  
*(멘토 조언: 제공해주신 아키텍처 텍스트를 이미지로 변환하여 삽입하면 가독성이 훨씬 좋아집니다. draw.io 같은 툴을 사용해보세요.)*

---

## 💡 저의 성장과 기술적 강점

### 1. "왜?"를 놓치지 않는 집요한 학습 과정
저는 모든 기술을 '그냥' 사용하지 않았습니다. `view` 함수가 복잡해졌을 때 왜 모듈화가 필요한지, `User` 모델을 왜 직접 상속하지 않고 `Profile` 모델로 확장해야 하는지, `Nginx`와 `Gunicorn`은 어떤 역할을 주고받는지 등 **모든 기술적 선택의 이유를 파고들어 30여 개의 `학습 노트(PDF)`로 기록**했습니다. 이 과정을 통해 단순히 지식을 쌓는 것을 넘어, 문제 해결을 위한 최적의 기술을 선택하고 적용하는 능력을 길렀습니다.

**➡️ [저의 3개월간의 학습 기록 전체 보기 (GitHub 폴더 링크)](./02_Study_Materials/)**

### 2. Full-Stack & DevOps: 웹 개발 전체 사이클 경험
백엔드 개발자를 지망하지만, 서비스 전체의 흐름을 이해하기 위해 **프론트엔드(HTML/CSS/JS), 백엔드(Django), 데이터베이스(PostgreSQL), 인프라(AWS) 및 배포(Nginx/Gunicorn)** 까지 모든 과정을 직접 설계하고 구축했습니다. 이 경험을 통해 각 기술 스택의 역할을 명확히 이해하고, 다른 직무의 동료들과 원활하게 협업할 수 있는 기반을 다졌습니다.

### 3. 실무를 고려한 확장 가능성 있는 설계
미래의 유지보수와 기능 확장을 고려하여 실무적인 설계 원칙을 적용했습니다.
*   **환경 분리:** `settings.py`를 `base`, `local`, `prod`로 분리하고 `.env`를 활용하여 민감 정보를 안전하게 관리합니다.
*   **관심사 분리:** 사용자(`common`)와 게시판(`pybo`) 앱을 분리하고, `views.py`를 기능 단위로 모듈화하여 코드의 응집도를 높였습니다.
*   **자동화:** Django `Signals`를 활용하여 `User` 생성 시 `Profile`이 자동으로 생성되도록 구현, 모델 간의 결합도를 낮추고 반복적인 로직을 자동화했습니다.

### 4. IP 기반의 정교한 조회수 기능 구현
단순히 카운트를 증가시키는 방식을 넘어, 별도의 `QuestionView` 모델을 설계하여 사용자의 `IP` 주소를 기록함으로써 **동일한 사용자에 의한 중복 조회수 증가를 방지**하는 정교한 로직을 직접 설계하고 구현했습니다.

---

## 🛠️ 기술 스택

*   **Backend:** Python 3.12, Django 5.2
*   **Database:** PostgreSQL (AWS RDS), SQLite3
*   **Infrastructure:** AWS Lightsail, Nginx, Gunicorn
*   **Frontend:** HTML5, CSS3, JavaScript, Bootstrap 5
*   **Libraries:** django-allauth, Pillow, python-dotenv, markdown2
*   **Version Control:** Git, GitHub
*   **Development Tools:** VS Code, MobaXterm, pgAdmin

---

## 🗂️ 프로젝트 구조

```
JumpToDjango_Portfolio/
├── 01_Learning_Archive/  # 단계별 학습 과정 코드
├── 02_Study_Materials/   # 주제별 학습 노트 (PDF)
├── 03_Final_Project/     # 최종 배포 프로젝트 소스코드
├── 04_Portfolio_Materials/ # README 및 포트폴리오 자료
└── 05_Deployment_Config/ # Nginx, Gunicorn 등 배포 설정 파일
```

---

## 🚀 로컬 환경에서 실행하기

```bash
# 1. 최종 프로젝트 코드 디렉토리로 이동
cd 03_Final_Project

# 2. 가상환경 생성 및 활성화
python -m venv venv
source venv/Scripts/activate

# 3. 의존성 설치
pip install -r requirements.txt

# 4. .env 파일 설정 (03_Final_Project 루트에 생성)
# SECRET_KEY='your_secret_key'
# ... (기타 필요한 환경 변수)

# 5. 데이터베이스 마이그레이션
python manage.py migrate

# 6. 개발 서버 실행
python manage.py runserver --settings=config.settings.local
```
