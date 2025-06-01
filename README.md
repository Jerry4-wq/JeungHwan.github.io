# AIX-DL-Project
## K-평균 클러스터링의 이해: 역사, 작동 원리, 그리고 응용 분야

> **Members**
> 
> *김승훈, 기계공학과*
> 
> *명정환, 파이낸스경영학과, myung06m@hanyang.ac.kr*

---

## 📑 Table of Contents
- [I. Proposal](#i-proposal)
- [II. Datasets](#ii-datasets)
- [III. Methodology](#iii-methodology)
- [IV. Evaluation & Analysis](#iv-evaluation--analysis)
- [V. Related Work](#v-related-work)
- [VI. Conclusion](#vi-conclusion-discussion)

---

## I. Proposal

### 🎯 Motivation
K-평균(K-means) 클러스터링은 데이터 분석 및 비지도 학습에서 가장 널리 사용되는 알고리즘 중 하나입니다.  
하지만 그 간단한 원리와 직관성에도 불구하고, 여전히 '왜', '어떻게' 동작하는지 명확히 이해되지 않는 경우가 많습니다.  
이 프로젝트에서는 K-평균의 역사, 수학적 직관, 작동 방식, 그리고 실제 응용까지 하나의 흐름으로 소개하고자 합니다.

### 📌 What do you want to see at the end?
- K-평균 알고리즘의 작동 원리에 대한 직관적 설명
- 예제 데이터를 이용한 시각적 시뮬레이션
- 응용 사례 분석을 통한 실제 활용 가능성 탐색

---

## II. Datasets

이 프로젝트에서는 다음의 두 가지 데이터셋을 사용했습니다:

1. **🌸 Iris Dataset** (UCI Machine Learning Repository)  
   - 꽃잎과 꽃받침의 길이/너비 데이터를 사용해 세 종의 군집 형성 시도  
   - **특징**: K-평균 알고리즘의 성능 비교에 자주 사용되는 벤치마크

2. **🧪 Synthetic Dataset** (`make_blobs` from `sklearn.datasets`)  
   - 클러스터가 명확하게 나뉘는 인공 데이터를 생성  
   - 알고리즘의 시각화 및 설명에 효과적

---

## III. Methodology

### 🔧 알고리즘 선택 이유
- 구현이 간단하고 계산 효율이 높음
- 결과를 시각적으로 쉽게 해석 가능
- 다양한 도메인에서 폭넓게 사용 가능

### ⚙️ 작동 원리
1. K개의 중심점(centroids)을 무작위로 초기화  
2. 각 데이터를 가장 가까운 중심점에 할당  
3. 각 클러스터의 평균을 새로운 중심점으로 설정  
4. 중심점 변화가 없을 때까지 반복 수행

> **수학적 기반**:  
> 유클리드 거리(Euclidean distance)를 기준으로 클러스터 내 분산을 최소화함

### 🧩 사용한 Feature
- 모든 feature는 정규화(normalization) 후 사용
- 차원 축소 기법 사용: **TSNE**, **PCA**

---

## IV. Evaluation & Analysis

### 📈 클러스터링 결과 시각화

#### 📊 Iris Dataset (k = 3)
- 실제 라벨과 비교해 대체로 정확히 분류
- Versicolor vs Virginica 간 일부 혼동 존재

#### 📊 Synthetic Data (k = 4)
- 명확한 클러스터 분리 확인 가능

### 📏 클러스터 평가 지표
- **Silhouette Score**: `0.68` (Iris 기준)
- **Inertia**: 클러스터 내 거리 제곱합(WCSS); 낮을수록 우수

---

## V. Related Work

- 📄 MacQueen, J. (1967). *Some methods for classification and analysis of multivariate observations*
- 📚 [Scikit-learn Documentation](https://scikit-learn.org)
- 📝 Towards Data Science: *Understanding K-Means Clustering in Python*
- 🔧 사용 라이브러리: `matplotlib`, `seaborn`, `numpy`, `pandas`, `scikit-learn`

---

## VI. Conclusion: Discussion

K-평균 클러스터링은 **단순하지만 강력한 비지도 학습 도구**입니다.  
초기 데이터 탐색이나 시각적 분석에 매우 유용하지만 다음과 같은 한계도 있습니다:

- `k` 값을 사전에 지정해야 함
- 원형 또는 균일 분포에 적합
- 이상치(outlier)에 민감

### 🔭 향후 계획
- K-평균의 변형 알고리즘들과 비교 실험 예정  
  (예: K-Medoids, DBSCAN, GMM 등)
- 실제 데이터셋을 활용한 성능 비교 및 시각화 분석 강화

---

📌 **Made with 💡 and Python**

