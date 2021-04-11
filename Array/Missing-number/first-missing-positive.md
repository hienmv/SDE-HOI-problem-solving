## Problem

https://leetcode.com/problems/first-missing-positive/

## Solution

```java
    public int firstMissingPositive(int[] nums) {
        int n = nums.length;
        for (int i = 0; i < n; i++) {
            // We don't care about non-positive numbers 
            // so we mark it as positive and larger than n. 
            // These numbers will be ignored in the next steps
            if (nums[i] <= 0) {
                nums[i] = Math.abs(nums[i]) + n + 1;
            }
        }
        int index;
        for (int v : nums) {
            index = Math.abs(v) - 1;
            // Ignore numbers with index larger than n
            if (index < n && nums[index] > 0) {
                nums[index] = -nums[index];
            }
        }
        for (int i = 0; i < n; i++) {
            if (nums[i] >= 0) return i + 1;
        }
        return n + 1;
    }

    // solution 2
        /*
    -Time O(n)
    -Space O(n)
    */
    public int firstMissingPositive2(int[] nums) {
        if (nums.length == 0) {
            return 1;
        }
        int n = nums.length;
        int[] tmp = new int[n+1];
        for(int i = 0; i < n; i++) {
            // dont care above lowerbound number (negative) and upperbound number (numbers which greater than length of array)
            if (nums[i] <= 0 || nums[i] > n) {
                continue;
            } 
            tmp[nums[i]] = 1;
        }
        for (int i=1; i < n+1; i++) {
            if (tmp[i] != 1) {
                return i;
            }
        }
        return n+1;
    }
```
