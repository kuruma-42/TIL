# Data Mining  Decision Tree - Design Decision Tree Induction 

Classification 

Definition 
- Decision Tree는 Classification을 하기 위한 방법 중 하나로, 우리는 본격적으로 decision tree를 알아보기 전에 먼저 classification에 대해서 알아보려고 한다. 
- Trainning Set으로 record들이 주어지게 되면 각 record는 attribute set x와 class label y로 만들어진 tuple(x,y)에 의해서 characterization될 수 있다. 
- attribute, predictor, independaent variable, input 등으로 부를 수 있고, y는 class, response, dependent variable, output 등으로 부를 수 있다. 
- 이를 기반으로 classification이 하고자 하는 task는 각각의 attribute set x를 미리 정의가 된 class label y중 하나로 mapping하는 model을 학습하는 것이다. 

General Approach for Building Classification Model

<img width="504" alt="Training Set" src="https://github.com/kuruma-42/TIL/assets/60722292/a205dd42-7229-4d01-bbe3-e572d557cae1">

￼
- Training Set에는 ID마다 3개의 attribute와 1개의 class label이 존재 
- classification을 위해서는 data기반 모델을 학습시켜야 한다. 
- 러닝 알고리즘을 선택하고 
- trainning set을 넣어 각각의 data object에 대하여 class label을 찾을 수 있따. 
- test set에 있는 데이터를 어플라이 모델에 집어넣어 class label y에 있는 ?를 채워 넣어야 한다. 

Decision Tree 
￼

<img width="681" alt="Home  Marital Annual Defaulted" src="https://github.com/kuruma-42/TIL/assets/60722292/505a4918-2e74-4d4b-b9b2-8a77dae99535">



- Decision Tree는 training set을 기반으로 만들 classifier이다. 
- 3개의 attribute와 1개의 class prediction이 있는 data. 
- 노란색의 노드와 파란색의 leaf node로 구성되어 있는 것을 볼 수 있다. 
- node는 attribute에 leaf node는 class label에 대응되는 것을 볼 수 있다. 

Another Decision Tree 

<img width="664" alt="No" src="https://github.com/kuruma-42/TIL/assets/60722292/35cafc20-eabc-4495-8684-16c79276057e">

￼
- Training data는 상기의 본과 동일하다. 
- 위의 Decision Tree의 형태는 조금 다르다. 
- 물어보고자 하는 Attribute의 순서에 따라 Tree구조가 달라진 것이다. 
- 동일한 data에 대해서 적어도 하나 이상의 tree가 존재할 수 있다. 

Induction 
Tree를 만드는 방법에는 여러가지가 존재한다. 
- Hunt’s Algo 
- CART
- ID3, C4.5

General Structure of Hunt’s Algo 

<img width="677" alt="Let D, be the set of training records that reach a" src="https://github.com/kuruma-42/TIL/assets/60722292/4fefe347-0218-4376-a4b0-66aa1232c58c">

￼
만약 모든 class label이 homogeneous하다면 leaf node를 만들면 되고, 만약 그렇지 않다면 branch를 만들면 되는 것이다.

Design issue of induction 
- How should training records be split?
- 이 질문은 split을 하는 기준과 관련이 있다. 위의 예시에서는 그저 attribute를 순서대로 선택해서 tree를 만들어나갔다. 하지만 가장 최적으로 split을 하기 위해서는 test condition과 관련한 method를 사용해야 한다. 또한, test condition의 좋고 나쁨을 평가하는 measure들도 존재한다. 우리가 attribute를 선택해서 split을 한다고 했을 때, 어떠한 기준이 존재해야 한다는 것이다.
- Split 할 기준이 명확해야한다. 

-  How should the splitting procedure stop?
- 이번에는 splitting procedure를 언제 어떻게 멈춰야하는지와 관련이 있다. 우리는 모든 class label이 완벽하게 분류가 되거나, 100%는 아니더라도 어느정도 완벽하다는 판단이 되었을 경우에 미리 멈춰도 된다. 

- 그래서 단순하지만 덜 정확할지, 복잡하지만 더 정확할지에 따른 것은 온전히 tree를 만드는 사람에게 달려있다. 때로는 완벽하진 않아도 간단한 model을 필요로하는 경우가 존재할 것이다. 만약 model이 너무나도 complex하다면 training data에 대해서는 완벽할지라도 test data에서는 accuracy가 많이 떨어질 수 있다. 우리는 이러한 상황을 overfitting이라 부를 것이다.
