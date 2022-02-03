---
title: "Random Processes (1)"

categories:
  - Probability and Random Variables
toc: true
toc_sticky: true
---

# Random Processes (1)

> 현재 정리하는 내용은 KAIST EE의 이융 교수님, Probability and Intorductory Random Process 강의를 참고하여 작성했습니다.

- 드디어 새로운 목차다.
- Random Process는 머신러닝, 통신 시스템 등에서 아주아주 많이 쓰이는 개념이라고 한다.

<br>

## Introduction of Random Processes

- Many probabilistic experiments that <span style="color:red">evolve in time</span>
  - Sequence of daily prices of a stock
  - Sequence of scores in football
  - Sequence failure times of a machine
  - Sequence of traffic loads in Internet
- Random Processes는 이러한 것에 대한 <span style="color:red">수학적 모델</span>을 만들기 위해 존재한다. 

<br>

### Random Process : Basic (1)

- 랜덤 프로세스의 정의는 다음과 같다. <br>
  → A random process is a <span style="color:red">sequence of Random Variables</span> indexed by <span style="color:orange">time</span>.
- 여기서 시간은 모델링 방법에 따라 discrete or continuous일 수 있다.
- **Notation**<br>![스크린샷 2021-11-16 오후 4 08 55](https://user-images.githubusercontent.com/37065429/141948191-f476e567-9d18-4a6e-aae0-0d06e17c6f66.png)
- 어떤 <span style="color:red">특정한 시간</span>에 대해서, t, Xt, X(t)는 RV이다.
  - 여기서, t, Xt, X(t)는 discrete or continous이다.

<br>

### Random Process : Basic (2)

- **Discrete case** 와 **Continous case**에 대한 예제를 한 번 보자.<br>

  #### 1.  Discrete

  ![스크린샷 2021-11-16 오후 4 15 15](https://user-images.githubusercontent.com/37065429/141948198-1c80b2f5-26f7-4d4a-b02d-1071d65b73b4.png)<br>

  → Xi는 <span style="color:orange">**i** 시간에 해당하는 RV</span>이다. 따라서, Xi는 sample space의 값을 실수로 mapping하는 역할을 한다. 그것이 w<br>→ 마지막에서, X3(w1)은 X에서 3번째 고정된 시간에 w1에 대한 아웃풋의 값이므로 130이 된다.<br><br>

  #### 2.  Continuous

  ![스크린샷 2021-11-16 오후 4 21 59](https://user-images.githubusercontent.com/37065429/141948202-6dac03a9-96e9-41b5-890e-f4c72afaf36f.png)<br>
  → Discrete와 매우 유사하다. <br>
  → 하지만 Notation을 사용하는 방법이 있음을 확인하자. <br><br>

  |          | Discrete | Continuous |
  | :------: | :------: | :--------: |
  | Notation |  Xt(w)   |  X(t, w)   |

  <br>

### Random Processes: Our Interest

- 근데, 우리는 CLT, WLLN에서 a sequence (or a collection) of RVs에 대해 배웠다.
- 도대체 <span style="color:red">무엇이 다를까</span>?
- 간단하게 생각하기 위해 discrete한 경우를 생각해보자.

1. Physical difference
   1. RP는 <span style="color:red">infinite sequence of RVs</span>(X1, X2, ...)를 다룬다.
   2. 즉, outcome은 a infinite sequence of sample values x1, x2, ...이다.
2. Semantic difference
   1. <span style="color:pink">Dependence</span> : 현재 시간과 다른 시간 또는 어떤 시간과 또 다른 시간에서의 Xi들의 연관성을 알 수 있다.
   2. <span style="color:pink">Long-term behavior</span> : 향후 발생할 미래에 대한 예측이 가능하다. <br>
      → What is the fraction of times that a stock price is above 3000?<br>

<br>

### 4 Types of Random Processes

![스크린샷 2021-11-16 오후 4 36 07](https://user-images.githubusercontent.com/37065429/141948206-201d3e78-d9a4-40ca-afa3-014e95b7b84c.png)<br>
→ 우리가 무엇을 원하냐에 따라 4가지 중 어떤 것을 사용해도 된다.<br>
→ (a) : 모든 시간대에서 변동하는 비트코인의 가격 <br>

<br>

### Random Processes in This Course

- 간단하게 무엇을 배우는가에 대해서 알아보자.

|                          Bernoulli                           |                           Poisson                            |                            Markov                            |
| :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
| Discrete Time<br />Xi  ㅛ Xi-1, Xi-2, ...<br />오늘은 과거와 관련이 없다! | Continuous time version of BP<br />s~t 기간의 일과 t~t+a 사이의 일은 관련 없다!<br />오늘은 과거와 관련이 없다와 비슷! | Discrete Time<br />One-step more general than BP/PP<br />오늘은 '어제'와만 관련이 있고, 그 나머지는 관련이 없다! |

<br>

## Bernoulli Process

- 가장 간단한 Random Process의 한 형태이다.

<br>

### Bernoulli Process

- 간단한 예제를 하나 들어보자.
- At each minute, We <span style="color:orange">toss a coin</span> with probability of head 0 < p < 1. <br>
  → 여기서 중요한 것은, 시간이 아닌 (물론 이것도 중요) 각 이벤트들이 <span style="color:orange">**independent**</span>하다는 것이다.
- 이러한 값들은 그러면 X1, X2, X3,...로 표현될 수 있고, 이것들은 <span style="color:orange">Independent Bernoulli trials</span>이다. <br>
  → 여기에 야무지게 시간으로 indexing을 해주면 된다.
- BP는 **discrete time**과 **discrete value**를 위한 것이다.
- 또한, BP를 a type of 'arrival' process라고도 한다. <br>
  → 서버로 데이터가 전송될 RP or 상점에 방문객이 존재할 RP

<br><br>

#### Number of arrivals and Time until the first arrival

- T라는 값이 # of slots until the first arrival이라고 해보자.
- 그러면 T는 RV를 의미하게 되고, 만약 (X, X, X, X, X, O)라고 하면 T는 6이라는 값을 가질 것이다.
- 이러한 T는 또한 Geometric Random variable이다.<br>![image](https://user-images.githubusercontent.com/37065429/142355639-5cde1b19-1636-4ec5-8222-4beaf118e5db.png)
- Geom RV는 <span style="color:blue">memoryless</span>라는 속성도 갖고 있다.

<br>

#### Memoryless and Fresh-start after Deterministic time n

- 앞선 예제를 한(세) 마디로 표현하면 다음과 같다. <br>→ Independence across slots
- 어? 그럼 어떤 프로세스가 진행되다가 그 중간에 들여다보면 어떻게 보일까?
- 이것에 대한 질문을 여러가지 해보자.
  1. U = X1 + X2 ㅛ V = X5 + X6?<br>
     → 매우 직관적으로 그렇다고 할 수 있다. <br>
     → Because Xi s are independent.<br>
  2. <span style="color:red">After</span> time n = 6, I start to <span style="color:red">look</span> at the process Xn (n=6 ~ INF) <br>
     → (X1, X2, ... , X5) ㅛ (X6, ... XINF) <br>
     → 즉, 우리는 이전 것과 상관없이 '우리의 입장'에서는 <span style="color:red">fresh-start</span>와 같이 보일 것이다. <br>
     → If you watch <span style="color:blue">the on-going</span> Bern process(p) <span style="color:blue">from some time n</span>, you still see <span style="color:blue">the same Bern process(p).</span><br><br>

#### Fresh-start after Random time N

- 더 빡센 질문이다.
- 우리가 언제 들여다 봐도 동일한 Bern process(p)를 볼 수 있다는 것은 위에서 알 수 있었다.
- 근데,,,,,,,시간이 random이라면?? 즉, '언제 들여다 본다' 자체가 random variable이라면 어찌될까
- 예제를 통해 어떤 의문인가를 확인해보자.<br>![image](https://user-images.githubusercontent.com/37065429/142356889-cecc9361-1730-4eb9-8e31-748e46ffd419.png)<br>*→ 누군가가 process를 지켜보다 조건이 충족되었을 때, 나를 불러 확인하도록 하는 예제이다.*
  1.  Time of 3rd arrival에 해당하는 N은 7, 그 이후는 Bern process이다.<br>→ 이전에 3개가 도착한 것은 <span style="color:red">이미 확정</span>되어 있다.
  2.  (1)과 동일하다.
  3.  이건 어렵다........ 결론을 말하자면 일단 답할 수 없고, n에서 본 순간 '111'이 나와야 하므로 '111'자체는 random이 될 수 없다.<br>
     → 즉, 111이 나왔다 해도 n 이후의 process는 Bern process가 아니다. <br>→ 추가로, 이를 알기 위해 <span style="color:red">future knowledge</span>가 필요하다.<br><br>

#### Stopping time

- Stopping time이라는 말의 정의를 앞서 설명한 예제를 통해 설명할 수 있다.
- In probability theory, a random time N is said to be a <span style="color:orange">stopping time</span>, if the question of "N=n?" <span style="color:orange">can be answered only from the present and the past knowledge</span> of X1, X2, ... Xn.
- 따라서, N 이후에 fresh-start라면, N은 stopping time이라고 할 수 있다.
- 앞선 예제에서, E1과 E2는 stopping time이다.

<br>



#### Distribution of Busy Periods (1)

- 예제를 하나 생각해보자.
- 어떤 서버가 있고, 요청이 들어왔을 때 busy(B), 아닐 때를 idle(I)라고 해보자.
- 여기서, First busy period B1을 다음과 같이 정의해보자. <br>
  → Starts with the first busy slot and ends just before the first subsequent idle slot
- 무수히 많은 B1들이 있을텐데 두 개를 대표적으로 확인해보자.<br>![image](https://user-images.githubusercontent.com/37065429/142364214-83b06658-9576-4564-892a-f25d9bed6d8e.png)
  1. B1 = 3
  2. B2 = 4
- 이런식으로 확인을 할 수 있고, 일반화해서 생각해본다면,
  1. Busy Period가 바로 시작
  2. Idle이 지속되다가 Busy Period가 시작
- 첫번째는 우리가 어디서 많이 본 RV로 치환할 수 있다.<br>
  → <span style="color:red">Geometric Random Variable</span>
- 두번째는? **Fresh-start**를 생각하자! <br>
  → N이라는 새로운 RV가 <span style="color:orange">time of the first busy slot</span>이라고 한다면, N은 <span style="color:orange">stopping time</span>이다.<br>
  → 왜냐? N 이후에는 Bern process를 fresh-start할 수 있기 때문이다! <br>
  → 그러면, 그 이후는 <span style="color:red">Geometric Random Variable</span>이다.
- 따라서, B1 is geometric with parameter <span style="color:orange">(1-p)</span> <br>
  → p : idle

<br><br>

#### Distribution of Busy Periods (2)

- (1)과 똑같다. 하지만 두 번째 periods를 알고 싶다!!! (B2)
- 여기서 <span style="color:red">fresh-start</span>의 힘을 알 수 있다.<br>
  → N : time of the first busy slot of the second busy period <br>
  → then, Is N a stopping time? → <span style="color:red">YES!</span>
- 그럼 B2 are <span style="color:blue">identically distributed</span> as <span style="color:red">Geom(1-p)</span>.
- 이는 B3, B4,...에도 동일하게 적용할 수 있다. <br>
  → 이것이 <span style="color:red">fresh-start의 힘이다.</span><br>

<br>

#### Time of k-th arrival

- 이제 더 확장해서 생각해보자.
- Time of the first arrival을 Y1이라 하면, Y1 ~ Geom(p)일 것이다.
- 그러면!! Time of the k-th arrival은 어떻게 될까? 즉, Yk는 어떻게 될까?
- 먼저, 두 Yi, Yi+1의 interval time을 구하고 이 모든 것을 합하면 결국 Yk가 나올 것이다. <br>
  → 이렇게 한 이유는, Yi는 i번째에서 봤을 때 fresh-time이고 i+1도 동일하기 때문이다. <br>
  ![image](https://user-images.githubusercontent.com/37065429/142367690-e6a32728-f660-41c2-a1d1-ef71eb4fb985.png)
- 즉, <span style="color:red">After each Tk, the fresh-start occurs</span> <br><span style="color:blue">
  → Ti are i.i.d and ~Geom(p)</span>
- i.i.d이기 때문에 다음도 도출할 수 있다. <br>
  ![image](https://user-images.githubusercontent.com/37065429/142367891-5f7dcac9-6581-4499-9aec-e30393af10fb.png)
- 근데 아직 distribution을 구하지는 않았다.

<br>

##### PMF of Yk

![image](https://user-images.githubusercontent.com/37065429/142367690-e6a32728-f660-41c2-a1d1-ef71eb4fb985.png)

- Ti는 또한 i.i.d 이고 Geom(p)이다.
- 이제 PMF를 구해보자.<br>
  ![image](https://user-images.githubusercontent.com/37065429/142368121-f748621b-5bf5-4594-91b5-7e6cf250f854.png)<br>→ k번째 도착했을 때의 시간이 t일 경우는 다음과 같이 계산이 된다. <br>
  → 먼저, 시간 t에서 arrival이 있으면서(and) k-1번의 arrivals가 t-1동안 있어야 한다.<br>
  → <span style="color:red">Fresh-start!!</span> 둘은 독립이다!!<br><br>

#### Pascal Random Variable with Parameter (k, p)

- 바로 앞 예제인 PMF of Yk에서 배운 방법이 pascal rv에 대한 내용이다.
- 정의하자면 다음과 같다. <br>→ In the sequence of <span style="color:red">Bernoulli trials</span>, the time Yk of k-th success.
- 식은 다음과 같다. parameter는 k와 p를 사용한다. <br>
  ![image](https://user-images.githubusercontent.com/37065429/142369405-47f36c43-2a42-4275-bab7-2ed5f5eec3c1.png)
- Pascal(1, p) = Geom(p) <br>
  → 당연히, 첫번째에 대한 것은 Geom이다. <br>

<br>
