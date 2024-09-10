# Implementing Day 5 Problems 📚

#### Day 5 - 09-09-2024

## 1. Maximum Sum Subarray of Size K

### Problem Description:

Given an array of integers and a number `k`, find the maximum sum of any contiguous subarray of size `k`.

#### Constraints:

- `1 ≤ arr.length ≤ 10⁵`
- `1 ≤ k ≤ arr.length`

#### Example 1:

**Input:**

- `arr = [1, 2, 3, 4, 5]`
- `k = 3`

**Output:**

- `12`

**Explanation:**

- The maximum sum subarray of size 3 is `[3, 4, 5]`, and its sum is `12`.

#### Example 2:

**Input:**

- `arr = [2, 1, 5, 1, 3, 2]`
- `k = 3`

**Output:**

- `9`

**Explanation:**

- The maximum sum subarray of size 3 is `[5, 1, 3]`, and its sum is `9`.

---

### Solutions in Various Languages:

#### 1. **Python**

The Python solution uses the Sliding Window technique to find the maximum sum.

```python
class Solution:
    def maxSumSubarray(self, arr, k):
        n = len(arr)
        if n < k:
            return 0

        # Compute the sum of the first window
        window_sum = sum(arr[:k])
        max_sum = window_sum

        # Slide the window
        for i in range(k, n):
            window_sum += arr[i] - arr[i - k]
            max_sum = max(max_sum, window_sum)

        return max_sum

# Example usage:
# arr = [1, 2, 3, 4, 5]
# k = 3
# print(Solution().maxSumSubarray(arr, k))  # Output: 12
```

**Explanation:**

- The initial window sum is calculated by summing the first `k` elements.
- For each subsequent window, update the sum by adding the new element and subtracting the element that is leaving the window.
- Track the maximum sum encountered during the sliding process.

---

#### 2. **Java**

The Java implementation also employs the Sliding Window approach.

```java
class Solution {
    public int maxSumSubarray(int[] arr, int k) {
        int n = arr.length;
        if (n < k) return 0;

        // Compute the sum of the first window
        int windowSum = 0;
        for (int i = 0; i < k; i++) {
            windowSum += arr[i];
        }

        int maxSum = windowSum;

        // Slide the window
        for (int i = k; i < n; i++) {
            windowSum += arr[i] - arr[i - k];
            maxSum = Math.max(maxSum, windowSum);
        }

        return maxSum;
    }
}
```

**Explanation:**

- Compute the sum for the initial window of size `k`.
- For each new window position, update the sum and compare with the maximum sum found.

---

#### 3. **C++**

The C++ solution follows a similar Sliding Window strategy.

```cpp
#include <vector>
#include <algorithm>
using namespace std;

class Solution {
public:
    int maxSumSubarray(vector<int>& arr, int k) {
        int n = arr.size();
        if (n < k) return 0;

        // Compute the sum of the first window
        int windowSum = 0;
        for (int i = 0; i < k; ++i) {
            windowSum += arr[i];
        }

        int maxSum = windowSum;

        // Slide the window
        for (int i = k; i < n; ++i) {
            windowSum += arr[i] - arr[i - k];
            maxSum = max(maxSum, windowSum);
        }

        return maxSum;
    }
};
```

**Explanation:**

- Use a loop to compute the sum of the first `k` elements.
- Update the sum for each new window and keep track of the maximum sum found.

---

## 2. Binary Search on Sorted Array

### Problem Description:

Given a sorted array and a target value, return the index of the target if it exists in the array, otherwise return `-1`.

#### Constraints:

- `1 ≤ arr.length ≤ 10⁵`
- `arr` is sorted in ascending order.

#### Example 1:

**Input:**

- `arr = [1, 2, 3, 4, 5]`
- `target = 3`

**Output:**

- `2`

**Explanation:**

- The target value `3` is located at index `2`.

#### Example 2:

**Input:**

- `arr = [1, 2, 3, 4, 5]`
- `target = 6`

**Output:**

- `-1`

**Explanation:**

- The target value `6` does not exist in the array.

---

### Solutions in Various Languages:

#### 1. **Python**

The Python solution utilizes Binary Search for efficient searching in a sorted array.

```python
class Solution:
    def binarySearch(self, arr, target):
        left, right = 0, len(arr) - 1

        while left <= right:
            mid = (left + right) // 2

            if arr[mid] == target:
                return mid
            elif arr[mid] < target:
                left = mid + 1
            else:
                right = mid - 1

        return -1

# Example usage:
# arr = [1, 2, 3, 4, 5]
# target = 3
# print(Solution().binarySearch(arr, target))  # Output: 2
```

**Explanation:**

- Use a loop to repeatedly divide the search interval in half.
- Adjust the search interval based on whether the target is greater or less than the middle element.

---

#### 2. **Java**

The Java implementation performs Binary Search similarly.

```java
class Solution {
    public int binarySearch(int[] arr, int target) {
        int left = 0, right = arr.length - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;

            if (arr[mid] == target) {
                return mid;
            } else if (arr[mid] < target) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }

        return -1;
    }
}
```

**Explanation:**

- The algorithm uses a while loop to narrow down the search range.
- Adjust the search bounds based on comparisons with the middle element.

---

#### 3. **C++**

The C++ solution applies Binary Search using similar logic.

```cpp
#include <vector>
using namespace std;

class Solution {
public:
    int binarySearch(vector<int>& arr, int target) {
        int left = 0, right = arr.size() - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;

            if (arr[mid] == target) {
                return mid;
            } else if (arr[mid] < target) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }

        return -1;
    }
};
```

**Explanation:**

- The Binary Search algorithm divides the array into halves based on comparisons.
- Continues adjusting the search bounds until the target is found or the bounds converge.

---

### Explanation:

Both problems for Day 5 use efficient algorithms:

- **Maximum Sum Subarray of Size K** employs the Sliding Window technique to maintain and update the sum of subarrays in linear time.
- **Binary Search on Sorted Array** utilizes the Binary Search algorithm to efficiently locate elements in logarithmic time.

These techniques are crucial for optimizing performance in problems involving arrays and sorted data.

---

Feel free to implement these solutions in your preferred language and test them with the provided examples to understand their functionality better!
