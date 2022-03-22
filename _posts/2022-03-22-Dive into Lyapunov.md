---
title: "Dive into Lyapunov"

categories:
  - Lyapunov Optimization
toc: true
toc_sticky: true
---

![image](https://user-images.githubusercontent.com/37065429/152164119-ec0d663b-3d7c-4ced-bdbb-3ed8211600f2.png)<br>Lyapunov Optimization은 위 책을 참고하여 정리 되었습니다.<br>

# Meaning of Lyapunov optimization

- Lyapunov optimization이 정말로 뭘 하는 녀석인지 제대로 확인해보자. <span style="color:gray">*(내 역량이 안될수도?)*</span>
- 먼저, 이전 포스트에서 나온 Lyapunov drift function을 다시 확인해보자.<br><img width="586" alt="스크린샷 2022-03-22 오후 9 59 52" src="https://user-images.githubusercontent.com/37065429/159487517-7cdbae50-cb89-4f6f-ac3d-b40668951816.png"><br>
  → 사실 이 녀석은 Upper bounded될 수 있다.<br><img width="614" alt="스크린샷 2022-03-22 오후 10 01 49" src="https://user-images.githubusercontent.com/37065429/159487827-f393907c-5cf8-4daa-a6be-236e0170beeb.png"><br>→ 구슬픈 나의 필기 실력을 기반으로,<br>
  <img width="1087" alt="스크린샷 2022-03-22 오후 10 02 52" src="https://user-images.githubusercontent.com/37065429/159488012-c3cba26f-11ee-4ed6-aa10-92b30eb5f980.png"><br>→ 다음과 같이 전개 후, upper bound를 제공할 수 있다.<br>
  → cf) 부등호 바로 다음 term은 나중에 B라는 constant로 바뀔 수 있다.<br><br>

# Conditional Lyapunov drift function

- 추가적으로, <span style="color:red">Conditional</span> Lyapunov drift function을 알아보자. 

  - Conditional만 붙는다. 물론 의미는 있다.<br>
    <img width="906" alt="스크린샷 2022-03-22 오후 10 04 29" src="https://user-images.githubusercontent.com/37065429/159488277-8b519f95-a352-46a6-b69a-612c3b10effb.png"><br>
    → Arrival과 state 자체는 시스템 상에서 '확률적'으로 주어지기 때문에 expectation을 사용하여 표현할 수 있다.

  - 이 놈도 upper bounded 될 수 있다. <br>
    → 위에서 적용한 방식을 그대로 사용한다.<br>
    <img width="935" alt="스크린샷 2022-03-22 오후 10 07 49" src="https://user-images.githubusercontent.com/37065429/159488838-0b4c92ab-33af-4f47-a658-e58b994b6414.png"><br>→ 여기서, 부등호 바로 앞 term은 **B**라는 상수로 치환될 수 있고, 붉은 색 람다 term은 나의 아름다운 필기를 보면 알 수 있다.<br><img width="507" alt="스크린샷 2022-03-22 오후 10 09 06" src="https://user-images.githubusercontent.com/37065429/159489088-584a2a5e-86bb-4e0a-9d29-a5d201522bac.png"><br>
    → Lyapunov 의 강력한 assumption이 i.i.d.인 이유이다.

  - **B**는 도대체 뭔데?<br>→ arrival과 departure는 현실적으로 생각해보면 어떠한 한계점이 존재한다.<br>→ 당연하....다...? 네트워크라고 하면 한번에 무한대의 값을 받을 수 없고 무한대의 값을 처리할 수 없으니께<br>
    → 그래서 한계점을 A_max, B_max라고 한다면,<br><img width="451" alt="스크린샷 2022-03-22 오후 10 11 38" src="https://user-images.githubusercontent.com/37065429/159489545-462e9425-b85c-4ee4-8264-6106598ebf8b.png">

  - 그럼 이제 식을 이쁘게 바꿔보자.<br><img width="862" alt="스크린샷 2022-03-22 오후 10 12 36" src="https://user-images.githubusercontent.com/37065429/159489700-77567b9a-7e45-4179-98f7-28208407ad6d.png"><br>

    → 각 박스를 숫자로 해서,

    1. B는 상수이므로, scheduling을 할 수 없다.
    2. Q(t)는 현재 시간에서는 주어졌지만, 평균 arrival은 control할 수 없는 값이다.
    3. 이것이 바로 우리가 control할 수 있는 scheduling 파라미터가 된다.

<br>

# Minimization of upper bound

- 우리는 이전 포스트에서 Drift를 최소화하기로 했었다.
- 근데, 이제는 상한을 얻었으니 요놈을 최소화하면 결국 우리의 결과가 된다!<br><img width="862" alt="스크린샷 2022-03-22 오후 10 12 36" src="https://user-images.githubusercontent.com/37065429/159489700-77567b9a-7e45-4179-98f7-28208407ad6d.png"><br>→ 그러면, 이 식에서 다시 생각해보자.
  1. 우리가 조절할 수 있는 파라미터는 α 값이다. 즉, scheduling indicator이다.
  2. 위 식을 minimization한다는 것은, α가 붙어있는 term을 maximization하게 되는 것이다. (빼기 붙어있음 ㅋㅋ)
- 정리하자면, 주어진 시스템 환경에서는 greedy 형태로<br><img width="651" alt="스크린샷 2022-03-22 오후 10 28 17" src="https://user-images.githubusercontent.com/37065429/159492513-de740d21-6e9f-4911-8682-af0a6d8a61cb.png"><br>→ 와 같이 scheduling을 할 수 있게 된다.
  1. 각 time slot t에서는 Q(t)와 S(t)를 observe
  2. <img width="444" alt="스크린샷 2022-03-22 오후 10 29 46" src="https://user-images.githubusercontent.com/37065429/159492748-9572248e-97e6-41c1-9d62-97bce77a8b28.png">에 따라 α를 결정 <br>→ Queue * amount of departure가 큰 queue일수록 높은 우선순위를 갖게 됨을 의미한다.
- 그럼, 진짜 이렇게만 해주면 좋은 성능(stable)이 나올까?<br>
  → 귀찮으니 다음번에 쓰겠다.
