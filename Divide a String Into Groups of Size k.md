# Divide a String Into Groups of Size k

This repository contains a solution to the problem of dividing a string into groups of size `k`. If the last group is shorter than `k`, it is padded with a specified character to ensure all groups are of equal size.

---

## Problem Description

Given a string `s`, an integer `k`, and a character `fill`, the task is to divide the string into groups of size `k`. If the length of the string is not a multiple of `k`, the last group should be padded with the `fill` character until its length is `k`.

### Input

- `s`: A string to divide into groups.
- `k`: An integer specifying the size of each group.
- `fill`: A character used to pad the last group if it is shorter than `k`.

### Output

- An array of strings representing the divided groups.

---

## Example

### Input:
```plaintext
s = "abcdefghi"
k = 3
fill = 'x'
```

### Output:
```plaintext
["abc", "def", "ghi"]
```

### Input:
```plaintext
s = "abcdefghij"
k = 4
fill = 'y'
```

### Output:
```plaintext
["abcd", "efgh", "ijyy"]
```

---

## Solution

### Code:
```csharp
using System;

namespace LeetCodeProblems
{
    internal class Divide_a_String_Into_Groups_of_Size_k
    {
        public string[] DivideString(string s, int k, char fill)
        {
            int length = s.Length;
            int parts = Convert.ToInt32(Math.Ceiling((decimal)length / k));
            string[] strings = new string[parts];

            for (int i = 0; i < parts; i++)
            {
                int lastPartValue = (i * k) + k;
                if (lastPartValue > length)
                {
                    strings[i] = s.Substring((i * k), length - (i * k));
                    if (strings[i].Length != k)
                    {
                        int lastWordLength = k - strings[i].Length;
                        for (int j = 0; j < lastWordLength; j++)
                        {
                            strings[i] += fill;
                        }
                    }
                }
                else
                {
                    strings[i] = s.Substring(i * k, k);
                }
            }

            return strings;
        }
    }
}
```

---

## Explanation

1. **Input Parsing**:
   - Read the string `s`, the group size `k`, and the `fill` character.
   - Calculate the number of groups required using the formula: 
     ```
     parts = ceil(length of s / k)
     ```

2. **Iterate Over Groups**:
   - For each group, extract a substring of size `k` from `s`.
   - If the remaining characters in `s` are fewer than `k`, pad the string with the `fill` character.

3. **Output Result**:
   - Return the groups as an array of strings.

---

## Edge Cases

- **Empty String (`s = ""`)**:
  - Output: An empty array `[]`.

- **Group Size Greater Than String Length (`k > length of s`)**:
  - Pad the entire string to form a single group of size `k`.

- **No Padding Required (`length of s` is a multiple of `k`)**:
  - The output contains all groups with size `k`.

---

## Complexity

### Time Complexity:
- **O(n)**: The solution iterates over the string once to create the groups.

### Space Complexity:
- **O(parts)**: Additional space is used for the output array, where `parts` is the number of groups.
