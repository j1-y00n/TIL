# Django Model
- DB의 테이블을 정의하고 데이터를 조작할 수 있는 기능등을 제공
- 테이블 구조를 설계하는 청사진
<br><br>

>## model class
```django
  class Article(models.Model):
      title = models.CharField(max_length=10)
      content = models.TextField()
```
- models.Model
  - django.db.models 모듈의 Model이라는 부모클래스를 상속받아 작성
  - Model 기능에 관련된 모든 설정이 담긴 클래스
  - 개발자는 테이블 구조를 어떻게 설계할 지에 대한 코드만 작성하도록 하기 위함
- title, content
  - 클래스 변수명
  - 테이블의 각 `필드 이름`
- CharField, TextField 
  - model Field class
  - 테이블 필드의 `데이터 타입`
- max_length=10
  - model Field class의 키워드 인자(필드 옵션)
  - 테이블 필드의 `제약조건` 관련 설정
<br><br>

>## Migrations
- model class의 변경사항(필드 생성, 추가, 수정 등)을 DB에 최종 반영하는 방법
- model class에 변경사항이 생겼다면, 반드시 새로운 설계도를 생성하고, 이를 DB에 반영해야 함
```
  model class ----------------> migration 파일 ----------> db.sqlite3
  (설계도 초안)   makemigrations   (최종 설계도)     migrate
```
```django
  python manage.py makemigrations
```
- model class를 기반으로 설계도(migration) 작성
```django
  python manage.py migrate
```
- 만들어진 설계도를 DB에 전달하여 반영
<br><br>

>## Admin site
- admin 계정 생성
```django
  python manage.py createsuperuser
```
- admin에 모델 클래스 등록 -> admin site에서 확인
```django
  from django.contrib import admmin
  from .models import Article

  admin.site.register(Article)
```
<br><br>

>## 데이터베이스 초기화
1. migration 파일 삭제
2. db.sqlite3 파일 삭제

`migrations 폴더를 지우지 않도록 주의`