动态规划将给定的问题分解成子问题，获得子问题的解来得出原问题的解。

并且在过程中将子问题的解进行保存，避免重复计算带来的性能消耗。



动态规划适用于重叠子问题和最优子结构的问题。



## 斐波那契数列

比如，斐波那契数列一般用的递归方式

```javascript
function fib(n) {
  if(n == 0 || n == 1) return n
  return fib(n - 1) + fib(n - 2)
}
```

当n越大的时候，越小的n的斐波那契数列结果将会被重复计算。

如果将已经计算过的斐波那契数列结果保存，再下次需要的时候直接给出进行其他计算的话，将无疑会增加性能。

```javascript
// Map for data to save
var fibResult = {
  "0": 0,
  "1": 1
}

function fib(n) {
  // check if the map has the data
  if(!fibResult[n]) {
    // calculat the result to save into the map
    fibResult[n] = fib(n - 1) + fib(n - 2)
  }
  return fibResult[n]
}
```



## 最大连续子序列和

给出数组[-2,1,-3,4,-1,2,1,-5,4]，获取拥有最大和的连续子数组

这个的思路是，

选取数组中任意一个位置i，其值为v(i)，前i-1项的和为A(i-1)

比较A(i-1) + v(i) 和 v(i)，A(i-1) + v(i) 可以写作A(i)

如果前n项的和加上当前项的值**小于**当前项，那么说明前n项的和肯定是负数

那么前n项的趋势是个递减的趋势，那么说明前n项并不符合**最大和**这个要求

那么应该从当前项开始，重新进行加和运算去查找新的连续子数组。



以上，可以简化成，计算并保存每次A(i)和v(i)的最大值，然后从这些值里面再找到最大值即可。

```javascript
var maxSubArray = function(nums) {
    // 记录第一个值
    const result = [nums[0]]
    for(const [index, num] of nums.slice(1).entries()) {
      // 保存每次计算比较v(i)和A(i)
      result.unshift(Math.max(num, num + result[0]))
    }
  	return Math.max(...result)
}
```

