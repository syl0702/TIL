# git

## 버전 관리란?
“버전 관리” 는 무엇이고 우리는 왜 이것을 알아야 할까? 버전 관리 시스템은 파일 변화를 시간에 따라 기록했다가 나중에 특정 시점의 버전을 다시 꺼내올 수 있는 시스템이다. 이 책에서는 버전 관리하는 예제로 소프트웨어 소스 코드만 보여주지만, 실제로 거의 모든 컴퓨터 파일의 버전을 관리할 수 있다.

## 분산 버전 관리 시스템 (DVCS)

![DVCS](./assets/distributed.png)


## 세 가지 상태

![areas](./assets/areas.png)

## 설정
```shell
git status
```
- 현재 상태를 체크하는 명령어

```shell
git config
```
- git 설정을 하는 명령어
- 일반적으로 `--global` 옵션으로 최초 한번만 실행
- `git config --global user.meail 'your@email.com`
    - `git config --global user.email`를 통해 값 확인
- `git config --global user.name 'yourname'`
    - `git config --global user.name`를 통해 값 확인

```shell
git remote
```
- `git remote add origin <remote url>`
- remote 저장소 주소를 추가하는 명령어

```shell
git remote -v
```
- git remote option 중 하나
- 현재 연결된 위치의 remote 주소를 출력
- 오른쪽 주소는 왼쪽의 별명을 가졌음을 디스플레이
- `git remote`만 출력할 경우 현재 연결된 별명만 나온다

##  git 명령어

```shell
git init
```
- `.git directory`를 생성하는 명령어
- 현재 폴더에 `.git` 폴더를 생성


```shell
git add .
```
- `working directory`에 있는 파일, 폴더를 `staging area`에 추가
- add 하기 전에는 파일이 저장이 되었는지 확인하기

```shell
git add <file, folder name>
```
- `working directory`에서 `staging area`로 추가
- 일반적으로 모든 파일, 폴더를 추가하기 위해 아래의 코드를 사용
- `git add .`


```shell
git commit -m 'message'
```

- `staging area`에 올라간 파일들을 저장
- `staging area`에 올라간 파일들의 스냅샷을 찍어 `.git directory`에 저장
- 일반적으로 `-m` 옵션을 넣어서 커밋 메세지를 추가하여 등록


```shell
git remote add origin <remoteurl>
```
- 원격 저장소 주소를 `origin`이라는 별명으로 저장


```shell
git push origin master
```
- `master` 브랜치를 `origin` 원격 저장소로 업로드

## Tips
- `Ctrl+ l` : 터미널 클리어
- VS 코드 깃에 업로드 및 업데이트 하기 : 업로드 전 **저장** 필수!
    1. `git init` : 첫 업로드 때만 (폴더 상위에 이미 git init을 했다면 그 내부에서는 하지 않는 것을 추천. 충돌 일어날 가능성이 있음)
    2. `git add .`
    3. `git commit -m '개념 추가'`
    4. `git remote add origin url` : 첫 업로드 때만. 보통 복붙으로 해결
    5. `git push origin master`

