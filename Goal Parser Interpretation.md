# Goal Parser Interpretation

## Problem Statement
You are given a string `command` that represents an interpreted version of a goal parser language. The language follows these rules:

- `'G'` is interpreted as `'G'`.
- `"()"` is interpreted as `'o'`.
- `"(al)"` is interpreted as `'al'`.

Your task is to implement a function that returns the interpreted string.

## Solution Explanation
The solution iterates through the string while checking patterns:
1. If the current character is `'G'`, append `'G'` to the result.
2. If it is `'('`, check the next character:
   - If `')'` follows, append `'o'`.
   - If `'a'` follows, recognize `"(al)"` and append `'al'`.
3. Use a **StringBuilder** for efficient string concatenation.

## Code Implementation
```csharp
using System;
using System.Text;

namespace LeetCodeProblems {
    public class GoalParserInterpretation {
        public string Interpret(string command) {
            StringBuilder result = new StringBuilder();
            int i = 0;
            while (i < command.Length) {
                if (command[i] == 'G') {
                    result.Append("G");
                    i++;
                } else if (command[i] == '(') {
                    if (command[i + 1] == ')') {
                        result.Append("o");
                        i += 2;
                    } else if (command[i + 1] == 'a') {
                        result.Append("al");
                        i += 4;
                    }
                }
            }
            return result.ToString();
        }
    }
}
```

## Complexity Analysis
- **Time Complexity**: `O(n)`, where `n` is the length of `command`. Each character is processed once.
- **Space Complexity**: `O(n)`, as the `StringBuilder` stores the interpreted result.

## Example Usage
```csharp
GoalParserInterpretation parser = new GoalParserInterpretation();
Console.WriteLine(parser.Interpret("G()(al)")); // Output: "Goal"
Console.WriteLine(parser.Interpret("G()()()G")); // Output: "GoGoG"
```

## Edge Cases Considered
- **Only `G`**: e.g., `"GGG"` should return `"GGG"`.
- **Only `()`, `G()`, or `(al)`**: Each should be parsed correctly.
- **Mixed cases**: `"G()(al)()G"` should return `"GoalG"`.

