## Introduction to Fast and Slow Pointers & Sliding Window 🚀

#### Day 4 - 03-09-2024

#### **📖 Concepts of Fast and Slow Pointers & Sliding Window**

### Fast and Slow Pointers

The Fast and Slow Pointers technique involves using two pointers that move at different speeds through a data structure, such as a linked list or array. This method is commonly used to detect cycles, find the middle of a list, and solve other problems where relative positioning of elements matters.

#### 🔍 Real-time Example

Fast and Slow Pointers can be used to detect cycles in a linked list, where one pointer moves twice as fast as the other. If there is a cycle, the pointers will eventually meet.

### Sliding Window

The Sliding Window technique is used to solve problems involving subarrays or substrings by maintaining a window that slides over the data structure. It is particularly useful for optimizing problems that require checking contiguous sequences or ranges.

#### 🔍 Real-time Example

Sliding Window can be used to find the maximum sum of a subarray of a fixed size within an array, by maintaining a sum of elements within the window and adjusting it as the window slides.

#### **✨ Advantages of Fast and Slow Pointers & Sliding Window**

- **_Fast and Slow Pointers_**:
  - Efficiently solves problems related to cycle detection and linked list manipulations.
  - Can reduce time complexity by avoiding nested loops.
- **_Sliding Window_**:
  - Optimizes problems involving contiguous subarrays or substrings.
  - Reduces time complexity by converting O(n²) operations to O(n).

#### **🌟 Use Cases**

- **_Fast and Slow Pointers_**:
  - Detecting cycles in linked lists.
  - Finding the middle of a linked list.
- **_Sliding Window_**:
  - Finding the maximum sum of a subarray of a given size.
  - Determining the smallest subarray with a sum greater than or equal to a given value.

#### **🛠️ Implementing Fast and Slow Pointers & Sliding Window Problems**

**_1. Remove Duplicates from Sorted Array_**

Given a sorted array `nums`, remove the duplicates in-place such that each element appears only once and return the new length. The relative order of the elements should be kept the same.

**_Constraints_**:

- 1 ≤ `nums.length` ≤ 3 \* 10⁴
- `nums` is sorted in non-decreasing order.

**_Example 1_**:

```java
Input: nums = [1, 1, 2]
Output: 2, nums = [1, 2, _]
Explanation: Function should return new length 2, and the array `nums` should be updated to [1, 2, _], where _ can be any value.
```

**_Example 2_**:

```java
Input: nums = [0,0,1,1,1,2,2,3,3,4]
Output: 5, nums = [0, 1, 2, 3, 4, _, _, _, _, _]
Explanation: Function should return new length 5, with the updated array maintaining the first 5 unique elements.
```

**_Solve Here to Get Credits_**: [LeetCode - Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)

**_2. Container with Most Water_**

You are given `n` non-negative integers `a1, a2, ..., an`, where each represents a point at coordinate (i, ai). `n` vertical lines are drawn such that the two endpoints of line i is at (i, ai) and (i, 0). Find two lines that together with the x-axis form a container that holds the most water.

**_Constraints_**:

- 2 ≤ `height.length` ≤ 10⁵
- 0 ≤ `height[i]` ≤ 10⁴

**_Example 1_**:

```java
Input: height = [1,8,6,2,5,4,8,3,7]
Output: 49
Explanation: The maximum amount of water can be contained between lines at index 1 and 8 (0-based), forming a container with height 7 and width 7.
```

**_Example 2_**:

```java
Input: height = [1,1]
Output: 1
Explanation: Only one container is possible with the two lines at index 0 and 1.
```

**_Solve Here to Get Credits_**: [LeetCode - Container with Most Water](https://leetcode.com/problems/container-with-most-water/)

#### **❓ Practice Problems**

1. **_Remove Duplicates from Sorted Array_**:

   - **_Objective_**: Modify the array in place to remove duplicates using the Fast and Slow Pointers approach.
   - **_Key Concept_**: Use two pointers, one for traversing the array (fast) and one for placing the unique elements (slow).

2. **_Container with Most Water_**:
   - **_Objective_**: Find the two lines that form a container with the most water using the Two Pointers approach.
   - **_Key Concept_**: Use two pointers starting from both ends of the array and move them towards each other to find the maximum area.

#### **📚 Suggested Reading**

- [Fast and Slow Pointers: A Deep Dive](https://www.geeksforgeeks.org/floyds-cycle-finding-algorithm/)
- [Sliding Window Technique: A Comprehensive Guide](https://www.geeksforgeeks.org/window-sliding-technique/)

---
