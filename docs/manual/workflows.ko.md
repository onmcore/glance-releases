# 핵심 워크플로우

[English](workflows.md) | [한글](workflows.ko.md) | [日本語](workflows.ja.md) | [Deutsch](workflows.de.md)

## 히스토리 보기

**Branches** 탭에서 커밋 그래프를 볼 수 있습니다 — 가상화된 리스트라 수십만 개 커밋에서도 부드럽게 스크롤됩니다. 사이드바의 refs 트리에는 브랜치·리모트·태그·stash가 나열되며, 하나를 선택하면 그래프가 필터되거나 해당 위치로 이동합니다.

- `Ctrl+F`로 검색 열기 — 메시지·작성자·해시로 커밋 필터링
- 커밋 우클릭으로 체크아웃, 브랜치 생성, cherry-pick, reset, compare, patch로 내보내기, 새 창에서 열기 등 실행
- **All Branches** 토글로 현재 브랜치 조상 커밋만이 아니라 전체 히스토리를 하나의 리스트로 보기
- 커밋에 마우스를 올리면 미리보기, 클릭하면 오른쪽 패널에 상세(Info / Changes 탭) 표시
- **새 창에서 열기**는 커밋 상세 화면을 별도 창으로 띄워, 메인 창에서 히스토리를 계속 보면서 비교할 수 있게 해줍니다

### Reset

커밋을 우클릭 → **Reset to this commit**으로 현재 브랜치를 그 지점으로 옮길 수 있습니다:

- **Soft** — 브랜치 포인터만 이동. 워킹 디렉토리와 staged 변경사항은 그대로 유지됩니다
- **Mixed** — 포인터를 옮기고 인덱스도 갱신하지만, 워킹 디렉토리 파일은 그대로 둡니다
- **Hard** — 포인터·인덱스·워킹 디렉토리를 전부 그 지점에 맞춰 재작성합니다 (커밋 안 된 변경사항은 사라짐 — untracked 파일은 건드리지 않습니다)

