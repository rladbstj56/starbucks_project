# 프로젝트 구조

이 프로젝트는 코드 애플리케이션이 아니라 데이터 분석 산출물 중심 저장소입니다. 따라서 구조를 볼 때는 최종 노트북, 데이터셋, 개인 분석 폴더를 기준으로 이해하는 것이 맞습니다.

## 정본 기준

최종 재현 기준은 [submit/Final](/Users/yoonseokim/starbucks_project/submit/Final)입니다.

```text
submit/Final/
├── 01_preprocessed_final.ipynb
├── 02_eda_final.ipynb
└── 03_analysis_final.ipynb
```

이 3개 노트북이 최종 제출 데이터인 [submit/dataset](/Users/yoonseokim/starbucks_project/submit/dataset)을 기준으로 실행됩니다.

## 폴더별 역할

| 폴더/파일 | 역할 | 비고 |
|---|---|---|
| [submit/Final](/Users/yoonseokim/starbucks_project/submit/Final) | 최종 제출 노트북 | 실행 기준 정본 |
| [submit/dataset](/Users/yoonseokim/starbucks_project/submit/dataset) | 제출용 데이터 | 최종 노트북과 경로가 맞음 |
| [dataset](/Users/yoonseokim/starbucks_project/dataset) | 루트 데이터 저장소 | 원본은 `original_dataset` 아래에 있음 |
| [Final](/Users/yoonseokim/starbucks_project/Final) | 최종 노트북 복사본 | 일부 경로가 현재 데이터 구조와 맞지 않을 수 있음 |
| [Myun_EDA](/Users/yoonseokim/starbucks_project/Myun_EDA) | 본인 개인 분석 폴더 | 내부 구조는 [Myun_EDA/README.md](/Users/yoonseokim/starbucks_project/Myun_EDA/README.md) 참고 |
| [team_analysis](/Users/yoonseokim/starbucks_project/team_analysis) | 팀원 개인 분석 폴더 모음 | Soyun, chanhui, Soohan, pjh 작업 분리 |
| [team_analysis/Soyun_EDA](/Users/yoonseokim/starbucks_project/team_analysis/Soyun_EDA) | 팀원 분석 및 프로젝트 계획 문서 | 파이프라인 설명 문서 포함 |
| [team_analysis/chanhui_EDA](/Users/yoonseokim/starbucks_project/team_analysis/chanhui_EDA) | 팀원 전처리/분석 실험본 | final_analysis 하위 폴더 포함 |
| [team_analysis/Soohan_EDA](/Users/yoonseokim/starbucks_project/team_analysis/Soohan_EDA) | 팀원 초기 전처리 실험 | 원본 데이터 구조 확인 |
| [team_analysis/pjh_EDA](/Users/yoonseokim/starbucks_project/team_analysis/pjh_EDA) | 팀원 초기 전처리 실험 | 원본 데이터 파싱 |
| [docs/team_analysis](/Users/yoonseokim/starbucks_project/docs/team_analysis) | 팀원 분석 구분 문서 | 개인 작업과 팀 공통 작업 분리 목적 |

## 현재 구조에서 주의할 점

- 루트 [README.md](/Users/yoonseokim/starbucks_project/README.md)는 이번 정리로 프로젝트 개요 문서가 되었습니다.
- 초기 템플릿 파일이던 `main.py`는 분석 실행 진입점이 아니어서 제거했습니다.
- `.csv`, `.zip`, `.DS_Store`는 `.gitignore` 대상입니다. 로컬 작업 폴더에는 데이터 산출물이 남아 있을 수 있지만 GitHub 추적 대상은 아닙니다.
- 개인 폴더에는 팀 공통 노트북을 복사한 파일과 개인 실험 파일이 섞여 있습니다. 기여도 판단은 파일명과 노트북 내용 기준으로 보수적으로 분리했습니다.
