## Implementing Array Problems

#### Day 1 - 19-08-2024

### 1. Peak Element Problem

#### Problem Description:

Given a 0-indexed array of integers `arr[]` of size `n`, the task is to find the peak element and return its index. An element is considered to be a peak if its value is greater than or equal to the values of its adjacent elements (if they exist).

#### Constraints:

- `1 ≤ n ≤ 10⁵`
- `1 ≤ arr[i] ≤ 10⁶`
- **Expected Time Complexity:** O(log(n))
- **Expected Auxiliary Space:** O(1)

#### Example:

**Input:**

- `n = 3, arr[] = {1, 2, 3}`

**Output:**

- `2`

**Explanation:**

- The element at index 2 with value 3 is a peak element since it's greater than its adjacent elements.

---

### Solutions in Various Languages:

#### 1. **Java**

This solution uses a binary search approach to find the peak element, achieving the desired time complexity of O(log n).

```java
class Solution {
    // Function to find the peak element
    public int peakElement(int[] arr, int n) {
        return binarySearch(arr, 0, n - 1);
    }

    private static int binarySearch(int[] nums, int low, int high) {
        if (low > high) {
            return -1;
        }
        if (low == high)
            return low;

        int mid = (low + high) / 2;

        if (mid - 1 >= low && nums[mid] >= nums[mid - 1] && mid + 1 <= high && nums[mid] >= nums[mid + 1]) {
            return mid;
        } else if (nums[mid] > nums[mid + 1]) {
            return binarySearch(nums, low, mid);
        } else {
            return binarySearch(nums, mid + 1, high);
        }
    }
}
```

**Explanation:**

- The function uses a binary search technique to efficiently find a peak element.
- If the middle element (`mid`) is greater than or equal to its adjacent elements, it is a peak.
- If the left neighbor of `mid` is greater, then the peak lies in the left half.
- Otherwise, the peak lies in the right half.

---

#### 2. **C**

This solution uses an iterative binary search approach to identify the peak element.

```c
// User function Template for C

int peakElement(int arr[], int n) {
    int l = 0, h = n - 1;
    while (l <= h) {
        int mid = l + (h - l) / 2;

        // Check if mid is a peak element
        if ((mid == 0 || arr[mid] >= arr[mid - 1]) &&
            (mid == n - 1 || arr[mid] >= arr[mid + 1])) {
            return mid;
        }
        // If the left neighbor is greater, then the peak must be on the left
        else if (mid > 0 && arr[mid] < arr[mid - 1]) {
            h = mid - 1;
        }
        // If the right neighbor is greater, then the peak must be on the right
        else {
            l = mid + 1;
        }
    }
    return -1;
}
```

**Explanation:**

- This implementation also uses binary search but iteratively.
- The peak element is identified by comparing the middle element with its neighbors.
- Adjust the search range based on the comparison results.

---

#### 3. **C++**

This solution checks for a peak element by iterating through the array.

```cpp
class Solution {
public:
    int peakElement(int arr[], int n) {
        for (int i = 0; i < n; i++) {
            if (i == 0 && arr[i + 1] <= arr[i]) {
                return i;
            } else if (arr[i + 1] <= arr[i] && arr[i - 1] <= arr[i]) {
                return i;
            } else if (i == n - 1 && arr[i - 1] <= arr[i]) {
                return i;
            }
        }
        return -1;
    }
};
```

**Explanation:**

- This approach iteratively checks each element to see if it is a peak.
- The edge cases are handled by checking the first and last elements separately.
- If any element is found to be a peak, its index is returned immediately.

---

#### 4. **Python**

This solution also iteratively checks for a peak element in the array.

```python
class Solution:
    def peakElement(self, arr, n):
        if n == 1:
            return 0
        if arr[0] >= arr[1]:
            return 0
        if arr[n - 1] >= arr[n - 2]:
            return n - 1

        # Check for every other element
        for i in range(1, n - 1):
            if arr[i] >= arr[i - 1] and arr[i] >= arr[i + 1]:
                return i
```

**Explanation:**

- The Python implementation checks the edge cases first, then iterates through the array to find a peak element.
- If an element meets the peak criteria, its index is returned.

---

### 2. Move Zeros Problem

#### Problem Description:

Given an integer array `nums`, the task is to move all 0's to the end of the array while maintaining the relative order of the non-zero elements. This must be done in-place without making a copy of the array.

#### Constraints:

- `1 ≤ nums.length ≤ 10⁴`
- `-2³¹ ≤ nums[i] ≤ 2³¹ - 1`

#### Example 1:

**Input:**

- `nums = [0, 1, 0, 3, 12]`

**Output:**

- `[1, 3, 12, 0, 0]`

#### Example 2:

**Input:**

- `nums = [0]`

**Output:**

- `[0]`

---

### Solutions in Various Languages:

#### 1. **Python**

This solution iterates through the array, moving non-zero elements to the front while keeping track of their positions.

```python
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        left = 0

        for right in range(len(nums)):
            if nums[right] != 0:
                nums[right], nums[left] = nums[left], nums[right]
                left += 1
```

**Explanation:**

- The algorithm uses two pointers (`left` and `right`).
- The `right` pointer iterates through the array, and whenever a non-zero element is found, it is swapped with the element at the `left` pointer.
- The `left` pointer is incremented only when a non-zero element is moved.

---

#### 2. **Java**

This implementation is similar to the Python solution, utilizing two pointers to move non-zero elements to the front of the array.

```java
class Solution {
    public void moveZeroes(int[] nums) {
        int left = 0;

        for (int right = 0; right < nums.length; right++) {
            if (nums[right] != 0) {
                int temp = nums[right];
                nums[right] = nums[left];
                nums[left] = temp;
                left++;
            }
        }
    }
}
```

**Explanation:**

- Two pointers (`left` and `right`) are used to track the position of non-zero elements.
- When a non-zero element is found at `right`, it is swapped with the element at `left`, and `left` is incremented.

---

#### 3. **C++**

This solution also uses two pointers to move non-zero elements to the front, while maintaining the relative order.

```cpp
class Solution {
public:
    void moveZeroes(vector<int>& nums) {
        int left = 0;

        for (int right = 0; right < nums.size(); right++) {
            if (nums[right] != 0) {
                swap(nums[right], nums[left]);
                left++;
            }
        }
    }
};
```

**Explanation:**

- The `swap` function is used to move non-zero elements to the front.
- Two pointers, `left` and `right`, help in maintaining the correct positions of the elements.

---

#### 4. **C**

This solution uses a similar approach to the ones above, tailored to the C programming language.

```c
#include <stdio.h>

void moveZeroes(int* nums, int numsSize) {
    int left = 0;

    for (int right = 0; right < numsSize; right++) {
        if (nums[right] != 0) {
            int temp = nums[right];
            nums[right] = nums[left];
            nums[left] = temp;
            left++;
        }
    }
}

int main() {
    int nums[] = {0, 1, 0, 3, 12};
    int numsSize = sizeof(nums) / sizeof(nums[0]);

    moveZeroes(nums, numsSize);

    for (int i = 0; i < numsSize; i++) {
        printf("%d ", nums[i]);
    }

    return 0;
}
```

**Explanation:**

- Similar to the other languages, this solution uses two pointers to move the non-zero elements to the front.
- The `left` pointer keeps track of the position where the next non-zero element should be placed.

---

This README provides comprehensive solutions for the given problems in Java, C, C++, and Python, covering both peak element detection and moving zeros in an array.
