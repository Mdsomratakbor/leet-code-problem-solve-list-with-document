# License Key Formatting

This GitHub document provides two implementations of the License Key Formatting problem in C#. The task involves reformatting a string `s` into groups of size `k` while removing dashes and converting letters to uppercase.

## Problem Statement
Given a string `s` (consisting of alphanumeric characters and dashes) and an integer `k`, format the string such that:
1. All dashes are removed.
2. The string is divided into groups of size `k`, separated by dashes.
3. The letters in the string are converted to uppercase.
4. The first group may be shorter than `k` but all other groups must be exactly `k` characters.

## Implementation Details
Below are two different implementations of the License Key Formatting problem.

### 1. **Standard Implementation**
This method uses a `StringBuilder` to construct the formatted string by traversing the input string from the end.

```csharp
using System;
using System.Text;
using System.Linq;

namespace LeetCodeProblems
{
    internal class License_Key_Formatting
    {
        public string LicenseKeyFormatting(string s, int k)
        {
            StringBuilder formatted = new StringBuilder();
            int count = 0;

            for (int i = s.Length - 1; i >= 0; i--)
            {
                if (s[i] != '-')
                {
                    if (count == k)
                    {
                        formatted.Append('-');
                        count = 0;
                    }
                    formatted.Append(char.ToUpper(s[i]));
                    count++;
                }
            }

            // Reverse the string as we built it from the back
            return new string(formatted.ToString().Reverse().ToArray());
        }
    }
}
```

#### Explanation
- **Input Traversal**: Traverse the string from the last character to the first.
- **Character Validation**: Skip dashes (`'-'`) while processing.
- **Group Formation**: Add a dash (`'-'`) after every `k` characters.
- **Final Reversal**: Reverse the string to get the correct order since it was constructed from the end.

### 2. **Optimized Implementation**
This implementation uses the `Insert` method to build the formatted string at the beginning, avoiding the need to reverse the string at the end.

```csharp
using System;
using System.Text;

namespace LeetCodeProblems
{
    internal class License_Key_Formatting
    {
        public string LicenseKeyFormatting__10PercentOptimized(string s, int k)
        {
            StringBuilder newStringBuilder = new StringBuilder();
            int count = 0;
            int i = s.Length - 1;

            while (i >= 0)
            {
                if (s[i] != '-')
                {
                    if (count >= k)
                    {
                        newStringBuilder.Insert(0, '-');
                        count = 0;
                        continue;
                    }
                    newStringBuilder.Insert(0, char.ToUpper((s[i])));
                    count++;
                }
                i--;
            }

            return newStringBuilder.ToString();
        }
    }
}
```

#### Explanation
- **Input Traversal**: Process the input string from the end to the beginning.
- **Efficient Building**: Use `Insert(0, ...)` to prepend characters and dashes, avoiding the need for reversal.
- **Dash Insertion**: Insert dashes dynamically when the count reaches `k`.

## Example
Input:
```plaintext
s = "2-4A0r7-4k", k = 4
```
Output:
```plaintext
"24A0-R74K"
```

Input:
```plaintext
s = "2-4A0r7-4k", k = 3
```
Output:
```plaintext
"24-A0R-74K"
```

## Key Points
- Both implementations achieve the same goal but have slightly different approaches to string construction.
- The second implementation may offer slight performance improvements by avoiding string reversal.
