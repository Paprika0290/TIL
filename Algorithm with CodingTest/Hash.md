<h1>해시법(Hashing)</h1>
- 데이터를 저장할 위치(인덱스)를 간단 연산으로 구하여 검색, 추가, 삭제를 효율적으로 수행하는 방법

<h3>1. 해시 테이블</h3>
&nbsp;&nbsp;&nbsp; - <b>Key-Value</b> 쌍으로 데이터를 저장하는 자료구조<br>
&nbsp;&nbsp;&nbsp; - Key값에 <b>해시함수</b>를 적용해 고유한 index를 생성, 이 index를 활용해 값을 저장하거나 검색<br>
&nbsp;&nbsp;&nbsp; - 실제 값이 저장되는 장소는 <b>버킷</b> (=해시 테이블의 요소)<br><br>
&nbsp;&nbsp;&nbsp; - 빠르게 데이터를 검색할 수 있다. ( <b>O(1)</b> )<br>
&nbsp;&nbsp;&nbsp; - 적재되지 않는 빈 버킷이 생겨 공간의 낭비로 이어지는 단점 존재 <br>
&nbsp;&nbsp;&nbsp; - 서로 다른 두 키에 대하여 동일한 해시값을 내는 해시 충돌이 발생하기도 한다.

<h3>1-1. 해시 충돌 대처법</h3>
&nbsp;&nbsp;&nbsp; - <b>해시 충돌: </b>이미 채워진 버킷에 또 다른 key값이 저장되어야 하는 경우<br><br>

|충돌 대처법||
|:---:|:---|
|체인법| 해시값이 같은 요소를 연결 리스트로 관리|
|오픈 주소법|빈 버킷을 찾을 때까지 해시를 반복|

<br>
&nbsp;&nbsp;&nbsp;<b>1. 체인법</b> (= 오픈 해시법)<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; - 동일한 버킷의 데이터에 대해 추가 메모리를 사용하여 다음 데이터의 주소를 저장한다. <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; - ex_ key(키 값), data(데이터 값), next(다음 노드에 대한 참조) 세 가지 필드를 가진 Node<K,V> 클래스 <br><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; - <b>장점</b> : 구현이 단순하다.<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;한정된 저장소(bucket)을 효율적으로 사용할 수 있다. (상대적으로 적은 메모리 사용) <br> 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;해시 함수의 중요성이 상대적으로 덜하다.<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;키의 삽입 및 삭제 횟수, 빈도를 알 수 없을 때 사용됨<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; - <b>단점</b> : 캐시 성능이 떨어진다<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;사용하지 않는 bucket이 생길 수 있어 공간 낭비가 발생할 수 있다.<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;한 bucket에 계속해서 값이 저장된다면 체인이 길어져 최악의 경우 검색 시간이 O(n)이 될 수도 있다.<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;다음 노드 참조(next) 저장을 위한 추가 메모리 공간이 필요하다.
<br><br>



&nbsp;&nbsp;&nbsp;<b>2. 오픈 주소법</b> ( = 닫힌 해시법 )<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; - 충돌이 발생했을 때 재해시를 반복수행하여 비어 있는 버킷을 찾아내는 방법 <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; - 오픈 주소법은 저장할 수 있는 원소의 개수가 해시 테이블의 크기로 한정되어 있다. <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ( = 모든 버킷에 원소가 저장되면 더 이상 추가로 원소를 저장할 수 없다.)<br><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; - <b>장점</b> : 해시테이블 내에서 데이터 저장 및 처리가 가능하다 (추가 메모리 필요 x) <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; - <b>단점</b> : 해시 함수의 성능에 전체 해시테이블의 성능이 좌지우지된다.<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;데이터의 길이가 늘어나면 그에 해당하는 저장소를 마련해 두어야 한다.

<h3>1-2. 해시 테이블의 장단점</h3>

- <b>장점</b>: key-value 쌍으로 저장하여 검색이 빠르다.<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;key에 대한 데이터가 있는지 확인이 쉽다.<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;충돌이 없다면 시간복잡도가 O(1)로 짧다.<br>

- <b>단점</b>: 순서가 있는 배열에는 어울리지 않는다.<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;공간효율성이 떨어진다. (일반적으로 저장공간이 많이 필요하다) <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;데이터 충돌이 일어나 체이닝을 사용할 시 O(N)까지 시간복잡도가 증가할 수 있다.<br>

- <b>주 사용처</b>: 검색이 많이 필요한 경우 / 저장, 삭제, 읽기가 빈번한 경우 / 캐시 구현