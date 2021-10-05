# Random Variables (4)

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

