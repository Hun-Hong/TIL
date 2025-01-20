# GitHub와 Git의 고급 사용법: 협업, Revert & Reset, 커밋 메시지 규칙

## GitHub 원격 저장소 생성 및 로컬 연결

### 원격 저장소 생성
1. GitHub에 로그인 후, 오른쪽 상단의 `+` 버튼 클릭 → `New repository` 선택.
2. 저장소 이름과 설명 입력.
3. 공개(Public) 또는 비공개(Private) 선택 → `Create repository` 클릭.

### 로컬 저장소와 원격 저장소 연결
1. 로컬 저장소 초기화
```bash
  git init
```
2. 원격 저장소 연결
```bash
  git remote add origin <저장소 URL>
```
<저장소 URL>: GitHub에서 제공하는 HTTPS 또는 SSH URL.

3. 변경 사항 업로드(Push)
```bash
  git add .
  git commit -m "커밋 메시지"
  git push origin main
```
4. GitHub에서 파일 업로드 결과 확인.

## GitHub를 활용한 협업 방법
- Fork와 Pull Request
  Fork: 원본 프로젝트를 복사해 독립적으로 작업.
- Pull Request (PR): 변경 내용을 원본 프로젝트에 반영 요청.
  작업 내용과 변경 이유를 명확히 작성.
### 브랜치 활용
  브랜치 생성:
```bash
  git checkout -b feature/branch-name
```
  브랜치 작업 후 커밋:
```bash
  git add .
  git commit -m "커밋 메시지"
```
  메인 브랜치 병합:
```bash
  git checkout main
  git merge feature/branch-name
```
### 브랜치를 사용하는 이유:
- 독립적인 작업 공간 확보.
- 협업 시 충돌 최소화.
- 검증된 코드만 메인 브랜치에 병합하여 안정성 유지.
## Revert와 Reset 기능
### Revert
  특정 커밋의 변경 사항을 되돌리는 새로운 커밋 생성
```bash
git revert <커밋 해시>
```
  히스토리를 유지하며 변경사항을 되돌림.
### Reset
  특정 커밋으로 돌아가는 기능:
- Soft Reset: 변경 사항을 Staging Area에 유지.
```bash
git reset --soft <커밋 해시>
```
- Mixed Reset: 변경 사항을 Unstaged 상태로 이동.
```bash
git reset --mixed <커밋 해시>
```
- Hard Reset: 변경 사항 삭제.
```bash
git reset --hard <커밋 해시>
```
사용 예시:
- Soft Reset: 잘못된 커밋 메시지를 수정할 때.
- Mixed Reset: 여러 커밋을 정리해 다시 작업할 때.
- Hard Reset: 불필요한 커밋을 삭제하고 초기화할 때.
## SHA-1과 Git 보안
- SHA-1 보안 취약점
  동일한 해시를 가진 데이터(충돌) 생성 가능.
  데이터 무결성을 위협.
- SHA-256으로의 전환
  더 긴 해시 값(256비트)을 생성해 보안성 강화.
  충돌 가능성을 현저히 낮춤.
## 커밋 메시지 작성 규칙
기본 형식
```plaintext
<타입>: <주제>

<본문>

<footer>
```
커밋 메시지 타입
- feat: 새로운 기능 추가
- fix: 버그 수정
- docs: 문서 관련 작업
- style: 코드 포맷팅, 세미콜론 수정 등
- refactor: 코드 리팩토링
- test: 테스트 코드 추가/수정

### 예시
```plaintext
feat: 사용자 로그인 기능 추가

- JWT를 사용해 인증 로직 구현
- 로그인 실패 시 에러 메시지 출력

Resolves: #123
```
