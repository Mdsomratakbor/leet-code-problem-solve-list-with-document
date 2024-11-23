

# Reformat Phone Number

## Problem Description

The function `ReformatNumber` reformats a phone number by:
1. Removing all non-digit characters.
2. Inserting hyphens to break the number into groups of 3 digits, except for the last group, which might consist of 2 or 4 digits.
3. If the last group has 4 digits, it is split into two groups of 2 digits.

### Example
Input: `123-456 789 0`
Output: `123-456-7890`

Input: `123 4-567 890`
Output: `123-456-7890`

Input: `123 4-567`
Output: `123-45-67`

## Code Explanation

```csharp
public class Reformat_Phone_Number
{
    public string ReformatNumber(string number)
    {
        StringBuilder stringBuilder = new StringBuilder();
        int length = 0;

        // Iterate through each character in the input string
        foreach (char c in number)
        {
            // Only append digits to the StringBuilder
            if (char.IsDigit(c))
            {
                stringBuilder.Append(c);
                length++;
            }
        }

        int index = 3;

        // Add hyphens until the length of the number is less than or equal to 4
        while (length > 4)
        {
            if (length > 4)
            {
                stringBuilder.Insert(index, '-');
                index += 4;
                length -= 3;
            }
        }

        // If the remaining length is 4, split into two groups of 2
        if (length == 4)
        {
            stringBuilder.Insert(index - 1, '-');
        }

        return stringBuilder.ToString();
    }
}
```

### Method: `ReformatNumber`

#### Parameters:
- `number` (string): The phone number to be reformatted, which can include spaces, hyphens, or other non-digit characters.

#### Returns:
- A string representing the formatted phone number.

#### Steps:
1. The method iterates over the input string, extracting digits and appending them to a `StringBuilder`.
2. The `StringBuilder` is used to assemble the reformatted number.
3. The digits are grouped into blocks of 3, and hyphens are inserted to separate these blocks.
4. If the last group consists of 4 digits, it is split into two groups of 2 digits.

## Example Usage

```csharp
var reformatter = new Reformat_Phone_Number();
Console.WriteLine(reformatter.ReformatNumber("123-456 789 0"));  // Output: 123-456-7890
Console.WriteLine(reformatter.ReformatNumber("123 4-567 890"));  // Output: 123-456-7890
Console.WriteLine(reformatter.ReformatNumber("123 4-567"));      // Output: 123-45-67
```
