1. django-allauth 설치
    ```
    pip install django-allauth
    ```

2. settings.py에 앱 추가
    ```python
    INSTALLED_APPS = [
        '''
        생략
        '''
        'django.contrib.sites',
        'allauth',
        'allauth.account',
        'allauth.socialaccount',
        'allauth.socialaccount.providers.naver',
    ]
    ```
    - sites : 사이트 정보 설정
    - acount : 가입한 계정 관리
    - socialaccount : 소셜 계정으로 가입한 계정 관리
    - providers.{제공자명} : 사용할 소셜 서비스에 따라 추가

3. settings.py 추가 설정
    ```python
    AUTHENTICATION_BACKENDS = {
        'django.contrib.auth.backends.ModelBackend',
        'allauth.account.auth_backends.AuthenticationBackend',
    }
    SITE_ID = 1
    LOGIN_REDIRECT_URL = '/'
    ```
    - AUTHENTICATION_BACKENDS : 어떤 형식의 로그인을 사용할 것인지 설정
        - ModelBackend : 장고 기본
        - AuthenticationBackend : allauth 방식 추가
    - SITE_ID
        - django_site 테이블에 있는 현재 사이트의 값
        - django_site 테이블에 여러 사이트를 등록하고 그 중 하나를 지정하는 역할
    - LOGIN_REDIRECT_URL
        - 로그인 후 이동할 URL이 설정되 지 않은 경우 이곳에 설정된 주소로 이동

4. 루트 urls.py 수정
    ```python
    urlpatterns = [
        '''생략'''
        path('accounts/', include('allauth.urls')),
        '''생략'''
    ]
    ```

5. migrate
    ```
    python manage.py migrate
    ```

6. 네이버 개발자 사이트 API 키 발급
    - https://developers.naver.com/products/login/api/

7. 관리자 페이지에 등록