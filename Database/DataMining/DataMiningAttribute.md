# Data Mining Attribute 

Data = Data Objects + Attributes 
- Data는 data objects들과 이들의 attributes들을 모아놓은 것. 
- data object는 data sample들과 이들이 가지고 있는 attribute 들을 모아놓은 것을 말한다. 
- attribute는 feature라고도 부른다. 
- ex) 사람의 얼굴을 하나의 data sample이라 한다면 이 sample을 보고 생각할 수 있는 attribute들이 존재해야한다. 큰 귀, 두꺼운 눈썹, 오똑한 코, 네모난 입, 파마머리 등이 attribute에 해당하며 이러한 attribute들을 사용해서 해당 data object를 설명할 수 있다. 이렇게 여러 개의 attribute를 통해서 하나의 data sample을 설명할 수 있다면, 여러 개의 data sample들을 만들 수가 있기에 이러한 것들을 모아놓은 것을 우리는 data라고 하는 것이다. 보통 이러한 data는 테이블 형식으로 정리할 수 있다. 

<img width="406" alt="Attributes, Features" src="https://github.com/kuruma-42/TIL/assets/60722292/69870759-8134-4af4-927a-fd56f3d78209">

￼

<img width="686" alt="Quantitativi" src="https://github.com/kuruma-42/TIL/assets/60722292/6f70a9cd-4a70-4333-b211-5faa9801f947">


￼
Attribute Definition 
- Attribute를 정의해보면 결국 object에 대한 propoerty와 characteristic을 의미한다
- 통계학에서는 attribute를 variable이라고 부른다. 
- Machine Learning에서는 feature라고 부른다. 
- 이외에도 다른 분야에서는 attribute를 filed, characteristic등으로 부르기도 한다. 
- 하나의 attirbute로 object를 설명할 수도 있지만, 대부분 여러 개의 attribute들을 모아서 하나의 object를 설명하곤 한다. Object는 또한 여러 분야에서 smaple, record, (data) point, case, entity, instance 등으로 부를 수 있다. 
- Object를 data point라고도 부르는데에는 관점을 살짝 달리하면 이해할 수 있다.  위에서 data에 대해서 table로 표현을 했는데, 이는 결국 2D matrix로 바꿔서 생각할 수 있기 때문이다. 

Attibute values 
- Attribute Value는 attribute에 할당된 number나 symbol을 말한다. 
- 어떤 질문에 대해서 숫자로 대답할 수 있으면 이 숫자가 바로 attribute value가 될 것이고, 숫자가 아니라 어떠한 명칭이 있다면 이 명칭이 attribute value가 될 것이다. 간단하게 yes or no에 대해서 대답할 수 있는 질문에 대해서는 yes or no가 symbol로서 attribute value가 될 것이다. 
- 결국, attribute value형식은 질문하는 형식에 따라 정해지게 되는 것이다. 


Distinction between attributes and attribute values 
- attribute와 attribute value를 구분하는 것이다. 
- Attribute는 일종의 질문에 해당하는 것, attribute value는 대답에 해당하는 것
- 동일한 attribute라도 다른 value를 가질 수 있다. ( 178cm, 1.78 feet) 

Diffrent attribute can be mapped to the same set of values 
- 만약 누군가의 ID와 나이에 대한 attribute를 얻고자 할 때, 둘 다 정수 형태로 대답이 가능하지만 의미상 다른 것을 가리키게 된다. 내 ID가 40이고 나이 또한 40이라고 했을 때 40이라고 했을 때 같은 값 처럼 보이지만 실제로 다른 것을 가리키고 있는 것이다. 

the way you measure an attribute may not match attribute properties 
- 동일한 object를 어떻게 측정하는지에 따라서 완전히 다른 결과를 가져올 수 있다. 

Typle of Attributes 1 

