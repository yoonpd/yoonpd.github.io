---
title: "Dynamic scheduling"

categories:
  - Lyapunov Optimization
toc: true
toc_sticky: true
---

# Dynamic Scheduling

- Dynamic scheduling은 후에 서술될 *Lyapunov Drift 와 Lyapunov optimization*으로부터 개발된 알고리즘이라고 할 수 있다.
- 이전 포스트와 동일하게, arrival rates와 channel state는 모두 알고 있다고 가정하지만, 현재 채널에 따라 결정되는 randomized scheduling algorithm이 아닌, minimizing the drift of a Lyapunov function을 기반으로 문제를 해결해 나갈 것이다.<br>
  <span style="color:gray">→ 뭔 소린지 이해가 안 간다.......</span>
- 이러한 것의 장점은 current channel states와 current queue backlogs를 시스템을 stable하게 만들기 위해 사용한다는 것이다. <br>
  → 즉, priori knowledge는 필요하지 않다.<br><br>

# Scheduling For Stability

- 이전 포스트에서 사용했던 예제를 그대로 가져와서 한 번 확인해보자.<br>
  <img width="911" alt="스크린샷 2022-02-02 오후 4 09 32" src="https://user-images.githubusercontent.com/37065429/152109505-f4087266-ad39-449e-8014-5237d62ef028.png"><br>→ 각 입력 값(유입되는 패킷의 양)은 λ1과 λ2의 expectation 값을 갖는다. <br>
  → 이로 인해서, 우측 그래프와 같이 <span style="color:orange">Capacity region Λ</span>가 생기게 된다.🍊

## Environment

- 위에서 가정한 상황을 자세히 살펴보자.
- In every time slot t,
  - Arrival vector는 각각 A1(t), A2(t)로 정의되고, i.i.d.이다. 그리고 각각은 λ1과 λ2의 expectation 값을 갖는다(arrival rate).
  - Channel state vector는 **S**(t) = (S1(t), S2(t))로 정의된다. non-negative integer로 channel i에서 전송될 수 있는 패킷의 개수를 의미한다.<br><img width="665" alt="스크린샷 2022-02-02 오후 4 14 15" src="https://user-images.githubusercontent.com/37065429/152110084-56ba03d6-0ac9-4180-9242-a6623b277e27.png"><br>→ S1(t)와 S2(t)는 다음과 같은 확률을 갖게 된다.
  - Network controller는 **S**를 매번 확인한 뒤, *transmission decision*을 내리게 된다. 이는 α(t)로 표현한다.<br><img width="644" alt="스크린샷 2022-02-02 오후 4 15 56" src="https://user-images.githubusercontent.com/37065429/152110293-5aaca634-6809-4888-84f4-740cc6b2a84b.png"><br>→ Idle은 당연히 아무것도 보내지 않을 때를 의미한다.
  - 위와 같이 정의된 변수를 기반으로 Queue를 디자인하면,<br><img width="678" alt="스크린샷 2022-02-02 오후 4 16 49" src="https://user-images.githubusercontent.com/37065429/152110379-9500c4dd-5ba9-4bae-96b5-350794c3c6d0.png">
  - 아직 우리는 b(t)를 정의하지 않았다. 이는 다음과 같이 정의되고, <br><img width="661" alt="스크린샷 2022-02-02 오후 4 17 47" src="https://user-images.githubusercontent.com/37065429/152110480-058bfcb5-9ecc-4197-ba31-46ab91918dc8.png"><br>→ Channel state vector와 decision 값을 사용하게 된다. <span style="color:gray">즉, 선택이 되었을 때, 몇 개를 보낼 수 있는가</span><br>

<br>

## The *S*-only policy algorithm and ε-max (only channel ***S*** tate)

- Channel state vector는 다음과 같은 output을 가질 수 있다. 이를 ***S***로 정의한다면, <br><img width="421" alt="스크린샷 2022-02-02 오후 4 20 21" src="https://user-images.githubusercontent.com/37065429/152110719-226fa794-3c0d-499e-aac1-ca9180297c15.png"><br>→ 이 놈을 사용한다면, independent, stationary, randomized transmission decision을 내릴 수 있을 것이다. <span style="color:gray">(+ independent of queue backlogs)</span>

- 이를 위해서, ***S***에 의존하는 변수를 하나 더 생성하자.<br><img width="420" alt="스크린샷 2022-02-02 오후 4 22 41" src="https://user-images.githubusercontent.com/37065429/152110948-03ad7707-5824-46c8-b18f-037cf30e031a.png"><br>→ 이로써, q1과 q2는 the probability of transmitting over channel i if **S**(t) = (S1, S2)가 된다. <br>

  <span style="color:red">→ q1 + q2 <= 1 (채널은 아예 선택하지 않을 상황도 고려)</span>

