---
title: "Random Variables (2)"

categories:
  - Probability and Random Variables
---

# Random Variable (2)

> 현재 정리하는 내용은 KAIST EE의 이융 교수님, Probability and Intorductory Random Process 강의를 참고하여 작성했습니다.

- 시작하기 전 (1)에서 한 내용을 복습하고 갑시다. <br/>

  1. Random Variables(X)는 어떤 이벤트 w에 대한 값을 실수(x)로 mapping해주는 '함수'이다.

  2. <img width="478" alt="스크린샷 2021-09-13 오후 2 23 53" src="https://user-images.githubusercontent.com/37065429/133351995-e169f824-894f-48c3-afae-950a685b83e3.png">

     <br/>

## (Functions of) Multiple random variables

- Joint PMF

  - For two random variables X, Y, consider two events {X=x}, {Y=y}, and <br/>
    <img width="427" alt="스크린샷 2021-09-13 오후 2 25 45" src="https://user-images.githubusercontent.com/37065429/133351984-d051a33c-575e-4a98-9bcc-b3219753ac76.png">
  - 그러면 얘는 이러한 속성을 갖게 된다. <br/>
    <img width="270" alt="스크린샷 2021-09-13 오후 2 30 28" src="https://user-images.githubusercontent.com/37065429/133351967-9288a6d0-4b70-4e49-bb14-647a233450de.png">
  - 또한, 얘에서 어떤 속성을 갖게 되면 Marginal PMF라고 불릴 수 있다.
    <br/>

- Marginal PMF

  - Joint PMF에서 아래 두 속성을 만족한다면 Marginal PMF이다.

    1. <img width="279" alt="스크린샷 2021-09-13 오후 2 32 05" src="https://user-images.githubusercontent.com/37065429/133351955-ac664120-cc4c-492f-b802-3ee02dc970cf.png">

    2. <img width="276" alt="스크린샷 2021-09-13 오후 2 32 25" src="https://user-images.githubusercontent.com/37065429/133351934-a9a0c4c5-8a27-453a-b9ad-769e77734a07.png">

       <br/>

- Functions of Multiple RVs

  - Z라는 Random Variable이 있다고 해보자, 그리고 Z = g(X, Y)로 rv인 X, Y와 g라는 함수를 통해 표현된다.<br/>
    → X+Y , X^2 + Y 등이 될 수 있다.<br/>

    <img width="629" alt="스크린샷 2021-09-13 오후 2 38 26" src="https://user-images.githubusercontent.com/37065429/133351917-55de77a6-d6d7-4f21-800a-3901d4be9b8b.png">

    - 그렇다면 이렇게 표현될 수 있다!

    - <span style="color:red">**여기서, Pz를 위해 시그마 연산에서 X와 Y, g를 통해 만들어질 수 있는 모든 값을 사용한다는 것을 명심하자.**</span>

      <br/>

  - 그럼 이 친구의 Expectation은 어떻게 표현될까? 비슷하다. <br/>

    <img width="571" alt="스크린샷 2021-09-13 오후 2 41 17" src="https://user-images.githubusercontent.com/37065429/133351903-5bcd3c92-aec9-4743-9fb3-2f51399d20bd.png"> <br/>

- Linearity of Expectation for Multiple RVs

  - (1)에서 말했던 것과 같이 Expectation은 다음과 같은 속성을 갖고 있다. <br/>
    <img width="305" alt="스크린샷 2021-09-13 오후 2 50 47" src="https://user-images.githubusercontent.com/37065429/133351881-fa58fa66-8f79-42f8-be66-30e98cd18e01.png">

  - 이에 따라서, Multiple RVs에서는 다음과 같은 속성을 가질 수 있다. <br/>
    <img width="311" alt="스크린샷 2021-09-13 오후 2 52 40" src="https://user-images.githubusercontent.com/37065429/133351860-753a8b81-f510-47ee-a29c-94604b389713.png">

  - 또! 여기서 확장해보자.

    1. <img width="494" alt="스크린샷 2021-09-13 오후 2 53 30" src="https://user-images.githubusercontent.com/37065429/133351850-00c8bd3a-cfb2-4c48-aff4-d5496b236498.png">

    2. <img width="525" alt="스크린샷 2021-09-13 오후 2 54 08" src="https://user-images.githubusercontent.com/37065429/133351838-60f2880f-6c0e-405f-bbd4-6662c30ea851.png">

       <br/>

  - Linearity를 사용하여, Mean of a binomial rv Y with (n, p)를 구해보자. <br/>
     → Y = number of success in n Bernoulli trials with p

    - 그렇다면, Y = X1 + X2 + ... + Xn으로 표현될 수 있고, Xi = Bernoulli rv라고 할 수 있다.

    - 여기서, Y의 Expectation을 구해보자.<br/><img width="443" alt="스크린샷 2021-09-13 오후 3 07 52" src="https://user-images.githubusercontent.com/37065429/133351828-84968af2-383b-4766-8520-1ed36bd755b1.png">
       <br/>

      → Bernoulli rv에서 P(X=1)로 표현됨을 기억하자... <br/>
      → Bernoulli rv는 단순히 '성공' 또는 '실패'로 나타나는 실행(bernoulli trials)을 n번 반복했을 때, 성공이 나타난 횟수를 확률 변수로 갖는 것 <br/>
      → 각 실행은 서로에게 어떤 영향도 주지 않음<br/>

