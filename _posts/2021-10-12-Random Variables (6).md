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
  
  💩 Sometimes, the problem is tricky, <span style="color:red">which requires careful case-by-case handling!!</span>

