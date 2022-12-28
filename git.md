# Git
> 분산버전 관리 시스템

> 차이와 수정 이유를 메세지로 남길수 있음

## Git 버전 관리 기초 흐름
```
1. Working directory -> add
2. Staging area -> commit
3. Head
```
## - git init
: 저장소 생성(초기화)

## - git add < file >
: working directory상의 변경 내용을 staging area에 추가하기 위함

## - git commit -m 'message here'
: staged 상태의 파일들을 커밋을 통해 버전으로 기록, 커밋 메시지는 변경사항을 나타냄

## - git status
: git 저장소에 있는 파일의 상태 확인

## - git log
: 현재 저장소에 기록된 커밋을 조회

<br>

# GitHub
> 원격저장소를 제공하는 서비스

## - 초기 원격저장소 설정
: New Repository, https://github.com/usename/저장소이름.git

## - git remote add origin : https://github.com/usename/저장소이름.git
: 로컬 저장소에 원격 저장소 정보 설정

## - git remote -v
: 원격 저장소 정보 확인

## - git remote rm origin(원격저장소이름)
: 원격저장소 삭제

## - git push origin(원격저장소이름) master(브랜치이름)
: 로컬 저장소의 버전을 원격저장소로 보냄

## - git pull origin(원격저장소이름) master(브랜치이름)
: 원격저장소의 버전을 로컬 저장소로 가져옴.

## - git clone 원격저장소주소(https://github.com/usename/저장소이름.git)
: 원격 저장소를 복제하여 가져옴

###
``` 
git clone과 pull의 차이점
: Clone-원격저장소 복제, Pull-원격저장소 커밋 가져오기
```

## - .gitignore
: 버전관리랑 상관 없는 파일 관리