## Conditioning of random variables

- 이전 내용을 복습하자면, probability law에는 두 가지의 종류가 있고, 이는 Normal과 Conditional이다.
- 둘 다, 3 axioms를 만족시키며 다음과 같은 속성과 notation을 갖고 있다. <br/>
  <img width="463" alt="스크린샷 2021-09-13 오후 3 25 29" src="https://user-images.githubusercontent.com/37065429/133351813-3eb60bbb-2b36-4f31-9811-c21c15dc2d12.png">
- 하지만 얘네가 모두 단순히 notation임을 기억하고, 우변이 나오게 된 이유에 대해서 잘 알고 있자.
  1. Normal과 Conditional에서의 E와 var 
     - 공통적으로 x={1, 2, 3, 4}를 뽑게 되고, 각각은 동일한 확률로 뽑힌다. <br/>
     - Normal <br/>
       <img width="257" alt="스크린샷 2021-09-13 오후 4 10 28" src="https://user-images.githubusercontent.com/37065429/133351793-f9498e86-4e17-4d4c-a560-8c6518cebb86.png">
     - Conditional,  조건 : X >= 2 <br/>
       <img width="286" alt="스크린샷 2021-09-13 오후 4 13 19" src="https://user-images.githubusercontent.com/37065429/133351777-9e0bc278-d91c-4bae-85f8-41dd3914cc8e.png">
       - X>=2에서는 P_X&#124;A(1) = 0이 됨을 이해하자, 그렇게 되면 모두 동일한 확률을 갖게 됨으로 P_X&#124;A(-) = 1/3이 된다.
- Conditioning on Event VS Conditioning on RV

| <img width="185" alt="스크린샷 2021-09-13 오후 4 22 36" src="https://user-images.githubusercontent.com/37065429/133351753-ba703656-ca81-4e81-9f9b-65d20ff148b1.png"> | <img width="236" alt="스크린샷 2021-09-13 오후 4 23 07" src="https://user-images.githubusercontent.com/37065429/133351739-87ca02f2-0c7e-432f-ae15-d736c278e559.png"> |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
|                   - Conditioning on Event                    |                     - Conditioning on RV                     |

​	→ Y=y를 A라고 생각한다면 동일한 Notation에서의 수식을 얻을 수 있다!

