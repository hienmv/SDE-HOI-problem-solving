## problem
https://www.interviewbit.com/problems/wave-array/

## solve
```java
public static int[] solve(int[] arr) {
    // 1. logic sort => O(nlogn)
    Arrays.sort(arr);
  
    // 2. iterate logic_sort array: 0(n)
    int[] result = new int[arr.length];
    int less_idx = 0;
    int mid = arr.length / 2;
    int great_idx = mid;
    int idx = 0;
    
    // append to result => other: swap elements which having corresponding idx
    while (less_idx < mid || great_idx < arr.length) {
      if (great_idx < arr.length) {
        result[idx] = arr[great_idx];
        great_idx++;
        idx++;
      }
      if (less_idx < mid) {
        result[idx] = arr[less_idx];
        less_idx++;
        idx++;
      }
    }
    
    return result;
  }
}
```