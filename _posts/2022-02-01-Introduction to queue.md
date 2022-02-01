---
title: "Introduction to Queue"

categories:
  - Lyapunov Optimization
toc: true
toc_sticky: true
---

# Introduction Queue

- 이 포스트는 동적 최적화의 기법 중 하나인 Lyapunov 최적화 기법에 대해 다룬다.

<br>

# What is Queue?

- Queue는 무엇이고, 어떻게 표현이 될까를 생각해보자.

<br>

## Queue Expression

- 네트워크에서 Queue는 실제적인 환경을 표현하기 위해 사용된다.

- 여기서 네트워크는 timeslot마다  <span style="color:blue">유입되는 일의 양</span>과 <span style="color:red">이 일을 처리해서 보내는 라우터</span>가 있다고 해보자.<br>
  → 각각을 <span style="color:blue">a(t)</span>와 <span style="color:red">b(t)</span>로 notation을 정의해보자.

- 우리가 정의한대로 한다면 다음과 같이 Queue를 표현할 수 있다.<br><img width="402" alt="스크린샷 2022-02-01 오후 9 47 23" src="https://user-images.githubusercontent.com/37065429/151971012-1229e4ff-5db6-4227-8f7c-063dbad584c8.png">

  <span style="color:gray">→ a(t) : the amount of new work that arrives at timeslot t.<br>
  → b(t) : the amount of work that the router of the queue can process on timslot t.</span>

- a(t)와 b(t)가 "stochastic"하다고 하면, 어쩌면 모든 네트워크를 대변할 수 있을 것이다.<br>→ 그렇다면, <span style="color:pink">a(t)와 b(t)가 어떤 RV로 모델링 되어야 한다는 것을 의미한다.</span><br>→ 즉, <span style="color:pink">미래의 상황까지 a(t)와 b(t)의 정보를 모두 알고 있다는 것을 의미한다.</span>

- 위 내용을 그림으로 확인해 보자.<br><img width="541" alt="스크린샷 2022-02-01 오후 9 52 06" src="https://user-images.githubusercontent.com/37065429/151971725-0aa5b8e7-55c0-4d22-bfe8-77c4220a51b1.png"><br>→ 여기서, Q(t)를 backlog라고 하고, 처리되어야 할 일의 양을 의미한다.<br>

  <span style="color:gray">→ Backlog : the amount of work that should be processed.</span><br><br>

# Rate Stability

- b(t)를 우리는 확률적인 값으로 한다고 앞서 말헀다.

- 그럼 b(t)를 실제 일의 처리량이라고 생각해보자. <span style="color:gray">b틸다로 표기할 것인데 특수 문자가 없다 ㅋㅅㅋ</span><br><img width="414" alt="스크린샷 2022-02-01 오후 9 54 38" src="https://user-images.githubusercontent.com/37065429/151972109-cf1af2a9-3b62-4d01-8d91-1e0734404aeb.png"><br>→ 실제 처리되는 일의 양은 확률 적인 값보다 낮을 것이기 때문에 max를 제외하고 화살표 아래와 같이 표현할 수 있다.

- 여기서, 식의 확장을 위해 두 개의 timeslot인 t1과 t2를 고려해보자.<br><img width="731" alt="스크린샷 2022-02-01 오후 9 58 39" src="https://user-images.githubusercontent.com/37065429/151972736-3255c6a2-e2d6-4f8a-9960-7976a7c8faa8.png"><br>

  → Queue는 시간의 연속에서 처리되는 형태이기 때문에, 화살표 왼쪽과 같이 표현을 할 수 있다. <br>

  - 먼저, 화살표 우측 상단의 식을 확인해보자.<br>
    → t2=t, t1=0인 상황에 대한 식으로, 단순히 좌측 식에서 t로 나눈 상황을 의미한다. (t2=t가 0이 아니기 때문에 가능)
  - 우측 하단의 식은 위와 동일하지만, b틸다가 아닌 b가 사용된 것을 알 수 있고, 이로 인해서 부등호가 적용된다.<br><br>

## Definition

