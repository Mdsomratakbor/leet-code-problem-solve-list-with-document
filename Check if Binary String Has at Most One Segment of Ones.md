# Check if Binary String Has at Most One Segment of Ones

This repository contains a solution to the LeetCode problem **"Check if Binary String Has at Most One Segment of Ones"**. The task is to determine if a given binary string `s` has at most one contiguous segment of ones.

## Problem Statement

Given a binary string `s` (consisting of only `0`s and `1`s), return `true` if it contains at most one contiguous segment of `1`s. Otherwise, return `false`.

For example:
- Input: `"1001"` → Output: `false`
- Input: `"110"` → Output: `true`

---

## Implementation

The solution is implemented in C# as a class `Check_if_Binary_String_Has_at_Most_One_Segment_of_Ones` with a method `CheckOnesSegment`.

### Code

```csharp
using System;

namespace LeetCodeProblems
{
    internal class Check_if_Binary_String_Has_at_Most_One_Segment_of_Ones
    {
        public bool CheckOnesSegment(string s)
        {
            bool isFoundZero = false;

            foreach (char c in s)
            {
                if (c == '0')
                    isFoundZero = true;

                if (isFoundZero && c == '1')
                    return false;
            }
            return true;
        }
    }
}
```

---

## Explanation

### Approach
1. Traverse the binary string character by character.
2. Use a boolean flag `isFoundZero` to keep track of whether a `0` has been encountered.
3. If a `1` is found after a `0`, return `false` since this indicates the presence of more than one segment of `1`s.
4. If the loop completes without encountering a `1` after a `0`, return `true`.

### Complexity
- **Time Complexity**: O(n), where `n` is the length of the string `s`, as we traverse the string once.
- **Space Complexity**: O(1), since no additional data structures are used.

---

## Example Usage

```csharp
using System;

namespace LeetCodeProblems
{
    class Program
    {
        static void Main(string[] args)
        {
            var checker = new Check_if_Binary_String_Has_at_Most_One_Segment_of_Ones();

            string test1 = "1001";
            Console.WriteLine($"Input: {test1} → Output: {checker.CheckOnesSegment(test1)}");

            string test2 = "110";
            Console.WriteLine($"Input: {test2} → Output: {checker.CheckOnesSegment(test2)}");
        }
    }
}
```

### Example Outputs
- **Input**: `"1001"` → **Output**: `false`
- **Input**: `"110"` → **Output**: `true`
