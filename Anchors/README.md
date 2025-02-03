# Anchors

**Definition:**  
*Anchors are special characters in regular expressions that assert the position of a match within a string. They do not match any characters themselves but specify where a match can occur.*

## Basic Syntax for Anchors

### Caret (`^`)
Asserts the position at the start of a string.  
- **Example:** The regex `^Hello` matches `Hello` in the string "Hello world" but does not match in "Say Hello".

### Dollar Sign (`$`)
Asserts the position at the end of a string.  
- **Example:** The regex `world$` matches `world` in the string "Hello world" but does not match in "worldwide".

### Word Boundary (`\b`)
Asserts a position where a word character (alphanumeric or underscore) is next to a non-word character.  
- **Example:** The regex `\bword\b` matches `word` in the string "The word is here" but does not match in "sword".

### Non-word Boundary (`\B`)
Asserts a position where a word character is next to another word character.  
- **Example:** The regex `\Bend` matches `bend` in the string "bend" but does not match in "end".

## Examples

- **Matching Start of String:**  
  - **Regex:** `^Hello`  
  - **Matches:** `Hello` in the string "Hello world".

- **Matching End of String:**  
  - **Regex:** `world$`  
  - **Matches:** `world` in the string "Hello world".

- **Matching Word Boundary:**  
  - **Regex:** `\bcat\b`  
  - **Matches:** `cat` in the string "The cat sat on the mat." but not in "scat".

- **Matching Non-word Boundary:**  
  - **Regex:** `\Bend`  
  - **Matches:** `bend` in the string "bend" but not in "end".

## Java Example Code

```java
  // Import the necessary classes for pattern matching
  import java.util.regex.Pattern;
  import java.util.regex.Matcher;

  public class AnchorsComponent {
      public static void main(String[] args) {
          // Compile a regular expression pattern using anchors
          String regex = "^Hello";
          Pattern p = Pattern.compile(regex);

          // Create a matcher that will search through the given string
          String searchString = "Hello world";
          Matcher m = p.matcher(searchString);

          // Use a while loop to find all occurrences of the pattern in the string
          while (m.find()) {
              // Print the matched anchor pattern to the console with index
              System.out.println("index " + m.start() + " : " + m.group());
          }
      }
  }
```

**OUTPUT**
```
index 0 : Hello
```

## Summary of Anchors
- **Start of String:** Use ^ to assert the position at the start of a string.
- **End of String:** Use $ to assert the position at the end of a string.
- **Word Boundary:** Use \b to assert a position where a word character is next to a non-word character.
- **Non-word Boundary:** Use \B to assert a position where a word character is next to another word character.

Anchors are crucial for defining the position of matches within a string, ensuring that patterns are matched at specific locations.

### Practical Use Cases for Anchors

1. **Matching the Start of a String:**
   - The caret `^` anchor is used to assert that a match must occur at the beginning of a string. For example, if you want to match a string that starts with "Hello":
     - **Regex:** `^Hello`  
     - This regex matches "Hello" only if it appears at the start of the string, making it useful for validating input formats or ensuring specific prefixes.

2. **Matching the End of a String:**
   - The dollar sign `$` anchor asserts that a match must occur at the end of a string. For example, to match a string that ends with "world":
     - **Regex:** `world$`  
     - This regex matches "world" only if it appears at the end of the string, which is useful for validating file extensions or ensuring specific suffixes.

3. **Combining Anchors for Full String Matches:**
   - You can combine both anchors to ensure that a string matches exactly. For example, to match the exact string "Hello, world!":
     - **Regex:** `^Hello, world!$`  
     - This regex matches the entire string, ensuring that it starts and ends with the specified text.

4. **Multiline Matching:**
   - When using the `m` flag (multiline mode), the `^` and `$` anchors can match the start and end of each line within a multiline string. For example, to match lines that start with "Error":
     - **Regex:** `^Error` (with the `m` flag)  
     - This regex matches "Error" at the beginning of any line in a multiline string, making it useful for log file analysis.

5. **Validating Input Formats:**
   - Anchors are often used in input validation to ensure that data conforms to specific formats. For example, to validate a US phone number format:
     - **Regex:** `^\(\d{3}\) \d{3}-\d{4}$`  
     - This regex matches a phone number in the format (123) 456-7890, ensuring that it starts and ends with the correct structure.

6. **Preventing Partial Matches:**
   - Anchors help prevent partial matches in strings. For example, to ensure that the word "cat" is matched as a whole word:
     - **Regex:** `\bcat\b`  
     - This regex uses word boundaries (`\b`) to ensure that "cat" is matched only when it appears as a complete word, not as part of another word like "catalog".

### Limitations

- **Context Sensitivity:** Anchors are context-sensitive, meaning they only work based on the position of the match in the string. This can lead to unexpected results if not carefully managed.
- **Multiline Complexity:** When using multiline mode, the behavior of anchors can change, which may confuse users who are not familiar with how anchors work in this context.
- **Performance:** While anchors themselves do not typically cause performance issues, complex patterns that rely heavily on anchors may lead to slower regex processing times.

### Conclusion

Anchors are essential components of regular expressions that allow you to assert the position of a match within a string. They are crucial for tasks such as validating input formats, ensuring exact matches, and preventing partial matches.

By mastering the use of anchors, you can create more precise and effective regex patterns that cater to various needs, from data validation to text processing. Understanding how to effectively use anchors will significantly enhance your regex skills and enable you to tackle complex text manipulation tasks with confidence.