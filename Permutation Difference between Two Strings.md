# Permutation Difference between Two Strings

## Problem Description
The `FindPermutationDifference` function calculates the permutation difference between two strings, `s` and `t`, by computing the sum of absolute differences in the indices of matching characters in each string. Specifically, for each character in `s`, it finds the index of the corresponding character in `t` and adds the absolute difference in indices to the total sum.

### Example
Given two strings, `s = "abc"` and `t = "cab"`, the function calculates the following:
- `'a'` at index 0 in `s` corresponds to index 2 in `t` (difference = |0 - 2| = 2)
- `'b'` at index 1 in `s` corresponds to index 1 in `t` (difference = |1 - 1| = 0)
- `'c'` at index 2 in `s` corresponds to index 0 in `t` (difference = |2 - 0| = 2)

The total difference is 2 + 0 + 2 = 4.

## Solution Explanation

### Overview
The function maps each character in `t` to its index in a dictionary (`tMap`). It then iterates through each character in `s`, finds its corresponding index in `t` using the dictionary, and calculates the absolute difference in their positions. This difference is added to the cumulative sum.

### Code

```csharp
using System;
using System.Collections.Generic;

namespace LeetCodeProblems
{
    internal class Permutation_Difference_between_Two_Strings
    {
        public int FindPermutationDifference(string s, string t)
        {
            int sum = 0;

            // Map each character in 't' to its index
            Dictionary<char, int> tMap = new Dictionary<char, int>();
            for (int k = 0; k < t.Length; k++)
            {
                tMap[t[k]] = k;
            }

            // Calculate the permutation difference by comparing indices
            for (int i = 0; i < s.Length; i++)
            {
                if (tMap.TryGetValue(s[i], out int tIndex))
                {
                    sum += Math.Abs(i - tIndex);
                }
            }

            return sum;
        }
    }
}
```

### Explanation of the Code

1. **Mapping Characters of `t`**:
   - A dictionary `tMap` is created to store each character in `t` along with its index.
   - This mapping allows for constant-time access to the index of any character in `t`.

2. **Calculating Permutation Difference**:
   - The function iterates through each character in `s`:
     - If the character exists in `tMap`, it retrieves the corresponding index in `t` and calculates the absolute difference between the indices in `s` and `t`.
     - This difference is added to `sum`.

3. **Result**:
   - The final sum, which represents the total permutation difference between `s` and `t`, is returned.

### Complexity Analysis
- **Time Complexity**: \(O(N + M)\), where \(N\) is the length of `s` and \(M\) is the length of `t`. The dictionary creation takes \(O(M)\), and iterating through `s` takes \(O(N)\).
- **Space Complexity**: \(O(M)\), for storing the dictionary of `t`'s characters.

### Edge Cases
- **Different Lengths**: If `s` and `t` are of different lengths, characters in one string may not have counterparts in the other. The function will only consider characters in `s` that have corresponding entries in `t`.
- **Empty Strings**: If `s` or `t` is an empty string, the function returns `0` as there are no characters to compare.
- **Duplicate Characters**: If `t` contains duplicate characters, only the last occurrence's index is stored, potentially affecting results.
