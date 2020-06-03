# RNN과 LSTM

## 1. RNN(Recurrent Neural Network)

1. RNN의 기본 구조

 <img src="C:\Users\GIHO\Desktop\Q8zv6TQ.png" alt="RNN" style="zoom: 50%;" />

   - 전통적인 neural network -> 지속되는 생각을 하지 못함

   - RNN은 이전 단계에서 얻은 정보를 계속 **지속**되도록 하여 순차적으로 데이터를 처리 할 수 있게 함

  <img src="C:\Users\GIHO\Desktop\s8nYcww.png" alt="rnn structure" style="zoom:50%;" />

   - activation function - 하이퍼볼릭탄젠트(-1~1)

   - input - 이전 state에서의 데이터($h_{t-1}$)와 $x_{t}$

   - 파라미터 - $W_{xh}$, $W_{hh}$, $W_{hy}$


2. RNN의 문제점
 - 관련 정보와 정보를 사용하는 지점의 거리가 멀 경우 학습 능력이 저하되는 문제점 존재
    - vanishing gradient problem
 - LSTM의 4개의 게이트를 통해 RNN의 문제점 어느정도 해결

## 2. LSTM(Long Short Term Memory)

- ***Cell State***  - 전체 체인을 관통 -> 정보는 계속해서 다음 단계로 전달

  <img src="C:\Users\GIHO\Desktop\캡처.PNG" alt="lstm" style="zoom: 80%;" />

- Sigmoid -> 0 또는 1 값 출력 => 이는 구성요소가 어느 정도의 영향을 주게 될지 결정해주는 역할을 함

![forget gate](C:\Users\GIHO\Desktop\forgetstate.PNG)

1. forget gate

   - 셀 스테이트에서 버릴 정보를 선택

   - Cell state와 $f_{t}$간의 곱셈에 의해 정보를 지움(sigmoid가 0에 가까울수록 정보를 없앰)

     ![input gate](C:\Users\GIHO\Desktop\inputgate.PNG)

2. input gate
   - 현재 정보를 저장할지 결정하는 과정

![update](C:\Users\GIHO\Desktop\updatestate.PNG)

3. update gate
   - 얼마나 버릴지, 얼마나 저장할지를 결정했으므로 input * current state+forget * previous state를 통해서 cell state 업데이트

![output gate](C:\Users\GIHO\Desktop\출력.PNG)

4. output gate
   - cell state 값을 얼마나 빼낼지 결정