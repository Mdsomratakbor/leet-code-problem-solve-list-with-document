
# Maximum Score After Splitting a String

### Problem Statement
Given a binary string `s`, the task is to split the string into two non-empty substrings such that the sum of the number of zeros in the left substring and the number of ones in the right substring is maximized. Return the maximum possible score.

### Example:
**Input:**  
```
s = "011101"
```
**Output:**  
```
5
```
**Explanation:**  
Split the string as "011" and "101".  
- Left substring (`"011"`) contains 2 zeros.  
- Right substring (`"101"`) contains 3 ones.  
Total score = 2 (zeros) + 3 (ones) = 5.

---

### Implementation

#### Optimized Solution (`MaxScore` Method)
```csharp
public int MaxScore(string s)
{
    int result = 0, totalOneCount = s.Count(x => x == '1');
    int zeroCount = 0, oneCountLeft = 0, oneCountRight = 0;
    int left = 0, right = s.Length - 1;

    while (left < right)
    {
        if (s[left] == '0')
        {
            zeroCount++;
        }
        else
        {
            oneCountLeft++;
        }

        oneCountRight = totalOneCount - oneCountLeft;
        result = Math.Max(result, oneCountRight + zeroCount);
        left++;
    }
    
    return result;
}
```

**Explanation:**  
1. **Initialize Counters:** Start by counting the total number of ones (`totalOneCount`) in the input string.
2. **Traverse the String:** For each position `left`, count zeros on the left side (`zeroCount`) and update the number of ones on the left (`oneCountLeft`).
3. **Calculate the Right Ones:** Use `totalOneCount - oneCountLeft` to determine the number of ones on the right side.
4. **Calculate and Update Score:** Calculate the current score as the sum of left zeros and right ones, then update the result with the maximum score found so far.

**Time Complexity:** O(n)  
**Space Complexity:** O(1)  

---

#### Alternative Solution (`MaxScore_Old` Method)
```csharp
public int MaxScore_Old(string s)
{
    int left = 0, right = s.Length;
    int sum = 0, tempSum = 0;

    while (left < right)
    {
        string leftString = s.Substring(0, left + 1);
        string rightString = s.Substring(left + 1, right - left - 1);

        int oneCount = 0, zeroCount = 0;

        if (rightString.Length > 0 && leftString.Length > 0)
        {
            oneCount = rightString.Count(x => x == '1');
            zeroCount = leftString.Count(x => x == '0');
        }
        tempSum = oneCount + zeroCount;

        sum = Math.Max(sum, tempSum);
        left++;
    }
    return sum;
}
```

**Explanation:**  
- **Brute Force Approach:** For each split point `left`, create two substrings and count zeros and ones in each substring.
- **Evaluate All Splits:** Calculate the score for each split and track the maximum score.

**Time Complexity:** O(n²)  
**Space Complexity:** O(n²)  

---

### How to Use
1. Clone this repository or add this file to your project.
2. Instantiate the class and call the `MaxScore` method:

```csharp
using LeetCodeProblems;

var solver = new Maximum_Score_After_Splitting_a_String();
int result = solver.MaxScore("011101");
Console.WriteLine($"Maximum Score: {result}");
```
