![스크린샷 2023-01-06 오전 9 15 45](https://user-images.githubusercontent.com/94108712/210904175-1db22a0d-97be-438b-8af0-24214a5342af.png)

# 9️⃣ boostcamp AI Tech 4th - RecSys

## 👪 Members
| [<img src="https://avatars.githubusercontent.com/u/94108712?v=4" width="200px">](https://github.com/KChanho) | [<img src="https://avatars.githubusercontent.com/u/22442453?v=4" width="200px">](https://github.com/sungsubae) | [<img src="https://avatars.githubusercontent.com/u/28619804?v=4" width="200px">](https://github.com/JJI-Hoon) | [<img src="https://avatars.githubusercontent.com/u/71113430?v=4" width="200px">](https://github.com/sobin98) | [<img src="https://avatars.githubusercontent.com/u/75313644?v=4" width="200px">](https://github.com/dnjstka0307) |
| :--------------------------------------------------------------------------------------: | :----------------------------------------------------------------------------------------------: | :--------------------------------------------------------------------------------------: | :--------------------------------------------------------------------------------------: | :--------------------------------------------------------------------------------------:
|                          [김찬호](https://github.com/KChanho)                           |                            [배성수](https://github.com/sungsubae)                             |                        [이지훈](https://github.com/JJI-Hoon)                           |                          [정소빈](https://github.com/sobin98)                           |                            [조원삼](https://github.com/dnjstka0307) |
| 협업 관리, 인퍼런스 구현, EASE, 앙상블 | 모델 탐색, 데이터 전처리, 모델 베이스라인 개발 및 실험, 앙상블 | 모델 탐색 및 실험, Nue-MF Pytorch Project 개발 | 모델 탐색 및 실험 | EDA, DeepFM, Bert4rec |

<br /> 
<br /> 

## 🎬 Movie Recommendation
사용자의 영화 시청 이력 데이터를 바탕으로 사용자가 다음에 시청할 영화 및 좋아할 영화를 예측

<br /> 
<br /> 


## 📄 Data
- 사용자의 영화 시청 이력 데이터 5,154,471 개
- 영화 아이템 메타 정보 데이터 6,807 개

<br /> 
<br /> 

## 💻 Repository Summary
![코드 구조도 drawio](https://user-images.githubusercontent.com/94108712/211151400-d7469957-c0db-48d2-8765-8ecc9e4c3270.png)

<br /> 
<br /> 

## 🗃 Project Process

### 🤖 Model
- AutoEncoder 계열: Multi-VAE, Multi-DAE, MSE-DAE, EASE, ALS
- 시퀀셜 모델: Sasrec, S3rec, Bert4rec

<br /> 

### 📈 Ensemble
- **모델 기반 앙상블**
    - 앙상블 기법으로 각 모델들의 top10 결과를 기반으로 hard voting 방법 사용.
    - 시퀀셜, AE기반 모델들 등 서로 다른 계열의 모델들이 앙상블로 조합했을 때, 시너지가 낼 수 있을 것으로 생각하고 실험을 진행하여 최적의 모델 조합을 찾음. 
    (ease, mse-dae, multi-dae, bert4rec, sasrec)
    - 모델 간 가중치는 각 모델들의 public test 성능을 사용함.
- **top-k 스코프 범위 확장**
    - 각 모델의 top10 범위 밖에도 정답이 존재할 가능성을 고려하여 top-k 스코프 범위 확장
    - k값을 20까지 확장하여 실험을 진행한 결과 public test 성능 기준으로 k=15~20일 때 앙상블 성능이 0.1646으로 가장 좋았음.
    - private test 성능을 확인해본 결과 k=20일 때 더 좋은 성능을 보여주는 것으로 확인되어 K값의 스코프를 확장시키는 것이 일반화 성능을 향상시키는 것으로 생각됨.

<br /> 
<br /> 

## 🏅 Result : Public 6th > Privite 5th

![스크린샷 2023-01-08 오후 11 45 27](https://user-images.githubusercontent.com/94108712/217742589-5ae82226-622b-4f06-b7eb-04f68a35e03e.png)

|리더보드| Recall@10 | 순위 |
|:--------:|:------:|:----------:|
|public| 0.1646 | **6위** |
|private| 0.1634 | **최종 5위** |

<br /> 
<br /> 

**상세한 프로젝트 내용은 레포트를 참고해주세요!**
