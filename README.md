# LLM 모델 비교 — Gemini 2.5\~3.1 · GPT-5\~5.5

> 작성일: 2026-05-21
> 가격: USD / 1M tokens. ₩ 환산은 1 USD = 1,400 KRW 가정. Per-call 비용은 μ$ = $0.000001 단위 사용.
> Standard rate(batch 미적용), ≤200K context 기준.

---

## TL;DR — 한눈에 보기

### 입력 단가 (저렴한 순)

| 순위 | 모델 | $/1M | ₩/1M |
|---:|---|---:|---:|
| 1 | GPT-5 nano | 0.05 | 70 |
| 2 | Gemini 2.5 Flash-Lite | 0.10 | 140 |
| 3 | GPT-5.4 nano | 0.20 | 280 |
| 4 | Gemini 3.1 Flash-Lite · GPT-5 mini | 0.25 | 350 |
| 6 | Gemini 2.5 Flash | 0.30 | 420 |
| 7 | Gemini 3 Flash | 0.50 | 700 |
| 8 | GPT-5.4 mini | 0.75 | 1,050 |
| 9 | Gemini 2.5 Pro · GPT-5 | 1.25 | 1,750 |
| 11 | Gemini 3.1 Pro | 2.00 | 2,800 |
| 12 | GPT-5.4 | 2.50 | 3,500 |
| 13 | GPT-5.5 | 5.00 | 7,000 |

### 출력 단가 (저렴한 순)

| 순위 | 모델 | $/1M | ₩/1M |
|---:|---|---:|---:|
| 1 | Gemini 2.5 Flash-Lite · GPT-5 nano | 0.40 | 560 |
| 3 | GPT-5.4 nano | 1.25 | 1,750 |
| 4 | Gemini 3.1 Flash-Lite | 1.50 | 2,100 |
| 5 | GPT-5 mini | 2.00 | 2,800 |
| 6 | Gemini 2.5 Flash | 2.50 | 3,500 |
| 7 | Gemini 3 Flash | 3.00 | 4,200 |
| 8 | GPT-5.4 mini | 4.50 | 6,300 |
| 9 | Gemini 2.5 Pro · GPT-5 | 10.00 | 14,000 |
| 11 | Gemini 3.1 Pro | 12.00 | 16,800 |
| 12 | GPT-5.4 | 15.00 | 21,000 |
| 13 | GPT-5.5 | 30.00 | 42,000 |

### 지연시간 (TTFT 짧은 순)

| 순위 | 모델 | TTFT (s) |
|---:|---|---:|
| 1 | GPT-5.4 nano (non-reasoning) | 0.57 |
| 2 | Gemini 2.5 Flash | 0.65 |
| 3 | GPT-5 nano (minimal) | 0.85 |
| 4 | Gemini 2.5 Flash-Lite | 1.66 |
| 5 | GPT-5.4 nano (xhigh) | 3.36 |
| 6 | GPT-5.4 nano (medium) | 3.93 |
| 7 | Gemini 3.1 Flash-Lite (reasoning) | 5.06 |
| 8 | Gemini 3 Flash (reasoning) | 7.06 |
| 9 | GPT-5.4 mini (xhigh) | 11.82 |
| 10 | Gemini 2.5 Pro (reasoning) | 20.49 |
| 11 | Gemini 3.1 Pro (reasoning) | 26.21 |
| 12 | GPT-5 nano (high) | 101.01 |

> GPT-5 · GPT-5 mini · GPT-5.4 · GPT-5.5는 Artificial Analysis 벤치마크 미공개로 제외.
> AA 캡처일 2026-05-21 기준. 시점·프로바이더에 따라 변동.

### 한/영 토큰 효율

| 입력 | OpenAI `o200k_base` | Gemini SentencePiece | 차이 |
|---|---:|---:|---|
| 한국어 단어 (`안녕하세요`) | 2 | 2 | 동일 |
| 영어 단어 (`Hello`) | 1 | 2 | OpenAI 50% 절감 |
| 한국어 문장 (~14자) | 9 | 10 | 거의 동일 |
| 영어 문장 (~6단어) | 7 | 8 | 거의 동일 |

> 영어 짧은 단어가 빈번한 워크로드에서만 OpenAI가 토큰 효율 우위. 그 외엔 사실상 동률.

---

## 1. 테스트 문구 토큰 수

각 모델 토크나이저로 측정한 실제 값.

| 문구 | OpenAI `o200k_base` (GPT-5 계열) | Gemini (`count_tokens` API) |
|---|---:|---:|
| `안녕하세요` | **2** | **2** |
| `Hello` | **1** | **2** |
| `이 문장은 테스트용 문장입니다.` | **9** | **10** |
| `This sentence is for a test.` | **7** | **8** |

