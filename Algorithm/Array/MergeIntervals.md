# 56. Merge Intervals
Given an array of intervals where intervals[i] = [starti, endi], merge all overlapping intervals, and return an array of the non-overlapping intervals that cover all the intervals in the input.

 

Example 1:

Input: intervals = [[1,3],[2,6],[8,10],[15,18]]
Output: [[1,6],[8,10],[15,18]]
Explanation: Since intervals [1,3] and [2,6] overlap, merge them into [1,6].
Example 2:

Input: intervals = [[1,4],[4,5]]
Output: [[1,5]]
Explanation: Intervals [1,4] and [4,5] are considered overlapping.
 
 
 ```swift
 class Solution {
    func merge(_ intervals: [[Int]]) -> [[Int]] {
        
        var sortedIntervals = intervals.sorted {$0[0] < $1[0]}
        var targetIndex = 0
        var pivotIndex = 1
        var intervalsCount = sortedIntervals.count - 1
    
        while targetIndex < intervalsCount {
            
            let target = sortedIntervals[targetIndex]
            let pivot =  sortedIntervals[pivotIndex]
            let targetEndIndex = target[1]
            let pivotStartIndex = pivot[0]
            
            if targetEndIndex >= pivotStartIndex {
                
                if sortedIntervals[pivotIndex][1] > sortedIntervals[targetIndex][1] {
                    sortedIntervals[targetIndex][1] = sortedIntervals[pivotIndex][1]
                }
                
                sortedIntervals.remove(at: pivotIndex)
                intervalsCount -= 1
            } else {
                
                targetIndex += 1
                pivotIndex += 1 
                
            }
        }
        return sortedIntervals
    }
}
 ```
 
 ### Review 
 - 주어진 값을 그래프나 표로 나타내보면 조금 더 빠르게 문제에 대한 인사이트를 얻을 수 있는 것을 깨달음
 - 예전 보다는 Array에 여러 개의 인덱스를 쓰는 것에 익숙해짐 
 - 연습장에 문제를 파악하고 설계하는데 시간을 많이 쓰고 코딩은 30분 내외로 했는데, 효율이 더 좋음