Hard reset이 잘못됐다면 [Timeline](#timeline)으로 대부분 복구할 수 있습니다.

![refs 사이드바 + 커밋 그래프](assets/screenshots/hero.png)

## 스테이징 & 커밋

**Changes** 탭은 워킹 디렉토리 스테이징 영역으로, **Staged** / **Unstaged** / (있는 경우) **Conflicts** 섹션으로 나뉩니다. 변경량이 많을 때 보기 편하도록 Flat / Grouped / Tree 레이아웃을 전환할 수 있습니다.

- diff 패널은 파일을 하나씩 여는 대신 변경된 모든 파일을 하나의 연속된 스크롤로 보여줍니다 — unified/split 레이아웃을 전환할 수 있고, 여러 줄을 드래그해 한 번에 stage/discard할 수 있습니다
- 파일이나 폴더 체크박스로 stage/unstage — `Ctrl`/`Shift` 다중 선택 지원
- Discard는 파일·hunk·드래그한 줄 범위 단위로 가능
- 바이너리 파일은 diff 대신 크기 카드로 표시됩니다
- 단어 단위 강조로 줄 안에서 정확히 어떤 문자가 바뀌었는지 표시하고, CSV/TSV diff는 열마다 다른 색으로 구분하며, 코드 diff에는 들여쓰기 깊이를 보여주는 인덴트 가이드가 표시됩니다
- Git LFS로 추적되지 않는 대용량 바이너리 파일에는 배지가 표시되며, 클릭 한 번으로 `.gitattributes`에 추가하는 **Track with LFS** 액션을 제공합니다 — 크기 기준과 이 검사를 켤지 여부는 Settings에서 조정 가능합니다
- 아래 패널에 커밋 메시지를 쓰고 `Ctrl+Enter`로 제출
- diff 헤더에 파일의 인코딩(UTF-8, EUC-KR 등)과 줄바꿈(LF/CRLF)이 표시됩니다. Unstaged 워킹 카피 파일은 칩을 클릭해 변환할 수 있습니다

변경 사항은 파일 워처가 실시간으로 감지합니다 — 수동 새로고침 불필요. 이 통합 멀티파일 뷰는 커밋 상세의 **Changes** 탭에서도 동일하게 쓰이므로, 히스토리를 리뷰할 때도 워킹 디렉토리를 볼 때와 같은 방식으로 볼 수 있습니다.

### 공동 작성자 & 서명

커밋 메시지 위 톱니바퀴(⚙) 아이콘에서:

- **공동 작성자(Co-authors)** — 이름/이메일로 기여자를 추가하는 모달을 엽니다(최근 기여자 자동완성 지원). 커밋 시 `Co-authored-by` 트레일러로 추가됩니다
- **커밋 서명(Sign commit)** — 설정된 Git 서명 키(SSH 또는 GPG)로 서명합니다. 암호화되지 않은/패스프레이즈 없는 SSH 키는 앱 내에서 바로 서명되고, GPG나 패스프레이즈 보호된 키는 시스템의 `git`/`gpg-agent` 설정으로 위임됩니다

### Amend

커밋 패널의 **Amend** 토글을 켜면 새 커밋을 만드는 대신 staged 변경사항을 이전 커밋에 합칩니다. 메시지와 작성자가 그 커밋에서 미리 채워지고, Staged 섹션에는 amend될 커밋의 내용이 표시됩니다 — 이미 `HEAD`에 있는 라인은 읽기 전용이며, 파일을 unstage하면 amend 대상에서 빠집니다.

![멀티파일 diff와 단어 단위 하이라이트가 보이는 Changes 패널](assets/screenshots/staging.png)

## 브랜치 & 머지

사이드바나 Branch 메뉴에서 브랜치를 생성·체크아웃·이름변경·삭제할 수 있습니다. 체크아웃은 대형 저장소에서 진행률을 보여주며, 실제 변경된 경로만 건드립니다. Windows에서는 checkout, pull, push, rebase, sync 등 오래 걸리는 작업의 진행률이 창을 최소화한 상태에서도 작업 표시줄 아이콘에 표시됩니다.

- **Merge** — 현재 브랜치에 다른 브랜치를 병합 (fast-forward 또는 실제 머지 커밋); 충돌이 있으면 Merge Editor가 열립니다
- **Rebase onto** — 브랜치나 커밋 위로 rebase — 단계별(체크아웃, 커밋 재생 등) 진행 상황 표시; 브랜치에 upstream이 설정돼 있다면 컨텍스트 메뉴에서 클릭 한 번으로 **Rebase onto upstream**도 가능합니다
- **Cherry-pick** — 커밋 컨텍스트 메뉴에서 현재 브랜치로 cherry-pick
- **태그** — 개별 생성·삭제·푸시 가능, annotated 태그 메시지는 인라인으로 확인 가능

### Stash

Branch 메뉴의 **Stash Changes...**로 커밋되지 않은 변경사항을 보관하며, staged 변경을 워킹 트리에 남겨둘지 선택할 수 있습니다. Stash는 사이드바의 Stashes 섹션과 커밋 그래프에 표시됩니다. 각 stash는 다음을 지원합니다:

- **Pop** — 적용 후 제거
- **Apply** — 적용하되 stash는 유지
- **Drop** — 적용 없이 삭제

### 충돌 해결

Merge, rebase, cherry-pick 중 충돌이 나면 Glance가 **Merge Editor**를 엽니다 — 3-way 뷰(Ours / Base / Theirs)이고 `[` / `]`로 충돌 사이를 이동합니다. 해결 후 같은 화면에서 계속하거나 작업을 중단(abort)할 수 있습니다.

외부 툴(Beyond Compare, WinMerge, KDiff3 등)을 쓰고 싶다면 Settings에서 설정하세요 — 내장 뷰 대신 그 툴로 diff와 충돌을 열어줍니다.

![Merge Editor 3-way 뷰](assets/screenshots/merge-editor.png)

## 리모트 동기화

사이드바에서 리모트를 추가·수정·삭제할 수 있습니다. Fetch는 수동 실행하거나 백그라운드에서 자동 실행되며(기본 3분 간격 — Settings에서 조정 가능), 새로 들어온 내용을 알려주는 결과 토스트도 표시됩니다 — 새로 생기거나 갱신·삭제된 브랜치와 태그를 여러 리모트 것이라도 카드 하나로 합쳐 보여줍니다. Push는 force와 force-with-lease를 지원합니다. Pull은 merge(fast-forward 또는 3-way, 충돌 해결 포함) 또는 rebase 방식을 선택할 수 있으며, 커밋되지 않은 변경사항이 방해가 될 경우 Glance가 자동으로 stash한 뒤 재시도하고 끝나면 다시 복원해줍니다 — pull 전략이나 엔진과 무관하게 동작하며, 재시도해도 충돌이 남으면 안전하게 되돌립니다.

### SSH 리모트

SSH 기반 clone/fetch/push를 쓰려면 **Settings → SSH Keys**에서 키를 먼저 설정하세요:

1. **Generate a key** — 알고리즘 선택(Ed25519 권장), 이름 지정 후 생성
2. 공개 키를 GitHub/GitLab 등 Git 호스트에 등록
3. **Host configuration**에서 호스트 항목 추가(HostName, User, Port, IdentityFile) — 실제 `~/.ssh/config`를 편집하는 것이므로, 기존 항목이나 Glance가 모르는 지시어도 그대로 보존됩니다
4. 새 호스트에 처음 연결하면 Glance가 SSH 호스트 키 신뢰(TOFU)를 **Known hosts**에서 물어봅니다 — `ssh` 최초 연결 시 뜨는 확인창과 같은 개념입니다

![SSH Keys 설정 화면](assets/screenshots/ssh-keys.png)

## 고급

### Worktree

Worktree는 타이틀 바 아래 스트립에 현재 저장소 옆 탭으로 표시됩니다 — 현재 작업을 건드리지 않고 두 가지를 동시에 진행할 때 유용합니다. **+**를 눌러 추가: 시작 브랜치, 대상 폴더, 이름을 지정하세요(경로는 기본으로 `<폴더>/<브랜치>`이며 생성 전에 수정 가능). 탭을 클릭하면 바로 전환되고, 우클릭하면 삭제할 수 있습니다(현재 있는 worktree는 삭제 불가). 스트립에 다 들어가지 않을 만큼 worktree가 많으면 "+N" 버튼으로 나머지를 볼 수 있습니다.

![타이틀 바 아래 worktree 탭 스트립](assets/screenshots/worktree-tabs.png)

### Submodule

Submodule은 사이드바에 표시됩니다. 초기화 안 된 항목은 **Init** 버튼이, 초기화된 항목은 클릭하면 별도 저장소로 열리며, 우클릭 메뉴에서 업데이트할 수 있습니다.

### Patch

공유 리모트 없이 변경사항을 주고받으려면, 커밋 우클릭(또는 범위 드래그 선택) → **Export as patch**를 쓰세요. 나중에 Repository 메뉴의 **Apply patch**로 적용합니다. 이건 `git am`보다는 `git apply`에 가깝습니다 — 워킹 트리만 갱신하므로, stage와 commit은 직접 해야 합니다.

### Diff 알고리즘

특정 diff가 예상과 다르게 보인다면, **Settings → Editor**에서 diff 알고리즘을 Histogram(기본) / Myers / Minimal 중에서 바꿀 수 있습니다.

## 두 ref 비교

커밋·브랜치·태그를 우클릭해 **Compare**를 선택하면, 현재 체크아웃 상태와 무관하게 임의의 두 ref 사이 파일 단위 diff를 볼 수 있습니다. 2-dot(`a..b`)과 3-dot(`a...b`, merge-base 기준) 비교를 전환하고 양쪽을 바꿀 수 있습니다.

## 파일 탐색

**File Explorer** 탭은 (변경 여부와 무관하게) 저장소 전체 파일 트리를 Flat / Grouped / Tree 레이아웃으로 보여줍니다. 파일을 열면 문법 강조가 적용된 내용이 표시되고, Markdown은 원본/렌더링 미리보기를 전환할 수 있으며, CSV/TSV는 원본 텍스트와 헤더 클릭으로 정렬 가능한 표를 전환할 수 있습니다.

파일 컨텍스트 메뉴에서 **history**(그 파일을 건드린 모든 커밋)나 **blame**(라인별 작성자·커밋 주석)도 볼 수 있습니다.

Git LFS로 관리되는 파일은 트리에 배지가 표시됩니다. Glance의 LFS 지원은 순수 Rust로 직접 구현한 네이티브 클라이언트라 별도의 `git-lfs` 바이너리가 필요 없습니다 — 포인터 파일과 실제 콘텐츠 변환을 자동으로 처리하고, checkout·reset·discard 시 없는 콘텐츠를 파일 하나씩이 아니라 한 번에 배치로 다운로드하며, LFS로 관리되는 이미지는 다운로드 전에도 온디맨드로 인라인 미리보기가 가능하고 대용량 전송 시 진행률도 보여줍니다. `.gitattributes`에 `filter=lfs`만 설정돼 있으면 별도 설정은 필요 없습니다. 직접 `git-lfs` CLI로 다운로드를 처리하고 싶다면 Settings에서 그렇게 바꿀 수도 있습니다.

파일 잠금 기능도 내장돼 있습니다: File Explorer나 Changes 패널에서 LFS로 추적되는 파일의 컨텍스트 메뉴로 잠그거나 잠금 해제(다른 사람의 잠금을 강제 해제하는 것도 가능)할 수 있고, 두 목록 모두 잠긴 파일만 걸러볼 수 있습니다. 잠금 배지가 어떤 파일이 현재 잠겨 있는지 보여줍니다.

![LFS 잠금 배지와 Locks Only 필터](assets/screenshots/lfs-locking.png)

## Timeline

**Timeline** 탭은 저장소 reflog를 시간순으로 보여줍니다 — checkout, commit, merge, rebase, reset, pull 등 HEAD가 거쳐온 모든 지점입니다. 눈에 보이는 브랜치 히스토리와 별개로 동작하는 안전망입니다. 각 항목에서:

- 해당 지점으로 바로 **checkout**
- 해당 지점에서 **새 브랜치** 생성
- 해당 커밋을 현재 브랜치로 **cherry-pick**
- 현재 브랜치를 해당 지점으로 **reset**
- 방금 Timeline으로 실수를 복구했다면 마지막 복구 동작을 **undo**

![Timeline reflog 피드](assets/screenshots/timeline.png)

---

다음: [단축키](shortcuts.ko.md)
