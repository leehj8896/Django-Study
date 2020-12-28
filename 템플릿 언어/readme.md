- Django template language

    - 변수
        - {{ 변수 }} 형태
        - 점(.)으로 속성에 접근

    - 필터
        - {{ 변수|필터:인자 }}
        - 변수의 값을 변환
        - 여려 개의 필터를 연속으로 사용 가능
        - default, length, upper, add 등
        - 참고 : https://himanmengit.github.io/django/2018/02/23/Built-In-Template-Filter.html

    - 태그
        - 제어문 (if 문, for 문)
        - {% 태그 %} 형태
        - {% extends %} 등 단독으로 사용하는 태그 존재
        - {% if %} {% endif %} 등 함께 사용해야 하는 태그 존재
        - 내장 태그 목록 : https://docs.djangoproject.com/en/3.1/ref/templates/builtins/
        - 커스텀 태그 : https://wikidocs.net/9677
        
    - 주석
        - 한 줄 : {# 주석 #}
        - 여러 줄 : {% comment %} 주석 {# endcomment #}
