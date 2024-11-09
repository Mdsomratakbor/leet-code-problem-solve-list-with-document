# Score of a String.

## Problem Description
The `ScoreOfString` function computes the score of a given string `s` by summing the absolute differences between the ASCII values of adjacent characters.

### Example
For the input `"abc"`, the function will calculate the score as follows:
- \( |a - b| = |97 - 98| = 1 \)
- \( |b - c| = |98 - 99| = 1 \)
- Total score = \(1 + 1 = 2\)

Thus, the function will return `2`.

### Input
- A string `s` containing alphanumeric characters.

### Output
- An integer representing the score of the string, calculated as the sum of absolute differences between adjacent characters' ASCII values.

## Solution Explanation

### Overview
The function computes the score by iterating over the string and calculating the absolute difference between the ASCII values of each pair of adjacent characters. This score is accumulated and returned.

### Code

```csharp
using System;

namespace LeetCodeProblems
{
    internal class Score_of_a_String
    {
        public int ScoreOfString(string s)
        {
            int sum = 0;
            // Iterate through the string, comparing each character with the next
            for (int i = 0; i < s.Length - 1; i++)
            {
                int sI = (int)s[i];    // Get ASCII value of the current character
                int sj = (int)s[i + 1]; // Get ASCII value of the next character
                sum += Math.Abs(sI - sj); // Add the absolute difference to the sum
            }
            return sum; // Return the accumulated score
        }
    }
}
```

### Explanation of the Code

1. **Initialization**:
   - A variable `sum` is initialized to zero. This will hold the total score of the string.

2. **Iterating Through the String**:
   - The `for` loop iterates over the string from index `0` to `s.Length - 2`. This allows comparison of adjacent characters without exceeding the bounds of the string.

3. **Calculating ASCII Difference**:
   - For each pair of adjacent characters (at index `i` and `i+1`), the function calculates the absolute difference between their ASCII values using `Math.Abs`.

4. **Accumulating the Score**:
   - The absolute difference is added to the `sum` variable for each iteration.

5. **Return the Result**:
   - Finally, the function returns the accumulated `sum`, which represents the score of the string.

### Complexity Analysis
- **Time Complexity**: \(O(N)\), where \(N\) is the length of the string. The function processes each character in the string exactly once.
- **Space Complexity**: \(O(1)\), since the function uses a constant amount of space aside from the input string.

### Edge Cases
- **Empty String**: If the string is empty, the function will return `0`, as there are no characters to compare.
- **Single Character String**: A string with only one character will also return `0`, as there are no adjacent characters to compute differences.
- **Identical Characters**: If the string contains identical adjacent characters (e.g., `"aaaa"`), the score will be `0`, as the differences between each adjacent pair will be `0`.
