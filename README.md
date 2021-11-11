# Two Pointers

## 15. 3Sum

Share
Given an integer array nums, return all the triplets [nums[i], nums[j], nums[k]] such that i != j, i != k, and j != k, and nums[i] + nums[j] + nums[k] == 0.

Notice that the solution set must not contain duplicate triplets.
```
class Solution:
    
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        nums.sort()
        n=len(nums)
        out=[]
        i=0        
        while i<n:
            front =i+1
            back=n-1
            target= -1*nums[i]
            while front<back:
                sum_val = nums[front] + nums[back]
                if sum_val < target:
                    front+=1
                elif sum_val > target:
                    back-=1
                else:
                    temp=[nums[i], nums[front], nums[back]]
                    out.append(temp)
                    while front< back and nums[front] == temp[1]:
                        front+=1
                    while front < back and nums[back] == temp[2]:
                        back-=1
            i+=1
            if i< n and nums[i] ==nums[i-1]:
                while i< n and nums[i] ==nums[i-1]:
                    i+=1
            
    
            
        return out
```


## 16. 3Sum Closest
Given an integer array nums of length n and an integer target, find three integers in nums such that the sum is closest to target.

Return the sum of the three integers.

You may assume that each input would have exactly one solution.
```
class Solution:
    def threeSumClosest(self, nums: List[int], target: int) -> int:
        nums.sort()
        out=[]
        i=0
        n=len(nums)
        closest=0
        mindiff=float('inf')
        while i<n:
            front=i+1
            back=n-1
            search=target-nums[i]
            while front<back:
                current = nums[front] + nums[back]
                #print(nums[i],",", nums[front],",", nums[back])
                if abs(search-current) < mindiff:
                    
                    mindiff=abs(search-current)
                    closest=nums[front] + nums[back]+nums[i]
                    #print(mindiff,":",closest)
                
                if current < search:
                    front+=1
                elif current > search:
                    back-=1
                else:
                    return closest

            i+=1
            while i<n and nums[i-1]== nums[i]:
                i+=1
        return closest
```            




## 259. 3Sum Smaller

Given an array of n integers nums and an integer target, find the number of index triplets i, j, k with 0 <= i < j < k < n that satisfy the condition nums[i] + nums[j] + nums[k] < target.

 

```
class Solution:
    def threeSumSmaller(self, nums: List[int], target: int) -> int:
        nums.sort()
        n=len(nums)
        out=0
        i=0
        while i<n:
            front=i+1
            back=n-1
            search = target-nums[i]
            while front < back:
                current= nums[front]+nums[back]
         
                if search -current > 0:
                    out+=back-front
                    front+=1
                else:
                    back-=1
            i+=1

        return out
 ```
