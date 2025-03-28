# Rings and Rods Problem

## Problem Statement
You have `n` rods labeled from `0` to `9`. Rings are placed onto these rods using a string representation, where each pair of characters represents a ring and its corresponding rod.

- The first character in the pair is the ring's color (`R`, `G`, or `B`).
- The second character in the pair is the rod number (`0`-`9`).

Your goal is to determine how many rods have all three ring colors (`R`, `G`, and `B`).

## Solution Explanation
The solution uses a **dictionary** to track ring colors on each rod:
1. Iterate through the `rings` string in steps of `2` to extract each ring's color and its corresponding rod.
2. Use a **HashSet** to store the unique colors for each rod.
3. After processing all rings, count the rods that contain all three colors.

## Code Implementation
```csharp
using System;
using System.Collections.Generic;

namespace LeetCodeProblems {
    public class Rings_And_Rods {
        public int CountPoints(string rings) {
            Dictionary<int, HashSet<char>> keyValuePairs = new Dictionary<int, HashSet<char>>();

            for (int i = 0; i < rings.Length; i += 2) {
                char color = rings[i];
                int rod = rings[i + 1] - '0';

                if (!keyValuePairs.ContainsKey(rod)) {
                    keyValuePairs[rod] = new HashSet<char>();
                }
                keyValuePairs[rod].Add(color);
            }

            int count = 0;
            foreach (var rod in keyValuePairs.Values) {
                if (rod.Contains('R') && rod.Contains('G') && rod.Contains('B')) {
                    count++;
                }
            }

            return count;
        }
    }
}
```

## Complexity Analysis
- **Time Complexity**: `O(n)`, where `n` is the length of `rings`. We iterate over the string once and perform `O(1)` operations for each character pair.
- **Space Complexity**: `O(1)`, since at most 10 rods are stored in the dictionary.

## Example Usage
```csharp
Rings_And_Rods solution = new Rings_And_Rods();
Console.WriteLine(solution.CountPoints("B0R0G0R1G1B1")); // Output: 2
```

## Edge Cases Considered
- **No complete sets**: e.g., `"R0G0B1"` should return `0`.
- **Single rod with all colors**: e.g., `"R0G0B0"` should return `1`.
- **Duplicate rings on a rod**: e.g., `"R0R0G0B0"` should not affect the result.
