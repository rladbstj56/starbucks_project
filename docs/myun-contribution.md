# Myun 개인 기여 정리

이 문서는 [Myun_EDA](/Users/yoonseokim/2025_main_bootcamp/3rd_practice_project/Myun_EDA) 폴더를 기준으로 본인 작업과 팀 공통/복사 작업을 구분합니다.

## 확정 본인 작업으로 볼 수 있는 파일

| 파일 | 역할 | 근거 |
|---|---|---|
| [eda_myun.ipynb](/Users/yoonseokim/2025_main_bootcamp/3rd_practice_project/Myun_EDA/01_personal_eda/eda_myun.ipynb) | 오퍼별 인지율/전환율, 채널 영향 분석 | 오퍼별 `aware_rate`, `conversion_rate`, 채널별 검정과 해석 포함 |
| [eda_myun_draft.ipynb](/Users/yoonseokim/2025_main_bootcamp/3rd_practice_project/Myun_EDA/01_personal_eda/eda_myun_draft.ipynb) | 개인 EDA 초안 | “마케팅 효과 좋았던/별로였던 오퍼”, 소셜 채널 가설 탐색 |
| [analysis_final_mydraft.ipynb](/Users/yoonseokim/2025_main_bootcamp/3rd_practice_project/Myun_EDA/02_channel_analysis/analysis_final_mydraft.ipynb) | 최종 코드 취합 후 개인 분석 추가 | `여기부터 내 코드` 마크다운 이후가 본인 작업 |
| [analysis_final_mine.ipynb](/Users/yoonseokim/2025_main_bootcamp/3rd_practice_project/Myun_EDA/02_channel_analysis/analysis_final_mine.ipynb) | 채널별/채널수별 분석 정리본 | 프로젝트 내 채널 분석 전체가 본인 작업 |
| [03_analysis_final_channel_enhanced.ipynb](/Users/yoonseokim/2025_main_bootcamp/3rd_practice_project/Myun_EDA/02_channel_analysis/03_analysis_final_channel_enhanced.ipynb) | 프로젝트 종료 후 채널 분석 고도화본 | 열람률/열람시간 영향이 채널 수인지 특정 채널인지 재점검 |

## 사용자 확인 필요 파일

아래 파일은 생성 경로가 완전히 확정되지 않아, 사용자 확인 전에는 본인 기여 산출물로 단정하지 않습니다.

| 파일 | 현재 확인된 내용 | 확인 필요 이유 |
|---|---|---|
| [analysis_offer_df.csv](/Users/yoonseokim/2025_main_bootcamp/3rd_practice_project/Myun_EDA/01_personal_eda/analysis_offer_df.csv) | 오퍼별 채널/성과 요약 테이블 | `eda_myun_draft.ipynb`의 `analysis_df` 저장 코드에서 나온 것으로 보이나, 현재 저장 코드는 주석 처리되어 있음 |

## 본인 핵심 기여

### 1. 오퍼별 인지율과 전환율 분해

단순 완료율 대신 `aware_rate`와 `conversion_rate`를 분리해 오퍼 성과를 해석했습니다.

- `aware_rate`: 오퍼를 완료한 고객 중 열람 후 완료한 비율
- `conversion_rate`: 오퍼를 열람한 고객 중 완료까지 이어진 비율

이 구분이 중요한 이유는 “고객이 샀다”와 “오퍼를 보고 샀다”가 다르기 때문입니다. CRM 분석에서는 후자가 실제 마케팅 효과에 더 가깝습니다.

### 2. 소셜 채널의 인지 기여 분석

소셜 채널이 없는 오퍼에서 인지율이 낮게 나타나는 패턴을 확인하고, 채널별 인지율/전환율 차이를 분석했습니다.

실무적으로는 “소셜 채널을 쓰면 무조건 매출이 오른다”가 아니라 “소셜 채널은 우선 오퍼를 보게 만드는 데 강점이 있다”로 해석하는 것이 안전합니다.

