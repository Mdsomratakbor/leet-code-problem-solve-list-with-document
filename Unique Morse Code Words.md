# Unique Morse Code Words

## Problem Description

You are given an array of words where each word can be converted into Morse code based on a predefined Morse code representation for each alphabet letter. Your goal is to determine the number of unique Morse code transformations for the given words.

Each lowercase letter can be mapped to a specific Morse code, as shown below:

```
a -> .-      b -> -...    c -> -.-.    d -> -..     e -> .
f -> ..-.    g -> --.     h -> ....    i -> ..      j -> .---
k -> -.-     l -> .-..    m -> --      n -> -.      o -> ---
p -> .--.    q -> --.-    r -> .-.     s -> ...     t -> -
u -> ..-     v -> ...-    w -> .--     x -> -..-    y -> -.--  
z -> --..
```

For example, the word "gin" can be converted into Morse code as follows:
- "g" -> "--."
- "i" -> ".."
- "n" -> "-."

Therefore, "gin" becomes `"--...-."`.

Given a list of words, the task is to find the number of unique Morse code representations among these words.

### Example
```plaintext
Input: words = ["gin", "zen", "gig", "msg"]
Output: 2
Explanation:
The words in Morse code are:
"gin" -> "--...-."
"zen" -> "--...-."
"gig" -> "--...--."
"msg" -> "--...--."

There are 2 unique transformations: `"--...-."` and `"--...--."`.
```

---

## Solution Explanation

The solution approach is as follows:

1. **Define Morse Code Mapping**: We define an array `morseCodes` where each index corresponds to the Morse code for the alphabet letter starting from 'a' (i.e., `morseCodes[0]` for 'a', `morseCodes[1]` for 'b', etc.).

2. **Map Characters to Morse Codes**: We use a `Dictionary` to map each lowercase alphabet letter to its respective Morse code using the `morseCodes` array.

3. **Build Unique Morse Representations**:
    - For each word in the input array, convert it to its Morse code representation by looking up each character's Morse code.
    - Use a `HashSet` to store each unique Morse code transformation, ensuring no duplicates are counted.

4. **Return the Count of Unique Transformations**: The size of the `HashSet` gives the number of unique Morse code transformations.

---

## Code

```csharp
public class Solution {
   public int UniqueMorseRepresentations(string[] words) {
       // Array holding Morse code representations for each letter from 'a' to 'z'
       string[] morseCodes = { ".-", "-...", "-.-.", "-..", ".", "..-.", "--.", "....", "..", ".---", "-.-", 
                               ".-..", "--", "-.", "---", ".--.", "--.-", ".-.", "...", "-", "..-", "...-", 
                               ".--", "-..-", "-.--", "--.." };
       
       // Dictionary to map each letter to its Morse code
       Dictionary<char, string> mapped = new Dictionary<char, string>();
       for (int i = 0; i < morseCodes.Length; i++) {
           mapped.Add((char)('a' + i), morseCodes[i]);
       }

       // HashSet to store unique Morse code transformations
       HashSet<string> result = new HashSet<string>();

       // Convert each word to Morse code and add it to the set
       foreach (string word in words) {
           string morseWord = "";
           foreach (char c in word) {
               morseWord += mapped[c];
           }
           result.Add(morseWord);  // Add the Morse code version of the word
       }

       // Return the count of unique transformations
       return result.Count;
   }
}
```

---

## Complexity Analysis

- **Time Complexity**: O(n * m), where `n` is the number of words and `m` is the average length of each word. Each word is converted to Morse code, and checking uniqueness in a `HashSet` takes O(1) on average.
- **Space Complexity**: O(n), for storing unique Morse code representations in the `HashSet`.

---

## Edge Cases

1. **Empty Input**: If `words` is empty, return 0.
2. **Single Word**: If `words` contains only one word, the answer will be 1.
3. **All Words Identical**: If all words are the same, the answer will be 1.
4. **Different Words, Same Transformation**: If different words have the same Morse code transformation, ensure duplicates are not counted.
