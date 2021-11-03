---
title: "Random Variables (8)"

categories:
  - Probability and Random Variables
toc: true
toc_sticky: true
---



# Radnom Variable (8)

# <br>

## Weak Law of Large Number : Result and Meaning

- 확률 및 랜덤 변수에서 가장 중요한 발견 중 하나이다.

### Our interset : Sum of random variables

- RV들의 합이 어떤 의미를 갖는지 간단한 예제를 살펴보자.
  1. n students who decides their presence, depending on their feeling. Each student is happy or sad at random, and only happy students will show their presence. How many students will show their presence?
  2. I am hearing some sound. Their are n noise sources from outside.
- 여기서, 학생의 감정이나 소음의 출처를 X1, X2, ... Xn 이라 하고, Xi가 i.i.d라고 해보자. <br>
  → <span style="color:orange"> i.i.d : independent and identically distributed</span>
- 그러면, Xi의 Expectation은 μ이고 Variance는 σ^2이 될 것이다.
- 우리가 궁금한 것은 이제 **"How the Sum of random variables behaves"**이다.<br>→ 나의 생각이지만 '평균 회귀'에 관한 내용 같다. (아직은 잘 모르겠음,,다 안들었음 ㅋㅋ)<br>![스크린샷 2021-11-03 오후 1 47 48](https://user-images.githubusercontent.com/37065429/140040329-b685283b-d11c-44ed-b27b-6037c2447cf1.png)
  <br>

<br>

### What about distribution of Sn?

- Sn의 distribution을 찾는 것은 매우 어려운 일이다.
- 우리는 저번주에 Z=X+Y의 distribution을 찾을 때도 <span style="color:red">convolution</span>을 사용하면서 꽤나 힘들었다.. <br>
  → 이건 두 개인데 무수히 많은 n은 참으로도 힘들 것이다.
- 단, Sn이 sum of normal rvs라면 Sn도 normal이기 때문에 쉬워지긴 한다. <br>
  → 근데 실제로 이런 일은 거의 없다.
- <span style="color:red">Possible approach</span> : Take <span style="color:blue">**a certain scaling with respect to n**</span> that corresponds **to a new glass**, and investigate the system for large n.

<br>

### Sample Mean

- Consider the <span style="color:orange">sample mean</span> and try to understand how Sn behaves: <br>![스크린샷 2021-11-03 오후 2 05 01](https://user-images.githubusercontent.com/37065429/140040354-9eb535e8-268b-4496-8202-2527a7b39583.png)
  <br>
- E(Mn) = μ , Var(Mn) = (σ^2)/n
- 매우 큰 n에 대해서는 var은 0으로 수렴할 것이다(decays).
- 그럼, Mn은 이것의 randomness를 잃어버릴 것이고, μ값을 중심으로 뭉쳐질 것이다!
- 이것을 <span style="color:red">Law of large numbers (LLN)</span> 이라고 부른다.

<br>

#### Let's Establish Mathematically

- 근데, **n이 무한대로 갔을 때, 과연 Mn을 μ라고 할 수 있을까?**
- n이 무한히 커지면서 var이 0이 되고 Mn은 μ를 중심으로 뭉치니까 그럴 것만 같다.
- 여기서 Ordinary convergence를 확인해보고 가자.
- <span style="color:blue">Ordinary Convergence</span> for the sequence of **real number** : an → L<br>![스크린샷 2021-11-03 오후 2 09 16](https://user-images.githubusercontent.com/37065429/140040374-a192f201-d5b3-4184-9e50-5df5a8b78d17.png)
  <br>
- 이걸 보면, 가정했던 내용이 맞는 것만 같다...하지만 Ordinary Convergence는 real number한테 적용되는 것이고, <br>
  → Mn은 <span style="color:orange">From sample space to Real number</span> 를 해주는 Random variable이다.
- 따라서, 새로운 concept of convergence for the sequence of RVs를 만들 필요가 있다.

<br>

### Convergence in Probability (1)

- 아까 말한 것처럼, Ordinary convergence는 real number만 취급해서 우리가 원하는 문제에 적용할 수 없었다...

- 이걸 이용해서 New concept of convergence for the sequence of RVs를 뚝딱 해보자.🔨

- 우리가 원한는 것은 <span style="color:blue">a sequence of rvs (Yn) convergence to a rv Y.</span>

- 먼저, Ordinary convergence를 사알짝 바꿔서 적용해보자.<br>![스크린샷 2021-11-03 오후 2 37 34](https://user-images.githubusercontent.com/37065429/140040401-aa50a294-b32f-4d9c-bf7e-22cc4fe35c47.png)
  <br>

  → 이렇게 되면, an은 real number이다. 왜냐면 An이라는 RV이가 sample space에서 real number로 바꿔준 값이 an이기 때문이다.

- 그럼 또 Ordinary convergence를 사알짝 적용해보자. <br>![스크린샷 2021-11-03 오후 2 44 33](https://user-images.githubusercontent.com/37065429/140040430-eef2fc59-ea34-488a-9791-9ecedfedce68.png)
  <br>

  → 짜잔. real number니까 Ordinary convergence가 그대로 적용된다. 물론 ε과 δ의 쓰임 위치를 주의하자. <br>
  ![스크린샷 2021-11-03 오후 2 45 47](https://user-images.githubusercontent.com/37065429/140040457-a9197f55-97db-43b9-bd32-6d1c61d57c6b.png)

<br>

### Convergence in Probability (2)

- 그럼,,, Y가 상수가 되면 어떻게 될까? <br>
   → *RV의 여러 형태 중 상수가 있으니까!*

- ![스크린샷 2021-11-03 오후 2 47 05](https://user-images.githubusercontent.com/37065429/140040486-5f967683-9a17-4d2e-8fb2-d4e29300c4ff.png)

- 나의 발 그림으로 표현을 해보겠다.<br>

  <img width="1074" alt="스크린샷 2021-11-03 오후 2 56 58" src="https://user-images.githubusercontent.com/37065429/140040502-c506bd4a-3508-4b6d-ad34-da532477561b.png"><br>→ 그럼, ε이 작으면 작을 수록 a쪽에 분포할 확률도 높아짐을 알 수 있다.

<br>

#### Examples : Convergence in Probability

![스크린샷 2021-11-03 오후 3 12 50](https://user-images.githubusercontent.com/37065429/140040526-1c0c5c4f-3354-4bfb-a761-13a18a13fb44.png)<br>

##### Exapmle 1.

![스크린샷 2021-11-03 오후 3 13 08](https://user-images.githubusercontent.com/37065429/140040639-85bd9e6a-00bf-4cdb-81bb-6aa2fa09a365.png)<br>

- 최솟값으로 mapping하기 때문에 Y1 >= Y2 >= Y3 >= ... >= Yn이다.
- 그럼 무한히 반복되면 당연히 Yn은 0(a)이 수렴할 것이다.  → Our intuition

<br>

##### Example 2.

![스크린샷 2021-11-03 오후 3 15 08](https://user-images.githubusercontent.com/37065429/140040695-1974a0df-8aa5-4c83-ac7b-b79c542877ff.png)<br>

- Y값을 일단 신경쓰지 않아도, n이 커지면 당연히 Yn은 0에 수렴할 것이다.

<br>

##### Example 3.

![스크린샷 2021-11-03 오후 3 16 24](https://user-images.githubusercontent.com/37065429/140040730-0860bbf9-a9f3-4c78-a185-59694eb15a4f.png)<br>



<br>

### Weak Law of Large Number (WLLN)

- 우리가 지금까지 사용했던 Mn은 간단하게 말하자면, μ 주변으로 값이 모인다라는 것이다.
  ![스크린샷 2021-11-03 오후 3 17 53](https://user-images.githubusercontent.com/37065429/140040754-9322a3a0-829c-4286-9c4d-23e6eb578747.png)<br>

#### WLLN : Why useful?

1. If we take the scaling of Sn by 1/n, it behabes like <span style="color:orange">**a deterministic number.**</span> This significantly simplfies **how we understand the world**. <br>

   → For example, assume that a large number of identically distributed noise come to you. Then, you can roughly approximate it as <span style="color:pink">n*average noise</span>.

2. Provides an interpretation of expectation in terms of a long sequence of identical independent experiments. <br>→ For example, what is the probability of head of a coin? <br>
   **→ Toss 1000 times, and count the number of heads.**

<br>

## Central Limit Theorem : Result and Meaning

### Central Limit Theorem : Start with Scaling (1)

- 이전에 배웠던 WLLG를 loosely하게 얘기하면 <br>
  ![스크린샷 2021-11-03 오후 3 42 39](https://user-images.githubusercontent.com/37065429/140040823-2a9b98ff-b57c-42df-92ee-726d071633e1.png)
- 그러나 우리는 <span style="color:red">어떻게</span> (Mn-μ)가 0으로 수렴되는지는 알지 못한다. 
- Question. What should be "somthing"?<br>![스크린샷 2021-11-03 오후 3 44 59](https://user-images.githubusercontent.com/37065429/140040788-df19a222-0107-4326-b978-a479724db1bf.png)
  <br>
  → (Mn-μ)은 0으로 수렴하니까, Something should blow up for large n. <br>![스크린샷 2021-11-03 오후 3 45 34](https://user-images.githubusercontent.com/37065429/140040844-176e0c7d-ad06-4369-83e3-a56cbd770f57.png)
  <br>
- 그럼 여기서 α는 몇이 되어야 할까? <br>
  → 1/2 (왜?????왜?????????? 모르겠다!!!!!!!!!)

<br><br>

### Central Limit Theorem : Start with Scaling (2)

- 나의 궁금증이 이제야 풀리는도다.
- 먼저, 앞서 작성한 식을 reshape해보자.<br>![스크린샷 2021-11-03 오후 3 52 14](https://user-images.githubusercontent.com/37065429/140040867-400aab26-dd34-41f7-84f8-399250f8c064.png)<br>
  → 시그마를 붙인 이유는 식의 아름다움을 위함이다. 뒤에 가면 느껴진다.
- 자, 여기서 나온 식을 Zn이라고 해보자.<br>![스크린샷 2021-11-03 오후 3 53 13](https://user-images.githubusercontent.com/37065429/140040875-bf92b7e3-f63c-439a-b955-6f008e8661ce.png)<br>
  → 이렇게 되면, Zn is well-centered with a variance irrespective of n.
- 우리는 이를 통해 Zn이 n이 무한대로 갈 때, <span style="color:red">어떤 의미있는 무언가</span>로 수렴하게 만들었다. <span style="color:red">무언가</span>가 무엇일까??<br>
  → Interestingly, it converges to some <span style="color:orange">well-known random variable.</span> (Zn → Z) <br>
  → 이제 이게 어떤 놈으로 나올지 알기 위해, Need a new concept of convergence : <span style="color:orange">Convergence in distribution</span>

<br><br>

### Convergence in Distribution

- 이전과 같이 a sequence of res (Yn) and a rv Y 를 생각해보자.
- ![스크린샷 2021-11-03 오후 4 11 07](https://user-images.githubusercontent.com/37065429/140040887-902f2a4b-484b-4f10-84f1-d99fc6f9e485.png)<br>
  → Another type of convergence of RVs <br>
  → Convergence in probability → Convergence in distribution, but the reverse is not true.
- 증명은 나중에 하도록 하고, 이해하기 위한 예제를 보고 가자.

<br>

#### Example : in Distribution but not in Probability

- 1 이상의 정수 n에서, 베르누이 RV Xn이 있다고 해보자.
- 그리고 X = 1 - Xn이라고 해보자. <br>
  → Xn은 누가 되었든 Bern(1/2)일 것이고, 따라서 X ~ Bern(1/2)이다. <br>
  → 그렇다는 것은 distribution of Xn and distribution X are equal. <br>
  → This is trivial that <span style="color:orange">Xn converges to X in distribution.</span>
- 그럼 Convergence in probability는??? <br>![스크린샷 2021-11-03 오후 4 19 50](https://user-images.githubusercontent.com/37065429/140040909-05250a20-3bb3-439d-9359-52eff3e7c23b.png)<br>
  → 역이 성립 안된다고 했으니 그렇다.

<br>

<br>

### Central Limit Theorem : Formalism

![스크린샷 2021-11-03 오후 4 25 53](https://user-images.githubusercontent.com/37065429/140040923-c2b79710-3fd9-4531-84bf-4eeaf269ef4e.png)

- 아까 누구로 변하는지 확인한다고 했다!
- 바로바로 CLT를 통해 Standard Normal Random Variable로 변환이 된다. <br>
  → <span style="color:red">Irrespective of the distribution of Xi, Z is normal.</span>

<br>

<br>

### LLG vs CLT : Different Scaling Glasses

- 둘 다 '안👓경'을 끼고 새로운 세계로 가는 방식이다.
- 안경을 낀 순간 두개가 어떤 세계로 가는지 확인해보자.

![스크린샷 2021-11-03 오후 4 31 28](https://user-images.githubusercontent.com/37065429/140040946-b3c22e7b-fac8-4a9e-8562-7d793796efd8.png)<br>

<br>

### Practival Use of CLT

- 지금까지 배웠던 CLT를 식으로 표현하면 다음과 같다. <br>![스크린샷 2021-11-03 오후 4 36 51](https://user-images.githubusercontent.com/37065429/140040987-3dac0dfb-6b8f-4689-8b5b-8a43640074cd.png)<br>
  → Zn을 Standard Normal RV로 근사시키는 역할을 한다.
- 그럼 여기서 Zn에 대한 식이 아닌 Sn에 대한 식으로 변환하면, 이 또한 Normal rv가 된다.<br>![스크린샷 2021-11-03 오후 4 37 52](https://user-images.githubusercontent.com/37065429/140041025-77b4daae-a16d-45dc-9cf7-9d9fb0a51792.png)
- 그럼, n이 얼마나 커야할까...?
  1. 보통은 20~30정도가 적당하다.
  2. Distribution of Xi가 symmetry or unimodality라면 더 작은 n도 작동한다.<br>
     → *Unimodality : A single maximum or minimum. 낙타 봉같은 모습이 아닌 종 모양이라고 생각하면 됨.*

<br><br>

#### CLT : Examples of Required n

![스크린샷 2021-11-03 오후 4 40 15](https://user-images.githubusercontent.com/37065429/140041048-d9157d1b-2307-4830-bbd4-688b02b402ae.png)

<br>

### Examples

![스크린샷 2021-11-03 오후 4 44 53](https://user-images.githubusercontent.com/37065429/140041074-08778903-350b-4164-8553-516519097eba.png)<br>

#### Examples of CLT (1)

- n과 a가 주어졌을 때, b를 구해보자. <br>![스크린샷 2021-11-03 오후 4 48 28](https://user-images.githubusercontent.com/37065429/140041106-bed0b1e7-43ff-4c26-b93c-256526fd8416.png)

<br><br>

#### Examples of CLT (2)

- n과 b가 주어졌을 때, a를 구해보자. <br>![스크린샷 2021-11-03 오후 4 49 10](https://user-images.githubusercontent.com/37065429/140041140-788e3317-430b-4c76-97bb-bcf2a109170b.png)<br>

<br>

#### Examples of CLT (3)

- a와 b가 주어졌을 때, n을 구해보자.<br>![스크린샷 2021-11-03 오후 4 49 59](https://user-images.githubusercontent.com/37065429/140041169-d7ac13a8-5c50-412c-99d8-b2585700c962.png)

