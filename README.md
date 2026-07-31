# Starbucks CRM Marketing Analysis

스타벅스 고객 이벤트 로그를 기반으로 **누구에게, 어떤 오퍼를, 어떤 채널로 보내야 실제 구매 행동으로 이어지는지** 분석한 팀 프로젝트입니다.

분석 기준 정본은 [submit/Final](/Users/yoonseokim/starbucks_project/submit/Final) 폴더의 최종 노트북 3개입니다.

## 프로젝트 한 줄 요약

오퍼 수신, 열람, 완료 이벤트를 고객-오퍼-시간 단위로 재구성해 CRM 마케팅 퍼널을 만들고, 오퍼 유형과 채널 조합이 고객 반응에 어떤 차이를 만드는지 분석했습니다.

## 핵심 파일

| 구분 | 파일 | 설명 |
|---|---|---|
| 최종 전처리 | [01_preprocessed_final.ipynb](/Users/yoonseokim/starbucks_project/submit/Final/01_preprocessed_final.ipynb) | 원본 3개 테이블을 파싱, 정제, 병합 |
| 최종 EDA | [02_eda_final.ipynb](/Users/yoonseokim/starbucks_project/submit/Final/02_eda_final.ipynb) | 고객, 이벤트, 오퍼, 거래금액 분포 확인 |
| 최종 분석 | [03_analysis_final.ipynb](/Users/yoonseokim/starbucks_project/submit/Final/03_analysis_final.ipynb) | 퍼널 인스턴스 생성, 세그먼트/채널/오퍼 분석 |
| 제출 데이터 | [submit/dataset](/Users/yoonseokim/starbucks_project/submit/dataset) | 최종 노트북 실행 기준 데이터 |
| 발표 자료 | [15조_STARBUCKS_MARKETING.pdf](/Users/yoonseokim/starbucks_project/15조_STARBUCKS_MARKETING.pdf) | 최종 발표 산출물 |

## 문서 구조

| 문서 | 내용 |
|---|---|
| [프로젝트 구조](/Users/yoonseokim/starbucks_project/docs/project-structure.md) | 폴더별 역할과 정본 파일 기준 |
| [데이터 설명](/Users/yoonseokim/starbucks_project/docs/data-description.md) | 원본/중간/최종 데이터셋 설명 |
| [실행 순서](/Users/yoonseokim/starbucks_project/docs/execution-guide.md) | 환경 설정과 노트북 실행 순서 |
| [주요 인사이트](/Users/yoonseokim/starbucks_project/docs/analysis-insights.md) | 분석 결과와 실무 해석 |
| [한계점](/Users/yoonseokim/starbucks_project/docs/limitations.md) | 분석 해석 시 주의할 점 |
| [Myun 폴더 인덱스](/Users/yoonseokim/starbucks_project/Myun_EDA/README.md) | 본인 분석 폴더 내부 구조 |
| [Myun 기여 정리](/Users/yoonseokim/starbucks_project/docs/myun-contribution.md) | 본인 작업과 팀원 작업 구분 |
| [팀원 분석 구분](/Users/yoonseokim/starbucks_project/docs/team-analysis-map.md) | 개인 폴더별 역할 정리 |

## 분석 파이프라인

```text
원본 데이터
  portfolio.csv / profile.csv / transcript.csv
        ↓
01_preprocessed_final.ipynb
  value 파싱, 채널 원핫 인코딩, 고객 정보 정제, 병합
        ↓
preprocessed_final.csv
        ↓
02_eda_final.ipynb
  고객/이벤트/오퍼/거래금액 분포 확인, 가입 시점 파생
        ↓
final_eda.csv
        ↓
03_analysis_final.ipynb
  오퍼 수신 단위 퍼널 인스턴스 생성, 지표 계산, 통계 분석
        ↓
funnel_instance.csv / funnel_instance_full.csv / tableau_df_final.csv
```

## 본인 기여 요약

본인 작업은 [Myun_EDA](/Users/yoonseokim/starbucks_project/Myun_EDA) 안의 개인 분석 노트북을 기준으로 정리했습니다.

현재 확정 가능한 핵심 기여는 **오퍼별 인지율과 전환율 분석**, **프로젝트 내 채널별/채널수별 분석 전체**, **소셜/모바일 채널의 역할 해석**, **프로젝트 종료 후 채널 수 효과와 특정 채널 효과를 구분하기 위한 고도화 분석**입니다.

고객 세그먼트 분석, 오즈비(오드비) 검정, 오퍼타입별 분석은 본인 기여로 표시하지 않았습니다.

생성 경로가 아직 완전히 확인되지 않은 `analysis_offer_df.csv`는 [Myun 기여 정리](/Users/yoonseokim/starbucks_project/docs/myun-contribution.md)에 “사용자 확인 필요”로 따로 표시했습니다.

## 사용 기술

- Python 3.13
- pandas, numpy
- matplotlib, seaborn
- scipy, statsmodels, scikit-posthocs
- Jupyter Notebook
