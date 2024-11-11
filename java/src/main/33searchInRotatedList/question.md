Suppose a sorted array is rotated at some pivot unknown to you beforehand.

(i.e., 0 1 2 4 5 6 7 might become 4 5 6 7 0 1 2).

You are given a target value to search. If found in the array return its index, otherwise return -1.

You may assume no duplicate exists in the array.


def rotated(nums, target):
  if not nums:
      return -1
  
  left = 0
  right = len(nums)-1
  while left <= right:
      mid = left + (right-left)//2
      midV = nums[mid]

      if midV == target:
          return mid

      if midV >= nums[left]:
          if nums[left] <= target and target <= nums[mid]:
              right = mid-1
          else:
              left = mid+1
      else:
          if nums[mid] <= target and target <= nums[right]:
              left = mid+1
          else:
              right = mid-1
  return -1
