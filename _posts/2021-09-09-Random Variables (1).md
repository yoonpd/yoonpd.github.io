---
title: "Random Variables (1)"

categories:
  - Probability and Random Variables
---

# **Random** Variable (1)

> 현재 정리하는 내용은 KAIST EE의 이융 교수님, Probability and Intorductory Random Process 강의를 참고하여 작성했습니다.

## Random variable : Idea and Formal definition

- 현실에서 많은 random variable들은 숫자 형태로 존재한다.<br/>
  → e.g., stock price

- 또한, 숫자 형태가 아닌 것들에 **숫자를 부여함**으로써 수학적 편리함을 갖게 하기도 한다.<br/>
  → e.g., '0' for male and '1' for female. <br/>
  → 이전에 봤던 two rolls of tetrahedral dice의 예제를 보자. <br/><img width="321" alt="스크린샷 2021-09-09 오후 3 18 23" src="https://user-images.githubusercontent.com/37065429/133015020-aab5a515-182d-42f4-b80b-6b3ed308cf9a.png">
  
  <br> → (면의 번호, 면호 번호)로 주어진 sample space 상의 random variable에 숫자를 부여하는 모습이다.

- 그렇다면, 이제 random variable의 정의를 확인해보자. <br/>
  → Mathematically, a random variable <span style="color:red">**X**</span> is a <span style="color:red">**function**</span> which <span style="color:blue">maps from Ω to R</span>. (R : Real Number) <br/>
  → Notation : Random variable X, numerical value x. <br/>
  → 물론, 동일한 sample space에서 다른 random variable(X)를 만들 수 있다. <br/>
  → For a fixed value x, we can associate an event that a random variable X has the value x, i.e., {w ∈ Ω &#124; X(w) = x} <br/><img width="364" alt="스크린샷 2021-09-09 오후 3 33 32" src="https://user-images.githubusercontent.com/37065429/133015050-b5234dbd-9a79-4262-9b5e-efca2995f914.png"><br/>

  → For a discrete random variable X, we call px(x) <span style="color:red">**probability mass function (PMF)**</span> <br/>

  → PMF는 이산 확률 변수에서 특정 값에 대한 확률을 나타내는 함수이다! <br/>
  
  
  
- 그러면, notation에 대한 예제를 살펴보자!

  - 주사위를 굴렸을 때, sample space Ω = {1,2,3,4,5,6}이다.

  - Random variables X의 대한 정의를 내려보자. 얘는 함수다!<br/>

    > X = 1 for even numbers.
    >
    > X = 0 for odd numbers.

  - 그럼 이 놈에 대한 Notation은 다음과 같이 된다.<br/>

    > Event A1 = {w ∈ Ω | X(w) = 1} = {2, 4, 6} ⊂ Ω <br/>
    > → simply, A1 = { X = 1 }
    >
    > Event A2 = {w ∈ Ω | X(w) = 0} = {1, 3, 5} ⊂ Ω <br/>
    > → simply, A2 = { X = 0 }

  - A1 = { X = 1 }이 A1 = {w ∈ Ω &#124; X(w) = 1} 이렇게 표현됨 또한 알아야 한다.

  - 그리고 random variable X는 함수이다.  <span style="color:blue">which maps from Ω to R</span> <br/>
  
    |                              X                               |          x           |             P(X=x)              |
    | :----------------------------------------------------------: | :------------------: | :-----------------------------: |
    | 확률 변수 X<br />Sample space 내에 있는 각 원소에<br /> 하나의 실수값을 대응시키는 함수 | X가 할당하는 실수 값 | 실수 값이 나올 확률 값<br />PMF |
  
    

## Popular discrete random variables

- **Only <span style="color:red">binary</span> values.** <br/>
  → p ∈ [0, 1] <br/>

  > X = 0, w.p. 1-p,
  >
  > X = 1, w.p. p
  >
  > w.p. : with probability

  - In other words, px(0) = 1-p, px(1) = p from our PMF notation. <br/>
    → success/failure, head/tail
  - Very useful for an indicator rv(random variable) of a event A.<br/>

- **Uniform X with paramete a, b (integer a,b, where a <= b)**

  - 그렇다면, Ω = {a, a+1, ..., b}가 될 것이고, 여기서 uniformly at random하게 숫자를 뽑는다고 해보자.

  - 그럼 X에 대해 몰라도 괜찮다! → 모든 숫자가 동일한 확률을 갖게 되니까 <br/>
    
    <img width="230" alt="스크린샷 2021-09-13 오전 11 24 19" src="https://user-images.githubusercontent.com/37065429/133015104-e8a70438-13ba-465e-90f5-3b6c5f0bc792.png">
    
    <br/>
    
    *typora로 수식 쓰는 법을 알아냈다.*<br/>
  
- Binomial X with parameter n, p <br/>
  → Models <span style="color:red">**the number of success**</span> in a given number of <span style="color:red">**independent trials**</span>.

  - n번의 동전 던지기를 하고, p의 확률로 앞면(success)이 나온다고 하자. 그럼 여기서, k번의 앞면이 나올 확률을 어떻게 구할까?

    <img width="211" alt="스크린샷 2021-09-09 오후 4 13 40" src="https://user-images.githubusercontent.com/37065429/133015076-09c3ffc1-aa05-46a2-9435-8a5dcdecf16a.png">

    → 요렇게 나오게 된다!
    
    <img width="174" alt="스크린샷 2021-09-13 오전 11 24 08" src="https://user-images.githubusercontent.com/37065429/133015089-bb75e34f-9d6e-4a38-8eca-af8c6f4192b7.png">
    
    → 괄호 표시가 다른건 내가 익숙하지 않아서다.<br/>
  
- Gemetric X with parameter p

  - 무한히 많은 independent한 시도 끝에(k번의 시도) 성공하는 확률

  <img width="191" alt="스크린샷 2021-09-13 오전 11 23 57" src="https://user-images.githubusercontent.com/37065429/133015163-0c0885c7-3003-47ad-88ad-5d20182fcc57.png">

  <img width="278" alt="스크린샷 2021-09-09 오후 4 24 07" src="https://user-images.githubusercontent.com/37065429/133015131-a1b1ec81-f093-4ec3-a9be-5c432bf8a490.png">

  - 그림처럼 모델이 성공을 할 때까지 기다리는 양상을 보인다.<br/>

  


## Summarizing random variables : Expectation and Variance

- Expectation(기대값)의 표현 : 

  1. Expectation은 RV에 대한 평균이라고 볼 수 있고, 흔히 아는 산술 평균이 아닌 확률 평균이다.

  2. 확률 평균 : 각각의 변수의 확률을 고려한 평균

  3. 수식 표현<br/>
     
     <img width="164" alt="스크린샷 2021-09-13 오전 11 23 45" src="https://user-images.githubusercontent.com/37065429/133015179-7cbbac03-3c50-42aa-8f01-980b0d24a43b.png">
     
     → 각각의 변수의 확률을 고려했다고 했으니까, </br>

     → px(x) : relative frequency of value x 
     
     <img width="193" alt="스크린샷 2021-09-13 오전 11 23 34" src="https://user-images.githubusercontent.com/37065429/133015189-2a7c59eb-4703-4025-9183-d3d4d93aa475.png">
4. <img width="139" alt="스크린샷 2021-09-13 오전 11 23 22" src="https://user-images.githubusercontent.com/37065429/133015203-6ed242db-c814-4c78-a1a4-bdb0f8e4cf6c.png">
   
     


  <br/>

- Properties of Expectation

  1. if X >= 0, E[X] >= 0
  2. if a <= X <= b, a <= E[X] <= b
  3. For a constant c, E[c] = c <br/>

- For a rv X, Y = g(X) is also rv. <br/>
  → 앞서 말한 것 처럼, 동일한 sample space에서 여러 개의 rv가 있을 수 있음 <br/>
  <img width="222" alt="스크린샷 2021-09-09 오후 4 44 20" src="https://user-images.githubusercontent.com/37065429/133015219-50062453-22d3-4c1b-9394-5affede8ecdd.png">

  - 그렇다면 이 식은 어떠한 특성이 적용이 됨

    1. <img width="276" alt="스크린샷 2021-09-13 오전 11 23 02" src="https://user-images.githubusercontent.com/37065429/133015241-b7780a5b-55fa-47fd-99ff-5c6f87f34ef7.png">
       
    2. <img width="209" alt="스크린샷 2021-09-13 오전 11 22 44" src="https://user-images.githubusercontent.com/37065429/133015251-eb1a4b42-c28b-4339-99ed-f46e7382d4cf.png">

- Variance : measures <span style="color:red">how much the spread of a PMF is</span>

  - 동일한 expectation을 갖더라도 서로 다른 '형태'를 띄고 있을 수 있다. <br/>
    → 형태 : spread pattern

  - <img width="210" alt="스크린샷 2021-09-13 오전 11 22 31" src="https://user-images.githubusercontent.com/37065429/133015270-4d679f67-980f-4997-89ab-8396eb75bf0a.png">
    
  - <img width="118" alt="스크린샷 2021-09-13 오전 11 22 13" src="https://user-images.githubusercontent.com/37065429/133015279-0ca1efe3-db90-43ab-b667-b493c4073cbf.png">
    
    <br/>→ Standard Deviation (표준 편차)
  
  - Variance : Useful property

    1. <img width="431" alt="스크린샷 2021-09-13 오전 11 21 54" src="https://user-images.githubusercontent.com/37065429/133015292-e4e1eb60-df8e-41ad-a0e8-293bdeff8257.png">
       
       

       
       
    2. <img width="170" alt="스크린샷 2021-09-13 오전 11 21 39" src="https://user-images.githubusercontent.com/37065429/133015304-e2d29c65-d4ca-474a-82cd-fd201d905d07.png">
       
       → Additional additive term does not affect to <span style="color:red">**spread pattern.**</span>
    
    3. <img width="485" alt="스크린샷 2021-09-13 오전 11 21 22" src="https://user-images.githubusercontent.com/37065429/133015323-b44f6f9b-5466-4bc3-99fe-88abc2efe207.png">
       
       
    
       
    
  - Example) Variance of a Bernoulli rv (p) <br/>
    <img width="356" alt="스크린샷 2021-09-13 오전 11 20 48" src="https://user-images.githubusercontent.com/37065429/133015339-9f210060-c835-4f99-8d27-9d40b71e5cc8.png">
