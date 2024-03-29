# Second-hand-tablet-price-prediction
[Paper] An Analysis of Price Influencing Factors for Used Tablets

at Journal of Industrial Convergence.


# 분석 과정
## 0. 시행착오
- 맨 처음 이 논문은 다중선형 회귀가 아니라 Linear Mixed model이었다. 제품 범주를 Random effect로 넣어 코드를 돌려봤는데 모델이 형편없었고, 원인을 찾아보기 위해 품목별로 데이터를 보기 시작했다. 
- 문제점
  - 심슨의 역설 발생 -> 전체 데이터에서는 제품 상태가 가장 좋으면 평균 중고판매가가 가장 높았지만, Electronics와 Others에서는 제품 상태가 가장 좋앗을 때의 평균 중고 판매가가 가장 낮았다.
  - 데이터 라벨링 오류 발견 -> 실제 판매 데이터이다보니, 이상하게 라벨링 되어있는 품목이 많았다. 예를 들어, 뷰티 제품인데 Womens -> cloth에 할당되어 있었고, 태블릿 품목에 이어폰 등의 부속기구들이 있었다.
- 해결책
  - 품목을 하나로 고정시키고 라벨링 다시하자...!


## 1. 데이터 전처리

- 가장 힘들었음, Real World data는 생각보다 노이즈가 엄청엄청 많았고, 거래에서 박스만 파는 경우(이건 대체 왜 파는지 모르겠음... $5근처 정도로 팔던데)와 같이 태블릿 판매 섹션에 이런 데이터가 들어오는 지도 모르겠고, 태블릿을 판매하는 경우인데 pc탭에서 발견되는 경우도 종종 있었다. 따라서 태블릿 판매 섹션에서만 데이터를 보는 게 아니라 전 섹션에서 데이터를 한번씩 훓는 과정이 필요했다. 
- real world data는 너무나도 방대해서 excel에서 직접 접근하는 것도 로드하지 못했다. python을 이용하여 전처리를 하였고, 진짜 이 과정에서 에너지도 많이 소비하고 시간도 엄청 많이 걸렸다.

## 2. 모델링
a) 다중선형회귀
</br>
b) 다중 선형회귀 + stepwise
</br>
c) 교호작용 넣은 선형회귀
</br>
d) 교호작용 + stepwise

## 3. 모형 비교
- 모형을 비교하는 metric은 Test-RMSE를 선택

## 4. 최종 모형 선택
- 모형 4 선택됨


# 느낀점
- 여태 했던 프로젝트 중, 가장 긴 호흡을 가지고 했던 프로젝트이다. 프로젝트 중간에 중단되었던 기간이 빈번해서, 체크포인팅과 기록이 무엇보다 중요했었다.
- GIGO를 여실히 느꼈던 작업, 데이터 분석에서 데이터 전처리 과정이 왜 90% 정도를 차지하는 지를 알 것 같다. 원본데이터를 하나하나 확인할 각오를 해야하고, 상식적으로 말이 되는 데이터인지 항상 확인하고 그렇지 않다면 이유를 무조건 찾아야한다. 만약 찾지 않으면 쓰레기같은 output이 나오게 될 것이다.
- 한 문장을 쓸 때마다 그 문장의 근거를 찾아내는 것도 시간이 꽤 걸렸다. 사실 다른 논문을 읽을 때에는 선행연구 부분을 자세하게 안 읽고 넘어가고 출처도 대충 보고 넘어갔지만, 막상 논문을 직접 써 보니까 이 부분이 꽤나 시간을 많이 차지하였다. 
- 연구직은 내가 원하는 결과 혹은 자료가 나올 때 까지 참고 기다리는 인내심과 체력이 중요한 요인인 것 같다. --> 중꺽마: 중요한 것은 꺾였는데도 다시하는 마음.
- 데이터를 확인할 때 평균만으로는 부족하다. 
- EDA는 Marginal distribution을 파악하기 위한 과정이다.
- 논리적으로 생각해야함.
- 미팅 전 준비와 미팅 후 기록 확실하게!
  - 과정위주로 이야기하고 교수님 설득한다는 마인드로 진행할 것
  - 피드백 받는 부분있으면 내용 꼼꼼히 정리.
- 꾸준히, 효울적으로 일하되 한정된 체력 언제, 얼만큼, 어디에 쓸 것인지 잘 분배할 것
- 큰 그림 볼 줄 아는 능력 기르기
  - 항상 내가 일하는 것의 줄기를 잊지 않고, 지금 내가 뭘 하고 있고, 어떤 과정 속에서 하는건지 알고 있어야한다.
  - 왜?라는 의문을 가져야한다. -> 수동적인 자세 X
- 가장 중요한 것은 스스로 멘탈 부여잡기!
  - 중심을 잡고, 남들과 비교하지 않기. 

<!--
- 평균은 생각보다 믿을 만한 수치가 아니다! -> 분산...?

- GIGO 를 여실히 느끼는중,,, 
  -> 데이터로 이야기하자! 
    원본 데이터를 볼 수 있어야 함, 
    말이 되는 데이터!!
  -> data cleaning 의 중요성,, 이래서 NLP를 이용해 데이터 정제하는 ML 을 많이 쓰는구나,,,
 -> 이제 NLP를 좀 좋아해봐야겠다!

- EDA는 marginal distribution을 파악하기 위한 과정!
  
- 미팅 전후 준비 확실하게!!
   -> 결과보다는 과정위주로 발표! 교수님 설득한다는 마인드로 하기기!, 
  -> 피드백 받는 부분 있으면 내용 꼼꼼히 정리하고 앞으로 어떻게 하면 같은 내용에       
    정리  !  !  는 받 는해야할 지민 해  !F하!   ?볼가족분것다    꼼 ! ㅠ , 려  석  그냥서료a에대 생고 으t만
 ED @
-> 인코딩 왜저래~~ 다 까먹었당 블로그에 정리할 때 다시 생각해봐야겠다

- 꾸준히, 그리고 효율적으로 일하기!


- 무엇보다 중요한건 멘탈 부여잡기!
   -> 스스로 중심을잡자!,  남들과 비교하지 않기~~ 내 주위에는 아웃라이어들이 많다고 생각!!
   -> 근데 객관적으로 사실임,, 
   -> 통계로 밥 벌어먹고 살 수 있을까...? -> 당연당연~~ 
  
- 큰 그림을 볼 줄 아는 능력을 기르자!
   -> 항상 줄기를 잊지 말기
  -> 왜?라는 의문을 갖도록 하자! 수동적인 자세 X
   -> 큰 그림 속에서 지금 내가 하고 있는 것이 뭘하고 있는 건지, 
     왜 하는건지 정확하게 파악하기

- 한정된 집중력/체력을 어디에, 언제, 얼만큼 쓸 것인지를 정하는 것도 능력임

- 논리적으로 생각하는 법
- real-world 데이터는 생각보다 힘드러~~
--!>
