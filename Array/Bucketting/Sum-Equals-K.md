## problem
https://leetcode.com/problems/subarray-sum-equals-k/

## solve
```java
/*
https://leetcode.com/explore/challenge/card/30-day-leetcoding-challenge/531/week-4/3307/
*/
/*
Co nhieu dai luong
=> co dinh 1 dai luong => giam so luong phan tu bien thien...
=> cung 1 huong.

    // [l, j] = K
    presum[r] - presum[l-1] = K => sum(l, r) = K

    presum[r] - presum[l-1] = K
    presum[r] - K = presum[l-1]
    cnt(presum[i]) = presum[r] - K
*/
class Solution {
    public int subarraySum(int[] nums, int k) {
        int result = 0;
        //      value, cnt
        HashMap<Integer, Integer> map = new HashMap<>();
        int presum = 0;
        map.put(0, 1);
        for (int i = 0; i < nums.length; i++) {
            presum += nums[i];
            if (map.containsKey(presum - k)) {
                result += map.get(presum - k);
            }
            if (map.containsKey(presum)) {
                map.replace(presum, map.get(presum) + 1);
            }
            else {
                map.put(presum, 1);
            }
        }
        return result;
    }
}
```