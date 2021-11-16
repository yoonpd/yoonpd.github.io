---
title: "Random Processes (1)"

categories:
  - Probability and Random Variables
toc: true
toc_sticky: true
---

# Random Processes (1)

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





