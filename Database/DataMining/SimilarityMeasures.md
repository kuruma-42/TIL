# Data Mining Similarity and Dissimilarity - Similarity Measures 

Similarity Between Bianry Vectors 

￼<img width="465" alt="and y was" src="https://github.com/kuruma-42/TIL/assets/60722292/f838ea8a-fc32-4a87-8cc1-1dec98dd98a1">

- binary attribute만을 가지고 있는 object x,y가 있는 상황을 가정한다. 
- 이를 이용해서 우리는 각 element를 비교할 것이다. 
- 총 네 가지 경우의 수가 생긴다. f01, f10, f00, f11 
- f01과 f10의 경우는 각 object들의 disimilarity를 보고자 하는 것이고
- f00과 f11의 경우는 각 object들의 similarity를 보고자 하는 것이다.

SMC vs Jaccard 

Simple Matching 
SMC = number of matches / number of attributes 

￼<img width="406" alt="SMC = number of matches  number of attributes" src="https://github.com/kuruma-42/TIL/assets/60722292/25e62ad2-dbd1-42ae-a114-090cc7762f9c">


Jaccard Coefficients 

￼<img width="493" alt="J = number of 11 matches  number of non-zero attributes" src="https://github.com/kuruma-42/TIL/assets/60722292/015e7d9d-930a-4e3b-83f7-3d95ed8330f4">

- 자카드에서는 f00은 신경쓰지 않고 오로지 f11에 대해서만 신경쓴다.
- non-zero elemet만이 중요한 정보를 가지고 있따고 판단하기 때문이다. 
- 0이라는 element는 어떠한 의미도 내포하고 있지 않다. 
- 그렇기에 non-zero의 경우만 고려해서 similarity를 측정하고자 하는 것이다.
- 그렇기 때문에 Jaccard Coefficient의 식을 보면 Simple matching과는 다르게 둘 다 0이 되는 경우는 제외시킨 것을 알 수 있다. 

￼<img width="492" alt="1000000000" src="https://github.com/kuruma-42/TIL/assets/60722292/3429e016-b7a5-4b33-83eb-a3e323dd7403">


SMC = (0 + 7) / ( 10 ) = 0.7 
Jaccard = 0 / 1 + 2 + 0 = 0 

Cosine Similarity 

￼<img width="540" alt="Pasted Graphic 20" src="https://github.com/kuruma-42/TIL/assets/60722292/666dbe5c-83b0-4f59-8d10-bc13fbdacd14">

-  만약 동일하다면 두 vector사이 각도가 0도가되어 cosine값은 1이 될 것이다. 즉, d1과 d2사이의 similarity 값은 1이 된다.
- orthogonal일 경우( 90도 ) cosine값은 0이 된다. d1 d2사이의 similarity는 0이 될 것이다.
- 
￼<img width="490" alt="Example" src="https://github.com/kuruma-42/TIL/assets/60722292/3ae5f00d-3d65-4d23-bb77-741a8a6f9008">

3*2 + 2 + 1 = 5 
|d1| = ( 9 + 4 + 25 + 4 )^ 2/1 = (42)^2/1 = 6. ~~~ 
|d2| = (1 + 1 + 4) = 6^2/1 = 2.~~~ 
cos(d1,d2) = 0.3150

￼<img width="683" alt="Pasted Graphic 22" src="https://github.com/kuruma-42/TIL/assets/60722292/8e1f8a5f-b82a-4c9c-8004-d152bdeeccf0">

제일 중요한 실습이다. 
똑같이 따라해보겠다. 

Correlation vs Cosine vs Euclidean Distance 

Correalation과 Cosine Similarity는 수식으로 봐도 상당히 유사한 구조다. 
먼저 data가 얼마나 similar한지를 quantification하고 이를 normalization하는 구조였다. 하지만 Euclidean distance는 이들과 좀 다르다 

<img width="616" alt="Compare the three proximity measures according to their behavior under variable transformation" src="https://github.com/kuruma-42/TIL/assets/60722292/4caebb4f-45fa-4bd6-81be-4a7c048c9ade">

- Scaling은 특정 값을 곱하는 것이고(ax), translation은 특정 상수를 더하는 것으로 (x+b)이는 offset이라고 생각하면 된다. 

Scaling
- Cosine Similarity에서 길이는 중요하지 않았따. 즉, scaling에 invariant하다는 것. 
- Correlation 또한 Scaling이 중요하지 않다. 
- 하지만 Euclidean distance의 경우 scaling이 중요하다. 길이가 변하게 되면 Euclidean distance 또한 영향을 받게 된다. 

Translation 
- 만약 translation을 통해서 vector가 이동하게 된다면 어떻게 될까?
- 먼저, Euclidean distance는 naive하게 distance를 구하기 때문에 그 값은 변하게 될 것이다. 
- cosine similarity 또한 각도가 변하기 때문에 결국 방향이 바뀌게 되어 그 결과 또한 변하게 될 것이다. 
- correlation의 경우 크게 상관이 없다. x가 중가할 때 y가 증가하는 상황에서 translation이 이루어져 vector가 이동했따고 하더라도 그 경향성은 변하지 않기 때문이다. 

<img width="472" alt="Consider the example" src="https://github.com/kuruma-42/TIL/assets/60722292/2aacdb8e-e32a-4af2-b2c7-a72cf5322be2">

￼
위의 예시는 x에다가 y와 더불어 scaling과 translation을 적용한 ys,yt를 이용하여 
3가지 similarity를 계산한 결과이다. Cosine Similarity부터 살펴보면 Translation한 결과만 바뀌는 것을 볼 수 있다. Correlation의 경우 Scaling과 Translation에 모두 invariant한 것을 볼 수 있다. 마지막으로 Euclidean distance의 경우 Scalingrhk Translation 모두 바뀐 것을 볼 수 있다. 

Proper Choice of Similarity Measures 
적정한 Proximity Measure를 선택하는 것은 domain에 따라 결정하면 된다. 
Euclidean distance가 널리 사용되고는 있지만 이것이 모든 곳에 사용될 수 있는 것은 아니다. 즉, 우리는 characterization 하고자 하는 data의 성격에 따라서 각자 알맞은 similarity measure를 사용해야 한다. 

그래서 correlation은 [−1,1]의 범위를 가지게 될 것이다. 반면, cosine의 경우에는 [0,1]의 범위를 가지게 되며 Euclidean distance는 흔히 생각하는 거리이기 때문에 [0,∞]의 범위를 가지게 된다. 이러한 특징을 생각하면서 예시를 살펴보도록 하자.

