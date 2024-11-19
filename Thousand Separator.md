# Thousand Separator 

A simple C# utility to format integers with a period (`.`) as the thousand separator. This utility can be useful in scenarios where you need to display large numbers in a human-readable format.

---

## Class: `Thousand_Separator`

This class provides a method to add thousand separators to an integer.

### Method: `ThousandSeparator`

**Purpose**:  
Formats a given integer by inserting a period (`.`) as a thousand separator.

---

### Code Example

```csharp
public class Thousand_Separator
{
    /// <summary>
    /// Formats an integer with thousand separators.
    /// </summary>
    /// <param name="n">The integer to be formatted.</param>
    /// <returns>A string representing the formatted integer.</returns>
    public string ThousandSeparator(int n)
    {
        // Convert the number to a string and prepare for modification.
        StringBuilder result = new StringBuilder(n.ToString());

        // Start from the third-to-last character and move backwards, inserting '.' every three characters.
        for (int i = result.Length - 3; i > 0; i -= 3)
        {
            result.Insert(i, ".");
        }

        return result.ToString();
    }
}
```

---

### Parameters

- **`int n`**  
  The integer to be formatted.

---

### Returns

- **`string`**  
  A string representation of the integer with thousand separators.

---

### Example Usage

```csharp
class Program
{
    static void Main(string[] args)
    {
        Thousand_Separator separator = new Thousand_Separator();

        int number = 1234567890;

        string formatted = separator.ThousandSeparator(number);

        Console.WriteLine(formatted);
        // Output: "1.234.567.890"
    }
}
```

---

### How It Works

1. Converts the integer to a string.
2. Uses a loop to traverse the string from the right, starting at the third-to-last character.
3. Inserts a period (`.`) at every third character position moving leftward.
4. Returns the formatted string.

---
