Random Variables (4)

## Gaussian (Normal) RVs

| Standard Normal                                              | General Normal                                               |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Notation : <img width="65" alt="스크린샷 2021-09-30 오후 2 03 01" src="https://user-images.githubusercontent.com/37065429/135974399-cfcfbb50-7287-46f0-a76e-fb1ae58358c0.png"><br>PDF : <img width="99" alt="스크린샷 2021-09-30 오후 2 03 49" src="https://user-images.githubusercontent.com/37065429/135974463-837ed48a-b8c1-4af9-95c0-6f171c8bec86.png"><br />Expectation And Variance<br /><img width="108" alt="스크린샷 2021-09-30 오후 2 04 28" src="https://user-images.githubusercontent.com/37065429/135974538-5cce97fb-fe16-4f8f-b0b8-3711d0ed4767.png"> | Notation : <img width="75" alt="스크린샷 2021-09-30 오후 2 03 17" src="https://user-images.githubusercontent.com/37065429/135974441-4423e452-f8f7-4ef0-ad04-c8b5efc66039.png"><br />PDF : <img width="152" alt="스크린샷 2021-09-30 오후 2 04 07" src="https://user-images.githubusercontent.com/37065429/135974495-0157177b-48a3-4f6b-b639-b47270eb552c.png"><br />Expectation And Variance<br /><img width="96" alt="스크린샷 2021-09-30 오후 2 04 54" src="https://user-images.githubusercontent.com/37065429/135974584-622f093d-43a7-4245-ae9b-2b512ee2a63e.png"> |

→ Expectation은 μ를 중심으로 symmetric하다는 것을 알 수 있다.<br>

→ 또한, PDF의 속성인 Normalization은 다음과 같은 수식으로 증명이 된다. (적분 수업이 아니여서 전개 과정은 없다.💩)<br><img width="261" alt="스크린샷 2021-09-30 오후 2 06 40" src="https://user-images.githubusercontent.com/37065429/135974620-0ff04e92-94fb-44fa-b558-ba5b2a40e953.png">
<br>

→ Variance는 다음과 같은 수식으로 증명이 되고, 이는 E[(X-μ)^2]과 같다.<br>

<img width="678" alt="스크린샷 2021-09-30 오후 2 07 23" src="https://user-images.githubusercontent.com/37065429/135974656-fcc1ebb9-b600-4416-b80c-60ad5455ef03.png"><br>

→ 마지막 부분에서 Normalization property가 적용됨을 확인하자. <br>

- Normal RV의 특이한 속성을 알아보자. <br>

  <img width="586" alt="스크린샷 2021-09-30 오후 2 15 14" src="https://user-images.githubusercontent.com/37065429/135974692-c0c4f2fd-30ee-44cc-a90b-24b23c264dd0.png"><br>→ X가 Normal일 때, 이를 통해 만들어진 RV Y또한 Normal함을 알 수 있다. <br>

  → Expectation과 Variance는 다음과 같이 쉽게 구해질 수 있다. <br><img width="401" alt="스크린샷 2021-09-30 오후 2 17 50" src="https://user-images.githubusercontent.com/37065429/135974720-dfa9d034-443a-4969-a706-54d257a4be75.png">
  <br>
  → Thus, every normal RV can be <span style="color:red">**STANDARDIZED**</span>. <br>

  →<img width="395" alt="스크린샷 2021-09-30 오후 2 20 29" src="https://user-images.githubusercontent.com/37065429/135974748-513739ac-9944-4f7c-95f7-56bd981dbadc.png"><br>

- Standardized된다는 것이 어떠한 의미를 가질까?

  - 모든 normal RV의 CDF를 특정한 표(table, Φ)를 사용하여 쉽게 구할 수 있다.<br><img width="441" alt="스크린샷 2021-09-30 오후 2 22 02" src="https://user-images.githubusercontent.com/37065429/135974778-0e8cad30-48d7-48c2-982b-6a39a74aa4c3.png">
    <br>

  - 이걸 적용한 예제를 하나 살펴보자.

    - 매년 강설량 X를 N(60, 20^2)으로 모델링 했다고 하자. 그럼, 최소 80 inches일 확률은 몇인가? <br><img width="291" alt="스크린샷 2021-09-30 오후 2 23 39" src="https://user-images.githubusercontent.com/37065429/135974874-d2503775-1ec3-4620-8ea4-6c282a2a0388.png">
      <br>

      → 구하려는 X를 Y로 변환함으로써 Standardized를 하고, 테이블을 통해 쉽게 구할 수 있는 것을 확인할 수 있다.<br>

