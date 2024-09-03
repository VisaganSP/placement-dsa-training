# Implementing Day 4 Problems 📚

#### Day 4 - 03-09-2024

## 1. Remove Duplicates from Sorted Array

### Problem Description:

Given an integer array `nums` sorted in non-decreasing order, remove the duplicates in-place such that each unique element appears only once. The relative order of the elements should be kept the same.

Return the new length of the array after removing the duplicates. It must be done with O(1) extra space.

#### Constraints:

- `1 ≤ nums.length ≤ 3 * 10⁴`
- `-100 ≤ nums[i] ≤ 100`
- `nums` is sorted in non-decreasing order.

#### Example 1:

**Input:**

- `nums = [1, 1, 2]`

**Output:**

- `2, nums = [1, 2, _]`

**Explanation:**

- Your function should return length = 2, with the first two elements of `nums` being 1 and 2 respectively. It doesn't matter what you leave beyond the returned length.

#### Example 2:

**Input:**

- `nums = [0,0,1,1,1,2,2,3,3,4]`

**Output:**

- `5, nums = [0,1,2,3,4,_,_,_,_,_]`

**Explanation:**

- Your function should return length = 5, with the first five elements of `nums` being modified to 0, 1, 2, 3, and 4 respectively.

---

### Solutions in Various Languages:

#### 1. **Python**

The Python solution uses the two-pointer technique to remove duplicates in-place.

```python
class Solution:
    def removeDuplicates(self, nums):
        if not nums:
            return 0

        left = 0  # Slow pointer

        for right in range(1, len(nums)):  # Fast pointer
            if nums[right] != nums[left]:
                left += 1
                nums[left] = nums[right]

        return left + 1

# Example usage:
# nums = [0,0,1,1,1,2,2,3,3,4]
# print(Solution().removeDuplicates(nums))  # Output: 5, nums = [0, 1, 2, 3, 4, _, _, _, _, _]
```

**Explanation:**

- The slow pointer (`left`) moves only when a new unique element is found.
- The fast pointer (`right`) traverses the entire array, and when a new unique element is found, it is placed at the `left + 1` position, maintaining the order.

---

#### 2. **Java**

The Java implementation similarly uses two pointers to modify the array in-place.

```java
class Solution {
    public int removeDuplicates(int[] nums) {
        if (nums.length == 0) return 0;

        int left = 0;  // Slow pointer

        for (int right = 1; right < nums.length; right++) {  // Fast pointer
            if (nums[right] != nums[left]) {
                left++;
                nums[left] = nums[right];
            }
        }

        return left + 1;
    }
}
```

**Explanation:**

- The Java solution uses a `for` loop with two pointers (`left` and `right`).
- When `nums[right]` is different from `nums[left]`, it updates `nums[left + 1]` with the new value and moves the `left` pointer.

---

#### 3. **C++**

The C++ solution also utilizes the two-pointer method, updating the array in place.

```cpp
#include <vector>
using namespace std;

class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        if (nums.empty()) return 0;

        int left = 0;  // Slow pointer

        for (int right = 1; right < nums.size(); right++) {  // Fast pointer
            if (nums[right] != nums[left]) {
                left++;
                nums[left] = nums[right];
            }
        }

        return left + 1;
    }
};
```

**Explanation:**

- The C++ solution efficiently manages duplicates by updating the array in-place.
- It keeps a `left` pointer to track the position of the last unique element and updates it whenever a new unique value is encountered.

---

## 2. Container With Most Water

### Problem Description:

You are given an integer array `height` of length `n`. There are `n` vertical lines drawn such that the two endpoints of the `i`-th line are `(i, 0)` and `(i, height[i])`.

Find two lines that together with the x-axis form a container, such that the container contains the most water. Return the maximum amount of water a container can store.

#### Constraints:

- `n = height.length`
- `2 ≤ n ≤ 10⁵`
- `0 ≤ height[i] ≤ 10⁴`

#### Example 1:

**Input:**

- `height = [1,8,6,2,5,4,8,3,7]`

**Output:**

- `49`

**Explanation:**

- The container with the most water is formed by lines at indices 1 and 8, with a height of 7 and a width of 7.

---

### Solutions in Various Languages:

#### 1. **Python**

The Python solution uses a two-pointer technique to find the maximum area.

```python
class Solution:
    def maxArea(self, height):
        left, right = 0, len(height) - 1
        max_area = 0

        while left < right:
            width = right - left
            max_area = max(max_area, min(height[left], height[right]) * width)

            if height[left] < height[right]:
                left += 1
            else:
                right -= 1

        return max_area

# Example usage:
# height = [1,8,6,2,5,4,8,3,7]
# print(Solution().maxArea(height))  # Output: 49
```

**Explanation:**

- The algorithm uses two pointers starting at the beginning (`left`) and end (`right`) of the array.
- It calculates the area for each possible container, moves the pointer pointing to the shorter line inward to potentially find a taller line, and updates the maximum area accordingly.

---

#### 2. **Java**

The Java solution employs the same two-pointer strategy for efficient area calculation.

```java
class Solution {
    public int maxArea(int[] height) {
        int left = 0, right = height.length - 1;
        int maxArea = 0;

        while (left < right) {
            int width = right - left;
            maxArea = Math.max(maxArea, Math.min(height[left], height[right]) * width);

            if (height[left] < height[right]) {
                left++;
            } else {
                right--;
            }
        }

        return maxArea;
    }
}
```

**Explanation:**

- Two pointers start at both ends of the array and calculate the area for each pair.
- The pointer corresponding to the shorter line is moved inward to potentially increase the container's height.

---

#### 3. **C++**

The C++ implementation uses the same two-pointer technique, adjusting pointers based on height.

```cpp
#include <vector>
using namespace std;

class Solution {
public:
    int maxArea(vector<int>& height) {
        int left = 0, right = height.size() - 1;
        int maxArea = 0;

        while (left < right) {
            int width = right - left;
            maxArea = max(maxArea, min(height[left], height[right]) * width);

            if (height[left] < height[right]) {
                left++;
            } else {
                right--;
            }
        }

        return maxArea;
    }
};
```

**Explanation:**

- The C++ solution maximizes the container's area by comparing the heights at the current pointers and moving inward from the shorter height.
- This method ensures that the potential for a larger area is considered by narrowing the width while trying to increase the height.

---

### Explanation:

Both problems for Day 4 make effective use of pointer techniques:

- **Remove Duplicates from Sorted Array** uses two pointers to maintain and update unique elements in-place, reducing extra space complexity.
- **Container With Most Water** uses a two-pointer approach to find the optimal container by calculating possible areas and adjusting pointers based on heights.

These approaches help optimize time and space complexity, making the solutions efficient for large inputs.

--- 

Feel free to implement these in your preferred language and test them with the provided examples to better understand their functionality!