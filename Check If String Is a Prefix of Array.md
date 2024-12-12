# Check If String Is a Prefix of Array

This repository contains a solution to the LeetCode problem **"Check If String Is a Prefix of Array"**. The problem requires checking if a given string `s` is a prefix formed by concatenating the elements of an array `words` in order.

## Problem Statement
Given a string `s` and an array of strings `words`, determine if `s` is a prefix string of `words`. A string `s` is a prefix string of `words` if it can be constructed by concatenating the first `k` strings from `words` (for some `k >= 1`) without any extra characters.

### Example:
```plaintext
Input: s = "iloveleetcode", words = ["i", "love", "leetcode", "apples"]
Output: true
Explanation: "iloveleetcode" can be formed by concatenating "i", "love", and "leetcode".

Input: s = "ilove", words = ["apples", "i", "love"]
Output: false
Explanation: "ilove" cannot be formed as a prefix of the given array.
```

---

## Solution Overview
This solution uses the `StringBuilder` class to efficiently concatenate strings and compares the result with `s` at each step. If at any point the concatenated string matches `s`, the function returns `true`. If the length of the concatenated string exceeds `s` without matching, the function returns `false` early.

---

## Implementation
The implementation is written in C#.

```csharp
using System;
using System.Text;

namespace LeetCodeProblems
{
    internal class Check_If_String_Is_a_Prefix_of_Array
    {
        public bool IsPrefixString(string s, string[] words)
        {
            StringBuilder newString = new StringBuilder();

            foreach (var word in words)
            {
                newString.Append(word);

                if (s == newString.ToString())
                    return true;

                if (newString.Length > s.Length)
                    return false;
            }

            return false;
        }
    }
}
```

---

## Key Features
- **Efficient Concatenation**: Uses `StringBuilder` for appending strings, minimizing the overhead of creating new string objects.
- **Early Exit**: The function exits early if the length of the concatenated string exceeds the length of `s`, improving runtime efficiency.
- **Clean and Readable**: The code is structured for clarity, making it easy to understand.

---

## Complexity Analysis
- **Time Complexity**: `O(n)`, where `n` is the sum of the lengths of all strings in `words` processed up to the point where the check completes.
- **Space Complexity**: `O(m)`, where `m` is the length of the concatenated string (managed by `StringBuilder`).

---

## Example Usage
To test the solution, instantiate the class and call the `IsPrefixString` method:

```csharp
class Program
{
    static void Main(string[] args)
    {
        var checker = new Check_If_String_Is_a_Prefix_of_Array();
        string s = "iloveleetcode";
        string[] words = { "i", "love", "leetcode", "apples" };

        bool result = checker.IsPrefixString(s, words);
        Console.WriteLine(result); // Output: true
    }
}
```