- Normal RVs : Why Important?

  1. Central limit theorem (중심 극한 정리)<br>
     → 모집단이 Normal을 이룬다고 할 때, 이 모집단으로부터 추출된 표본의 크기가 충분히 크다면 표본 평균들이 이루는 분포는 정규분포에 근접한다.
     1. One of the most remarkable findings in the probability theory
     2. <span style="color:red">**Sum of any random variables ≈ Normal random variables**</span>
  2. Modeling aggregate noise with many small, independent noise term
  3. Convenient analytical properties, allowing closed forms in many cases
  4. Highly popular in communication and machine learning ares

<br>

## Continuous : Joint PDF and CDF (1)

- 다음과 같은 조건을 만족한다면, 두 개의 continuous RV는 **jointly continuous**라고 말할 수 있다. <br><img width="656" alt="스크린샷 2021-10-06 오전 10 57 12" src="https://user-images.githubusercontent.com/37065429/136158112-39134cb3-1871-485f-ba00-650e658064e7.png">
  <br>
- B는 subset이고, two dimensional plane은 쉽게 생각하면 바둑판이라고 생각할 수있다. <br>
  → B = { (x, y) &#124; a <= x <= b, c<= y <=d } 
- <span style="color:blue">**The Marginal PDFs**</span> of X and Y are from the joint PDF as :<br><img width="460" alt="스크린샷 2021-10-06 오전 11 00 51" src="https://user-images.githubusercontent.com/37065429/136158144-4fdf75a5-0a6a-4890-9cae-55f81dd91ee5.png">
  <br>
- <span style="color:red">**The Joint CDF**</span> is defined by F_(X, Y)(x,y) = P(X <= x, Y <= y) and determines the Joint CDF as : <br><img width="224" alt="스크린샷 2021-10-06 오전 11 02 37" src="https://user-images.githubusercontent.com/37065429/136158175-d37e0742-bdd1-4135-9b3e-ee267bcb37ba.png"><br>
  → CDF와 PDF의 연관성은 미분과 적분이였음을 기억하자💩 
- A function g(X, Y) of X and Y defines a new random variable, and <br><img width="387" alt="스크린샷 2021-10-06 오전 11 03 45" src="https://user-images.githubusercontent.com/37065429/136158206-cd6c6f52-6604-4c83-a520-fd0d6a5c345e.png">
  <br>

<br>

- Event가 주어졌을 때, PDF를 구해보자. 즉, <span style="color:pink">**Conditional PDF, given an event A**</span>를 생각해보자. <br>

  **✣ 여기서 사용하는 A 는 event를 의미하고, B와 C는 subset을 의미한다.** <br>
  <img width="275" alt="스크린샷 2021-10-06 오전 11 06 06" src="https://user-images.githubusercontent.com/37065429/136158238-ebb25e4d-33d1-4a91-8e01-8aa22285e804.png">

  - PDF의 정의를 통해서 첫 번째 줄이 어떻게 나오는지 알 수 있고, conditional PDF는 두 번째 줄과 같이 나온다는 것을 이해하자.<br>

  <img width="233" alt="스크린샷 2021-10-06 오전 11 10 06" src="https://user-images.githubusercontent.com/37065429/136158261-b6308c4d-2373-4fc7-81fe-30814f667434.png"><br>

  - 어떠한 subset 안에서의 PDF는 첫 번째 줄과 같이 나올 것이고, 여기서 subset에 이벤트가 주어졌을 때, 두 번째 줄과 같이 나온다.<br>

  <img width="132" alt="스크린샷 2021-10-06 오전 11 11 24" src="https://user-images.githubusercontent.com/37065429/136158291-1e584928-d3eb-4c40-b6f2-0aa8d0abf69e.png"><br>

  - 그리고, 당연히 event 내에서의 PDF는 1이 된다. 💩<br>

- Event가 아닌, subset 에 포함된다는 event가 주어졌을 때, conditional PDF는 어떻게 될까? <br><img width="363" alt="스크린샷 2021-10-06 오전 11 15 10" src="https://user-images.githubusercontent.com/37065429/136158327-c535350d-ad88-4f1d-b669-594ae894ea3b.png">
  <br>
  💩 이렇게 된다~!

<br>

- 추가로, **Conditional Expectation**을 구해보자. <br>
  → 먼저, 그림을 통해 일반 PDF를 통해 Conditional PDF를 구하는 방법을 확인해 보자. <br><img width="515" alt="스크린샷 2021-10-06 오전 11 21 21" src="https://user-images.githubusercontent.com/37065429/136158364-a1dd78db-06fb-4e75-8876-1e06ab37ed24.png">
  <br>
  → Conditional로 떨어진 부분의 넓이는 1이 되어야 하기 때문에 높이가 2/(b-a)가 됨을 확인합시다~🐯 

  - 이렇게 되면, Conditional Expectation은 쉽게 구해질 수 있고, <br>

    <img width="192" alt="스크린샷 2021-10-06 오전 11 22 58" src="https://user-images.githubusercontent.com/37065429/136158438-70f3d819-fc56-41b6-a779-c28b4dd1f359.png">

  - rv X를 통해 만들어지는 새로운 rv g(X)에 대해서도 확장해서 적용할 수 있다. <br>
    <img width="250" alt="스크린샷 2021-10-06 오전 11 23 46" src="https://user-images.githubusercontent.com/37065429/136158492-c74a31ce-2ad2-46fb-9201-87b6b0ea3d67.png">

  - 그럼, 그림에서 나온 Conditional PDF의 Expectation은 어떻게 구할 수 있을까? <br>
    → 위 공식을 사용하면 쉽게 구할 수 있다. <br>
    <img width="336" alt="스크린샷 2021-10-06 오전 11 25 48" src="https://user-images.githubusercontent.com/37065429/136158525-aa92ccff-a353-4c11-bfbb-22579c1cf877.png">

<br>

<br>

- **Example : Train Arrival**

  - 예제에 들어가기 앞서, 이전에 배웠던 두 가지에 대해 다시 살펴보자

  - Exponential RV : Memoryless

    1. Exponential RV는 geometric RV의 continuous counterpart이다.

    2. 그래서, geometric의 memoryless를 exponential도 가질 것이라 기대할 수 있다.<br>

       <img width="286" alt="스크린샷 2021-10-06 오전 11 48 25" src="https://user-images.githubusercontent.com/37065429/136158572-3e95f05f-f3c4-4c21-94fc-c234b06660bd.png">

    3. Exponential RV의 CCDF를 사용하고, CCDF P(X > x) = e^(-λx)라 하면,
       <img width="593" alt="스크린샷 2021-10-06 오전 11 49 24" src="https://user-images.githubusercontent.com/37065429/136158594-f5b8a531-b32f-4e59-8989-a1540e804d8d.png"><br>
       → 이니까, 나의 기대를 충족시켰다.

  - Total Probability / Expectation Theorem

    |                        Discrete Case                         |                       Continuous Case                        |
    | :----------------------------------------------------------: | :----------------------------------------------------------: |
    | Total Probability Theorem<br /><img width="298" alt="스크린샷 2021-10-06 오전 11 51 15" src="https://user-images.githubusercontent.com/37065429/136158620-7332d7ff-9f9f-434b-a93a-b014f5a25f3a.png"><br />Total Expectation Theorem<br /><img width="245" alt="스크린샷 2021-10-06 오전 11 51 43" src="https://user-images.githubusercontent.com/37065429/136158651-867fc72e-13c8-40fd-9764-c6bdb0807b79.png"> | Total Probability Theorem<br /><img width="249" alt="스크린샷 2021-10-06 오전 11 51 59" src="https://user-images.githubusercontent.com/37065429/136158683-6bf132aa-be1c-4808-afdf-d929096e58f4.png"><br />Total Expectation Theorem<br /><img width="245" alt="스크린샷 2021-10-06 오전 11 51 43" src="https://user-images.githubusercontent.com/37065429/136158651-867fc72e-13c8-40fd-9764-c6bdb0807b79.png"> |

  - 예제 설명 시작.

    1. 어떤 기차🚃는 15분에 한 번 씩 도착을 한다. (every quater hour, 0min - 15min - 30min - 45min - 60min)
    2. 나는 7:10~7:30에 도착할 것이라 예상되고, 10분에서 30분 사이의 확률은 Uniform하다.
    3. 기차가 도착할 때까지 기다려야하는 시간의 PDF는 어떻게 계산해야 할까?
    4. X : your arrival time, Y : waiting time

    - 먼저, X에 따라 waiting time이 달라지니까 두 개의 유형으로 분류를 하자.<br>
      <img width="251" alt="스크린샷 2021-10-06 오후 2 09 55" src="https://user-images.githubusercontent.com/37065429/136158738-6939bdcd-8127-457e-ad1c-f491b8b8f43e.png">

    - 그러면, Y에게 A 또는 B 이벤트가 발생했을 때의 condition을 부여하고, Total Probability Theorem을 적용하면 구할 수 있다. (물론, Continuous이다💩)<br><img width="357" alt="스크린샷 2021-10-06 오후 2 27 35" src="https://user-images.githubusercontent.com/37065429/136158849-41b8c9b9-9cfc-4d6b-bfdd-c33378c7868d.png">
      <br>

      <img width="390" alt="스크린샷 2021-10-06 오후 2 27 10" src="https://user-images.githubusercontent.com/37065429/136158818-987d4813-df91-49d0-9777-e5e792de3979.png">

      - 15분에 도착했을 때, 30분 기차를 타야한다!! <br>

  - Conditional PDF given a RV

    - 이전에 했던 내용의 반복이고, 단순히 PDF로 치환만 하면 된다.
    - 이건 첨부를 그냥 하겠다...이전 내용을 다시 복습해야할 필요성도 많이 느껴진다.😢 <br><img width="972" alt="스크린샷 2021-10-06 오후 2 32 49" src="https://user-images.githubusercontent.com/37065429/136158895-3e5ac752-9eb3-4508-8d1f-a7014b58c6da.png">
      <br>

  - 이를 활용한 예제를 하나 살펴보자.

    - Stick-breaking

      - 길이가 l인 막대를 반으로 쪼개버렸다..

      - 두개로 나뉘어진 막대 중 첫번째 막대는 길이가 Y이고, 이 막대를 다시 쪼갰다.

      - 막대는 두 개로 쪼개졌고, 이 중 하나의 길이가 X이다.

      - Y와 X는 uniform한 형태로 나타나게 되며, Y ~ U[0, l]이고 X ~ U[0, Y]이다. (**U는 Uniform을 의미한다.**) <span style="color:red">**즉, Continuous하다.**</span>

        > first break at Y ~ U[0, l]
        >
        > second break at X ~ U[0, Y]

        1. Joint PDF f_(X, Y) (x, y)를 구해보자. <br><img width="352" alt="스크린샷 2021-10-06 오후 2 44 06" src="https://user-images.githubusercontent.com/37065429/136158943-21930efb-f8f2-485c-9198-ca9764c301e8.png">
           <br>
           💩 앞서 내가 그림만 뚱땅 올린 내용을 통해서 쉽게 구해질 수 있다. discrete에서 continuous로 생각만 하면 된다!
        2. Marginal PDF f_X(x)를 구해보자. <br>
           <img width="324" alt="스크린샷 2021-10-06 오후 2 46 15" src="https://user-images.githubusercontent.com/37065429/136158974-cd20b465-a334-4508-b40e-6b4c1cefcadf.png">
        3. Evaluate E(X), using f_X(x)<br>
           <img width="375" alt="스크린샷 2021-10-06 오후 2 57 38" src="https://user-images.githubusercontent.com/37065429/136159005-b4cd4a35-ba55-4354-8d2c-d4bc2fcdd829.png">
        4. Evaluate E(X), using X=Y*(X/Y) <br>
           → if X ㅛ X/Y, it becomes easy, but true? <br><img width="288" alt="스크린샷 2021-10-06 오후 2 57 50" src="https://user-images.githubusercontent.com/37065429/136159038-35d70c77-42a3-4a4e-859b-9383dec235af.png">
           <br>
           → X 와 Y가 왜 독립적인지는 이해가 잘 가지 않는다... 수업에서는 처음 막대가 어떻게 잘리든 X의 분포가 달라지지 않기 때문이라고 한다.(uniform하기 때문)
        5. Evaluate E(X), using TET<br>
           <img width="350" alt="스크린샷 2021-10-06 오후 2 58 02" src="https://user-images.githubusercontent.com/37065429/136159067-a561bf1a-2c7a-4d93-96bf-9f483a7e02e7.png">

      - Expectation을 구하는 방식은 여러 개가 있음을 또한 확인할 수 있다.

