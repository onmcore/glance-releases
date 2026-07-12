# 시작하기

[English](getting-started.md) | [한글](getting-started.ko.md)

## 설치

[Releases](../../releases/latest) 페이지에서 최신 설치본을 받아 실행하세요. 이후에는 Glance가 스스로 업데이트합니다 — 채널을 바꾸고 싶은 경우([문제 해결](troubleshooting.ko.md#업데이트-채널) 참고)가 아니면 이후 버전을 수동으로 받을 필요는 없습니다.

설치본을 처음 실행하면 **"Windows에서 PC를 보호했습니다"**라는 SmartScreen 경고가 뜰 수 있습니다. 악성 코드라서가 아니라, Glance가 아직 코드 서명이 안 되어 있어서입니다 — 서명 인증서는 매년 비용이 드는데, 무료로 혼자 만드는 프로젝트라 그럴 예산이 없습니다. **추가 정보 → 실행**을 눌러 계속 진행하시면 됩니다.

## 저장소 열기

처음 실행하면 (아직 비어 있는) **Recent Repositories** 목록과 함께 다음 옵션이 보입니다:

- 기존 로컬 저장소 **열기(Open)**
- URL(HTTPS 또는 SSH)로 저장소 **Clone**

여러 저장소를 동시에 열어두고 사이드바의 저장소 스위처로 오갈 수 있습니다. Clone은 백그라운드에서 진행되므로, clone을 시작해 두고 다른 저장소에서 계속 작업할 수 있습니다.

SSH로 clone하는데 아직 키를 만들지 않았다면 핵심 워크플로우의 [SSH 설정](workflows.ko.md#ssh-리모트)을 참고하세요.

<!-- TODO: screenshot — Recent Repositories / clone 진입점 -->

## 인터페이스 둘러보기

왼쪽 사이드바에는 위에서부터 5개 탭이 있습니다:

| 탭 | 내용 |
|---|---|
| **Branches** | 커밋 히스토리 그래프, refs(브랜치/리모트/태그), stash |
| **Changes** | 워킹 디렉토리 스테이징 영역 (staged / unstaged / conflicts) |
| **File Explorer** | 변경 여부와 무관한 저장소 전체 파일 트리 |
| **Timeline** | HEAD가 거쳐온 모든 지점을 시간순으로 보여주는 reflog + 되돌리기 |
| **Settings** | Git 설정, 엔진, 외형, 에디터, 업데이트, SSH 키, 라이선스 |

커밋·브랜치·파일을 선택하면 오른쪽 패널에 상세 내용이 열립니다 — 상황에 따라 커밋 메타데이터와 diff, 파일 내용, 또는 충돌 해결 에디터가 표시됩니다.

![사이드바 탭 아이콘 레일](assets/screenshots/hero.png)

다음: [핵심 워크플로우](workflows.ko.md)에서 일상적인 작업들 — 히스토리 보기, 스테이징, 브랜치, 리모트 동기화 등을 다룹니다.
