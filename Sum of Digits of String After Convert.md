# Sum of Digits of String After Convert

## Problem Description
Given a string `s` consisting of lowercase English letters and an integer `k`, perform the following operations:
1. Replace each letter in the string with its position in the alphabet (e.g., `'a' = 1, 'b' = 2, ..., 'z' = 26'`) to form a new string.
2. Concatenate all the numeric values into a single string.
3. Convert the numeric string into a single integer by summing its digits.
4. Repeat the process of summing the digits of the resulting integer `k` times.

The function should return the integer value obtained after performing the above operations.

---

### Example Input and Output

#### Example 1:
- **Input**: 
  ```csharp
  s = "zbax", k = 2
  ```
- **Output**: 
  ```csharp
  8
  ```
  **Explanation**:
  - Convert `"zbax"`: `'z' = 26`, `'b' = 2`, `'a' = 1`, `'x' = 24` → `"262124"`.
  - Sum digits: `2 + 6 + 2 + 1 + 2 + 4 = 17`.
  - Repeat summing digits (`k = 2`): `1 + 7 = 8`.

#### Example 2:
- **Input**: 
  ```csharp
  s = "iiii", k = 1
  ```
- **Output**: 
  ```csharp
  36
  ```
  **Explanation**:
  - Convert `"iiii"`: `'i' = 9` → `"9999"`.
  - Sum digits (`k = 1`): `9 + 9 + 9 + 9 = 36`.

---

## Constraints
- \( 1 \leq \text{s.length} \leq 100 \)
- \( 1 \leq k \leq 10 \)
- `s` consists of lowercase English letters only.

---

## Solution

### Approach
The solution involves two main steps:
1. **Convert Letters to Numeric String**:
   - Replace each character in the input string `s` with its corresponding alphabetic position (`'a' = 1, ..., 'z' = 26`).
   - Concatenate these numbers into a single numeric string.

2. **Sum Digits Repeatedly**:
   - Sum the digits of the numeric string to reduce it to an integer.
   - Repeat the digit-summing process `k` times or until the result becomes a single-digit number.

---

### Code Implementation
Here’s the C# implementation:

```csharp
using System;

namespace LeetCodeProblems
{
    internal class Sum_of_Digits_of_String_After_Convert
    {
        public int GetLucky(string s, int k)
        {
            // Step 1: Convert the string into numeric representation
            int sum = 0;
            foreach (char c in s)
            {
                int value = c - 'a' + 1; // Convert character to position in alphabet

                // Break down the numeric value into digits and sum them
                while (value > 0)
                {
                    sum += value % 10;
                    value /= 10;
                }
            }

            // Step 2: Repeat the process of summing digits k times
            for (int i = 1; i < k; i++)
            {
                int newSum = 0;
                while (sum > 0)
                {
                    newSum += sum % 10; // Extract and add each digit
                    sum /= 10;
                }
                sum = newSum; // Update the sum for the next iteration
            }

            return sum;
        }
    }
}
```

---

### Complexity Analysis

- **Time Complexity**:
  - The conversion of letters to numeric values takes \( O(n) \), where \( n \) is the length of the string.
  - The digit-summing process involves \( O(\log_{10}(x)) \), where \( x \) is the numeric value.
  - For \( k \) iterations, the total time complexity is \( O(n + k \cdot \log_{10}(x)) \).

- **Space Complexity**:
  - \( O(1) \): The algorithm uses a constant amount of extra space.

---

### Test Cases
Here are some test cases to validate the implementation:

```csharp
public void TestGetLucky()
{
    var solution = new Sum_of_Digits_of_String_After_Convert();

    Console.WriteLine(solution.GetLucky("zbax", 2) == 8);  // Example 1
    Console.WriteLine(solution.GetLucky("iiii", 1) == 36); // Example 2
    Console.WriteLine(solution.GetLucky("leetcode", 2) == 6); // Custom Test Case
    Console.WriteLine(solution.GetLucky("a", 1) == 1); // Single letter case
    Console.WriteLine(solution.GetLucky("a", 10) == 1); // Single letter with max k
}
```

---

## Edge Cases
1. **Single Character String**:
   - Example: `s = "a", k = 1`
   - Result should be the numeric position of the letter (`1` for `'a'`).

2. **Maximum String Length**:
   - Example: `s` contains 100 characters, all `'z'`.
   - Ensure the implementation can handle the large numeric string formed.

3. **High Value of `k`**:
   - Example: `k = 10`.
   - Ensure that the repeated summing process terminates as expected.

4. **String with Repeated Letters**:
   - Example: `s = "aaa", k = 2`.
   - Handle multiple occurrences of the same character.
