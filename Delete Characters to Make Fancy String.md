# Delete Characters to Make Fancy String

## Overview

The `Delete_Characters_to_Make_Fancy_String` class provides a solution to make a string "fancy" by removing excessive repeated characters. A string is considered "fancy" if there are **no three consecutive identical characters**.

### Problem Definition

Given a string `s`, the goal is to construct a new string by removing characters to ensure that no three consecutive characters are the same, while maintaining the original order of the remaining characters.

### Example Cases

- **Input**: `s = "leeetcode"`
  - **Output**: `"leetcode"`
  - **Explanation**: The substring `"eee"` is reduced to `"ee"`.

- **Input**: `s = "aaabaaaa"`
  - **Output**: `"aabaa"`
  - **Explanation**: The consecutive substring `"aaa"` is reduced to `"aa"` and `"aaaa"` is reduced to `"aa"`.

## Code Explanation

### Method `MakeFancyString`

```csharp
public string MakeFancyString(string s)
{
    int left = 1, right = s.Length;
    StringBuilder result = new StringBuilder();
    result.Append(s[0]);

    int count = 1;

    while (left < right)
    {
        if (s[left - 1] == s[left])
        {
            count++;
        }
        else
        {
            count = 1;
        }

        if (count < 3)
        {
            result.Append(s[left]);
        }

        left++;
    }

    return result.ToString();
}
```

- **Parameters**:
  - `string s`: The input string containing only lowercase letters.
- **Returns**:
  - `string`: The "fancy" version of `s` with no three consecutive identical characters.

- **Logic**:
  - Initializes `count` to track the number of consecutive characters.
  - Uses a `StringBuilder` named `result` to efficiently build the output string.
  - Iterates over the string:
    - If the current character matches the previous one, increment `count`.
    - If `count` is less than 3, add the current character to `result`.
    - If characters do not match, reset `count` to 1.
  
### Complexity Analysis

- **Time Complexity**: \(O(n)\) because we iterate through the string once.
- **Space Complexity**: \(O(n)\) due to the use of `StringBuilder` to construct the result string.

## Example Usage

```csharp
using System;

namespace LeetCodeProblems
{
    internal class Program
    {
        private static void Main(string[] args)
        {
            Delete_Characters_to_Make_Fancy_String solution = new Delete_Characters_to_Make_Fancy_String();

            Console.WriteLine(solution.MakeFancyString("leeetcode")); // Output: "leetcode"
            Console.WriteLine(solution.MakeFancyString("aaabaaaa"));  // Output: "aabaa"
            Console.WriteLine(solution.MakeFancyString("aab"));       // Output: "aab"
        }
    }
}
```

## Remarks

This solution effectively uses a pointer-based approach to track consecutive character counts and `StringBuilder` for optimal string construction. It ensures minimal operations while achieving the desired "fancy" format of the input string. This method is efficient and performs well for long strings.
