# Glance

Windows용 초고성능 Git GUI.

[![Download for Windows](https://img.shields.io/github/v/release/onmcore/glance-releases?label=Download%20for%20Windows&color=2f6feb)](https://github.com/onmcore/glance-releases/releases/latest)

[English](README.md) | [한글](README.ko.md) | [日本語](README.ja.md) | [Deutsch](README.de.md)

![Glance로 리눅스 커널 저장소를 탐색하는 모습 — 커밋 그래프, 커밋 상세, diff 스테이징](docs/manual/assets/gifs/repo-open.gif)

이 저장소는 Glance의 공식 바이너리 릴리스와 릴리스 노트를 보관합니다.

## Glance란?

Glance는 한 가지 집착으로 처음부터 다시 만든 Git GUI입니다 — **속도**. 수백만 개의 커밋, 수십만 개의 파일이 들어찬 저장소에서도 기민하게 반응하고, 메모리 사용량도 가볍게 유지합니다.

Glance는 **지금은 개인·상업적 용도 모두 조건 없이 완전히 무료**입니다 — 평가판 타이머 없음, 기능 잠금 없음, 계정 가입 필요 없음. (향후 버전에 유료 상업 라이선스가 도입될 계획이지만, 이미 받으신 버전에는 영향이 없습니다.)

혼자 개발하고 있습니다 — 본업은 C++ 게임 개발자인데, 이번엔 Rust·Tauri·Solid.js를 새로 배워가며 AI와 페어링해서 개발하고 있어요.

### 핵심 특징

- **다른 도구가 멈출 때 빠르게** — 엔터프라이즈 규모 모노레포에서 즉각 반응, [직접 확인하기](docs/manual/performance.ko.md)
- **가벼운 메모리** — GB를 먹는 부류가 아닙니다
- **Tauri 런타임** — Electron급이 아닌 작은 설치본
- **풍부한 Git 작업** — branch / merge / rebase / stash / cherry-pick / blame / 히스토리 시각화
- **내장 충돌 해결** — merge·rebase·cherry-pick 충돌마다 뜨는 시각적인 3-way [머지 에디터](docs/manual/workflows.ko.md#충돌-해결)
- **네이티브 Worktree** — 현재 작업을 건드리지 않고 다른 브랜치를 별도 폴더에 체크아웃; [Worktree](docs/manual/workflows.ko.md#worktree) 참고
- **네이티브 Git LFS** — 순수 Rust로 만든 클라이언트라 별도의 `git-lfs` 바이너리가 필요 없음; 파일 하나씩이 아니라 배치로 다운로드하고 인라인 미리보기 지원; [Git LFS](docs/manual/workflows.ko.md#파일-탐색) 참고

### 이런 분께

- 대형 저장소에서 Git GUI가 버벅이는 게 지긋지긋한 개발자
- 브라우저를 둘러 포장한 도구보다 네이티브 느낌의 집중된 툴을 좋아하는 분
- 익숙한 그것들 말고 현대적인 대안을 찾는 Windows 사용자

## 다운로드

최신 설치본은 [Releases](../../releases) 페이지에서 받으세요.

### 릴리스 채널

| 채널 | 설명 | 받는 곳 |
|---|---|---|
| **Stable** | 검증된 안정 릴리스. 일상 사용 권장. | [Latest release](../../releases/latest) |
| **Preview** | 다가올 기능, 대체로 안정적. | [Pre-releases](../../releases) (*Pre-release* 표시) |

자동 업데이트가 내장되어 있습니다 — **설정 → 업데이트** 에서 채널을 고르세요.

## 매뉴얼

Glance가 처음이신가요? [매뉴얼](docs/manual/README.ko.md)에서 시작하기, 핵심 워크플로우, 단축키, 문제 해결을 다룹니다.

## 후원하기

Glance는 지금은 상업적 용도를 포함해 누구에게나 조건 없이 무료입니다. 도움이 되셨다면 [작은 후원을 고려해주세요](https://onmcore.github.io/glance-releases/sponsor.html) — 어디까지나 선택 사항이며, 꾸준한 개발에 큰 힘이 됩니다.

## 버그 리포트 & 피드백

- 버그를 발견했다면 [이슈 열기](https://github.com/onmcore/glance-releases/issues/new)
- 기능 아이디어가 있다면 [디스커션 시작](https://github.com/onmcore/glance-releases/discussions)

Glance는 저 혼자 개발하고 있습니다 — 리포트도 전부 제가 직접 읽어요. 그래서 답변까지 하루이틀 걸릴 수 있습니다.

## 라이센스

Glance는 현재 상업적 사용을 포함해 누구나 무료로 사용할 수 있습니다 — 라이선스 키나 결제가 필요 없습니다. 자발적 후원은 환영하나 선택 사항입니다. 향후 버전에 유료 상업 라이선스가 도입될 수 있으나, 이미 배포된 버전에는 적용되지 않습니다.

무수정 재배포는 허용되며, 리버스 엔지니어링·수정·재패키징은 금지됩니다(자세한 약관은 [LICENSE](./LICENSE) 참고). 무보증.

서드파티 구성요소 라이센스는 [THIRD_PARTY_LICENSES.md](./THIRD_PARTY_LICENSES.md)에 정리되어 있습니다.

---

**Glance** © 2026 onmcore
