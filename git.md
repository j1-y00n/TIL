# Git
> 분산버전 관리 시스템

> 차이와 수정 이유를 메세지로 남길수 있음

## Git 버전 관리 기초 흐름
```
Working directory -add-> Staging area -commit-> Head
```
1. 작업하면
2. add하여 staging area에 모아
3. commit으로 버전 기록

**Git은 파일을 modified, staged, committed로 관리**

## 기본 명령어
- git init
    - 저장소(repository) 생성(초기화)
    - .git 폴더가 생성됨

- git add \<file>
    - working directory상의 변경 내용을 staging area에 추가하기 위함

- git commit -m 'message here'
    - staged 상태의 파일들을 커밋을 통해 버전으로 기록
    - 커밋 메시지는 변경사항을 나타냄

- git status
    - git 저장소에 있는 파일의 상태 확인

- git log
    - 현재 저장소에 기록된 커밋을 조회

<br>

# GitHub
> 원격저장소를 제공하는 서비스

## 초기 원격저장소 설정
1. New Repository
2. 저장소 설정
3. URL확인 https://github.com/GitHubusername/저장소이름.git

## 기본 명령어

- git remote add origin : https://github.com/GitHubusername/저장소이름.git
    - 로컬 저장소에 원격 저장소 정보 설정
    - 한번만 하면 됨

- git remote -v
    - 원격 저장소 정보 확인

- git remote rm origin(원격저장소이름)
    - 원격저장소 삭제

- git push origin(원격저장소이름) master(브랜치이름)
    - 로컬 저장소의 버전을 원격저장소로 보냄

- git pull origin(원격저장소이름) master(브랜치이름)
    - 원격저장소의 버전을 로컬 저장소로 가져옴.

- git clone 원격저장소주소(https://github.com/usename/저장소이름.git)
    - 원격 저장소를 복제하여 가져옴
``` 
git clone과 pull의 차이점
: Clone-원격저장소 복제, Pull-원격저장소 커밋 가져오기
```

- .gitignore
    - 버전관리랑 상관 없는 파일 관리
    
<br>

# Branch
> 독립적인 작업흐름을 만들고 관리

## 주요 명령어
- git branch {branch name}
    - branch 생성

- git checkout {branch name}
    - branch 이동

- git checkout -b {branch name}
    - branch 생성 및 이동

- git branch
    - branch 목록 확인

- git branch -d {branch name}
    - branch 삭제

## merge
> 각 branch에서 작업을 한 후 이력(commit)을 합치기 위해 merge 명령어를 사용

1. merge-fast foward
    - 기존 master branch에 변경사항이 없어 단순히 앞으로 이동
        1. feature-a branch로 이동 후 commit
        2. master 별도 변경 없음
        3. master branch로 병합
2. merge-merge commit
    - 기존 master branch에 변경사항이 있어 병합 커밋 발생
        1. feature-a branch로 이동 후 commit
        2. master branch commit
        3. master branch로 병합

<br>

# Git Flow
> Git을 활용하여 협업하는 흐름

> branch를 활용하는 전략

```
GitHub Flow 기본 원칙
1. master branch는 반드시 배포 가능한 상태여야 함
2. feature branch는 각 기능의 의도를 알수 있도록 작성
3. Commit message는 매우 중요하며, 명확하게 작성
4. Pull Request를 통해 협업 진행
5. 변경사항을 반영하고 싶다면, master branch에 병합
```

## GitHub Flow Models
- Shared Repository Model
    1. 팀원 초대 및 저장소 Clone
        1. Invite collaborator
        2. Accept Invitation
        3. Clone project(remote) repository
    2. branch에서 작업 및 GitHub Push
        1. Feature branch 생성 및 작업
        2. Commit
        3. Push to remote repository
    3. Pull Request 생성
        1. Open a Pull Request
        2. Creat Pull Request
    4. Review 및 Merge
        1. Merge pull Request
    5. 다음 작업 준비
        1. 로컬저장소에서는 merge된 branch는 삭제하고 master branch를 업데이트 함.
        2. 이후 1~3 과정 반복.   

- Fork & Pull Request Model
    1. Fork & Clone
        1. Fork repository
        2. Clone project(remote) repository
   2. branch에서 작업 및 GitHub Push
        1. Feature branch 생성 및 작업
        2. Commit
        3. Push to remote repository
    3. Pull Request 생성
        1. Open a Pull Request
        2. Creat Pull Request
    4. Review 및 Merge
        1. Merge pull Request
    5. 다음 작업 준비
        1. 로컬저장소에서는 merge된 branch는 삭제하고 master branch를 업데이트 함. 

            ` 단, master branch는 원본 저장소를 받아와야 하며 별도의 원격저장소를 추가하여 진행할 수 있음. 혹은 GitHub에서 fetch upstream도 가능. `
        2. 이후 1~3 과정 반복. 