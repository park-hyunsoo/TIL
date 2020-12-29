# Git Command

## 0.init
- `git init`
- `.git/` 폴더를 생성해준다.
- ![image](https://user-images.githubusercontent.com/60903805/103262731-30ced100-49e9-11eb-97fc-531e4d9d723d.png)
- `.git` 폴더가 생성된 경우 `master`라는 표시가 나온다.

## 1.add
- git add <추가하고싶은 파일>
  - `git add .` : 현재 폴더의 모든 파일과 폴더를 add
- working directory => staging area 로 파일 이동


## 2. config
- `git config --global user.email "myemail@gmail.com"`
  - 이메일의 경우 깃헙에 올릴경우 잔디가 심어지는 기준이므로 정확하게 입력하는 것이 좋다.
- `git config --global user.name "myname"`
- 최초에 한번만 하면 된다.

## 3. commit
- `git commit -m "메시지"`
- 스냅샷을 찍는 동작
- add 되어있는 파일들을 하나의 묶음으로 저장
- 메세지에 들어가는 내용은 기능 단위로

## 4.remote
- `git remote add origin <주소>
- 원격 저장소와 현재 로컬 저장소를 연결

## 5.push
- `git push origin master` 
- 원격저장소의 master 브랜치로 로컬 저장소의 데이터를 전송
