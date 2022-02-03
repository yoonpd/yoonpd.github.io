---
title: "Generalized inequality"

categories:
  - Convex Optimization
toc: true
toc_sticky: true
---

><img width="170" alt="스크린샷 2022-02-03 오후 12 51 44" src="https://user-images.githubusercontent.com/37065429/152278442-3259d054-5ae5-4754-ac20-4eb90dbd8ed1.png"><br>
>Convex Optimization 포스트는 위 책을 참고해서 작성했습니다.<br>
>이 외에도 참고한 사이트는 다음과 같습니다. <br>저한테는 어려워서 이해한 만큼만 작성했습니다....<br>
>https://convex-optimization-for-all.github.io/ (모두를 위한 컨벡스 최적화)

# Generalized Inequality

- 우리는 정수 1과 2 중 누가 큰지 알고 있다.<span style="color:gray">*1인가?*</span>
- 그럼 n-차원의 공간에서는 어떤 점이 다른 점보다 어떻게 크다고 말할 수 있을까?<br>
  → 이를 할 수 있도록 하는 것이 Generalized inequality라고 한다.
- 그럼 첫 번째로 proper cone에 대해서 알아보자.

<br>

## Proper cone

- proper cone은 다음과 같은 세 가지 조건을 만족할 때 성립하는 cone이다.<br>
  <img width="500" alt="스크린샷 2022-01-31 오후 11 59 31" src="https://user-images.githubusercontent.com/37065429/151816767-0dad69c0-9689-4ab3-a68f-1bab52577464.png"><br>→ 마지막 조건은 원점을 지나되, <span style="color:red">직선</span>이 만들어 지지 않아야 한다는 것을 의미한다. <br><img width="283" alt="스크린샷 2022-02-01 오전 12 01 16" src="https://user-images.githubusercontent.com/37065429/151817080-e48ad260-c8ad-4ec8-b9a6-da09c7fd1106.png"><br>

  → 즉, 이 상황이 나오면 안 된다는 것이다!<br>
  <br>

## Definition

- 여기서는 "작다"의 개념이 아닌 <span style="color:red">"앞서 온다"</span>라는 개념을 사용한다.<br><img width="656" alt="스크린샷 2022-02-01 오전 12 14 13" src="https://user-images.githubusercontent.com/37065429/151819424-f955147b-fa8e-4ca5-ba86-45d28150001a.png"><br>→ 부등호 밑에 첨자로 K가 있는 것을 알 수 있는데, 이 K가 proper cone일 때 성립하게 된다.<br>
  → 즉, proper cone K 관점에서<span style="color:gray">(in respect of)</span> x가 y보다 앞서 온다. (검은 점)<br>
  → <span style="color:red">빨간 점</span>은 부등호가 성립하지 않는 것을 확인할 수 있다.

- 또한 중요한 것은, 부등호<span style="color:gray">(<)</span>가 성립하지 않는다고 해서 그 반대<span style="color:gray">(>=)</span>가 성립하지 않는다는 것이다.

<br>

## Minimum

- 다음으로 배울 내용은 minimum이다.

- Minimum의 정의는 다음과 같다.

  > 어떤 집합 S에 속해 있는 **어떤 점 x**와 **모든 점 y**에 대해서, **항상 x가 y보다 앞서 온다면** 이 x를 minimum이라고 한다.<br>
  > <img width="402" alt="스크린샷 2022-02-01 오전 12 21 29" src="https://user-images.githubusercontent.com/37065429/151820693-e6dd5e65-90ea-4d3f-8772-d4bf975aa128.png">

- 2차원 평면에서 생각해본다면, 어떤 집합에서 어떤 점을 기준으로 우측 상단으로만 집합의 원소들이 있다면 그 점이 minimum이다.<br>
  <img width="282" alt="스크린샷 2022-02-01 오전 12 23 36" src="https://user-images.githubusercontent.com/37065429/151821055-f0fde935-d486-44dc-ba6d-c8e5c755dad8.png"><br>

<br>

## Minimal

- Minimum과 정의가 비슷하지만 조건이 살짝 다르다.

- Minimal의 정의는 다음과 같다.

  > 어떤 집합 S에 속해 있는 **어떤 점 x**와 **모든 점 y**에 대해서, **y가 x보다 앞서 오는 상황이 x=y일 때만 발생**한다면, x 점을 minimal이라고 한다.<br>
  > <img width="464" alt="스크린샷 2022-02-01 오전 12 27 44" src="https://user-images.githubusercontent.com/37065429/151821768-6baf9612-3fba-4d1d-831b-2cc083ad3690.png">

