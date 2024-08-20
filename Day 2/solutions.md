# Implementing Array Problems 📚

#### Day 2 - 20-08-2024

### 1. Product Array Puzzle

#### Problem Description:

Given an array `arr[]` of `n` integers, construct a Product Array `P[]` (of the same size) such that `P[i]` is equal to the product of all the elements of `arr[]` except `arr[i]`.

#### Constraints:

- `1 ≤ n ≤ 10⁵`
- `1 ≤ arr[i] ≤ 10⁵`

#### Example 1:

**Input:**

- `n = 5, arr[] = {10, 3, 5, 6, 2}`

**Output:**

- `P[] = {180, 600, 360, 300, 900}`

**Explanation:**

- For index 0, `P[0] = 3 * 5 * 6 * 2 = 180`.

#### Example 2:

**Input:**

- `n = 2, arr[] = {12, 20}`

**Output:**

- `P[] = {20, 12}`

**Explanation:**

- For index 0, `P[0] = 20`.

---

### Solutions in Various Languages:

#### 1. **Java**

This solution involves calculating the prefix and suffix products and combining them to obtain the result.

```Java
class Solution {
    public static long[] productExceptSelf(int nums[]) {
        boolean isZero = false;
        int zeroCount = 0;
        long[] pre = new long[nums.length];

        int i = 0;
        while (i < nums.length && nums[i] == 0) {
            isZero = true;
            zeroCount++;
            i++;
        }

        long product = nums[i];
        i++;
        for (; i < nums.length; i++) {
            if (nums[i] != 0) {
                product *= nums[i];
            } else {
                isZero = true;
                zeroCount++;
            }
        }

        i = 0;
        for (; i < nums.length; i++) {
            if (nums[i] != 0) {
                pre[i] = product / nums[i];
            } else {
                isZero = true;
            }
        }

        long[] ans = new long[nums.length];
        for (i = 0; i < nums.length; i++) {
            if (isZero && nums[i] == 0 && zeroCount == 1) {
                ans[i] = product;
            } else if (isZero) {
                ans[i] = 0;
            } else {
                ans[i] = pre[i];
            }
        }

        return ans;
    }
}
```

**Explanation:**

- The code calculates the total product of all elements except zeros.
- The result is then computed by dividing the total product by each element, with special handling for zeros.

---

#### 2. **C++**

This solution uses two helper functions to calculate the prefix and suffix products, which are then combined to form the final result.

```C++
#include <vector>

class Solution {
  public:
    std::vector<long long int> prefixproduct(std::vector<long long int>& nums) {
        std::vector<long long int> prefix(nums.size(), 1);
        for (int i = 1; i < nums.size(); ++i) {
            prefix[i] = prefix[i - 1] * nums[i - 1];
        }
        return prefix;
    }

    std::vector<long long int> suffixproduct(std::vector<long long int>& nums) {
        std::vector<long long int> suffix(nums.size(), 1);
        for (int i = nums.size() - 2; i >= 0; --i) {
            suffix[i] = suffix[i + 1] * nums[i + 1];
        }
        return suffix;
    }

    std::vector<long long int> productExceptSelf(std::vector<long long int>& nums) {
        std::vector<long long int> prefix = prefixproduct(nums);
        std::vector<long long int> suffix = suffixproduct(nums);
        std::vector<long long int> ans(nums.size());

        for (int i = 0; i < nums.size(); i++) {
            ans[i] = prefix[i] * suffix[i];
        }
        return ans;
    }
};
```

**Explanation:**

- The `prefixproduct` function calculates the cumulative product from the start to each position.
- The `suffixproduct` function calculates the cumulative product from the end to each position.
- The final product for each position is the product of the corresponding prefix and suffix values.

---

#### 3. **Python**

The Python solution follows a similar approach to the C++ solution but utilizes Python's list and arithmetic capabilities.

```Python
class Solution:
    def productExceptSelf(self, nums):
        n = len(nums)
        prefix = [1] * n
        suffix = [1] * n

        for i in range(1, n):
            prefix[i] = prefix[i - 1] * nums[i - 1]

        for i in range(n - 2, -1, -1):
            suffix[i] = suffix[i + 1] * nums[i + 1]

        ans = [prefix[i] * suffix[i] for i in range(n)]
        return ans
```

**Explanation:**

- Two lists `prefix` and `suffix` are used to store the products from the start and end respectively.
- The final product array is calculated by multiplying the corresponding prefix and suffix values.

---

#### 4. **C**

The C solution directly implements the product calculation using a prefix and suffix array.

```C
#include <stdio.h>

void productExceptSelf(int nums[], int n, long long int result[]) {
    long long int prefix[n];
    long long int suffix[n];

    prefix[0] = 1;
    suffix[n - 1] = 1;

    for (int i = 1; i < n; i++) {
        prefix[i] = prefix[i - 1] * nums[i - 1];
    }

    for (int i = n - 2; i >= 0; i--) {
        suffix[i] = suffix[i + 1] * nums[i + 1];
    }

    for (int i = 0; i < n; i++) {
        result[i] = prefix[i] * suffix[i];
    }
}

int main() {
    int nums[] = {10, 3, 5, 6, 2};
    int n = 5;
    long long int result[n];

    productExceptSelf(nums, n, result);

    printf("Product Array: ");
    for (int i = 0; i < n; i++) {
        printf("%lld ", result[i]);
    }
    printf("\n");

    return 0;
}
```

