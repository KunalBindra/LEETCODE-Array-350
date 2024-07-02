# LEETCODE-Array-350
Let's dry run the `intersect` method in the `Solution` class using a specific example. Assume we have the following input arrays:

```java
int[] nums1 = {1, 2, 2, 1};
int[] nums2 = {2, 2};
```

Here is a step-by-step walkthrough of the method execution:

1. **Initial Call:**
    - Input: `nums1 = {1, 2, 2, 1}`, `nums2 = {2, 2}`
    - Since `nums1.length` (4) is greater than `nums2.length` (2), the method calls itself with the arguments swapped:
      ```java
      return intersect(nums2, nums1);
      ```
    - Now, the input is `nums1 = {2, 2}`, `nums2 = {1, 2, 2, 1}`

2. **Second Call:**
    - Input: `nums1 = {2, 2}`, `nums2 = {1, 2, 2, 1}`
    - Initialize `ans` as an empty list: `List<Integer> ans = new ArrayList<>();`
    - Initialize `count` as an empty hashmap: `Map<Integer, Integer> count = new HashMap<>();`
    - Populate `count` with the frequency of elements in `nums1`:
      - For `num = 2`, `count.put(2, count.getOrDefault(2, 0) + 1)`, `count` becomes `{2: 1}`
      - For `num = 2` again, `count.put(2, count.getOrDefault(2, 0) + 1)`, `count` becomes `{2: 2}`
    - Iterate through `nums2` and find intersections:
      - For `num = 1`, `count.containsKey(1)` is `false`, so skip.
      - For `num = 2`, `count.containsKey(2)` is `true` and `count.get(2) > 0` is `true`:
        - Add `2` to `ans`: `ans.add(2)`
        - Decrement `count`: `count.put(2, count.get(2) - 1)`, `count` becomes `{2: 1}`
      - For `num = 2` again, `count.containsKey(2)` is `true` and `count.get(2) > 0` is `true`:
        - Add `2` to `ans`: `ans.add(2)`
        - Decrement `count`: `count.put(2, count.get(2) - 1)`, `count` becomes `{2: 0}`
      - For `num = 1`, `count.containsKey(1)` is `false`, so skip.

3. **Convert Result to Array:**
    - `ans` is `[2, 2]`
    - Convert `ans` to an int array: `return ans.stream().mapToInt(Integer::intValue).toArray()`
    - The final result is `{2, 2}`

Therefore, for the input `nums1 = {1, 2, 2, 1}` and `nums2 = {2, 2}`, the `intersect` method returns `{2, 2}`.
