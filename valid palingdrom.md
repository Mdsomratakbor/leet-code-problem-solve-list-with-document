

# Valid Palindrome

## Problem Description
The `IsPalindrome` function checks whether a given string is a palindrome, ignoring non-alphanumeric characters and case differences. A palindrome reads the same forwards and backwards.

### Example:
Input: `"A man, a plan, a canal: Panama"`  
Output: `true`  

Input: `"race a car"`  
Output: `false`  

## Solution Explanation

### Overview
This function uses two main steps:
1. It filters the input string to retain only alphanumeric characters and convert it to lowercase.
2. It performs a two-pointer comparison from the beginning and end of the string towards the center to determine if the filtered string is a palindrome.

### Code

```csharp
public bool IsPalindrome(string s)
{
    var result = new StringBuilder();
    foreach (char c in s)
    {
        if (char.IsLetterOrDigit(c))
        {
            result.Append(c);
        }
    }
    s = result.ToString().ToLower();

    int right = s.Length - 1, left = 0;
    while (left < right)
    {
        if (s[right] != s[left])
            return false;
        left++;
        right--;
    }
    return true;
}
```

### Explanation of the Code

1. **String Filtering**:
   - A `StringBuilder` named `result` is used to store only the alphanumeric characters from `s`.
   - Each character in `s` is checked; if it's alphanumeric, it's appended to `result`.
   - The filtered string is then converted to lowercase for case-insensitive comparison.

2. **Two-Pointer Comparison**:
   - `left` starts from the beginning, and `right` starts from the end of the filtered string.
   - The function checks characters at `left` and `right`. If they are not equal, the string is not a palindrome, and `false` is returned.
   - If characters match, the pointers move inward (increment `left` and decrement `right`).
   - If all comparisons are successful, the string is a palindrome, and `true` is returned.

### Complexity Analysis
- **Time Complexity**: \(O(N)\), where \(N\) is the length of the input string. This includes filtering the string and performing the palindrome check.
- **Space Complexity**: \(O(N)\), due to the additional `StringBuilder` for storing the filtered string.

### Edge Cases
- **Empty String**: An empty string should return `true` because an empty string is trivially a palindrome.
- **String with No Alphanumeric Characters**: If the string contains only non-alphanumeric characters, the function returns `true` because, after filtering, the string would be empty.
- **Single Character String**: A single alphanumeric character is always a palindrome.
