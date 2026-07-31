# 데이터 설명

분석 데이터는 Starbucks Marketing Dataset의 고객 정보, 오퍼 정보, 이벤트 로그를 결합해 만들었습니다. 원본 로그는 이벤트 단위이고, 최종 분석은 오퍼 수신 인스턴스 단위로 재구성됩니다.

## 원본 데이터

| 파일 | 행 수 | 주요 컬럼 | 설명 |
|---|---:|---|---|
| `portfolio.csv` | 10 | `reward`, `channels`, `difficulty`, `duration`, `offer_type`, `id` | 오퍼 정보 |
| `profile.csv` | 17,000 | `gender`, `age`, `id`, `became_member_on`, `income` | 고객 프로필 |
| `transcript.csv` | 306,534 | `person`, `event`, `value`, `time` | 고객 이벤트 로그 |
| `starbucks_menu_260112.csv` | 195 | 제품명, 영양성분 | 부가 데이터 |

## 전처리 산출물

| 파일 | 행 수 | 컬럼 수 | 역할 |
|---|---:|---:|---|
| `preprocessed_final.csv` | 306,534 | 26 | 원본 3개 테이블 병합 및 기본 파생변수 생성 결과 |
| `final_eda.csv` | 306,534 | 29 | EDA용 가입 연도/월/코호트 파생변수 추가 결과 |
| `funnel_instance.csv` | 76,277 | 22 | 오퍼 수신 1건을 하나의 분석 단위로 재구성한 퍼널 데이터 |
| `funnel_instance_full.csv` | 76,277 | 35 | 퍼널 데이터에 오퍼/고객 속성을 결합한 최종 분석 데이터 |
| `tableau_df_final.csv` | 76,277 | 26 | 대시보드 연결용 축약 데이터 |

## 주요 파생변수

| 컬럼 | 의미 | 만든 이유 |
|---|---|---|
| `customer_id` | 고객 식별자 | 원본 `person`, `id`를 분석용 공통 키로 통일 |
| `offer_id` | 오퍼 식별자 | 이벤트 로그와 오퍼 마스터를 연결 |
| `amount` | 거래금액 | transaction 이벤트에서 구매 규모 분석 |
| `actual_reward` | 실제 지급 리워드 | completed 이벤트에서 보상 발생 확인 |
| `ch_web`, `ch_email`, `ch_mobile`, `ch_social` | 채널별 원핫 변수 | 채널 포함 여부가 반응에 미치는 영향 분석 |
| `channel_count` | 오퍼 발송 채널 수 | 채널 다양성과 반응률 관계 확인 |
| `reward_ratio` | `reward / difficulty` | 오퍼 매력도 대비 필요 지출 부담 비교 |
| `offer_strength` | `reward - difficulty` | 보상과 난이도의 단순 차이 확인 |
| `is_profile_missing` | 프로필 결측 여부 | `age=118` 등 비정상 프로필을 구분 |
| `age_group`, `age_gender`, `income_group` | 고객 세그먼트 | 인구통계별 반응 차이 분석 |
| `join_year`, `join_month`, `join_cohort` | 가입 시점 변수 | 가입 시점/멤버십 기간별 패턴 확인 |

## 퍼널 인스턴스 주요 컬럼

| 컬럼 | 의미 |
|---|---|
| `t_received` | 오퍼 수신 시점 |
| `t_expire` | 오퍼 만료 시점 |
| `t_viewed` | 수신 후 최초 열람 시점 |
| `t_completed` | 수신 후 최초 완료 시점 |
| `gap_to_view` | 수신부터 열람까지 걸린 시간 |
| `gap_to_complete` | 수신부터 완료까지 걸린 시간 |
| `is_viewed` | 수신 후 열람 여부 |
| `is_completed` | 유효기간 내 완료 여부 |
| `completed_with_prior_view` | 열람 후 완료 여부 |
| `completed_without_prior_view` | 열람 없이 완료 여부 |
| `gap_view_to_complete` | 열람부터 완료까지 걸린 시간 |

## 왜 인스턴스 단위 재구성이 필요한가

원본 `transcript.csv`는 이벤트 로그라서 한 고객의 `offer received`, `offer viewed`, `offer completed`가 서로 다른 행에 흩어져 있습니다. 마케팅 퍼널을 분석하려면 “이번에 받은 오퍼가 열람됐는가, 완료됐는가”를 한 행에서 비교할 수 있어야 합니다.

그래서 최종 분석에서는 **고객-오퍼-수신시점**을 하나의 인스턴스로 만들고, 그 뒤에 발생한 열람/완료 이벤트를 시간 순서로 붙입니다. 이 구조가 있어야 열람률, 완료율, 열람 후 완료율, 미인지 완료율 같은 CRM 지표를 안정적으로 계산할 수 있습니다.

