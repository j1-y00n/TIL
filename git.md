# GIT
> 분산버전 관리 시스템

> 차이와 수정 이유를 메세지로 남길수 있음

## Git 버전 관리 기초 흐름
```
1. Working directory -> add
2. Staging area -> commit
3. Head
```
## git init
: 저장소 생성(초기화)

## git add < file >
: working directory상의 변경 내용을 staging area에 추가하기 위함

## git commit -m '< message here >'
: staged 상태의 파일들을 커밋을 통해 버전으로 기록, 커밋 메시지는 변경사항을 나타냄

## git status
: git 저장소에 있는 파일의 상태 확인

## git log
: 현재 저장소에 기록된 커밋을 조회