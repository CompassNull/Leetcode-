# 练习题-01



## 2235. 两整数相加

[https://leetcode.cn/problems/plus-one/description/](https://leetcode.cn/problems/plus-one/description/)

给定一个由 **整数** 组成的 **非空** 数组所表示的非负整数，在该数的基础上加一。

最高位数字存放在数组的首位， 数组中每个元素只存储**单个**数字。

你可以假设除了整数 0 之外，这个整数不会以零开头。

**示例 1：**

```Python
输入：digits = [1,2,3]
输出：[1,2,4]
解释：输入数组表示数字 123。
```

**示例 2：**

```Python
输入：digits = [4,3,2,1]
输出：[4,3,2,2]
解释：输入数组表示数字 4321。
```

**示例 3：**

```Python
输入：digits = [0]
输出：[1]
```

**提示：**

- `1 <= digits.length <= 100`

- `0 <= digits[i] <= 9`

**思路**

将数组`digits`转换成数字进行加一，再转换为数组

**代码**

```Python
class Solution:
    def plusOne(self, digits: List[int]) -> List[int]:
        d = ''
        res = []
        for i in digits:
            d += str(i)
        d = int(d) + 1
        for j in str(d):
            res.append(int(j))
        return res
```



## 724. 寻找数组的中心下标

[https://leetcode.cn/problems/find-pivot-index/](https://leetcode.cn/problems/find-pivot-index/)

给你一个整数数组 `nums` ，请计算数组的 **中心下标** 。

数组 **中心下标** 是数组的一个下标，其左侧所有元素相加的和等于右侧所有元素相加的和。

如果中心下标位于数组最左端，那么左侧数之和视为 `0` ，因为在下标的左侧不存在元素。这一点对于中心下标位于数组最右端同样适用。

如果数组有多个中心下标，应该返回 **最靠近左边** 的那一个。如果数组不存在中心下标，返回 `-1` 。

**示例 1：**

```Python
输入：nums = [1, 7, 3, 6, 5, 6]
输出：3
解释：
中心下标是 3 。
左侧数之和 sum = nums[0] + nums[1] + nums[2] = 1 + 7 + 3 = 11 ，
右侧数之和 sum = nums[4] + nums[5] = 5 + 6 = 11 ，二者相等。
```

**示例 2：**

```Python
输入：nums = [1, 2, 3]
输出：-1
解释：
数组中不存在满足此条件的中心下标。
```

**示例 3：**

```Python
输入：nums = [2, 1, -1]
输出：0
解释：
中心下标是 0 。
左侧数之和 sum = 0 ，（下标 0 左侧不存在元素），
右侧数之和 sum = nums[1] + nums[2] = 1 + -1 = 0 。
```

**提示：**

- `1 <= nums.length <= 10^4`

- `-1000 <= nums[i] <= 1000`

**思路**

假设`left`代表中心下标`i`左边元素的和，`right`为中心下标`i`右边元素的和。初始化`left = 0, right = sum(nums)`。对数组`nums`遍历，如果左边`left`等于 `right`减去`nums[i]`，那么`i`就是该数组的中心下标 

**代码**

```Python
class Solution:
    def pivotIndex(self, nums: List[int]) -> int:
        left = 0
        right = sum(nums)
        for i in range(len(nums)):
            right -= nums[i]
            if left == right:
                return i
            left += nums[i]
        return -1 
```



##  189. 轮转数组

[https://leetcode.cn/problems/rotate-array/](https://leetcode.cn/problems/rotate-array/)

给定一个整数数组 `nums`，将数组中的元素向右轮转 `k` **个位置，其中 `k` **是非负数。

**示例 1:**

```Python
输入: nums = [1,2,3,4,5,6,7], k = 3
输出: [5,6,7,1,2,3,4]
解释:
向右轮转 1 步: [7,1,2,3,4,5,6]
向右轮转 2 步: [6,7,1,2,3,4,5]
向右轮转 3 步: [5,6,7,1,2,3,4]
```

**示例 2:**

```Python
输入：nums = [-1,-100,3,99], k = 2
输出：[3,99,-1,-100]
解释: 
向右轮转 1 步: [99,-1,-100,3]
向右轮转 2 步: [3,99,-1,-100]
```

**提示：**

- `1 <= nums.length <= 105`

- `-231 <= nums[i] <= 231 - 1`

- `0 <= k <= 105`

**进阶：**

- 尽可能想出更多的解决方案，至少有 **三种** 不同的方法可以解决这个问题。

- 你可以使用空间复杂度为 `O(1)` 的 **原地** 算法解决这个问题吗？

**思路**

遍历`stones`判断元素`s`是否存在`jewels`中

**代码**

```Python
class Solution:
    def rotate(self, nums: List[int], k: int) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        n = len(nums)
        k = k % n
        nums[:] = nums[n - k:] + nums[:n - k]
```



# 练习题-02

