# Maximum Average Subarray of Length K

You are given an integer array `nums` consisting of `n` elements, and an integer `k`.

Your task is to find a contiguous subarray of `nums` whose length is exactly `k` that has the **highest average value**. A subarray is simply a sequence of consecutive elements from the original array. After identifying this subarray, return the **average value, rounded to two decimal places**.

---

## Example 1

**Input:**  
`nums = [1, 2, -5, -3, 10, 3]`  
`k = 3`

**Output:**  
`3.33`

**Explanation:**  
The subarray here is `[-3, 10, 3]`, so the average is `(−3 + 10 + 3) / 3 = 10 / 3 = 3.33`.

---

## Example 2

**Input:**  
`nums = [9]`  
`k = 1`

**Output:**  
`9.00`

**Explanation:**  
The subarray here is just `[9]`, so its average is exactly `9.00`.

---

## Constraints

- `1 <= n <= 10^5`
- `1 <= k <= n`
- `-10^4 <= nums[i] <= 10^4`



```python

def find_max_average(nums, k):
    current_sum = sum(nums[:k])
    max_sum = current_sum

    for i in range(k, len(nums)):
        current_sum = current_sum - nums[i - k] + nums[i]
        max_sum = max(max_sum, current_sum)

    max_avg = max_sum / k
    return round(max_avg, 2)
