LLM-comparison repo  
입출력 비용, 지연시간 메모  

<br>

# LLM 모델 비교 — Gemini 2.5~3.1 & GPT-5 계열

> 작성일: 2026-05-19
> 가격은 모두 USD / 1M tokens 기준. 한국 시장에 익숙한 microdollar(μ$) = $0.000001 단위 사용.

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

| 모델 | 입력 ($/1M) | 출력 ($/1M) | 비고 |
|---|---:|---:|---|
| **Gemini 2.5 Pro** | 1.25 | 10.00 | reasoning, ≤200K |
| **Gemini 2.5 Flash** | 0.30 | 2.50 | 일반 |
| **Gemini 2.5 Flash-Lite** | 0.10 | 0.40 | 최저가 |
| **Gemini 3 Flash** | 0.50 | 3.00 | reasoning, Preview |
| **Gemini 3.1 Pro** | 2.00 | 12.00 | reasoning, ≤200K (>200K: 4.00/18.00) |
| **Gemini 3.1 Flash-Lite** | 0.25 | 1.50 | Preview, 최고속 |
| **GPT-5** | 1.25 | 10.00 | 구세대 flagship |
| **GPT-5 mini** | 0.25 | 2.00 | 구세대 mid |
| **GPT-5 nano** | 0.05 | 0.40 | 구세대 최저가 |
| **GPT-5.4** | 2.50 | 15.00 | 현 flagship, ≤272K |
| **GPT-5.4 mini** | 0.75 | 4.50 | 현 mid |
| **GPT-5.4 nano** | 0.20 | 1.25 | 현 저가 |
| **GPT-5.5** | 5.00 | 30.00 | 2026-04 신모델 |

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

`latency ≈ TTFT + (output_tokens / output_speed)`

Artificial Analysis 공개 벤치마크의 TTFT/output speed 사용. 출력 토큰 수는 각 문구 길이(섹션 1).
"n/a" 는 공개 벤치마크에 해당 변종이 등록되지 않음.

| 모델 | TTFT (s) | Out speed (t/s) | 안녕하세요 | Hello | KR 문장 | EN 문장 |
|---|---:|---:|---:|---:|---:|---:|
| Gemini 2.5 Pro (reasoning) | 21.15 | 130.0 | 21.17 | 21.17 | 21.23 | 21.21 |
| Gemini 2.5 Flash | 0.65 | 219.7 | 0.66 | 0.66 | 0.70 | 0.69 |
| Gemini 2.5 Flash-Lite | 0.73 | 234.9 | 0.74 | 0.74 | 0.77 | 0.76 |
| Gemini 3 Flash (reasoning, Preview) | 7.29 | 162.7 | 7.30 | 7.30 | 7.35 | 7.34 |
| Gemini 3.1 Pro (reasoning, Preview) | 26.16 | 124.2 | 26.18 | 26.18 | 26.24 | 26.22 |
| **Gemini 3.1 Flash-Lite** (Preview) | **0.29** | **381.9** | **0.30** | **0.30** | **0.32** | **0.31** |
| GPT-5 | n/a | n/a | n/a | n/a | n/a | n/a |
| GPT-5 mini | n/a | n/a | n/a | n/a | n/a | n/a |
| GPT-5 nano (minimal reasoning) | 1.14 | 142.5 | 1.15 | 1.15 | 1.20 | 1.19 |
| GPT-5 nano (high reasoning) | 101.01 | 150.4 | 101.02 | 101.02 | 101.07 | 101.06 |
| GPT-5.4 | n/a | n/a | n/a | n/a | n/a | n/a |
| GPT-5.4 mini (xhigh reasoning) | 8.76 | 163.8 | 8.77 | 8.77 | 8.82 | 8.80 |
| **GPT-5.4 nano** (현 프로젝트, medium) | **3.20** | **161.0** | **3.21** | **3.21** | **3.26** | **3.24** |
| GPT-5.4 nano (xhigh reasoning) | 4.79 | 190.6 | 4.80 | 4.80 | 4.84 | 4.83 |
| GPT-5.5 | n/a | n/a | n/a | n/a | n/a | n/a |

> 짧은 문구에서는 latency가 사실상 **TTFT가 좌우**. output speed의 영향은 0.01~0.06s 수준.

---

## 6. 핵심 관찰

### 가성비
- **Gemini 2.5 Flash-Lite**: 입력/출력 모두 절대 최저가 ($0.10/$0.40). 0.73s TTFT로 빠르기도 함.
- **GPT-5 nano**: OpenAI 진영 최저가 ($0.05/$0.40). 입력은 Gemini lite보다 절반.
- **현재 사용 중인 GPT-5.4 nano** ($0.20/$1.25)는 GPT-5 nano 대비 입력 4배, 출력 3배 비용. 더 똑똑하지만 비쌈.

### 지연시간
- 가장 빠름: **Gemini 3.1 Flash-Lite (0.29s)** > Gemini 2.5 Flash (0.65s) > Gemini 2.5 Flash-Lite (0.73s) > GPT-5 nano minimal (1.14s).
- reasoning 활성화된 모델 (Gemini 2.5/3.1 Pro, GPT-5.4 모든 변종)은 TTFT 3s~26s로 길어, 짧은 문답 작업에는 부적합.
- GPT-5.4 nano는 reasoning effort에 따라 medium(3.20s) → xhigh(4.79s) 로 늘어남.

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

1. **가격 출처 다양성**: Gemini 2.5 Pro 가격은 출처마다 $1.00 ~ $1.25 사이로 보고됨. Google 공식 docs 기준 $1.25 채택. >200K context 구간은 별도 가격으로 본 표는 ≤200K 기준.
2. **GPT-5/5-mini/5.4/5.5 latency 누락**: Artificial Analysis에서 해당 변종 벤치마크가 일관되지 않거나 게재 안 됨. 추정치보다 n/a로 표시.
3. **Reasoning effort 가변**: GPT-5 계열은 `minimal/medium/high/xhigh` 옵션마다 TTFT가 1.1s ~ 101s로 천차만별. 사용 시 명시적으로 effort 설정 권장.
4. **벤치마크 환경**: TTFT/output speed는 모델링된 평균치(Artificial Analysis)로 실제 production 부하·지역·시간대에 따라 차이가 큼.
5. **batch 모드 미반영**: Gemini/OpenAI 모두 batch API 50% 할인 옵션 있으나 본 표는 standard rate 기준.

---

## Sources

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
