# 스타벅스 CRM 마케팅 퍼널 분석

스타벅스 리워드 앱의 고객 이벤트 로그를 바탕으로 **어떤 고객에게, 어떤 오퍼를, 어떤 채널로 전달해야 실제 구매 행동으로 이어지는지** 분석한 CRM 마케팅 퍼널 분석 프로젝트입니다.

원본 이벤트 로그를 그대로 집계하지 않고, `offer received` 이후의 `offer viewed`, `offer completed` 이벤트를 고객-오퍼-수신시점 단위로 재구성해 마케팅 퍼널을 만들었습니다. 이후 오퍼 유형, 고객 세그먼트, 채널 조합별 반응 차이를 비교하고 CRM 운영 전략으로 연결했습니다.

## 주요 링크

| 구분 | 링크 |
|---|---|
| Tableau 대시보드 | [Tableau Public](https://public.tableau.com/app/profile/yoonseo.kim2044/viz/_15_17749189412390/1) |
| 최종 노트북 | [submit/Final](submit/Final) |
| 프로젝트 문서 | [docs](docs) |
| 본인 기여 정리 | [docs/myun-contribution.md](docs/myun-contribution.md) |

## 프로젝트 개요

| 항목 | 내용 |
|---|---|
| 주제 | 스타벅스 리워드 앱 오퍼 반응 로그 기반 CRM 퍼널 분석 |
| 기간 | 2026.03.18 - 2026.03.31 |
| 형태 | 4명 팀 프로젝트 |
| 분석 단위 | 오퍼 수신 인스턴스 76,277건 |
| 핵심 질문 | 오퍼 수신 이후 열람과 완료를 높이는 고객, 오퍼, 채널 조건은 무엇인가 |
| 주요 역할 | 채널 분석, 통계 검정, 효과크기 해석, 최종 코드 취합 및 고도화 |

## 문제 정의

마케팅 캠페인의 성과를 단순 완료율로만 보면 오퍼를 실제로 보고 구매한 고객과, 오퍼를 보지 않았지만 원래 구매했을 가능성이 있는 고객이 섞입니다. 이 경우 캠페인 효과를 과대평가하거나 불필요한 리워드 비용을 발생시킬 수 있습니다.

이 프로젝트에서는 CRM 성과를 더 정확히 보기 위해 완료율을 하나의 지표로 보지 않고 아래처럼 분해했습니다.

| 지표 | 의미 |
|---|---|
| `view_rate` | 오퍼 수신 후 열람한 비율 |
| `complete_rate` | 오퍼 수신 후 유효기간 내 완료한 비율 |
| `view_cvr` | 열람자 중 열람 후 완료한 비율 |
| `eff_cvr` | 완료자 중 열람 후 완료한 비율 |
| `non_eff_cvr` | 완료자 중 열람 없이 완료한 비율 |

이 지표 분해를 통해 “성과가 좋아 보이는 오퍼”와 “실제로 노출 효과가 있었던 오퍼”를 구분했습니다.

## 주요 분석 결과

1. **Social 채널은 열람률에 가장 강한 신호를 보였습니다.**  
   Social 포함 여부와 열람 여부의 관계에서 Cramer's V가 약 0.49로 나타나, 개별 채널 중 열람 단계에 가장 큰 영향을 주는 신호로 해석했습니다.

2. **Mobile 채널은 완료까지 걸리는 시간을 줄이는 핵심 채널로 확인됐습니다.**  
   Mobile 포함 여부에 따른 완료 소요시간 차이 검정에서 효과크기 r이 약 0.41로 나타났습니다. 빠른 반응이 필요한 캠페인에서는 Mobile 채널 우선순위를 검토할 수 있습니다.

3. **채널 수 자체보다 특정 채널 포함 여부가 중요했습니다.**  
   채널 수가 많을수록 열람률이 높아 보였지만, 오퍼별 채널 구성이 고정되어 있어 채널 수 자체를 인과 효과로 단정하기 어렵습니다. 추가 분석 결과, 채널 수 효과는 Social, Mobile 포함 여부와 얽혀 있을 가능성이 높다고 해석했습니다.

4. **저소득층에서는 Discount 오퍼의 인지완료 승산이 BOGO보다 높았습니다.**  
   저소득층 기준 Discount의 `completed_with_prior_view` 승산은 BOGO 대비 약 1.57배로 나타났습니다. 가격 민감도가 높은 고객에게는 BOGO보다 Discount가 더 직접적인 행동 유도 수단이 될 수 있습니다.

5. **미열람 완료 고객은 리워드 비용 효율 점검 대상입니다.**  
   `completed_without_prior_view`는 오퍼를 보지 않았지만 완료 조건을 만족한 경우입니다. 이 고객군은 오퍼가 없어도 구매했을 가능성이 있어, 캠페인 비용 최적화 관점에서 별도 관리가 필요합니다.

## 담당 역할과 기여

이 프로젝트에서 제가 담당한 핵심 업무는 **채널 분석과 최종 분석 코드 고도화**입니다.

- 오퍼별 인지율, 전환율, 채널 반응 차이 분석
- 채널별, 채널 수별 열람률 및 완료 소요시간 분석
- Social, Mobile, Web 채널 포함 여부에 따른 통계 검정 및 효과크기 해석
- 채널 수 효과와 특정 채널 효과가 혼재되어 있는지 추가 검증
- 최종 제출 노트북 3개 기준으로 코드 취합, 지표명 정리, 실행 검증
- Tableau 대시보드 연결용 최종 데이터셋 생성

고객 세그먼트 분석, 오즈비 검정 전체, 오퍼 타입별 분석 전체는 팀 분석에 포함되어 있으나 제 단독 기여로 표시하지 않았습니다. 자세한 기여 구분은 [docs/myun-contribution.md](docs/myun-contribution.md)에 정리했습니다.

## 분석 파이프라인

```text
원본 데이터
  portfolio.csv / profile.csv / transcript.csv
        ↓
01_preprocessed_final.ipynb
  value 파싱, 채널 원핫 인코딩, 고객 정보 정제, 테이블 병합
        ↓
preprocessed_final.csv
        ↓
02_eda_final.ipynb
  고객, 이벤트, 오퍼, 거래금액 분포 확인 및 가입 시점 파생변수 생성
        ↓
final_eda.csv
        ↓
03_analysis_final.ipynb
  오퍼 수신 인스턴스 생성, 퍼널 지표 계산, 통계 검정, 채널 분석
        ↓
funnel_instance.csv / funnel_instance_full.csv / tableau_df_final.csv
```

## 저장소 구조

```text
.
├── submit/
│   ├── Final/                  # 최종 제출 노트북 3개
│   └── dataset/                # 최종 노트북 실행 기준 데이터
├── docs/                       # 프로젝트 구조, 데이터 설명, 인사이트, 한계점 문서
├── Myun_EDA/                   # 개인 분석 및 채널 분석 고도화 기록
├── team_analysis/              # 팀원별 개인 분석 폴더
├── Final/                      # 원본 최종 폴더 보존용 복사본
└── README.md
```

## 최종 노트북

| 순서 | 파일 | 역할 |
|---:|---|---|
| 1 | [01_preprocessed_final.ipynb](submit/Final/01_preprocessed_final.ipynb) | 원본 데이터 파싱, 결측 및 이상값 처리, 테이블 병합 |
| 2 | [02_eda_final.ipynb](submit/Final/02_eda_final.ipynb) | 고객, 이벤트, 오퍼, 거래금액 분포 확인 |
| 3 | [03_analysis_final.ipynb](submit/Final/03_analysis_final.ipynb) | 퍼널 인스턴스 생성, KPI 계산, 통계 분석, 채널 효과 분석 |

재현 목적이면 루트의 `Final` 폴더가 아니라 [submit/Final](submit/Final)을 기준으로 실행하는 것이 안전합니다.

## 실행 방법

이 프로젝트는 `uv` 기반 Python 환경을 사용합니다.

```bash
uv sync
uv run jupyter notebook
```

노트북은 아래 순서대로 실행합니다.

```text
submit/Final/01_preprocessed_final.ipynb
submit/Final/02_eda_final.ipynb
submit/Final/03_analysis_final.ipynb
```

각 노트북은 이전 단계 산출물을 다음 단계 입력으로 사용하므로 순서대로 실행해야 합니다.

## 사용 기술

- Python 3.13
- pandas, numpy
- matplotlib, seaborn
- scipy, statsmodels, scikit-posthocs
- Jupyter Notebook
- Tableau Public

## 문서 안내

| 문서 | 내용 |
|---|---|
| [docs/project-structure.md](docs/project-structure.md) | 폴더별 역할과 최종 파일 기준 |
| [docs/data-description.md](docs/data-description.md) | 원본 데이터, 전처리 산출물, 주요 파생변수 설명 |
| [docs/execution-guide.md](docs/execution-guide.md) | 환경 설정과 노트북 실행 순서 |
| [docs/analysis-insights.md](docs/analysis-insights.md) | 주요 분석 결과와 실무 해석 |
| [docs/limitations.md](docs/limitations.md) | 분석 한계와 후속 개선 방향 |
| [docs/myun-contribution.md](docs/myun-contribution.md) | 개인 기여와 팀 공통 작업 구분 |

## 한계와 후속 개선 방향

- 이 분석은 관측 로그 기반 분석이므로 채널이나 오퍼가 구매 행동을 직접 유발했다고 단정할 수 없습니다.
- 오퍼별 채널 조합이 고정되어 있어 채널 수 효과와 특정 채널 효과가 완전히 독립적으로 분리되지는 않습니다.
- 실제 CRM 적용 전에는 A/B 테스트를 통해 채널 전략과 오퍼 조건의 인과 효과를 검증해야 합니다.
