# Check If a Word Occurs as a Prefix of Any Word in a Sentence

This repository contains a solution to the problem **"Check If a Word Occurs as a Prefix of Any Word in a Sentence"**. The problem involves determining the first occurrence of a word as a prefix within a given sentence.

## Problem Statement
Given a sentence consisting of words separated by spaces, and a search word, return the index of the first word in the sentence that contains the search word as a prefix. If no such word exists, return `-1`.

### Example:
```plaintext
Input: sentence = "i love eating burger", searchWord = "burg"
Output: 4
Explanation: "burger" is the 4th word in the sentence and starts with "burg".

Input: sentence = "hello from the other side", searchWord = "they"
Output: -1
Explanation: No word starts with "they".
```

---

## Solution Overview
The solution uses the `Split` method to break the sentence into an array of words. It then iterates through the array, checking if each word starts with the `searchWord` using the `StartsWith` method. The index of the matching word is returned, or `-1` if no match is found.

---

## Implementation
The implementation is written in C#.

```csharp
using System;
using System.Text;

namespace LeetCodeProblems
{
    internal class Check_If_a_Word_Occurs_As_a_Prefix_of_Any_Word_in_a_Sentence
    {
        public int IsPrefixOfWord(string sentence, string searchWord)
        {
            string[] arrayOfString = sentence.Split(' ');
            int count = 1;
            foreach (string word in arrayOfString)
            {
                if (word.StartsWith(searchWord))
                {
                    return count;
                }
                count++;
            }
            return -1;
        }
    }
}
```

---

## Key Features
- **Efficient Word Search**: Iterates through words and checks prefixes using the built-in `StartsWith` method.
- **Simple and Readable**: Uses straightforward logic for splitting and iterating through the words.

---

## Complexity Analysis
- **Time Complexity**: `O(n * m)`, where `n` is the number of words in the sentence and `m` is the average length of a word.
- **Space Complexity**: `O(k)`, where `k` is the number of words in the sentence (due to the array created by `Split`).

---

## Example Usage
To test the solution, instantiate the class and call the `IsPrefixOfWord` method:

```csharp
class Program
{
    static void Main(string[] args)
    {
        var checker = new Check_If_a_Word_Occurs_As_a_Prefix_of_Any_Word_in_a_Sentence();
        string sentence = "i love eating burger";
        string searchWord = "burg";

        int result = checker.IsPrefixOfWord(sentence, searchWord);
        Console.WriteLine(result); // Output: 4
    }
}
```