> OpenAI는 BPE(`o200k_base`)로 영어 단일어를 1토큰으로 묶지만, Gemini SentencePiece는 짧은 영어어도 보통 2토큰. 한국어는 두 토크나이저가 거의 같은 효율을 보임.

---

## 2. 대상 모델 카탈로그 & 베이스 가격

| 모델 | 입력 $/1M | 출력 $/1M | 입력 ₩/1M | 출력 ₩/1M | 비고 |
|---|---:|---:|---:|---:|---|
| **Gemini 2.5 Pro** | 1.25 | 10.00 | 1,750 | 14,000 | 2025 flagship, reasoning, ≤200K |
| **Gemini 2.5 Flash** | 0.30 | 2.50 | 420 | 3,500 | 2025 mid |
| **Gemini 2.5 Flash-Lite** | 0.10 | 0.40 | 140 | 560 | 2025 저가 |
| **Gemini 3 Flash** | 0.50 | 3.00 | 700 | 4,200 | reasoning, Preview |
| **Gemini 3.1 Pro** | 2.00 | 12.00 | 2,800 | 16,800 | 현 flagship, reasoning, ≤200K (>200K: 4.00/18.00) |
| **Gemini 3.1 Flash-Lite** | 0.25 | 1.50 | 350 | 2,100 | 현 저가, Preview, reasoning. output 314.8 t/s 최상위 |
| **GPT-5** | 1.25 | 10.00 | 1,750 | 14,000 | 2025 flagship |
| **GPT-5 mini** | 0.25 | 2.00 | 350 | 2,800 | 2025 mid |
| **GPT-5 nano** | 0.05 | 0.40 | 70 | 560 | 2025 최저가 |
| **GPT-5.4** | 2.50 | 15.00 | 3,500 | 21,000 | 2026 flagship, ≤272K |
| **GPT-5.4 mini** | 0.75 | 4.50 | 1,050 | 6,300 | 2026 mid |
| **GPT-5.4 nano** | 0.20 | 1.25 | 280 | 1,750 | 2026 저가 |
| **GPT-5.5** | 5.00 | 30.00 | 7,000 | 42,000 | 2026-04 최신 flagship |

---

## 3. Input 비용 비교표 (μ$ per call)

각 문구를 1회 입력 전송할 때 비용. `μ$ = 0.000001 USD` 이므로 100만 곱하면 USD/1M-call.

| 모델 | 안녕하세요 | Hello | 이 문장은 테스트용 문장입니다. | This sentence is for a test. |
|---|---:|---:|---:|---:|
| Gemini 2.5 Pro | 2.500 | 2.500 | 12.500 | 10.000 |
| Gemini 2.5 Flash | 0.600 | 0.600 | 3.000 | 2.400 |
| Gemini 2.5 Flash-Lite | 0.200 | 0.200 | 1.000 | 0.800 |
| Gemini 3 Flash | 1.000 | 1.000 | 5.000 | 4.000 |
| Gemini 3.1 Pro | 4.000 | 4.000 | 20.000 | 16.000 |
| Gemini 3.1 Flash-Lite | 0.500 | 0.500 | 2.500 | 2.000 |
| GPT-5 | 2.500 | 1.250 | 11.250 | 8.750 |
| GPT-5 mini | 0.500 | 0.250 | 2.250 | 1.750 |
| GPT-5 nano | 0.100 | 0.050 | 0.450 | 0.350 |
| GPT-5.4 | 5.000 | 2.500 | 22.500 | 17.500 |
| GPT-5.4 mini | 1.500 | 0.750 | 6.750 | 5.250 |
| **GPT-5.4 nano** (현 프로젝트) | **0.400** | **0.200** | **1.800** | **1.400** |
| GPT-5.5 | 10.000 | 5.000 | 45.000 | 35.000 |

---

## 4. Output 비용 비교표 (μ$ per call)

각 문구를 1회 출력할 때 비용.

| 모델 | 안녕하세요 | Hello | 이 문장은 테스트용 문장입니다. | This sentence is for a test. |
|---|---:|---:|---:|---:|
| Gemini 2.5 Pro | 20.00 | 20.00 | 100.00 | 80.00 |
| Gemini 2.5 Flash | 5.00 | 5.00 | 25.00 | 20.00 |
| Gemini 2.5 Flash-Lite | 0.80 | 0.80 | 4.00 | 3.20 |
| Gemini 3 Flash | 6.00 | 6.00 | 30.00 | 24.00 |
| Gemini 3.1 Pro | 24.00 | 24.00 | 120.00 | 96.00 |
| Gemini 3.1 Flash-Lite | 3.00 | 3.00 | 15.00 | 12.00 |
| GPT-5 | 20.00 | 10.00 | 90.00 | 70.00 |
| GPT-5 mini | 4.00 | 2.00 | 18.00 | 14.00 |
| GPT-5 nano | 0.80 | 0.40 | 3.60 | 2.80 |
| GPT-5.4 | 30.00 | 15.00 | 135.00 | 105.00 |
| GPT-5.4 mini | 9.00 | 4.50 | 40.50 | 31.50 |
| **GPT-5.4 nano** (현 프로젝트) | **2.50** | **1.25** | **11.25** | **8.75** |
| GPT-5.5 | 60.00 | 30.00 | 270.00 | 210.00 |

