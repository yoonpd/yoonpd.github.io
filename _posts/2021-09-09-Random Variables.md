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
  → For a fixed value x, we can associate an event that a random variable X has the value x, i.e., {w ∈ Ω | X(w) = x} <br/>![image-20210909153336864](/Users/yunpildo/Library/Application Support/typora-user-images/image-20210909153336864.png)<br/>

  → For a discrete random variable X, we call px(x) <span style="color:red">**probability mass function (PMF)**</span>

- 그러면, notation에 대한 예제를 살펴보자!

  - 주사위를 굴렸을 때, sample space Ω = {1,2,3,4,5,6}이다.

  - Random variables X의 대한 정의를 내려보자. 얘는 함수다!<br/>

    > X = 1 for even numbers.
    >
    > X = 0 for odd numbers.

  - 그럼 이 놈에 대한 Notation은 다음과 같이 된다.<br/>

    > Event A1 = {w ∈ Ω | X(w) = 1} = {2, 4, 6} ⊂ Ω
    > → simply, A1 = { X = 1 }
    >
    > Event A2 = {w ∈ Ω | X(w) = 0} = {1, 3, 5} ⊂ Ω
    > → simply, A2 = { X = 0 }

  - A1 = { X = 1 }이 A1 = {w ∈ Ω | X(w) = 1} 이렇게 표현됨 또한 알아야 한다.

  - 그리고 random variable X는 함수이다.  <span style="color:blue">which maps from Ω to R</span> <br/>

## Popular discrete random variables

## Summarizing random variables : Expectation and Variance

## (Functions of) Multiple random variables

## Conditioning for random variables

## Independence for random variables