- Rate stability는 다음과 같은 상황을 지칭한다.<br><img width="580" alt="스크린샷 2022-02-01 오후 10 13 09" src="https://user-images.githubusercontent.com/37065429/151974799-44542648-6940-44b6-b520-874120d78fd2.png"><br>

  <span style="color:gray">→ 앞서 본 식에서 limit을 취했을 때를 가정한 것이다.<br>→ 위 식을 해석해보자면, 시간이 계속해서 흐를수록 쌓이는 양이 없이 처리를 잘 한다는 뜻이다.(큐가 수렴한다는 뜻이다.)</span>

- 저걸 만족하려면 어떻게 해야될까? 다음을 먼저 정의해보자.

  1. <span style="color:blue">들어오는 일의 양</span>의 수렴 값 → **a**<br><img width="376" alt="스크린샷 2022-02-01 오후 10 21 52" src="https://user-images.githubusercontent.com/37065429/151976097-8d285cc1-8fc0-473d-8782-8e57a2d3838c.png">
  2. <span style="color:red">처리될 수 있는 일의 양</span>의 수렴 값 → **b**<br><img width="378" alt="스크린샷 2022-02-01 오후 10 22 32" src="https://user-images.githubusercontent.com/37065429/151976185-ac94766f-3b4f-4577-96f4-0cbe697bf800.png">
  3. 편의 상 각각을 **a**와 **b**로 notation을 정의하겠다.

- 그럼, a <= b를 만족하기만 한다면 시간이 계속 지났을 때 큐는 0으로 수렴하게 될 것이다!<br>
  <span style="color:gray">→ a > b 라고 한다면, a - b로 큐가 수렴되게 될 것이다. </span><br>

<br>

# Example

- 야무진 예제를 살펴보자.<br><img width="214" alt="스크린샷 2022-02-01 오후 10 38 12" src="https://user-images.githubusercontent.com/37065429/151978426-c14888d7-08ef-4a32-b0e5-ed6e387bdf41.png">
  1. 모든 패킷은 고정된 길이를 갖고 각 Queue에 입력으로 들어온다.
  2. 라우터에 할당된 Queue는 한 슬롯에서 하나의 패킷만을 처리할 수 있다.
  3. 매 슬롯에서, 우리는 어떤 Queue로 서비스 해야할지 골라야 한다. (한 슬롯에서 2개씩)

- <span style="color:pink">Q. Design **a router allocation algorithm** to make all queues **to be rate stable** when arrical rates are given as follows.</span>

- 자 그러면 as follows를 보자! <br>
  → 여기서 사용되는 a는 각 Queue로 유입의 수렴 값(a^av)을 의미한다.

- 처리량(b(t))는 다음과 같이 정의된다. <br><img width="311" alt="스크린샷 2022-02-01 오후 10 43 44" src="https://user-images.githubusercontent.com/37065429/151979329-f3d23155-e88d-482d-b2f7-e4d295118460.png"><br><span style="color:gray">→ 단순히 위 조건 중 (2)번을 의미한다.</span>

  <br>

## 1. (a1, a2, a3) = (0.5, 0.5, 0.9)

- 각 큐가 선택된 확률이 (0.5, 0.5, 0.9)라고 이해해도 괜찮다. <br><span style="color:gray">→ Law of large number 때문이고, 각 큐로의 유입이 1이라고 해석해도 괜찮기 때문이다.</span>
- 그러면 큐가 서비스할 확률을 한 번 살펴보자. <span style="color:gray">(문제에서 정의해준다.)</span>
  1. 0.5의 확률로 (0, 1, 1)
  2. 0.5의 확률로 (1, 0, 1)
- 위의 확률이 주어졌을 때, Law of large number에 따라 **b1, b2, b3가 어떻게 수렴**될지 생각해보자.
  1. **b1** : 두 개의 choice에서 0.5의 확률만을 가지니, **b1 = 0.5**
  2. **b2** : 두 개의 choice에서 0.5의 확률만을 가지니, **b2 = 0.5**
  3. **b3** : 두 개의 choice에서 모두 있으니, **b3 = 1**
- 자, 수렴 값을 모두 찾았으니 이제 rate stable한지 확인을 해보면, <br><img width="187" alt="스크린샷 2022-02-01 오후 10 53 38" src="https://user-images.githubusercontent.com/37065429/151981081-0580ca3b-4b7f-472c-b8dc-e2a17a7bf499.png"><br>→ 모두 만족하는 것을 알 수 있다!<br>
  → <span style="color:red">따라서, 위와 같이 확률적 모델링을 한 네트워크 환경은 rate stable하다.</span>

