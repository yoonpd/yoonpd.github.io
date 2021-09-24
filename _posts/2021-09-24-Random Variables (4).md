# Random Variables (4)

## Continuous Random Variable and PDF (Probability Density Function)

- **일상에서 많은 RV는 보통 continuous values를 갖고 있음** <br/>
  → 대표적인 예로, 자동차의 속력🚗

- All of the concepts and methods for discrete RVs have continuous counterparts. <br/>
  → 이를 간단한 그래프와 수식으로 살펴보자. <br/>
  <img width="402" alt="스크린샷 2021-09-23 오후 2 48 22" src="https://user-images.githubusercontent.com/37065429/134603695-488094cd-11ef-469d-aa33-0d6a2a3c6baf.png"><br/>
  → 지금까지 봐왔던 discrete RVs이다. 여기서, **두 값(x) 사이의 확률**은 어떻게 구할 수 있을까?💩 <br/>
  <img width="559" alt="스크린샷 2021-09-23 오후 2 50 00" src="https://user-images.githubusercontent.com/37065429/134603783-a6f368f4-7c8c-4d86-bac5-90593003c2c8.png"><br/>

  1. **간단하게 그 사이의 값을 더하면 된다**.
  2. 물론, 이를 만족하려면 두 번째 조건을 만족해야 한다. <br/>

  → 그러면, 이 개념을 continuous로 확장한다면 어떤 개념을 추가하면 될까? 바로, <span style="color:red">**적분**</span>이다. <br/>

  <img width="493" alt="스크린샷 2021-09-23 오후 2 51 35" src="https://user-images.githubusercontent.com/37065429/134603864-270d51f6-30ec-4d36-84c0-191c808f5ca4.png"><br/>

  - Continuous values들의 그래프는 고등학교때부터 봐왔던 꾸불꾸불한 모습을 갖고 있다.

  - 그럼 a와 b 사이의 확률은 어떻게 구할까?<br/>

    <img width="479" alt="스크린샷 2021-09-23 오후 2 52 24" src="https://user-images.githubusercontent.com/37065429/134603938-94ca7186-d590-4d7f-9846-6358cf470545.png"><br/>

    1. 간단하게 흔히 알고 있는 적분 공식을 사용하면 된다.
    2. 이것도 두 번째 조건을 만족해야 한다.
    3. 이것이 <span style="color:red">**PDF(Probability Density Function)**</span>이며, <span style="color:blue">**notation이 바뀌었음**</span>을 확인하자. <br/>
       

- PDF의 속성을 살펴보자. <br/>
  <img width="323" alt="스크린샷 2021-09-23 오후 2 56 30" src="https://user-images.githubusercontent.com/37065429/134604880-8c08b683-0884-4f5f-8008-9481714eb5dc.png"><br/>

  - 지금까지 설명했던 적분의 형태이다. 그러면 우리는 아주 아주 작은 δ를 사용한다면, 특정 값에서의 확률을 비슷하게 구할 수 있다.
  - 하지만, '특정 값'에서의 확률은 0이 된다. 적분은 넓이니까! 💩 <br/>
    

- 자 한번, uniform한 형태에서 PDF 그래프를 그려보고, Expectation과 Variance를 구해보자. <br/>
  <img width="211" alt="스크린샷 2021-09-23 오후 2 57 46" src="https://user-images.githubusercontent.com/37065429/134605121-9a2e0a36-13c2-4718-b316-87ad2992a468.png">→ PDF 그래프는 다음과 같이 그려지고, 총합은 당연히 1이 나온다.<br/>
  <img width="503" alt="스크린샷 2021-09-23 오후 2 58 11" src="https://user-images.githubusercontent.com/37065429/134605169-15464fb1-eb96-4f4e-9619-24fe279342c0.png">

  - Expecatation과 Variance는 다음과 같이 쉽게 구해질 수 있다.<br>



## CDF (Cumulative Distribution Function)

