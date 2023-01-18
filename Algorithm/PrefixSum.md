# Prefix Sum 
- 누적합은 0번째는 비우고 첫 번째 부터 값을 넣는 게 만들기가 편하다
- A에서 B까지의 합을 구한다. 
- 구간 쿼리 문제라고 생각하면 된다 ( 구간에 대한 합이나 곱처럼 쿼리를 하는 문제) 
- 구간 쿼리 문제가 오면 지금은 prefix를 생각하지만 나중에는 펜윅트리를 생각하면 된다. 
- prefix를 쓸 때는 정적 배열일 때 쓴다고 생각하면 된다. 
- 동적 배열 같은 경우에는 누적합을 쓸 수 없으니 펜윅트리를 사용하면 된다.

```swift
let input = readLine()!.split(separator: " ").map { Int(String($0))! }
let n = input[0]
let arr = readLine()!.split(separator: " ").map { Int(String($0))! }
var pSum = [Int](repeating: arr[0], count: n)

for i in 1..<n {
    pSum[i] = pSum[i - 1] + arr[i]
}

let range = readLine()!.split(separator: " ").map { Int(String($0))! }

let low = range[0] - 1
print("LOW : \(low)")
let high = range[1] - 1
print("HIGH : \(high)")
let result = pSum[high] - (low == 0 ? 0 : pSum[low - 1])
print("RESULT : \(result)")

```