### 3. 모바일/소셜 채널과 반응 속도 분석

`gap_to_view`, `gap_to_complete`, `gap_view_to_complete`를 활용해 고객이 오퍼를 얼마나 빨리 보고, 얼마나 빨리 완료하는지 확인했습니다.

이 분석은 기간이 짧은 프로모션이나 당일성 캠페인에서 어떤 채널을 우선해야 하는지 판단하는 근거가 됩니다.

### 4. 채널별/채널수별 분석

프로젝트 내 채널별/채널수별 분석 전체를 담당했습니다.

주요 분석 내용은 다음과 같습니다.

- 채널 수에 따른 열람시간, 완료시간, 열람률, 완료율 비교
- `ch_web`, `ch_email`, `ch_mobile`, `ch_social` 유무별 반응 차이 검정
- Mann-Whitney U 검정, Kruskal-Wallis 검정, 카이제곱 검정, 효과크기 해석
- 소셜/모바일 채널이 열람률과 열람 속도에 더 직접적인 영향을 주는지 검토
- 채널 수가 실제 원인인지, 특정 채널 포함 여부의 대리지표인지 점검

이 분석이 중요한 이유는 채널 수가 많아 보이는 효과를 그대로 전략으로 옮기면 비용이 커질 수 있기 때문입니다. 실무에서는 “채널을 더 늘릴 것인가”보다 “어떤 채널을 반드시 포함할 것인가”가 더 실행 가능한 의사결정입니다.

### 5. 프로젝트 종료 후 채널 분석 고도화

[03_analysis_final_channel_enhanced.ipynb](/Users/yoonseokim/2025_main_bootcamp/3rd_practice_project/Myun_EDA/02_channel_analysis/03_analysis_final_channel_enhanced.ipynb)는 프로젝트 종료 후 개인적으로 고도화한 파일입니다.

기존 [03_analysis_final.ipynb](/Users/yoonseokim/2025_main_bootcamp/3rd_practice_project/Myun_EDA/02_channel_analysis/03_analysis_final.ipynb)와 비교했을 때 핵심 추가점은 채널 분석 구간 앞에 아래 확인 셀이 추가된 것입니다.

- `funnel_metrics(funnel, ['offer_type', 'channel_count'])`
- `funnel.info()`
- `bogo`의 `channel_count`별 수신/열람 집계
- `discount`의 `channel_count`별 수신/열람 집계

이 추가 작업의 목적은 열람률과 열람시간에 영향을 주는 요인이 단순히 채널 수인지, 아니면 `mobile`/`social` 같은 특정 채널인지 확인하는 것입니다.

## 본인 기여로 표시하지 않을 항목

아래 내용은 최종 노트북에 포함되어 있더라도 본인 기여로 표시하지 않습니다.

| 항목 | 구분 이유 |
|---|---|
| 고객 세그먼트 분석 | 사용자가 본인 작업이 아니라고 명시 |
| 오즈비(오드비) 검정 | 사용자가 본인 작업이 아니라고 명시 |
| 오퍼타입별 분석 | 사용자가 본인 작업이 아니라고 명시 |
| `stage3 copy.ipynb` | Soyun_EDA의 `stage3.ipynb`와 동일한 파일이라 삭제 |
| `stage4 copy.ipynb` | Soyun_EDA의 `stage4.ipynb`와 동일한 파일이라 삭제 |
| `01_preprocessed_final.ipynb`, `02_eda_final.ipynb` | 최종 제출 파이프라인의 공통 파일 성격 |

## 포트폴리오용 역할 문장

> 오퍼별 인지율과 열람 후 전환율을 분리해 CRM 캠페인의 실제 기여도를 분석했고, 채널별/채널수별 비교를 통해 소셜·모바일 채널이 열람률과 반응 속도에 미치는 영향을 검정했습니다. 프로젝트 종료 후에는 채널 수 효과가 특정 채널 포함 여부에서 비롯된 것인지 추가 점검해 결론을 보완했습니다.
