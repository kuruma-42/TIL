Data Mining Data Preprocessing 

Dimensionality 
- 하나의 object를 표현하기 위해 수백 개 혹은 수백만 개의 서로 다른 attribute를 생각해내야하는 경우도 존재한다. 
- 차원이 많다는 것은 해당 object가 매우 복잡하다는 것을 말하는 것이다. 
- 고차원의 data가 존재해도 괜찮은 경우는 그 만큼 많은 object가 존재할 때이다. 

Spartsity 
- Spartsity라는 것은 무수히 많은 0이 존재하는 경우를 말한다. 
- data table이 90%가 0의 값을 가지는 경우는 0보다 0이 아닌 element가 많은 경우가 훨씬 더 유용하게 사용될 것이다, 
- 즉 존재성의 중요함이 필요하다. 
- 드문드문 

Resoloution 
- Data에서 특정 pattern은 scale에 의존할지도 모른다. 
- 만약 물병 전체를 보고 있을 때 바로 물병임을 알 수 있을 것이다.
- 그렇지만 물병의 일부분만 봤을 때는 우리는 물병임을 모를 수 있다. 
- 그래서 특정 pattern은 scale에 의존적일 수 밖에 없다. 

Size 
- attribute의 개수가 너무나도 많아지면 컴퓨터가 이를 다루는데 어려움이 존재한다.
- 컴퓨터에서 알고리즘 동작시킬 때 중요한 computation issue가 발생할 수 있다. 

Data의 이러한 characteristic들을 종합해 봤을 때 data를 다루는 경우에 attribute의 개수에 비해서 충분히 많은 object의 개수가 있는지, 충분히 많은 정보가 있는지, 충분히 적당한 해상도에 측정이 되었는지, data가 내 컴퓨터에 사용될만큼 적절한 크기인지 등 이러한 질문들이 data를 다루기 전에 가장 먼저 확인해야하는 내용들이다.

Types of Datasets 
데이터를 표현하는 방식에도 여러 다양한 방식이 존재한다. 

Record
- Data marix: Data Matrix에서 row는 object를 columndms attribute를 설명하고 있다. 
- Domcument Data: 보통 가공되지 않은 data들이 document의 형식으로 존재하곤 한다. 
- Transaction Data: 여기 item들은 보통 순서를 가지게 된다. 

Graph 
- 그래프의 경우 수많은 variable을 가지게 되는데, 이들이 서로 연결되어있게 된다. 특히, 연결이 임의로 형성된다는 점이 graph의 특징이다. 
    - word wide web, molecular structres 

Orderd 
- Spatial Data
- Temporal Data
- Sequential Data
- Genetic Sequence Data 

여기서 중요한 부분은 이렇게 다양한 형태로 data가 존재할 수 있는데, 이 때 각 data type마다 적용해야 하는 data mining 기법이 다르다는 것이다. 


Record Data 
<img width="299" alt="Tid Refund Marital" src="https://github.com/kuruma-42/TIL/assets/60722292/dc04046a-0026-40d3-a9d4-14518aa76f0d">

￼
- 매우 친숙한 data type일 것이다. 
- 가장 중요한 칼럼은 cheat이라는 attribute이다. 
- 이러한 정보들을 바탕으로 예측하고자 하는 것이 cheat의 유무이다. 

DataMatrix 
<img width="546" alt="Projection Projection" src="https://github.com/kuruma-42/TIL/assets/60722292/917b253f-7bd5-48a6-83ff-fc25bcca132e">

￼
만약 모든 것들이 숫자로 되어져 잇다면, 이는 record data 중에서도 data matrix가 될 것이다. m x n matrix라고 한다면 m개의 object와 n개의 attribute를 표현한 것이다. 

Document Data 
- 사람들이 흔히 term vector로서 document를 vector 형식으로 설명하고자 하는 것이다. 그리고 각 vector에서 elemet가 하는 일을 각각의 term을 표현하는데 사용된다. 여기서 각 term은 vector componet혹은 attribute에 해당하게 된다. 
<img width="516" alt="Document 1" src="https://github.com/kuruma-42/TIL/assets/60722292/ab464b70-9256-4050-8b53-dc723c18ba93">

