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

## Classification of States

### Different States and Classes?

![스크린샷 2021-12-01 오후 3 48 42](https://user-images.githubusercontent.com/37065429/144185724-baa30963-82b3-4429-8f00-271aa9146812.png)<br>
→ 다음과 같은 State Transition Diagram이 시사하는 메시지를 생각해보자.<br>

1. Multiple Classes may exist.
   - State 3 <span style="color:green">can only be reached from 3</span>.
   - State 1 and 2 <span style="color:green">can reach each other</span> but no other state.
   - State 4, 5 and 6 <span style="color:green">all reach each other</span>.
   - All states can <span style="color:green">be divided into three classes</span> : {1, 2}, {3}, {4, 5, 6}
2. Some states are visited <span style="color:lightblue">infinite times</span>, but some states are not.
   - If I start from stage 1, <span style="color:lightblue">visit 1 infinite times</span>.
   - If I start from stage 3, <span style="color:lightblue">visit 3 only finite times</span>. (move to other classes and don't return)
3. States in the same class <span style="color:orange">share some properties</span>.
   - State 2 will <span style="color:orange">share the above properties with stage 1</span>. (Self-visit infinite times)

<br>

### Classification of States

1. <span style="color:red">Accesible</span>
   - **Definition** : State j is <span style="color:red">accessible</span> from state i, if for some n, r(ij)(n) > 0 <br>
     → denoted by ![스크린샷 2021-12-01 오후 4 19 28](https://user-images.githubusercontent.com/37065429/144189255-96c6b73b-aed4-4036-820e-8e22adbf3127.png)
2. <span style="color:blue">Communicate</span>
   - **Definition** : If i is <span style="color:red">accessible</span> from j and j is <span style="color:red">accessible</span> from i, we say that i <span style="color:blue">communicates</span> with j.<br>
     → denoted by ![스크린샷 2021-12-01 오후 4 21 15](https://user-images.githubusercontent.com/37065429/144189471-ddd15f71-90be-4f9a-b258-55e1c74df0fc.png)
3. <span style="color:green">Recurrent And Trasient</span>
   - **Definition** : Let A(i) = {state <span style="color:red">accessible</span> from i}, State i is <span style="color:green">recurrent</span>, if j ∈ A(i), i is also <span style="color:red">accessible</span> from j.<br>
     → If A state that is not <span style="color:green">recurrent</span> is <span style="color:green">transient</span>.
   - <span style="color:gray">어렵다!</span> <span style="color:red">i로부터</span> 어떻게든 연결되어 있는 states(j)들이 i와 communicate할 때
   - 어떤 state가 <span style="color:green">Recurrent</span> 속성을 갖고 있으면, 그 state에서 출발을 하면 <span style="color:orange">언제가는</span> 다시 돌아오게 된다.

<br>

#### Cont.

- Recurrent 속성에 대해서 더 알아보자.

- A set of recurrent states which <span style="color:blue">communicate</span> with each other in a class.<br>![스크린샷 2021-12-01 오후 4 44 23](https://user-images.githubusercontent.com/37065429/144192464-d5459583-dd80-4d06-9222-13b88ec5caa2.png)<br>→ 한 집합 내에 모든 state들이 recurrent할 때, 서로 간에는 <span style="color:blue">communicate</span>할 수 있다.

- Markov chain decomposition

  - A MC can be decomposed into <span style="color:orange">one or more recurrent classes</span>, plus possibly <span style="color:orange">some transient states</span>.

  - A recurrent state is accessible from all states in its class.<br>
    ![스크린샷 2021-12-01 오후 4 44 23](https://user-images.githubusercontent.com/37065429/144192464-d5459583-dd80-4d06-9222-13b88ec5caa2.png)

  - A recurrent state is not accessible from recurrent states in other classes.<br>
    ![스크린샷 2021-12-01 오후 4 47 28](https://user-images.githubusercontent.com/37065429/144192877-497ae9c8-505d-4484-bf29-e2d62e8f58a5.png)

  - A transient state is not accessible from any recurrent state. <br>
    → 위 사진과 같다.

  - At least one, possibly more, recurrent states are accessible from a given transient state.<br>

    → <span style="color:green">Transient</span>는 쉽게 생각해서 나가는 것은 마음대로지만 들어오는게 힘들다.

- The MC with only <span style="color:orange">a single recurrent class</span> is said to be <span style="color:red">irreducible</span>.<br>
  → 앞에 나온 것을 응용하면, All states in a single recurrent class can communicate with each other.

<br>

### Periodicity

- <span style="color:red">Definition. </span>**A recurrent class** is said to be <span style="color:red">periodic</span>, if its states can be grouped in disjoint subset S1, ..., Sd (d > 1) so that **all transitions from Sk** lead to **Sk+1**(or to S1 if k = d). <br>
  → A recurrent class that is not periodic <span style="color:gray">(i.e., d=1)</span> is said to be <span style="color:red">aperiodic</span>.
- 내가 그린 이쁜 그림으로 이해해보자.<br>
  ![IMG_CCFC587F4F1C-1](https://user-images.githubusercontent.com/37065429/144196650-fa939c26-da17-4781-83b6-e84a6aa6ee3b.jpeg)<br>*아이패드를 샀다*<br>
  → 왼쪽은 하나의 recurrent class이다. <br>
  → 이를 우측과 같이 세 개(d=3)의 그룹으로 나눌 수 있는데, 이 그룹은 {1, 2}→{3, 4, 5}→{6}→{1,2} 이런 식으로만 움직일 수 있다.
- 이것의 속성 중 하나는 n이 d로 나눠질 수 없다면 r(ii)(n) = 0가 된다는 것이다.<br>
  → 위 그림에서, <br>
  → r(33)(0) = 0, r(33)(1) = 0, r(33)(3) > 0, r(33)(127) > 0
- 하지만, 이러한 periodic 속성이 해당 클래스에 존재하는지를 확인하는 것은 때로는 매우 어려울 수도 있다.<br>
  → But, 야매로 <span style="color:blue">self-transition</span>이 존재한다면 <span style="color:red">aperiodic</span>이라는 것은 쉽게 알 수 있다.<br><br>

## Steady-state Behaviors and Stationary Distribution

- Markov chain을 오랜 기간 진행하다보면 steady한 상태의 행동을 확인할 수 있다.

<br>

### n-step transition prob. : r(ij)(n) for large n

- 그림을 통해 n이 무수히 커질 때, Markov chain이 어떻게 되는지 확인해보자.<br>
  ![스크린샷 2021-12-01 오후 5 48 03](https://user-images.githubusercontent.com/37065429/144201657-45430b34-079d-4678-9067-dedfd02f639d.png)<br>
   → 출발 지점에 초점을 맞추는지/아닌지에 따른 Markov chain의 행동이다.
- 여기서, 우리는 "도착 지점"에 초점을 맞춰보자

<br>

### Steady-state behavior : Why Important?

- 새로운 Notation을 적용해서, <br>
  ![IMG_2D42F9E7D28F-1](https://user-images.githubusercontent.com/37065429/144202315-aa5679d6-38ae-4be6-8482-f864e8687284.jpeg)<br>→ 다음과 같이 해보자. 이를 stationary probability라고 부른다.
- 이를 사용한다면, MC를 오~랜 시간 진행시켰을 때, MC가 어떠한 최종 상태에 이르는 확률을 알 수 있다.
- 직관적으로 Machine 예제를 또 가져와보자.<br>
  ![스크린샷 2021-12-01 오후 5 54 03](https://user-images.githubusercontent.com/37065429/144202579-d682b976-8055-4c4c-9b54-ff8c4dba8388.png)<br>
  → a+b = 1이라는 것은 명백하고, <br>
  → 기계를 엄청나게 오래 동작시켰을 때, 얘가 계속해서 일을 잘 할 수 있는지, 아니면 죽는지를 확률을 통해 알 수 있게 된다.<br>
  <br>

### Steady-state Behavior : Convergence Condition

- 이렇게 좋은 것을 그럼 언제만 사용할 수 있을까?
  1. <span style="color:red">A single recurrent class</span>
  2. <span style="color:red">Aperiodic</span>
- 왜 두 개의 조건을 만족해야하는지 직관적으로만 확인해보자.
  1. 여러 개의 recurrent class가 존재한다고 하면, 하나의 recurrent class에서는 다른 class로 넘어갈 수 없다.<br>
     → <span style="color:orange">즉, 시작 지점을 고려하지 않을 수 없다.</span>
  2. Divergent behavior for periodic recurrent classes.<br>
     → 간단하게, d=2일 때를 생각해보자.<br>
     → r(ab)(1) = 0, r(ab)(2) > 0, r(ab)(3) = 0<br>
     → 수렴 형태가 아닌 divergent한 형태를 보이게 될 것이다.<br>

<br>

### Steady-state Convergence Theorem

- 그럼 이렇게 좋은 것을 어떻게 계산해야될까?<br>
  <span style="color:gray">→ Brute Force!!!!!</span>
- 다 해보는 것은 매우 좋지 않고 비용만 드는 문제다.
- 따라서, 두 개의 방정식을 통해 푸는 방법을 알아보자.
  1. Balance Equation<br>
     ![스크린샷 2021-12-01 오후 6 10 07](https://user-images.githubusercontent.com/37065429/144205243-02d53ff1-9bdf-4029-9e41-a3620e1e17c6.png)<br>
     → j = 1, 2, ... m
  2. Normalization Equation<br>
     ![스크린샷 2021-12-01 오후 6 10 25](https://user-images.githubusercontent.com/37065429/144205278-039fbea2-f3f6-40ff-9561-18f44008c84d.png)<br>
     → 결국, 확률 값이기 때문에 이들의 합은 1이 된다.
- Balance Eqn. + Normalization Eqn.을 같이 사용한다면 Linear equations을 푸는 것이기 때문에 steady-state probabiliteis의 계산이 가능하다.

<br>

#### Long-term Frequency Interpretation

- 직관적으로 Balance equation을 이해해보자.
- 지금까지 배운 확률이라는 개념은 다음과 같다. <br>
  → Probability is interpreted as the <span style="color:red">relative frequencies</span> out of many independent trials.
- 이러한 개념을 convergence에 적용해보면, <br>
  ![스크린샷 2021-12-01 오후 6 20 53](https://user-images.githubusercontent.com/37065429/144206918-a4e5fd5d-58d3-4076-9d9e-0677f1a306cf.png)
- 즉, πj는 state j로의 <span style="color:red">expected fraction of time</span>이라고 볼 수 있다.<br>
  ![스크린샷 2021-12-01 오후 6 21 59](https://user-images.githubusercontent.com/37065429/144207120-0d46b36c-b3fe-4449-a677-6fe3c823f53f.png)
- 그럼, 최종적으로 balance equation을 해석해보자.<br>
  ![스크린샷 2021-12-01 오후 6 22 28](https://user-images.githubusercontent.com/37065429/144207200-9289f601-f15e-4892-9d3c-1a9c8f2b7e79.png)<br>

<br>

#### Example.

- Transition Probability Matrix가 다음과 같이 주어졌을 때, π1과 π2를 구해보자!<br>
  ![스크린샷 2021-12-01 오후 6 23 18](https://user-images.githubusercontent.com/37065429/144207324-55b9861c-fd5a-41f0-9d47-ec36e662df23.png)<br>
  ![IMG_2CAF36226429-1](https://user-images.githubusercontent.com/37065429/144207954-4b2ae1d5-97e0-4836-b88d-374f91a01779.jpeg)<br>
  <br>

### Stationary Distribution

- πj는 <span style="color:red">stationary distribution</span>로 불리기도 한다. 왜일까?<br>
  → <span style="color:gray">Stationary : not moving or not intended to be moved.</span>
  1. Distribution으로 부를 수 있는가?<br>![image](https://user-images.githubusercontent.com/37065429/144337560-147a3a6c-7348-439c-b0f0-f3c3b2f2a434.png)
  2. Stationary라고 부를 수 있는가?<br>
     ![image](https://user-images.githubusercontent.com/37065429/144337636-4d05fafb-81c6-4b7b-81e7-0eb0961e3982.png)<br>
     → 원래는 출발점을 고려하지 않았지만, <span style="color:red">πj에 따라서</span> 출발 지점을 선택 했을 때는 위와 같은 결과가 나온다.<br><span style="color:gray">→ 나의 생각으로는 Long-term frequency interpretation에서 나온 것처럼 애초에 πj라는 것이 모든 경우를 포함하기 때문...?</span> 
- 확장해서 다음과 같은 것을 알 수 있다.
  1. ![image](https://user-images.githubusercontent.com/37065429/144338002-c426b688-f7d7-4a17-b415-fcca153e92bf.png)
  2. ![image](https://user-images.githubusercontent.com/37065429/144338038-4f2b3792-7d77-41a8-9c69-32f01ef08737.png)
- 그럼 이 좋은게 항상 모든 것에 적용이 가능할까?<br>
  → 좋은 것은 그렇지 않다.
  1. Only single recurrent class
  2. Aperiodic

<br>

#### Example.

- 한 사람은 우산을 두 개 가지고 있고, 집에서 사무실로 또 그 반대로 우산을 가지고 다닌다.

- 만약 비가 내리고, 우산이 있다면 그 우산을 갖고 가지만, 비가 오지 않으면 우산을 그냥 내비 두고 간다.

  1. 집 : 2 / 사무실 : 0<br>
     → 출근(🌧) : 집 : 1 / 사무실 : 1<br>
     → 출근(☀️) : 집 : 2 / 사무실 : 0<br>→ <span style="color:blue">퇴근(🌧) : 집 : 2 / 사무실 : 0</span><br>
     → 퇴근(☀️) : 집 : 2 / 사무실 : 0<br>
  2. 집 : 1 / 사무실 : 1<br>
     → 출근(🌧) : 집 : 0 / 사무실 : 2<br>
     → 출근(☀️) : 집 : 1 / 사무실 : 1<br>→ 퇴근(🌧) : 집 : 2 / 사무실 : 0<br>
     → 퇴근(☀️) : 집 : 1 / 사무실 : 1<br>
  3.  집 : 0 / 사무실 : 2<br>
     → <span style="color:blue">출근(🌧) : 집 : 0 / 사무실 : 2</span><br>
     → 출근(☀️) : 집 : 0 / 사무실 : 2<br>→ 퇴근(🌧) : 집 : 1 / 사무실 : 1<br>
     → 퇴근(☀️) : 집 : 0 / 사무실 : 2<br>

- 비가 올 확률은 p이다.

- <span style="color:red">Q. </span>What is the steady-state probability that she gets wet during a commute?

  - State space = {0, 1, 2} : i umbrellas available in location.<br>
    → 즉, 상태의 변화는 출근 또는 퇴근이 된다.
  - Transition diagram<br>
    ![image](https://user-images.githubusercontent.com/37065429/144340096-b03c6892-67f9-473d-ada6-0ec0ab5c3b49.png)<br>
    → 상태의 변화는 출근 또는 퇴근임을 기억하자. <br>
    → 예시로, 0에서 2로 가는 것은 출근 때 집에 0개이지만 사무실에는 2개가 있으니 1의 확률이 된다.
  - 이는 <span style="color:red">single recurrent class</span>이고 <span style="color:red">aperiodc(self-transition)</span>이므로 우리가 배운 내용을 모두 적용할 수 있다.
  - Using Balance and Normalization equation.<br>
    ![image](https://user-images.githubusercontent.com/37065429/144340341-ccf757ca-cdad-4370-be4f-4ca01151a669.png)<br>

  <br>



## Birth-Death Process

### Example 1. Random Walk with Reflecting Barriers

- 한 사람이 직선의 길을 걷고 있다고 해보자.
- 그리고 이 사람은 각 slot time에서 오른쪽으로 갈 확률은 b, 왼쪽으로 갈 확률은 1-b라고 해보자.
- 직선의 길이는 m이고 직선에서의 위치는 1, 2, ..., m으로 표현하고 그 중하나의 위치에서 시작한다.
- <span style="color:orange">이 때, 0의 위치(1의 위치에서 왼쪽으로 또는 m의 위치에서 오른쪽)에 도착했을 때, 즉시 방향 전환하기 직전의 위치로 가게 된다.</span>
- <span style="color:red">Q. </span>이 때의 Transition Diagram은?<br>
  ![image](https://user-images.githubusercontent.com/37065429/144341872-7ac7be0a-0ca2-497e-87df-4a1410e3ca0c.png)<br>
  <br>

### Example 2. Queueing

- 손님이 슈퍼 마켓에서 계산을 위해 카운터로 간다.
- 카운터에 줄을 설 수 있는 최대 인원 수는 m이고, 앞선 손님이 있고 m이 아니라면 기다리게 된다.
- 이러한 condition에서는 3가지의 상황이 발생할 수 있다.
  1. 새로운 손님이 b의 확률로 도착
  2. 이미 줄에 있던 사람이 d의 확률로 떠남(계산 또는 다른 물건을 가지러)
  3. 줄에 1-b-d의 확률로 그 누구도 새로 오지 않고 떠나지 않음

- <span style="color:red">Q. </span>이 때의 Transition Diagram은?<br>![image](https://user-images.githubusercontent.com/37065429/144342198-9f47846b-3269-4b65-bfc1-f38f17a4483a.png)<br>

<br>

### Birth-Death Process

- 앞서 본 두 예제의 공통점이 무엇일까?<br>
  → 바로 근처의 이웃과만 transition이 발생한다는 것이다.

- 이러한 Markov chain을 <span style="color:red">Birth-death process</span>라고 부른다.

  1. Linearly arranged
  2. Transition only occur to a neighboring state

- State Diagram of Birth-Death Process<br>

  ![스크린샷 2021-12-02 오후 2 49 18](https://user-images.githubusercontent.com/37065429/144365269-6b2c175c-e1c9-4acd-bba0-53b88aa7c659.png)<br>
  → 앞서 다룬, Random Walk와 Queueing은 Birth-Death Process의 특이 케이스 중 하나이다.

- Balance Equation.

  - at state 0.<br>![스크린샷 2021-12-02 오후 2 56 04](https://user-images.githubusercontent.com/37065429/144365966-60f94c66-2f52-4025-aa64-197a2002abb8.png)

  - at state 1.<br>
    ![스크린샷 2021-12-02 오후 2 56 24](https://user-images.githubusercontent.com/37065429/144365999-ec192690-41eb-4c10-abd5-49dcd903cdfe.png)

  - General.<br>
    ![스크린샷 2021-12-02 오후 2 56 44](https://user-images.githubusercontent.com/37065429/144366032-e3861985-5cba-4d04-8c7c-40a20a514642.png)

  - 이 식으로부터 우리가 유추할 수 있는 것은 <span style="color:red">state n의 관점에서</span> <span style="color:orange">dn, bn의 frequency</span>는 동일하다는 것이다.<br>
    → 따라서, Birth-Death Process에서는 이를 <span style="color:red">**Local balance equation**</span>이라고 한다.

  - 특이한 Balance Eqn.을 갖고 있기 때문에 stationary probability를 구하는 것도 간단하게 할 수 있다.<br>![스크린샷 2021-12-02 오후 3 02 12](https://user-images.githubusercontent.com/37065429/144366601-dc98f0b9-ef94-4520-8783-b6afaa322267.png)<br>

    → 추가로, 당연히 ![스크린샷 2021-12-02 오후 3 02 39](https://user-images.githubusercontent.com/37065429/144366654-dfcdd221-1861-4d20-8e51-77468464fb8b.png)<br>

  <br>

## Transient behaviors

### Motivating Questions

- 이 전까지는 Steady-state behavior에 대해서 공부를 했었다. <br>
  → 하나의 recurrent class 🏝
- 이제는 더 확장된, 그리고 일반적인 MC에 대해서 생각해보자. <br>
  → A MC with <span style="color:orange">multiple recurrent class and a set of transient states T</span>.
- 여기서 그럼 하나의 가정을 진행해야 한다. <br>
  → 이 MC가 어디서 시작해야될까?
  1. Recurrent class<br>
     → 한 번 빠지면 헤어나올 수 없다. (탈모)
  2. <span style="color:orange">Transient state </span><br>
     → 그러면 언젠가는 Recurrent class로 진입하게 될 것이고, 거기서 재밌게 놀 것이다.
- 그래서 우리는 일반적인 MC에서 이러한 질문을 던질 수 있다.<br>
  → <span style="color:red">Q. </span><span style="color:orange">Transient Behavior</span> : What is the <span style="color:orange">first recurrent state to be entered</span> as well as <span style="color:orange">time until this happens</span>?<br>

<br>

### Special case : Every Recurrent State is Absorbing

- General한 형태를 다루기 전에, 특이한 케이스를 하나 살펴보자.<br>
  →<span style="color:blue"> Every recurrent state is absorbing</span>

- <span style="color:red">Definition. </span>A state k is <span style="color:blue">absorbing</span>, if p(kk) = 1, and pky = 0 for all j != k.<br>
  ![스크린샷 2021-12-02 오후 3 45 39](https://user-images.githubusercontent.com/37065429/144371706-0335aa96-5aed-446b-a02d-26185c2421dc.png)<br>
  → 여기서는 1과 6이 해당된다.

- For a given absorbing state s, the probability ai = ai(s) of reaching s, starting from a state i?<br>
  → i : starting point<br>
  → s : End point, absorbing state<br>

- S = 6으로 고정시켰을 때, <br>
  ![스크린샷 2021-12-02 오후 3 50 50](https://user-images.githubusercontent.com/37065429/144372347-a13c9bf1-e1f1-45a1-814f-43276d09eccb.png)<br>
   → <span style="color:gray">(s는 생략)</span> 위 그림에서 각각의 ai의 확률은 위와 같다.<br>
  ![스크린샷 2021-12-02 오후 3 53 08](https://user-images.githubusercontent.com/37065429/144372609-c98c278f-4427-4112-a1c2-f3455ac31010.png)<br>→ a2(1) = 1 / a2(6)가 된다. 1로 가려면 2를 무조건 거쳐야 하고, <br>

  → 6이 absorbing한 것처럼 1도 absorbing하기 때문.<br>

<br>

### For General MCs

- 다음 그림을 봐 보자.<br>![IMG_1ABD6BCF9224-1](https://user-images.githubusercontent.com/37065429/144379214-b2866610-9d17-4b99-b38e-a76180bab6a9.jpeg)

  1. {1}과 {4, 5}는 Recurrent class로서 한 번 들어오면 다시는 나갈 수 없는 구조이다.

  2. 그럼 여기서 질문.<br>

     → Probability that the state eventually enters the recurrent class {4, 5}?

- {4, 5}는 들어가는 순간 나올 수 없기 때문에, 단순히 그 '섬'으로 들어갈 확률을 구하는 문제이다.

- 그럼, {4, 5}를 하나의 섬, 즉 {6}으로 치환해도 별 다를 것이 없는 문제가 된다. <br>
  ![스크린샷 2021-12-02 오후 4 48 12](https://user-images.githubusercontent.com/37065429/144379637-d933608e-cb04-4f75-978e-842db560a421.png)<br>
  → 문제에 대한 정답? 우린 이미 구했다. 위를 보자!<br>

<br>

#### Expected Time to Any Recurrent State

- <span style="color:red">Question. </span>Starting from a <span style="color:orange">transient state i</span>, what is the <span style="color:orange">expected number of steps until a recurrent state is entered</span>(which we call <span style="color:orange">absorption</span>)?

  - Special case when all recurrent states are absorbing<br>
    ![스크린샷 2021-12-02 오후 5 01 40](https://user-images.githubusercontent.com/37065429/144381445-9f75809b-9ba9-48d3-8ee1-d6866367b88e.png)<br>
    → Spider-Fly!
  - μi를 새롭게 정의해서, <br>
    ![스크린샷 2021-12-02 오후 5 02 23](https://user-images.githubusercontent.com/37065429/144381555-b5a4818a-ffb5-4dd2-9fe9-ada5c167f519.png)
  - 그럼 문제에 대한 정답은 다음과 같다.<br>
    ![스크린샷 2021-12-02 오후 5 02 52](https://user-images.githubusercontent.com/37065429/144381625-1e89d15c-1183-439d-86fb-b461b0787650.png)<br>

  <br>

#### Expected Time to a Particular Recurrent State s

- 풀이의 용이성을 위해 Single recurrent class를 생각하자.
- 우리는 두 개의 질문을 할 것이다.<br>
  <span style="color:red">Q1. </span>**Mean first passage time.** Starting from i, <span style="color:blue">expected number of transitions to ti</span> to reach s for the first time.<br><span style="color:red">Q2. </span>**Mean first recurrence time.** Starting from s, <span style="color:blue">expected number of transitions to ts*</span> to reach s for the first time.
- 가정하는 MC는 다음과 같다.<br>
  ![스크린샷 2021-12-02 오후 8 51 55](https://user-images.githubusercontent.com/37065429/144416877-3cad1b10-72fc-42be-9f3f-01279e08ba4a.png)
- 풀이는 다음과 같다.<br>![IMG_B2B85526A866-1](https://user-images.githubusercontent.com/37065429/144416597-cd7e099c-e08f-477b-a252-45b9a2d8bbe2.jpeg)<br>
  → 1-2와 2-2는 내가 풀어서 넣었다. 틀릴 수도 있당.
