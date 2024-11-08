# Clear Digits

## Problem Description
The `ClearDigits` function processes an input string `s` by removing any digits. If a digit is encountered, it removes the last character in the current result string if it exists. If a non-digit character is encountered, it adds that character to the result. This process continues until the entire string is processed.

### Example:
Input: `"a1bc2d"`  
Output: `"ac"`

Input: `"123abc"`  
Output: `"ac"`

## Solution Explanation

### Overview
The function uses a `while` loop to iterate through each character in `s`. When a digit is found, it removes the last character from the `result` string (if any characters are present). Otherwise, it appends the non-digit character to `result`.

### Code

```csharp
public string ClearDigits(string s)
{
    int left = 0, right = s.Length;
    string result = string.Empty;
    while (left < right)
    {
        if (char.IsDigit(s[left]))
        {
            if (result.Length > 0)
                result = result.Remove(result.Length - 1);
        }
        else
        {
            result += s[left];
        }
        left++;
    }

    return result;
}
```

### Explanation of the Code

1. **Initialization**:
   - `left` starts from the beginning of the string, and `right` is set to the length of `s`.
   - `result` is an empty string that will store the final output after processing.

2. **Character Processing**:
   - A `while` loop iterates through each character in `s` from left to right.
   - If `s[left]` is a digit:
     - It removes the last character from `result` if `result` is not empty.
   - If `s[left]` is not a digit, the character is appended to `result`.

3. **Final Output**:
   - The function returns the `result` string after processing all characters in `s`.

### Complexity Analysis
- **Time Complexity**: \(O(N)\), where \(N\) is the length of the input string `s`. The function iterates over each character once.
- **Space Complexity**: \(O(N)\), as `result` may hold up to all non-digit characters of `s`.

### Edge Cases
- **Empty String**: If `s` is empty, the function returns an empty string.
- **All Digits**: If `s` consists only of digits, `result` will remain empty, and the function will return an empty string.
- **No Digits**: If `s` contains no digits, the function returns the input string as is.
- **Single Digit or Character**: If `s` contains a single character (digit or non-digit), it processes accordingly (removes if digit, adds if non-digit).
