# AIX-DL-Project
## K-평균 클러스터링의 이해

> **Members**
> 
> *김승후, 경영학과, shawn060512@gmail.com*
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

### 동기
K-평균(K-means) 클러스터링은 데이터 분석 및 비지도 학습에서 가장 널리 사용되는 알고리즘 중 하나입니다.  
k-평균의 개념은 1957년 후고 스테인하우스가 처음 소개한 이후 그 단순성과 계산 효율성 덕분에 다양한 산업 및 연구 분야에서 활용되고 있습니다.  
본 프로젝트의 목적은 K-평균의 작동 원리를 수학적, 시각적으로 이해하고 현실 데이터와 인공 데이터를 통한 적용 사례를 탐구하는 것에 있습니다.
또한 K-평균 클러스터링이 지닌 한계와 이를 보완할 수 있는 방법을 탐구하고자 합니다.

---

## II. Datasets

이 프로젝트에서는 다음의 두 가지 데이터셋을 사용했습니다:

1. **Iris Dataset** (UCI Machine Learning Repository)  
   - 꽃잎과 꽃받침의 길이/너비 데이터를 사용해 세 종의 군집 형성 시도
   - 150개의 샘플, 4개의 특성 (꽃받침/꽃잎 길이와 너비)
   - 실제 품종 레이블 존재 (Setosa, Versicolor, Virginica)
   - K-평균 결과를 실제 레이블과 비교하여 평가 가능
   - K-평균 알고리즘의 성능 비교에 자주 사용되는 벤치마크

2. **Synthetic Dataset** (`make_blobs` from `sklearn.datasets`)  
   - 클러스터가 명확하게 나뉘는 인공 데이터를 생성  
   - 알고리즘의 시각화 및 설명에 효과적

---

## III. Methodology


### ⚙️ 작동 원리
1. 데이터로부터 K개의 중심점(centroids)을 무작위로 초기화  
2. 각 데이터를 가장 가까운 중심점에 할당  
3. 각 클러스터의 평균을 새로운 중심점으로 설정  
4. 중심점 변화가 없을 때까지 반복 수행

> **수학적 기반**:  
> 유클리드 거리(Euclidean distance)를 기준으로 클러스터 내 분산을 최소화합니다.
> K-평균은 **클러스터 내 거리 제곱합(WCSS: Within-Cluster Sum of Squares)**를 최소화하는 것을 목표로 합니다.
> 
> <img width="196" alt="image" src="https://github.com/user-attachments/assets/2c725eae-2fd0-429f-bec7-c430604b2339" />

여기서 Ci는 i번째 클러스터를 뜻하고 Ui는 해당 클러스터의 중심점을 뜻합니다.



---

## IV. Evaluation & Analysis

### 📈 클러스터링 결과 시각화

