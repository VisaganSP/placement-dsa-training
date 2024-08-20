## Introduction to Arrays and its use cases 🚀

#### Day 2 - 20-08-2024

#### **📖 Concept of Arrays**

Arrays in Java are a collection of elements, all of the same type, stored in a contiguous memory location. They allow you to store multiple values in a single variable, making data management more efficient. Arrays are fixed in size and can be accessed using an index.

#### 🔍 Real-time Example

![Input](../Day%201/images/Array.png)

#### **✨ Advantages of Arrays**

- **_Efficient Memory Usage_**: Arrays store elements in contiguous memory locations, leading to efficient data retrieval.
- **_Ease of Access_**: Elements can be accessed quickly using their index, making arrays ideal for scenarios requiring fast lookups.
- **_Data Management_**: Store and manage large volumes of data in a structured format.
- **_Fixed Size_**: Knowing the array size beforehand ensures better memory allocation and management.

#### **🌟 Use Cases of Arrays**

- **_Data Storage_**: Store a list of elements, such as numbers or strings.
- **_Matrix Operations_**: Represent matrices and perform mathematical operations on them.
- **_Sorting and Searching Algorithms_**: Implement and optimize algorithms for data sorting and searching.
- **_Handling Multiple Variables_**: Manage collections of similar data types, such as student grades or product prices.

#### **🛠️ Implementing Array Problems**

**_1. Product Array Puzzle_**

Given an array `arr[]` of `n` integers, construct a Product Array `P[]` (of the same size) such that `P[i]` is equal to the product of all the elements of `arr[]` except `arr[i]`.

**_Constraints_**:

- 1 ≤ n ≤ 10⁵
- 1 ≤ arr[i] ≤ 10⁵

**_Example 1_**:

```java
Input: n = 5, arr[] = {10, 3, 5, 6, 2}
Output: P[] = {180, 600, 360, 300, 900}
Explanation: For index 0, P[0] = 3 * 5 * 6 * 2 = 180.
```

**_Example 2_**:

```java
Input: n = 2, arr[] = {12, 20}
Output: P[] = {20, 12}
Explanation: For index 0, P[0] = 20.
```

**_Solve Here to Get Credits_**: [Geeks for Geeks - Product Array Puzzle Problem](https://www.geeksforgeeks.org/problems/product-array-puzzle4525/1)

**_2.Longest Substring Without Repeating Characters_**

Given a string s, find the length of the longest substring without repeating characters

**_Constraints_**:

- 0 ≤ s.length ≤ 5 \* 10⁴
- `s` consists of English letters, digits, symbols, and spaces.

**_Example 1_**:

```java
Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.
```

**_Example 2_**:

```java
Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```

**_Solve Here to Get Credits_**: [LeetCode - Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/description/)

#### **❓ Array Questions to Practice**

1. **_Product Array Puzzle_**:

   - **_Objective_**: Construct a product array where each element is the product of all the elements of the input array except the one at that index.
   - **_Key Concept_**: Efficient array manipulation without division.

2. **_Longest Substring Without Repeating Characters_**:
   - **_Objective_**: Find the length of the longest substring without repeating characters.
   - **_Key Concept_**: Understanding the sliding window technique and hash map usage.

#### **📚 Suggested Reading**

- [Arrays: A Step-by-Step Guide](https://www.geeksforgeeks.org/array-data-structure-guide/)

---
