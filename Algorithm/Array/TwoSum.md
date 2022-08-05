# 1. Two Sum
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

 

Example 1:

Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
Example 2:

Input: nums = [3,2,4], target = 6
Output: [1,2]
Example 3:

Input: nums = [3,3], target = 6
Output: [0,1]

```swift
class Solution {
    func twoSum(_ nums: [Int], _ target: Int) -> [Int] {
    var dict = [Int: Int]()
    for index in 0..<nums.count {
        // Key => Found Value
        if let found = dict[target - nums[index]] {
            // Case Found Value Exist
            return [found, index]
        } else {
            // Key가 없으면 등록 
            // Key에 nums의 Value가 저장되고, Value에 nums의 Index가 저장됨.
            dict[nums[index]] = index
        }
    }
    return []
    }
}

```

