# 실행 순서

최종 노트북은 [submit/Final](/Users/yoonseokim/starbucks_project/submit/Final)을 기준으로 실행합니다. 이 폴더의 노트북은 [submit/dataset](/Users/yoonseokim/starbucks_project/submit/dataset)을 상대 경로로 읽습니다.

## 환경 준비

이 프로젝트는 `uv` 기반 Python 프로젝트로 구성되어 있습니다.

```bash
uv sync
```

Jupyter를 실행합니다.

```bash
uv run jupyter notebook
```

또는 VS Code/Jupyter Lab에서 프로젝트의 `.venv` 커널을 선택해 실행합니다.

## 실행 순서

1. [submit/Final/01_preprocessed_final.ipynb](/Users/yoonseokim/starbucks_project/submit/Final/01_preprocessed_final.ipynb)
2. [submit/Final/02_eda_final.ipynb](/Users/yoonseokim/starbucks_project/submit/Final/02_eda_final.ipynb)
3. [submit/Final/03_analysis_final.ipynb](/Users/yoonseokim/starbucks_project/submit/Final/03_analysis_final.ipynb)

## 각 노트북의 역할

| 순서 | 노트북 | 입력 | 출력 | 역할 |
|---|---|---|---|---|
| 1 | `01_preprocessed_final.ipynb` | 원본 CSV | `preprocessed_final.csv` | 원본 파싱, 결측/이상값 처리, 테이블 병합 |
| 2 | `02_eda_final.ipynb` | `preprocessed_final.csv` | `final_eda.csv` | 기본 분포 확인, 가입 시점 파생변수 추가 |
| 3 | `03_analysis_final.ipynb` | `final_eda.csv`, `funnel_instance.csv` | `funnel_instance_full.csv`, `tableau_df_final.csv` | 퍼널 생성, 통계 분석, 채널/오퍼 분석 |

## 경로 주의사항

루트 [Final](/Users/yoonseokim/starbucks_project/Final)의 노트북은 일부 입력 경로가 현재 루트 데이터 구조와 맞지 않을 수 있습니다. 재현 목적이면 `submit/Final`을 기준으로 실행하는 편이 안전합니다.

CSV와 ZIP 데이터 파일은 `.gitignore`로 Git 추적 대상에서 제외합니다. 따라서 GitHub에서 저장소를 새로 받은 경우에는 아래 경로에 데이터 파일을 먼저 배치해야 노트북을 그대로 실행할 수 있습니다.

특히 루트 `dataset`의 원본 CSV는 아래에 있습니다.

```text
dataset/original_dataset/
```

반면 `submit/Final` 노트북은 아래 파일을 읽습니다.

```text
submit/dataset/portfolio.csv
submit/dataset/profile.csv
submit/dataset/transcript.csv
submit/dataset/starbucks_menu_260112.csv
```

## 실무적으로 중요한 실행 포인트

노트북 순서를 지켜야 하는 이유는 산출물이 다음 단계의 입력으로 쓰이기 때문입니다. 분석 프로젝트에서 이 연결 관계를 명확히 보여주는 것은 재현성의 핵심입니다.

면접에서는 “노트북을 그냥 나눴다”가 아니라 “원본 로그를 분석 가능한 테이블로 정제하고, 그 결과를 EDA와 퍼널 분석의 입력으로 사용했다”고 설명하는 것이 좋습니다.
