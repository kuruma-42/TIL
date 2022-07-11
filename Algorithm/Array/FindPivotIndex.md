
# Find Pivot Index

Given an array of integers nums, calculate the pivot index of this array.

The pivot index is the index where the sum of all the numbers strictly to the left of the index is equal to the sum of all the numbers strictly to the index's right.

If the index is on the left edge of the array, then the left sum is 0 because there are no elements to the left. This also applies to the right edge of the array.

Return the leftmost pivot index. If no such index exists, return -1.

```swift
class Solution {
    func pivotIndex(_ nums: [Int]) -> Int {
        
        let sum = nums.reduce(0, +)
        
        var leftSum = 0
        var rightSum = sum 
        var pastPivotNum = 0
        
        for idx in 0..<nums.count {
            var pivot = nums[idx]
            
           rightSum = rightSum - pivot
            leftSum = leftSum + pastPivotNum
            
            if rightSum == leftSum {
                return idx
            }
            
            pastPivotNum = pivot
            
        }
        
        return -1
    }
}
```
