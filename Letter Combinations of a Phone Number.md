# Letter Combinations of a Phone Number

## Problem Description
Given a string containing digits from `2` to `9`, return all possible letter combinations that the number could represent. Each digit maps to a set of letters similar to the mapping on a telephone keypad.

### Example:
Input: `"23"`  
Output: `["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"]`

## Solution Explanation

### Overview
This solution uses backtracking to generate all possible combinations. We start with an initial list containing an empty string and then add new combinations iteratively for each digit.

### Code

```csharp
public IList<string> LetterCombinations(string digits)
{
    List<string> result = new List<string>();
    Dictionary<char, string> mappings = new Dictionary<char, string>()
            {
                { '2', "abc" },
                { '3', "def" },
                { '4', "ghi" },
                { '5', "jkl" },
                { '6', "mno" },
                { '7', "pqrs" },
                { '8', "tuv" },
                { '9', "wxyz" }
            };

    result.Add(""); // Start with an empty string as the initial combination

    foreach (var digit in digits)
    {
        List<string> newResult = new List<string>();

        foreach (var letter in mappings[digit])
        {
            foreach (var combination in result)
            {
                newResult.Add(combination + letter);
            }
        }
        result = newResult;
    }

    return result;
}
```

### Explanation of the Code

1. **Dictionary Setup**: A dictionary, `mappings`, is used to store the letter mappings for each digit from `2` to `9`.
2. **Initial Setup**: We initialize `result` with an empty string, as this will act as the base for building combinations.
3. **Loop Through Digits**: For each digit in `digits`, we perform the following:
   - Create a new list `newResult` to store the updated combinations.
   - For each letter associated with the digit, append it to each existing combination in `result` and store it in `newResult`.
4. **Update Result**: After processing each digit, we update `result` to `newResult`, which contains the new combinations formed.

5. **Return Result**: After processing all digits, `result` contains all the valid letter combinations.

### Complexity Analysis
- **Time Complexity**: \(O(3^N \times 4^M)\), where \(N\) is the number of digits that map to three letters (like `2`, `3`, `4`, etc.) and \(M\) is the number of digits that map to four letters (like `7` and `9`).
- **Space Complexity**: \(O(3^N \times 4^M)\), which is the total number of combinations.

### Edge Cases
- If `digits` is an empty string, the function will return an empty list.
- If `digits` contains any characters other than `2` to `9`, it may raise an error because they are not mapped.

### Usage
This code can be used in applications that involve generating all possible strings or sequences from a given set of options, such as creating word combinations, auto-suggestions, and similar use cases.

---------------------------------



### Another Solution Using Recursive function

## Solution Explanation

### Overview
This solution utilizes recursive backtracking to generate all possible combinations. The `BackTracking` function is called recursively to build up each combination by iterating through letters mapped to each digit.

### Code

```csharp
public IList<string> LetterCombinations(string digits)
{
    Dictionary<char, string> mappings = new Dictionary<char, string>()
        {
            { '2', "abc" },
            { '3', "def" },
            { '4', "ghi" },
            { '5', "jkl" },
            { '6', "mno" },
            { '7', "pqrs" },
            { '8', "tuv" },
            { '9', "wxyz" }
        };

    if (!string.IsNullOrEmpty(digits))
        BackTracking(0, digits, mappings, "");
    
    return result;
}

public void BackTracking(int index, string digits, Dictionary<char, string> mappings, string currentString)
{
    if (currentString.Length == digits.Length)
    {
        result.Add(currentString);
        return;
    }

    foreach (var letter in mappings[digits[index]])
    {
        currentString += letter;
        BackTracking(index + 1, digits, mappings, currentString);
        currentString = currentString.Substring(0, currentString.Length - 1);  // Backtrack to try the next letter
    }
}
```

### Explanation of the Code

1. **Mappings Initialization**: A dictionary `mappings` stores letter mappings for each digit from `2` to `9`.
2. **Recursive Backtracking Setup**: The `BackTracking` function is called with initial values if `digits` is not empty.
3. **Base Case**: Inside `BackTracking`, if `currentString` has the same length as `digits`, the combination is complete and is added to `result`.
4. **Recursive Step**: For each letter associated with the current digit:
   - Append the letter to `currentString`.
   - Call `BackTracking` with the next index.
   - Backtrack by removing the last character to explore other possible letters for that position.

5. **Backtracking Mechanism**: After each recursive call, `currentString` is reverted by removing the last added letter, allowing other paths to be explored without interference from previous choices.

### Complexity Analysis
- **Time Complexity**: \(O(3^N \times 4^M)\), where \(N\) is the number of digits with three letters (like `2`, `3`, `4`, etc.) and \(M\) is the number of digits with four letters (like `7` and `9`).
- **Space Complexity**: \(O(3^N \times 4^M)\), which is the space required to store all possible combinations in `result`.

### Edge Cases
- **Empty Input**: If `digits` is an empty string, the function returns an empty list as no combinations are possible.
- **Invalid Characters**: If `digits` contains characters other than `2` to `9`, behavior is undefined and may raise an error.

