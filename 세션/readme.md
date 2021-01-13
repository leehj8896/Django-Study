- 세션 vs 쿠키
    - 쿠키
        - 클라이언트 로컬에 저장되는 key-value 쌍의 작은 데이터 파일
        - 브라우저를 종료해도 남아있을 수 있음
        - 상대적으로 빠름
    - 세션
        - 브라우저가 종료되기 전까지 클라이언트의 요청을 유지하게 해주는 기술
        - 로그인 후 sessionid를 포함해 요청과 응답을 주고 받음
        - 보안에 상대적으로 좋음

- 관련 설정
    ```python
    # settings.py

    INSTALLED_APPS = [
        '''생략'''
        'django.contrib.sessions',
        '''생략'''
    ]

    MIDDLEWARE = [
        '''생략'''
        'django.contrib.sessions.middleware.SessionMiddleware',
        '''생략'''
    ]
    ```

- 사용법
    - view 함수의 request 인자의 속성으로 사용 가능
    - 딕셔너리 연산
        ```python
        # key-value
        my_car = request.session['my_car']

        # default 값
        my_car = request.session.get('my_car', 'mini')

        # value 저장
        request.session['my_car'] = 'mini'

        # value 삭제
        del request.session['my_car']
        ```