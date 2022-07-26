# 162. Find Peak Element

A peak element is an element that is strictly greater than its neighbors.

Given a 0-indexed integer array nums, find a peak element, and return its index. If the array contains multiple peaks, return the index to any of the peaks.

You may imagine that nums[-1] = nums[n] = -∞. In other words, an element is always considered to be strictly greater than a neighbor that is outside the array.

You must write an algorithm that runs in O(log n) time.

 

Example 1:

Input: nums = [1,2,3,1]
Output: 2
Explanation: 3 is a peak element and your function should return the index number 2.
Example 2:

Input: nums = [1,2,1,3,5,6,4]
Output: 5
Explanation: Your function can return either index number 1 where the peak element is 2, or index number 5 where the peak element is 6.

```swift
/// Description : O(log n) 배열 문제에서 봤으면 Binary Search를 생각해봐야 한다.
/// SeeAlso : Peak문제를 풀 때는 그래프를 한 번 그려보자, 조금 더 문제에 인사이트가 생길 수 있다.
class Solution {
    func findPeakElement(_ nums: [Int]) -> Int {
        
        if nums.count <= 0 {
            return 0 
        }
      
        var left: Int = 0
        var right: Int = nums.count - 1 
        
        
        while left < right {
            
            var pivot: Int = ( left + right ) / 2
            var num = nums[pivot]
            var nextNum = nums[pivot + 1]
            
            if nextNum > nums[pivot] {
                left = pivot + 1 
            } else {
                right = pivot 
            }
            
        }
        
        return left
        
    }
}


/// Description: 한 번에 풀어서 좋아했지만 O(n)으로 풀어서 문제의 조건에 부합하지 않는다. 
class Solution {
    func findPeakElement(_ nums: [Int]) -> Int {
        var greatIdx = 0
        
        for idx in 0..<nums.count {
            if nums[greatIdx] <= nums[idx] {
                greatIdx = idx 
            }
        }
        
        return greatIdx
    }
}


```
