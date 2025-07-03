# Coin Change (Minimum Coins to Form Amount)

## Problem Statement

You are given an integer array `coins` representing coins of different denominations and an integer `target_amount` representing a total amount of money.

Return the **fewest number of coins** that you need to make up that amount. If that amount of money **cannot** be made up by any combination of the coins, return **-1**.

You may assume that you have an **infinite number** of each kind of coin.

### Input

- `` (List[int]): Distinct (or possibly duplicate) positive integers representing coin denominations.
- `` (int): The desired sum of money.

### Output

- An integer representing the minimum number of coins needed to reach `target_amount`, or **-1** if impossible.

---

## Examples

### Example 1

```text
Input:  coins = [2, 4, 1, 4], target_amount = 5
Output: 2
```

**Explanation**\
Possible ways to make 5:

- 1 + 1 + 1 + 1 + 1  (five coins)
- 1 + 1 + 1 + 2      (four coins)
- 2 + 2 + 1          (three coins)
- 4 + 1              (two coins) ← *minimum*

### Example 2

```text
Input:  coins = [2], target_amount = 3
Output: -1
```

**Explanation**\
Using coin 2 alone, it is impossible to total 3.

---

## Constraints

| Name                       | Description              |
| -------------------------- | ------------------------ |
| `1 ≤ len(coins) ≤ 12`      | Number of denominations. |
| `1 ≤ coins[i] ≤ 10^4`      | Each coin value.         |
| `1 ≤ target_amount ≤ 10^4` | Target sum.              |

---

## Approach

This is the classic **Coin Change** problem, solvable via *dynamic programming* (DP):

1. **State Definition**\
   Let `dp[amt]` be the minimum number of coins needed to form amount `amt`.
2. **Initialization**
   - `dp[0] = 0` (no coins needed for zero).
   - For all other `amt`, initialize `dp[amt] = ∞` (or a sentinel > `target_amount`).
3. **Transition**\
   For each amount `amt` from **1** to `target_amount` (inclusive), iterate over each coin `c`:
   - If `c ≤ amt`, update

     `dp[amt] = min(dp[amt], dp[amt - c] + 1)`
4. **Answer**
   - If `dp[target_amount]` remains sentinel, return **-1**; otherwise, return `dp[target_amount]`.

### Correctness Proof (Sketch)

- *Base*: `dp[0]` is 0—trivially optimal.
- *Induction*: Assume `dp[k]` is optimal for all `k < amt`. For `amt`, we consider every last coin `c`. The remainder `amt − c` has optimal solution `dp[amt − c]` by induction, so adding `c` yields a candidate solution with `dp[amt − c] + 1` coins. Taking the minimum over all `c` ensures optimality for `amt`.
- By induction, `dp[target_amount]` is optimal.

### Complexity Analysis

- **Time**: `O(target_amount × len(coins))` — one inner loop per coin.
- **Space**: `O(target_amount)` — the DP table.

---

## Reference Implementation (Python 3)

```python
from typing import List

def coin_change(coins: List[int], target_amount: int) -> int:
    MAX = target_amount + 1  # sentinel > any possible minimum
    dp = [MAX] * (target_amount + 1)
    dp[0] = 0

    for amt in range(1, target_amount + 1):
        for c in coins:
            if c <= amt:
                dp[amt] = min(dp[amt], dp[amt - c] + 1)

    return -1 if dp[target_amount] == MAX else dp[target_amount]
```

---

## Test Cases

| `coins`               | `target_amount` | Expected  |
| --------------------- | --------------- | --------- |
| `[1, 2, 5]`           | 11              | 3 (5+5+1) |
| `[2, 4, 1, 4]`        | 5               | 2         |
| `[2]`                 | 3               | -1        |
| `[186, 419, 83, 408]` | 6249            | 20        |

---



