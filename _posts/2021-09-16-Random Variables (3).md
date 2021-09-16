# Random Variable (3)

> 현재 정리하는 내용은 KAIST EE의 이융 교수님, Probability and Intorductory Random Process 강의를 참고하여 작성했습니다.

## Independence for random variables

- Independence에 대해서 다시 한 번 보자 <br/>

  <img width="394" alt="스크린샷 2021-09-16 오전 11 30 44" src="https://user-images.githubusercontent.com/37065429/133580649-874adf2f-b78a-4511-b55d-85726dca0d54.png"><br/>

  → 다음과 같은 식을 만족한다면 **[Conditional] independence** 하다고 말할 수 있다.

- 그럼 **Random Variable과 event의 independence**는 어떤 조건을 가져야 할까? <br/><img width="529" alt="스크린샷 2021-09-16 오전 11 32 18" src="https://user-images.githubusercontent.com/37065429/133580694-83ed954f-4a87-468b-901d-429ad6f66f92.png"> <br/>

  → 당연히, 비슷한 형태를 갖게 된다.

- 추가적으로, **두 개의 RV에 대한 independence**는 어떤 조건일까? <br/><img width="532" alt="스크린샷 2021-09-16 오전 11 35 06" src="https://user-images.githubusercontent.com/37065429/133580725-696228c4-af60-4bcb-990f-15ea09cb27b5.png"><br/>
  → 이것 또한 비슷한 형태를 갖게 되고, 지난 시간에 봤던 Joint PMF를 사용한 notation을 다시 한 번 숙지하자.<br/>

- 예제를 통해 이해를 해봅시다~~<br/>
  <img width="374" alt="스크린샷 2021-09-13 오후 5 28 01" src="https://user-images.githubusercontent.com/37065429/133351680-6c16ca54-4109-4989-a27e-106053edc3d0.png"><br/>
  → 익숙한 그림이다..........<br/>

  1) X ㅛ Y ?<br/>
     <img width="244" alt="스크린샷 2021-09-16 오전 11 46 02" src="https://user-images.githubusercontent.com/37065429/133580771-5e994839-e2cf-4b9d-bbd8-b384717b1261.png"><br/>

  2) X ㅛ Y &#124; **{X <= 2 and Y >= 3}** ?

     - 조건을 Z라고 말한다면, 다음과 같은 수식을 만족해야 한다. <br/><img width="398" alt="스크린샷 2021-09-16 오전 11 50 30" src="https://user-images.githubusercontent.com/37065429/133580842-a9d14d18-8172-42c5-a926-a49daa2ccdef.png"><br/>

       <img width="499" alt="스크린샷 2021-09-16 오전 11 48 58" src="https://user-images.githubusercontent.com/37065429/133580806-89a10c78-7196-48a8-b298-e7056a394bb6.png">
       <br/>→ 자, 그러면 Z 조건에서 발생할 확률은 다음과 같이 채워지게 된다. <br/>

       → 여기서 중요한 점은, <span style="color:red">**'Z 조건'에서 발생할 확률이기에 분모가 달라진다는 것**</span>이다. <br/>

     - 그럼 계산을 해 보십다!

       1. X=1이고 Y=3일 때. (1/3)*(2/3)=2/9이다.
       2. X=2이고 Y=4일 때, (2/3)*(1/3)=2/9이다.
       3. 나머지도 똑같다^^, 따라서 independence이다.<br/>

- **Expectation과 Variance에서 Independence**

  - **Expectation**<br/>
    <img width="685" alt="스크린샷 2021-09-16 오후 12 13 39" src="https://user-images.githubusercontent.com/37065429/133581165-b239ad98-32dc-4553-a641-a66892d2f307.png">

  - **Variance**<br/>
    <img width="442" alt="스크린샷 2021-09-16 오후 1 35 50" src="https://user-images.githubusercontent.com/37065429/133580889-3c0b89e3-76a2-4e71-bc6a-7d42b525a98c.png">

    - 여기서, 일반적으로 var[X+Y] != var[X] + var[Y]인 이유를 확인해보자. (**var의 정의**를 사용하면 쉽게 생각할 수 있다.)<br/>
      <img width="573" alt="스크린샷 2021-09-16 오후 1 44 12" src="https://user-images.githubusercontent.com/37065429/133580924-81e0cd23-26a5-41c5-9076-7f5022eeb574.png">
    - 감이 오지 않는가, <br/>
      X ㅛ Y이기 위해서는 var[X+Y] = var[X] + var[Y]이니까, <br/>
      **E[XY] = E[X]E[Y]를 만족하면 된다.**💩<br/>

  - 하나의 예제를 살펴보자.

    > n명의 사람이 모자를 어떤 박스에 던진다.<br/>
    >
    > 그리고 박스에서 랜덤하게 하나의 모자를 꺼낸다.<br/>
    >
    > 이 때, rv X를 자기 자신의 모자를 꺼낸 사람(1)이라고 해보자.<br/>
    >
    > 이 때, E[X], var[X]를 구하라.

    1. **Define a rv Xi = 1 if i selects its own hat and 0 otherwise.**
       <img width="262" alt="스크린샷 2021-09-16 오후 5 18 32" src="https://user-images.githubusercontent.com/37065429/133580990-f1b123de-60da-4856-8472-7c0279dd5c9d.png"><br/>
       → {Xi}, i=1,2,3, ..., n : identically distributed. <br/>
       <img width="362" alt="스크린샷 2021-09-16 오후 5 20 23" src="https://user-images.githubusercontent.com/37065429/133581017-d1de9f2e-f46e-4666-b35a-a176351771d1.png"><br/>

       → 그러면 Expectation은 다음과 같은 식을 만족할 것이고, X1 = 1/n이므로, E[X]=1이 될 것이다.

    2. **Are Xis ars independent? If yes, easy to get var(X).<br/>**
       <img width="383" alt="스크린샷 2021-09-16 오후 5 23 08" src="https://user-images.githubusercontent.com/37065429/133581049-2e798448-551a-4c89-ae29-848bc633eb8e.png">
       → 다음과 같은 간단한 가정만으로도 Xi들은 dependent하다는 것을 알 수 있다. <br/>
       → independent하면 var 계산이 쉬울테지만,,,아니니까 하나 씩 해야된다. <br/><img width="620" alt="스크린샷 2021-09-16 오후 5 24 53" src="https://user-images.githubusercontent.com/37065429/133581105-3b5d6219-11fb-404a-bd43-cfa62411227c.png"><br/>

       → Xi가 identically distributed이기 때문에 i에 어떤 값이 들어가도 괜찮다는 것을 기억하자.