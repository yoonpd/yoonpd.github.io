---
title: "Random Variables (6)"

categories:
  - Probability and Random Variables

toc: true
toc_sticky: true
---

# Radnom Variable (6)

## Derived Distribution: *Y = g(X)*

- Given the PDF of X, What is the PDF of *Y = g(X)* 에 관한 문제이다. <br>
  → *g(X)* 는  Y = X, Y = X + 1, Y = X^2 등 여러 경우가 있다.

- 그럼 어떨 때 쉽고 어떨 때 어려울까?

  1. ### Easy Case 

     - #### Discrete 

       - 간단하게 case-by-case 로 생각하면 된다.
       - 예시를 통해 한 번 알아보자. <br>![스크린샷 2021-10-12 오후 2 17 49](https://user-images.githubusercontent.com/37065429/136903608-2514afc8-9c00-45ff-be64-eb04ef519a0a.png)
         <br>
         → 어떤 함수 g로 인해서 *Y = g(X)* 일 때, Y의 확률 p_Y(y) = P(g(X) = y)일 것이고 이는 y에 값에 따른 x의 값을 모두 합해주면 된다. <br>![스크린샷 2021-10-12 오후 2 19 24](https://user-images.githubusercontent.com/37065429/136903654-b3e95368-ccd9-4525-b627-187c8044d67c.png)
         <br>
         → g(X)의 동작 과정이 다음과 같을 때, y값은 3과 4일 것이고, 앞서 말한 것과 같이 case-by-case로 생각한다면<br>![스크린샷 2021-10-12 오후 2 20 31](https://user-images.githubusercontent.com/37065429/136903693-70131e94-9bee-40d0-babf-3a6cd45474f8.png) 
         <br>
         → 확률은 다음과 같이 구할 수 있다.💩  <br>

     - #### Linear : Y = aX + b, a != 0, X : Continuous

       - a의 값이 양수인지 음수인지를 통해 쉽게 계산을 할 수 있다.

         1. a > 0 <br>

            ![스크린샷 2021-10-12 오후 2 27 27](https://user-images.githubusercontent.com/37065429/136903716-c9aa1954-2bdf-46ae-aeea-6f607b059945.png)
            )
         
         2. a < 0<br>![스크린샷 2021-10-12 오후 2 27 53](https://user-images.githubusercontent.com/37065429/136903753-77979f7b-dd82-47d8-b327-3de716a3a51e.png)
            )
         
         3. 그럼 이걸 합쳐보자. <br><img width="247" alt="스크린샷 2021-10-12 오후 2 29 51" src="https://user-images.githubusercontent.com/37065429/136903777-0bb5d919-1116-4999-891b-a2097672aa82.png">
            <br>
            → a는 0이 될 수 없기에 가능하다. <br>
  
     - #### Linear : Y = aX + b, when X is **exponential**
  
       - 앞서 구한 방식으로 쉽게 구해질 수 있다. <br>![스크린샷 2021-10-12 오후 2 32 29](https://user-images.githubusercontent.com/37065429/136903801-ade462a2-50f6-42bc-8c19-09fdd604a847.png)
         <br>
         → 그렇다면, Y 또한 Exponential일까? <br>
         → 일반적으로 그렇지 않고, b = 0 and a >0일 때, Y는 λ/a를 파라미터로 갖는 Exponential RV가 된다. <br>
  
     - #### Linear : Y = aX + b, when X is normal
  
       - Normal을 베웠을 때, 우리(나)는 Linear transform은 normality를 보존한다는 것을 배웠다. <br>
         ![스크린샷 2021-10-12 오후 2 51 04](https://user-images.githubusercontent.com/37065429/136903829-6e8c49b1-b601-4b6e-a29f-240012d0d86c.png)
       - 근데, 증명은 안했다. 이제 해보자. <br>![스크린샷 2021-10-12 오후 2 51 29](https://user-images.githubusercontent.com/37065429/136903859-35cbd286-35bd-4c3f-acf6-6e8ad8f99512.png)
          <br>
         → 최종적으로 나온 값에서 fX와 fY를 비교해보면, μ자리가 (b+aμ)로 σ는 aσ로 바뀐 것을 보면 된다.💩 <br>
         → 그럼 X를 Linear Transform한 Y의 결과는 N(aμ+b, (aσ)^2)이 된다! <br>
  
  2. ### Sometimes Easy and Sometimes Difficult Case
  
     - #### Y = g(X), X : Continuous
  
       - 말 그대로 쉽기도하고 어렵기도 하다. 하지만 일반적인 원리가 있으니 이 것을 알아보자.
  
         1. Step : Find the CDF of Y : <br>![스크린샷 2021-10-12 오후 3 03 46](https://user-images.githubusercontent.com/37065429/136903888-aef1a32f-63ef-4739-8822-349fd28ac6b2.png)
         2. Step : Differentiate : <br>![스크린샷 2021-10-12 오후 3 04 01](https://user-images.githubusercontent.com/37065429/136903919-2321a348-02e9-49ba-9a85-95701620b435.png)
  
       - 예제 몇 개를 보면서 이 원리를 적용해보자. <br>
         ![스크린샷 2021-10-12 오후 3 04 35](https://user-images.githubusercontent.com/37065429/136903964-08d4958b-7659-4168-95f2-ffed521795a7.png) <br>
         ![스크린샷 2021-10-12 오후 3 04 49](https://user-images.githubusercontent.com/37065429/136904021-0580b217-01ed-42e4-b727-cf27305b1e77.png)<br>
         
         → *g(X)*에 따라, <span style="color:red">Y의 범위가 한정됨</span>을 확인하자.
  
         <br>
  
       

## Derived Distribution: *Z = g(X, Y)*

- 앞서 배운 원리를 사용하면 된다. 예제를 보자! <br>![스크린샷 2021-10-12 오후 3 16 34](https://user-images.githubusercontent.com/37065429/136904086-6cc9f9d8-a04d-40fd-9eec-326a3a802b91.png)
   <br>
  → X와 Y가 uniform하기 때문에, P(X <= z) = P(Y <= z) = z임은 당연하다. <br>
  → 또한, Z = max(X, Y)일 때는 P(X <= z) and P(Y <= z)이고, 이는 P(X <= z, Y <=z) = P(X <= z)P(Y <= z)이다. <br>
  → 독립이니까!!!!!!

- 다음 예제를 살펴보자. <br>

  ![스크린샷 2021-10-12 오후 3 24 55](https://user-images.githubusercontent.com/37065429/136904117-79481e97-3b2b-4639-b4c8-182d2d65860a.png)
  <br>
  ![스크린샷 2021-10-12 오후 3 25 09](https://user-images.githubusercontent.com/37065429/136904172-e5a55952-0996-4554-a8f2-a6ca98ed72a6.png)<br>
  ![스크린샷 2021-10-12 오후 3 25 23](https://user-images.githubusercontent.com/37065429/136904188-96727c91-bc89-4e7f-92d5-0c5474428397.png) <br>
  ![스크린샷 2021-10-12 오후 3 25 34](https://user-images.githubusercontent.com/37065429/136904206-a828e3cc-7728-410d-8a6a-3157f8480559.png)<br>
  
  💩 Sometimes, the problem is tricky, <span style="color:red">which requires careful case-by-case handling!!</span> <br>

## Derived distribution of *Z = X + Y*

### Function of multiple RVs

#### - Z = X + Y, X ㅛ Y (1)

- Sum of two independent RVs

- 매우 기본적인 예시이지만 사용되는 경우가 매우 많다. <br>

  ![스크린샷 2021-10-14 오전 10 55 42](https://user-images.githubusercontent.com/37065429/137258830-32d0c7ea-5c9f-4226-9618-0854f82cb075.png) <br>
  → pZ(z)는 the PMFs of X and Y의 Convolution이라고 할 수 있고, <br>
  → Convolution은 두 개의 인풋(pX, pY)이 <span style="color:orange">마지막 항</span> 이라는 함수를 통해 pZ가 됨을 의미한다. <br>
  → 여기서 중요한 점은, 이 **Convolution이 무엇을 의미하는지**이다. 이제 알아보자. <br>

#### - Z = X + Y, X ㅛ Y (2) <br>

![스크린샷 2021-10-14 오전 11 04 45](https://user-images.githubusercontent.com/37065429/137258850-8dd3224a-910d-4986-9f84-ac882130ff2a.png)

- Interpretation for a given z :

  1. Horizontally Flip the PMF of Y → **pY(-x)**
  2. Put it underneath the PMF of X
  3. Right-shift the flipped PMF by z → **pY(-x+z)**
  4. Do convolution!

- 실제 예제를 통해 확인해보자.

  - pX와 pY가 다음과 같이 주어졌다.<br>![스크린샷 2021-10-14 오전 11 06 54](https://user-images.githubusercontent.com/37065429/137258868-5efb65f9-0860-43e3-970d-b9a9b3b9c2a9.png)
    <br>

    1. Horizontally Flip! And 2.  Put it underneath the PMF of X<br>
       ![스크린샷 2021-10-14 오전 11 07 37](https://user-images.githubusercontent.com/37065429/137258884-c40862a6-b9af-4617-8340-55cceaeb4e32.png)

    3.  Right-shift the flipped PMF by z(=3)<br>
       ![스크린샷 2021-10-14 오전 11 08 35](https://user-images.githubusercontent.com/37065429/137258897-79acf7d2-3e2b-4ef9-8fb6-a696a04659c9.png)
    4. Do convolution! <br><img width="360" alt="스크린샷 2021-10-14 오전 11 10 20" src="https://user-images.githubusercontent.com/37065429/137258917-6fbc18c2-b795-490a-abff-1dce8384ae87.png">
       <br>
       → 이 과정을 원하는 모든 z에 대해서 수행하면 된다.

#### - Y = X + Y, X ㅛ Y, Continuous

- Same logic as the discrete case. <br>
  ![스크린샷 2021-10-14 오전 11 15 40](https://user-images.githubusercontent.com/37065429/137258935-b6309d99-d305-40a5-9cd5-001d298b0ea6.png)
- 그림으로 보면 더 쉽게 이해가 간다. 그리고 계산 순서도 같다! 단지, 넓이를 구할 뿐! <br>
  ![스크린샷 2021-10-14 오전 11 16 23](https://user-images.githubusercontent.com/37065429/137258950-d98e9baa-8a2b-49f0-8daf-a214d8ad32b7.png)
- 예제를 보자~
  - X와 Y가 U[0, 1]이라고 하고, X ㅛ Y라고 헤보자.
  - 그럼, the PDF of Z = X + Y는 어떠한 형태를 보일까?
  - 쉽게 생각해보자. 💩
    1. Flip : Y는 0~1 값을 가졌으니, -1 ~ 0의 값을 갖게 된다.
    2. Put under X : 처음에는 겹치는 부분이 하나도 없을 것이다.
    3. PDF of Z는 0의 값을 가질 것이다.
    4. 조금씩 옮기다보면 점점 겹치는 영역이 많아지고
    5. 어느 순간 완전히 겹쳤다가 점점 겹치는 영역이 줄어들어 최종적으로는 완전히 벗어날 것이다.
    6. 그래서 형태는 다음과 같다. <br>
       ![스크린샷 2021-10-14 오전 11 26 30](https://user-images.githubusercontent.com/37065429/137258978-e088d8ee-8e8d-4cf8-9397-e9992e9ea42f.png)

<br>

#### - Z = X + Y, X ㅛ Y, Normal (1)

- 매우 특별하고 유용한 case.
- 두 개의 Normal RVs의 합(Z)은 다음과 같이 나타낼 수 있다. <br>![스크린샷 2021-10-14 오전 11 29 44](https://user-images.githubusercontent.com/37065429/137258994-a3b9df28-3ff8-445b-ad37-4e5e9c77a204.png)
  <br>→ Extension. <span style="color:red">**The sum of finitely many independent normals is also normal .**</span>

#### - Z = X + Y, X ㅛ Y, Normal (2)

- 증명(?)을 해보자. <br><img width="758" alt="스크린샷 2021-10-14 오전 11 38 24" src="https://user-images.githubusercontent.com/37065429/137259015-0a725df1-5ec0-4add-b827-bf1f4409c829.png">

<br>

## Covariance: Degree of dependence between two RVs

### Making a Metric of Dependence Degree

- Goal : Given two RVs X and Y, assign some number that quantifies the degree of their dependence. <br>
  → feeling😢 / weather⛈, university ranking / annual salary, etc... <br>
  → Covariance : 두 개 또는 그 이상의 랜덤 변수에 대한 의존성을 의미 <br>
- Requirements
  1. Increase(reps. decrease) as they become more(resp. less) dependent. 0 when they are independent
  2. Shows the 'direction' of dependence by + and -.
  3. Always bounded by some bumber (i.e., dimensionless metric). For example, [-1, 1] <br>
     

### OK. Let's design!

- Simple Example <br>![스크린샷 2021-10-14 오후 3 01 08](https://user-images.githubusercontent.com/37065429/137264073-841665ae-4518-46ef-b7f5-871cef880385.png)<br>
- Dependent : 
  1. Positive : if X ↑, Y ↑
  2. Negative : if X ↑, Y ↓
- 그럼, Covariance를 E[XY]로 표현해보자.
  - E[XY] = E[X] E[Y] = 0 when X ㅛ Y
  - More data points (thus increase) when xy > 0 (both positive or negative)
    → 서로 다르면 감소함, 즉 우리가 원하던 대로임
  -  &#124; E[XY]  &#124; also quantifies the amount of spread. <br>![스크린샷 2021-10-14 오후 3 14 38](https://user-images.githubusercontent.com/37065429/137264097-202a0f95-4c4a-48d4-b45d-66ac82d6b96b.png)<br>

#### What if μx != 0 and μy != 0

- <span style="color:red">**Solution : Centering**</span> <br>
  → ![스크린샷 2021-10-14 오후 3 16 34](https://user-images.githubusercontent.com/37065429/137264125-1b992b55-7529-43f9-826d-87467baba90a.png)
- 이를 수식으로 사용해서 앞서 우리가 만든 공식에 대입해본다면 <br><img width="685" alt="스크린샷 2021-10-14 오후 3 18 33" src="https://user-images.githubusercontent.com/37065429/137264139-3d6867bd-8509-48fe-8713-2fc6243cc7be.png">
- X ㅛ Y일 때는 con(X, Y) = 0이 나온다. 즉, 독립이니까 상관이 없다는 뜻이다.
- 그럼 반대로, cov(X, Y) = 0이라해서 X ㅛ Y일까? → 항상 그렇지 않다.
- 그래서 우리는 cov(X, Y) = 0을 X와 Y가 uncorrelated하다고 부르기로 했다.

<br>

#### Example : cover(X, Y) = 0, but not independent.

- ![스크린샷 2021-10-14 오후 3 22 52](https://user-images.githubusercontent.com/37065429/137264156-439ba48c-02a3-42db-942e-546abf86f0cf.png)<br>
- 이렇게 된다면, E[X] = E[Y] = 0이 되고, 자연스럽게 E[XY] = 0이 되어 cov(X, Y) = 0이 된다.
- 그럼, X와 Y가 독립인가? 아니다. X(Y)가 주어졌을 때 Y(X)를 알 수 있다. 즉, 독립이 아니다.<br>![스크린샷 2021-10-14 오후 3 24 20](https://user-images.githubusercontent.com/37065429/137264178-8ec1ac1d-df5a-4077-bfba-3ee4bb720842.png)<br>

### Some Properties of COV

![스크린샷 2021-10-14 오후 3 26 41](https://user-images.githubusercontent.com/37065429/137264192-1925f2f1-0426-469a-8f79-d555465d9e20.png)<br>

### Example : The hat problem Using Bern RV

![스크린샷 2021-10-14 오후 3 31 23](https://user-images.githubusercontent.com/37065429/137264208-de494a52-d479-43c7-ad9d-a83f309c0ebb.png)<br>
→ 앞에서 정리한 속성을 갖고 variance를 구할 수 있다.



<br>

## Correlation Coefficient

- 앞서 배운 Covariance와 비슷한 내용이다. 그럼 무엇이 다를까?

- [Covariance를 만들기 위한 우리들의 요구사항](#making-a-metric-of-dependence-degree)#Making a Metric of Dependence Degree 을 보면 어디서 다른지 알 수 있다. <br>

  → R1과 R2는 이미 만족을 하고 있다. <br>
  → R3....이게 문제인데 어떻게 만족해야할까?

### Bounding the metric : Correlation Coefficient

- Normalization을 한다면 어떻게 펼쳐져있든, 일정 범위로 맞춰줄 수 있다.

- 그럼 무엇을 기준으로 해야할까?<br>

  ![스크린샷 2021-10-27 오전 9 56 29](https://user-images.githubusercontent.com/37065429/138983213-0e93eaf2-f2c2-4c25-8046-3cec22536928.png)<br>→ σ로 하면 된다.<br>
  → 만약, 분자가 제곱의 형태를 갖는다면 → var로 하면 된다.

- 식을 보자.<br>

  ![스크린샷 2021-10-27 오전 9 56 48](https://user-images.githubusercontent.com/37065429/138983223-8aed97a8-f5ec-4538-83bb-f987b9770e89.png)<br>
  <br>

### Theorem. 

- 그럼, coef가 의미하는 것은 무엇일까?
  1. **-1 <= ρ <= 1**
  2. **&#124; ρ &#124; = 1 ⇔ X - μX = c(Y - μY)** for some constant c (c > 0 when ρ = 1 and c < 0 when ρ = -1) <br>
     → In other words, <span style="color:red">**Linear relation meaning VERY RELATED.**</span><br>

### Proof. 1

![스크린샷 2021-10-27 오전 10 08 30](https://user-images.githubusercontent.com/37065429/138983237-0e94773e-172d-4e68-93c6-35a32551a564.png)

<br>

### Proof. 2

![스크린샷 2021-10-27 오전 10 09 15](https://user-images.githubusercontent.com/37065429/138983252-48cd8136-8d8c-4300-93de-aff9ce1d21c4.png)<br>

