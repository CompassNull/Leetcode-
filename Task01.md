# 练习题-01



## 2235. 两整数相加

[https://leetcode.cn/problems/add-two-integers/description/](https://leetcode.cn/problems/add-two-integers/description/)

给你两个整数 `num1` 和 `num2`，返回这两个整数的和。

**示例1**

```Plain Text
输入：num1 = 12, num2 = 5
输出：17
解释：num1 是 12，num2 是 5 ，它们的和是 12 + 5 = 17 ，因此返回 17 。
```

**示例2**

```Plain Text
输入：num1 = -10, num2 = 4
输出：-6
解释：num1 + num2 = -6 ，因此返回 -6 。
```

**提示：**

- `-100 <= num1, num2 <= 100`

**思路**

直接输出`num1+num2`

**代码**

```Python
class Solution:
    def sum(self, num1: int, num2: int) -> int:
        return num1+num2
```



## 1929. 数组串联

[https://leetcode.cn/problems/concatenation-of-array/](https://leetcode.cn/problems/concatenation-of-array/)

给你一个长度为 `n` 的整数数组 `nums` 。请你构建一个长度为 `2n` 的答案数组 `ans` ，数组下标 **从 0 开始计数** ，对于所有 `0 <= i < n` 的 `i` ，满足下述所有要求：

- `ans[i] == nums[i]`

- `ans[i + n] == nums[i]`

具体而言，`ans` 由两个 `nums` 数组 **串联** 形成。

返回数组 **`ans` 。

**示例 1：**

```SQL
输入：nums = [1,2,1]
输出：[1,2,1,1,2,1]
解释：数组 ans 按下述方式形成：
- ans = [nums[0],nums[1],nums[2],nums[0],nums[1],nums[2]]
- ans = [1,2,1,1,2,1]
```

**示例 2：**

```SQL
输入：nums = [1,3,2,1]
输出：[1,3,2,1,1,3,2,1]
解释：数组 ans 按下述方式形成：
- ans = [nums[0],nums[1],nums[2],nums[3],nums[0],nums[1],nums[2],nums[3]]
- ans = [1,3,2,1,1,3,2,1]
```

**提示：**

- `n == nums.length`

- `1 <= n <= 1000`

- `1 <= nums[i] <= 1000`

**思路**

直接输出`nums+nums`

**代码**

```Python
class Solution:
    def sum(self, num1: int, num2: int) -> int:
        return nums+nums
        # return nums*2
```



##  771. 宝石与石头

[https://leetcode.cn/problems/jewels-and-stones/description/](https://leetcode.cn/problems/jewels-and-stones/description/)

给你一个字符串 `jewels` 代表石头中宝石的类型，另有一个字符串 `stones` 代表你拥有的石头。 `stones` 中每个字符代表了一种你拥有的石头的类型，你想知道你拥有的石头中有多少是宝石。

字母区分大小写，因此 `"a"` 和 `"A"` 是不同类型的石头。

**示例 1：**

```Python
输入：jewels = "aA", stones = "aAAbbbb"
输出：3
```

**示例 2：**

```Python
输入：jewels = "z", stones = "ZZ"
输出：0
```

**提示：**

- `1 <= jewels.length, stones.length <= 50`

- `jewels` 和 `stones` 仅由英文字母组成

- `jewels` 中的所有字符都是 **唯一的**

**思路**

遍历`stones`判断元素`s`是否存在`jewels`中

**代码**

```Python
class Solution:
    def numJewelsInStones(self, jewels: str, stones: str) -> int:
        result = 0
        for i in stones:
            if i in jewels:
                result += 1
        return result
```

**简便算法**

```Python
class Solution:
    def numJewelsInStones(self, jewels: str, stones: str) -> int:
        return sum(s in jewels for s in stones)
```

**大佬算法**

链接：[https://leetcode.cn/problems/jewels-and-stones/solutions/2356253/ben-ti-zui-you-jie-xian-xing-shi-jian-ch-ddw3/](https://leetcode.cn/problems/jewels-and-stones/solutions/2356253/ben-ti-zui-you-jie-xian-xing-shi-jian-ch-ddw3/)

```Python
class Solution:
    def numJewelsInStones(self, jewels: str, stones: str) -> int:
        # 把 jewels 转换成字符集合 mask
        mask = 0
        for c in jewels:
            mask |= 1 << (ord(c) & 63)
        # 统计有多少 stones[i] 在集合 mask 中
        return sum(mask >> (ord(c) & 63) & 1 for c in stones)
```





# 练习题-02



## 1480. 一堆数组的动态和

[https://leetcode.cn/problems/running-sum-of-1d-array/](https://leetcode.cn/problems/running-sum-of-1d-array/)

给你一个数组 `nums` 。数组「动态和」的计算公式为：`runningSum[i] = sum(nums[0]…nums[i])` 。

请返回 `nums` 的动态和。



**示例 1：**

```Python
输入：nums = [1,2,3,4]
输出：[1,3,6,10]
解释：动态和计算过程为 [1, 1+2, 1+2+3, 1+2+3+4] 。
```

**示例 2：**

```Python
输入：nums = [1,1,1,1,1]
输出：[1,2,3,4,5]
解释：动态和计算过程为 [1, 1+1, 1+1+1, 1+1+1+1, 1+1+1+1+1] 。
```

**示例 3：**

```Python
输入：nums = [3,1,2,10,1]
输出：[3,4,6,16,17]
```



**提示：**

- `1 <= nums.length <= 1000`

- `-10^6 <= nums[i] <= 10^6`

**思路**

遍历`nums`后元素累加

代码

```Python
class Solution:
    def runningSum(self, nums: List[int]) -> List[int]:
        count = 0
        res = []
        for i in range(len(nums)):
            count = count+nums[i]
            res.append(count)
        return res
 
"""
for i in range(1,len(nums)):
    nums[i] += nums[i-1]
return nums
"""
```



## 709. 转换成小写字母

[https://leetcode.cn/problems/to-lower-case/](https://leetcode.cn/problems/to-lower-case/)

给你一个字符串 `s` ，将该字符串中的大写字母转换成相同的小写字母，返回新的字符串。



**示例 1：**

```Python
输入：s = "Hello"
输出："hello"
```

**示例 2：**

```Python
输入：s = "here"
输出："here"
```

**示例 3：**

```Python
输入：s = "LOVELY"
输出："lovely"
```



**提示：**

- `1 <= s.length <= 100`

- `s` 由 ASCII 字符集中的可打印字符组成



代码

```Python
class Solution:
    def toLowerCase(self, s: str) -> str:
        return s.lower()
```

**另一种方法**

思路：字母大小写差值为32，函数`ord()`将大写字母转为对应的 ASCII 数值，然后加上差值再用函数`chr()`转换为对应小写字母

```Python
class Solution:
    def toLowerCase(self, s: str) -> str:
        result = ""
        for i in s:
            if i >= 'A' and i <= 'Z' :
                i = chr(ord(i) + 32)
            result += i
        return result
```



## 1672. 最富有客户的资产总量

[https://leetcode.cn/problems/richest-customer-wealth/](https://leetcode.cn/problems/richest-customer-wealth/)

给你一个 `m x n` 的整数网格 `accounts` ，其中 `accounts[i][j]` 是第 `i​​​​​​​​​​​​` 位客户在第 `j` 家银行托管的资产数量。返回最富有客户所拥有的 **资产总量** 。

客户的 **资产总量** 就是他们在各家银行托管的资产数量之和。最富有客户就是 **资产总量** 最大的客户



**示例 1：**

```Python
输入：accounts = [[1,2,3],[3,2,1]]
输出：6
解释：
第 1 位客户的资产总量 = 1 + 2 + 3 = 6
第 2 位客户的资产总量 = 3 + 2 + 1 = 6
两位客户都是最富有的，资产总量都是 6 ，所以返回 6 。
```

**示例 2：**

```Python
输入：accounts = [[1,5],[7,3],[3,5]]
输出：10
解释：
第 1 位客户的资产总量 = 6
第 2 位客户的资产总量 = 10 
第 3 位客户的资产总量 = 8
第 2 位客户是最富有的，资产总量是 10
```

**示例 3：**

```Python
输入：accounts = [[2,8,7],[7,1,3],[1,9,5]]
输出：17
```



**思路**

遍历`accounts[i]`并求`accounts[i]`的总和，最后用`max()`求出最大值

**代码**

```Python
class Solution:
    def maximumWealth(self, accounts: List[List[int]]) -> int:
        result = []
        for i in range(len(accounts)):
            result.append(sum(accounts[i]))
        return max(result)
"""
return max(map(sum ,accounts))
"""
```



