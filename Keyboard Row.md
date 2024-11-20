# Keyboard Row

## Problem Description
The **Keyboard Row** problem is a programming challenge where we are tasked with finding all the words from a given array that can be typed using letters from only one row of a QWERTY keyboard. 

The keyboard is divided into the following rows:

- **First Row**: `QWERTYUIOP`
- **Second Row**: `ASDFGHJKL`
- **Third Row**: `ZXCVBNM`

The input is an array of strings, and the output should be an array containing words that satisfy the above condition.

---

## Solution Approaches

### **Approach 1: HashSet-Based Solution**
This approach utilizes **HashSet** collections to represent the rows of the keyboard. The advantage of using `HashSet` is its constant-time lookup for character containment, which makes the solution efficient.

#### Steps:
1. Create `HashSet` objects for each keyboard row.
2. Iterate through each word in the input array:
    - Convert the word to lowercase for case insensitivity.
    - Determine the row of the first character of the word.
    - Check if all characters of the word belong to the same row.
3. If a word satisfies the condition, add it to the result list.
4. Convert the result list to an array and return.

#### Code:
```csharp
public string[] FindWords(string[] words)
{
    HashSet<char> firstRow = new HashSet<char>("qwertyuiop");
    HashSet<char> secondRow = new HashSet<char>("asdfghjkl");
    HashSet<char> thirdRow = new HashSet<char>("zxcvbnm");
    List<string> result = new List<string>();

    foreach (string word in words)
    {
        string lowerWord = word.ToLower();
        HashSet<char> targetRow = new HashSet<char>();

        if (firstRow.Contains(lowerWord[0]))
            targetRow = firstRow;
        else if (secondRow.Contains(lowerWord[0]))
            targetRow = secondRow;
        else if (thirdRow.Contains(lowerWord[0]))
            targetRow = thirdRow;

        if (lowerWord.All(ch => targetRow.Contains(ch)))
        {
            result.Add(word);
        }
    }
    return result.ToArray();
}
```

---

### **Approach 2: String-Based Solution**
This approach uses string comparison to check which keyboard row the word belongs to.

#### Steps:
1. Define strings representing each keyboard row.
2. Iterate through each word in the input array:
    - Convert the word to lowercase for case insensitivity.
    - Check each character of the word against the rows using nested loops.
3. Count the number of characters that match a row. If the count matches the length of the word, it belongs to that row.
4. If a word satisfies the condition, add it to the result list.
5. Convert the result list to an array and return.

#### Code:
```csharp
public string[] FindWords_Complex_Way(string[] words)
{
    string firstRow = "qwertyuiop";
    string secondRow = "asdfghjkl";
    string thirdRow = "zxcvbnm";
    List<string> result = new List<string>();

    foreach (string word in words)
    {
        int firstRowCount = 0, secondRowCount = 0, thirdRowCount = 0;
        int length = word.Length;
        string lowerWord = word.ToLower();

        foreach (char ch in lowerWord)
        {
            if (firstRow.Contains(ch))
                firstRowCount++;
        }
        if (firstRowCount != length)
        {
            foreach (char ch in lowerWord)
            {
                if (secondRow.Contains(ch))
                    secondRowCount++;
            }
        }
        if (firstRowCount == 0 && secondRowCount != length)
        {
            foreach (char ch in lowerWord)
            {
                if (thirdRow.Contains(ch))
                    thirdRowCount++;
            }
        }
        if (firstRowCount == length || secondRowCount == length || thirdRowCount == length)
        {
            result.Add(word);
        }
    }
    return result.ToArray();
}
```

---

## Comparison of Approaches

| **Aspect**                  | **HashSet-Based Approach** | **String-Based Approach** |
|-----------------------------|----------------------------|---------------------------|
| **Performance**             | Faster due to `HashSet`'s O(1) lookup time. | Slower due to nested loops and string operations. |
| **Code Complexity**         | Cleaner and more concise. | More verbose and detailed. |
| **Space Usage**             | Requires additional memory for `HashSet`. | Lower memory footprint (uses strings). |

---

## Example

### Input:
```plaintext
words = ["Hello", "Alaska", "Dad", "Peace"]
```

### Output:
```plaintext
["Alaska", "Dad"]
```

### Explanation:
- "Hello" contains characters from multiple rows.
- "Alaska" contains only characters from the second row.
- "Dad" contains only characters from the second row.
- "Peace" contains characters from multiple rows.

---

## Conclusion
Both solutions solve the problem effectively, but the **HashSet-based solution** is preferred due to its performance advantages. Use the string-based solution if memory constraints are critical or additional clarity in character matching is desired.
