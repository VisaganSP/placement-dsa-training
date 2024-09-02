# Implementing Day 3 Problems 📚

#### Day 3 - 02-09-2024

## 1. Lemonade Change

### Problem Description:

You are given an integer array `bills` where `bills[i]` is the amount paid by the `i`-th customer. There are only three types of bills: 5, 10, and 20. You start with no change in hand.

Return `true` if and only if you can provide every customer with the correct change.

#### Constraints:

- `1 ≤ bills.length ≤ 10⁵`
- `bills[i]` is either `5`, `10`, or `20`.

#### Example 1:

**Input:**

- `bills = [5, 5, 5, 10, 20]`

**Output:**

- `true`

**Explanation:**

- Provide change for the 4th customer with one $5 bill.
- Provide change for the 5th customer with one $10 bill and one $5 bill.

#### Example 2:

**Input:**

- `bills = [5, 5, 10, 10, 20]`

**Output:**

- `false`

**Explanation:**

- Provide change for the 3rd customer with one $5 bill.
- Cannot provide change for the 5th customer because you only have two $10 bills.

---

### Solutions in Various Languages:

#### 1. **Python**

The Python solution uses a greedy algorithm with a HashMap to manage the change available.

```python
class Solution:
    def lemonadeChange(self, bills):
        five, ten = 0, 0

        for bill in bills:
            if bill == 5:
                five += 1
            elif bill == 10:
                if five == 0:
                    return False
                five -= 1
                ten += 1
            else:
                if ten > 0 and five > 0:
                    ten -= 1
                    five -= 1
                elif five >= 3:
                    five -= 3
                else:
                    return False
        return True

# Example usage:
# bills = [5, 5, 5, 10, 20]
# print(Solution().lemonadeChange(bills))  # Output: True
```

**Explanation:**

- The code keeps count of $5 and $10 bills.
- When a $20 bill is received, the algorithm tries to give back $15 using one $10 bill and one $5 bill. If not possible, it tries to give three $5 bills.
- The solution is greedy because it prioritizes using the largest bills available to give change, reducing the overall count of bills and minimizing the risk of running out of smaller denominations.

---

#### 2. **Java**

The Java implementation follows a similar logic using conditionals to manage the change.

```java
class Solution {
    public boolean lemonadeChange(int[] bills) {
        int five = 0, ten = 0;

        for (int bill : bills) {
            if (bill == 5) {
                five++;
            } else if (bill == 10) {
                if (five == 0) {
                    return false;
                }
                five--;
                ten++;
            } else {
                if (ten > 0 && five > 0) {
                    ten--;
                    five--;
                } else if (five >= 3) {
                    five -= 3;
                } else {
                    return false;
                }
            }
        }

        return true;
    }
}
```

**Explanation:**

- Uses integer counters to track the number of $5 and $10 bills.
- Similar approach as the Python solution, with a greedy strategy to ensure efficient change management.

---

#### 3. **C++**

In C++, the solution is also implemented with counters and simple condition checks.

```cpp
#include <vector>
using namespace std;

class Solution {
public:
    bool lemonadeChange(vector<int>& bills) {
        int five = 0, ten = 0;

        for (int bill : bills) {
            if (bill == 5) {
                five++;
            } else if (bill == 10) {
                if (five == 0) {
                    return false;
                }
                five--;
                ten++;
            } else {
                if (ten > 0 && five > 0) {
                    ten--;
                    five--;
                } else if (five >= 3) {
                    five -= 3;
                } else {
                    return false;
                }
            }
        }

        return true;
    }
};
```

**Explanation:**

- The C++ solution efficiently manages cash flow with counters for $5 and $10 bills.
- By checking available bills before each transaction, it ensures correct change is provided.

---

## 2. Roman to Integer

### Problem Description:

Given a Roman numeral, convert it to an integer. Roman numerals are represented by seven symbols: I, V, X, L, C, D, and M, which correspond to values 1, 5, 10, 50, 100, 500, and 1000, respectively.

#### Constraints:

- `1 ≤ s.length ≤ 15`
- `s` contains only Roman numerals (`'I', 'V', 'X', 'L', 'C', 'D', 'M'`).

#### Example 1:

**Input:**

- `s = "III"`

**Output:**

- `3`

**Explanation:**

- III = 3.

#### Example 2:

**Input:**

- `s = "IV"`

**Output:**

- `4`

**Explanation:**

- IV = 4.

---

### Solutions in Various Languages:

#### 1. **Python**

The Python solution uses a HashMap to map Roman symbols to values and processes the string from left to right.

```python
class Solution:
    def romanToInt(self, s: str) -> int:
        roman_map = {
            'I': 1, 'V': 5, 'X': 10, 'L': 50,
            'C': 100, 'D': 500, 'M': 1000
        }
        total = 0
        prev_value = 0

        for char in s:
            current_value = roman_map[char]
            if current_value > prev_value:
                total += current_value - 2 * prev_value
            else:
                total += current_value
            prev_value = current_value

        return total

# Example usage:
# s = "MCMXCIV"
# print(Solution().romanToInt(s))  # Output: 1994
```

**Explanation:**

- The algorithm checks if the current value is greater than the previous one. If it is, it means we have encountered a special case (like IV, IX) where the previous value needs to be subtracted.
- It subtracts twice the previous value because it has been added once in the previous iteration.

---

#### 2. **Java**

The Java version uses a HashMap and processes the string similarly to handle Roman numeral conversions.

```java
import java.util.HashMap;
import java.util.Map;

class Solution {
    public int romanToInt(String s) {
        Map<Character, Integer> romanMap = new HashMap<>();
        romanMap.put('I', 1);
        romanMap.put('V', 5);
        romanMap.put('X', 10);
        romanMap.put('L', 50);
        romanMap.put('C', 100);
        romanMap.put('D', 500);
        romanMap.put('M', 1000);

        int total = 0;
        int prevValue = 0;

        for (char c : s.toCharArray()) {
            int currentValue = romanMap.get(c);
            if (currentValue > prevValue) {
                total += currentValue - 2 * prevValue;
            } else {
                total += currentValue;
            }
            prevValue = currentValue;
        }

        return total;
    }
}
```

**Explanation:**

- A HashMap is used to map Roman numerals to their values.
- The logic checks if a smaller numeral precedes a larger one, subtracting appropriately for cases like IV and IX.

---

#### 3. **C++**

The C++ implementation uses a similar approach with an unordered_map to handle Roman numeral conversions.

```cpp
#include <unordered_map>
#include <string>
using namespace std;

class Solution {
public:
    int romanToInt(string s) {
        unordered_map<char, int> romanMap = {
            {'I', 1}, {'V', 5}, {'X', 10},
            {'L', 50}, {'C', 100}, {'D', 500}, {'M', 1000}
        };
        int total = 0;
        int prevValue = 0;

        for (char c : s) {
            int currentValue = romanMap[c];
            if (currentValue > prevValue) {
                total += currentValue - 2 * prevValue;
            } else {
                total += currentValue;
            }
            prevValue = currentValue;
        }

        return total;
    }
};
```

**Explanation:**

- The use of `unordered_map` for quick lookups allows for efficient conversion from Roman to integer.
- The logic accounts for special cases where subtraction is required based on Roman numeral rules.

---

### Explanation:

Both problems for Day 3 employ efficient algorithms and data structures to manage specific requirements:

- **Lemonade Change** uses a greedy approach to minimize the risk of running out of change by prioritizing larger denominations.
- **Roman to Integer** leverages maps for efficient symbol lookup and handles specific Roman numeral rules with a straightforward iteration and comparison approach.

---
