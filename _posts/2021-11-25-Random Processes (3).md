---
title: "Random Processes (3)"

categories:
  - Probability and Random Variables
toc: true
toc_sticky: true
---

# Random Processes (3)

> 현재 정리하는 내용은 KAIST EE의 이융 교수님, Probability and Intorductory Random Process 강의를 참고하여 작성했습니다.

## Playing with Bern. and Poisson Process

### Description via Inter-arrival Times

- 지금까지 배웠던 Bern.과 Poisson에서 <span style="color:orange">Inter-arrival</span>이라는 조건 하에서 생각해보자.
- Bern.과 Poisson의 간략하고 직관적인 설명을 확인해보자. <br>
  ![스크린샷 2021-11-25 오후 5 05 32](https://user-images.githubusercontent.com/37065429/143402983-86c6a29f-fbe1-44fe-9edd-4f378505647a.png)
- 이번 정리에서부터 쭉 쓰게될 Notation은 다음과 같다. <br>
  ![스크린샷 2021-11-25 오후 5 12 51](https://user-images.githubusercontent.com/37065429/143403971-36313cc2-b34e-4a32-9333-9d548d6cc884.png)<br><br>

#### Example.

- It has been observed that after a rainy day, the number of days until the next rain is <span style="color:orange">Geom(p)</span>, indepedent of the past.
- <span style="color:orange">Question. </span>What is the probability that it rains on both <span style="color:orange">the 5th and the 8th</span> day of the month?
  - 우리가 지금까지 배웠던 the geometric PMF를 사용한다면? 때에 따라 다소 어렵고 복잡한 문제가 될 수도 있다.
  - 그래서 쉽게 생각해보자.
    1. Rainy days is a Bern. process
    2. Each rainy day is independent with probability p.
  - 그럼 결론은? <span style="color:orange">p^2</span>이 된다. 쉽다!

<br>

### Split: Bern. Process

- BP(p)를 두 개의 process로 나눠보자.
- 쉽게 생각해서, q라는 성공 확률을 갖고 성공 시 A 프로세스로 실패 시 B 프로세스로 옮긴다고 해보자. 그림은 다음과 같다.<br>![스크린샷 2021-11-25 오후 5 22 35](https://user-images.githubusercontent.com/37065429/143405223-06047bab-a4ff-4bb6-821f-d464ff781090.png)
- <span style="color:orange">Question. </span>What are the two split processes? <br>
  → BP(pq) and BP(p(1-q))<br>
  → 새로운 BP가 두 개 생기게 된다!
- 그럼, 이 두 BP가 서로 독립일까? <br>
  → 당연히 아니다.<br>
  → 하지만 <span style="color:orange">각 프로세스의 각 슬롯</span>끼리는 independent하다.

<br>

### Merge: Bern. Process

- 자 이제 두 개를 합치는 상황에서는 어떻게 되는지 살펴보자.
- 이전과는 관계가 없는 문제라고 생각하고, Proc. 1과 Proc. 2를 합친다고 생각하자. <br>
  → Merge **BP(p)** and **BP(q)** into one process.<br>
  ![스크린샷 2021-11-25 오후 5 35 37](https://user-images.githubusercontent.com/37065429/143407089-d2a9af0e-3193-42ea-b763-3bab861ad52e.png)
- 여기서, 1과 2의 특정 슬롯을 합칠 때 충돌이 발생한다면 merged process에는 하나만 들어간다고 하자.
- <span style="color:orange">Question. </span>Probability of having at least one arrival <br>
  → 1 - (1 - p)(1 - q) = p + q - pq <br>
  → <span style="color:orange">적어도 하나</span>라고 말하는 이유는 Collid arrival에 대한 예외를 처리했기 떄문이다.
- 그러면, 합쳐진다는 것이 '도착'이라고 해석한다면<br>
  → Merged Process : BP(<span style="color:orange"> p + q - pq </span>)
- 살짝 꼬아서, Merged proc.에 도착이 생겼을 때, 그것이 1번 proc.으로 부터 왔을 확률은? <br>
  ![스크린샷 2021-11-25 오후 5 35 19](https://user-images.githubusercontent.com/37065429/143407045-da90266a-ef39-4079-b1b5-60ffd19bd725.png)

<br>

<br>

### Split: Poisson Process

- 개념은 Bern. Process를 split했던 것과 같다.

- p의 확률로 keep process로 분리, 1-p의 확률로 discard process로 분리한다고 해보자.

- 그럼 이렇게 분리된 <span style="color:orange">split process</span>는 무엇일까?<br>
  → 얘네도 <span style="color:orange">Poisson Process</span>이다.

- 그래서 이들도 어떠한 속성을 갖게 되는데

  1. Independence : 다른 시간대에 존재하는 process는 서로 독립적이다.

  2. Time-homogeneity : 동일한 길이의 시간대에서의 process는 동일하다.

  3. Small interval probability over δ-interval <br>
     → keep process의 관점에서 보도록 하자.

     1. 한 슬롯(δ-interval)에서 도착이 1개일 경우 : p(λδ + o(δ))
     2. 한 슬롯에서 도착이 2개(<span style="color:gray">이상</span>)일 경우 : p(o(δ))
     3. 한 슬롯에서 도착이 0개일 경우 : 1 - p(λδ + o(δ) + o(δ))<br>

     ![image](https://user-images.githubusercontent.com/37065429/143731868-95308911-01fa-4f6d-a80d-131a5d2e7a3d.png)<br>
     → o(δ)는 negligible하다는 것을 기억하자.

- 따라서, 두 프로세스는 <span style="color:orange">PP(λp)와 PP(λ(1-p))</span>로 분리되게 된다.

<br>

### Merge: Poisson Process

- 요놈도 개념은 Bern. Process를 merge했던 것과 같다.

- PP(λ1)과 PP(λ2)를 Merge!

- 얘도 당연히 merged된 것은 <span style="color:orange">Independence와 Time-Homogeneity</span>를 갖게 된다.

- 그럼, 중요한 Small interval probability를 살펴보자.

  1. 한 슬롯에 도착이 없을 때 : (1 - λ1δ)(1 - λ2δ)
  2. 한 슬롯에 도착이 하나 있을 때 : λ1δ(1 - λ2δ) + (1 - λ1δ)λ2δ
  3. 한 슬롯에 도착이 두개 있을 때 : λ1δ * λ2δ<br>

  ![image](https://user-images.githubusercontent.com/37065429/143732064-2f7b757c-92d4-4315-a96f-3fccc3d47887.png)<br>
  → δ^2 은 negligible.

- 따라서, Merged Process는 <span style="color:orange">PP(λ1 + λ2)</span>이다.

<br>

#### Cont.

- Merged에서 뭔가 더 생각해보자.
- <span style="color:red">Red </span>: PP(λ1), <span style="color:blue">Blue</span> : PP(λ2)
- 그럼, Merged에 누군가 도착했는데, 얘가 Red에서 온 놈일 확률은 어떻게 될까?<br>
  ![스크린샷 2021-11-28 오후 3 36 16](https://user-images.githubusercontent.com/37065429/143732304-5410299e-6acc-4cde-8e30-096531db69f7.png)<br>→ 간단하게 구해질 수 있다.
- 더 나아가서, 하나의 이벤트 Ak를 정의해보자. <br>
  → Ak = {k-th arrival in the merged proc. is <span style="color:red">RED</span>}
  - Ak의 확률은 당연히 앞서 구한 λ1/(λ1 + λ2)이다.
  - 그리고, A1, A2, ... Ak는 모두 <span style="color:orange">독립적이다</span>.<br>
    → Red와 Blue가 독립이니까.
  - 그럼 10번의 도착 중에서 k개의 Red가 있을 확률은?? <br>
    ![스크린샷 2021-11-28 오후 3 38 38](https://user-images.githubusercontent.com/37065429/143732344-ca7f5378-44c2-4362-80fe-4ec2245438f4.png)<br>
    → Binomial의 형태를 갖게 된다!<br>

<br>

## Using Poisson Processes for Intuitive Problem Solving

- 지금까지 배웠던 Split과 Merge가 실제 문제에서 어떻게 사용되는지 확인해보자.

<br>

### Competing Exponential (1)

- 두 개의 독립적인 전구가 있다고 해보자. 그리고 이들의 생명을 Exponential RV로 모델링하자.<br>
  ![스크린샷 2021-11-28 오후 4 02 26](https://user-images.githubusercontent.com/37065429/143732964-0ba97ee0-5760-4b44-b040-8bc7d9a8ad3d.png)

- <span style="color:orange">Question. </span>Distibution of Z = min(Ta, Tb), the first time when a bulb burns out?<br>

  Approach 1. <br>
  ![스크린샷 2021-11-28 오후 4 03 44](https://user-images.githubusercontent.com/37065429/143733009-163c4e6f-b218-4604-bc12-23088333fd90.png)<br>
  → 근데 우리는 Poisson Process를 Merge하는 방법을 알고 있으니까, 그걸 적용해보자. <br>
  Approach 2. <br>
  ![스크린샷 2021-11-28 오후 4 04 24](https://user-images.githubusercontent.com/37065429/143733034-32eb96a6-4ead-4b92-ad4f-2a07c34e4c14.png)<br>→ 훨씬 간결하게 풀 수 있다. (확장된다면) <br>

<br>

### Competing Exponential (2)

- 그럼 확장해보자!
- 세 개의 전구가 있고 각각은 Exp(λ)로 생명이 모델링 되어 있다.
- <span style="color:orange">Question. </span> E[time until the **last** bulb burns out]
- 먼저, 세 개의 Merged Poisson Process를 생각해보자
  1. Time until the first burn-out : T1 = Exp(λ + λ + λ) = Exp(3λ)
  2. Time until the second burn-out : T2 = Exp(λ + λ) = Exp(2λ)
  3. Time until the third burn-out : T3 = Exp(λ)
- 이렇게 만들어버리면 E[time until the **last** bulb burns out] = E[ T1 + T2 + T3 ]가 된다. <br>![image](https://user-images.githubusercontent.com/37065429/143733337-83d6a426-f224-45d1-81de-135538731aa9.png)<br>

<br>

 ### Sum of Independent Poisson RVs

- 두 개의 독립적인 X와 Y RV가 있다고 해보자. 각각은  X ~ Poisson(μ)와 Y ~ Poisson(v).

- <span style="color:orange">Question. </span>Distirution of X + Y? <br>
  → RV의 덧셈은 Convolution을 사용하면 됐었는데, 이건 복잡하고 귀찮다.<br>
  → 그러면, PP(λ) = # of arrivals in 𝛕<span style="color:gray">(N𝛕)</span> ~ Poisson(λ𝛕)라는 것을 기억해서 X 와 Y에서 PP를 추출하자.

- Poisson Process perspective.<br>![스크린샷 2021-11-28 오후 4 25 10](https://user-images.githubusercontent.com/37065429/143733647-17054ab4-b84c-47ae-b7b0-834cbac62fa8.png)<br>→ 그럼 각각은 μ와 v를 시간으로 갖는 PP가 만들어질 것이고 X와 Y는 독립이였기 때문에 disjoint time interval을 갖게 된다.(일종의 연속된 시간으로도 볼 수 있다.)

- 따라서, 질문에 대한 답은 μ와 v의 시간 동안의 # of arrivals of <span style="color:orange">PP(1)</span>이 되고, 따라서 <br>

  → X + Y ~ Poisson(μ + v) <br>

<br>

### Poisson arrivals during Exponential Interval (1)

- <span style="color:orange">Random Time Interval</span> 에서의 PP를 생각해보자.
- PP(λ)와 하나의 독립적인 RV T ~ Exp(v)로 생각해보자.
- <span style="color:orange">Question. </span> Distribution of N_T ?
- 우리가 배웠던 것 중에 Total Probability Theorem을 사용해서 생각해보자. <br>
  ![스크린샷 2021-11-28 오후 4 44 12](https://user-images.githubusercontent.com/37065429/143734119-92ff47af-b297-439c-90e4-0f4698317a4e.png)<Br>→ 흠,,, 근데 무지하게 복잡해보인다.
- 그럼 '진짜' 배웠던 것을 써보자!

<br>

#### Cont.

- 새로운 PP를 도입하자. <br>
  → <span style="color:orange">PP(v)</span>
- 머리속에서 <span style="color:blue">PP(λ)</span>와 <span style="color:orange">PP(v)</span>의 Merge에 대한 상상의 그림을 펼쳐보면, 
  1. Merged Process에서 <span style="color:blue">PP(λ)</span>로 부터 도착들이 합쳐지다가
  2. 어느 순간 <span style="color:orange">PP(v)</span>에서 온 애가 등장할 것이다.
  3. 그럼, 이 순간 전까지의 <span style="color:blue">PP(λ)</span>를 구하면 된다.
- 구해보자. <br>
  ![스크린샷 2021-11-28 오후 4 47 04](https://user-images.githubusercontent.com/37065429/143734196-5b013782-b7fd-40ef-95f3-b838f733298a.png)<br>
  → ㅇㅋ
- K라는 RV를 하나 생성하고 이 친구의 정의를 다음과 같이 내려보자 <br>
  → K : number of total arrivals until we get the first arrival from <span style="color:orange">PP(v)</span>. <br>
  → Then, <span style="color:pink">K ~ Geom(v / (λ + v)) </span><br>
  → 즉, 성공 확률을 v / (λ + v)로 갖는 Geom RV가 된다.
- 이렇게 만들어진 Geom RV의 문제점은 <span style="color:pink">성공까지 횟수를 Count</span>한다는 것이다. <br>→ 그럼 하나 빼자!
- Let <span style="color:pink">L</span> be the number of arrivals from <span style="color:blue">PP(λ)</span> until we get the first arrival from <span style="color:orange">PP(v)</span>.<br>![스크린샷 2021-11-28 오후 4 51 17](https://user-images.githubusercontent.com/37065429/143734299-b7d8142f-68be-4dd4-b445-7ed5a4f65380.png)<br>
  → 5개의 도착이 있으려면, 6개의 시도 중 하나의 성공이 있으면 된다.<br>

<br>

### Approximation of Binomial : Poisson vs. Normal

- 우리가 배웠던 Central Limit Theorem에 따르면, <br>
  ![image](https://user-images.githubusercontent.com/37065429/143734696-b9188056-b829-4e78-adcd-f200dbfa0c81.png)
- n이 무한대로 갈 때를 상정했던 것이니까, Poisson RV도 여기에 숟가락을 얹을 수 있지 않을까?
- 일단 둘의 차이점을 살펴보자.<br>![스크린샷 2021-11-28 오후 5 06 14](https://user-images.githubusercontent.com/37065429/143734716-81110e2a-801b-42f8-acd0-c5907b7c6866.png)<br>
  → 가장 큰 차이점은 Poisson에서는 <span style="color:orange">p도 변하는 값</span>이라는 것이다. <br>→ 따라서, Xi도 이에 따라 영향을 받게 된다.
- 그럼 언제는 Poisson을 써야하고, 언제는 Normal을 써야 할까? <br>
  ![스크린샷 2021-11-28 오후 5 07 26](https://user-images.githubusercontent.com/37065429/143734741-50cf0c35-7d29-4a87-8680-2b7901aa11e3.png)<br>
  → 현장에서는 p와 n이 주어질 때가 많다고 한다. 따라서 어떤 방식을 쓸지 정하는 것이 중요하다. <br>

<br>

## Random Incidence Phenomenon

### Example : Survey of Utilization of Town buses

- "도시의 버스 운용이 얼마나 잘 되고 있는가?"에 대한 설문 조사를 한다고 한다.
- 우리는 여기서 두 가지의 가정을 할 수 있다.
  1. (1) <span style="color:orange">랜덤으로 몇 개의 버스를 선택하고</span>, (2)그 버스의 승객 수를 구한다.
  2. (1)<span style="color:pink">버스 탑승객을 랜덤으로 선택하고</span>, (2) 승객들이 탄 버스를 알아낸 다음에 (3) 그 버스의 이용자 수를 구한다.
- 그럼 이렇게 했을 때, [1]과 [2]의 가정을 통해 구해진 수가 다를까? 아님 차이가 날까? <br><span style="color:gray">→ Sampling method에 관련된 문제이다.</span>
- 이 이후에 나오는 내용은 이를 다루게 된다.

<br>

### Random Incidence Phenomenon 

- 하나의 예제를 들어보자.

- 고정된 시간 t*에 나는 버스 정류장으로 간다.<br>
  *시간은 PP(λ), ~ Exp(λ)로 모델링* 

  1. 정류장에 있는 사람에게 "이전 버스는 언제 왔나요?"라고 물어본다. <br>
     → 답변은 U에 왔어요.
  2. 그리고 기다렸다가 다음 버스가 왔을 때, 나는 시간을 측정한다. <br>
     → 그 시간은 V이다.<br>

  ![스크린샷 2021-11-28 오후 5 46 18](https://user-images.githubusercontent.com/37065429/143735805-dbbedd26-9c83-4d25-b21c-58a5373a32c6.png)

- U와 V 동안의 시간을 L이라고 했을 때, Distribution은 어떻게 구해야할까?<br>
   → *당연히 Exp(λ)아닌교?*

- 아니다. 여기서 중요한 점은 t*는 <span style="color:orange">고정된 시간</span>이다. <span style="color:gray"> *(그래서 incidence)* </span><br>

#### Distribution of L

- 우리는 t*이라는 Additional condition을 주었으니까, 일단은 L을 다음과 같이 표기한다. <br>
  ![스크린샷 2021-11-28 오후 5 49 46](https://user-images.githubusercontent.com/37065429/143735925-85583114-ce7f-47f3-84de-73b12db7c265.png)<br>→ 이제 항별로 따져보자.

  1. V - t* : 내가가 좋아하는 memoryless 덕분에 fresh-start! <br>
     → <span style="color:orange">V - t* ~ Exp(λ)</span>

  2. t* - U : 아~ 이게 애매하다. '이전'의 시간이다... <br>
     → Trick을 사용하자. 시간을 거꾸로 본다면, 결국은 <span style="color:green">이후의 시간</span>이 된다.

     >수학적으로 이를 확인해보자면,
     >
     >P(t* - U > x) = P(no arrivals over[ t* - x , t* ])
     >
     >= e^(-λx) = P(T_inter > x)

     → <span style="color:orange">Thus, t* - U ~ Exp(λ)</span>

- 이걸 종합해보면, L = X1 + X2 이고 X1, X2 ~ Exp(λ)이다. <br>→ <span style="color:orange">Time until we have **two arrivals in PP(λ).**</span><br>
  → <span style="color:orange">Erlang RV</span> with parameter(2, λ) <br>
  ![스크린샷 2021-11-28 오후 5 55 18](https://user-images.githubusercontent.com/37065429/143736107-eba19ac2-34fe-4881-b837-0f8e795005a2.png)

- 이는 Mean 값으로 2/λ를 갖게 되는데, Exp(λ)의 Mean이 1/λ라는 것을 생각하면 **평균보다 큰 interarrival interval**이라는 것을 알 수 있다. <br>

  → <span style="color:blue">An observer who arrives at an arbitary time is more likely to fall in a **large** rather than a **small interarrival interval.**</span><br>→ 따라서, Exp(λ)를 사용할 수 없다.<br>

<br>

### Back to Survey of Utilization of Town Buses.

- 우리는 <span style="color:orange">[1]</span>과 <span style="color:pink">[2]</span>에서 count한 승객의 수가 어떨지를 생각해봤었다.
- 결론은 <span style="color:orange">[1]</span> < <span style="color:pink">[2]</span>이다. <br>→ "Random Incidence Phenomenon"에서 봤듯이, <span style="color:pink">[2]</span>는 승객을 고르고 그 승객이 탄 버스를 알아내는 것이니까 동일한 문제이다.
- 결론의 이유는 다음과 같다. <br>
  → <span style="color:red">More likely to select a bus with a large number of riders than a bus that is near-empty.</span>
