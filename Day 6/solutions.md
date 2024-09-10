# Implementing Day 6 Problems 📚

#### Day 6 - 10-09-2024

## 1. Coin Change

### Problem Description:

Given a set of coin denominations and a total amount, find the minimum number of coins needed to make up that amount. If it is not possible to make up the amount, return `-1`.

#### Constraints:

- `1 ≤ coins.length ≤ 12`
- `1 ≤ amount ≤ 10⁴`

#### Example 1:

**Input:**

- `coins = [1, 2, 5]`
- `amount = 11`

**Output:**

- `3`

**Explanation:**

- The minimum number of coins is `3` (5 + 5 + 1).

#### Example 2:

**Input:**

- `coins = [2]`
- `amount = 3`

**Output:**

- `-1`

**Explanation:**

- It is not possible to make the amount using only coin `2`.

---

### Solutions in Various Languages:

#### 1. **Python**

The Python solution uses Dynamic Programming to solve the Coin Change problem.

```python
class Solution:
    def coinChange(self, coins, amount):
        dp = [float('inf')] * (amount + 1)
        dp[0] = 0
        
        for i in range(1, amount + 1):
            for coin in coins:
                if i - coin >= 0:
                    dp[i] = min(dp[i], dp[i - coin] + 1)
        
        return dp[amount] if dp[amount] != float('inf') else -1

# Example usage:
# coins = [1, 2, 5]
# amount = 11
# print(Solution().coinChange(coins, amount))  # Output: 3
```

**Explanation:**

- Use a DP array `dp` where `dp[i]` represents the minimum number of coins needed for amount `i`.
- Initialize `dp[0]` to `0` (base case: no coins needed for amount `0`).
- For each amount `i`, update `dp[i]` by checking each coin and choosing the minimum number of coins required.

---

#### 2. **Java**

The Java solution similarly utilizes Dynamic Programming.

```java
class Solution {
    public int coinChange(int[] coins, int amount) {
        int[] dp = new int[amount + 1];
        Arrays.fill(dp, Integer.MAX_VALUE);
        dp[0] = 0;
        
        for (int i = 1; i <= amount; i++) {
            for (int coin : coins) {
                if (i - coin >= 0 && dp[i - coin] != Integer.MAX_VALUE) {
                    dp[i] = Math.min(dp[i], dp[i - coin] + 1);
                }
            }
        }
        
        return dp[amount] == Integer.MAX_VALUE ? -1 : dp[amount];
    }
}
```

**Explanation:**

- Initialize `dp` array with `Integer.MAX_VALUE` (infinity) and set `dp[0]` to `0`.
- Update `dp[i]` for each amount `i` using available coins.

---

#### 3. **C++**

The C++ solution uses a similar approach with Dynamic Programming.

```cpp
#include <vector>
#include <algorithm>
using namespace std;

class Solution {
public:
    int coinChange(vector<int>& coins, int amount) {
        vector<int> dp(amount + 1, INT_MAX);
        dp[0] = 0;
        
        for (int i = 1; i <= amount; ++i) {
            for (int coin : coins) {
                if (i - coin >= 0 && dp[i - coin] != INT_MAX) {
                    dp[i] = min(dp[i], dp[i - coin] + 1);
                }
            }
        }
        
        return dp[amount] == INT_MAX ? -1 : dp[amount];
    }
};
```

**Explanation:**

- Use a DP vector `dp` to store the minimum number of coins for each amount.
- Update the DP vector by iterating over each coin and amount.

---

## 2. Subsets

### Problem Description:

Given a set of distinct integers, return all possible subsets (the power set). The solution set must not contain duplicate subsets.

#### Constraints:

- `1 ≤ nums.length ≤ 10`
- `nums` consists of distinct integers.

#### Example 1:

**Input:**

- `nums = [1, 2, 3]`

**Output:**

- `[[], [1], [2], [1, 2], [3], [1, 3], [2, 3], [1, 2, 3]]`

**Explanation:**

- All possible subsets of the given set are returned.

---

### Solutions in Various Languages:

#### 1. **Python**

The Python solution uses Backtracking to generate all possible subsets.

```python
class Solution:
    def subsets(self, nums):
        def backtrack(start, path):
            res.append(path[:])
            for i in range(start, len(nums)):
                path.append(nums[i])
                backtrack(i + 1, path)
                path.pop()
        
        res = []
        backtrack(0, [])
        return res

# Example usage:
# nums = [1, 2, 3]
# print(Solution().subsets(nums))  # Output: [[], [1], [2], [1, 2], [3], [1, 3], [2, 3], [1, 2, 3]]
```

**Explanation:**

- Use backtracking to explore all subsets.
- Maintain a path to record the current subset, and recursively generate subsets by adding each element and then backtracking.

---

#### 2. **Java**

The Java solution uses Backtracking to achieve the same.

```java
import java.util.ArrayList;
import java.util.List;

class Solution {
    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> result = new ArrayList<>();
        backtrack(nums, 0, new ArrayList<>(), result);
        return result;
    }
    
    private void backtrack(int[] nums, int start, List<Integer> path, List<List<Integer>> result) {
        result.add(new ArrayList<>(path));
        for (int i = start; i < nums.length; i++) {
            path.add(nums[i]);
            backtrack(nums, i + 1, path, result);
            path.remove(path.size() - 1);
        }
    }
}
```

**Explanation:**

- Use a helper function to handle backtracking.
- Maintain a list to record current subsets and explore further by adding each element and then removing it (backtracking).

---

#### 3. **C++**

The C++ solution also utilizes Backtracking for generating subsets.

```cpp
#include <vector>
using namespace std;

class Solution {
public:
    vector<vector<int>> subsets(vector<int>& nums) {
        vector<vector<int>> result;
        vector<int> path;
        backtrack(nums, 0, path, result);
        return result;
    }
    
private:
    void backtrack(const vector<int>& nums, int start, vector<int>& path, vector<vector<int>>& result) {
        result.push_back(path);
        for (int i = start; i < nums.size(); ++i) {
            path.push_back(nums[i]);
            backtrack(nums, i + 1, path, result);
            path.pop_back();
        }
    }
};
```

**Explanation:**

- Use a recursive function to handle backtracking and generate subsets.
- Manage the current subset with a path vector and update results accordingly.

---

### Explanation:

- **Coin Change** uses Dynamic Programming to efficiently find the minimum number of coins needed by solving subproblems and combining their solutions.
- **Subsets** utilizes Backtracking to explore all possible combinations of elements to generate subsets, ensuring no duplicate subsets.

---

Feel free to implement these solutions in your preferred language and test them with the provided examples to understand their functionality better!