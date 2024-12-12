# Determine if String Halves Are Alike

This repository provides a solution to the problem **"Determine if String Halves Are Alike"**, which involves checking if the number of vowels in the first half of a string equals the number of vowels in the second half.

---

## Problem Statement
You are given a string `s` of even length. Split this string into two halves of equal length. Determine if the first half and the second half contain the same number of vowels. Return `true` if they do; otherwise, return `false`.

### Example:
```plaintext
Input: s = "book"
Output: true
Explanation: The first half "bo" has 1 vowel ('o') and the second half "ok" has 1 vowel ('o').

Input: s = "textbook"
Output: false
Explanation: The first half "text" has 1 vowel ('e') and the second half "book" has 2 vowels ('o', 'o').
```

---

## Solution Overview
The solution involves:
1. Converting the string to lowercase to handle case insensitivity.
2. Using a two-pointer approach to iterate through the first and second halves of the string simultaneously.
3. Counting vowels in each half and comparing the counts.

---

## Implementation
The implementation is written in C#.

```csharp
using System;

namespace LeetCodeProblems
{
    internal class Determine_if_String_Halves_Are_Alike
    {
        public bool HalvesAreAlike(string s)
        {
            s = s.ToLower();
            int firstHalfVowel = 0, secondHalfVowel = 0, left = 0, half = 0, right = 0, length = 0;

            length = s.Length;
            right = length - 1;
            half = length / 2;

            while (left < half && right >= half)
            {
                if (s[left] == 'a' || s[left] == 'e' || s[left] == 'i' || s[left] == 'o' || s[left] == 'u')
                    firstHalfVowel++;
                if (s[right] == 'a' || s[right] == 'e' || s[right] == 'i' || s[right] == 'o' || s[right] == 'u')
                    secondHalfVowel++;
                left++;
                right--;
            }

            return firstHalfVowel == secondHalfVowel;
        }
    }
}
```

---

## Key Features
- **Two-Pointer Technique**: Efficiently compares the first and second halves of the string.
- **Case Insensitivity**: Converts the string to lowercase for uniform vowel comparison.
- **Direct Vowel Check**: Matches characters against a list of vowels ('a', 'e', 'i', 'o', 'u').

---

## Complexity Analysis
- **Time Complexity**: `O(n)`, where `n` is the length of the string. The loop iterates through half of the string.
- **Space Complexity**: `O(1)`, since no additional data structures are used apart from a few integer variables.

---

## Example Usage
Here is an example of how to use the solution:

```csharp
class Program
{
    static void Main(string[] args)
    {
        var checker = new Determine_if_String_Halves_Are_Alike();
        string input = "book";

        bool result = checker.HalvesAreAlike(input);
        Console.WriteLine(result); // Output: true
    }
}
```

