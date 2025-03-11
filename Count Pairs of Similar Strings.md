# Count Pairs of Similar Strings

## Problem Description

The problem asks to find the number of pairs of words in a given list where both words are similar. Two words are considered similar if they contain the same set of unique characters. The order of characters does not matter.

For example, the words `"abc"` and `"cab"` are similar because they contain the same unique characters: `{'a', 'b', 'c'}`.

## Problem Approach

We have two approaches implemented in the code to solve this problem:

1. **Optimized Approach**:
    - For each word, we compute a unique character key by extracting the unique characters, sorting them, and converting them into a string.
    - Using a dictionary, we count how many times each unique character key occurs.
    - For each occurrence of a unique character key, we count how many pairs can be formed using it.

2. **Old Approach**:
    - For each word, we remove duplicate characters and create a string representing the unique characters.
    - Then, for every pair of words, we check if they have the same unique characters by comparing them character by character.

---

## Code Explanation

### 1. Optimized Approach (`SimilarPairs` method)

```csharp
public int SimilarPairs(string[] words)
{
    Dictionary<string, int> uniqueWordCount = new Dictionary<string, int>();
    int count = 0;

    foreach(var word in words)
    {
        string uniqueCharKey = GetUniqueCharacterKey(word);

        if (uniqueWordCount.ContainsKey(uniqueCharKey))
        {
            count += uniqueWordCount[uniqueCharKey];
            uniqueWordCount[uniqueCharKey]++;
        }
        else
        {
            uniqueWordCount[uniqueCharKey] = 1;
        }
    }
    return count;
}
```

- **Description**: 
    - We iterate through each word in the input array `words`.
    - For each word, we generate a unique key that represents its unique characters.
    - We maintain a dictionary `uniqueWordCount` to keep track of the frequency of each unique key.
    - If a word has the same unique character key as another word, we increment the count for each such pair.

### 2. Helper Method (`GetUniqueCharacterKey`)

```csharp
static string GetUniqueCharacterKey(string word)
{
    HashSet<char> charSet = new HashSet<char>(word);
    char[] sortedChars = new char[charSet.Count];
    charSet.CopyTo(sortedChars);
    Array.Sort(sortedChars);
    return new string(sortedChars);
}
```

- **Description**: 
    - This method takes a word as input and converts it into a string representing the sorted unique characters of the word.

### 3. Old Approach (`SimilarPairs_Old` method)

```csharp
public int SimilarPairs_Old(string[] words)
{
    string[] uniqueCharacterWord = new string[words.Length];
    int count = 0;
    for (int i = 0; i < words.Length; i++)
    {
        string word = words[i];
        uniqueCharacterWord[i] = RemoveDuplicateCharacters(word);
    }
    for (int i = 0; i < uniqueCharacterWord.Length; i++)
    {
        for (int j = i + 1; j < uniqueCharacterWord.Length; j++)
        {
            if (HaveSameUniqueCharacters(uniqueCharacterWord[i], uniqueCharacterWord[j]))
                count++;
        }
    }
    return count;
}
```

- **Description**: 
    - This approach removes duplicates from each word and compares each pair of words to check if they have the same unique characters.

### 4. Helper Method (`HaveSameUniqueCharacters`)

```csharp
static bool HaveSameUniqueCharacters(string word1, string word2)
{
    bool[] chars1 = new bool[26];
    bool[] chars2 = new bool[26];

    foreach (char c in word1)
        chars1[c - 'a'] = true;

    foreach (char c in word2)
        chars2[c - 'a'] = true;
    for (int i = 0; i < 26; i++)
    {
        if (chars1[i] != chars2[i])
            return false;
    }

    return true;
}
```

- **Description**: 
    - This helper function compares the unique characters of two words by marking their characters in a boolean array and checking if both arrays match.

### 5. Helper Method (`RemoveDuplicateCharacters`)

```csharp
static string RemoveDuplicateCharacters(string word)
{
    bool[] seen = new bool[26];
    StringBuilder sb = new StringBuilder();

    foreach (char c in word)
    {
        if (!seen[c - 'a'])
        {
            sb.Append(c);
            seen[c - 'a'] = true;
        }
    }

    return sb.ToString();
}
```

- **Description**: 
    - This method removes duplicate characters from a word and returns a string of unique characters.

---

## Time Complexity

- **Optimized Approach**: The time complexity of the optimized approach is primarily determined by the following:
    - The operation to compute the unique character key for each word takes O(m log m), where m is the length of the word (due to sorting).
    - We process each word only once, making the time complexity for this approach O(n * m log m), where n is the number of words and m is the average length of the words.

- **Old Approach**: The old approach has a higher time complexity due to the nested loops:
    - Removing duplicates for each word takes O(m) time.
    - Comparing pairs of words has a time complexity of O(n² * m), where n is the number of words and m is the average word length.

---

## Example

### Input:
```csharp
string[] words = {"aba", "aab", "abc", "cab"};
```

### Output:
```csharp
int result = SimilarPairs(words); // Output will be 2
```

### Explanation:
- `"aba"` and `"aab"` are similar because both contain the same unique characters `{'a', 'b'}`.
- `"abc"` and `"cab"` are similar because both contain the same unique characters `{'a', 'b', 'c'}`.

Thus, there are 2 similar pairs in total.
