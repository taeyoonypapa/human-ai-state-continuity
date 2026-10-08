# Human–AI State Continuity

[English](README.md) | [한국어](README_KO.md)

버전: v0.5 (2026-10-09 개정) · 상태: 실험적, 개념 단계

**장기 Human–AI 협업에서 발생하는 특정 실패 유형을 탐구하는 실험적 접근입니다. AI가 과거 맥락의 상당 부분을 재구성해 겉으로는 일관되게 보이면서도 현재 작업 상태는 잘못 도출할 수 있다는 문제에 집중합니다.**

## 핵심 주장

문제는 단순히 모델이 충분히 기억하는가가 아닙니다.

문제는 **현재 실행 가능한 상태를 올바르게 재구성하는가**입니다.

모델이 이전 대화의 대부분을 복구하더라도 다음 행동을 결정하는 하나의 미해결 문제를 놓칠 수 있습니다.

```text
90% 정확한 재구성
        +
10% 누락된 미해결 작업
        ↓
100% 잘못된 실행 결론:
"작업이 완료되었다."
```

*위 비율은 설명용이며 실측값이 아닙니다.*

여기서 이 프로젝트의 핵심 규칙이 나옵니다.

> **남은 작업이 재구성되지 않았다는 사실은 완료의 근거가 아니다.**

남은 작업이 떠오르지 않았다는 이유만으로 작업 흐름을 COMPLETE로 판정해서는 안 됩니다.

완료에는 적극적인 근거가 필요합니다.

## False Completion Failure

```text
이전 작업 상태
│
├─ 완료된 작업
├─ 인간이 확인한 결정
├─ 미해결 문제       ← 재구성에서 누락
└─ 다음 예정 작업    ← 재구성에서 누락

          ↓

새 세션에서 재구성:
완료된 작업 + 인간이 확인한 결정

          ↓

모델의 추론:
"남은 작업이 없다."

          ↓

FALSE COMPLETION
```

위험한 것은 단순한 망각 자체가 아닙니다.

> **더 위험한 실패는 불완전한 재구성으로부터 잘못된 현재 상태를 도출하는 것입니다.**

## Memory와 State는 다릅니다

대화 기억과 현재 작업 상태는 관련되어 있지만 같은 객체는 아닙니다.

```text
대화 이력
    ↓
재구성
    ↓
후보 현재 상태
    ↓
외부화된 작업 상태 근거와 검증
    ↓
계속 진행 / 재검증 / 불확실성 유지
```

재구성된 대화 맥락은 **상태에 대한 근거**로 취급하되 그 자체를 권위 있는 상태로 보지는 않습니다.

## 최소 Current Work State

공개용 최소 템플릿은 다음처럼 단순할 수 있습니다.

```text
Workstream:
Last confirmed work:
Human-confirmed decision:
Open issue:
Next intended step:
Evidence / source:
```

목적은 과거의 모든 내용을 저장하는 것이 아닙니다.

다음 행동을 결정할 가능성이 높은 최소 정보만 보존하는 것입니다.

## Completion Challenge

재구성 결과가 작업 완료를 주장할 때는 이를 기본값으로 받아들이기보다 검증 대상으로 올려야 합니다.

```text
후보 상태: COMPLETE
        ↓
확인:
- Open issue가 남아 있는가?
- Next intended step이 남아 있는가?
- 미해결 contradiction이 있는가?
- 외부화된 상태는 아직 active로 표시되는가?
- 실제 closure가 있었다는 적극적 근거가 있는가?
        ↓
미해결 불일치가 있는가?
        ↓
YES → 완료로 인정하지 않거나 재검증
NO  → 완료 가능
```

이는 운영 알고리즘이 아니라 유창하지만 근거 없는 종료 판단을 막기 위한 개념적 safeguard입니다.

## Insufficient evidence

근거가 부족할 때 시스템은 하나의 상태를 억지로 확정해서는 안 됩니다.

```text
필수 상태 근거 누락
        ↓
COMPLETE 입증 불가
        ↓
불확실성 유지
        ↓
누락 근거 요청 또는 복구
```

핵심 원칙:

> **필수 상태 필드를 근거로 확인할 수 없다면, 작업 흐름을 조용히 완료 상태로 판정해서는 안 된다.**

## 검증 모델

```text
재구성된 맥락
    +
외부화된 현재 작업 상태
    ↓
대조 / 조정
    ↓
일치       → 계속 진행
모순       → 재검증
근거 부족  → 불확실성 유지
```

