# Count the Number of Special Characters I

## Problem Description
The `NumberOfSpecialChars` function counts the number of characters in a given string `word` that appear both in lowercase and uppercase. For example, if the character 'a' appears as 'a' and 'A', it is considered a "special character".

### Example
For the input `"aAabc"`, the function will return `1`, because:
- The character 'a' appears as both 'a' and 'A', making it a special character.

### Input
- A string `word` containing alphanumeric characters.

### Output
- An integer representing the count of characters that appear both as uppercase and lowercase in the string.

## Solution Explanation

### Overview
The function uses two `HashSet<char>` collections to store the lowercase and uppercase characters found in the input string. It then checks for characters that exist in both sets, counting those characters as "special characters" if they appear in both forms.

### Code

```csharp
using System;
using System.Collections.Generic;

namespace LeetCodeProblems
{
    internal class Count_the_Number_of_Special_Characters_I
    {
        public int NumberOfSpecialChars(string word)
        {
            // HashSets to track lowercase and uppercase characters
            HashSet<char> lowers = new HashSet<char>();
            HashSet<char> uppers = new HashSet<char>();

            // Iterate through each character in the word
            foreach (char c in word)
            {
                // Add lowercase characters to lowers set
                if (char.IsLower(c))
                {
                    lowers.Add(c);
                }
                // Add uppercase characters to uppers set
                if (char.IsUpper(c))
                {
                    uppers.Add(c);
                }
            }

            // Count special characters (those that appear as both upper and lower case)
            int count = 0;
            foreach (char c in uppers)
            {
                if (lowers.Contains(char.ToLower(c)))
                {
                    count++;
                }
            }

            return count;
        }
    }
}
```

### Explanation of the Code

1. **HashSet for Lowercase and Uppercase Characters**:
   - We create two `HashSet<char>` collections: `lowers` to store lowercase characters and `uppers` to store uppercase characters.
   - These sets ensure that only unique characters are stored.

2. **Iterating Through the String**:
   - The function iterates through each character in the input string `word`.
   - For each character, it checks if it's lowercase or uppercase and adds it to the respective set.

3. **Count Special Characters**:
   - The function then iterates over the `uppers` set, and for each uppercase character, it checks if its lowercase counterpart is present in the `lowers` set.
   - If both the lowercase and uppercase versions of the character are found, it counts it as a "special character."

4. **Return the Result**:
   - Finally, the function returns the count of special characters.

### Complexity Analysis
- **Time Complexity**: \(O(N)\), where \(N\) is the length of the `word`. The function iterates through the string twice: once to populate the `HashSet`s and once to count the special characters.
- **Space Complexity**: \(O(N)\), because in the worst case, we store all characters in the `HashSet`s.

### Edge Cases
- **Empty String**: An empty string will return `0` since there are no characters to check.
- **All Lowercase or All Uppercase Characters**: If no character appears in both lowercase and uppercase, the result will be `0`.
- **Non-Alphabetic Characters**: The function only processes alphabetic characters, ignoring digits or special symbols.
