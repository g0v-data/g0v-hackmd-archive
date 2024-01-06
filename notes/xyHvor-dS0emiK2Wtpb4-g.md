leetcode Q1-Q3

# 1. Two Sum
## Brute Force
```
def twoSum(nums, target):
    for i in range(len(nums)-1):
        print("i=", i)
        for j in range(i+1, len(nums)):
            print("j=", j)
            if nums[i]+nums[j] == target:
                return [i, j]
```

## One-pass Hash Table
```
def twoSum(nums, target):
    h = {}
    for i, num in enumerate(nums):
        n = target - num
        if n not in h:
            h[num] = i
        else:
            return [h[n], i]
```

# 2. Add Two Numbers
```
def addTwoNumbers(self, l1, l2):
    """
    :type l1: ListNode
    :type l2: ListNode
    :rtype: ListNode
    """
    str_l1, str_l2 = '', ''
    while l1:            
        str_l1 += str(l1.val)
        l1 = l1.next
    while l2:            
        str_l2 += str(l2.val)
        l2 = l2.next
    int_l1 = int(str_l1[::-1])
    int_l2 = int(str_l2[::-1])     

    return list(map(int, str(int_l1 + int_l2)[::-1]))
```

# 3. Longest Substring Without Repeating Characters
```
def lengthOfLongestSubstring(self, s: str) -> int:
    maxlen = 0
    for i in range(len(s)):
        temp = []
        temp.append(s[i])
        for j in range(i+1, len(s)):
            if s[j] not in temp:
                temp.append(s[j])
            else:
                break
        if len(temp) > maxlen:
            maxlen = len(temp)
    return maxlen
```
