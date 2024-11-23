
```markdown
# Merge Strings Alternately

## Problem Statement

Given two strings `word1` and `word2`, merge them alternately into a new string by taking one character at a time from each string in order. If one string is longer than the other, append the remaining characters of the longer string to the end of the merged string.

### Example:

```plaintext
Input:
word1 = "abc"
word2 = "pqr"

Output:
"apbqcr"
```

If the strings have unequal lengths, the extra characters from the longer string are appended to the result after all characters from the shorter string have been merged alternately.

### Example 2:

```plaintext
Input:
word1 = "abc"
word2 = "defgh"

Output:
"adbecfgh"
```

### Constraints:
- `1 <= word1.length, word2.length <= 100`
- `word1` and `word2` consist of lowercase English letters.

## Solution Explanation

This solution provides two methods to merge the strings alternately.

### Method 1: `MergeAlternately`

The `MergeAlternately` method iterates through both strings and appends characters from both strings alternately to the result string. It checks whether there are remaining characters in each string before appending them.

#### Code:

```csharp
public string MergeAlternately(string word1, string word2)
{
    int left = 0, rightWord1 = word1.Length, rightWord2 = word2.Length;
    int right = Math.Max(rightWord1, rightWord2); // Max length of both strings

    StringBuilder result = new StringBuilder();
    while (left < right)
    {
        if (left < rightWord1)
        {
            result.Append(word1[left]); // Append character from word1 if it exists
        }
        if (left < rightWord2)
        {
            result.Append(word2[left]); // Append character from word2 if it exists
        }
        left++;
    }
    return result.ToString();
}
```

#### Explanation:
1. **Iterate** through both strings using the `left` pointer.
2. **Append characters** from both `word1` and `word2` if the `left` pointer is within bounds for each string.
3. Continue appending characters until all characters from both strings are processed.

### Method 2: `MergeAlternately_2`

This method is a simplified version of the first. It uses a while loop to run as long as either of the strings has remaining characters. The check `while (left < rightWord1 || left < rightWord2)` ensures that both strings are processed.

#### Code:

```csharp
public string MergeAlternately_2(string word1, string word2)
{
    int left = 0, rightWord1 = word1.Length, rightWord2 = word2.Length;
    StringBuilder result = new StringBuilder();
    while (left < rightWord1 || left < rightWord2)
    {
        if (left < rightWord1)
        {
            result.Append(word1[left]); // Append character from word1 if it exists
        }
        if (left < rightWord2)
        {
            result.Append(word2[left]); // Append character from word2 if it exists
        }
        left++;
    }
    return result.ToString();
}
```

#### Explanation:
- This method checks if there are remaining characters in either string using `left < rightWord1 || left < rightWord2`.
- If characters remain, it appends them alternately from both strings.

## Time and Space Complexity

- **Time Complexity**: O(n + m), where `n` is the length of `word1` and `m` is the length of `word2`. We iterate through both strings once.
- **Space Complexity**: O(n + m) for the `StringBuilder` that stores the merged string.

## Usage

You can use the `Merge_Strings_Alternately` class in your C# program to merge two strings alternately.

```csharp
Merge_Strings_Alternately merger = new Merge_Strings_Alternately();
string result = merger.MergeAlternately("abc", "pqr");
Console.WriteLine(result); // Output: "apbqcr"
```
