# Detect Capital Use

## Problem Statement
Given a word, you need to determine if the usage of capital letters in the word is correct. The rules for correct capitalization are as follows:

1. All letters in the word are uppercase (e.g., `USA`).
2. All letters in the word are lowercase (e.g., `leetcode`).
3. Only the first letter in the word is uppercase (e.g., `Google`).

The function should return `true` if the word satisfies one of these rules, otherwise, it should return `false`.

## Solution
The solution is implemented in the `DetectCapital` class. The key idea is to check for consistent capitalization patterns using logical conditions and iterate through the word to ensure it adheres to one of the rules.

### Code Implementation
```csharp
using System;

namespace LeetCodeProblems
{
    public class DetectCapital
    {
        public bool DetectCapitalUse(string word)
        {
            if (string.IsNullOrEmpty(word))
                return false;

            bool isFirstCapital = char.IsUpper(word[0]);
            bool areAllCaps = word.Length > 1 && char.IsUpper(word[1]);

            for (int i = 1; i < word.Length; i++)
            {
                // Check consistency based on the case of the first two letters
                if ((areAllCaps && !char.IsUpper(word[i])) ||
                    (!areAllCaps && char.IsUpper(word[i])))
                {
                    return false;
                }
            }

            return true;
        }
    }
}
```

## Usage
1. Clone this repository.
2. Add the code to your C# project or run it in an online compiler.
3. Call the `DetectCapitalUse` method with a string input to validate the capitalization.

### Example Usage
```csharp
using System;

namespace LeetCodeProblems
{
    class Program
    {
        static void Main(string[] args)
        {
            DetectCapital detectCapital = new DetectCapital();

            Console.WriteLine(detectCapital.DetectCapitalUse("USA")); // Output: true
            Console.WriteLine(detectCapital.DetectCapitalUse("leetcode")); // Output: true
            Console.WriteLine(detectCapital.DetectCapitalUse("Google")); // Output: true
            Console.WriteLine(detectCapital.DetectCapitalUse("FlaG")); // Output: false
        }
    }
}
```

## Explanation
- **Case 1**: If all letters are uppercase, the method validates that all characters from index 1 are uppercase.
- **Case 2**: If all letters are lowercase, the method validates that no character after index 1 is uppercase.
- **Case 3**: If only the first letter is uppercase, the method ensures all other characters are lowercase.

## Edge Cases
- Empty string (`""`) - Returns `false`.
- Single-character words - Always return `true` as they satisfy the rules.

## Time Complexity
The solution has a time complexity of **O(n)**, where `n` is the length of the input word, as it iterates through the word only once.

## Space Complexity
The solution has a space complexity of **O(1)**, as no additional data structures are used.
