# AI Game Maker Portfolio

게임 규칙과 구현 방향을 정한 뒤, 기존 코드를 살펴보고 기능을 구현하는 데 Codex를 활용합니다. 게임을 직접 실행해 예상과 다른 동작을 확인하고, 다음 수정에서 바꿀 조건과 유지할 동작을 정리합니다.

> 문제 재현 → 영향 범위 확인 → 변경·유지 조건 지정 → Codex 구현 → 정적 확인·빌드 → 실제 플레이 → 다음 수정 범위 결정

## 대표 프로젝트 · MYGOATmatch

**Godot · C# | Windows | 개발 중**

룰과 경기장을 바꿔 자동 전투를 돌리고, 저장한 경기의 리플레이를 9:16 촬영 화면에서 다시 보는 프로젝트입니다. 전투 규칙과 화면에 표시하는 코드가 함께 얽혀 있어, 수정할 때는 먼저 어느 쪽에서 문제가 생겼는지 확인했습니다. [시즌 2 전투 영상](https://www.instagram.com/p/Dey872nMY9Q/)

| 기술 문제 | 내가 내린 결정 |
| --- | --- |
| 미래 위치 예측으로 연속 공격 연결 | 상대가 밀리는 동안 도착점을 계산해, 넉백이 끝날 때 다음 공격자가 준비 위치에 있도록 했습니다. |
| 상태별 피해·누적·해제 규칙 분리 | 지정된 스킬로 멈추거나 돌진하면 피해는 적용하고 누적 효과 증가는 막되 타이머는 계속 흐릅니다. 특정 상태 전환 시 기존 효과를 초기화합니다. |
| 공용 전투 상태와 전용 표시의 책임 분리 | 변신은 상대의 장착 기술과 전투 로직을 재사용하고, 외형과 HUD는 변신 단계에 맞춰 전환하게 했습니다. |
| 판정·상태 전이·VFX를 별도로 확인 | 질주 히트박스를 표시해 화면 크기와 비교하도록 하고, 다운 발동 시점과 총공격 연출을 따로 점검했습니다. |

[기술 사례 4편](docs/MYGOATMATCH_CASE.md) · [Codex에 일을 맡기고 확인하는 과정](docs/AI_WORKFLOW.md)

## 다른 프로젝트

**Website Escape Game** · 해커톤 사전과제로 3일 동안 제작해 배포한 웹게임입니다. 축구 미니게임에서 공이 양 팀 선수 사이를 왕복하자, 동시 접근을 경합으로 처리하고 킥 직후 재접촉을 막았습니다. [제작 사례](docs/WEBSITE_ESCAPE_CASE.md) · [바로 플레이](https://mindarinda47.github.io/website-escape-game/)

**붐비(Boombi)** · 부산 혼잡 예보 서비스입니다. 모델에는 행사 공지 해석과 결과 설명을 맡겼습니다. 혼잡 점수와 추천 순서는 규칙 엔진이 계산하며, 모델 응답이 검증에 실패해도 규칙 결과를 제공합니다. [설계 사례](docs/BOOMBI_CASE.md) · [공개 코드](https://github.com/Mindarinda47/boombi-ai-crowd-forecast)

## Game Programming Foundation

Unity 2D RPG와 VR 네트워크 프로젝트 등 기존 개발 작업은 종합 포트폴리오에 정리했습니다. [Game Programming Portfolio](https://github.com/Mindarinda47/game-programming-portfolio)
