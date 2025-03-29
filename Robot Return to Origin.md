# Robot Return to Origin

## Problem Statement
The problem requires determining whether a robot, starting at the origin `(0,0)`, returns to the origin after executing a sequence of moves. The robot can move in four directions:
- `'U'` (up) → increases vertical position
- `'D'` (down) → decreases vertical position
- `'L'` (left) → decreases horizontal position
- `'R'` (right) → increases horizontal position

If the robot's final position is `(0,0)`, return `true`; otherwise, return `false`.

---

## Approach
The approach involves maintaining two counters:
- `vertical` to track up and down movements (`U` increases, `D` decreases)
- `horizontal` to track left and right movements (`L` decreases, `R` increases)

By iterating over the moves, the counters update accordingly. If both `vertical` and `horizontal` are `0` at the end, the robot returns to the origin.

---

## Code Implementation (C#)

```csharp
using System;

namespace LeetCodeProblems
{
    public class Robot_Return_to_Origin
    {
        public bool JudgeCircle(string moves) {
            int vertical = 0, horizontal = 0;

            foreach (char move in moves) {
                switch(move) {
                    case 'U': vertical++; break;
                    case 'D': vertical--; break;
                    case 'L': horizontal--; break;
                    case 'R': horizontal++; break;
                }
            }

            return vertical == 0 && horizontal == 0;
        }
    }
}
```

---

## Complexity Analysis
- **Time Complexity:** `O(N)`, where `N` is the length of the `moves` string (each move is processed once).
- **Space Complexity:** `O(1)`, since only two integer variables are used.

---

## Example Test Cases
```csharp
Console.WriteLine(JudgeCircle("UD")); // true
Console.WriteLine(JudgeCircle("LL")); // false
Console.WriteLine(JudgeCircle("LRUD")); // true
Console.WriteLine(JudgeCircle("LDRR")); // false
Console.WriteLine(JudgeCircle(""); // true (empty moves mean the robot stays at the origin)
```

---

## Edge Cases Considered
- Empty string (`""`) → returns `true`
- Moves with only one direction (e.g., `"UUU"`) → returns `false`
- Moves with equal opposing pairs (e.g., `"LRUD"`) → returns `true`
- Large input cases with long move sequences



