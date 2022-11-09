# Permutation 
- 순열(permutation)이란 순서가 정해진 임의의 집합을 다른 순서로 섞는 연산을 말한다. 
- nPr => n! / (n-r)! 
- 0! = 1 이다
- 순서와 관계 있다가 중요한 조건이다 

next_permutation (오름차순 기반 순열) C++ 전용 </br>
[first, last]를 매개변수로 넣어줘야한다. ( 순열을 시작할 범위의  첫 번째 주소, 그리고 포함되지 않는 마지막 주소를 넣어서 만든다) 

```swift 
let input = Int(readLine() ?? "")!
var data = [1,2,3]
perm(input)
func perm(_ k: Int) {
    if k == data.count {
        print(data)
        return
    }

    for i in k..<data.count {
        data.swapAt(k, i)
        perm(k+1)
        data.swapAt(k, i)
    }
}
```

# Review 
- 이해가 잘 안 되는 경우는 손으로 도식화 해보면 이해가 간다
- 꼭 도식화를 한 번 쯤은 해볼 것 
