# Django URLs
<br><br>

>## URL dispatcher
- URL 패턴을 정의하고 해당 페턴이 일치하는 요청을 처리할 view 함수를 연결(매핑)
<br><br>

>## Variable Routing
- URL 일부에 변수를 포함시키는 것
- 변수는 view 함수의 인자로 전달 할 수 있음
- <path_converter:variable_name>
```django
  path('articles/<int:num>/', views.hello)
  path('hello/<str:name>/', views.greeting)
```
- Path converters
  - URL 변수의 타입을 지정 (str, int 등 5가지 타입 지원)
<br><br>

>## App URL mapping
- 각 앱에 URL을 정의하는것
- 프로젝트와 각각의 앱이 URL을 나누어 관리하여 주소 관리를 편하게 하기 위함
- **`include()`**
  - 다른 URL들을 참조할 수 있도록 돕는 함수
  - URL의 그 시점까지 일치하는 부분을 잘라내고, 남은 문자열 부분을 후속 처리를 위해 include된 URL로 전달
  ```django
    path('articles/', include('articles.urls'))
  ```
<br>

- **`Naming URL patterns`**
  - URL에 이름을 지정하는 것
  - path 함수의 name 인자를 정의해서 사용
  ```django
    path('index/', views.index, name='index')
  ```
<br>

- **`URL tag`**
  - 주어진 URL 패턴의 이름과 일치하는 절대 경로 주소를 반환
  ```django
    {% url 'url-name' arg1 arg2 %}
  ```
  ex)
  ```django
    {% url 'index' %}
  ```
<br>

- **`app_name 속성 지정`**
  - URL 이름 + app 이름표 붙이기
  ```django
    app_name = 'articles'
    urlpatterns = [
      ...,
    ]
  ```
  <br>

- **`URL tag의 변화`**
  ```django
    {% url 'app_name:url-name' %}
  ```
  ex)
  ```django
    {% url 'index' %} -> {% url 'articles:index' %}
  ```