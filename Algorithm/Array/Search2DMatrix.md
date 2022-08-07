# 74. Search a 2D Matrix

Write an efficient algorithm that searches for a value target in an m x n integer matrix matrix. This matrix has the following properties:

Integers in each row are sorted from left to right.
The first integer of each row is greater than the last integer of the previous row.
 

Example 1:


Input: matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 3
Output: true
Example 2:


Input: matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 13
Output: false

```swift
class Solution {
    func searchMatrix(_ matrix: [[Int]], _ target: Int) -> Bool {
        
         guard matrix.count != 0 && matrix[0].count != 0 else{
            return false
        }
        
        var yLeft = 0
        var yRight = matrix.count - 1
        
        // Binary Search 
        while yLeft <= yRight {
            var yPivot = yLeft + (yRight - yLeft) / 2
            if matrix[yPivot][0] < target {
                // Binary Search 
                var xLeft = 0 
                var xRight = matrix[yPivot].count - 1
                
                while xLeft <= xRight {
                    var xPivot = xLeft + (xRight - xLeft) / 2
                    if matrix[yPivot][xPivot] < target {
                        xLeft = xPivot + 1
                    } else if matrix[yPivot][xPivot] == target {
                        return true
                    } else if matrix[yPivot][xPivot] > target {
                        xRight = xPivot - 1
                    }
                }
                yLeft = yPivot + 1
            } else if matrix[yPivot][0] == target {
                return true 
            } else {
                yRight = yPivot - 1
            }
        }
        return false
    }
}
```

### Review 
처음에는 Brute Force로 풀 때는 쉬운 문제였다, 
조금 성능을 좋게 만들고자 X축과 Y축 탐색에 Binary Search를 적용해서 풀었다.
Binary Search를 외워서 풀다가 Pivot 설정하는 공식에서 헷갈려서 조금 시간이 걸렸다. 

```swift 
var pivot = leftIndex + (rightIndex - leftIndex) / 2
```
상기의 피벗 공식을 적용하자 문제가 금방 풀렸다. 
Binary Search를 다시 한 번 살펴보는 계기가 되서 좋았다.
