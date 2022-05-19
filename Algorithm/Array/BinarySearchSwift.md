# Binary Search Swift 

Binary Search LeetCode

Given an array of integers nums which is sorted in ascending order, and an integer target, write a function to search target in nums. If target exists, then return its index. Otherwise, return -1.

You must write an algorithm with O(log n) runtime complexity.

- Example 1:

Input: nums = [-1,0,3,5,9,12], target = 9
Output: 4
Explanation: 9 exists in nums and its index is 4
Example 2:

Input: nums = [-1,0,3,5,9,12], target = 2
Output: -1
Explanation: 2 does not exist in nums so return -1

- Example 2:

Input: nums = [-1,0,3,5,9,12], target = 2
Output: -1
Explanation: 2 does not exist in nums so return -1


 ```swift
 class Solution {
    func search(_ nums: [Int], _ target: Int) -> Int {
        
        var leftIndex: Int = 0
        var rightIndex: Int = nums.count - 1
        while leftIndex <= rightIndex {
            
        var pivot = leftIndex + (rightIndex - leftIndex) / 2
            
            if nums[pivot] == target {
                return pivot
            } else if nums[pivot] > target {
                rightIndex = pivot - 1
            } else {
                leftIndex = pivot + 1
            }
        }
        return -1
    }
}
 ```
