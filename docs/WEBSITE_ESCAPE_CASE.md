# Website Escape Game — 3일 동안 플레이 가능한 웹게임 제작

[포트폴리오](../README.md) · [바로 플레이](https://mindarinda47.github.io/website-escape-game/) · [공개 코드](https://github.com/Mindarinda47/website-escape-game-portfolio)

해커톤 본선 전 개인 사전과제로, 가상의 브라우저에서 페이지를 탐색하고 아이템과 단서를 조합해 탈출하는 게임을 만들었습니다. **2026년 8월 8~10일**의 구현·배포 기록과 프로젝트 README를 기준으로 한 3일 작업입니다. React·TypeScript·Vite로 웹 화면을 만들고, Canvas로 액션 미니게임을 구현했습니다. [개발 커밋](https://github.com/Mindarinda47/website-escape-game/commits/main/)

## 한 번 플레이할 수 있는 흐름부터 연결

저는 주소창과 페이지 내 찾기, 화면 테마 변경을 퍼즐 행동으로 쓰고 뉴스·쇼핑·스포츠 페이지의 단서와 보상이 미니게임으로 이어지도록 기획했습니다. Codex에 명세를 주고 가상 브라우저, 인벤토리와 진행 상태, Canvas 미니게임을 연결해 첫 버전에서 엔딩까지 도달할 수 있게 했습니다. 이후 스포츠 보상으로 열쇠를 얻는 흐름을 다듬고, 별도 작업으로 RPG 맵·전투·보스 패턴을 확장했습니다. [게임 구조](https://github.com/Mindarinda47/website-escape-game-portfolio/blob/main/docs/architecture.md)

## 공을 동시에 잡으려 할 때의 규칙

축구 승부예측 화면에서 양 팀 선수가 동시에 공에 붙으면 공이 둘 사이를 계속 오갔습니다. Codex에 이 장면을 설명하고, 두 선수가 동시에 닿는 순간 공이 튕겨 나가도록 요청했습니다. 후속 경기에서는 득점 직후에도 선수들이 기존 위치에 남아 공격 패턴이 반복됐습니다. 그 상황에서는 대형을 다시 배치하고, 실점한 팀이 중앙에서 시작하도록 요청했습니다.

현재 코드에서는 팀마다 공을 쫓는 필드 선수를 한 명으로 두고, 나머지는 대형을 바탕으로 움직입니다. 양 팀이 점유 범위에 동시에 들어오면 경합으로 처리해 공을 튕깁니다. 바로 다시 공을 건드리는 일을 막기 위해 Codex가 짧은 재접촉 쿨다운을 넣었습니다. 회귀 테스트는 득점 후 대형과 킥오프, 직전 패서에게 즉시 돌아가는 패스, 공수 전환 시 수비 대형을 각각 확인합니다. [경기 시뮬레이션](https://github.com/Mindarinda47/website-escape-game-portfolio/blob/main/src/pages/SportsPage.tsx) · [회귀 테스트](https://github.com/Mindarinda47/website-escape-game-portfolio/blob/main/src/test/sportsSimulation.test.ts)

## 지인 테스트 후 힌트 강도를 조정

초기에는 진행률 문구가 정답의 방향을 지나치게 쉽게 알려줘, 완료한 페이지의 테두리 발광으로 피드백을 바꿨습니다. 이후 지인에게 게임을 플레이해 달라고 했을 때는 힌트를 보강할 필요가 있다는 의견을 받았습니다. 이에 인벤토리 처음부터 문자 단서의 빈칸 여섯 개를 보여주고, 찾은 문자를 드래그로 배열하며, 더 필요한 힌트는 마을의 점술가에게 물을 수 있게 했습니다. Codex에 인벤토리·저장 상태와 점술가 대화를 연결하도록 맡겼습니다. [인벤토리 코드](https://github.com/Mindarinda47/website-escape-game-portfolio/blob/main/src/browser/InventoryDrawer.tsx) · [미니게임 코드](https://github.com/Mindarinda47/website-escape-game-portfolio/blob/main/src/minigame/AdventureCanvas.tsx)

최종 버전은 GitHub Actions에서 테스트와 빌드를 거쳐 GitHub Pages로 배포했습니다. 짧은 일정에 탐색과 엔딩을 먼저 연결해 두었기 때문에 이후에는 미니게임을 보강하고, 플레이테스트에서 드러난 막힘을 수정하는 데 집중할 수 있었습니다. [배포 워크플로](https://github.com/Mindarinda47/website-escape-game/blob/main/.github/workflows/deploy-pages.yml) · [플레이 영상](https://youtu.be/Y9AoMUE8m2I)
