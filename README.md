# AI Game Maker Portfolio

게임을 만들며 어떤 규칙을 정했는지, Codex에 어떤 구현을 맡겼는지, 직접 플레이해 무엇을 바꿨는지 정리했습니다.

## MYGOATmatch

여러 캐릭터의 특징을 스킬·이동·판정 규칙으로 옮겨 대결시키는 2D 탑뷰 자동전투 게임입니다. 경기를 관전하고, 저장한 리플레이를 9:16 전투 영상 제작에 활용합니다.

**개인 프로젝트 · 2026.08–현재 · Godot 4 / C# · Windows · 개발 중**

<img align="right" width="180" src="assets/mygoatmatch-battle.gif" alt="MYGOATmatch 4인 자동전투 실제 화면. 경기장, 체력 바, 스킬 HUD가 보입니다.">

**제가 맡은 일**<br>
전투 규칙과 연출을 정하고, 직접 경기를 돌려 수정할 부분을 골랐습니다.

**Codex에 맡긴 일**<br>
관련 코드를 찾아 정해 둔 범위에서 구현하고, 회귀 테스트까지 작성하게 했습니다.

[시즌 2 전투 영상](https://www.instagram.com/p/Dey872nMY9Q/)

### AI와 작업하는 방식

> 문제 재현 → 영향 범위 확인 → 변경·유지 조건 지정 → Codex 구현 → 정적 확인·빌드 → 실제 플레이 → 다음 수정 범위 결정

<br clear="right">

### 대표 기술 판단

| 문제 | 결정 |
| --- | --- |
| 상대가 밀려난 뒤에야 다음 공격자가 출발해 연속 공격이 끊겨 보였습니다. | 상대의 도착점을 예측해 먼저 이동시키고, 넉백이 끝난 뒤 타격합니다. |
| 상대가 연속 돌진 궁극기를 시작한 뒤에도, 공격이 맞을 때마다 쌓인 효과와 화면 표시가 남았습니다. | 해당 궁극기가 시작되는 순간 기존 효과와 표시를 지우도록 했습니다. |
| 변신 외형에 기본 방향선이 겹치고 전환이 너무 빨랐습니다. | 전투 로직과 장착 기술을 재사용하고, 외형과 기술 아이콘은 단계에 맞춰 바꿨습니다. |
| 돌진으로 상대를 지나쳐도 공격이 잘 맞지 않는 것처럼 보였습니다. | 타격 범위와 이동 경로를 표시하고, 판정 범위를 탑승체 크기에 맞췄습니다. |

[기술 사례 4편](docs/MYGOATMATCH_CASE.md) · [Codex 작업 방식](docs/AI_WORKFLOW.md)

MYGOATmatch 소스 코드는 비공개입니다.<br>
캐릭터와 원작 IP의 권리는 각 권리자에게 있으며, 이 문서는 개인 프로젝트의 개발 과정과 기술적 판단을 소개합니다.

## 다른 프로젝트

### Website Escape Game

가상의 브라우저에서 여러 페이지를 탐색하며 단서와 아이템을 모아 탈출하는 웹게임입니다.

**개인 프로젝트 · 3일 제작 · React / TypeScript / Canvas · GitHub Pages 배포**

탐색부터 엔딩까지 이어지는 흐름을 정하고, Codex에 가상 브라우저와 진행 상태, 미니게임을 연결하는 구현을 맡겼습니다. 축구 미니게임에서 공이 양 팀 선수 사이를 반복해 오가자, 동시 접근을 경합으로 처리하고 킥 직후 재접촉을 막았습니다.

[바로 플레이](https://mindarinda47.github.io/website-escape-game/) · [공개 코드](https://github.com/Mindarinda47/website-escape-game-portfolio) · [제작 사례](docs/WEBSITE_ESCAPE_CASE.md)

### 붐비(Boombi) · AI 활용 설계 사례

**개인 프로젝트 · TypeScript / React · 공모전 제출 완료**

부산 혼잡 예보에서 규칙 엔진이 혼잡 점수와 추천 후보·순서를 정합니다. 모델은 행사 공지를 정리하고 추천 이유와 별도의 목적 적합도 점수를 덧붙일 수 있습니다. 응답이 검증에 실패하면 규칙 기반 결과를 사용합니다.

[설계 사례](docs/BOOMBI_CASE.md) · [공개 코드](https://github.com/Mindarinda47/boombi-ai-crowd-forecast)

## 기존 게임 개발 경험

**Unity 2D RPG Gameplay Systems** · Unity / C# · 개인 프로젝트<br>
NPC 대화·퀘스트·인벤토리·전투·저장과 불러오기를 하나의 플레이 흐름으로 연결했습니다.

**VR Disaster Simulation** · Unity / C# / Netcode for GameObjects / XR · 3인 팀<br>
PC Host–VR Client 연결, 플레이어 생성·소유권 이전·위치 동기화와 관제 기능을 맡았습니다.

[Game Programming Portfolio](https://github.com/Mindarinda47/game-programming-portfolio)
