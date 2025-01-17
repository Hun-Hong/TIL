# Git 기초 개념

소프트웨어 개발을 시작할 때 가장 먼저 배워야 하는 기술 중 하나가 **Git**입니다. Git은 프로젝트의 버전 관리를 돕는 강력한 도구로, 협업 작업과 코드 관리의 필수적인 역할을 합니다.

---

## Git이란?

**Git**은 분산 버전 관리 시스템(DVCS)입니다. 여러 개발자가 동시에 작업하더라도 각자의 작업을 독립적으로 관리하고, 필요할 때 중앙 서버나 다른 개발자의 작업과 통합할 수 있습니다.

- **로컬 저장소(Local Repository)**: 내 컴퓨터에 저장된 프로젝트.
- **원격 저장소(Remote Repository)**: GitHub, GitLab 등 서버에 저장된 프로젝트.

---

## 분산 버전 관리 시스템: 왜, 그리고 어떻게 가능한가?

**중앙 집중식 버전 관리 시스템(CVCS)**와 **분산 버전 관리 시스템(DVCS)**의 주요 차이점은 데이터를 관리하는 방식에 있습니다.

1. **중앙 집중식 버전 관리 (CVCS)**  
   - 서버에 모든 데이터가 저장되고, 사용자는 서버에서 데이터를 가져와 작업을 수행합니다.
   - 로컬 저장소에는 최신 상태의 파일만 저장되고, 변경 이력은 서버에만 존재합니다.
   - 서버가 다운되거나 손상되면 프로젝트 복구가 어려울 수 있습니다.

2. **분산 버전 관리 (DVCS)**  
   - 서버의 데이터를 로컬 저장소로 **완전 복제(Clone)**하여 작업합니다.
   - 변경 사항은 로컬에서 저장(Commit)하고, 필요할 때만 원격 저장소와 동기화(Push, Pull)합니다.
   - 모든 커밋 히스토리가 로컬에 저장되므로, 네트워크 연결 없이도 작업 가능합니다.

Git은 **스냅샷 방식**을 사용하여 프로젝트의 상태를 효율적으로 관리합니다. 커밋마다 전체 파일 상태를 저장하는 대신, 변경된 파일(차이점)만을 추적하고 압축합니다.

---

## Git 설치 및 환경 설정

### 설치
운영 체제별 Git 설치 방법은 다음과 같습니다:
- **Windows**: [Git 다운로드 링크](https://git-scm.com/downloads/win)
- **macOS**: Homebrew를 사용해 설치
  ```bash
  brew install git
  ```
- **Linux**: 패키지 관리자를 사용해 설치
  ```bash
  sudo apt-get install git
  ```
  Git 최초 설정
Git 설치 후, 사용자 정보를 설정해야 커밋 기록에 작성자가 포함됩니다.

### 사용자 이름 설정
```bash
git config --global user.name "Your Name"
```
### 사용자 이메일 설정
```bash
git config --global user.email "youremail@example.com"
```

## Git의 기본 흐름
Git은 Working Directory → Staging Area → Repository라는 세 가지 단계로 파일을 관리합니다.

### 주요 명령어
- 저장소 초기화
```bash
git init
```
- 상태 확인
```bash
git status
```
- 파일 추가
```bash
git add 파일명
```
- 또는 모든 변경 사항 추가
```bash
git add .
```
- 커밋
```bash
git commit -m "커밋 메시지"
```
- 변경 이력 보기
```bash
git log
```
- 간단히 보기
```bash
git log --oneline
```
## .gitignore 파일 생성
Git이 특정 파일이나 폴더를 추적하지 않도록 .gitignore 파일을 설정할 수 있습니다.

### 생성 방법
- .gitignore 파일 생성
```bash
touch .gitignore
```
- .gitignore 파일에 추적 제외할 파일명 또는 폴더명을 추가
```
secret.txt
*.log
.DS_Store
...
```
- 이미 추적 중인 파일 제외하기
이미 커밋된 파일은 다음 명령어로 추적에서 제외할 수 있습니다:
```bash
git rm --cached secret.txt
```

## 추가 자료
- [Git 공식 문서](https://git-scm.com/doc)
- [GitIgnore 생성기](https://www.toptal.com/developers/gitignore)

