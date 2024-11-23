

# Check if All 'A's Appear Before All 'B's

## Problem Description

The task is to determine if all 'A' characters appear before any 'B' characters in the input string. If there is any 'B' before an 'A', or if an 'A' appears after a 'B', the function should return `false`. Otherwise, it returns `true`.

### Example:
- Input: `"aaabbb"`
  - Output: `true`
- Input: `"abab"`
  - Output: `false`
- Input: `"bbaa"`
  - Output: `false`

## Solution

The solution iterates over each character of the string and ensures that once a 'B' has been found, no 'A' is encountered after it. It utilizes a simple flag `isFoundB` to keep track of whether a 'B' has been encountered in the string.

## Code Implementation

```csharp
using System;

namespace LeetCodeProblems
{
    internal class Check_if_All_A_s_Appears_Before_All_B_s
    {
        public bool CheckString(string s)
        {
            bool isFoundB = false;
            foreach (char c in s)
            {
                char lowerChar = Char.ToLower(c);

                if (lowerChar == 'b')
                {
                    isFoundB = true;
                }
                else if (isFoundB && lowerChar == 'a')
                {
                    return false;
                }
            }
            return true;
        }
    }
}
```

## Instructions

1. Clone this repository to your local machine.
   
   ```bash
   git clone https://github.com/yourusername/Check-if-All-A-s-Appears-Before-All-B-s.git
   ```

2. Open the project in Visual Studio or any C# compatible IDE.

3. Run the solution to check if all 'A's appear before all 'B's in a string.

## Usage Example

You can use the `CheckString` method like this:

```csharp
var checker = new Check_if_All_A_s_Appears_Before_All_B_s();
bool result = checker.CheckString("aaabbb");
Console.WriteLine(result); // Output: true
```

## Testing

You can create additional test cases to validate the solution. Here are a few test cases to get you started:

```csharp
Console.WriteLine(checker.CheckString("aaabbb"));  // true
Console.WriteLine(checker.CheckString("abab"));    // false
Console.WriteLine(checker.CheckString("aabb"));    // true
Console.WriteLine(checker.CheckString("bbaa"));    // false
```


