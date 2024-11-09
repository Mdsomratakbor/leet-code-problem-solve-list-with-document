# Rotate String

This project provides a solution to the "Rotate String" problem from LeetCode. The goal of the problem is to determine if one string can become another string by rotating it any number of times.

## Problem Description

Given two strings, `s` and `goal`, return `true` if and only if `s` can become `goal` after performing any number of shifts on `s`.

A **shift** on `s` consists of moving the leftmost character of `s` to the rightmost position.

### Example
- Input:  
  ```csharp
  s = "abcde"
  goal = "cdeab"
  ```
- Output:  
  `true`

### Explanation
If we rotate the string `"abcde"` two times, we get `"cdeab"`, which matches `goal`. Therefore, the output is `true`.

## Solution Explanation

To solve this problem, we:
1. Check if the lengths of `s` and `goal` are the same. If not, return `false` immediately.
2. Use a loop to simulate rotating `s` one character at a time.
3. For each rotation, check if `s` matches `goal`. If they match, return `true`.
4. If no match is found after all rotations, return `false`.

## Code

```csharp
using System;

namespace LeetCodeProblems
{
    internal class Rotate_String
    {
        public bool RotateString(string s, string goal)
        {
            // Check if lengths are equal
            if (s.Length != goal.Length) return false;

            // Rotate s one character at a time
            for (int i = 0; i < s.Length; i++)
            {
                s = s.Substring(1) + s[0]; // Perform rotation
                if (s == goal)             // Check for match
                {
                    return true;
                }
            }
            return false; // No match found after all rotations
        }
    }
}
```

## Usage

```csharp
using LeetCodeProblems;

class Program
{
    static void Main()
    {
        var rotateString = new Rotate_String();
        string s = "abcde";
        string goal = "cdeab";
        
        bool result = rotateString.RotateString(s, goal);
        Console.WriteLine(result); // Output: true
    }
}
```

## Complexity Analysis

- **Time Complexity**: \(O(n^2)\) – where \(n\) is the length of `s`. Each rotation takes \(O(n)\), and we do this \(n\) times.
- **Space Complexity**: \(O(n)\) – due to the substring operations.