**Explanation:**

- The C implementation uses two arrays `prefix` and `suffix` to store intermediate products.
- The final result is computed by multiplying the values from the prefix and suffix arrays for each index.

---

### Explanation:

The problem is solved by calculating the product of all elements except the current index using prefix and suffix arrays. The solutions provided handle edge cases like zeros in the array efficiently and ensure that the result is computed in O(n) time with O(n) space complexity.

---

# Implementing String Problems 📚

### 2. Longest Substring Without Repeating Characters

#### Problem Description:

Given a string `s`, the task is to find the length of the longest substring without repeating characters.

#### Constraints:

- `0 ≤ s.length ≤ 5 * 10⁴`
- `s` consists of English letters, digits, symbols, and spaces.

#### Example 1:

**Input:**

- `s = "abcabcbb"`

**Output:**

- `3`

**Explanation:**

- The answer is "abc", with the length of 3.

#### Example 2:

**Input:**

- `s = "bbbbb"`

**Output:**

- `1`

**Explanation:**

- The answer is "b", with the length of 1.

---

### Solutions in Various Languages:

#### 1. **Python**

This solution uses a sliding window approach to maintain the longest substring without repeating characters.

```Python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        n = len(s)
        maxLength = 0
        charSet = set()
        left = 0

        for right in range(n):
            if s[right] not in charSet:
                charSet.add(s[right])
                maxLength = max(maxLength, right - left + 1)
            else:
                while s[right] in charSet:
                    charSet.remove(s[left])
                    left += 1
                charSet.add(s[right])

        return maxLength
```

**Explanation:**

- The algorithm uses a sliding window technique with two pointers (`left` and `right`).
- The `charSet` set is used to track the characters within the current window.
- The `right` pointer expands the window by adding characters to the set.
- If a repeating character is found, the `left` pointer moves to shrink the window until the repeating character is removed.

---

#### 2. **Java**

This implementation also uses the sliding window technique and a `Set` to track characters.

```Java
import java.util.HashSet;
import java.util.Set;

class Solution {
    public int lengthOfLongestSubstring(String s) {
        int n = s.length();
        int maxLength = 0;
        Set<Character> charSet = new HashSet<>();
        int left = 0;

        for (int right = 0; right < n; right++) {
            if (!charSet.contains(s.charAt(right))) {
                charSet.add(s.charAt(right));
                maxLength = Math.max(maxLength, right - left + 1);
            } else {
                while (charSet.contains(s.charAt(right))) {
                    charSet.remove(s.charAt(left));
                    left++;
                }
                charSet.add(s.charAt(right));
            }
        }

        return maxLength;
    }
}
```

**Explanation:**

- Similar to the Python solution, a sliding window is used with two pointers.
- The `Set` is used to track the characters in the current window, and the maximum length is updated whenever a longer substring is found.

---

#### 3. **C++**

This solution follows the same approach using a `unordered_set` to track characters.

```C++
#include <unordered_set>
#include <string>
#include <algorithm>

class Solution {
public:
    int lengthOfLongestSubstring(std::string s) {
        int n = s.length();
        int maxLength = 0;
        std::unordered_set<char> charSet;
        int left = 0;

        for (int right = 0; right < n; right++) {
            if (charSet.count(s[right]) == 0) {
                charSet.insert(s[right]);
                maxLength = std::max(maxLength, right - left + 1);
            } else {
                while (charSet.count(s[right])) {
                    charSet.erase(s[left]);
                    left++;
                }
                charSet.insert(s[right]);
            }
        }

        return maxLength;
    }
};
```

**Explanation:**

- The `unordered_set` is used to efficiently check for the presence of a character in the current window.
- The sliding window approach allows the solution to handle large inputs effectively.

---

#### 4. **C**

This solution uses a similar sliding window technique, implemented in C.

```C
#include <stdio.h>
#include <string.h>

int lengthOfLongestSubstring(char* s) {
    int n = strlen(s);
    int maxLength = 0;
    int left = 0;
    int charSet[256] = {0};

    for (int right = 0; right < n; right++) {
        charSet[s[right]]++;

        while (charSet[s[right]] > 1) {
            charSet[s[left]]--;
            left++;
        }

        maxLength = (maxLength > (right - left + 1)) ? maxLength : (right - left + 1);
    }

    return maxLength;
}

int main() {
    char s[] = "abcabcbb";
    int result = lengthOfLongestSubstring(s);
    printf("The length of the longest substring without repeating characters is: %d\n", result);
    return 0;
}
```

**Explanation:**

- In this implementation, an array `charSet` of size 256 is used to keep track of the count of each character (assuming ASCII).
- The sliding window approach is maintained, with the `left` pointer adjusting to maintain the longest substring without repeating characters.

---

### Explanation:

The provided solutions find the length of the longest substring without repeating characters using a sliding window approach. This approach efficiently handles large input sizes by only scanning each character once, leading to a time complexity of O(n). The use of sets or arrays to track characters ensures that the solution is space-efficient as well.

---
