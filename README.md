# AI Game Maker Portfolio

게임과 서비스를 만들며 직접 내린 결정, AI에 맡긴 일, 결과를 확인하고 수정한 과정을 정리했습니다.

## MYGOATmatch

캐릭터마다 다른 스킬과 전투 규칙을 가진 2D 탑뷰 자동전투 게임입니다. 관전할 때 각 캐릭터의 싸움 방식이 드러나도록 만들고, 저장한 리플레이는 9:16 전투 영상에 활용합니다.

**개인 프로젝트 · 2026.08–현재 · Godot 4 / C# · Windows · 개발 중**

<img align="right" width="160" src="assets/mygoatmatch-battle.gif" alt="MYGOATmatch 4인 자동전투 실제 화면. 경기장, 체력 바, 스킬 HUD가 보입니다.">

**제가 맡은 일**<br>
캐릭터별 전투 규칙과 발동 조건, 연출을 정하고 경기를 돌려 수정할 부분을 골랐습니다.

**Codex에 맡긴 일**<br>
관련 코드를 찾아 정해 둔 범위에서 구현·수정하고, 필요한 회귀 테스트를 작성하게 했습니다.

[시즌 2 전투 영상](https://www.instagram.com/p/Dey872nMY9Q/)<br>
[기술 사례 4편](docs/MYGOATMATCH_CASE.md) · [Codex 작업 방식](docs/AI_WORKFLOW.md)

<br clear="right">

경기에서 발견한 문제는 판정 범위 표시와 리플레이로 확인했습니다.

MYGOATmatch 소스 코드는 비공개입니다.<br>
캐릭터와 원작 IP의 권리는 각 권리자에게 있으며, 이 문서는 개인 프로젝트의 개발 과정과 기술적 판단을 소개합니다.

## 다른 프로젝트

### Website Escape Game

가상의 웹 브라우저에서 여러 페이지를 탐색해 단서와 아이템을 찾고, 퍼즐과 미니게임을 거쳐 탈출하는 게임입니다.

**개인 프로젝트 · 3일 제작 · React / TypeScript / Canvas · GitHub Pages 배포**

탐색부터 엔딩까지의 흐름을 먼저 정하고, Codex에 가상 브라우저·진행 상태·미니게임을 구현하고 연결하는 일을 맡겼습니다. 이후 플레이테스트에서 막히는 구간을 확인해 힌트와 진행 흐름을 다듬었습니다.

[바로 플레이](https://mindarinda47.github.io/website-escape-game/) · [공개 코드](https://github.com/Mindarinda47/website-escape-game-portfolio) · [제작 사례](docs/WEBSITE_ESCAPE_CASE.md)

### 붐비(Boombi)

부산의 시간대별 혼잡 가능성과 덜 붐비는 대체 장소를 보여주는 서비스입니다.

**개인 프로젝트 · TypeScript / React · 공모전 제출 완료**

모델은 형식이 제각각인 행사 공지를 정리하고 추천 이유를 설명합니다. 혼잡 점수와 추천 장소·순서는 코드가 계산합니다. 모델 호출이 실패하거나 응답이 검증을 통과하지 못하면 규칙으로 계산한 결과를 보여주도록 설계했습니다.

[설계 사례](docs/BOOMBI_CASE.md) · [공개 코드](https://github.com/Mindarinda47/boombi-ai-crowd-forecast)

## 기존 게임 개발 경험

**Unity 2D RPG Gameplay Systems** · Unity / C# · 개인 프로젝트<br>
NPC 대화·퀘스트·인벤토리·전투·저장과 불러오기를 하나의 플레이 흐름으로 연결했습니다.

**VR Disaster Simulation** · Unity / C# / Netcode for GameObjects / XR · 3인 팀<br>
PC Host–VR Client 연결, 플레이어 생성·소유권 이전·위치 동기화와 관제 기능을 맡았습니다.

[Game Programming Portfolio](https://github.com/Mindarinda47/game-programming-portfolio)
