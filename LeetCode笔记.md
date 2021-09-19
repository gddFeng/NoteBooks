# 算法入门

## 第一天 二分法查找

### 二分查找

给定一个`n`个元素有序的（升序）整型数组`nums`和一个目标值 `target` ，写一个函数搜索`nums`中的`target`，如果目标值存在返回下标，否则返回`-1`。

**示例：**

```C
输入: nums = [-1,0,3,5,9,12], target = 9
输出: 4
解释: 9 出现在 nums 中并且下标为 4
```

**解答：**

* 我的垃圾解答

```C
int search(int* nums, int numsSize, int target){
    int left = 0;
    int right = numsSize - 1;
    int mid = 0;
    while(left <= right){
        mid =left + (right - left) / 2;
        //这个控制至关重要，只有这样才能确保在左右都变化的情况下mid不会超出范围
        if(nums[mid] == target)
        return mid;
        if(nums[mid] < target)
        left = mid + 1;
        if(nums[mid] > target)
        right = mid - 1;
    }
    return -1;
}
```

### 第一个错误版本

你是产品经理，目前正在带领一个团队开发新的产品。不幸的是，你的产品的最新版本没有通过质量检测。由于每个版本都是基于之前的版本开发的，所以错误的版本之后的所有版本都是错的。

假设你有 n 个版本`[1, 2, ..., n]`,你想找出导致之后所有版本出错的第一个错误的版本。

你可以通过调用`bool isBadVersion(version)`接口来判断版本号`version`是否在单元测试中出错。实现一个函数来查找第一个错误的版本。你应该尽量减少对调用 API 的次数。

**示例：**
```C
输入：n = 5, bad = 4
输出：4
解释：
调用 isBadVersion(3) -> false 
调用 isBadVersion(5) -> true 
调用 isBadVersion(4) -> true
所以，4 是第一个错误的版本。
```

**提示：**

* `1 <= bad <= n <= 231 - 1`

**解答：**

```C
int firstBadVersion(int n) {
    int left=1,right=n,mid;
    while(left<right){
        mid=left+(right-left)/2;
        // 防止计算溢出
        if(isBadVersion(mid))
            right=mid;
            //暂定是第一个，查找继续
        else
            left=mid+1;
        
    }
    return left;
}
//这个是写死了必有错误的，如果没有错误就会出问题。
```

### 搜索插入位置

给定一个排序数组和一个目标值，在数组中找到目标值，并返回其索引。如果目标值不存在于数组中，返回它将会被按顺序插入的位置。

请必须使用时间复杂度为`O(log n)`的算法。

**示例：**
```C++
输入: nums = [1,3,5,6], target = 5
输出: 2
```

**提示：**

* `1 <= nums.length <= 104`
* `-104 <= nums[i] <= 104`
* `nums`为无重复元素的升序排列数组
* `-104 <= target <= 104`

**解答：**

```C
int searchInsert(int* nums, int numsSize, int target) {
    int left = 0, right = numsSize - 1, ans = numsSize;
    while (left <= right) {
        int mid = ((right - left) / 2) + left;
        if (target <= nums[mid]) {
            ans = mid;
            right = mid - 1;
        } else {
            left = mid + 1;
        }
    }
    return ans;
}
```