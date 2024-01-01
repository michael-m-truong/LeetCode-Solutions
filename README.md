# LeetCode-Solutions

## Two Sum

```
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        store = dict()
        for i, num in enumerate(nums): 
            diff = target - num
            if diff in store:
                return [store[diff], i]
            store[num] = i
```

## Add Two Numbers

```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        dummy = ListNode()
        curr = dummy
        carry = 0
        while l1 != None or l2 != None or carry != 0:
            val1 = l1.val if l1 != None else 0
            val2 = l2.val if l2 != None else 0
            total = val2 + val1 + carry
            carry = total // 10

            curr.next = ListNode(total % 10)
            curr = curr.next

            l1 = l1.next if l1 != None else l1
            l2 = l2.next if l2 != None else l2
        return dummy.next
```

## Product of Array Except Self
```
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        res = [1] * len(nums)
        temp = nums[0]

        for i in range(1, len(nums)): 
            res[i] = temp
            temp *= nums[i]
        
        temp = nums[-1]
        for i in range(len(nums)-2, -1, -1):
            res[i] *= temp
            temp *= nums[i]

        return res
```
