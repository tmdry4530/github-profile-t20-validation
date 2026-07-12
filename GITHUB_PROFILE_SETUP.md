# GitHub Profile 설정 안내

자동 갱신 workflow가 활성 상태로 생성되었습니다.

## 업데이트 정책

- 자동 갱신: 공개 활동 기반 PROJECTS, SKILLS, ACTIVITY 변경은 default branch에 한 commit으로 적용됩니다.
- 정체성 변경: INTRO, IDENTITY, EVIDENCE 변경은 근거 요약이 포함된 고정 branch PR로 제안됩니다.
- 사용자 관리 영역: managed marker 밖의 내용과 MANUAL block은 자동화가 수정하지 않습니다.

## 필수 설정

1. 공개 Action 저장소와 검증된 40자리 immutable commit SHA를 설정합니다.
2. Actions workflow 권한에 `contents: write`, `pull-requests: write`를 유지합니다.
3. 저장소 Settings → Actions → General에서 GitHub Actions의 PR 생성·승인을 허용합니다.
4. branch protection이 bot의 dynamic commit을 허용하는지 확인합니다.
5. 가능하면 `github-profile/identity-update` branch의 writer를 이 workflow identity로 제한합니다.
6. 정체성 PR을 merge하기 전에 본문의 Verified commit SHA와 현재 PR head SHA가 같은지 확인합니다.
7. 비활성 workflow는 설정을 완료한 뒤 `.disabled` 확장자를 제거합니다.

## 현재 누락 항목

- 없음

token이나 API key를 config 또는 README에 저장하지 마세요. workflow는 실행 시점의 `github.token`만 사용합니다.
checkout credential은 저장소 Git config에 남기지 않도록 `persist-credentials: false`를 유지하세요. Action이 network Git 명령에만 요청 단위 인증 header를 전달합니다.
