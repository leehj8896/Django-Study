- 데코레이터 란?
    - 상속과 유사?
    - 참고 : https://ssungkang.tistory.com/entry/python-%EC%9E%A5%EC%8B%9D%EC%9E%90-%EB%8D%B0%EC%BD%94%EB%A0%88%EC%9D%B4%ED%84%B0decorator-%EB%A5%BC-%EC%95%8C%EC%95%84%EB%B3%B4%EC%9E%90
    
- Django view에서의 사용법

    - Function based view 일 경우
        - 방법 1
            ```
            from django.contrib.auth.decorators import login_required
            from django.shortcuts import render

            @login_required
            def post_create(request):
                return render(request, 'core/index.html')
            ```
        - 방법 2
            ```
            from django.contrib.auth.decorators import login_required
            from django.shortcuts import render

            def post_create(request):
                return render(request, 'core/index.html')

            post_create = login_required(post_create)
            ```

    - Class based view 일 경우
        - 방법 1 : as_view -> 함수로 감싸주기
            ```
            from django.contrib.auth.decorators import login_required
            from django.views.generic import TemplateView

            class MyTemplateView(TemplateView):
                template_name= "core/index.html"

            index = MyTemplateView.as_view()
            index = login_required(index)
            ```
        - 방법 2 : method_decorator를 함수에 적용
            ```
            from django.utils.decorators import method_decorator

            class MyTemplateView(TemplateView):
                template_name= "core/index.html"
                
                @method_decorator(login_required)
                def dispatch(self, *args, **kwargs):
                return super().dispatch(*args, **kwargs)
                
            index = MyTemplateView.as_view()
            ```
        - 방법 3 : method_decorator을 클래스에 적용
            ```
            @method_decorator(login_required, name="dispatch")
            class MyTemplateView(TemplateView):
                template_name= "core/index.html"
                
            index = MyTemplateView.as_view()
            ```
    - 참고 : https://ssungkang.tistory.com/entry/Django-FBV-%EC%99%80-CBV-%EC%9D%98-decorators-%EC%82%AC%EC%9A%A9%EB%B2%95

- 종류
    - login_required
    - require_http_methods, require_GET, require_POST, require_safe(GET이나 POST만)
    - 등등
    - Custom 가능