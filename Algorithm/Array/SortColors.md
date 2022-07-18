# 75. Sort Colors

Given an array nums with n objects colored red, white, or blue, sort them in-place so that objects of the same color are adjacent, with the colors in the order red, white, and blue.

We will use the integers 0, 1, and 2 to represent the color red, white, and blue, respectively.

You must solve this problem without using the library's sort function.

```swift 

class Solution {
    func sortColors(_ nums: inout [Int]) {
        
        var idx0 = 0
        var idx2 = nums.count - 1 
        var i = 0
        
        while i <= idx2 {
            if nums[i] == 0 {
                nums.swapAt(idx0, i)
                idx0 += 1
                i += 1
            }
            
            else if nums[i] == 2 {
                nums.swapAt(idx2, i)
                idx2 -= 1
            }
            
            else {
                i += 1
            }
        }
        
        }
    
}








/// Description : Wrong Answer 
class Solution {
    func sortColors(_ nums: inout [Int]) {
        
        var idx0 = 0
        var idx2 = nums.count - 1 
        
        for idx in 0..<nums.count {
            if nums[idx] == 0 {
                nums.swapAt(idx0, idx)
                idx0 += 1
            } else if nums[idx] == 2 {
                if idx < idx2 {
                    nums.swapAt(idx, idx2)
                    idx2 -= 1
                }
            }
        }
    }
}


```
