---
title: "Introduction to Statistical Inference"

categories:
  - Probability and Random Variables
toc: true
toc_sticky: true
---

> 현재 정리하는 내용은 KAIST EE의 이융 교수님, Probability and Intorductory Random Process 강의를 참고하여 작성했습니다.

# What is Statistical Inference?

- 몇 개의 예제를 통해 Inference가 무엇을 의미하는지 확인해보자.
  1. Take 1000 voters uniformly at random, and count the popularity of each candidate to infer the true popularity.<br>
     → What is true popularity?
  2. COVID-19 has spread over a collection of people, and we collect a sample of COVID-19 infectees to infer the true source of infection.<br>
     → What is true source of infection?
  3. When an original signal S is transmitted over the School Wi-Fi connection, the received signal X becomes X = aS+W, where 0 < a < 1 and W ~ N(0, 1). If we have 10 samples of (S, X) values, what is the inferred value of a?<br>
     → What is value of a?
- 위 3가지 예제를 통해 Inference는 <span style="color:red">정보를 추출해내는 Process</span>라는 것을 알 수 있고, 이 때 <span style="color:red">unknown variable or an unknown model</span>을 기반으로 한다는 것을 알 수 있다.
  <br>

## Statistical Inference : Three Main Ideas.

- 앞서 말한 내용에서 주된 3가지의 아이디어를 생각해보자.
  1. Samples are likely to be a <span style="color:red">good representation of the unknown.</span>
  2. There exists <span style="color:red">uncertainty (i.e, noise)</span> as to how well the sample represents the unknown.
  3. How to obtain samples has impact on inference

<br>

## Inference, Real World, Probability Theory

- 이 세 가지의 연관성을 알아보자.<br>
  ![image](https://user-images.githubusercontent.com/37065429/147216129-64fce176-8c8e-4ec5-a6f2-87094502f1c9.png)
  <br>
  → 그림에서 나온 것과 같이 세 가지는 모두 연관이 되어있다.
- **Inference**<br>
  → 현실 세계의 데이터를 갖고, probabilistic model 또는 parameters를 결정하는 것<br>

<br>

### What to infer? Unknown Model vs. Unknown Variable

- 이 둘의 차이가 무엇일까? 앞서 예제에서 봤던 것 중 하나를 가져와보자.<br>→ When an original signal S is transmitted over the School Wi-Fi connection, the received signal X becomes X = aS+W, where 0 < a < 1 and W ~ N(0, 1). If we have 10 samples of (S, X) values, what is the inferred value of a?<br>![image](https://user-images.githubusercontent.com/37065429/147216958-857d5c61-2718-48d2-b2c9-aed28294c24a.png)<br>→ X = aS + W<br>

  |                        Model Building                        |                     Variable Estimation                      |
  | :----------------------------------------------------------: | :----------------------------------------------------------: |
  | <span style="color:red">Know</span> the original signal S<br /><span style="color:red">Observe</span> X<br /><span style="color:red">Infer</span> the model parameter a | <span style="color:red">Know</span> the original signal S<br /><span style="color:red">Observe</span> X<br /><span style="color:red">Infer</span> the original signal S |

- 이 둘의 다른 점은 있지만, 즉 다른 질문을 던지지만 동일한 수학적 구조를 갖게 된다.

  <br>

### What kind of inference? Hypothesis Testing vs. Estimation

|                      Hypothesis Testing                      |                          Estimation                          |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
| <span style="color:red">Unknown</span> : a few possible ones.<br />→ Finite discrete<br /><span style="color:red">Goal</span> : small probability of incorrect decision<br />→ How can we evaluate my decision?<br />Ex. Something detected on the radar. Is it a bird or something? | <span style="color:red">Unknown</span> : a value included an infinite, typically continuous<br /><span style="color:red">Goal</span> : Finding the value close to the true value.<br />Ex. Biased coin with unknown prob. of head. What is  data of heads <br />Note. If u have the candidate values of {1/4, 1/2, 3/4}, then it's a hypothesis testing problem. |

<br>

## Different views: Bayesian vs. Classical

<img width="760" alt="스크린샷 2021-12-23 오후 6 28 05" src="https://user-images.githubusercontent.com/37065429/147219432-dac6b4fd-d730-41f1-bbc1-01447c405107.png"><br>
→ Infere할 것이 {1/4, 3/4}이므로, Hypothesis testing.<br>
→ 직관적으로 생각해본다면, HHH가 나왔으니까 3/4일 확률이 더 높다. 이걸 Bayesian 관점과 classical 관점으로 확인해보자.<br>

|                        Bayesian View                         |                        Classical View                        |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
| ![image](https://user-images.githubusercontent.com/37065429/147221133-37ecadf6-8e1e-428b-9ac1-455ada48b19c.png)<br />→ Prior distribution을 통해 posterior를 계산하는 전형적인 Bayesian 방법이다.<br><br />→ 가장 큰 θ를 고르는 방식은 MAP라고 한다. 후에 나온다. | ![image](https://user-images.githubusercontent.com/37065429/147221478-c953420a-b013-4bd4-994d-e3260658528e.png)<br />→ 옆에 있는 Bayesian과 다르다는게 느껴진다.<br />→ θ가 있다는 가정 하에 HHH일 확률을 구하는 방식으로 한다. |

- 이거는 Bayesian rule 계산 방식<br>
  ![image](https://user-images.githubusercontent.com/37065429/147221806-90d072ef-5205-409f-a449-834e497d79f0.png)<br>

- 수식으로 확인해보았으니 이제 글로 확인해보자.<br>

  |                        Bayesian View                         |                        Classical View                        |
  | :----------------------------------------------------------: | :----------------------------------------------------------: |
  | <span style="color:red">Unknown</span> : RV with some distribution (prior)<br /><span style="color:red">Observe</span> : Data X, posterior distribution<br /><img width="97" alt="스크린샷 2021-12-23 오후 6 47 52" src="https://user-images.githubusercontent.com/37065429/147222138-80f54a06-783b-461b-95f6-2a8e7faeee6a.png"><br />→ 표본으로부터 제공된 정보와 함께<br /> unknown parameter의 확률 분포에 대한 지식을 사용하여 추론<br />![image](https://user-images.githubusercontent.com/37065429/147222230-ba581e8a-ba8f-4824-aa5e-c536310a04c9.png) | <span style="color:red">Unknown</span> : Deterministic value<br /><span style="color:red">Observe</span> : Data X<br />![image](https://user-images.githubusercontent.com/37065429/147222494-2eed42fe-f5f0-4f94-aede-57d085f86d73.png) |

  

- 그럼 누가 더 좋은 방식이야? <br>
  → 이것에 대한 정답은 아직 없다. 아래 예제를 한 번 확인해보자.
- Example. mass of the electron by noisy measurement.<br>
  <span style="color:red"> Classical View </span>: unknown이기는 한데,,,전자의 질량은 당연히 상수지. 그러니까 모델링할 수 있는 RV는 없어.<br>
  <span style="color:orange">Bayesian</span> : 아니! 우리는 some range of candidate values를 이전 측정에서 구할 수 있으니까 당연히 가능해!
- 이렇게 서로 다른 주장을 할 수 있다. 따라서 누가 더 좋고 말고 할 것이 없다.
- 근데, Bayesian은 다차원 데이터에 대한 계산의 용이성이 있다는 점은 존재한다.<br>
  → MNIST는 28 by 28의 다차원 데이터이다.<br>

<br>