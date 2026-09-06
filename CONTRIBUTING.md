# 협업 가이드

이 저장소는 GitHub Pages로 **`main` 브랜치에 push되는 즉시 실제 사이트(tiarto.com)에 배포**됩니다.
그래서 실수 방지를 위해 `main`에 직접 push하지 않고, 아래 흐름을 따릅니다.

## 새 팀원 온보딩 체크리스트 (관리자용)

1. **Settings → Collaborators and teams → Add people**
   - Role은 **Write**로 초대하세요 (Admin은 신뢰가 쌓인 뒤에).
2. **Settings → Branches → Add branch protection rule** (`main` 대상, 최초 1회만 설정하면 계속 유지됨)
   - `Require a pull request before merging` + `Require approvals` (1명 이상)
   - `Do not allow bypassing the above settings` (관리자 본인도 직접 push 금지 — 실수 방지)
   - `Block force pushes`, `Restrict deletions`
3. `.github/CODEOWNERS`에 새 팀원 GitHub 아이디 추가
   - 예: `* @donghyup-shin @새아이디`
   - 이렇게 해두면 PR 올릴 때 자동으로 리뷰 요청이 감

> 1~2번은 GitHub 웹 UI에서만 가능해서 Claude가 대신 설정할 수 없습니다. 위 경로대로 관리자가 직접 눌러주세요.

## 실제 작업 흐름 (모든 팀원 공통)

```bash
# 1. 최신 main 받기
git checkout main
git pull origin main

# 2. 작업용 브랜치 생성 (이름은 자유, 예: 이름-작업내용)
git checkout -b donghyup/update-hero-text

# 3. 수정 후 커밋
git add .
git commit -m "hero 문구 수정"

# 4. 내 브랜치 push
git push -u origin donghyup/update-hero-text
```

이후 GitHub 저장소 페이지에 뜨는 **"Compare & pull request"** 버튼을 눌러 PR을 생성합니다.
PR을 만들면 `.github/pull_request_template.md`에 정의된 체크리스트가 자동으로 채워지고,
`CODEOWNERS`에 등록된 사람에게 리뷰 요청이 자동으로 갑니다.

리뷰어가 Approve 하면 **"Merge pull request"** 버튼으로 `main`에 병합하고, 이때 사이트가 배포됩니다.

## 요약

- `main`에 직접 push ❌
- 브랜치 만들고 → PR 올리고 → 리뷰받고 → 머지 ✅
- 브랜치 보호 규칙이 켜져 있으면 위 순서를 안 지키면 애초에 push/merge가 막힙니다.
