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
  → (Xn, Yn) <span style="color:orange">only depends on (Xn-1, Yn-1)</span>.