- 그렇다면, 지금까지 배운 PMF와 PDF를 종합할 수식은 없을까? 

  - Discrete : PMF
  - Continuous : PDF <br>
    <img width="271" alt="스크린샷 2021-09-23 오후 3 04 24" src="https://user-images.githubusercontent.com/37065429/134605944-23803eaa-efdc-4aba-b463-ea1d4321e28e.png"><br>
    → 간단하게 표현이 가능하고, 이는 단순히 이전의 값을 모두 더한 것을 의미한다. <br>
    → 그래프로 PMF가 CDF로 변환되는 과정을 살펴보자. 💩<br>
    <img width="704" alt="스크린샷 2021-09-23 오후 3 09 28" src="https://user-images.githubusercontent.com/37065429/134606018-51b8d64e-5430-4510-b232-b9f715bb94ab.png"><br>
    → 수식과 종합해서 본다면, '누적'된 값임을 알 수 있다.<br>

- 이러한 CDF의 속성을 한 번 살펴보자.<br>
  <img width="541" alt="스크린샷 2021-09-23 오후 3 21 12" src="https://user-images.githubusercontent.com/37065429/134606087-01764a7c-8bef-49ca-aa15-a460cb9c16d6.png"><br>
  → 앞서 말한, PMF와 PDF의 속성 덕분에 누적 값은 항상 증가하는 방향이다. (내 카카오 주식은 반대다.)<br>

  → 또한, 무한대로 갈 수록 1에 가까워지고 그 반대의 경우에는 0으로 수렴하게 된다. <br>
  → 여기가 중요하다🐯

  1. discrete의 경우에는 CDF는 piecewise constant function(계단 함수)의 형태를 갖게 된다. <br>
     → 그러면 k에서의 확률은 CDF에서 k번째와 k-1번째 값을 빼서 계산이 가능하다.
  2. continuous의 경우에는 PDF와 CDF의 관계성이 나타나게 된다. <br>
     → PDF를 적분해서 얻은 것이 CDF이기 때문에, 미분을 했을 땐 역으로 계산할 수 있다.<br>

- 예제를 하나 생각해서 CDF의 이점을 생각해보자.

  - 세 번의 시험을 본 뒤 점수를 내고, 네 번째 시험에서의 점수가 앞선 세 점수보다 높을 확률을 구해보자.<br>
    <img width="818" alt="스크린샷 2021-09-23 오후 3 40 38" src="https://user-images.githubusercontent.com/37065429/134606614-90be739b-12ed-47e6-bb02-8b8b01515610.png"><br>

## Exponential RV

- 이는 파라미터 λ를 갖는 exponential RV를 의미한다.

- 수식으로 보면 더욱 간단하다. <br>

  <img width="220" alt="스크린샷 2021-09-23 오후 4 09 19" src="https://user-images.githubusercontent.com/37065429/134606875-3607eb83-3cd6-4956-b963-b8a3ffac41b5.png"><br>

-  λ에 따라 RV는 특성을 다르게 갖게 된다. <br>
  → λ가 크다면 : 급격히 낮아지는 형태의 RV를 갖게 된다. <br>
  → λ가 작다면 : 천천히 낮아지는 형태의 RV를 갖게 된다. <br>
  <img width="606" alt="스크린샷 2021-09-23 오후 4 10 32" src="https://user-images.githubusercontent.com/37065429/134607001-9486b19d-5b1e-4650-b46e-82e527ea143b.png"> <br>

  
  
- 그렇다면, Exponential RV를 사용하여 CDF, Expectation, Variance를 구해보자. <br>

  <img width="458" alt="스크린샷 2021-09-23 오후 4 16 20" src="https://user-images.githubusercontent.com/37065429/134607831-42b4ad69-9fde-4ccf-935b-094bcb1108fc.png"><br>
  → CCDF는 Complementary CDF를 의미한다. <br>
  → 이러한 CCDF는 Waiting Time 모델링에 유리하다. 이후 예제에서 이를 다루겠다. <br>

  <img width="599" alt="스크린샷 2021-09-23 오후 4 19 08" src="https://user-images.githubusercontent.com/37065429/134607890-301bf7db-060c-4146-ad12-92df9517a95a.png"><br>
  → Expectation과 Variance를 구하는 방법은 다음과 같다. <br>

