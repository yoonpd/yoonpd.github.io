---
title: "Jekyll Github 블로그에 MathJax로 수학식 표시하기"
tags:
  - Blog
  - MathJax
  - Jekyll
  - LaTeX
use_math: true
---

# Random Variable

> 현재 정리하는 내용은 KAIST EE의 이융 교수님, Probability and Intorductory Random Process 강의를 참고하여 작성했습니다.

## Random variable : Idea and Formal definition

- 현실에서 많은 random variable들은 숫자 형태로 존재한다.<br/>
  → e.g., stock price

- 또한, 숫자 형태가 아닌 것들에 **숫자를 부여함**으로써 수학적 편리함을 갖게 하기도 한다.<br/>
  → e.g., '0' for male and '1' for female. <br/>
  → 이전에 봤던 two rolls of tetrahedral dice의 예제를 보자. <br/>
  ![image-20210909151837671](/Users/yunpildo/Library/Application Support/typora-user-images/image-20210909151837671.png)
  <br> → (면의 번호, 면호 번호)로 주어진 sample space 상의 random variable에 숫자를 부여하는 모습이다.

- 그렇다면, 이제 random variable의 정의를 확인해보자. <br/>
  → Mathematically, a random variable <span style="color:red">**X**</span> is a <span style="color:red">**function**</span> which <span style="color:blue">maps from Ω to R</span>. (R : Real Number) <br/>
  → Notation : Random variable X, numerical value x. <br/>
  → 물론, 동일한 sample space에서 다른 random variable(X)를 만들 수 있다. <br/>
  → For a fixed value x, we can associate an event that a random variable X has the value x, i.e., {w ∈ Ω &#124; X(w) = x} <br/>![image-20210909153336864](/Users/yunpildo/Library/Application Support/typora-user-images/image-20210909153336864.png)<br/>

  → For a discrete random variable X, we call px(x) <span style="color:red">**probability mass function (PMF)**</span>

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

## Popular discrete random variables

- Only <span style="color:red">**binary**</span> values. <br/>
  → p ∈ [0, 1] <br/>

  > X = 0, w.p. 1-p,
  >
  > X = 1, w.p. p
  >
  > w.p. : with probability

  - In other words, px(0) = 1-p, px(1) = p from our PMF notation. <br/>
    → success/failure, head/tail
  - Very useful for an indicator rv(random variable) of a event A.<br/>

- Uniform X with paramete a, b (integer a,b, where a <= b)

  - 그렇다면, Ω = {a, a+1, ..., b}가 될 것이고, 여기서 uniformly at random하게 숫자를 뽑는다고 해보자.

  - 그럼 X에 대해 몰라도 괜찮다! → 모든 숫자가 동일한 확률을 갖게 되니까 <br/>
    $$
    px(i) = \frac {1} {b-a+1}
    , i ∈ Ω
    $$
    <br/>

    *typora로 수식 쓰는 법을 알아냈다.*<br/>

- Binomial X with parameter n, p <br/>
  → Models <span style="color:red">**the number of success**</span> in a given number of <span style="color:red">**independent trials**</span>.

  - n번의 동전 던지기를 하고, p의 확률로 앞면(success)이 나온다고 하자. 그럼 여기서, k번의 앞면이 나올 확률을 어떻게 구할까?

    ![image-20210909161349852](/Users/yunpildo/Library/Application Support/typora-user-images/image-20210909161349852.png)

    → 요렇게 나오게 된다!
    $$
    \begin{bmatrix}
    n \\
    k
    \end{bmatrix}
    = \frac {n!} {k!(n-k)!}
    $$
    → 괄호 표시가 다른건 내가 익숙하지 않아서다.<br/>

- Gemetric X with parameter p

  - 무한히 많은 independent한 시도 끝에(k번의 시도) 성공하는 확률

  $$
  px(k) = (1-p)^{k-1} p
  $$

  ![image-20210909162412919](/Users/yunpildo/Library/Application Support/typora-user-images/image-20210909162412919.png)

  - 그림처럼 모델이 성공을 할 때까지 기다리는 양상을 보인다.<br/>

- 

## Summarizing random variables : Expectation and Variance

- Expectation(기대값)의 표현 : 

  1. Expectation은 RV에 대한 평균이라고 볼 수 있고, 흔히 아는 산술 평균이 아닌 확률 평균이다.

  2. 확률 평균 : 각각의 변수의 확률을 고려한 평균

  3. 수식 표현<br/>
     $$
     E[X] = \sum_{x} {xpx(x)}
     $$
     → 각각의 변수의 확률을 고려했다고 했으니까, </br>

     → px(x) : relative frequency of value x 
     $$
     px(x) = \frac {x} {total~trails}
     $$

  4. $$
     \sum_x {p(x)} = 1
     $$

  5. 

  <br/>

- Properties of Expectation

  1. if X >= 0, E[X] >= 0
  2. if a <= X <= b, a <= E[X] <= b
  3. For a constant c, E[c] = c <br/>

- For a rv X, Y = g(X) is also rv. <br/>
  → 앞서 말한 것 처럼, 동일한 sample space에서 여러 개의 rv가 있을 수 있음 <br/>
  ![image-20210909164427147](/Users/yunpildo/Library/Application Support/typora-user-images/image-20210909164427147.png)

  - 그렇다면 이 식은 어떠한 특성이 적용이 됨

    1. $$
       E[Y] = E[g(X)] = \sum_x {g(x)px(x)}
       $$

    2. $$
       E[aX + b] = aE[X] + b
       $$

- Variance : measures <span style="color:red">how much the spread of a PMF is</span>

  - 동일한 expectation을 갖더라도 서로 다른 '형태'를 띄고 있을 수 있다. <br/>
    → 형태 : spread pattern

  - $$
    var[X] = E[ {(X-μ)}^2]
    $$

  - $$
    σx = \sqrt{[X]}
    $$

    <br/>→ Standard Deviation (표준 편차)

  - Variance : Useful property

    1. $$
       var[X] = E[X^2] - {(E[X])}^2
       $$

       $$
       var[X] = E[X^2 - 2μ + μ^2] = E[X^2] - 2μE[X] + μ^2 \\
       = E[X^2] - μ^2 = E[X^2] - {(E[X])}^2
       $$

       

    2. $$
       Y = X + b \\, var[Y] = var[X]
       $$

       → Additional additive term does not affect to <span style="color:red">**spread pattern.**</span>

    3. $$
       Y = aX\\,  var[Y] = a^2var[X]
       $$

       $$
       var[Y] = E[a^2X^2] - (aE[X])^2 = a^2E[X^2] - a^2(E[X])^2 \\= a^2var[X]
       $$

       

  - Example) Variance of a Bernoulli rv (p) <br/>
    $$
    μ = E[X] = 1*P + 0*(1-p) = p \\
    E[X^2] = 1^2*p + 0^2*(1-p) = p \\
    var[X] = E[X^2] - μ^2 = p - p^2 = p(1-p)
    $$
    

## (Functions of) Multiple random variables

## Conditioning for random variables

## Independence for random variables
