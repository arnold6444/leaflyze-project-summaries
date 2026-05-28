# Explainable Industrial Anomaly Detection

졸업프로젝트 | 2026.03 ~

## 한 줄 요약

산업 검사 이미지에서 평소와 다른 부분을 찾아 표시하고, 검사자가 확인할 근거를 Action Card로 정리하는 프로젝트입니다.

## 왜 만들었나

산업 검사 데이터는 정상 이미지가 대부분이고 이상 이미지는 적은 경우가 많습니다. 그래서 단순히 정상/비정상만 맞히는 것보다, 어느 부분이 이상해 보이는지와 다음에 무엇을 확인해야 하는지를 보여주는 흐름이 더 중요하다고 보았습니다.

## 구현한 것

- OPGW 송전선로 이미지 검사를 목표로 두고, 현재는 MVTec AD Cable 데이터로 구조 검증
- 검사 이미지에서 이상 의심 위치를 heatmap과 ROI crop으로 표시
- 원본 이미지, heatmap, ROI crop, anomaly score를 LVLM 입력으로 구성
- LVLM이 시각적 근거와 추가 확인 항목을 문장으로 정리하도록 설계
- 최종 결과를 결함 유형, 위치, 근거, 위험도, 후속 확인 항목이 담긴 Action Card로 정리

## 흐름

```mermaid
flowchart LR
    A[검사 이미지] --> B[이상 위치 탐지]
    B --> C[Heatmap / ROI]
    C --> D[LVLM 설명 생성]
    D --> E[Action Card]
```

## 기술

Python, anomaly detection, heatmap/ROI visualization, LVLM-based explanation, MVTec AD Cable

## 코드

공개 repository: [explainable-industrial-anomaly-detection](https://github.com/arnold6444/explainable-industrial-anomaly-detection)
