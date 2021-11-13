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

<br>

<br>

## Central Limit Theorem: Proof

### Moment Generating Function (MGF)

- CLT에 대한 증명을 하기 전에 MGF라는 것을 알고 가보자
- 간단하게 <span style="color:red">Moment Generating Function</span>은 s라는 파라미터를 갖는 X에 대한 함수이다. <br>
  → The <span style="color:red">Moment Generating Function</span> Mx(s) of a rv X is a function of a scaler parameter s
- 수식으로는 다음과 같이 표현된다. <br>
  ![스크린샷 2021-11-13 오후 1 01 48](https://user-images.githubusercontent.com/37065429/141607748-0fb44cd5-0b75-43f2-a996-53d2fa867c34.png)
- 정리할 때는 편하게 M(s)라고 적겠다.

<br>

#### Examles

- 몇 가지의 예제를 통해 MGF를 만드는 법을 확인해보자.
  1. Discrete<br>
     ![스크린샷 2021-11-13 오후 1 08 25](https://user-images.githubusercontent.com/37065429/141607774-2e8eed52-a677-4077-ac49-adcfcdb4dac5.png)
  2. Continuous<br>
     ![스크린샷 2021-11-13 오후 1 08 48](https://user-images.githubusercontent.com/37065429/141607775-ddc88b69-9b4d-47e5-8dc9-657fc566606f.png)
  3. Linear RVs<br>![스크린샷 2021-11-13 오후 1 09 02](https://user-images.githubusercontent.com/37065429/141607776-55e3df9c-23df-4916-bf84-97da56eb290a.png)
     <br>
     → MY와 MX간의 관계를 표현하는 식으로도 해석이 가능하다.
  4. Standard Noraml RV<br>
     <img width="361" alt="스크린샷 2021-11-13 오후 1 11 14" src="https://user-images.githubusercontent.com/37065429/141607777-d3dc7e55-6ca3-4773-bb5d-1362bb6e48b6.png">

<br>

<br>

### Useful Properties of MGF

![스크린샷 2021-11-13 오후 1 19 35](https://user-images.githubusercontent.com/37065429/141607780-85de0925-26d8-4b7e-8d0d-805a566406f0.png)

<br><br>

#### Example

- 앞서 설명한 속성이 어떻게 활용되는지 간단한 Exp RV를 통해 이해해보자.<br>![스크린샷 2021-11-13 오후 1 22 05](https://user-images.githubusercontent.com/37065429/141607781-908e1e48-c80c-49dd-883b-518e3a0c4412.png)
  <br>
  <br>

### Inversion Property

- MGF에는 또 다른 중요한 특성이 있다.<br>
  ![스크린샷 2021-11-13 오후 1 24 43](https://user-images.githubusercontent.com/37065429/141607782-8bf0682e-2862-430d-a680-a2fd6b8d5b90.png)
- 이게 무슨 말일까?<br>
  → 간단히 말하자면, MGF와 X는 <span style="color:red">일대일 관계</span>이고, 만약 우리가 MGF를 안다면 distribution을 <span style="color:red">recover</span> 할 수 있다는 것이다.
- 어떨 떄는 복구하는 것이 어려울 수도 있고, 쉬울 수도 있다.
- 쉬운 예제와 어려운 예제를 하나씩 살펴보자.

<br>

#### Example 1.

![스크린샷 2021-11-13 오후 1 28 48](https://user-images.githubusercontent.com/37065429/141607784-a42fb99e-d87f-4daa-ad36-bc39acfe3615.png)<br>

→ 쉽다 쉬워~~~ 이제 어려운거 해보자.<br>

#### Example 2.

![스크린샷 2021-11-13 오후 1 29 32](https://user-images.githubusercontent.com/37065429/141607786-e674cfb3-ca80-4489-8cfb-70292004426c.png)<br>
→ 식을 전개하면서 사용한 방법은 1 + a + a^2 + ... = 1/(1-a) (when abs(a) < 1)

<br>

<br>

### Back to CLT Proof

- Without loss of generality, assume E(Xi) = 0 and var(Xi) = 1.
- 그러면 Zn은 다음과 같이 정의가 될 것이다.<br>
  ![스크린샷 2021-11-13 오후 1 45 02](https://user-images.githubusercontent.com/37065429/141607787-2faff9dd-5481-4593-a2ce-0dbfe80fb695.png)
- 먼저, Zn의 MGF를 구해보자. (이는 Standard Normal Distribution이 될 것이다.)<br>
  ![스크린샷 2021-11-13 오후 1 46 12](https://user-images.githubusercontent.com/37065429/141607788-7f6d5c9a-d728-4976-8f27-1f7b6a28f4ac.png)
- 간단하게 수식을 전개하기 위해 M = M_X1이라고 하자.
- 그럼 우리가 배웠던 MGF의 첫번째 속성에 의해 다음을 알 수 있다. <br>
  → M(0) = 1, M'(0) = 0, M''(0) = 1
- 그리고 우리가 CLT의 증명을 위해 원하는 것은 다음이다. <br>
  → ![스크린샷 2021-11-13 오후 1 47 55](https://user-images.githubusercontent.com/37065429/141607789-83393f57-d7c8-497c-a6e5-8ce88eef873a.png)<br>
  → 증명을 위해 log도 취하겠다. (으 취한다)
- 그리고 더 편리함을 위해 y = 1/sqrt(n)이라고 하면 <br>![스크린샷 2021-11-13 오후 1 48 42](https://user-images.githubusercontent.com/37065429/141607790-f3e76420-c8f6-4452-b236-2cabcd4011c0.png)
  <br>
  → 분모가 0으로 수렴하니까, 로피탈 룰을 2번 적용하자.
- <img width="588" alt="스크린샷 2021-11-13 오후 1 52 39" src="https://user-images.githubusercontent.com/37065429/141607791-e3596f54-7764-4d9d-a664-aa1926223001.png">