목표는 완벽한 기억이 아닙니다.

목표는 불완전한 재구성이 조용히 잘못된 현재 상태로 전환될 가능성을 줄이는 것입니다.

## 인접 접근과의 차이

이 프로젝트의 중심은 recall 자체를 개선하는 것이 아닙니다.

핵심은 **상태 재구성과 종료 판단의 안전성**입니다.

| 접근 | 핵심 질문 | 강점 | 이 문제에서의 한계 |
|---|---|---|---|
| Conversational memory | 무엇을 기억해야 하는가? | recall 향상 | 기억한 내용으로도 잘못된 현재 상태를 만들 수 있음 |
| Checkpoint / persistence | 무엇이 저장되었는가? | 저장 시점 복원 | 저장된 checkpoint가 미해결 semantic state를 놓칠 수 있음 |
| Human-maintained work log | 무엇이 남아 있는가? | 명시적이고 검토 가능 | 사람의 지속적 유지관리 필요 |
| State reconciliation | 지금 올바른 실행 상태는 무엇인가? | 재구성과 수용을 분리 | 외부화된 상태 표현과 검증 단계 필요 |

이 접근들은 서로 배타적이라는 주장이 아닙니다.

State reconciliation은 memory, checkpoint, human work log 위에 추가될 수 있습니다.

## 왜 중요한가

장기 Human–AI 협업은 세션, 문서, 결정, 미해결 문제, 다음 예정 작업 사이의 연속성에 의존합니다.

많은 사실을 기억하더라도 현재 실행 가능한 상태를 잃은 시스템은 겉으로는 일관되게 보이면서 실제로는 운영적으로 잘못된 상태일 수 있습니다.

따라서 **상태 연속성**은 일반적인 memory retrieval과 구분되는 문제입니다.

## 권한 경계

추론된 현재 상태가 중요한 행동을 촉발한다면 별도의 결정 경계가 필요할 수 있습니다.

```text
재구성된 상태
    ↓
검증된 현재 상태
    ↓
결정 경계
    ↓
중요한 행동
```

이 저장소의 중심은 그 주변의 통제 아키텍처 전반이 아니라 연속성 문제 자체입니다.

## 저장소 구성

- [`docs/reconstruction-vs-memory.md`](docs/reconstruction-vs-memory.md)
- [`docs/current-work-state.md`](docs/current-work-state.md)
- [`docs/completion-challenge.md`](docs/completion-challenge.md)
- [`docs/validation-model.md`](docs/validation-model.md)
- [`docs/adjacent-approaches.md`](docs/adjacent-approaches.md)
- [`docs/limitations.md`](docs/limitations.md)
- [`cases/false-completion.md`](cases/false-completion.md)
- [`evaluation/open-questions.md`](evaluation/open-questions.md)
- [`README.md`](README.md)
- [`LICENSE`](LICENSE)

## 공개 범위

이 저장소는 **문제 구조와 개념적 대응**만 다룹니다. 운영용 상태 스키마와 구현 세부는 범위에 포함하지 않으므로, 여기 제시된 내용은 구현으로 검증된 결과가 아니라 개념적 제안입니다.

## 알려진 한계

외부화된 상태 자체가 불완전하거나 낡았을 수 있다는 점 등 이 접근에는 실질적인 약점이 있습니다. [`docs/limitations.md`](docs/limitations.md)를 참고하세요. (영문)

## 프로젝트 상태

실험적 연구 프로젝트이며 운영 준비가 완료된 continuity framework 또는 일반적으로 검증된 표준으로 제시하지 않습니다.

공개의 목적은 문제 정의, memory와 state의 구분, completion rule, 개념적 검증 모델에 대한 외부 비판을 받는 것입니다.

단순한 지지보다 비판적인 피드백을 선호합니다.

## 라이선스

이 저작물은 [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0/)(CC BY 4.0)에 따라 이용할 수 있습니다. [`LICENSE`](LICENSE)를 참고하세요.

Copyright 2026 KIWON KIM

재사용하거나 인용할 때는 이 저장소(Human–AI State Continuity)를 출처로 밝히고 링크를 달아 주세요.

## 피드백

이 저장소의 GitHub Issues 또는 Discussions를 이용해 주세요. 반례, 더 단순한 대안, 기존 연구 소개가 가장 도움이 됩니다.
