# Python Framework Django 개발환경 설정 가이드 / 가상환경(venv : virtual environment) 설정 가이드

>## 가상환경을 사용하는 이유
- `의존성 관리`
  - 라이브러리 및 패키지를 각 프로젝트마다 독립적으로 사용 가능
- `팀 프로젝트 협업`
  - 모든 팀원이 동일한 환경과 의존성 위에서 작업하여 버전간 충돌을 방지
<br><br>

>## 가상환경 설정 순서
### 1. 가상환경 생성
- 작업할 폴더 생성
- 폴더에서 Visual Studio Code 실행 또는 터미널 실행
- Terminal -> New Termminal
```python
  python -m venv venv
```
- 두번째 venv : 가상환경이름(다른 이름으로 지정할 수 있으나 venv로 고정, 룰)
<br><br>

### 2. 가상환경 활성화
```python
  source venv/bin/activate
```
- 비활성화
```python
  deactivate
```
<br>

### 3. django 설치
```python
  pip install django==3.2.18
```
- django 설치 버전 : 3.2.18 (2023년 LTS)
  - LTS(Long-Term-Support)  
    : 프레임워크나 라이브러리 등의 소프트웨어에서 장기간 지원되는 안정적인 버전을 의미할때 사용
<br>

```python
  pip list
```
- pip를 통해 확인
<br><br>

### 4. python 패키지 의존성 관리
- **의존성 파일 생성(패키지 설치시마다 진행)**
  - 현재 환경에 설치된 패키지 목록을 requirements 포맷으로 출력
  ```python
    pip freeze > requirements.txt
  ```
<br>

- **의존성 파일 사용(패키지 목록 설치)**
  - requirements.txt에 있는 내용을 가지고 자동으로 패키지를 설치해줌으로써 해당 프로젝트가 어떤 버전의 패키지를 썼는지 기억하지 않아도 개발환경을 설정 할 수 있음
  - github에서 프로젝트를 받게되는 사람도 해당 파일이 있으면 가상환경 설정 후 바로 설치 가능
  - 설치 순서   
  : 가상환경 생성 -> 가상환경 활성화 -> requirements.txt 파일을 읽어서 패키지 자동 설치
  ```python
    pip install -r requirements.txt
  ```
<br><br>

>## django 프로젝트 생성
```python
  django-admin startproject firstpjt .
```
- firstpjt라는 이름의 프로젝트를 생성
- `.` 꼭 써주기
<br><br>

>## django 서버 실행
```python
  python manage.py runserver
```
- manage.py와 동일한 경로에서 명령어 진행
- http://127.0.0.1:8000/ 링크 접속 
<br><br>

>## github 연동
1. .gitignore 작성
    - gitignore.io를 활용해서 .gitignore 파일 생성
<br><br>

2. git 생성
    - `git init`
<br><br>

3. 작업물을 add
    - `git add`
<br><br>

4. git commit
    - `git commit -m 'commit message'`
<br><br>

5. github repository 생성
<br><br>

6. 작업폴더와 원격저장소 연결
    - `git remote add origin {생성한 repository의 code}`
<br><br>

6. commit한 작업물을 원격저장소에 push
    - `git push origin master`
<br><br>

>## django 앱 생성
- django project : 애플리케이션의 집합 (DB 설정, URL 연결, 전체 앱 설정 등을 처리)
- django application : 독립적으로 작동하는 기능 단위 모듈 (각자 특정한 기능을 담당, 다른 앱들과 합께 하나의 프로젝트를 구성)
```python
  python manage.py startapp articles
```
- articles라는 앱 생성
- 앱의 이름은 '복수형'으로 지정하는 것을 권장
<br><br>

>## django 앱 등록
- project폴더 -> settings.py -> INSTALLED_APPS 리스트에 앱 등록
- `반드시 앱을 생성한 후에 등록해야함`, 등록 후 생성 불가