# Decrypt String from Alphabet to Integer Mapping

### Problem Description:

Given a string `s` consisting of digits and '#' characters, this problem decrypts the string into the alphabet according to a mapping where:

- `1` to `9` map to 'a' to 'i'.
- `10#` maps to 'j', `11#` to 'k', and so on, up to `26#` mapping to 'z'.

For example:
- Input: `"10#11#12"`
- Output: `"jkl"`

---

## Solution Explanation

The algorithm iterates through the given string `s`. It checks if a 3-character substring ending with `#` exists, which corresponds to the two-digit alphabet mappings (`10#` to `26#`). Otherwise, it processes single digits (`1` to `9`).

### Code Walkthrough:

```csharp
using System;
using System.Collections.Generic;
using System.Text;

namespace LeetCodeProblems
{
    internal class Decrypt_String_from_Alphabet_to_Integer_Mapping
    {
        public string FreqAlphabets(string s)
        {
            // Mapping dictionary for both single digit and two-digit alphabet mappings
            var mapping = new Dictionary<string, char> {
                { "1", 'a' }, { "2", 'b' }, { "3", 'c' }, { "4", 'd' },
                { "5", 'e' }, { "6", 'f' }, { "7", 'g' }, { "8", 'h' },
                { "9", 'i' }, { "10#", 'j' }, { "11#", 'k' }, { "12#", 'l' },
                { "13#", 'm' }, { "14#", 'n' }, { "15#", 'o' }, { "16#", 'p' },
                { "17#", 'q' }, { "18#", 'r' }, { "19#", 's' }, { "20#", 't' },
                { "21#", 'u' }, { "22#", 'v' }, { "23#", 'w' }, { "24#", 'x' },
                { "25#", 'y' }, { "26#", 'z' }
            };

            // StringBuilder to accumulate the decoded characters
            StringBuilder sb = new StringBuilder();
            int i = 0;

            // Iterate through the string
            while (i < s.Length)
            {
                // Check for two-digit characters with #
                if (i + 2 < s.Length && s[i + 2] == '#')
                {
                    string key = s.Substring(i, 3); // Take 3 characters
                    if (mapping.ContainsKey(key))
                    {
                        sb.Append(mapping[key]); // Append decoded character
                        i += 3; // Move 3 steps forward
                    }
                }
                else
                {
                    // Process single character mappings
                    string key = s.Substring(i, 1); // Take 1 character
                    if (mapping.ContainsKey(key))
                    {
                        sb.Append(mapping[key]); // Append decoded character
                        i++; // Move 1 step forward
                    }
                }
            }
            return sb.ToString(); // Return the decoded string
        }
    }
}
```

### How It Works:
1. **Mapping Setup**: A `Dictionary` is used to map string representations of numbers to their respective characters.
2. **String Processing**: The input string is processed character by character. If a `#` character is encountered after two digits, it considers it as a two-digit number (like "10#"). If no `#` is encountered, it handles single digits (like "1").
3. **StringBuilder**: A `StringBuilder` is used for efficiently concatenating the resulting characters.

---

## Example:

```csharp
Decrypt_String_from_Alphabet_to_Integer_Mapping decrypt = new Decrypt_String_from_Alphabet_to_Integer_Mapping();
string result = decrypt.FreqAlphabets("10#11#12"); 
Console.WriteLine(result);  // Output: "jkl"
```
---
## Performance:

- Time Complexity: **O(n)** where `n` is the length of the input string.
- Space Complexity: **O(n)** for storing the result.

---