- ***S-only*** 에서 결정되는 α 값을 α* 라 하고 b 값을 b* 라고 한다면, 다음과 같이 정의가 될 것이다.<br><span style="color:gray">→ 즉, 어떠한 정책을 기반으로 정해지는 처리량과 채널 선택 여부이다. (이건 **상수**다.)</span>

  <br><img width="421" alt="스크린샷 2022-02-02 오후 4 27 13" src="https://user-images.githubusercontent.com/37065429/152111489-7c2bc270-5687-4145-9020-54ed9e6fcaa9.png"><br>
  → ***S-only policy***를 통해 결정되는 b의 expectation은 다음과 같이 정의된다.<br><img width="464" alt="스크린샷 2022-02-02 오후 4 28 27" src="https://user-images.githubusercontent.com/37065429/152111612-3ceb2378-a96c-418d-a691-26dc0166a806.png"><br><img width="275" alt="스크린샷 2022-02-02 오후 4 31 03" src="https://user-images.githubusercontent.com/37065429/152111895-da29917e-3195-4330-b2ad-8a807142db51.png"><br>→ 한국어로 말하자면, (몇 개를 처리할 확률) * (몇 개를 처리할 수 있나의 몇 개) * (그 채널이 선택될 확률)이 된다.<br>

<br>

### ε-max

- 정책으로 값이 정해졌으니, 아래 식을 만족해야 한다.<br><img width="401" alt="스크린샷 2022-02-02 오후 4 46 43" src="https://user-images.githubusercontent.com/37065429/152113599-66ac8032-b6e1-49ed-a55d-8bf6ca700ad7.png">
- 그리고, rate stability를 위해서, <br><img width="327" alt="스크린샷 2022-02-02 오후 4 48 06" src="https://user-images.githubusercontent.com/37065429/152113778-7c1952c7-30f8-4c2c-bdc7-02fd4f9d7fdf.png"><br>→ 앞서 정의한 λ1과 λ2는 위 식을 만족해야한다.
- 쉽게 생각하면, 무작정 transmission rate를 높이면 될 일이지만, 유입량을 생각해봤을 때, ε 값을 추가로 도입해볼 수 있다.<br><img width="430" alt="스크린샷 2022-02-02 오후 4 51 01" src="https://user-images.githubusercontent.com/37065429/152114152-c5a5437e-d984-425d-b003-b3ad998ba6ca.png"><br>→ 짜잔. ε을 Maximize하는 문제로 변형할 수 있다.<br><img width="551" alt="스크린샷 2022-02-02 오후 4 52 21" src="https://user-images.githubusercontent.com/37065429/152114289-02f2bbe9-9988-4684-b27f-a9bf8a0f52c2.png"><br>

<br>

## Maximize Problem

- 위 식에서는 known parameters와 unknown parameters가 있다.<br>

  |                            KNOWN                             |                           UNKNOWN                            |
  | :----------------------------------------------------------: | :----------------------------------------------------------: |
  | <img width="372" alt="스크린샷 2022-02-02 오후 4 54 51" src="https://user-images.githubusercontent.com/37065429/152114628-45501cd8-ef7c-47e4-9ce4-5ac9b91f9482.png"> | <img width="363" alt="스크린샷 2022-02-02 오후 4 55 00" src="https://user-images.githubusercontent.com/37065429/152114649-71fbf812-3425-44e4-ba0c-b21091738b11.png"> |

- 위 식의 optimal을 ε-max라고 가정했을 때, 이 값은  <span style="color:orange">Capacity region Λ</span>안에서 찾을 수 있게 된다.🍊<br>
  → 그렇다면, ε-max는 현재의 **λ**와 <span style="color:orange">Region Boundary</span>까지의 거리가 될 것이다. <br>
  <span style="color:gray">→ 더 나아갈 수 있는 여력(?)이라고 이해했다.</span><br>→ 그럼 추가로, **λ**가 interior of <span style="color:orange">Capacity region</span>에 있다면, ε-max는 **0보다 클 것**이다(0이 아니다).

- 그럼 그림에서의 예제로 다시 살펴보자.<br>
  <img width="911" alt="스크린샷 2022-02-02 오후 4 09 32" src="https://user-images.githubusercontent.com/37065429/152109505-f4087266-ad39-449e-8014-5237d62ef028.png"><br>→ 우측 그래프에서 Y점은 (0.3, 0.7)의 값을 갖고 있는 상황이고, boundary까지 거리는 0.12이다. <br>
  → 즉, 이러한 방식을 통해서 다음 식을 만족하는 and policy를 만족하는 값들을 찾을 수 있다. <br><span style="color:pink">→ 예시를 하나 생각해본다면, router에 주는 power를 고정시켰을 때 유입량을 최대화하는 방법도 있다. (아닐수도?)</span><br>
  <img width="519" alt="스크린샷 2022-02-02 오후 5 06 20" src="https://user-images.githubusercontent.com/37065429/152115942-d3a84162-30d8-4975-b6bb-18decb2985f1.png">