￼
- 예를 들어, 각 documnet가 위와 같은 attribute를 포함하고 있다고 했을 때 각 element가 설명하고자 하는 것은 얼마나 해당 단어가 등장했는지이다. 이러한 방식이 document를 term vector로서 흔히 사용하는 방식인 것이다. 
- 즉, 각 componet의 값은 document에서 해당하는 term이 얼마나 등장했는지를 나타내게 된다. 


Transaction Data 
￼<img width="404" alt="Bread  Coke, Milk" src="https://github.com/kuruma-42/TIL/assets/60722292/eb56c787-5e0b-4c04-a515-5695a981d701">

- 개별 구매 제품은 item에 해당하게 된다. 
- 구매한 제품 set은 transaction을 구성한다. 
- 결국에는 우리는 위와 같은 data를 table로 보게되면 각 제품을 구매했는지 하지 않았는지 설명 할 수 있는 것이고, 이는 term vector와 유사하다고 볼 수 있다. 

핵심은 이러한 matrix에서 0d이 아닌 value들의 존재성이다. 
위의 document data를 보면 매우 많은 0이 존재하는 것을 알 수 있다. 
그래서 0이 아닌 value들이 의미를 가지게 되는 것이다. 
document data 에서는 document를 비교하기 위해서 0이 아닌 value들을 참고하게 되는 셈이다. 

Graph Data 
￼<img width="428" alt="Benzene Molecule C6H6" src="https://github.com/kuruma-42/TIL/assets/60722292/71cceab0-6d33-49a2-8256-bd8a157d113d">

graph data는 node와 edge로 되어있는 data type으로, node들은 edge를 통해서 
연결되어 있다. 여기서 edge에는 방향성이 존재할 수도 있고 아닐 수도 있는 것이다. 이러한 data는 매우 흔하지만 사용되는데는 어려움이 존재한다. Graph data가 사용되는 예시로는 generic graph, molecule, webpage, social network, brain network들이 있다. 

Ordered Data 
￼<img width="652" alt="( A B) (D) (C E)" src="https://github.com/kuruma-42/TIL/assets/60722292/246b6bfc-e2fb-47ee-94a4-7f725d019f0f">


- Ordered Data에서 중요한 것은 순서이며, transaction data에 순서가 존재하는 버전이 대표적인 예시 중 하나이다. 
- 위와 같이 item들의 순서가 존재하며 (AB)와 (BA)는 서로 다른 item에 해당하게 된다.
- 때로는 이러한 순서가 중요한 의미를 가지기도 하며, 이러한 예시로는 genomic sequence data가 있다 여기에는 GTCA특정한 순서로 존재하게 되는데 이는 Pattern을 형성하게 된다. 이러한 순서는 특정 질병과 연관지을 수 있고, 사람의 특징을 설명할 수 있다. 
- 

Saptio-Temporal Data 
￼<img width="653" alt="Average Monthly Temper" src="https://github.com/kuruma-42/TIL/assets/60722292/0ca1c23f-2392-4b2d-88ef-bc7277365385">

- Saptio-Temporal data는 이름에서부터 알다시피 space와 time이 결합되어 사용하는 data이다. 
- 위의 예시는 시간의 흐름에 따라 변화하는 월평균 기온을 보여주는 것인데, space는 2차원으로 지구상의 위치를 알려주고있으며 time으로는 한 달 마다 변화하고 있다. 

Data Quality 

Poor data quaility negatively affect many data processing efforts 
- Data를 얻고자 할 때 sensor를 이용해서 수집을 하기도 하고, 가령 선생님이 같은 교실에 있는 학생들에게 속삭이며 말을 할 때 선생님과 거리가 먼 학생들의 경우 다르게 들릴 수도 있을 것이다.
-  즉, 자연적으로 data를 온전히 받아들이지 못하는 경우가 많으며 대부분은 data의 quality가 떨어지는 현상이 발생한다. Data quality에 따라 이후의 영향력의 차이는 굉장히 크기 때문에 data quality는 고려해야하는 부분 중 하나이다.

Data mining example: a classfication model for detecting for detecting people who are loan risks is built using poor data 
- 신용도가 높은 몇몇 지원자들은 대출을 거절당하고, 더 많은 대출이 채무 불이행 개인들에게 주어진다. 이러한 경우에 문제는 은행의 경우 파산의 위험이 존재한다. 
- 그렇다면 어떠한 종류의 data quailty 문제가 존재하는 것일까? data에 대해서 어떻게 발견할 수 있을까? 

