---
title: "Random Variables (9)"

categories:
  - Probability and Random Variables
toc: true
toc_sticky: true
---

# Random Variable (9)

## Weak Law of Large Numbers : Proof

- WLLN을 증명하기 위해서 Inequality에 관한 두 가지 증명을 알아야 한다.
  1. **Markov Inequality**
  2. **Chebyshev Inequality**

- 하나씩 증명해보자.

<br>

### Markov Inequality

- 이 증명이 궁금해 하는 질문은 <br>
  → Knowing <span style="color:blue">E(X)</span>, Can we say something <span style="color:red">about the distribution of X</span>?
- E만 알고 있다고 해서, distribution을 정확히 알 수는 없지만 rough하게는 알 수 있다.
- 직관적으로 생각해보자. <br>
  ![스크린샷 2021-11-11 오후 4 26 55](https://user-images.githubusercontent.com/37065429/141267825-b8b55090-327f-46a9-88e7-b792eec7696e.png)
- 이를 활용한 것이 Markov Inequality이다. <br>
  ![스크린샷 2021-11-11 오후 4 27 20](https://user-images.githubusercontent.com/37065429/141267857-b4fcdd02-49fb-40e7-9f9b-ef038d6d637e.png)
- 이제 이를 증명해보자. 간단하다.
  1. a > 0일 때, **Ya라는 RV**를 하나 정의하자. <br>
     ![스크린샷 2021-11-11 오후 4 28 15](https://user-images.githubusercontent.com/37065429/141267874-d6558e8e-9f9a-48be-bae3-85b8421a793c.png)
  2. 그러면, non-negativity of X를 사용해서 **Ya <= X일 때, E[Ya] <= E[X]**임을 알 수 있다.
  3. 이제 마지막 단계! <br>
     ![스크린샷 2021-11-11 오후 4 29 08](https://user-images.githubusercontent.com/37065429/141267893-90c7a406-8a99-48c3-8379-918695642a3c.png)

<br><br>

### Chebyshev Inequality

- 이 증명도 궁금해하는 것이 있다. <br>
  → Knowing both <span style="color:blue">E(X) and var(X)</span>, Can we say something <span style="color:red">about the distribution of X</span>?
- Markov Inequality보다 주어진 정보가 더 많으니, 이보다 조금이라도 더 자세하게 distribution을 표현할 수 있을 것이다.
- 직관적으로 생각해보자. <br>
  → 작은 분산은 무엇을 의미할까? 즉, small var(X)가 무엇을 의미할까? <br>
  → 간단하게, X가 이것의 평균으로부터 멀지 않은 곳에 뭉쳐있음을 의미한다 (*간단*). <br>
- 자 그러면, Expectation이 μ, Var가 σ^2이라고 해보자. <br>
  → 이러한 가정에서 Chebyshev Inequality는 다음을 정의한다. <br>
  ![스크린샷 2021-11-11 오후 4 41 16](https://user-images.githubusercontent.com/37065429/141267931-0b65d4cd-3222-4cc4-8a20-1b3948de9bc5.png)
- 정의는 더 간단하다. <br>![스크린샷 2021-11-11 오후 4 41 40](https://user-images.githubusercontent.com/37065429/141267953-d6eb17d7-be3f-4b4c-aa29-2d7c657204c9.png)
  <br>

<br>

#### Example: MI vs CI

- 먼저 앞서 증명한 MI와 CI는 정확한 Distribution이 아닌, 여기 정도에 존재할 것 같다라는 <span style="color:orange">bound</span>를 제공한다.

- X ~ exp(1). Then, E[X] = 1/λ = 1, Var[X] = 1/(λ^2) = 1
- Exact CCDF : P(X >= a) = e^(-aλ) = e^(-a)

|                      Markov Inequality                       |                     Chebyshev Inequality                     |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
| ![스크린샷 2021-11-11 오후 4 52 43](https://user-images.githubusercontent.com/37065429/141268254-9a0e6ba6-1f2e-4c52-8125-d9ffac3f01fb.png) | ![스크린샷 2021-11-11 오후 4 52 52](https://user-images.githubusercontent.com/37065429/141268042-a7fcbe86-ab00-4185-8424-c9d48860d844.png) |

- 여기서 알아낼 수 있는 것은 무엇일까?
  1. <span style="color:orange">For resonably large a</span>, CI provides <span style="color:orange">much better bound.</span>
  2. Knowing the variance helps
  3. Both bounds are the ones that bound the <span style="color:orange">probability of rare events.</span>

<br>

### Back to WLLN Proof

![스크린샷 2021-11-11 오후 4 56 27](https://user-images.githubusercontent.com/37065429/141268067-7744375f-e463-4d0f-8c52-dc6c9a5ee5fa.png)

- CI를 적용하면 다음과 같이 정의할 수 있다.

<br>

## Comparison : WLLN vs CLT

- 동일한 문제에 대해서 WLLN과 CLT로 풀었을 때의 차이점을 확인해보자.

<br>

### Example : Polling using WLLN

- p : fraction of voters who support someone

- <span style="color:orange">Interview n randomly selected voters</span> and record the result in **Mn = (X1 + ... + Xn)/n which is a estimate of p**, where **Bern. rv Xi** = 1 if i-th interviewee answers 'yes', and 0 otherwise.

- 그러면 다음과 같이 WLLN과 CI를 사용하여 식을 만들 수 있다. <br>
  ![스크린샷 2021-11-11 오후 5 46 28](https://user-images.githubusercontent.com/37065429/141268112-00341b72-721b-4efb-8d6c-7dcd1f8d82db.png)

  <br>

  Q1. What is <span style="color:red">*n*</span> so that the probability that our estimate is correct by more than 0.1 is no longer than 0.25?<br>![스크린샷 2021-11-11 오후 5 47 31](https://user-images.githubusercontent.com/37065429/141268136-0d5e7755-9f56-49c1-b5b4-9a86fcaead59.png)
  <br>
  Q2. What is <span style="color:red">*n*</span> so that the probability that our estimate is correct by more than 0.01 is no longer than 0.05?<br>![스크린샷 2021-11-11 오후 5 48 09](https://user-images.githubusercontent.com/37065429/141268186-de36cac2-fa1f-4116-a43e-a805fa98a37c.png)
  <br>

<br>

### Example : Polling using CLT

- 조건은 이전에 푼 문제와 동일하다.

- 그러면, 이번엔 CLT를 적용해서 식을 만들어보자.<br>

  ![스크린샷 2021-11-11 오후 5 49 14](https://user-images.githubusercontent.com/37065429/141268211-e3ba1afc-3858-4b65-85c0-c5cad421561b.png)

- WLLN에서 풀었던 두번째 질문에 대해 CLT를 사용해서 답을 도출해보자. <br>
  ![스크린샷 2021-11-11 오후 5 50 12](https://user-images.githubusercontent.com/37065429/141268231-dd975dc3-1022-437d-8458-6b86ab442001.png)

- 확실히 다른 값이다. CLT가 



