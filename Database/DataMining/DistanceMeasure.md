# DataMining Similarity and Dissimilarity - Distance measure 

Similarity and Dissimilarity 
- 어떠한 두 가지가 비슷하다고 한다는 것은 그것들을 quantification 할 수 있다면, 이들이 서로 다른지 아닌지도 quantification 할 수 있다. Similarity와 dissimilarity는 정반대의 것을 필요로 하지만 similarity를 측정하게 되면 이는 곧 dissimilarity를 측정하는 것으로 이어지게 된다. 

Measure

Similarity Measure 
- Similarity measure는 두 data object들이 얼마나 유사한지를 나타내는 numerical한 measure이다. 
- 예를 들면 오른손과 왼손이 각각 존재한다고 가정했을 때 이들은 서로 다른 object이고 이들 사이에 similarity를 측정할 수 있을 것이다. 
- 만약 similarity가 높게 나왔다면, data object들은 서로 유사함을 의미하게 된다. 
- 하지만 그 값이 0에 가깝다면 object들은 서로 유사하지 않음을 의미하게 될 것이다. 
- 그래서 일반적으로 similarity는 [0,1]이라는 범위 내에서 설명하게 된다. 

Dissimilarity Measure 
- Dissimilarity Measure은 두 data object들이 얼마나 서로 다른지를 나타내는 numerical measure이다
- Similarlity와는 반대로 그 값이 낮을 수록 object들이 서로 유사하게 되는 것이다.
- 일반적으로 dissimiliarity의 최소는 0이고 최대는 제한 없이 얼마든 커질 수 있다. 
- Similarity는 일반적으로 0과 1사이에서 그 값이 형성되며 dissimilality와는 반대되는 관계를 가지게 된다. 
- 그래서 2개의 object가 매우 다른 상황을 반대로 생각하게 되면 아마 dissimilarity measure의 값은 무한대로 커질 것이고, 1을 넘어가게 되면 similarity measure의 0과 같아질 것이다. 

Proximity 
- Proximity라는 용어는 상황에 따라 similarity를 나타낼 수 도 있고, Dissmilarity를 나타낼 수 도 있다. 그래서 이 둘을 합쳐서 proximity라는 용어를 사용할 수 있다. 

Simple Attributes 
- Data mining에서 2개의 data object가 있을 때, 우리는 data가 서로 어떻게 생겼는지 알 수가 있다. 예를 들어 data matrix가 있고, row는 data obejct가 있고 column으로는 feature가 있다고 해보자. 우리가 여기서 하고자하는 일은 특정 2개의 object의 similarity와 dissimilarity를 구하고자 하는 것이다.
- Data mining에서 comparision은 정말로 중요한 개념이다. 왜냐하면 하나를 다른 것과 비교한다는 것은 자신을 제외한 유사한 cluster에서 유사한 data를 aggregation하는 방법에 대해서 말하고 있는 것과 같기 때문이다. 그렇기 때문에 similarity를 정의하는 것은 정말 중요하며, 여기에 필요한 것은 하나의 object가 다른 object와 얼마나 비슷한지에 대한 정보이다. 그렇다면 이러한 정보들을 어떻게 해서 알 수 있을까? 바로 attribute value들을 이용하면 된다.
- Attribute value는 각 object를 설명할 수 있어서 attribute value를 통해서 각 attribute를 comparison에 사용하곤 한다.

￼<img width="593" alt="Attribute" src="https://github.com/kuruma-42/TIL/assets/60722292/8acddef6-c297-4ae4-b020-9ad0e263c077">

Nominal 
- nominal attirbute를 사용하게 되면 이를 통해 오로지 object들이 같거나 다른지만 설명하게 된다.
- 같은 object라면 similarity는 1이 될 것이고, dissimilarity는 0이 될 것이다. 

Ordinal 
- Ordinal attribute의 경우에는 2개의 object의 difference를 계산해서 n - 1로 나누어  dissimilarity를 구하면 된다.
- 여기서 n - 1로 나누는 이유는 d 값을 적절한 값에 mapping하기 위해서다. 
- 이와 다르게 similarity는 간단하게 1에서 dissimilarity 값을 빼주면 된다.
- Dissimilarity값을 최종적으로 구하게 되면 값의 범위는 0 - 1사이가 될 것이다. 
- 때문에 similarity는 1에서 빼주는 것이고, 이렇게 함으로서 ordinal similarity를 구하게 되는 것이다. 

