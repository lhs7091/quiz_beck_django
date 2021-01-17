## Django 설치 및 코드작성

 - venv 설치
   - python3 -m venv venv
   - ls (venv 폴더 생성 확인) 
 - venv 활성화
   - source venv/bin/activate
 - Django, djangorestframework 설치
   - pip install django djangorestframework
 - django project 생성
   - django-admin startproject myapi .
 - App 생성
   - python manage.py startapp quiz

 - vscode open

 - settings.py
   - ALLOWED_HOSTS = ['*'] // 모두허용
   - TIME_ZONE = 'Asia/Seoul'
   - STATIC_ROOT = os.path.join(BASE_DIR, 'staticfiles') // 제일 마지막에 추가(정적파일관리)
   - INSTALLED_APPS = ['quiz','rest_framework',] // 추가

 - django migration
   - python manage.py makemigrations
   - python manage.py migrate
 - 기동
   - python manage.py runserver

 - 관리자계정 생성
   - python manage.py createsuperuser

 - models.py 작성
 - serializers.py 작성// serializer는 장고 모델 데이트럴 json 타입으로 바꿔주는 직렬화 기능
 - view.py 작성

## Django 배포(heroku)

 - package 설치
   - pip install django-cors-headers gunicorn psycopg2-binary whitenoise dj-database-url
     - django-cors-headers : cors 에러 방지
     - gunicorn : 배포
     - psycopg2-binary : heroku에서 사용하는 DB postgressql을 위함
     - white noise : 정적 파일의 사용을 돕는 미들웨어
 - settings.py
   - SECRET_KEY = os.environ.get('DJANGO_SECRET_KEY', 'key value')
     - DEBUG = False
     - MIDDLEWARE = ['whitenoise.middleware.WhiteNoiseMiddleware'] 추가
     - db_from_env = dj_database_url.config(conn_max_age=500)  
       DATABASES['default'].update(db_from_env) // databases 하단 추가
 - Procfile 추가
 - runtime.txt 추가
 - .gitignore 추가

 - heroku CLI 환경 설치
   - brew install heroku/brew/heroku
 - heroku 로그인
   - heroku login
 - pjt 생성
   - heroku create drf-quiz-test(pjt name)
 - git 추가
   - git push heroku main
 - maigration
   - heroku run python manage.py migrate
 - super user 생성
   - heroku run python manage.py createsuperuser
 - 서버 기동
   - heroku open

    