---

## 5. 평균 지연시간 비교표 (초)

`latency ≈ TTFT + (output_tokens / output_speed)`. 출력 토큰 수는 각 문구 길이(섹션 1).
Artificial Analysis 캡처일: **2026-05-21**. 변종(reasoning effort)이 공개된 경우 함께 표기.

| 모델 | TTFT (s) | Out speed (t/s) | 안녕하세요 | Hello | KR 문장 | EN 문장 |
|---|---:|---:|---:|---:|---:|---:|
| Gemini 2.5 Pro (reasoning) | 20.49 | 128.6 | 20.51 | 20.51 | 20.57 | 20.55 |
| Gemini 2.5 Flash | 0.65 | 199.3 | 0.66 | 0.66 | 0.70 | 0.69 |
| Gemini 2.5 Flash-Lite | 1.66 | 191.4 | 1.67 | 1.67 | 1.71 | 1.70 |
| Gemini 3 Flash (reasoning) | 7.06 | 175.3 | 7.07 | 7.07 | 7.12 | 7.11 |
| Gemini 3.1 Pro (reasoning) | 26.21 | 119.5 | 26.23 | 26.23 | 26.29 | 26.28 |
| Gemini 3.1 Flash-Lite (reasoning) | 5.06 | 314.8 | 5.07 | 5.07 | 5.09 | 5.09 |
| GPT-5 nano (minimal) | 0.85 | 150.6 | 0.86 | 0.86 | 0.91 | 0.90 |
| GPT-5 nano (high) | 101.01 | 150.4 | 101.02 | 101.02 | 101.07 | 101.06 |
| **GPT-5.4 nano (non-reasoning)** | **0.57** | **165.9** | **0.58** | **0.58** | **0.62** | **0.61** |
| GPT-5.4 nano (medium) | 3.93 | 154.7 | 3.94 | 3.94 | 3.99 | 3.98 |
| GPT-5.4 nano (xhigh) | 3.36 | 156.1 | 3.37 | 3.37 | 3.42 | 3.40 |
| GPT-5.4 mini (xhigh) | 11.82 | 170.1 | 11.83 | 11.83 | 11.87 | 11.86 |

> 짧은 문구에서는 latency가 사실상 **TTFT가 좌우**. output speed 영향은 0.01~0.06s 수준.
> **벤치마크 미공개**: GPT-5, GPT-5 mini, GPT-5.4, GPT-5.5.
> AA 수치는 시점·프로바이더에 따라 변동. 정확한 production 비교 시 자체 측정 권장.

---

## 6. 핵심 관찰

### 가성비
- **GPT-5 nano**: 입력 절대 최저가 ($0.05). Gemini 2.5 Flash-Lite보다 입력 50%, 출력 동률($0.40).
- **Gemini 2.5 Flash-Lite**: 출력 최저가 공동 1위 ($0.40), 입력은 $0.10. TTFT 1.66s.
- **현재 사용 중인 GPT-5.4 nano** ($0.20/$1.25): GPT-5 nano 대비 입력 4배·출력 3배 비용. non-reasoning 모드는 TTFT 0.57s로 최단.

### 지연시간
- 가장 빠름: **GPT-5.4 nano non-reasoning (0.57s)** > Gemini 2.5 Flash (0.65s) > GPT-5 nano minimal (0.85s) > Gemini 2.5 Flash-Lite (1.66s).
- Pro 계열 reasoning 모델(Gemini 2.5/3.1 Pro)은 TTFT 20~26s로 짧은 문답에 부적합.
- Gemini 3.1 Flash-Lite는 output speed(314.8 t/s)가 최상위지만 reasoning 모델이라 TTFT는 5.06s. 긴 출력엔 유리, 짧은 응답엔 불리.
- GPT-5 계열은 reasoning effort에 따라 편차가 큼: GPT-5 nano minimal 0.85s → high 101s, GPT-5.4 nano non-reasoning 0.57s → xhigh 3.36s. 사용 시 effort 명시 권장.

