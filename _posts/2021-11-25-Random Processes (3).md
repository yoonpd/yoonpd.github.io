---
title: "Random Processes (3)"

categories:
  - Probability and Random Variables
toc: true
toc_sticky: true
---

# Random Processes (3)

## Playing with Bern. and Poisson Process

### Description via Inter-arrival Times

- 지금까지 배웠던 Bern.과 Poisson에서 <span style="color:orange">Inter-arrival</span>이라는 조건 하에서 생각해보자.
- Bern.과 Poisson의 간략하고 직관적인 설명을 확인해보자. <br>
  ![스크린샷 2021-11-25 오후 5 05 32](https://user-images.githubusercontent.com/37065429/143402983-86c6a29f-fbe1-44fe-9edd-4f378505647a.png)
- 이번 정리에서부터 쭉 쓰게될 Notation은 다음과 같다. <br>
  ![스크린샷 2021-11-25 오후 5 12 51](https://user-images.githubusercontent.com/37065429/143403971-36313cc2-b34e-4a32-9333-9d548d6cc884.png)<br><br>

#### Example.

- It has been observed that after a rainy day, the number of days until the next rain is <span style="color:orange">Geom(p)</span>, indepedent of the past.
- <span style="color:orange">Question. </span>What is the probability that it rains on both <span style="color:orange">the 5th and the 8th</span> day of the month?
  - 우리가 지금까지 배웠던 the geometric PMF를 사용한다면? 때에 따라 다소 어렵고 복잡한 문제가 될 수도 있다.
  - 그래서 쉽게 생각해보자.
    1. Rainy days is a Bern. process
    2. Each rainy day is independent with probability p.
  - 그럼 결론은? <span style="color:orange">p^2</span>이 된다. 쉽다!

<br>

### Split: Bern. Process

- BP(p)를 두 개의 process로 나눠보자.
- 쉽게 생각해서, q라는 성공 확률을 갖고 성공 시 A 프로세스로 실패 시 B 프로세스로 옮긴다고 해보자. 그림은 다음과 같다.<br>![스크린샷 2021-11-25 오후 5 22 35](https://user-images.githubusercontent.com/37065429/143405223-06047bab-a4ff-4bb6-821f-d464ff781090.png)
- <span style="color:orange">Question. </span>What are the two split processes? <br>
  → BP(pq) and BP(p(1-q))<br>
  → 새로운 BP가 두 개 생기게 된다!
- 그럼, 이 두 BP가 서로 독립일까? <br>
  → 당연히 아니다.<br>
  → 하지만 <span style="color:orange">각 프로세스의 각 슬롯</span>끼리는 independent하다.

<br>

### Merge: Bern. Process

- 자 이제 두 개를 합치는 상황에서는 어떻게 되는지 살펴보자.
- 이전과는 관계가 없는 문제라고 생각하고, Proc. 1과 Proc. 2를 합친다고 생각하자. <br>
  → Merge **BP(p)** and **BP(q)** into one process.<br>
  ![스크린샷 2021-11-25 오후 5 35 37](https://user-images.githubusercontent.com/37065429/143407089-d2a9af0e-3193-42ea-b763-3bab861ad52e.png)
- 여기서, 1과 2의 특정 슬롯을 합칠 때 충돌이 발생한다면 merged process에는 하나만 들어간다고 하자.
- <span style="color:orange">Question. </span>Probability of having at least one arrival <br>
  → 1 - (1 - p)(1 - q) = p + q - pq <br>
  → <span style="color:orange">적어도 하나</span>라고 말하는 이유는 Collid arrival에 대한 예외를 처리했기 떄문이다.
- 그러면, 합쳐진다는 것이 '도착'이라고 해석한다면<br>
  → Merged Process : BP(<span style="color:orange"> p + q - pq </span>)
- 살짝 꼬아서, Merged proc.에 도착이 생겼을 때, 그것이 1번 proc.으로 부터 왔을 확률은? <br>
  ![스크린샷 2021-11-25 오후 5 35 19](https://user-images.githubusercontent.com/37065429/143407045-da90266a-ef39-4079-b1b5-60ffd19bd725.png)

