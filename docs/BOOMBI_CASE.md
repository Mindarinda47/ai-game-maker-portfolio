# 붐비(Boombi) — 혼잡 점수와 AI 설명의 경계

[포트폴리오](../README.md) · [공개 코드](https://github.com/Mindarinda47/boombi-ai-crowd-forecast)

붐비는 부산의 권역별·시간대별 혼잡 가능성과 대체 장소를 보여주는 1인 개발 서비스입니다. 형식이 제각각인 행사 공지는 모델이 구조화하고, 사용자에게 보여주는 혼잡 점수와 추천 순서는 규칙 엔진이 계산합니다.

## 모델에 맡긴 일과 코드가 결정하는 결과

규칙 엔진에 같은 입력을 주면 같은 혼잡 점수가 나옵니다. 평시 기준값은 권역 특성과 시간대별 패턴을 바탕으로 설정했고, 점수는 상대적인 혼잡 가능성을 나타냅니다. 현장 인원 수와 비교한 정확도는 검증하지 않았습니다.

| 단계 | 구현 |
| --- | --- |
| 행사 입력 | 모델이 공지·포스터의 날짜, 장소, 행사 규모, 선착순 여부 같은 항목을 JSON으로 정리합니다. 응답은 필드 타입, 허용된 범주, 배열 길이, 신뢰도 범위를 검사한 뒤 사용합니다. |
| 혼잡 예보 | 규칙 엔진이 평시 기준값, 검색 추세, 요일·공휴일, 행사 속성, 날씨 등을 받아 0~100점과 혼잡 단계를 계산합니다. 모델이 추출한 행사 속성은 계산에 들어가는 입력입니다. |
| 대체 장소 | 코드가 후보 3곳과 순서를 먼저 계산합니다. 모델이 반환한 후보 ID가 중복되거나 순서가 다르면 규칙 결과를 반환합니다. 혼잡 점수와 권장 방문 구간은 예보 값을 사용하며, 후보의 별도 **목적 적합도**는 모델이 0~100 범위로 반환할 수 있습니다. |
| 조건 비교 | 코드가 기준·시나리오 점수를 계산합니다. 모델이 반환하는 값은 변화 이유, 방문 안내 문구, 불확실성 설명에 사용합니다. |

[행사 응답 검증](https://github.com/Mindarinda47/boombi-ai-crowd-forecast/blob/main/providers/openai-event-analysis.ts) · [점수 계산](https://github.com/Mindarinda47/boombi-ai-crowd-forecast/blob/main/domain/forecast/score.ts) · [추천·비교 응답 처리](https://github.com/Mindarinda47/boombi-ai-crowd-forecast/blob/main/providers/openai-decisions.ts)

## 데이터와 모델에 문제가 생겼을 때

기본 설정의 모델 호출은 Gemini에서 실패하면 Groq로 넘어갑니다. 둘 다 사용할 수 없거나 유효한 결과가 없으면 행사 분석은 원문 키워드에 기반한 기본 분류로, 추천·비교는 규칙으로 계산한 결과로 응답합니다. 행사 갱신은 원문이 바뀌었는지 확인해 이전 분석을 재사용하고, 새로 분석할 건에 호출 한도를 둡니다. 예보 조회는 저장된 예보를 우선 사용하며, 저장소에서 읽지 못하면 기본 예보에 사용 가능한 외부 데이터를 합칩니다. [모델 전환](https://github.com/Mindarinda47/boombi-ai-crowd-forecast/blob/main/providers/ai-runtime.ts) · [행사 갱신](https://github.com/Mindarinda47/boombi-ai-crowd-forecast/blob/main/providers/event-refresh.ts) · [예보 조회](https://github.com/Mindarinda47/boombi-ai-crowd-forecast/blob/main/app/api/public/forecast/route.ts)
