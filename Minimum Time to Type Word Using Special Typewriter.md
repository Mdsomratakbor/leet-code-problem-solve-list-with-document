# Minimum Time to Type Word Using Special Typewriter

---

## Problem Description
A special typewriter has a circular keyboard with lowercase English letters arranged in alphabetical order (`'a'` to `'z'`). It starts at `'a'` and rotates both clockwise and counterclockwise.

Given a string `word`, the goal is to determine the minimum time required to type the word. The typewriter rotates to each letter, and typing a letter takes 1 second.

### Example:
- **Input:** `"abc"`
- **Output:** `5`  
  **Explanation:**  
  Start at `'a'`:  
  - Move to `'a'` (already there): 1 second  
  - Move to `'b'`: 1 step (clockwise) + 1 second to type = 2 seconds  
  - Move to `'c'`: 1 step (clockwise) + 1 second to type = 2 seconds  
  Total = 5 seconds

---

## Implementation

### Function Details:
- **Method:** `MinTimeToType`
- **Parameters:**  
  - `word` (string): The word to be typed.
- **Returns:**  
  - `int`: The minimum time to type the given word.

### Code:
```csharp
using System;

namespace LeetCodeProblems
{
    internal class Minimum_Time_to_Type_Word_Using_Special_Typewriter
    {
        public int MinTimeToType(string word)
        {
            int time = 0;
            char current = 'a';  // Start at 'a'

            foreach (char c in word)
            {
                int distance = Math.Abs(c - current);  // Calculate the distance between current and target
                int minValue = Math.Min(distance, 26 - distance);  // Choose the shorter path (clockwise or counterclockwise)
                time += minValue + 1;  // Add 1 second for typing
                current = c;  // Update the current character
            }
            return time;
        }
    }
}
```

---

## Explanation:
1. **Initialize Variables:**
   - `time`: Keeps track of the total time.
   - `current`: Tracks the current character position (starting at `'a'`).

2. **Loop through the Word:**
   - For each character, calculate the **distance** from the current position.
   - Choose the shorter path: clockwise or counterclockwise.
   - Add the time for moving and typing the character (1 second for moving, 1 second for typing).

3. **Update Position:**
   - After typing, update the `current` position to the newly typed character.

---

## Complexity Analysis:
- **Time Complexity:** `O(n)` where `n` is the length of the word.
- **Space Complexity:** `O(1)` (constant space usage).

---

## Test Cases:
| Input | Output |
|-------|--------|
| `"abc"` | `5` |
| `"bza"` | `7` |
| `"zjpc"` | `34` |
| `"a"` | `1` |

---

## Contribution:
Feel free to contribute additional test cases, optimizations, or enhancements to this solution. Fork and create a pull request if you have improvements or suggestions!

---
