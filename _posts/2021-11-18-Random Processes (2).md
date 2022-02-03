---
title: "Random Processes (2)"

categories:
  - Probability and Random Variables
toc: true
toc_sticky: true
---

# Random Processes (2)

> 현재 정리하는 내용은 KAIST EE의 이융 교수님, Probability and Intorductory Random Process 강의를 참고하여 작성했습니다.

## Poisson Processes : Poisson RV and Basic Idea

<br>*뿌아송~*

- 오늘 배울 것은 Poisson process로 BP에서 Continous한 상황을 생각한 방식이다.



### Background : Poisson rv X with parameter λ (1)

- 예전에 배웠던 Binomial RV에 대해 생각해보면 이 놈의 정의는 다음과 같다. <br>
  → n번의 독립적인 시도에서 성공확률 p를 가질 때, 성공 개수 <br>
  → Models the number of successes in a given number n of independent trials with success probability p.

- 공식은 다음과 같다. <br>
  ![image](https://user-images.githubusercontent.com/37065429/142373616-b3f3792b-5d08-4dbc-97bd-de8a99474d37.png)

- 여기서 우리는 궁금해진 것이 있다.<br>
  → 매우매우 큰 n과 매우 작은 p를 가지고 np = λ로 정했을 때, 어떤 일이 발생할까?<br>→ 즉, np = λ를 가정하고 n이 무한대로 갈 때 어떻게 될까?

  - 여기서 np = λ는 쉽게 생각하면 된다.
    1. n = 1일 때, p = λ
    2. n = 2일 때, p = λ/2
    3. n = n일 때, p = λ/n

- 앞서 나온 공식을 np = λ를 적용해서 lim하기 쉽게 풀게 되면<br>
  ![image](https://user-images.githubusercontent.com/37065429/142373958-c46076af-6346-4e33-bc3d-dbaf0ba8901e.png)<br>→ 요놈이 Poisson rv이다.<br>

  <br>

### Background : Poisson rv X with parameter λ (2)

- 앞서 찾아낸 Poisson rv의 공식은 다음과 같다.<br>![image](https://user-images.githubusercontent.com/37065429/142374734-560b831c-696d-4abb-87d5-b80a8e502033.png)

  1.  기본적으로 Binomail을 표방했기 때문에, λ는 nonnegative integer value를 갖는다.
  2. Infinitely many slots(n) with the infinitely small slot duration

- Poisson rv의 Expectation과 var은 다음과 같다. <br>![image](https://user-images.githubusercontent.com/37065429/142375134-d752a42d-0a52-4898-9c49-556b50d95e6d.png)<br>

  → <span style="color:red">여기서 Expectation은 mean # of arrivals이다.</span> <br>→ var을 구할 때, np(1-p)에서 n이 무한대로 갈 때를 생각하며 된다. <br>
  <br>

#### Example : Poisson Approximation

- Limit을 취하기 때문에 Approximation이라고 하기도 한다.

- 요놈자식이 어디에 쓰이는지 하나의 예제를 살펴보자.

  > A packet consisting of a string of n symbols is transmitted over a noisy channel.
  >
  > Each symbol has errorneous transmission with prob. of 0.0001, independent of other symbols.
  >
  > Incorrect transmission is when at least one symbol is in error.
  >
  > <br>
  > Question. How small should n be in order for the prob. of incorrect transmission to be less than 0.001?

- 에러 확률은 아주 낮다. 그리고 패킷의 길이가 꽤나 크다. <br>
  → <span style="color:red">Poisson approximation</span>을 사용하자!

- 간단하다. <br>

  ![image](https://user-images.githubusercontent.com/37065429/142376344-b7994bb6-f5d3-467d-9e8a-a34c9940ba75.png)

<br>
<br>



### Design of Continuous Analogue of Bernoulli Process

- Remind 
  - Geometric vs. Exponential
  - Two rvs with memoryless property
  - conitnuous system is <span style="color:orange">discrete system with infinitely many slots</span> whose duration is <span style="color:orange">infinitely small</span>.
- <span style="color:orange">Independence</span> between what happens in a different time region.
- Memoryless and fresh-start property
- <span style="color:red">Key Idea</span> : Making it as a <span style="color:red">limit of a sequence </span>of Bernoulli processes.

<br>

#### Key design idea to develop a Continuous Twin (1)

- Continuous twin

  - Key point : Understand the number of arrivals over a given interval [0, 𝛕]

  - Assume that it has some <span style="color:red">arrival rate λ</span>.<br>

    → Bern Process에서 하나의 슬롯에서의 성공확률 p를 모방한 것 <br>
    → # of arrivals / unit time

  - 우리는 discrete time slots의 BP를 다룰 줄 안다.

- Limit을 해준다고 했으니 일단은 [0, 𝛕] 구간을 δ의 길이를 갖도록 쪼개주자. <br>
  → Then, n = # of slots = 𝛕 / δ

- 그럼, 여기서 δ를 무한대로 보내버리면 continuous 상황을 만들 수 있을 것이다!

<br>



#### Key design idea to develop a Continuous Twin (2)

- 우리가 갖고 있는 아이디어는 : during one time slot of length δ
- 그럼 모델링을 위해 여기서 3가지의 상황을 생각해보자.
  1.  슬롯에 하나의 도착이 있을 확률 <br>
     → **arrival rate와 slot length**가 관련이 있을 것이다. <br>
     → arrival rate가 높아지면 확률 상승, 반대면 반대 (slog length도 비슷)
  2.  슬롯에 두 개 이상의 도착이 있을 확률 <br>
     → **슬롯이 매우 작아지면 거의 없을 법한 확률**이다.
  3.  슬롯에 도착이 없을 확률<br>
     → **전체 확률(1)에서 [1]과 [2]의 확률을 빼주**면 된다~!
- 수학적으로 이제 생각해보자.
  1. arrival rate와 slot length가 [1]의 확률에 영향을 끼치니 <br>→ λδ
  2. 거의 없을 법한 확률이니까 <br>
     → 0
  3. 이건 [1]과 [2]를 빼면 되니까 <br>
     → 1 - λδ - 0
- 근데.. 없을 법한 확률이지 완전히 0은 아니다. 따라서 다음과 같이 수정을 해준다.
  1. **λδ + o(δ)**
  2. **0 + o(δ)**
  3. **1 - λδ + o(δ)**
- 여기서 o(δ)의 정의는 다음과 같다. <br>
  → Some function that <span style="color:blue">goes to zero faster than delta</span>. <br>
  → Thus, for very small delta, o(δ) becomes <span style="color:blue">negligible</span>, compared to δ.

<br><br>

#### Key design idea to develop a Continuous Twin (3)

- 지금까지 우리가 생각한 아이디어는 다음과 같다.

  - Given <span style="color:purple">small</span> δ, <br>→ # of arrivals : ~ Bin(n, p) where n = 𝛕 / δ and p = λδ

  - 그럼 여기서, δ → 0라고 한다면, np = 𝛕 / δ * λδ = λ𝛕 <br>→ Oh! 어디서 봤던 것이다! 바로 <span style="color:red">Poisson rv</span>! <br>

    → [ δ → 0 ] == [ n → INF ]

  - 따라서, 다음이 성립되게 된다. <br>![image](https://user-images.githubusercontent.com/37065429/142384828-550963ba-a089-4f3b-9b25-6c29ee2c5f1f.png)<br>

    → Expectation = λ𝛕 : mean # of arrivals * time



## Poisson Processes: Definition and Properties

### Poisson Process: Definition 

- An arrival process is called a <span style="color:blue">Poisson process</span> with rate λ, if the following are satisfied :
  1. **Independence** : 두 개의 <span style="color:red">겹치지 않는</span> 시간대의 # of arrivals는 독립적이다. <br>
     ![스크린샷 2021-11-25 오후 2 52 09](https://user-images.githubusercontent.com/37065429/143387134-276b8e54-6de5-416d-a057-f181d02f46b8.png)
  2. **Time homogeneity** : 동일한 길이를 갖는 시간대의 # of arrivals의 확률은 동일하다. <br>
     ![스크린샷 2021-11-25 오후 2 52 48](https://user-images.githubusercontent.com/37065429/143387199-3263e037-529f-4d0d-9448-d952513169b9.png)
  3. **Small interval probability** : <br>
     ![image](https://user-images.githubusercontent.com/37065429/143387231-b0455395-8c63-468d-bbe1-83bdce3f4702.png)<br>→ 함수 oi(𝛕)는 negligible하다.
  4. **Distribution of N𝛕** : (3)의 확장판이다.<br>
     ![스크린샷 2021-11-25 오후 2 57 48](https://user-images.githubusercontent.com/37065429/143387733-0df3be70-b107-468c-8061-0e9630502801.png)

<br><br>

### Poisson Process : P(k, 𝛕), N𝛕 and T

- 이해를 돕기 위해 몇가지 질문을 던져보자.

1. Number of arrivals of <span style="color:orange">any interval</span> with length 𝛕 ~ Poisson(λ𝛕)<br>
   → <span style="color:orange">**PP는 '시간의 위치'가 아닌, '시간 자체'와 상관이 있다.**</span><br>→![스크린샷 2021-11-25 오후 3 04 46](https://user-images.githubusercontent.com/37065429/143388386-3a7a8f44-417e-4050-9887-b33967a3443a.png)<br>
   → 따라서, 모든 값에 대해 Poisson RV 값을 갖게 되고.<br>

   → 여기서 λ𝛕는 <span style="color:orange">mean # of arrivals</span>를 의미한다. 죽, 0 ~ 𝛕 까지의 시간 중에서의 mean # of arrivals.<br>

2. Time of first arrival T <br>
   → Continuous 한 상황에서 생각을 해보자. <span style="color:orange">CDF!</span><br>
   → ![image](https://user-images.githubusercontent.com/37065429/143388659-3b0a60cd-e25a-40c6-82b6-122bc151261f.png)<br>
   → 이는 Exp rv임을 알 수 있고, 따라서 memoryless 속성을 갖는다.<br>

<br>

#### Poisson Process: Example

- Receive emails according to a Poisson process <span style="color:red">at rate λ = 5 messages/hour</span>.

  1. Mean and variance of mails recieved during a day <br>
     → day = 24 hours. <br>
     → E(N𝛕) = var(N𝛕) = λ𝛕 = 5 * 24 = 120
  2. P[one new message in the next one hour] <br>
     → 𝛕 = 1 <br>
     → ![스크린샷 2021-11-25 오후 3 13 22](https://user-images.githubusercontent.com/37065429/143389297-bbd4d961-608f-411e-b820-6652f7194cf3.png)
  3. P[exactly two msgs during each of the next 3 hours] <br>
     → '시간의 위치'가 아닌, '시간 자체'와 상관 있으며, 따라서 두 개의 겹치지 않는 시간대의 확률은 독립적! <br>
     → P(2, 1) * P(2, 1) * P(2, 1) <br>
     → ![image](https://user-images.githubusercontent.com/37065429/143389478-d82a842c-a183-4d62-8b3f-c9074e0f986a.png)<br>

  <br>

  ### Memoryless and Fresh-start property

  - 이전에 배웠던 Bern. process의 속성과 아주 비슷하지만, 연속적인 시간을 다루기 때문에 time slots이 없음을 먼저 숙지하자.
  - <span style="color:red">Fresh start. </span>: Start <span style="color:red">wathcing at time t</span>, then you see the Poisson process, <span style="color:red">independent of **What has happend in the past**</span>.
  - Bern. Process에서도 배웠던 k-th arrival time, Yk에 대해서도 생각해보자. <br>
     → k-th interval time을 Tk라고 했을 때, Tk = Yk - Yk-1이 될 것이다. <br>
    ![스크린샷 2021-11-25 오후 3 26 30](https://user-images.githubusercontent.com/37065429/143390766-7ac96a2c-a1b0-4962-bec5-cd113658b1ab.png)<br>→ 그럼, Yk = T1 + T2 + ... + Tk이고 이것은 BP와 달리, <span style="color:orange">sum of i.i.d. exponential RVs</span>이다.<br>
    → T1, T2, ..., Tk들은 <span style="color:orange">모두 독립</span>이기 때문에, Exp.과 Var.는 다음과 같이 표현된다. (Linear transform) <br>
    ![스크린샷 2021-11-25 오후 3 27 38](https://user-images.githubusercontent.com/37065429/143390892-f58865c1-9d82-473a-ae1b-b6909befa159.png)<br>

  <br>

  #### PDF of Yk

  - 아주 작은 값 δ가 주어졌을 때, <br>
    → PDF of Yk = ![스크린샷 2021-11-25 오후 3 36 35](https://user-images.githubusercontent.com/37065429/143391904-f51bf29f-5c0f-4271-a4ab-219129b1ed8b.png) = prob. of k-th arrival over [y, y+δ]<br>→ 적분을 위해 직사각형을 만든다고 생각하면 된당.
  - 여기서, δ는 아주아주아주 작은 값이기 때문에, 오직 하나의 arrival만 생긴다고 하면 앞의 식은 다음과 같이 전개된다.<br>
    ![스크린샷 2021-11-25 오후 3 38 02](https://user-images.githubusercontent.com/37065429/143392057-effa2a62-a742-4219-8095-891d6e2ff657.png)<br>→ 이것을 <span style="color:blue">Erlang rv</span>라고 한다.
  - Erlang rv.<br>
    ![스크린샷 2021-11-25 오후 3 38 46](https://user-images.githubusercontent.com/37065429/143392128-d0fe4326-53a4-4c3e-8916-a374e9c79b4c.png)<br>→ Bern. 에서 했던 것과 같이, Erlang(1, λ) = EXP(λ)이다. <br>
    → *Bern.에서는 Geom!*<br>

  <br>

  ### Poisson vs. Bern.

  ![스크린샷 2021-11-25 오후 3 40 48](https://user-images.githubusercontent.com/37065429/143392346-bb94f451-10cf-4478-a226-e69bf7a8f1cf.png)<br>

  <br> 

  ### Example: Poisson Fishing 

  > Catching fish : Poisson process λ = 0.6/hour.
  >
  > 2시간 동안 낚시를 하게 된다.
  >
  > 여기서, 2시간 안에 적어도 한 마리의 물고기를 낚는다면, 2시간째에 낚시를 멈춘다(그 동안 몇마리를 잡든 상관 없다.).
  >
  > 그렇지 않다면 한 마리의 물고기를 낚을 때까지 계속한다.

  1. fishing time > 2 hours. <br>
     → 2시간 초과를 한다는 것은, 2시간 동안 한 마리도 못잡았다는 뜻이다. <br>
     ![스크린샷 2021-11-25 오후 4 36 59](https://user-images.githubusercontent.com/37065429/143399197-4cc3d588-7944-44a3-bce1-ef42ba30dbd7.png)

  2. 2 < fishing time < 5<br>
     → 2시간 동안 한 마리도 못 잡았고, 3시간 동안 적어도 한 마리를 낚을 경우이다. <br>
     → 여기서 <span style="color:red">2시간~5시간</span>이 아닌 <span style="color:red">3시간</span>이라는 것은 fresh-start 속성 때문이다.<br>
     ![스크린샷 2021-11-25 오후 4 40 45](https://user-images.githubusercontent.com/37065429/143399654-c0ac8245-c480-4ab3-966c-a4be90bee3d6.png)

  3. Catch at least two fish<br>
     → 이 때는 적어도 2마리의 물고기를 2시간 이내에 잡아야 할 때이다. <br>
     ![스크린샷 2021-11-25 오후 4 42 35](https://user-images.githubusercontent.com/37065429/143399891-10490b0e-078d-4b83-8f09-92a29aa89486.png)

  4. E [ future fishing time &#124; already fished for 3h ]<br>
     → <span style="color:red">Fresh-start</span><br>→ 즉, 3시간 동안 낚은 것은 까먹어버리고 새롭게 한 마리를 잡는 것에 대한 Expectation을 구하면 된다.<br>
     ![스크린샷 2021-11-25 오후 4 43 14](https://user-images.githubusercontent.com/37065429/143399974-adff60a3-8f71-46a4-b0d8-ee275fa691e3.png)

  5. E[ total fishing time ]<br>
     → Expectation은 <span style="color:red">mean # of arrivals</span>이다. 따라서, 걸린 시간을 다 더해주자.<br>

     → 그러면 2시간 전에 걸린 시간(<span style="color:red">이건 무조건 2시간</span>)과 딱 2시간째, 2시간 이후를 구하면 된다. <br>
     → Continuous에서는 특정 값에 대한 확률은 0이라는 것을 다시 생각하자. <br>
     ![스크린샷 2021-11-25 오후 4 46 05](https://user-images.githubusercontent.com/37065429/143400375-1317b40a-bdcf-4216-b73b-6e7c66489297.png)

  6. E[ number of fish ]<br>
     → 앞의 것과 같지만, λ * 시간 = 물고기 개수!라는 것을 생각해보면 (5)에 λ를 곱해주면 된다.<br>

     ![스크린샷 2021-11-25 오후 4 48 17](https://user-images.githubusercontent.com/37065429/143400644-3a6647f9-5088-4309-bf86-342c1768d2b3.png)

  <br><br>

  
