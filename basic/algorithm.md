# 면접 준비 - 알고리즘
> 나만의 언어로 정리하는 면접 준비  

## 목록
- [시간복잡도](#알고리즘의-시간-복잡도)
- [정렬](#정렬)
- [이분 탐색](#이분-탐색)
- [HashTable](#hashtable)
- [BFS vs DFS](#bfs-vs-dfs)

---

## 알고리즘의 시간 복잡도
> 알고리즘의 시간복잡도를 나타내는 방법은 총 3가지가 있다.

- 오메가표기법 : 최상의 시간 복잡도 표기
- 세타 표기법 : 평균적인 시간 복잡도 표기
- 빅오 표기법 : 최악의 시간 복잡도 표기

#### 빅오(Big-O)표기법
- 해당 알고리즘에서 성능에 가장 큰 영향을 미치는 부분의 최악의 시간 복잡도를 표기한 것
- O(n!) > O(2^n) > O(n^2) > O(nlogn) > O(n) > O(logn) > O(1) 순으로 오래 걸린다.

#### 자료구조 별 시간 복잡도

###### ArrayList
- 삽입/삭제
    - 맨뒤 : O(1) 인덱스 접근 후 삽입/삭제 가능
    - 중간/맨앞 : O(N) 삽입/삭제 후 배열 복사
- 조회
    - O(1) 어느 위치나 인덱스로 접근 가능

- 사용
    - 데이터 개수가 정해졌을 때
    - 데이터 삽입/삭제 에 비해 조회 작업이 많을 때

###### LinkedList
- 삽입/삭제
    - 맨 앞/맨 뒤 : O(1)
    - 중간 : O(N) 탐색을 해야 한다.
- 조회
    - O(N) 인덱스 개념이 없기 때문에 하나하나 접근해야한다.

- 사용
    - 데이터 개수가 동적일 때
    - 데이터 검색에 비해 삽입/삭제 작업이 많을 때

###### Tree
- 트리의 경우 평균 시간과 최악의 시간이 다르다
- 삽입/삭제/조회
    - 완전 이진트리의 경우 O(logN)
    - 편향 이진트리의 경우 O(N)

###### 인접 행렬 vs 리스트
||행렬|리스트|
|--|--|--|
|node 추가|O(N^2)|O(1)|
|node 삭제|O(N^2)|O(N+E)|
|edge 추가|O(1)|O(1)|
|edge 삭제|O(1)|O(E)|

[위로](#목록)

---

## 정렬
#### 버블 정렬
- 인접한 원소와 조건에 따라 자리를 바꾸며 가장 끝자리 원소부터 결정해 나가는 방식
- 시간복잡도는 O(N^2) 이다.
- 공간복잡도는 swap 을 통해 이루어 지므로 O(N) 이다.
#### 선택 정렬
- 타겟으로 설정한 위치에 어떤 원소가 올지 선택하는 방식
- 타겟 설정 후 타겟 인덱스부터 끝까지 순회 후 조건에 맞는 원소 와 타겟값의 자리를 바꾼다.
- 시간 복잡도는 O(N^2) 이다.
- 공간 복잡도는 swap 을 통해 이루어 지므로 O(N) 이다.
#### 삽입 정렬
- 타겟은 2번째 원소부터 시작한다. 타겟부터 앞쪽 원소를 비교하며 조건에 따라 자리를 바꾸는 방식
- 만약 조건에 부합하지 않다면 종류 후 타겟 하나 증가
- 시간 복잡도는 모두 정렬이 되어 있는 경우 O(N) 이며, 최악의 경우 O(N^2) 이다.
- 공간 복잡도는 swap 을 통해 이루어 지므로 O(N) 이다.

#### 퀵 정렬
- 분할 정복으로 이루어 진다.
- 피벗을 통해 영역 분할을 한 후, 분할된 영역을 정렬한다. 모든 영역을 분할 - 정복을 반복하며, 정렬이 끝나면 합친다.
- 평군 O(NlogN) 이 걸리며 이미 선택한 피벗이 범위 내 가장 크거나 작은 경우 O(N^2) 이 걸린다.
- swap 을 통해 이루어 지므로 O(N) 이다.
#### 병합 정렬
- 영역을 쪼갤 수 있는 만큼 쪼갠 후 합치면서 정렬을 한다.
- 시간복잡도 O(NlogN)이 걸린다.
- 공간복잡도 여러 개의 배열을 잡지만 O(N) 의 상수배 이므로 O(N) 으로 생각된다.
- 퀵정렬은 피벗을 통해 정렬 후 영역을 나누는 것을 반복
- 병합 정렬은 먼저 쪼갠 후 합치면서 정렬

[위로](#목록)

---

## 이분 탐색
- 기준점을 잡은 후 기준점보다 클 경우 오른쪽, 기준점보다 작을 경우 왼쪽만 탐색
- 먼저 정렬이 이루어 져야 함.
- 시간 복잡도 logN

[위로](#목록)

---

## HashTable
- 입력 값에 해당하는 해쉬값을 얻어서 해당 값을 키로 배열에 입력 유무를 저장한다.
- 모든 인풋값을 비교하지 않고 특정 값만 비교하기 때문에 중복 체크 비용이 O(1) 이다.
- 소수를 이용해서 이를 변환해야함 ( 17, 19, 23, 31 등.. )

[위로](#목록)

---

## BFS vs DFS

- DFS 는 모든 노드를 탑색해야 할 때 
- BFS 는 최소/최대 비용을 탐색해야 할 때

||BFS|DFS|
|--|--|--|
|구현방식|Queue|Stack|
|인접행렬|O(N^2)|O(N^2)|
|인접리스트|O(N+E)|O(N+2)|

[위로](#목록)



