## 题目描述
[https://leetcode-cn.com/problems/kth-missing-positive-number/](https://leetcode-cn.com/problems/kth-missing-positive-number/)


## 解题思路
1、新数组 arr + 缺失数据，长度2001

## 解题代码
#### PHP
```php
class Solution {

    /**
     * @param Integer[] $arr
     * @param Integer $k
     * @return Integer
     */
    function findKthPositive($arr, $k) {
        $rv = [];
        for ($i = 1; $i <= 2001; $i++) {
            if (!in_array($i, $arr)) {
                $rv[] = $i;
            }
        }

        return $rv[$k-1];
    }
}
```

#### GO
```go
/*
第k个缺失的整数, 至少是k, 直接遍历数组, 遇到小于等于k的数, k必然后移.

如 k == 5, 至少是5
如果 数组包含 1, k至少是6
如果 数组还包含 6,k至少是7
*/
func findKthPositive(arr []int, k int) int {
    for _,v := range arr {
        if v <= k {
            k++
        }
    }

    return k
}
```