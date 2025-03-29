# Check if Word Equals Summation of Two Words

## Problem Statement
Given three strings `firstWord`, `secondWord`, and `targetWord`, each consisting of lowercase English letters, return `true` if the summation of `firstWord` and `secondWord` equals `targetWord` when each letter is converted into its corresponding digit (i.e., 'a' = 0, 'b' = 1, ..., 'j' = 9). Otherwise, return `false`.

### Example 1:
```csharp
Input: firstWord = "acb", secondWord = "cba", targetWord = "cdb"
Output: true
Explanation:
firstWord = "acb" -> 021 (integer value 21)
secondWord = "cba" -> 210 (integer value 210)
targetWord = "cdb" -> 231 (integer value 231)
21 + 210 = 231, hence the result is true.
```

### Example 2:
```csharp
Input: firstWord = "aaa", secondWord = "a", targetWord = "aab"
Output: false
Explanation:
firstWord = "aaa" -> 000
secondWord = "a" -> 0
targetWord = "aab" -> 001
0 + 0 != 1, hence the result is false.
```

## Solution Approach
The solution follows these steps:
1. Convert each input string into an integer representation where 'a' = 0, 'b' = 1, ..., 'j' = 9.
2. Sum the numeric values of `firstWord` and `secondWord`.
3. Compare the sum with the numeric value of `targetWord`.
4. Return `true` if they match, otherwise return `false`.

## Implementation
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

namespace Leet_Code_Problems
{
    public class Check_if_Word_Equals_Summation_of_Two_Words
    {
        public bool IsSumEqual(string firstWord, string secondWord, string targetWord)
        {
            int firstValue = ConvertWordToNumber(firstWord);
            int secondValue = ConvertWordToNumber(secondWord);
            int targetValue = ConvertWordToNumber(targetWord);

            return firstValue + secondValue == targetValue;
        }

        private int ConvertWordToNumber(string word)
        {
            int num = 0;
            foreach (char c in word)
            {
                num = num * 10 + (c - 'a');
            }
            return num;
        }
    }
}
```

## Complexity Analysis
- **Time Complexity**: `O(N)`, where `N` is the length of the longest string. Each word is processed in linear time.
- **Space Complexity**: `O(1)`, since only a few integer variables are used.

## Edge Cases Considered
- Single-letter words.
- Words containing the same characters.
- Words with leading zeros.
- Large input strings.
