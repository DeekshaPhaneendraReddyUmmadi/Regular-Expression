# Literals

**Definition:**  <br>
    *A literal is any character that matches itself. For example, the regex cat will match the string "cat" exactly.*

**Examples:** <br>
    - The regex hello matches the string "hello". <br>
    - The regex 123 matches the string "123".

**Java Program**
``` Java
    // Import the necessary classes for pattern matching
    import java.util.regex.Pattern;
    import java.util.regex.Matcher;

    public class LiteralsComponent {
        public static void main(String[] args) {
            // Compile a regular expression pattern that matches itself.
            Pattern p = Pattern.compile("hello");

            // Create a matcher that will search through the given string
            Matcher m = p.matcher("hello world!");

            // Use a while loop to find all occurrences of the pattern in the string
            while (m.find()) {
                // Print the matched vowel to the console with index
                System.out.println("index " + m.start() + " : " + m.group());
            }
        }
    }
```
**OUTPUT**
``` 
hello
```