## problem
https://www.interviewbit.com/problems/find-duplicate-in-array/

## solve
```java
public class Solution {
    // DO NOT MODIFY THE ARGUMENTS WITH "final" PREFIX. IT IS READ ONLY
    public int repeatedNumber(final int[] A) {
        HashSet<Integer> existed_number = new HashSet<>();
        for(int i=0; i < A.length; i++) {
            if (existed_number.contains(A[i])) {
                return A[i];
            }
            existed_number.add(A[i]);
        }
        return -1;
    }
}

```