Interval / Ratio 
- interval과 ratio attribute의 경우에는 dissimilarity는 그저 두 object의 difference만 계산해주면 된다. 
- 중요한 점은 이러한 방법이 유일한 것은 아니며, dissimilarlity를 어떻게 구하는지에 따라서 이에 대응되게 similarity를 구해줄 수 있따. 그렇기 떄문에 similarity와 dissimilarity의 경우 inverse relation을 갖는다. 


Euclidean Distance 

￼<img width="390" alt="Pasted Graphic 14" src="https://github.com/kuruma-42/TIL/assets/60722292/22f6be51-2def-426e-891e-26c9bf773ef4">

- 우리가 흔히 배우는 2개의 point사이의 길이를 Euclidean distance라고 한다. 
- n차원 가상 공간 상에 있을 때 서로 대응되는 index간 차이를 구해서 제곱해서 더해준 뒤 결과적으로 root를 취해주면 된다. 
- Euclidean distance의 값이 커지게 되면 서로 다르다는 것이고, 반대로 값이 작아지게 되면 서로 유사하다는 의미가 된다. 이 때 attribute value들의 경우 만약 sacle이 다른 경우에는 standardization이 필수적이게 된다. 왜냐하면 attribute value들의 경우 만약 scale이 다른 경우에는 standardization이 필수적이게 된다. 
- attribute value가 다르다는 것은 일반적으로 서로 다른 distribution을 형성하게 될 것이기에, scale을 맞춰서 standard normal distribution을 따르도록 standardization 과정이 동반 되어야 한다. 
￼<img width="609" alt="Pasted Graphic 15" src="https://github.com/kuruma-42/TIL/assets/60722292/f54bec4b-ffa4-46ec-85a8-4bd67c3318eb">


위와 같이 4개의 서로 다른 point가 있다고 했을 때, 각 point 별로 distance를 측정할 수 있다. 여기서 point는 data object, x와 y는 coordinate를 attribute value로 가지는 attribute가 된다. 2차원에서 object들이 scatter point로 존재하고 있는 상태이고, distance matrix를 보면 각 object 사이의 distance가 기록되어져 있다. 여기서의 distance는 위에서 살펴 본 Euclidean distance를 사용했고, 각 point들을 연결한 길이를 symmetric하게 표기한 것이다.

Common Properties
1. Distance 
Eucliean distance와 같은 distance들은 잘 알려진 property들을 가지고 있다. d(x,y)를 2개의 data object x,y 사이의 distance(dissimilarity)라고 한다면, distance는 다음과 같은 성질들을 만족하게 된다.
* (1) d(x,y)≥0 for all x and y and d(x,y)=0 if and only if x=y
* (2) d(x,y)=d(y,x) for all x and y. (Symmetry)
* (3) d(x,z)≤d(x,y)+d(y,z) for all points x,y and z. (Triangle Inequality)
위 3가지 property를 만족하는 distance를 우리는 metric이라고 한다. 우리는 metric이란 것을 이용해서 무언가를 측정하는데 사용할 수 있다.

2. Similarity
Similarity 또한 잘 알려진 property들이 존재한다. Distance가 dissimilarity를 나타냈다면, 이번에는 그 반대되는 개념으로 similarity를 살펴보고자 한다. Similarity의 경우 2개의 object가 동일한다면 maximum similarity로 1의 값을 가지게 된다. 다시한번 차이점을 되새겨보면 similarity의 경우 maximum으로 1의 값을 가지지만, dissimilarity의 경우 maximum으로 ∞의 값을 가지게 된다. s(x,y)를 2개의 data object x,y 사이의 similarity라고 한다면, similarity는 다음과 같은 성질들을 만족하게 된다.
* (1) s(x,y)=1 (or maximum similarity) only if x=y (does not always hold, e.g. cosine)
* (2) s(x,y)=s(y,x) for all x and y. (Symmetry)
