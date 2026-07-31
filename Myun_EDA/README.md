# Myun EDA 작업 정리

이 폴더는 본인 개인 분석과 최종 코드 취합 과정에서 만든 파일을 역할별로 정리한 공간입니다.

## 구조

```text
Myun_EDA/
├── 01_personal_eda/
├── 02_channel_analysis/
├── 03_pipeline_reference/
├── 04_outputs/
└── README.md
```

## 01_personal_eda

초기 개인 EDA와 오퍼별 인지율/전환율 분석 파일입니다.

| 파일 | 설명 |
|---|---|
| [eda_myun.ipynb](/Users/yoonseokim/2025_main_bootcamp/3rd_practice_project/Myun_EDA/01_personal_eda/eda_myun.ipynb) | 오퍼별 인지율, 전환율, 채널 영향 분석 |
| [eda_myun_draft.ipynb](/Users/yoonseokim/2025_main_bootcamp/3rd_practice_project/Myun_EDA/01_personal_eda/eda_myun_draft.ipynb) | 초기 분석 초안 |
| [analysis_offer_df.csv](/Users/yoonseokim/2025_main_bootcamp/3rd_practice_project/Myun_EDA/01_personal_eda/analysis_offer_df.csv) | 오퍼별 채널/성과 요약 산출물 |

## 02_channel_analysis

최종 코드 취합 이후 본인이 맡은 채널별/채널수별 분석과 고도화 파일입니다.

| 파일 | 설명 |
|---|---|
| [analysis_final_mydraft.ipynb](/Users/yoonseokim/2025_main_bootcamp/3rd_practice_project/Myun_EDA/02_channel_analysis/analysis_final_mydraft.ipynb) | `여기부터 내 코드` 마크다운 이후가 본인 작업 |
| [analysis_final_mine.ipynb](/Users/yoonseokim/2025_main_bootcamp/3rd_practice_project/Myun_EDA/02_channel_analysis/analysis_final_mine.ipynb) | 채널별/채널수별 분석 정리본 |
| [03_analysis_final.ipynb](/Users/yoonseokim/2025_main_bootcamp/3rd_practice_project/Myun_EDA/02_channel_analysis/03_analysis_final.ipynb) | 개인 분석이 반영된 통합 분석 파일 |
| [03_analysis_final_channel_enhanced.ipynb](/Users/yoonseokim/2025_main_bootcamp/3rd_practice_project/Myun_EDA/02_channel_analysis/03_analysis_final_channel_enhanced.ipynb) | 프로젝트 종료 후 채널 수 효과와 특정 채널 효과를 재점검한 고도화본 |

## 03_pipeline_reference

최종 제출 파이프라인 또는 팀 공통 코드와 연결되는 참고 파일입니다. 본인 기여 설명의 중심 파일은 아니지만, 작업 흐름과 재현 과정을 추적하기 위해 보관합니다.

| 파일 | 설명 |
|---|---|
| [01_preprocessed_final.ipynb](/Users/yoonseokim/2025_main_bootcamp/3rd_practice_project/Myun_EDA/03_pipeline_reference/01_preprocessed_final.ipynb) | 공통 전처리 파일 성격 |
| [02_eda_final.ipynb](/Users/yoonseokim/2025_main_bootcamp/3rd_practice_project/Myun_EDA/03_pipeline_reference/02_eda_final.ipynb) | 공통 EDA 파일 성격 |
| [preprocessed_final.ipynb](/Users/yoonseokim/2025_main_bootcamp/3rd_practice_project/Myun_EDA/03_pipeline_reference/preprocessed_final.ipynb) | 초기 전처리 작업 기록 |
| [stage1_copy.ipynb](/Users/yoonseokim/2025_main_bootcamp/3rd_practice_project/Myun_EDA/03_pipeline_reference/stage1_copy.ipynb) | Soyun stage1과 코드 차이가 있어 보관 |
| [stage2_copy.ipynb](/Users/yoonseokim/2025_main_bootcamp/3rd_practice_project/Myun_EDA/03_pipeline_reference/stage2_copy.ipynb) | Soyun stage2와 코드 차이가 있어 보관 |

## 04_outputs

개인 분석 과정에서 생성된 산출물입니다.

| 파일 | 설명 |
|---|---|
| [funnel_instance.csv](/Users/yoonseokim/2025_main_bootcamp/3rd_practice_project/Myun_EDA/04_outputs/funnel_instance.csv) | 루트 `dataset/funnel_instance.csv`와 해시가 달라 보존 |

## 삭제한 파일

| 파일 | 삭제 이유 |
|---|---|
| `advanced_analysis.ipynb` | 빈 노트북 |
| `final_eda.csv` | 루트 `dataset/final_eda.csv`와 동일한 중복 산출물 |
| `tableau_df.csv` | 루트 `dataset/tableau_df.csv`와 동일한 중복 산출물 |
| `stage3 copy.ipynb` | Soyun `stage3.ipynb`와 완전히 동일 |
| `stage4 copy.ipynb` | Soyun `stage4.ipynb`와 완전히 동일 |