Nominal
- Nominal은 이름과 같은 것으로 ID number, zip code 등과 같은 것으로  이들은 어떤 순서도 가지고 있지 않다.
-  이들은 이들 자체로 중요한 의미를 가지게 된다. 만약 attribute가 nominal attribute에 해당한다면, 누군가가 더 큰 숫자를 가지욌다고 하더라도 실질적으로 순서나 크기와 같은 의미는 존재하지 않는 것이다. 
- 이는 그냥 그 자체로 의미가 있게 된다. 

Ordinal 
- Ordinal은 이제부터 어떠한 비교가 생길 것을 의미한다. 예를 들어, 순위, 성적, 킹 등과 같이 해당 결과를 다른 결과와 비교하여 순서를 매길 수 있으면 이는 ordinal attribute가 되는 것이다. 숫자로도 비교도 가능하지만 tall과 short 처럼 어떠한 문자로도 비교가 가능할 수 있다. 여기서 핵심은 순서가 발생하여 비교가 가능해진다는 것이다. 

Interval 
- Interval의 예시로는 달력의 날짜, 섭씨 온도, 화씨 온도 등이 해당한다. 
- 이들은 숫자로 표현되면서 이들은 상대성이 존재하게 된다. 
- 현재 기온이 섭씨 15도이고 아침의 기온이 섭씨 8도라고 했을 때 현재 기온이 아침의 기온보다 2배 높은 것을 알 수 있다. 하지만 이를 interval attribute에서는 2배 높다고 할 수 없다. 대신 8도의 간격을 두고 차이가 존재한다고 할 수 있다. 
- Interval attribute는 균일한 간격을 두고 측정을 해서 수치 간에 차이가 의미를 가지게 되는 것이다. 

Ratio 
- Ratio는 interval과는 다르게 ‘절대적인 기준’이 존재하게 된다.
- 대표적으로 켈빈 온도가 여기에 해당하며, 길이, 무게, 개수 등 우리가 다루는 대부분이 Ratio Attribute에 해당한다 여기서는 20K가 10K보다 2배 높다고 얘기할 수 있다. 
- Ratio Atrrtibute는 Scale을 보존하는 것을 알 수 있다.
- 그리고 interval attribute와는 다르게 zero point가 존재하여 모든 사칙 연산이 가능하게 된다. 

Types of Attributes 2
Attribute의 type은 각각 가지고 있는 property나 operation에 따라서 나뉘기도 한다.

성질 
1. Distinctness : =, != 
2. Order : <, >
3. Differences are meaningful : +, -
4. Ratios are meaningful : *, /

위의 성질 유무에 따라서 attribute를 나누면 

1. Nominal attribute : distinctness
2. Ordinal attribute : distinctness & order
3. Interval attribute : distinctness & order & meaningful differences
4. Ratio attribute : all 4 properties/operations

Difference between Ratio and Interval
- 10도라는 온도가 5도의 2배라는 물리적인 의미가 있는지에 대해서 살펴봄
- 그리고 온도의 종류에 따라 그 대답이 달라짐 
- 섭씨 온도와 화씨 온도는 interval attribute지만, 켈빈 온도는 ratio attribute이기 때문. 
- Interval attribute에서는 scale과 ratio가 보존되지 않는다. 반면, 켈빈 온도는 절대 온도이기 때문에 zero-point가 존재하고 scale과 ratio가 보존된다. 

<img width="653" alt="Attribute Description" src="https://github.com/kuruma-42/TIL/assets/60722292/c3a52b8f-7c05-484c-aeb5-ed6d425dc564">

￼

- nominal attribute와 ordinal attribute는 categorical qualitative에 해당
- interval, ratio attribute는 numeric quantitative에 해당한다. 
- nominal operation들이 ordinal operation에 적용될 수 있고, ordinal operation들은 interval operation에 적용될 수 있으며, interval operation들은 ratio operation에 적용될 수 있다. 
- 어떤 것이든 nominal, ordinal, interval operation에서 가능하다면, 이는 곧 ratio operation에서도 가능하다는 이야기다. 

