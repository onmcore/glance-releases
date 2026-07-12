# 문제 해결

[English](troubleshooting.md) | [한글](troubleshooting.ko.md) | [日本語](troubleshooting.ja.md) | [Deutsch](troubleshooting.de.md)

## 업데이트 채널

Glance는 백그라운드에서 자동 업데이트됩니다. **Settings → Updates**에서 채널을 선택하세요:

| 채널 | 설명 |
|---|---|
| **Stable** | 검증된 안정 릴리스. 일상 사용 권장. |
| **Preview** | 다가올 기능, 대체로 안정적이며 더 자주 릴리스됨. |

Stable을 쓰면서 Preview 채널 업데이트 확인만 추가로 켤 수도 있습니다(완전히 전환하지 않고도). 채널 변경은 다음 업데이트 확인 시점부터 적용됩니다.

## 내장 복구 기능

나쁜 순간이 저장소 손실로 번지지 않도록 자동으로 동작하는 것들이 있습니다:

- **인덱스/HEAD 손상 감지 및 복구** — 쓰기 도중 크래시 등으로 `.git`의 인덱스나 HEAD가 이상한 상태가 되면, 조용히 실패하는 대신 Glance가 감지하고 복구합니다
- **워처 회복력** — 실시간 변경 감지를 담당하는 백그라운드 파일 워처는 크래시로부터 격리되어 있고, 죽으면 스스로 재시작하므로 UI가 조용히 갱신을 멈추는 일이 없습니다
- **[Timeline](workflows.ko.md#timeline)** — 실수(잘못된 reset, 브랜치 삭제 등)를 했다면, Timeline의 reflog 뷰로 대부분 되돌릴 수 있습니다 — Glance가 직접 추적하지 않은 범위까지 포함해서요
- **Detached HEAD 경고** — 태그나 특정 커밋을 체크아웃하거나(또는 rebase가 중간에 멈추면), HEAD가 브랜치가 아니라 커밋을 직접 가리키게 됩니다. 이 경우 Glance가 주황색 배지를 표시합니다 — 클릭하면 현재 위치에서 브랜치를 만들어 정상 상태로 돌아갈 수 있습니다. Detached 상태에서는 추적할 브랜치가 없으므로 push/pull이 비활성화됩니다

## 그래도 문제가 있다면

- 무엇을 하다가, 무엇을 기대했고, 실제로 무슨 일이 있었는지와 함께 [이슈 열기](https://github.com/onmcore/glance-releases/issues/new)
- 버그라기보다 애매한 것들 — 기능 아이디어, 질문, 피드백은 [디스커션 시작](https://github.com/onmcore/glance-releases/discussions)

모든 리포트는 개발자가 직접 읽습니다. 응답 시간은 상황에 따라 다릅니다.
