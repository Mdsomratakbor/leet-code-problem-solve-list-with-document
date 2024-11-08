# IsBalanced Function

## Problem Description
The `IsBalanced` function checks whether a given string of digits, `num`, has balanced sums of digits at odd and even positions. If the sum of digits at odd indices equals the sum of digits at even indices, the function returns `true`; otherwise, it returns `false`.

### Example:
Input: `"1230"`  
Output: `true` (Sum at even indices `1 + 3 = 4`, sum at odd indices `2 + 0 = 4`)

Input: `"12345"`  
Output: `false` (Sum at even indices `1 + 3 + 5 = 9`, sum at odd indices `2 + 4 = 6`)

## Solution Explanation

### Overview
The function uses a single loop to iterate over each character in the input string, converting each character to its integer value. It then sums up the digits at odd and even indices separately. Finally, it compares these sums and returns `true` if they are equal.

### Code

```csharp
public class Solution
{
    public bool IsBalanced(string num)
    {
        int oddSum = 0, evenSum = 0;

        for (int i = 0; i < num.Length; i++)
        {
            int number = num[i] - '0';
            if (i % 2 == 0)
            {
                evenSum += number;
            }
            else
            {
                oddSum += number;
            }
        }

        return oddSum == evenSum;
    }
}
```

### Explanation of the Code

1. **Sum Calculation**:
   - Two integer variables, `oddSum` and `evenSum`, are initialized to zero.
   - A `for` loop iterates through each character in `num`:
     - The current character is converted to an integer by subtracting the character `'0'`.
     - If the index `i` is even, the digit is added to `evenSum`.
     - If the index `i` is odd, the digit is added to `oddSum`.

2. **Comparison**:
   - After the loop completes, the function checks if `oddSum` and `evenSum` are equal.
   - If they are, the function returns `true`, indicating that `num` is balanced. Otherwise, it returns `false`.

### Complexity Analysis
- **Time Complexity**: \(O(N)\), where \(N\) is the length of `num`. The function iterates over each character in the string once.
- **Space Complexity**: \(O(1)\), as it uses only a constant amount of extra space for `oddSum` and `evenSum`.

### Edge Cases
- **Empty String**: If `num` is an empty string, the function returns `true`, as both sums are zero and thus equal.
- **Single Digit**: If `num` has a single digit, it returns `false` as there’s no comparison between sums.
- **All Zeros**: If `num` contains only zeros, it returns `true` since both sums will be zero.
