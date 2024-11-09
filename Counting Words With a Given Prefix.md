# Counting Words With a Given Prefix

## Problem Description

Given an array of strings `words` and a string `pref`, the goal is to count the number of strings in `words` that start with the prefix `pref`.

**Example**:  
- Input: `words = ["pay", "attention", "practice", "attend"]`, `pref = "at"`
- Output: `2`  
  (The words `"attention"` and `"attend"` start with `"at"`)

## Solution Explanation

The solution uses the `StartsWith` method to check if each word in `words` begins with the specified prefix `pref`. If it does, we increment a counter. This simple approach ensures that each word is checked only once, making it efficient.

### Time Complexity
- **O(n \* m)**, where `n` is the number of words and `m` is the maximum length of a word (because `StartsWith` checks each character up to the length of `pref`).

### Space Complexity
- **O(1)**, only a single counter is used for storage.

## Code Implementation

```csharp
using System;

namespace LeetCodeProblems
{
    internal class Counting_Words_With_a_Given_Prefix
    {
        public int PrefixCount(string[] words, string pref)
        {
            int count = 0;
            foreach (var word in words)
            {
                if (word.StartsWith(pref))
                    count++;
            }
            return count;
        }
    }
}
```
### Explanation of Example
The words `"attention"` and `"attend"` begin with the prefix `"at"`, so the output is `2`.

## Edge Cases
- `pref` is an empty string (all words should match).
- `words` array is empty (output should be `0`).
- No words in `words` start with `pref`.