<img width="624" alt="Attribute Transformation" src="https://github.com/kuruma-42/TIL/assets/60722292/a9aa3495-9fd3-4f62-b2ab-047915119371">

￼
-  Nominal : Transformation을 보면 nominal attribute의 경우 할 수 있는 것은 오로지 단순하게 치환 혹은 순서를 섞는 것이다.
- Ordinal : Ordinal attribute의 경우 data의 가장 앞단에 transformation을 한다고 했을 때 순서는 보존되어야만 한다. 만약 무작위로 섞는다고 했을 때, ordinal attribute에서 중요한 순서를 파괴하게 된다. 그렇게 되면 ordinal attribute로 존재하지 못하게 되기에 transformation을 한다고 했을 때, 반드시 ordinal data의 경우에 순서는 보존되어야 한다. 기존 값에 f라는 함수를 취해서 새로운 값으로 만든다고 했을 때, f는 monotonic function이어야 할 것이다. 즉, transformation을 적용했을 때 순서가 변하지 않으려면 단순하게 증가하거나 감소하는 형태여야만 한다.
- Interval : Interval attribute의 경우 모든 sample들에 대해서 동일하게 a를 곱해 scale을 바꾸고 b를 더해서 값을 변화시켜도 상관이 없다. 즉, scale과 offset을 그대로 보존하지 않고 변화시켜도 된다는 이야기다. 이러한 경우에 순서도 보존이 될 것이다. 섭씨 온도에 특정 값을 곱해서 특정 값을 더해서 화씨 온도로 변환시킬 수가 있다. 이는 interval attribute이기에 이러한 transformation이 가능한 것이다.
- Ratio : Ratio attribute에서 가장 중요한 성질은 scale이다. 그래서 오로지 할 수 있는 것은 기존 값에 특정 값을 곱하는 것 뿐이다. 만약 키가 2배가 차이나는 두 사람이 있을 때, 두 사람의 키에 특정 값만을 곱하면 그 scale은 보존될 것이다. 하지만 여기에 특정 값을 더하게 된다면 scale이 보존되지 않고 변하게 될 것이다.
- Transformation의 경우 nominal attribute에서 ratio attribute 쪽으로 향할수록 더 제한적이게 된다.

Discrete and Continous Attributes 
symbol은 항상 discrete한 성질을 가지고 있지만, number는 discrete와 continous를 둘 다 가지게 된다. 그렇다면 discrete attribute와 continous attribute의 차이는 무엇이며 어떠한지에 대해 알아보고자 한다. 

Discrete Attribute
Discrete attribute에 해당하는 것은 오로지 finite하거나 countably infinite한 값들의 집합뿐이다. 예를 들면 대학에서 부여하는 성적의 경우가 discrete attribute인 것이다. 이외에도 ‘우리가 셀수 있는 모든 것들’이 discrete attribute이다. 
그리고 binary attribute는 discrete attribute 중에서도 특별한 경우에 해당한다. 

Binary attribute는 0이나 1로 표현되는 attribute로 왼쪽 오른쪽 등 2가지 경우로 표현할 수 있어 Binary attribute는 중요한 개념으로 data mining 문제를 해결하고자 할 때 가장 간단한 경우에 해당하게 된다. 매우 복잡한 경우에 대해서도 binary하게 단순화시켜가면서 문제를 해결할 수 있는 것이다. (비트마스킹과 비슷한 느낌이 들기도) 

Continous Attribute 
Continous attribute는 attribute value로 실수를 취하는 경우들이 해당하게 된다. 
예를들어 온도, 키, 혹은 몸무게 등과 같이 연속된 값의 범위를 가지는 것들이 continous attribute에 해당하게 되는 것이다. 실질적으로, 실수는 finite number를 사용하여 측정되고 표현될 수 있다. 비록 continous attribute가 있다고 하더라도, 컴퓨터에 import할 때에는 어떠한 방식으로든 discrete하게 바꾸게 되어있다. 그래도 여전히 이를 continous attribute라고 부르는 이유는 우리가 이를 continous함을 알고 있기 때문이다. 그리고 countinous attribute는 전형적으로 floating-point variable로서 표현이 된다. 

