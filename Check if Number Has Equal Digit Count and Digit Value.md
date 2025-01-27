# Check if Number Has Equal Digit Count and Digit Value

## Problem Statement
Given a string `num` consisting of digits (0-9), verify if for every index `i`, the digit at `num[i]` represents the count of digit `i` in the string.

### Example:

**Input:** `num = "1210"`  
**Output:** `true`  
**Explanation:**
- The digit `0` appears `1` time.
- The digit `1` appears `2` times.
- The digit `2` appears `1` time.
- The digit `3` (or any other higher digit) appears `0` times.

The solution must return `true` because the count matches the value at each index.

---

## Implementation

### **Approach 1: Using LINQ to Count Digits Dynamically**

```csharp
public bool DigitCount_Approach1(string num)
{
    for (int i = 0; i < num.Length; i++)
    {
        int value = num[i] - '0';
        int count = num.Count(c => c - '0' == i);
        if (count != value)
        {
            return false;
        }
    }
    return true;
}
```

#### Explanation:
1. Iterate through each character in the string using a `for` loop.
2. Convert the character at index `i` to an integer (`value`), which represents the expected count of the digit `i` in the string.
3. Use LINQ's `Count` method to count the occurrences of digit `i` in the string.
4. Compare the actual count of the digit (`count`) with its expected value (`value`).
5. If any mismatch is found, return `false`. Otherwise, return `true` after completing the loop.

#### Complexity Analysis:
- **Time Complexity:** O(n^2), where `n` is the length of the string. This is because the `Count` method is called for every character, and it iterates through the entire string each time.
- **Space Complexity:** O(1), as no extra data structures are used.

---

### **Approach 2: Precomputing Digit Counts Using an Array**

```csharp
public bool DigitCount(string num)
{
    int[] digitCount = new int[10];
    foreach (char c in num)
    {
        digitCount[c - '0']++;
    }
    for (int i = 0; i < num.Length; i++)
    {
        int value = num[i] - '0';
        if (digitCount[i] != value)
        {
            return false;
        }
    }
    return true;
}
```

#### Explanation:
1. Create an integer array `digitCount` of size 10 to store the count of each digit (0-9).
2. Traverse the string `num` and update the count of each digit in the `digitCount` array.
3. Iterate through each index of the string:
   - Convert the character at index `i` to an integer (`value`), which represents the expected count of digit `i`.
   - Compare `digitCount[i]` (the actual count of digit `i`) with `value`.
4. If any mismatch is found, return `false`. Otherwise, return `true`.

#### Complexity Analysis:
- **Time Complexity:** O(n), where `n` is the length of the string. The first loop calculates digit counts in O(n), and the second loop verifies the condition in O(n).
- **Space Complexity:** O(1), as only a fixed-size array is used.

---

## Summary
Both approaches solve the problem effectively, but their performance differs:
- **Approach 1** is simpler to implement but inefficient for longer strings due to repeated counting operations.
- **Approach 2** is optimized for performance by precomputing counts, making it suitable for larger inputs.