- Conditional PMF

  - Conditional PMF <br/>
    <img width="345" alt="스크린샷 2021-09-13 오후 5 19 02" src="https://user-images.githubusercontent.com/37065429/133351717-169a0cca-f972-40f6-9d54-4a830982a321.png">

    - P(A|B) = P(A ∩ B) / P(B) 인데, P(A ∩ B)를 Joint PMF로 표현할 수 있다.

  - Multiplication rule <br/>
    <img width="362" alt="스크린샷 2021-09-13 오후 5 22 58" src="https://user-images.githubusercontent.com/37065429/133351707-22b865f0-33ee-4c20-be34-c759c1c1ab5f.png">

  - 예제를 풀어보자

    - 다음은 tetrahedral 주사위를 던졌을 때, 두 면의 숫자에 따른 확률이다. <br/>
      <img width="374" alt="스크린샷 2021-09-13 오후 5 28 01" src="https://user-images.githubusercontent.com/37065429/133351680-6c16ca54-4109-4989-a27e-106053edc3d0.png">

      1. <img width="488" alt="스크린샷 2021-09-13 오후 5 29 42" src="https://user-images.githubusercontent.com/37065429/133351662-867e0f10-46d5-4133-916d-7bbfbf4829b1.png">

      2. <img width="121" alt="스크린샷 2021-09-13 오후 5 30 47" src="https://user-images.githubusercontent.com/37065429/133351545-aeece199-5a54-46e1-b169-faf292818c04.png">

      3. <img width="466" alt="스크린샷 2021-09-13 오후 5 36 01" src="https://user-images.githubusercontent.com/37065429/133351535-f87d4b2e-2d1d-4fa7-8e65-94a95eb48436.png">

         <br/>

  - Total Expectation Theorem for {Ai}

    - 여기서 잠깐! TPT에 대해 복습을 해보고 들어가자. <br/>
      → Sample space를 mutually exclusive하게 partition({A1,...An})으로 나눴을 때, P(B) = ΣP(Ai)P(B &#124; Ai)를 만족한다.

    - 이거를 Conditional PMF에 적용해보자. <br/> <img width="416" alt="스크린샷 2021-09-13 오후 6 07 27" src="https://user-images.githubusercontent.com/37065429/133351509-8d7d295e-64ca-4fe3-863c-c242d8918a59.png">

      - 그러면 이렇게 된다. 이걸로 Expectation을 계산해보자.
      - Expectation은 기댓값, 확률적 평균을 의미하니까 각 나온 TPT에 시그마를 붙여 계산한다. <br/>
        → Conditioning of random variables 에 대한 정리를 위에서 살펴보면서 하면 된다.

    - Total Expectation Theorem <br/>

      <img width="505" alt="스크린샷 2021-09-13 오후 6 14 37" src="https://user-images.githubusercontent.com/37065429/133351495-75f4eff5-857c-4182-8108-0ced24939e69.png">

      → 이전에도 했듯이, 얘는 가중치를 더한 형태가 된다. 하지만 가중치와 기댓값이 곱해질 때(2번째 변), 각 Ai에 대한 값이 곱해짐을 확인해야 한다. <br/>

      → 물론, **Conditioning on Event VS Conditioning on RV** 에서 설명한 것 처럼 Ai는 Y=y처럼 다른 Random Variable로 변환될 수 있다. <br/>
      <img width="446" alt="스크린샷 2021-09-13 오후 6 24 46" src="https://user-images.githubusercontent.com/37065429/133351475-88c79b3b-e16e-408a-919b-015db69a30b9.png">

      - 이에 대한 예제를 살펴보자, <br/>
  <img width="738" alt="스크린샷 2021-09-15 오전 10 12 21" src="https://user-images.githubusercontent.com/37065429/133358076-d350833b-cbc9-466a-b074-9b76ce060508.png">

- Memoryless Property 

  - Some RVs often do not have memory. → 말 그대로 기억력이 없음을 의미

  - 예시를 통해 이 말을 이해해보자. <br/>
    <img width="591" alt="스크린샷 2021-09-15 오전 10 28 54" src="https://user-images.githubusercontent.com/37065429/133358108-c5622dde-579b-477c-a722-99deacc90dee.png">

    → 필은 m분을 먼저 기다린 뒤, n분 후에 버스가 도착할 확률을 궁금해 하고 있다. <br/>

    → 도는 지금부터 n분 후에 버스가 도착할 확률을 궁금해 하고 있다. <br/>

    → 이 둘은 결국 같은 질문이고, 필이 m분을 기다렸다는 것은 사실상 영향을 주지 않는다.

  - <span style="color:blue">**Definition.**</span> A random variable X is called memoryless. If, for any n, m >= 0

  - <span style="color:red">**Meaning.**</span> Conditioned on X > m, X - m 's distrubution is **the same as the original X**.
    <img width="298" alt="스크린샷 2021-09-15 오전 10 34 59" src="https://user-images.githubusercontent.com/37065429/133358127-865195ce-8b2d-4c7d-9400-54821c9fb4dc.png">

  - *모든 RV가 이를 만족하는 것은 아님*<br/>

  - Memoryless Porperty of Geometric RVs <br/>
    → Geometric RVs는 무한히 많은 independent한 시도 끝에(k번의 시도) 성공하는 확률을 의미 <br/>
    → 그리고 아래와 같은 식을 만족한다.

    <img width="383" alt="스크린샷 2021-09-15 오전 10 40 59" src="https://user-images.githubusercontent.com/37065429/133358162-13e448df-4c6f-4fe5-ad98-27b793c2c414.png"> <br/>

    - 그럼 이 친구가 항상 memoryless라고 가정을 해보자.
      <img width="599" alt="스크린샷 2021-09-15 오전 10 43 52" src="https://user-images.githubusercontent.com/37065429/133358143-d21dae51-e1d2-45c9-8466-d87bc122ed73.png"> <br/>

      → 짜잔, 이렇게 증명이 되고 Geometric RV는 항상 memoryless임을 알 수 있다. <br/>

    - 그럼 또, 이 친구가 좋은 친구인 이유를 아래 예시를 보면서 확인해보자.
      <img width="734" alt="스크린샷 2021-09-15 오전 10 58 17" src="https://user-images.githubusercontent.com/37065429/133358187-6ae70e69-8428-4f1d-b980-4a9880961225.png">

## 