1. Noise and outliers: 하나의 outlier가 우리의 prediction model에 굉장한 타격을 입힐 수 있다. 
2. Wrong data: 보통 이러한 data는 사람의 실수나 sensor의 문제로부터 만들어지게 된다. 
3. Fake Data: 이는 사람의 의도로 만들어져 대중들에게 영향력을 행사할 수 있다. 
4. Missing Values
5. Duplicate Data : 사람의 경우 문제가 되지 않지만 컴퓨터의 경우에는 연산하는데 있어서 큰 문제를 야기할 수 있다. 

Noise 
Data에서 주목하고 싶은 pattern을 object라고 했을 때, 우리는 이러한 object를 찾기를 원하며 noise의 경우에는 불필요한 object에 해당하게 된다. 우리는 data로부터 특정 pattern을 얻기를 원하는데 원하지 않는 object인 noise가 존재할 수 있으며, 사실 이러한 object를 분리시키는 기법들도 많이 존재한다. 그리고 obejct를 설명하기 위한 attribute에 대해서 noise는 원래 value의 수정을 의미한다. True value가 있다고 가정해보자. 여기에 noise가 추가가 된다면 원래 value와는 다른 결과를 만들어 낼 것이다. 우리가 흔히 sensor를 통해서 측정되는 결과는 true value와 noise가 더해진 형태일 것이다.

￼<img width="655" alt="Pasted Graphic 11" src="https://github.com/kuruma-42/TIL/assets/60722292/ec9fdf2f-ec10-4399-b1d1-f9a64f245be5">



Outliers 
￼<img width="387" alt="Pasted Graphic 12" src="https://github.com/kuruma-42/TIL/assets/60722292/b1e7680a-f72d-45ec-9af5-5239bd3afbc2">

- clustering을 통해 outlier의 존재를 파악할 수 있다. 
- Data object를 point라고 할 수 있는 이유는 data가 vector로 표현되기 때문 
- 위의 예시는 cluster와 3개의 point를 보여주고 있으며 3개의 cluster에도 속하지 않아 이를 outlier라 부를 수 있다.
- Outlier는 data alalysis를 방해하는 noise로 볼 수도 있고, 특정한 pattern을 찾아내는데 방해되는 존재로 간주되기도 한다. 그리고 현실에서는 안전과 관련된 많은 문제들에서 outlier를 찾아내는 것은 매우 중요하다. 

Mssing value 
- 정보가 수집되지 않거나 특정 attribute가 모든 case에 적용되지 않기 때문이다. 
- 사람들은 개인정보를 제공해주는 사례가 줄어들게 되고, 연간 소득과 같은 경우는 어린 아이에게는 해당하지 않는다. 
- massing value 핸들링은 극단적인 해결 방안으로 data object를 없애버리면 된다. 아니면 missing value가 있는 공간에 특정 값을 추정해서 채워 넣을 수도 있다. 특히 시간과 관련있는 기온이나 인구 조사 결과와 같은 경우에는 어느정도 추정이 가능하게 된다. 아니면 추천하지는 않지만 data analysis 동안 missing value를 무시하는 방안도 있다. 

    1. Eliminate data objects or variables
    2. Estimate missing values
    3. Ignore the missing value during analysis

Duplicate Data 
Data set에는 중복되거나 거의 서로 중복되는 data object가 포함될 수 있다. 
이는 주로 다른 종류(heterogeneous)들로 이루어진 source의 data를 병합할 때 주요 문제가 된다. 예시로는 동일한 사람이 사용하는 여러 개의 이메일 주소가 이에 해당한다. 내가 주로 사용하는 학교 이메일 계정을 A라는 database에 제공하고, 개인적으로 사용하는 이메일 계정을 B라는 database에 제공했을 때 이를 병합하려고 하면 서로 다른 이메일이지만 동일한 사람의 것이라서 문제가 된다. 

이러한 dupicate data문제를 해결하는데 있어서 data cleaning이라는 process 기술이 사용된다. 하지만 이러한 기술의 경우 data를 지우는데 많은 비용을 소모하게 된다. 
