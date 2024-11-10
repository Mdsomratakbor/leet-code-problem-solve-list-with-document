# Find Words Containing Character

This repository contains the solution to the problem of finding the indices of words that contain a specified character.

## Problem Description

Given an array of words, `FindWordsContaining` identifies all indices of words containing a specific character `x`. This can be helpful in text processing tasks where we need to locate words with certain attributes.

### Example:
```csharp
Input:
words = ["apple", "banana", "cherry", "date"]
x = 'a'

Output:
[0, 1, 3]
```

### Explanation:
- The function checks each word in the array to see if it contains the character `x`. 
- In the example above:
  - `"apple"` (index 0) contains 'a'
  - `"banana"` (index 1) contains 'a'
  - `"date"` (index 3) contains 'a'
- Thus, the result is `[0, 1, 3]`.

## Solution

The solution is implemented in the `FindWordsContainingCharacter` class as a function called `FindWordsContaining`, which returns a list of indices for words containing the character `x`.

### Code:
```csharp
using System;
using System.Collections.Generic;

namespace LeetCodeProblems
{
    internal class Find_Words_Containing_Character
    {
        public IList<int> FindWordsContaining(string[] words, char x)
        {
            List<int> result = new List<int>();

            for(int i = 0; i < words.Length; i++)
            {
                if (words[i].Contains(x))
                {
                    result.Add(i);
                }
            }
            return result;
        }
    }
}
```

### Method Explanation:
- **Input Parameters**:
  - `words`: An array of strings representing the words to search through.
  - `x`: The character to look for in each word.
- **Output**:
  - A list of indices where each index corresponds to a word in the array that contains the specified character `x`.

### Complexity Analysis
- **Time Complexity**: `O(n * m)`, where `n` is the number of words, and `m` is the average length of each word (due to the `Contains` method check).
- **Space Complexity**: `O(k)`, where `k` is the number of indices stored in the result list.

## Usage

To use this code:
1. Clone this repository.
2. Include the `Find_Words_Containing_Character` class in your C# project.
3. Instantiate the class and call the `FindWordsContaining` method with your `words` array and character `x`.

### Example Usage:
```csharp
using System;
using LeetCodeProblems;

class Program
{
    static void Main()
    {
        string[] words = { "apple", "banana", "cherry", "date" };
        char x = 'a';

        Find_Words_Containing_Character finder = new Find_Words_Containing_Character();
        IList<int> indices = finder.FindWordsContaining(words, x);

        Console.WriteLine("Indices of words containing '" + x + "': " + string.Join(", ", indices));
    }
}
```
