# 🚀 DI String Match Solution in C#

## 📚 Problem Description

Given a string `s` of length `n` consisting only of the characters 'I' (for increasing) and 'D' (for decreasing), the task is to return a permutation of integers `[0, 1, ..., n]` such that:

- If `s[i] == 'I'`, then `arr[i] < arr[i + 1]`
- If `s[i] == 'D'`, then `arr[i] > arr[i + 1]`

### Example:

Input: `"IDID"`  
Output: `[0, 4, 1, 3, 2]`

---

## 💻 Code Implementation

```csharp
using System;

namespace LeetCodeProblems
{
    internal class DI_String_Match
    {
        public int[] DiStringMatch(string s)
        {
            int left = 0, right = s.Length;
            int[] outputArray = new int[right + 1];
            int i = 0;
            
            while (i < s.Length)
            {
                if (s[i] == 'I')
                {
                    outputArray[i] = left;
                    left++;
                }
                else if (s[i] == 'D')
                {
                    outputArray[i] = right;
                    right--;
                }
                i++;
            }
            outputArray[i] = left;
            return outputArray;
        }
    }
}
```

---

## 🛠️ How It Works:

1. **Initialization:**
   - Two pointers (`left` and `right`) are initialized: `left = 0` and `right = s.Length`.
   - An array `outputArray` of size `n+1` is created.

2. **Iteration:**
   - The code loops through each character in the input string:
     - If the character is `'I'`, the current element is set to the value of `left`, and `left` is incremented.
     - If the character is `'D'`, the current element is set to the value of `right`, and `right` is decremented.

3. **Final Step:**
   - After the loop, the last element of the array is assigned the remaining value (`left` or `right`).

---

## 📊 Complexity:

- **Time Complexity:** O(n) — The algorithm processes each character of the string once.
- **Space Complexity:** O(n) — An array of size `n + 1` is used.

---

## 🧪 Example Test Cases:

```csharp
public static void Main(string[] args)
{
    DI_String_Match solver = new DI_String_Match();
    
    int[] result1 = solver.DiStringMatch("IDID");
    Console.WriteLine(string.Join(", ", result1)); // Output: 0, 4, 1, 3, 2
    
    int[] result2 = solver.DiStringMatch("III");
    Console.WriteLine(string.Join(", ", result2)); // Output: 0, 1, 2, 3
    
    int[] result3 = solver.DiStringMatch("DDI");
    Console.WriteLine(string.Join(", ", result3)); // Output: 3, 2, 0, 1
}
```

---

## 📝 Notes:

- This solution leverages a greedy approach with two pointers to efficiently build the resulting array.
- The method ensures that all conditions for 'I' and 'D' are satisfied without backtracking.

