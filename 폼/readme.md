- 개요
    - 사용자로부터 정보 수집, 서버에 제출하기 위해 사용됨
    - 텍스트박스, 체크박스 등 다양한 위젯 제공
    - 교차 사이트 요청 위조 방지(CSRF protection) 지원

- 처리 과정
    ![Form Handling - Standard](https://user-images.githubusercontent.com/28583563/104425634-4389fe00-55c4-11eb-81dc-67e3acef54b9.png)
    - https://developer.mozilla.org/ko/docs/Learn/Server-side/Django/Forms
    - 첫 요청일 경우
        - 기본 폼을 보여줌
    - 아닐 경우
        - 유효성 검사
            - 유효할 경우
                1. 요청 내용 처리
                2. 리다이렉트
            - 아닐 경우
                - 기본 폼을 보여줌

- Form vs Model Form
    - Form
        - 직접 필드 정의
        - 위젯 설정 필요
    - Model Form
        - 모델과 필드를 지정하면 자동으로 필드 생성

- 정의하기(Form)
    - forms.Form 클래스 상속
        - cleaned_data 속성
    - 속성 정의
        - 모델과 유사
        - BooleanField, CharField 등
    - 함수 정의
        - 유효성 체크
            - clean_<필드명>() 재정의
            - self.cleaned_data를 받아 검사 후 다시 return
            - 틀릴 경우 ValidationError 발생시키기

- 사용하기
    - 첫 요청일 경우
        - 기본 폼 인스턴스 생성
        ```python
        book_renewal_form = RenewBookForm()
        ```
    - 아닐 경우
        1. 데이터 삽입
        ```python
        book_renewal_form = RenewBookForm(request.POST)
        ```
        2. 유효성 검사
            - (폼 인스턴스).is_valid()
            - 유효할 경우 form.cleaned_data['key']를 받아 요청 처리

- 템플릿 작성
```html
<form action="" method="post">
    {% csrf_token %}
    {{ form.as_table }}
    <input type="submit" value="Submit">
</form>
```