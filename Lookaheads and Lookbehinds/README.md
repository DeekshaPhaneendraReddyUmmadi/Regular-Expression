# Lookaheads and Lookbehinds

**Definition:**  
*Lookaheads and lookbehinds are zero-width assertions in regex that allow you to match a pattern only if it is followed or preceded by another pattern, without including that other pattern in the match itself.*

## Basic Syntax for Lookaheads and Lookbehinds

### Lookaheads
A lookahead assertion checks for a pattern that follows the current position in the string. It is denoted by `(?=...)`. For example:
- **Regex:** `\d(?= dollars)`  
- **Matches:** `5` in the string "5 dollars" because `5` is followed by `dollars`.

### Negative Lookaheads
A negative lookahead assertion checks that a pattern does not follow the current position. It is denoted by `(?!...)`. For example:
- **Regex:** `\d(?! dollars)`  
- **Matches:** `5` in the string "5 apples" but not in "5 dollars" because `5` is not followed by `dollars`.

### Lookbehinds
A lookbehind assertion checks for a pattern that precedes the current position in the string. It is denoted by `(?<=...)`. For example:
- **Regex:** `(?<=\$)\d+`  
- **Matches:** `5` in the string "$5" because `5` is preceded by `$`.

### Negative Lookbehinds
A negative lookbehind assertion checks that a pattern does not precede the current position. It is denoted by `(?<!...)`. For example:
- **Regex:** `(?<!\$)\d+`  
- **Matches:** `5` in the string "5 apples" but not in "$5" because `5` is not preceded by `$`.

## Examples

- **Lookahead:**  
  - **Regex:** `\w+(?=!)`  
  - **Matches:** `Hello` in the string "Hello!" because `Hello` is followed by `!`.

- **Negative Lookahead:**  
  - **Regex:** `\w+(?!!)`  
  - **Matches:** `Hello` in the string "Hello there" but not in "Hello!" because `Hello` is not followed by `!`.

- **Lookbehind:**  
  - **Regex:** `(?<=@)\w+`  
  - **Matches:** `example` in the string "email@example.com" because `example` is preceded by `@`.

- **Negative Lookbehind:**  
  - **Regex:** `(?<!@)\w+`  
  - **Matches:** `example` in the string "example.com" but not in "email@example.com" because `example` is preceded by `@`.

## Java Example Code

```java
    // Import the necessary classes for pattern matching
    import java.util.regex.Pattern;
    import java.util.regex.Matcher;

    public class LookaheadsAndLookbehindsComponent {
        public static void main(String[] args) {
            // Compile a regular expression pattern with lookaheads
            String regexLookahead = "\\d(?= dollars)";
            Pattern pLookahead = Pattern.compile(regexLookahead);

            // Create a matcher that will search through the given string
            String searchStringLookahead = "5 dollars";
            Matcher mLookahead = pLookahead.matcher(searchStringLookahead);

            // Use a while loop to find all occurrences of the pattern in the string
            while (mLookahead.find()) {
                // Print the matched lookahead to the console
                System.out.println("Lookahead Match: " + mLookahead.group());
            }

            // Compile a regular expression pattern with lookbehinds
            String regexLookbehind = "(?<=\\$)\\d+";
            Pattern pLookbehind = Pattern.compile(regexLookbehind);

            // Create a matcher that will search through the given string
            String searchStringLookbehind = "$5";
            Matcher mLookbehind = pLookbehind.matcher(searchStringLookbehind);

            // Use a while loop to find all occurrences of the pattern in the string
            while (mLookbehind.find()) {
                // Print the matched lookbehind to the console
                System.out.println("Lookbehind Match: " + mLookbehind.group());
            }
        }
    }
```

**OUTPUT**
```
Lookahead Match: 5
Lookbehind Match: 5
```

## Summary of Lookaheads and Lookbehinds
- **Lookaheads:** Use `(?=...)` to assert that a pattern follows the current position.  
- **Negative Lookaheads:** Use `(?!...)` to assert that a pattern does not follow the current position.  
- **Lookbehinds:** Use `(?<=...)` to assert that a pattern precedes the current position.  
- **Negative Lookbehinds:** Use `(?<!...)` to assert that a pattern does not precede the current position.

Lookaheads and lookbehinds are powerful tools in regex that allow for more complex pattern matching without consuming characters in the input string. They enable you to create conditions for matches based on surrounding context, which can be particularly useful in various text processing tasks.

### Practical Use Cases

1. **Validation of Input Formats:**
   - Lookaheads can be used to ensure that certain characters or patterns follow a specific input. For example, validating that a password contains at least one digit:
     - **Regex:** `(?=.*\d).{8,}`  
     - This regex checks that the string is at least 8 characters long and contains at least one digit.

2. **Extracting Information:**
   - Lookbehinds can be used to extract information that is preceded by a specific character or string. For example, extracting prices from a string:
     - **Regex:** `(?<=\$)\d+`  
     - This regex captures the numeric value that follows a dollar sign.

3. **Conditional Matching:**
   - You can use negative lookaheads to exclude certain patterns from matches. For example, matching words that are not followed by an exclamation mark:
     - **Regex:** `\w+(?!!)`  
     - This regex matches words that are not immediately followed by `!`.

4. **Complex String Manipulation:**
   - Combining lookaheads and lookbehinds can help in complex string manipulations, such as finding specific patterns in a text while ignoring certain contexts.

### Limitations

- **Performance:** Lookaheads and lookbehinds can sometimes lead to performance issues, especially in large texts or complex patterns, as they require additional checks.
- **Zero-width Assertions:** Since lookaheads and lookbehinds do not consume characters, they can sometimes lead to confusion in understanding what is being matched, especially for those new to regex.

### Conclusion

Lookaheads and lookbehinds enhance the capabilities of regular expressions by allowing you to assert conditions about the surrounding context of matches. They are essential for advanced regex users who need to perform intricate pattern matching and text processing tasks. Understanding how to effectively use these assertions can significantly improve your regex skills and enable you to tackle more complex problems in text manipulation.

By mastering lookaheads and lookbehinds, you can create more robust and flexible regex patterns that cater to a wide range of applications, from data validation to information extraction.