### 한·영 토큰 효율
- "Hello" 1글자가 OpenAI는 1토큰, Gemini는 2토큰 → 영어 짧은 단어가 빈번하면 OpenAI 비용 50% 절감.
- "안녕하세요"는 양쪽 모두 2토큰으로 동일.
- 긴 문장은 토큰 수 차이가 약 1~2개라 큰 영향 없음.

### 현재 프로젝트(`gpt-5.4-nano` 통일) 비교 포인트
- KR 문장 한 건당 input 1.8μ$ + output 11.25μ$ = 13μ$ 전후.
- 같은 작업을 Gemini 2.5 Flash-Lite로 하면 input 1μ$ + output 4μ$ = 5μ$로 약 60% 절감 가능.
- 다만 ① 한국어 reasoning 품질 차이, ② 출력 포맷 안정성, ③ 503 가용성 이슈는 별도 평가 필요.

---

## 7. 가정 & 한계

1. **환율 가정**: ₩ 환산은 1 USD = 1,400 KRW로 일괄 계산. 실제 결제 시점 환율·카드 수수료에 따라 ±5% 변동 가능.
2. **가격 출처 다양성**: Gemini 2.5 Pro 가격은 출처마다 $1.00 ~ $1.25 사이로 보고됨. Google 공식 docs 기준 $1.25 채택. >200K context 구간은 별도 가격으로 본 표는 ≤200K 기준.
3. **latency 누락**: GPT-5, GPT-5 mini, GPT-5.4, GPT-5.5는 Artificial Analysis에 해당 변종 벤치마크가 일관되지 않거나 미게재. 추정치 대신 표에서 제외.
4. **Reasoning effort 가변**: GPT-5 계열은 `non-reasoning/minimal/medium/high/xhigh` 옵션마다 TTFT가 0.57s ~ 101s로 천차만별. 사용 시 명시적으로 effort 설정 권장.
5. **벤치마크 환경**: TTFT/output speed는 Artificial Analysis 캡처(2026-05-21) 기준 평균치. 실제 production 부하·지역·시간대에 따라 차이가 큼.
6. **batch 모드 미반영**: Gemini/OpenAI 모두 batch API 50% 할인 옵션 있으나 본 표는 standard rate 기준.

---

## Sources

**가격 (섹션 2 카탈로그)** — Gemini는 Google 공식 docs, GPT 계열은 OpenAI 공식 pricing/모델 페이지.
**TTFT · output speed (섹션 5)** — Artificial Analysis 모델별 페이지.
**토큰 수 (섹션 1)** — OpenAI는 `tiktoken o200k_base`, Gemini는 `count_tokens` API 실측.

- [Gemini Developer API pricing | Google AI for Developers](https://ai.google.dev/gemini-api/docs/pricing)
- [Gemini 2.5 Pro - Artificial Analysis](https://artificialanalysis.ai/models/gemini-2-5-pro)
- [Gemini 2.5 Flash - Artificial Analysis](https://artificialanalysis.ai/models/gemini-2-5-flash)
- [Gemini 2.5 Flash-Lite - Artificial Analysis](https://artificialanalysis.ai/models/gemini-2-5-flash-lite)
- [Gemini 3 Flash - Artificial Analysis](https://artificialanalysis.ai/models/gemini-3-flash-reasoning)
- [Gemini 3.1 Pro Preview - Artificial Analysis](https://artificialanalysis.ai/models/gemini-3-1-pro-preview)
- [Gemini 3.1 Flash-Lite Preview - Artificial Analysis](https://artificialanalysis.ai/models/gemini-3-1-flash-lite-preview)
- [Gemini 3.1 Flash Lite is now stable | Google Blog](https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-3-1-flash-lite/)
- [OpenAI API Pricing](https://openai.com/api/pricing/)
- [GPT-5 nano Model | OpenAI API](https://developers.openai.com/api/docs/models/gpt-5-nano)
- [GPT-5.4 nano Model | OpenAI API](https://developers.openai.com/api/docs/models/gpt-5.4-nano)
- [Introducing GPT-5.4 mini and nano | OpenAI](https://openai.com/index/introducing-gpt-5-4-mini-and-nano/)
- [GPT-5 nano (minimal) - Artificial Analysis](https://artificialanalysis.ai/models/gpt-5-nano-minimal/providers)
- [GPT-5.4 nano - Artificial Analysis](https://artificialanalysis.ai/models/gpt-5-4-nano-medium/providers)
- [GPT-5.4 mini - Artificial Analysis](https://artificialanalysis.ai/models/gpt-5-4-mini-non-reasoning/providers)
- [GPT-5.5 Pricing Breakdown](https://aicostcheck.com/blog/gpt-5-pricing-breakdown)
