# Character Classes

**Definition:**  
*A character class is a set of characters enclosed in square brackets `[]` that defines a group of characters to match. When you use a character class in a regex pattern, it will match any single character that is included in the class.*

## Basic Syntax

- **Single Characters:**  
  `[abc]` matches any one of the characters `a`, `b`, or `c`.

- **Range of Characters:**  
  `[a-z]` matches any lowercase letter from `a` to `z`. You can also combine ranges, like `[a-zA-Z]`, to match any letter, regardless of case.

- **Negation:**  
  If you want to match any character except those in the class, you can use the caret `^` at the beginning:  
  `[^abc]` matches any character except `a`, `b`, or `c`.

## Examples

- **Matching Digits:**  
  `[0-9]` matches any digit from `0` to `9`.

- **Matching Letters:**  
  `[A-Za-z]` matches any uppercase or lowercase letter.

- **Matching Special Characters:**  
  `[!@#$%^&*()]` matches any of the specified special characters.

- **Combining Classes:**  
  `[a-zA-Z0-9]` matches any alphanumeric character.


## Java Example Code

```java
    // Import the necessary classes for pattern matching
    import java.util.regex.Pattern;
    import java.util.regex.Matcher;

    public class RegexExample {
        public static void main(String[] args) {
            // Sample input strings
            String[] testStrings = {
                "Hello123",   // Valid
                "Hello 123",  // Invalid (contains space)
                "Hello@123",  // Invalid (contains special character)
                "12345",      // Valid
                "HelloWorld"  // Valid
            };

            // Regular expression pattern to match only alphanumeric characters
            String regex = "[A-Za-z0-9]+";

            // Compile the regex pattern
            Pattern pattern = Pattern.compile(regex);

            // Test each string against the regex pattern
            for (String testString : testStrings) {
                Matcher matcher = pattern.matcher(testString);
                if (matcher.matches()) {
                    System.out.println(testString + " is valid.");
                } else {
                    System.out.println(testString + " is invalid.");
                }
            }
        }
    }

```

**OUTPUT**
```
Hello123 is valid.
Hello 123 is invalid.
Hello@123 is invalid.
12345 is valid.
HelloWorld is valid.
```

## Summary of Character Classes
- **Basic Character Class:** Use [] to define a set of characters to match any one of them.
- **Range of Characters:** Use a hyphen (-) inside brackets to specify a range (e.g., [a-z]).
- **Negated Character Class:** Use [^] to match any character not in the specified set.

Character classes provide flexibility in matching multiple characters, allowing for concise and powerful pattern definitions.

### Practical Use Cases for Character Classes

1. **Defining Sets of Characters:**
   - Character classes allow you to define a set of characters to match. For example, if you want to match any vowel (a, e, i, o, u):
     - **Regex:** `[aeiou]`  
     - This regex matches any single vowel character in the input string, making it useful for vowel extraction or filtering.

2. **Matching Digits:**
   - You can use character classes to match any digit from 0 to 9. For example:
     - **Regex:** `[0-9]`  
     - This regex matches any single digit, which is useful for validating numeric input or extracting numbers from text.

3. **Matching Alphanumeric Characters:**
   - To match any alphanumeric character (letters and digits), you can use:
     - **Regex:** `[a-zA-Z0-9]`  
     - This regex matches any single letter (uppercase or lowercase) or digit, making it useful for validating usernames or passwords.

4. **Negating Character Classes:**
   - You can create a negated character class to match any character that is not in a specified set. For example, to match any character that is not a digit:
     - **Regex:** `[^0-9]`  
     - This regex matches any non-digit character, which can be useful for filtering out numeric values.

5. **Matching Whitespace Characters:**
   - You can define a character class to match whitespace characters. For example, to match spaces, tabs, and newlines:
     - **Regex:** `[ \t\n]`  
     - This regex matches any whitespace character, which is useful for processing text where spacing is variable.

6. **Combining Character Classes:**
   - You can combine multiple character classes to create more complex patterns. For example, to match any letter or digit:
     - **Regex:** `[a-zA-Z0-9]`  
     - This regex matches any single alphanumeric character, allowing for flexible matching of various input types.

### Limitations

- **Complexity:** While character classes simplify matching multiple characters, they can become complex when combining multiple sets or using negation, making regex patterns harder to read.
- **Overlapping Classes:** Care must be taken to avoid unintended matches when defining character classes, especially when using ranges or combining classes.
- **Performance:** Although character classes are generally efficient, overly complex patterns with many character classes may lead to performance issues in large texts.

### Conclusion

Character classes are powerful features of regular expressions that allow you to define sets of characters to match. They are essential for a wide range of applications, from validating input formats to extracting specific data from text.

By mastering the use of character classes, you can create more flexible and sophisticated regex patterns that cater to various needs, such as data extraction, validation, and pattern matching. Understanding how to effectively use character classes will significantly enhance your regex skills and enable you to tackle complex text processing tasks with confidence.