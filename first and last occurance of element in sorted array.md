## first and last occurance of element in sorted array
Given an array of integers nums sorted in non-decreasing order, find the starting and ending position of a given target value.
If target is not found in the array, return [-1, -1].
You must write an algorithm with O(log n) runtime complexity.

Example 1:

Input: nums = [5,7,7,8,8,10], target = 8
Output: [3,4]
Example 2:

Input: nums = [5,7,7,8,8,10], target = 6
Output: [-1,-1]
Example 3:

Input: nums = [], target = 0
Output: [-1,-1]

## APPROACH : - 

USE BINARY SEARCH LOOP RESPECTIVELY FOR FIRST AND LAST OCCURANCE OF TARGET.
FOR FIRST OCC - IF ELEMENT FOUND THEN STORE THE INDEX AND TARMINATE RIGHT HALF AND SEARCH IN LEFT HALF.
FOR LAST OCC -  USE ABOVE APPROACH AND AFTER FINDING ELEMENT TARMINATE LEFT HALF AND SEARCH IN RIGHT HALF.

JAVA CODE  
```
class Solution {
    public int[] searchRange(int[] nums, int target) {
        int ans[]=new int[2];
        int beg=0,end=nums.length-1;
        int left=-1, right=-1;
        while(beg<=end){
            int mid =(beg+end)/2;
            if(nums[mid]==target){
                left=mid;
                end=mid-1;
            }else if(nums[mid]<target){
                beg=mid+1;
            }else{
                end=mid-1;
            }
        }
        beg=0; end=nums.length-1;
        while(beg<=end){
            int mid =(beg+end)/2;
            if(nums[mid]==target){
                right=mid;
                beg=mid+1;
            }else if(nums[mid]<target){
                beg=mid+1;
            }else{
                end=mid-1;
            }
        }
        ans[0]=left; ans[1]=right; return ans;
    }
}