#### 📊 Iris Dataset (k = 3)
- 실제 라벨과 비교해 대체로 정확히 분류
- Versicolor vs Virginica 간 일부 혼동 존재
![image](https://github.com/user-attachments/assets/f8bc9ce2-5789-449a-8c66-2832f4a74f28)


#### 📊 Synthetic Data (k = 4)
- 각 클러스터가 뚜렷히 분리되고 중심점이 명확히 수렴
![image](https://github.com/user-attachments/assets/a5857a80-2400-4201-b347-11e247524c47)


### 📏 클러스터 평가 지표
- **Silhouette Score**: 군집의 응집도와 분리도를 동시에 평가하는 지표로 0.5 이상이면 괜찮은 군집, 0.7 이상이면 매우 우수한 군집으로 평가
  a(i): 같은 클러스터 내 다른 점들과의 평균 거리(응집도)
  b(i): 가장 가까운 다른 클러스터의 점들과의 평균 거리(분리도)

   <img width="122" alt="image" src="https://github.com/user-attachments/assets/04e55926-90c8-46e0-bcd6-d84b14632f93" />

  실루엣 계수 값의 범위는 -1부터 1까지로 1에 가까울수록 잘 클러스터링된 것이고 음수면 잘못된 클러스터에 속한 것입니다. 0에 가까우면 그 경계에 있는 것입니다.
- **Inertia**: 클러스터 내 거리 제곱합(WCSS); 낮을수록 우수


  
| 항목            | Iris Dataset | Synthetic Dataset |
| 클러스터 수 (K)  | 3            | 4                 |
| Silhouette Score | 0.68         | 0.81             |
| 분류 정확도        | 약 89%        | -              |
| Inertia (WCSS)    | 낮음           | 매우 낮음      |


---

## V. Related Work

- 📄 MacQueen, J. (1967). *Some methods for classification and analysis of multivariate observations*
- 📚 [Scikit-learn Documentation](https://scikit-learn.org)
- 📝 Towards Data Science: *Understanding K-Means Clustering in Python*
- 🔧 사용 라이브러리: `matplotlib`, `seaborn`, `numpy`, `pandas`, `scikit-learn`

---

## VI. Conclusion: Discussion

K-평균 클러스터링은 단순하지만 효과적인 비지도 학습 기법입니다.
데이터 분포가 명확할 수록 효과적으로 군집을 분리할 수 있기에 시각화 기반 분석, 이상 탐지 등 다양한 분야에서 활용되고 있습니다.
초기 데이터 탐색이나 시각적 분석에 매우 유용하지만 다음과 같은 한계가 있음:

- `k` 값을 사전에 지정해야 함
- 원형 또는 균일 분포에 적합
- 이상치(outlier)에 민감

이에 대한 보완으로는 

  DBSCAN(밀도 기반 클러스터링 알고리즘): 데이터가 얼마나 밀집해 있는지를 기준으로 클러스터를 형성해 멀리 떨어진 점을 노이즈로 간주합니다. 주변에 일정 수 이상의 이웃이 있는 점을 Core Point, Core Point 근처에 있지만 자신 주변에는 이웃이 부족한 점을 Border Point, 외로운 점을 Noise Point로 규정합니다. 주요 파라미터로는 이웃으로 간주할 기준 거리인 eps, Core Point로 간주할 최소 이웃 수인 MinPts가 있습니다. DBSCAN의 장점으로는 클러스터의 모양이 자유로워 원형일 필요가 없고 노이즈를 자동 감지할 수 있으며 클러스터의 개수를 사전 지정할 필요가 없다는 것입니다.
  
  엘보우 방법: 다양한 K 값에 대해 K-평균 클러스터링을 수행한 후 각 K에 대해 WCSS 값을 계산해 이를 그려보았을 때 급격히 감소하다가 완만해지는 지점입니다. 팔꿈치처럼 꺾이는 지점을 최적의 K값으로 간주해 지정할 수 있습니다. 이는 직관적이고 시각적으로 이해가 쉬우며 계산이 간단하다는 장점을 가지고 있습니다.
  
  Gap Statistic: 실제 데이터 클러스터링 결과를 무작위로 생성된 기준 데이터와 비교해 클러스터링이 얼마나 의미있는지를 확인하는 방법입니다. 실제 데이터에 대한 K-평균 클러스터링을 수행해 얻은 WCSS값과 원래 데이터와 같은 분포와 차원의 무작위 기준 데이터를 생성하고 WCSS값을 계산합니다. 
  <img width="190" alt="image" src="https://github.com/user-attachments/assets/11cfd6fa-9f1e-44b1-ab4c-9cc2a50ad152" />
  
Wk는 실제 데이터의 WCSS, Wbk는 기준의 데이터의 WCSS, B는 기준 데이터의 샘플 수를 뜻합니다. 최적의 K값을 선택하기 위해서는 Gap(K)가 가장 큰 K를 선택합니다. 

---

## Youtube video link
https://youtu.be/HwhIAZ-Q8aY?si=XiPgRS2CDoTR-w6B

