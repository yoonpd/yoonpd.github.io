---
title: "Random Processes (4)"

categories:
  - Probability and Random Variables
toc: true
toc_sticky: true
---

# Random Processes (4)

- 지금까지 Bern, Poisson Process에 대해서 배웠다.
- 또 하나의 중요하고 유명한 Markov Chain을 이번 정리해서 해보겠다.

<br>

## Definition, Transition Probability Matrix, State Transition Diagram

### Recap and Markov Chain

- Discrete한 시간을 가정했을 때, Random Process는 <br>
  → RV X1, X2, ...의 sequence로 볼 수 있다.
- 이 중 가장 간단한 random process는 Bernoulli Process인데, 이는 
  1. Process without memory라고 볼 수 있다. <br>
     ![스크린샷 2021-11-29 오후 2 26 50](https://user-images.githubusercontent.com/37065429/143813611-5a9ccc11-a219-40c8-ae99-696102280c7a.png)
  2. 즉, 이전에 발생한 일들은 현재 일에 전혀 영향을 주지 않는다는 것을 의미한다.
- 그럼, 이것보다 <span style="color:orange">just a little more general</span>한 것은 없을까? <br>
  → 아주 약간의 기억만을 갖고 있는 random process가 이에 해당할 것이다.<br>
  ![스크린샷 2021-11-29 오후 2 28 21](https://user-images.githubusercontent.com/37065429/143813734-2692d0fb-23f0-4fcf-828b-f838d0a93bb7.png)
- 그리해서 나온 것이 오늘 배울 <span style="color:red">Markov Chain</span>이다.

<br>

### Example: Machine Failure, Repair and Replacement

- 예제를 통해서 Markov Chain이 무엇을 의미하는지 간략하게 생각해보자.
- 하나의 기계가 있고, 얘는 열심히 일을 한다. 그리고 이 기계는 다음과 같은 상태 변화에 대환 확률을 가진다.
  1. 현재 일을 하고 있으면, 다음 날 고장날 확률은 b
  2. 현재 일을 하고 있으면, 다음 날도 일을 할 확률은 1-b
  3. 현재 고장났으면, 수리를 받고 일을 할 수 있는 확률은 r
  4. 현재 고장 났으면, 또 고장날 확률은 1-r
- 여기서, 하루 하루의 상태를 표현할 RV Xn 을 하나 선언하자. <br>
  ![스크린샷 2021-11-29 오후 2 49 13](https://user-images.githubusercontent.com/37065429/143815418-9e08dfb0-67b9-463f-9b93-71687dc2c34f.png)
- 이렇게 하면 Conditional을 통해 다음과 같이 또 다음 날에 대한 확률을 구할 수 있다. <br>
  ![스크린샷 2021-11-29 오후 2 51 02](https://user-images.githubusercontent.com/37065429/143815588-c6133236-4318-492b-861c-065581215efc.png)
- 여기서 Markov Chain이 답할 수 있는 것은<br>
  → **What will happen at (n+1)-th day depends only on what happens at n-th day?**<br>

<br>

### Markov Chain: Definition 

- 정의 : X1, X2, ..., Xn, ...이 <span style="color:red">finite</span> sample space S = {1, 2, ..., m}에서의 값을 매핑할 때, S에 포함되는 i와 j 그리고 n >= 0 이면서 다음의 속성을 만족시킨다면 Markov Chain이라고 한다. <br>
  ![스크린샷 2021-11-29 오후 3 05 59](https://user-images.githubusercontent.com/37065429/143816952-694c0775-c27a-4b37-92db-3723b48b28db.png)<br>→ 강의에서는 finite한 sample space만을 고려하지만, 원래는 infinite까지 커버할 수 있다.
  - 또한, Alternate definition via conditional independence. For **any fixed n**, the future of the process after n is <span style="color:red">independent</span> of {X1, X2, ..., Xn-1}, <span style="color:red">given Xn</span>.
- Markov Chain에서의 sample space는 <span style="color:red">state space</span>라고도 한다.
- P(Xn+1 = j &#124; Xn = i)는 n에 무관한 값이다.
- MC를 표현할 새로운 notation은 다음으로 한다.<br>
  ![스크린샷 2021-11-29 오후 3 09 17](https://user-images.githubusercontent.com/37065429/143817265-b7d29aee-6c9d-4706-8a0e-239f89c04106.png)<br>→ n에 independent하다는 것을 강조할 수 있는 아주 훌륭한 notation이다.<br><br>

### Transition Probability Matrix

- 새롭게 정의한 Notation은 n에 independent함을 강조하기에는 좋지만 쓰기에는 좀 별로다.<br>
  → p1234면 12와 34? 123과 4? 흑흑<br>
  ![스크린샷 2021-11-29 오후 3 18 01](https://user-images.githubusercontent.com/37065429/143818119-6463d2f6-32da-4a6b-8197-bf10f030ede8.png)
- 그래서 사람들은 매트릭스로 만드는 방법을 생각해냈다. <br>
  ![스크린샷 2021-11-29 오후 3 18 33](https://user-images.githubusercontent.com/37065429/143818183-e59d2170-2f71-4b80-ae9d-b3d707d43856.png)
  - 이것이 <span style="color:red">Transition Probability Matrix</span>이다.<br>
    ![스크린샷 2021-11-29 오후 3 19 12](https://user-images.githubusercontent.com/37065429/143818236-d9804e9e-18d9-433d-af91-ea4a3338bbfb.png)
  - 여기서 하나의 중요한 특성이 있다.<br>
    → "row"를 고정하면, "column"의 합은 1이 된다는 것이다. <br>
    → 즉, 오늘이 고정되면 내일에 있을 일은 확률이 된다는 것이다.<br>

<br>

### State Transition Diagram

- 또 다른 표현 방법이다.
- State Transition Diagram<br>
  ![스크린샷 2021-11-29 오후 3 23 35](https://user-images.githubusercontent.com/37065429/143818665-b76395b4-0369-404e-bace-b37ed6e07fc1.png)
- 여기서는 <span style="color:red">Out-going</span>의 총 합은 1이 된다.

<br>

### Spider-Fly Example

- 한 파리가 1, 2, 3, 4 position에서 하나씩 옮겨가며 날라다닌다고 하자.<br>
  🪰는 다음과 같은 확률로 움직인다.
  1. 왼쪽은 0.3
  2. 오른쪽은 0.3
  3. 가만히 있을 경우는 0.4
- 여기서, 1번과 4번에는 거미🕷가 숨어있어서 파리가 그 위치로 가면 잡아 먹히게 된다.
- Xn을 <span style="color:blue">position of the fly</span>라고 한다면, State transition diagram과 Transition probability matrix는 어떻게 될까?<br>
  ![스크린샷 2021-11-29 오후 4 20 59](https://user-images.githubusercontent.com/37065429/143824653-71f26181-cab9-4c7a-bf57-70b70a95c933.png)<br>

<br>

#### Modified Spider-fly

- 약간의 수정을 가해서 Markov Chain에서 무엇이 중요한지 확인해보자.
- 이전에 사용했던 Xn이 아닌, Yn이라는 새로운 RV로 modeling을 해보자.<br>
  ![스크린샷 2021-11-29 오후 4 23 01](https://user-images.githubusercontent.com/37065429/143824874-751e85b2-b56f-409f-90a9-c81535cdc763.png)
- 흠,,그러면 Yn : n >=0 일 때, 이것이 Markov chain이라고 할 수 있을까? <br>
  → <span style="color:red">Markov property</span>를 사용해서 생각해보자. 즉, given Y1, Y2 ㅛ Y0 ? <br>
  ![스크린샷 2021-11-29 오후 4 24 37](https://user-images.githubusercontent.com/37065429/143825048-395a6f99-9ef8-4030-8419-eb27fe8803e1.png)<br>
  → 우리가 배운 property를 생각해보면 두 개의 값은 같아야 한다. 내일을 알고 싶은데 어제는 필요 없으니까.
- 먼저, 좌항<br>
  ![스크린샷 2021-11-29 오후 4 26 03](https://user-images.githubusercontent.com/37065429/143825271-070992ce-fcad-44ab-9099-384d019b5d8e.png)<br>→ Y0 = 1이고, Y1 = 2가 되기 위해서는 Y0에서 위치는 3일 수 밖에 없다.
- 그리고 우항<br>
  ![스크린샷 2021-11-29 오후 4 27 08](https://user-images.githubusercontent.com/37065429/143825430-e0349ddc-517c-461f-952a-0126da250c3e.png)<br>
  → 같지 않다!
- 따라서, Yn : n >= 0는 Markov chain이 아니고, Markov chain을 위해선 modeling 또한 중요한 요소임을 알 수 있다.

<br>

### COVID-19 Infection Example

- In discrete time slots, N persons.
- Each person is in one of the three conditions : <br>
  (F) : infectious <br>
  (I) : Purely infected <br>
  (N) : Noninfected
- **Infection model.**<br>
  ![스크린샷 2021-11-29 오후 5 43 34](https://user-images.githubusercontent.com/37065429/143835296-f67ce476-3914-43a6-8500-2c04be52bf3c.png)<br>→ 한 사람이 N인 상태로 계속해서 있다가 어느 날 감염자를 만나게 되면 <br>
  → 해당 Time slot은 F로 변경. 단 하나의 time slot만이 해당된다. 그리고 이 때, 다른 이를 감염시킬 수 있다. <br>
  → 이후, 격리된다.
- **Contact model.** <br>![스크린샷 2021-11-29 오후 5 46 31](https://user-images.githubusercontent.com/37065429/143835734-12a58190-c8e7-4e41-9968-d79ed3209744.png)
- 자 그러면, 모델링을 한 번 해보자잇! <br>
  <span style="color:red">Xn</span> : # of infectious (F) persons at the beginning of time slot n. <br>
  <span style="color:blue">Yn</span> : # of noninflected (N) persons at the beginning of time slot n.
- <span style="color:orange">Q1. </span>Xn : n >= 0 가 Markov Chain??? <br>
  → <span style="color:orange">Nope.</span><br>
  ![스크린샷 2021-11-29 오후 5 48 59](https://user-images.githubusercontent.com/37065429/143836106-63fe8c5f-ca71-4d34-b0d4-c95c401713a6.png)<br>→ Xn-1 자체에서 얻어 오는 것이 아닌 Yn-1로부터 얻어지게 된다.
- <span style="color:orange">Q2. </span>Yn : n >= 0 가 Markov Chain??? <br>
  → <span style="color:orange">Nope.</span><br>
  ![스크린샷 2021-11-29 오후 5 50 06](https://user-images.githubusercontent.com/37065429/143836254-431a82c7-696a-4826-87be-84198d7013f1.png)<br>
  → Xn에서 설명했던 것과 동일한 이유이다.
- <span style="color:orange">Q3. </span>Zn = (Xn, Yn) : n >= 0 가 Markov Chain??? <br>
  → <span style="color:orange">Yes!</span><br>
  → (Xn, Yn) <span style="color:orange">only depends on (Xn-1, Yn-1)</span>.<br><br>

## n-Step Transition Probability

### Probability of a Sample Path

- <span style="color:red">Q. </span>What is the probability of a <span style="color:orange">sample path</span> in a Markov chain with <span style="color:orange">the transition probability matrix P = [pij]?</span><br>→ 어떤 경로가 주어졌을 때, Markov chain에 의해서 이 경로로 올 확률은 어떻게 되는 것인가에 대한 질문이다.
- 어떤 경로가 다음과 같이 주어졌다고 하자.<br>
  ![스크린샷 2021-12-01 오후 2 00 38](https://user-images.githubusercontent.com/37065429/144174786-6bf4f254-38c9-4fb6-b0bf-3fd42668ff72.png)<br>
  → 이를 Conditional probability로 해석하면, P(A &#124; B)∙P(B)로 변경할 수 있다. <br>
  ![스크린샷 2021-12-01 오후 2 01 42](https://user-images.githubusercontent.com/37065429/144174888-63199ab1-4b9b-46a5-bbec-c4f3354a463e.png)<br>→ 하지만 Markov chain이라고 하면, <span style="color:orange">n은 n-1과만 관련</span>되기 때문에, <span style="color:red">P(A &#124; B)는 p(i_n-1)(i_n)</span>로 바꿀 수 있다. <br>→ 이후, P(B)의 항을 recursive하게 이어나갈 수 있게 되어 마지막 항의 값이 나오게 된다.
- Spider-fly 예제에서 다음과 같은 경로가 주어졌을 때의 확률<span style="color:gray">(Transition probability)</span>을 구해보자.<br>
  ![스크린샷 2021-12-01 오후 2 04 29](https://user-images.githubusercontent.com/37065429/144175136-626da4dc-a502-4882-be7d-0d6bd8aee480.png)<br>→ 👍<br><br>

### Prabability after n steps

- <span style="color:pink">Q. </span>What is the probability that my state is j, after n steps, starting from i?<br>
  → 특정 구간에 해당하는 확률은 앞서 나온 내용으로 구할 수 있다. <br>
  → <span style="color:red">"i"</span>에서 시작해서 <span style="color:orange">n</span>번의 스텝 이후에 <span style="color:blue">"j"</span>로 끝나는 경로의 확률은 어떻게 구할 수 있을까?
- 먼저, notation을 하나 정하자.<br>
  ![스크린샷 2021-12-01 오후 2 15 52](https://user-images.githubusercontent.com/37065429/144176064-cc387bbe-d326-4f48-a8a5-8e282f148443.png)<br>
  → n=1일 때는 당연히 다음 단계이기 때문에 transition probability matrix를 통해 구할 수 있다.
- 그럼, 공식으로 생각해보자.<br>![스크린샷 2021-12-01 오후 2 17 08](https://user-images.githubusercontent.com/37065429/144176172-29efe8a6-8b10-4ea0-9ead-a320f6c51906.png)<br>
  → 처음 상태가 i이고 n번의 스텝 이후에 j의 상태로 끝나는 것은 conditional로 표현할 수 있고, <br>
  → k가 모든 상태를 포함한다면 conditional과 마지막 항은 동일하다고 볼 수 있다.<br>![스크린샷 2021-12-01 오후 2 19 25](https://user-images.githubusercontent.com/37065429/144176371-ba90fbed-3701-4e08-bf44-d472aa2a0baa.png)<br>
  → P(A, C &#124; B) = P(C &#124; B)P(A &#124; C, B)공식을 통해서 풀어낼 수 있다.<br>
  → 마지막 항에서 n과 n-1만 신경쓰면 되니까 X0=i를 없앨 수 있고<br>
  ![스크린샷 2021-12-01 오후 2 20 23](https://user-images.githubusercontent.com/37065429/144176444-e22a1596-cf62-439b-ad3e-cc671e370501.png)<br>
  → 마지막으로 다음과 같은 식이 도출될 수 있다.
- 따라서, r(ij)(n)은 재귀적으로 풀 수 있다는 것을 확인할 수 있고, 이것을 <span style="color:blue">Chapman-Kolmogorov equation</span>이라고 한다.

<br>

### More Generalized Chapman-Kolmogorov Equation

- Chapman-Kolmogorov Equation이 더 일반적인 상황에서 어떻게 적용되는지 확인해보자.<br>
  → n-step에서 (n+l)-step인 상황을 생각해보자.<br>
  ![스크린샷 2021-12-01 오후 3 02 32](https://user-images.githubusercontent.com/37065429/144180498-0c39da2c-8e26-480e-9e36-f1e97ce20127.png)<br>→ 앞에서 증명한 방식을 사용해서 똑같이 할 수 있다.
- Notation도 새롭게 하나 추가하자.<br>
  ![스크린샷 2021-12-01 오후 3 03 27](https://user-images.githubusercontent.com/37065429/144180590-fc1fba7a-81d2-41e2-a7f9-0971fc0d0b74.png)<br>→ 이는 특정한 값이 아닌 <span style="color:pink">Matrix</span>이다.
- 과연 Matrix로 선언한 것이 어디에 좋은지 간단하게 알아보자.<br>
  ![스크린샷 2021-12-01 오후 3 12 32](https://user-images.githubusercontent.com/37065429/144181536-37862d9f-015f-4ea5-be16-1a8caa2b0d2c.png)<br>
  → In other words, n-step transition probability matrix is just a <span style="color:blue">n-time multiplication</span> of the <span style="color:red">transition probability matrix P</span>.<br>

<br>

#### Example: Urn with Two balls

- 한 항아리는 항상 2개의 공을 갖고 있고, 이 공의 색은 <span style="color:red">Red</span> or <span style="color:blue">Blue</span>

- 각 단계에서, 항아리에서 랜덤으로 하나의 공을 선택하고, 랜덤으로 새로운 공을 채워 넣는다.

- 채워 넣을 때,

  1. 뽑은 공과 같은 색이 들어갈 확률은 0.8
  2. 뽑은 공과 반대되는 색이 들어갈 확률은 0.2이다.<br>

  <span style="color:gray">이렇게 되면 공을 뽑는 것은 오직 이전 상태하고만 연관이 된다.</span>

- 처음에 항아리는 2개의 <span style="color:red">Red</span> 공이 들어가있다.

- <span style="color:orange">Q. </span>Find the probability <span style="color:red">the fifth ball</span> selected is red.

- <span style="color:orange">Solution. </span><br>
  → Xn을 n-stage 이후에 남아 있는 빨간 공의 색으로 해보자. <br>
  → 여기서, stage space, S = {0, 1, 2}가 된다.<br>
  ![스크린샷 2021-12-01 오후 3 32 15](https://user-images.githubusercontent.com/37065429/144183903-33e21032-dac9-4802-bbf4-623aca05d8a0.png)<br>
  → 그러면, Transition Probability Matrix는 다음과 같이 생성될 것이다. <br>
  → Let A = fifth ball is red, 그럼 매우매우 간단하게 앞서 배운 내용으로 문제를 풀 수 있다.<br>
  ![스크린샷 2021-12-01 오후 3 33 42](https://user-images.githubusercontent.com/37065429/144184072-b7b9a594-78ae-46d1-bef2-f79860a52554.png)<br>
  → 4 단계 이후에 남아있는 공이 2개라면 그 중 뽑을 확률은 1이므로 1*r(2, 2)(4)<br>

  → 4 단계 이후에 남아있는 공이 1개라면 그 중 뽑을 확률은 1/2이므로 0.5*ㄱ(2, 1)(4)<br>

- <span style="color:orange">Another Solution. </span><br>
  ![스크린샷 2021-12-01 오후 3 35 30](https://user-images.githubusercontent.com/37065429/144184245-fd64af2b-5c11-4bba-b58c-da35e6fd4db5.png)<br>

<br>