- 그럼, Waiting time 모델링에서 어떻게 유리한지 예제를 통해 살펴보자. <br>
  → messages arriving at a computer, some equipment breaking down, a light bulb burning out, etc... <br>
  → 근데, 우리는 앞서 이러한 '발생 확률'을 예측하는 것을 해보지 않았는가? <span style="color:red">**Geometric**</span> <br>

  → 이건 또 나중에 살펴보도록 하고, 먼저 예제를 들어보자

  - 메테오가 한국에 떨어진다고 한다. 큰일이다.⚠︎
  - Time of landing은 Expectation(mean)을 10 days로 갖는 Exponential RV로 모델링 되어있다.
  - 그러면, 현재가 자정일 때 첫 날, 6시와 18시 사이에 메테오가 떨어질 확률은 어떻게 될까?<br>
    <img width="588" alt="스크린샷 2021-09-23 오후 4 52 50" src="https://user-images.githubusercontent.com/37065429/134608370-fb697801-9d03-4efb-8a27-c1cada419551.png"><br>
    → CCDF를 사용한다면 이와 같이 쉽게 해결할 수 있다.<br>

- 자, 그럼 뒤로 미뤄뒀던 Geometric과의 차이점을 알아보자.

  - 어떤 상점에서 손님의 도착에 대한 정보를 저장하고 있다.
    1. 30분 동안 들어온 손님의 수를 기록한다. (30분의 window size를 갖는다.) <br>
       → discrete 
    2. 손님들이 들어온 정확한 시간을 기록한다. <br>
       → continuous
    
  - 이 둘의 기록하는 방법(modeling)에서의 차이점은 존재하지만, 두 방법이 '틀린 방법'은 아니다.

  - In many cases, continuous case is some type of <span style="color:green">**limit**</span> of its corresponding discrete case. <br>
    → 그렇다면, 수학적으로 어떻게 geometric과 exponential이 극한에서 만나는지를 설명할 수 있을까?

    - 이를 위해 몇 가지 가정을 해보자.

      1. SLOT : 단위 시간

      2. Continuous system == Discrete system with <br>

         → **infinitely many slots** whose duration is <span style="color:red">**infinitly small**</span>. <br>
         → success probability "**p**" over one slot <span style="color:blue">**decrease to 0 in the limit**</span>. <br>

      3. <img width="676" alt="스크린샷 2021-09-23 오후 5 32 08" src="https://user-images.githubusercontent.com/37065429/134618406-b471eed9-9dab-45dc-9836-315bef9eea6a.png"><br>
         → geometric RV인 X_δ^geo를 새롭게 가정하자.

      4. 위에서 정한 geometric RV의 success probability를 P_δ라고 하자. <br>
         → 그러고, <br>

         <img width="132" alt="스크린샷 2021-09-24 오후 1 34 13" src="https://user-images.githubusercontent.com/37065429/134618847-4c742718-82b5-40d6-952a-9192485af7db.png">이라고 하면, 얘는 마법같이 앞서 얘기한 Exponential RV의 조건에 모두 부합하게 된다. <br>

    - 가정한 내용을 기반으로, X_δ^geo의 확률을 구해보면, <br>
      <img width="377" alt="스크린샷 2021-09-24 오후 1 37 03" src="https://user-images.githubusercontent.com/37065429/134619004-a59419dc-c476-4c5e-8e1c-69c69385e6ff.png"><br>
      → Geometric이니까, 그 녀석의 수식이 적용된다. <br>
      → 근데, 얘는 Exponential CDF와 비슷하게 생겼다.

      - 자, 그래프로 한 번 보자. <br>
        <img width="744" alt="스크린샷 2021-09-24 오후 1 43 11" src="https://user-images.githubusercontent.com/37065429/134619434-4c1a91da-1fdc-4e45-a52e-68f999a674db.png"><br>

        → δ는 slot의 길이였고, n이 자연수라면, δn은 slot이 n만큼 이어질 때의 위치가 될 것이다. <br>
        → 즉, nδ는 그래프에서 보이듯 x값이라 할 수 있다.

      - 이 내용을 정리한다면 다음과 같다. <br>
        <img width="734" alt="스크린샷 2021-09-24 오후 1 57 38" src="https://user-images.githubusercontent.com/37065429/134620578-f8d4c1d9-34dd-4316-9004-ec6dba608b03.png">

        

