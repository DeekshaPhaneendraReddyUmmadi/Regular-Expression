# Groups and Capturing

**Definition:**  
*Groups and capturing in regex allow you to create sub-patterns within a regular expression. This enables you to apply quantifiers to part of a pattern, as well as extract specific portions of a match for further use.*

## Basic Syntax for Groups and Capturing

### Grouping with Parentheses
You can create a group by enclosing a part of the regex in parentheses `()`. This allows you to treat multiple characters as a single unit. For example:
- **Regex:** `(abc)`  
- **Matches:** `abc` in the string "abc def".

### Capturing Groups
When you use parentheses, the matched content can be captured and referenced later. Each group is assigned a number based on the order of the opening parentheses. For example:
- **Regex:** `(cat)(s)?`  
- **Matches:** `cat` and `cats` in the strings "cat" and "cats", respectively. The second group captures the optional `s`.

### Non-Capturing Groups
If you want to group without capturing, you can use `(?:...)`. This is useful when you need to apply quantifiers but do not need to extract the matched content. For example:
- **Regex:** `(?:abc)+`  
- **Matches:** `abcabc` in the string "abcabc".

### Backreferences
You can refer to a previously captured group using a backreference. This is done by using a backslash followed by the group number. For example:
- **Regex:** `(a)(b)\1`  
- **Matches:** `aba` in the string "aba" because `\1` refers to the first captured group `a`.

## Examples

- **Basic Grouping:**  
  - **Regex:** `(dog)`  
  - **Matches:** `dog` in the string "The dog barks."

- **Capturing Groups:**  
  - **Regex:** `(hello) (world)`  
  - **Matches:** `hello world` in the string "hello world". Captures `hello` as group 1 and `world` as group 2.

- **Non-Capturing Group:**  
  - **Regex:** `(?:abc)+`  
  - **Matches:** `abcabc` in the string "abcabc" but does not capture the groups.

- **Backreference:**  
  - **Regex:** `(x)(y)\1`  
  - **Matches:** `xyx` in the string "xyx" because `\1` refers to the first captured group `x`.

## Java Example Code

```java
    // Import the necessary classes for pattern matching
    import java.util.regex.Pattern;
    import java.util.regex.Matcher;

    public class GroupsAndCapturingComponent {
        public static void main(String[] args) {
            // Compile a regular expression pattern with capturing groups
            String regex = "(hello) (world)";
            Pattern p = Pattern.compile(regex);

            // Create a matcher that will search through the given string
            String searchString = "hello world!";
            Matcher m = p.matcher(searchString);

            // Use a while loop to find all occurrences of the pattern in the string
            while (m.find()) {
                // Print the matched groups to the console with index
                System.out.println("Matched: " + m.group(0)); // Full match
                System.out.println("Group 1: " + m.group(1)); // First group
                System.out.println("Group 2: " + m.group(2)); // Second group
            }
        }
    }
```

**OUTPUT**
```
Matched: hello world
Group 1: hello
Group 2: world
```

## Summary of Groups and Capturing
- **Grouping with Parentheses:** Enclose part of the regex in `()` to create a group.  
- **Capturing Groups:** Captured content can be referenced later using group numbers.  
- **Non-Capturing Groups:** Use `(?:...)` to group without capturing.  
- **Backreferences:** Use `\n` to refer to the nth captured group.

Groups and capturing are essential for managing complex patterns and extracting specific data from matches in a string.

### Practical Use Cases for Groups and Capturing

1. **Extracting Substrings:**
   - Capturing groups are often used to extract specific parts of a string. For example, if you want to extract the area code and the phone number from a string:
     - **Regex:** `(\d{3})-(\d{3})-(\d{4})`
     - This regex captures the area code, the first three digits, and the last four digits of a phone number in separate groups.

2. **Reformatting Strings:**
   - You can use capturing groups to reformat strings. For instance, if you want to change the format of a date from `MM-DD-YYYY` to `YYYY-MM-DD`:
     - **Regex:** `(\d{2})-(\d{2})-(\d{4})`
     - Replacement string: `$3-$1-$2`
     - This captures the month, day, and year, allowing you to rearrange them in the desired format.

3. **Conditional Matching:**
   - Groups can be used to apply quantifiers to specific parts of a pattern. For example, matching a word that may or may not have a suffix:
     - **Regex:** `(test)(ing)?`
     - This regex matches both `test` and `testing`, capturing the base word and the optional suffix.

4. **Backreferencing:**
   - Capturing groups allow for backreferencing, which can be useful in matching repeated patterns. For example, to find repeated words:
     - **Regex:** `\b(\w+)\s+\1\b`
     - This regex matches any word that is immediately followed by the same word, capturing the repeated word in a group.

5. **Validating Input Formats:**
   - Groups can help validate complex input formats, such as email addresses. For example:
     - **Regex:** `([a-zA-Z0-9._%+-]+)@([a-zA-Z0-9.-]+)\.([a-zA-Z]{2,})`
     - This regex captures the username, domain, and top-level domain of an email address in separate groups.

### Limitations

- **Complexity:** Using multiple groups can make regex patterns complex and harder to read, especially for those unfamiliar with regex syntax.
- **Performance:** Capturing groups can lead to performance issues in large texts or complex patterns, as they require additional memory to store the captured content.
- **Overhead:** If you only need to group parts of a pattern without capturing them, using non-capturing groups can be more efficient.

### Conclusion

Groups and capturing are fundamental features of regular expressions that enhance their power and flexibility. They allow you to extract, manipulate, and validate specific parts of strings, making them essential for a wide range of applications in text processing.

By mastering groups and capturing, you can create more sophisticated regex patterns that cater to various needs, from data extraction to input validation. Understanding how to effectively use these features can significantly improve your regex skills and enable you to tackle more complex text manipulation tasks with confidence.