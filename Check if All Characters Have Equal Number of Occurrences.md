# Check if All Characters Have Equal Number of Occurrences

## Problem Description
Given a string `s`, determine whether all characters in the string appear the same number of times.

### Example
#### Input: 
`s = "abacbc"`

#### Output: 
`true`

#### Explanation: 
All characters (`a`, `b`, `c`) appear exactly 2 times.

---

### Constraints
1. `1 <= s.length <= 1000`
2. `s` consists of lowercase English letters only.

---

## Solution

### Approach
The solution involves counting the occurrences of each character in the string and checking if all values in the frequency dictionary are equal.

### Steps:
1. **Create a frequency dictionary**: Iterate through the string and populate a dictionary where the key is the character and the value is its occurrence count.
2. **Compare frequencies**: Store the frequency of the first character. Compare it with all other frequencies in the dictionary.
3. **Return the result**: If all frequencies are equal, return `true`. Otherwise, return `false`.

---

### Code Implementation

```csharp
using System;
using System.Collections.Generic;
using System.Linq;

namespace LeetCodeProblems
{
    internal class Check_if_All_Characters_Have_Equal_Number_of_Occurrences
    {
        public bool AreOccurrencesEqual(string s)
        {
            int firstLetterCount = 0;
            Dictionary<char, int> keyValuePairs = new Dictionary<char, int>();

            foreach (char c in s)
            {
                if (keyValuePairs.ContainsKey(c))
                    keyValuePairs[c] = keyValuePairs[c] + 1;
                else 
                    keyValuePairs[c] = 1;
            }

            firstLetterCount = keyValuePairs.First().Value;
            return !keyValuePairs.Any(x => x.Value != firstLetterCount);
        }
    }
}
```

---

### Complexity Analysis
- **Time Complexity**: 
  - `O(n)` where `n` is the length of the string, to iterate through the string and populate the dictionary.
  - `O(k)` where `k` is the number of unique characters, to check frequency values in the dictionary.
  - Overall: `O(n + k)`.

- **Space Complexity**:
  - `O(k)` to store character frequencies in the dictionary, where `k` is the number of unique characters in the string.

---

### Example Execution

#### Example 1
Input: `"abacbc"`

- Frequency Dictionary: 
  ```
  {
    'a': 2,
    'b': 2,
    'c': 2
  }
  ```
- Comparison: All values are equal to 2.  
**Output**: `true`

#### Example 2
Input: `"aaabb"`

- Frequency Dictionary:
  ```
  {
    'a': 3,
    'b': 2
  }
  ```
- Comparison: Values `3` and `2` are not equal.  
**Output**: `false`

---

### Edge Cases
1. **Single Character**: 
   - Input: `"a"`  
   - Output: `true` (only one character, all occurrences are equal).

2. **Empty String**: 
   - Input: `""` (Not valid as per constraints).  
   - Handle using input validation if necessary.

3. **All Unique Characters**: 
   - Input: `"abcd"`  
   - Output: `true` (Each character occurs exactly once).
