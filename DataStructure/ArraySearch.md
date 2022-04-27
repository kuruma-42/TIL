

### 검색 (Search)의 정의

성공한 검색 
- Key Element가 배열에 있는 경우
실패한 검색
- Key Element가 배열에 없는 경우

선형 검색 (linear search)
- 완전 검색 (exhaustive search) 또는 순차 검색 (sequential search)
- 배열의 첫 번째 원소부터 차례로 방문하면서 key element와 동일한 원소가 있는지 확인 
- 정렬되지 않은 배열에서도 적용할 수 있다. 

i번째 원소와 key element의 비교 -> 같으면 i를 리턴 
모든 원소 (0 ~ n - 1 번째)에 대해서 비교 
끝까지 같은 원소를 찾지 못했으면 -> -1을 리턴 (실패) 

```c
index linear_search( Array arr, elt x )
for( int i = 0; i < n; i++) {
    if (arr[i] == x)
    return i;
}

return -1; // Null
```

선형 탐색의 시간 복잡도(time complexity)는?
- 최악의 경우 : O(n)
- 평균의 경우 : O(n/2) -> O(n)
- 최선의 경우 : O(1)


이진 검색 (binary search) 
- 분할 정복 (divide & conquer) 알고리즘
- 배열의 중간 원소 (mid element)와 key element를 비교하여 배열을 분할함으로써 검색을 수행
- 정렬된 배열에서만 적용할 수 있음 


재귀적 알고리즘이란? 
- 어떤 문제를 해결하기 위해 알고리즘을 설계할 때 동일한 문제의 조금 더 작은 경우를 해결함으로써 그 문제를 해결하는 것이다. 이런 테크닉을 재귀라고 한다

How to make binary search 

배열에서 검색할 범위를 지정할 것 
- 시작 위치 : S
- 끝 위치 : E 

```c
index binary_search ( Array arr, index s, index e, elt x) {
// 더 이상 분할이 불가능 할 때의 예외적인 경우를 처리해야 한다.
 if ( s == e )
    return (arr[s] == x) ? s : -1; 
int mid = (s + e)/2; 
if ( x == arr[mid]) 
    return mid;
else if (arr[mid] > x )
    return binary_search (arr, s, mid-1, x); 
else 
    return binary_search ( arr, mid+1, e, x);
}
```

```c
index binary_search ( Array arr, int count, elt x) {
int s = 0;
int e = count - 1;
int mid;

while (s <= e) {
    mid = (s + e)/2;
    if (x == arr[mid])
        return mid;
    else if ( arr[mid] > x )
        e = mid - 1 ;
    else 
        s = mid + 1;
    }
    return -1;
}
```

이진 검색의 시간 복잡도 
- O(log n)
- T(n) <- n 개의 데이터에 대해서 검색 (n = s + 1)
- T(n) - T(n/2) + 1 <- Telescoping 

