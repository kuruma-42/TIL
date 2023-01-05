# Combination
- n개의 원소에서 r 개의 원소를  순서에 상관없이 뽑는 경우의 수 
- 조합에서 “순서” 는 상관이 없다. 
- nCr = n! / r!(n-r)

* 4개 이상 재귀함수로 구현 
* 3개 이하는 중첩For문 구현 (구현이 쉽기 때문 ) 


int n = 5 
k = 3
a[5] = {1,2,3,4,5}

```swift
var n = 5
var k = 3
var a = [1,2,3,4,5]
var container: [Int] = []
var count = 0

public func combination(start: Int, b: inout [Int]) {
    if b.count == k {
        count += 1
        print("cnt :: \(count) result :: \(b)")
        return
    }
    
    for i in (start+1)..<n {
        b.append(i)
        combination(start: i, b: &b)
        b.popLast()
    }
}
```
