- 주요 제너릭 뷰
    - 기본 뷰 : View, TemplateView, RedirectView
    - 보기 뷰 : DetailView, ListView
    - 수정 뷰 : FormView, CreateView, UpdateView, DeleteView
    - 날짜 뷰
        - YearArchiveView, MonthArchiveView, DayArchiveView
        - TodayArchiveView, DateDetailView

- 속성 변수 오버라이딩
    - model
    - queryset
    - template_name
    - context_object_name
        - ListView에서 사용
        - 템플릿에 전달하는 object name
        - default : object_list
    - paginate_by
    - date_field
    - form_class
    - success_url

- 메소드 오버라이딩
    - def get_queryset()
    - def get_context_data(**kwargs)
    - def form_valid(form)

- 참고 : https://wikidocs.net/9623#cbv-class-based-view