- 2차원 평면에서 본다면, x 점을 기준으로 좌측 하단에 집합 S의 점이 없을 때, x를 minimal이라고 한다.<br>
  ![image](https://user-images.githubusercontent.com/37065429/151821970-d0c0cfbc-4fc3-4b5b-8e2b-3ab384ac2583.png)<br><br>

# Theorem

## Separating hyperplane theorem

- 두 집합 C와 D가 있을 때, 그리고 C와 D가 non-empty disjoint convex set이라고 할 때, C와 D를 가르는 hyperplane이 존재한다는 이론이다.<br><img width="673" alt="스크린샷 2022-02-01 오전 12 31 39" src="https://user-images.githubusercontent.com/37065429/151822433-5d6fadf5-1fb2-4992-b53e-6eeaa59aec14.png"><br>→ 왼쪽 그림이 대표적인 예를 의미하고, hyperplane이 존재한다고 해서, C와 D가 non-empty disjoint convex set이 아닐 수 있다. <span style="color:gray">옆의 그림이 그 대표적인 예이다.</span><br><br>

## Supporting hyperplane theorem

- non-empty convex set C가 있고, boundary에 어떤 점 x0가 있다고 할 때, x0에서 **항상 supporting hyperplane이 존재**한다는 이론이다.

<br>

# Dual Generalized Inequality

## Dual Cone

- 먼저, Dual cone을 정의해보자.

- 이는 Cone으로부터 정의가 되고, 다음과 같은 조건을 만족하게 된다.<br>
  <img width="246" alt="스크린샷 2022-02-01 오전 12 52 17" src="https://user-images.githubusercontent.com/37065429/151826670-f64ae130-174f-4db4-9020-d3a5aaf5174e.png"><br>
  → 내적의 정의를 생각해본다면, 사이각이 -90~90가 될 때를 의미한다. K는 cone을 의미한다.<br>
  <img width="575" alt="스크린샷 2022-02-01 오전 12 53 40" src="https://user-images.githubusercontent.com/37065429/151826914-c9127b13-287f-41d9-aad6-796bc4a0795d.png">

- 예제를 몇 개 살펴보자면, <br>
  <img width="298" alt="스크린샷 2022-02-01 오전 12 54 29" src="https://user-images.githubusercontent.com/37065429/151827069-388b6de8-fbe7-4963-aa5c-42c69432a1d4.png"><br>

  → 각 예시들은 self dual cone으로, cone과 dual cone이 동일한 형태임을 의미한다. <br>→ 마지막 예제는 Norm cone이다. 그림을 보면 확실하게 이해할 수 있다.<br><img width="438" alt="스크린샷 2022-02-01 오전 12 55 07" src="https://user-images.githubusercontent.com/37065429/151827187-815db85c-03c1-425c-a618-a3a100bb7371.png">

- 이 놈이 왜 중요한지를 보면, cone이 convex가 아니더라도 dual cone은 convex가 된다.

<br>

## Definition

- 정의라기보다는 확장된 개념으로 이해를 하면 편하다.<br>
  <img width="618" alt="스크린샷 2022-02-01 오전 12 57 54" src="https://user-images.githubusercontent.com/37065429/151827698-d6e36fa1-4ac0-4f8c-9feb-f580d7672f12.png">
- 이에 대한 속성을 살펴보자면, lambda라는 하나의 값을 정의해서 확인할 수 있다.<br>
  <img width="294" alt="스크린샷 2022-02-01 오전 12 58 59" src="https://user-images.githubusercontent.com/37065429/151827905-eb9c150c-d81f-4535-9597-a4dd0ba506b5.png"><br><br>

## Mimimum

- 정의를 바로 확인하자.<br><img width="622" alt="스크린샷 2022-02-01 오전 1 03 55" src="https://user-images.githubusercontent.com/37065429/151828785-5da5e3bd-be56-465c-b010-e1e29fb357b6.png">
- 2차원 평면을 생각한다면, 쉽게 이해할 수 있다...(?)<br>
  <img width="660" alt="스크린샷 2022-02-01 오전 1 05 00" src="https://user-images.githubusercontent.com/37065429/151828949-3ce38647-a7b3-48f6-ae1c-0ce2cbd93a05.png"><br><br>

## Minimal

- 요놈도 정의를 바로 확인하자. <br><img width="706" alt="스크린샷 2022-02-01 오전 1 05 46" src="https://user-images.githubusercontent.com/37065429/151829076-23d18bb9-ac6d-406d-925a-e46188f099f2.png"><br>

<br>

# Example

- 실제 예제를 한 번 보면서 optimization problem에서의 적용법을 보자.<br><img width="529" alt="스크린샷 2022-02-01 오전 1 06 58" src="https://user-images.githubusercontent.com/37065429/151829281-3bedc1e8-8ee0-4415-9eb8-6fe8ded12ea2.png"><br>→ P를 생산 방법의 집합이라고 하면, 집합의 원소를 구성하는 벡터는 x로 연료(fuel)와 노동(labor)이라고 해보자.<br>
  → 여기서, 자원 가격을 lambda라고 할 때, <br>
  <img width="282" alt="스크린샷 2022-02-01 오전 1 08 29" src="https://user-images.githubusercontent.com/37065429/151829547-2898066c-c71f-4bad-b5d4-66bf3d8f8fe5.png"><br>
  → 그럼 생산 방법의 가격은 위와 같이 정의될 수 있다. <br>
  → 가격을 최소화 하는 방법을 minimum을 찾는 것이라 할 수 있고, 최선의 방법을 minimal이라고 할 수 있게 된다.<br>
  → 따라서, x1, x2, x3, x4는 minimal이 될 수 있다.

