## Linux Commands
> 리눅스 명령어에 대해 알아보기
- `pwd` (print working directory)
    - 현재 작업 중인 경로를 출력
- `ls` (list)
    - 현재 폴더에 있는 파일, 폴더를 출력
    - `-a` (optional) : 숨김 처리된 파일, 폴더까지 출력
- `cd` (change directory)
    - 폴더 이동
- `mkdir` (make directory)
    - 폴더 생성
- `touch`
    -파일 생성
- `rm` (remove)
    - 파일 및 폴더 삭제
    - -r (optional) : 폴더 삭제를 위해 입력해야 하는 옵션

- `rm -r`
    - recursive 재귀적인
    - 정확하게 폴더 지정하여 폴더 안의 폴더 안의 폴더 까지 모두 삭제

- `rm -f`
    - force
    - 권한이 없어도 강제적으로 삭제


## Linux 개념

### lf와 crfl의 차이
- `lf` (Line feed) : 엔터
- `Carriage Return` : 맨 첫 줄로 가는 것
- 이 두 가지를 윈도우와 리눅스가 다르게 받아 들임
- 어떤 os는 엔터를 `lf`로 어떤 것은 `crfl`로 인식