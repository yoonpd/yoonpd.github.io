---
title: "Random Processes (5)"

categories:
  - Probability and Random Variables
toc: true
toc_sticky: true
---

> 현재 정리하는 내용은 KAIST EE의 이융 교수님, Probability and Intorductory Random Process 강의를 참고하여 작성했습니다.

# Random Processes (5)

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