Asymmetric Attributes 
일반적으로 binary attribute는 2개의 대답 혹은 상태를 나타낼 수 있다. 이 때, 2개의 attribute balue 모두 동일하게 중요한 정보를 지니면 symmetric attribute라 하고, 2개의 attribute의 중요도가 동일하지 않으면 asymmetric attribute라 한다. 
- 남자/여자와 같은 경우는 symmeric attribute에 해당하고, 네/아니오와 같은 경우는 assymetric attribute에 해당한다. 

Only presense(a non-zero attribute value) is regard as important
시작은 엄청나게 많은 양의 sample들과 함께 할 것이다. 여기서 어떠한 sample들이 서로 비슷하고 어떠한 sample들이 서로 다른지에 대해서 알아보고자 하는 것이다. 
이러한 비교를 하고자 할 때는 오직 존재성만이 중요하게 작용한다. 

- 5개의 다른 attribute가 존재한다고 가정 
- 가장 먼저 해야하는 중요한 질문으로는 attribute나 attribute value가 존재하는지 비어있는지에 대한 것.
- 존재성이라는 것은 가장 먼저 해당 attribute가 어떠한 value를 가지고있는지 물어보기 이전에 정말 해당 attribute가 존재하는지 확인해야한다 (여자친구) 
- 그리고 존재성이 확인된다면 어떠한 value를 가지고 있는지 확인하는 것이다. 
- 0이 아닌 attribute value가 있다면 이는 중요하게 생각되어야 한다. 
- 어떠한 두 문서를 비교한다고 했을 때도 아무리 많은 단어를 가지고 있더라도 존재하는 단어 그 자체가 비교하는데 있어 중요하다는 것이다. 

Critiques of the Attribute Categorization 

Incomplete
- 지금까지 이렇게 category를 나눈다는 것은 완벽하지 않다.
- 몇 몇 attribute는 asymmetric binary하고 또 다른 attribe들은 cyclical할 수 있다.  

3. Asymmetric binary (비대칭)
4. Cyclical (순환적)
5. Multivariate (반복성)
6. Partially ordered (부분적 순서) 
7. Partial membership (부분적 포함) 
8. Relationships between the data

Real data is approximate and noisy 
또한 현실 세계에서 data를 얻는다고 했을 때, 흔히 sensor로 데이터를 수집하는 경우에 data에 불필요한 noise가 존재할 수 있다. 그리고 현실로부터 sensor를 거쳐 원하는 patter을 어떠한 방식을 사용해서 얻는데 까지는 무수히 많은 approximation 과정을 거치게 될 것이다. 각각의 단계에서 이전 단계의 결과를 완전히 그대로 받아들이지 않는다는 것이다. 특히 data전체를 완벽하게 설명할 수 없어 대표적인 결과를 전달하는 것이 일반적이다. 

Key Messages for Attribute Types 

The types of operation you choose should be “meaningful” for the type of data you have 

상기에서 살펴본 data의 property로는 distinctness, order, meaningful difference, meaningful ratio가 있고, 오로지 4가지만이 data의 propoerty가 된다. 
만약 data에 대해서 어떠한 operation을 하고자 할 때는 무엇을 하고있는지 확실히 해야만 한다. 반드시 operation을 하고 싶은 data에 대해서 해당 data type을 알고있는 상태로 올바른 operation을 적용해야 한다. 

meaningful 하다는 것은 특정 domain에 대해서만 구체화 될 수 있다는 것이다. 
만약 어떠한 A라는 domain에 대해서 동작하는 것들이 B라는 domain에서는 동작하지 않게 되는 것이다. 사실 이러한 것이 data mining뿐만 아니라 machine learning에서도 문제가 되는 점들 중 하나이다.

















