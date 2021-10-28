---
title: "Random Variables (7)"

categories:
  - Probability and Random Variables
toc: true
toc_sticky: true
---



# Radnom Variable (7)

# <br>

## Conditional Expectation and law of iterative expectation

### A Special Random Variable

- 우리는 이전에 RV를 입력으로 받는 함수 또한 RV가 됨을 배웠다.
- 간단한 예를 통해 잠깐 보고 가자. <br>![스크린샷 2021-10-28 오후 2 28 07](https://user-images.githubusercontent.com/37065429/139205989-accb5d78-e55e-46d5-879d-18037ebeff9c.png)
  <br>
  → 먼저, Random Variable은 sample space 에서 발생하는 일을 real number로 mapping하는 함수이다. <br>
  → 그러면, Y라는 rv가 y = 0, 1, 2로 매핑하고, 이를 h(y) = y^2을 통과시킨다면? <br>
  → h(y)=0, 1, 4가 될 것이고, h(Y)라는 새로운 rv를 정의할 수 있다.
- 이것을 살짝 바꿔서, expectation 함수를 적용해보자.<br>![스크린샷 2021-10-28 오후 2 30 17](https://user-images.githubusercontent.com/37065429/139206023-7420d46f-5f99-46c5-b9a5-4881377d13aa.png)
  <br>
  → g(y)는 y에 의해 값이 바뀌기에 y에 대한 함수로서 정의할 수 있다. <br>
  → 그럼 g(y)=3, 8, 9의 값으로 mapping하는 새로운 rv g(Y)를 정의할 수 있다. <br>
  → 얘한테 fancy한 이름을 지어주자~💩

<br>

### Conditional Expectation E[X &#124; Y]

- 얘의 이름은 Conditional Expectation이다! <br>![스크린샷 2021-10-28 오후 2 34 54](https://user-images.githubusercontent.com/37065429/139206063-e84d70a5-0607-4711-9f44-95106a3a83c9.png)
  <br>
- 주의해야할 점이 몇가지 있다.
  1. Conditional Expectation is <span style="color:red">**a function of Y.**</span>
  2. Conditional Expectation is <span style="color:red">**a random variable.**</span>
  3. Thus, having a distribution, expectation, variance, all the things that a random variable has.
     <br>

#### - Expectation of Conditional Expectation

- 말장난 같지만 중요한 개념이라고 한다.
- Conditional Expectation이 RV이니까 당연히 Expectation도 존재해야 한다. <br>![스크린샷 2021-10-28 오후 2 40 03](https://user-images.githubusercontent.com/37065429/139206086-c113eb66-3a9d-4e54-91d0-806e2f2230ff.png)
  <br>
  → TET(Total Expectation Theorem)을 사용하여 증명한다.



<br>

#### - Examples and Meaning

- 이전에 봤던 막대 쪼개기 문제와 새로운 문제이다.
  ![스크린샷 2021-10-28 오후 2 45 26](https://user-images.githubusercontent.com/37065429/139206110-eddd21b4-34ed-46b5-bc82-6c2bb69e6520.png)<br>
  → beg. : beginning <br>
  → Revised forecast는 새로운 정보가 주어졌으니 E[X &#124; Y=y]로 수정되어야 한다. <br>
  → 이 때, 당연히  **E[X &#124; Y=y]와  E[X &#124; Y]는 다른 값이다.** <br>
  → 하지만, law of iterated expectations 덕분에 두 개의 Expectation은 같은 값을 가지게 된다. <br>

<br>

#### - Example : Averaging Quiz scores by section

- 직관적으로 지금까지 배운 Law of iterated expectation을 이해해보자.
- 한 수업에 n명의 학생이 있고, i 번째 학생의 퀴즈 점수를 xi라고 하자. <br>![스크린샷 2021-10-28 오후 2 57 50](https://user-images.githubusercontent.com/37065429/139206137-2260891f-b518-4ff1-bc12-aac19cf0f2a0.png)
- 그런 다음에, 학생을 A1, ..., Ak개의 분반으로 나누고, s 분반에 속한 학생의 수를 ns라고 해보자.<br>![스크린샷 2021-10-28 오후 2 58 47](https://user-images.githubusercontent.com/37065429/139206155-e08c8811-7105-43b0-bb44-bc215ef2a2c0.png)
- 그러면 전체 학생의 평균을 어떻게 구할까?
  1. Taking the average m_s of each section
  2. Forming a weighted average <br>![스크린샷 2021-10-28 오후 2 59 38](https://user-images.githubusercontent.com/37065429/139206175-446a0b7b-5f6f-40e7-a411-10592a56aaa5.png)

<br>

- 이거를 우리가 배운 Law of iterated expectation에 적용해보자. (TET 말고~)
- X를 랜덤하게 선택된 학생의 점수, Y는 학생의 분반이라고 해보자. <br>![스크린샷 2021-10-28 오후 3 01 01](https://user-images.githubusercontent.com/37065429/139206193-8905ba82-e54e-44a1-b611-f14db79749c8.png)<br>
  → 💩

<br>

## Conditional variance and law of total variance

### Conditional Variance var[X &#124; Y]

- 배웠던 var[X]와 이제 배울 conditional variance의 notation을 정리해보자.<br>![스크린샷 2021-10-28 오후 3 34 08](https://user-images.githubusercontent.com/37065429/139206217-300d5e34-3b60-4dd2-9ae5-3d9c77299166.png)<br>
  → 앞서 배운 Conditional Expectation과 매우 유사하다.
  
- 그럼, 똑같이 Conditional Variance의 정의를 살펴보자.<br>![스크린샷 2021-10-28 오후 3 34 51](https://user-images.githubusercontent.com/37065429/139206233-16cb1c46-7e09-41e1-9e78-6dfe1facc5c3.png)<br>
  
  → 물론, 이 친구도 조심해야할 점이 있다. 무엇일까? 그거다.
  
  1. Conditional Variance is <span style="color:red">**a function of Y.**</span>
  2. Conditional Variance is <span style="color:red">**a random variable.**</span>
  3. Thus, having a distribution, expectation, variance, all the things that a random variable has.

<br>

### Expectation and Variance of E[X &#124; Y] and var[X &#124; Y]

- 헷갈리지만 Conditional Expectation과 Conditional Variance 둘 다 RV임을 생각한다면 이해할 수 있다.<br>![스크린샷 2021-10-28 오후 3 37 31](https://user-images.githubusercontent.com/37065429/139206265-48cf07c0-df63-4540-966c-80260f25c1fa.png)<br>

<br>

### Law of Total Variance (LTV)

- 먼저, 이 공식을 보고 그 다음에 증명을 해보자.<br>![스크린샷 2021-10-28 오후 3 41 08](https://user-images.githubusercontent.com/37065429/139206274-72bae702-0247-478c-9b85-07f51318a02d.png)<br>
  
- Proof.<br>![스크린샷 2021-10-28 오후 3 41 23](https://user-images.githubusercontent.com/37065429/139206300-5caa0953-0f3a-4116-91ad-53731b0dd5b3.png)
  
  <br>
  (1).  맨 위의 식에 Expectation을 적용한다면, Law of iterated expectation에 의해 식이 도출된다.<br>
  (2).  E[X &#124; Y]를 하나의 RV Z라고 생각한다면, E[Z] = E[Z^2] - (E[Z])^2이니까 쉽게 나올 수 있다. 그리고, Law of iterated expectation을 적용한다. <br>
  (1) + (2) = E[X^2] - (E[X])^2 = var[X]가 되게 된다. <br>

<br>

#### - Example: Averaging Quiz Scores by Section

- LTV가 정확히 무엇을 하는지를 직관적으로 이해해보자.
- 예제는 앞서 들었던 것과 동일한 셋팅이다.
- var[X] = E[ var(X &#124; Y) ] + var[ E(X &#124; Y) ]라고 앞서 표현할 수 있었다.
  - E[ var(X &#124; Y) ] <br>![스크린샷 2021-10-28 오후 3 53 34](https://user-images.githubusercontent.com/37065429/139206330-fc40a614-1473-4baa-9f19-847e93040f4a.png)<br>
    → Weighted average of the section variances. <br>
    → <span style="color:red">**Average score variability within individual sections.**</span> **→ intra-variability.**
  - var[ E(X &#124; Y) ] <br>
    → Variability of the average of the different sections. <br>
    → E[X &#124; Y = s] is average score in section s. <br>
    → <span style="color:blue">**Variability between sections.**</span> **→ inter-variability**<br>

<br>

#### - Example: Stick-breaking

- 이것도 앞서 본 것과 같은 예제다.<br>![스크린샷 2021-10-28 오후 3 59 33](https://user-images.githubusercontent.com/37065429/139206350-32717787-c071-4727-9e54-858838570ab2.png)<br>



<br>

## Random number of sum of random variables

### Sum of a random number of rvs

- 오늘 배운 Law of iterated expectation과 Law of total variance를 종합한 문제를 보자.<br>![스크린샷 2021-10-28 오후 4 09 01](https://user-images.githubusercontent.com/37065429/139206367-bfcca26e-5897-49c9-a7fe-3ebb4c01603b.png)
  <br>
  → N이 고정되어 있는 숫자라면 문제는 쉬워진다. <br>
  → E[Y] = nE[Xi] <br>
  → Var[Y] = nVar[Xi]<br>
  → 하지만 N은 Random이다.💩

- 그러면 공식을 적용해보자.<br>

  ![스크린샷 2021-10-28 오후 4 10 25](https://user-images.githubusercontent.com/37065429/139206384-b066ea14-348e-47a0-9f7a-7d1b5325a46d.png)<br>













