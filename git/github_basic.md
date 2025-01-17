## git이란?
- git은 분산버전관리 시스템
- 개발자 표준
## git 명령어 모음
- git init:
  git 로컬 저장소 선언
- git add []:
  [] 파일을 스테이지에 올림
- git commit -m "":
  스테이지에 올린 파일들을 "" 커밋 메세지로 커밋
- git remote add (origin) remote url:
  (origin)이라는 별칭으로 remote url을 추가
- git push origin master:
  master branch를 origin이라는 remote 저장소에 업로드
- git pull origin master:
  origin remote 저장소에서 master branch로 업데이트
- git clone remote url path:
  path에 remote url의 저장소를 그대로 복사