## Problem 
https://leetcode.com/problems/height-checker/

## Solution

```java
// Use counting sort
// Time: O(n)
// Space: O(n)
    public int heightChecker(int[] heights) {
        int[] counts = new int[101];
        for (int h : heights) {
            counts[h] += 1;
        }
        for (int i = 1; i < counts.length; i++) {
            counts[i] = counts[i-1] + counts[i];
        }

        int[] sorted = new int[heights.length];
        for (int h : heights) {
            counts[h] = counts[h] - 1;
            sorted[counts[h]] = h;
        }

        int ans = 0;
        for (int i = 0; i < heights.length; i++) {
            if (heights[i] != sorted[i]) ans++;
        }
        return ans;
    }
```
