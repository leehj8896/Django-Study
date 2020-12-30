- 디폴트 폼
    ```python
    admin.site.register(Question)
    ```

- 커스터마이징
    ```python
    class QuestionAdmin(admin.ModelAdmin):
        pass

    admin.site.register(Question, QuestionAdmin)
    ```

- ModelAdmin 클래스 변수

    - fields : detail 페이지에서 보여줄 필드 목록
    - fieldsets : fields 그룹화
    - inlines : 관계 모델 추가
    - list_display
        - 리스트 페이지에서 보여줄 필드 목록
        - 커스텀 함수 추가 가능
            - 기본 이름 : 함수 명.replace('_', '')
            - return 값 str() 출력
            - 함수에 속성 부여하여 또 커스텀 가능
                - admin_order_field, boolean, short_description 속성 등
                - 참조 : https://docs.djangoproject.com/ko/3.1/ref/contrib/admin/#django.contrib.admin.ModelAdmin.list_display
    - list_filter : 필터링할 변수 목록
    - search_field : 검색할 변수 목록


- 관계 모델 추가
    - StackedInline, TabularInline 등 사용
    - 예시
        ```python
        class ChoiceInline(admin.StackedInline):
            model = Choice
            extra = 3

        class QuestionAdmin(admin.ModelAdmin):
            ```
            생략
            ```
            inlines = [ChoiceInline]

        admin.site.register(Question, QuestionAdmin)
        ```

- 템플릿 커스터마이징
    - 참고 : https://teamlab.github.io/jekyllDecent/blog/tutorials/Django-Admin-%EC%BB%A4%EC%8A%A4%ED%84%B0%EB%A7%88%EC%9D%B4%EC%A7%95

- 참조 : https://docs.djangoproject.com/ko/3.1/intro/tutorial07/