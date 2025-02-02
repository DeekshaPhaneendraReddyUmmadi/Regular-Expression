# Regular Expression using java

Basic understanding how to use java for the regular expression.

*The java.util.regex package in Java provides classes for working with regular expressions. The two primary classes you'll be working with are `Pattern` and `Matcher`.*

## The Pattern Class

The `Pattern` class is a compiled representation of a regular expression. It provides various methods to create and manipulate regex patterns.

### Key Methods of the Pattern Class

- **static Pattern compile(String regex)**: Compiles the given regular expression into a pattern.
- **static Pattern compile(String regex, int flags)**: Compiles the given regular expression with the specified flags (e.g., `Pattern.CASE_INSENSITIVE`).
- **Matcher matcher(CharSequence input)**: Creates a matcher that can be used to perform matching operations on the given input sequence.
- **String pattern()**: Returns the string representation of the pattern.
- **int flags()**: Returns the flags used to create this pattern.
- **boolean isGreedy()**: Returns whether this pattern is greedy.
- **String[] split(CharSequence input)**: Splits the input sequence around matches of this pattern.
- **String[] split(CharSequence input, int limit)**: Splits the input sequence around matches of this pattern, with a limit on the number of splits.

### Example of Using Pattern

```java
Pattern pattern = Pattern.compile("\\b\\w{4}\\b");
```

## The Matcher Class

The `Matcher` class is used to perform matching operations on a character sequence using a `Pattern`. It provides methods to find matches, extract matched groups, and perform replacements.

### Key Methods of the Matcher Class

- **boolean find()**: Attempts to find the next subsequence of the input sequence that matches the pattern.
- **boolean find(int start)**: Attempts to find the next subsequence of the input sequence that matches the pattern, starting at the specified index.
- **boolean matches()**: Attempts to match the entire input sequence against the pattern.
- **boolean lookingAt()**: Attempts to match the input sequence, starting at the beginning, against the pattern.
- **String group()**: Returns the input subsequence matched by the previous match operation.
- **String group(int group)**: Returns the input subsequence captured by the given group during the previous match operation.
- **int start()**: Returns the start index of the previous match.
- **int end()**: Returns the end index of the previous match.
- **int start(int group)**: Returns the start index of the specified group.
- **int end(int group)**: Returns the end index of the specified group.
- **String replaceAll(String replacement)**: Replaces every substring of the input sequence that matches the pattern with the given replacement string.
- **String replaceFirst(String replacement)**: Replaces the first substring of the input sequence that matches the pattern with the given replacement string.
- **void reset()**: Resets the matcher to the beginning of the input sequence.
- **void reset(CharSequence input)**: Resets the matcher with a new input sequence.

### Example of Using Matcher

```java
Matcher matcher = pattern.matcher("The quick brown fox jumps over the lazy dog.");
while (matcher.find()) {
    System.out.println("Found: " + matcher.group());
}
```


### Example of Using Pattern and Matcher

```java
    import java.util.regex.*;

    public class RegexExample {
        public static void main(String[] args) {
            String text = "The quick brown fox jumps over the lazy dog.";
            String patternString = "\\b\\w{4}\\b"; // Matches words with exactly 4 letters

            // Compile the pattern
            Pattern pattern = Pattern.compile(patternString);
            
            // Create a matcher for the input text
            Matcher matcher = pattern.matcher(text);

            // Find and print all matches
            while (matcher.find()) {
                System.out.println("Found: " + matcher.group());
            }
        }
    }

    OUTPUT:
        Found: over
        Found: lazy
```

### Example of Using Split Method

```java
    import java.util.regex.Pattern;

    public class UsingSplitMethod {
        public static void main(String[] args) {
            Pattern p = Pattern.compile("\\s");
            String[] m = p.split("using split method");
            for(String i: m){
                System.out.println(i);
            }
        }
    }

    OUTPUT:
        using
        split
        method
```

### Example of Using StringTokenizer

```java
    import java.util.StringTokenizer;

    public class UsingStringTokenizer {
        public static void main(String[] args) {
            StringTokenizer s = new StringTokenizer("using string tokenizer"); // default re/pattern is "space"
            while(s.hasMoreTokens()){
                System.out.println(s.nextToken());
            }

            StringTokenizer s1 = new StringTokenizer("29-01-2025","-"); // (target string , regex/pattern/delimiter)
            while(s1.hasMoreTokens()){
                System.out.println(s1.nextToken());
            }
        }
    }
    
    OUTPUT:
        using
        string
        tokenizer
        
        29
        01
        2025
```
### Example of Using external txt file (Phone number)

```java
    import java.io.BufferedReader;
    import java.io.FileNotFoundException;
    import java.io.FileReader;
    import java.io.IOException;
    import java.io.PrintWriter;
    import java.util.regex.Matcher;
    import java.util.regex.Pattern;

    public class TestingNoEmail {
        public static void main(String[] args) throws IOException {
            /*
             * The below regular expression pattern will search for the Indian phone number 
             * which have 10 numbers, 11 numbers(includes 0 at start) and 12 numbers(includes 91 at start)
            */
            String phoneNumberRegexPattern = "(0|91)?[7-9][0-9]{9}";

            Pattern p = Pattern.compile(phoneNumberRegexPattern);
            try (PrintWriter pw = new PrintWriter("regex practice phone numbers output.txt");
                // It search for a txt file called input.txt and get the content inside of the file
                BufferedReader br = new BufferedReader(new FileReader("regex practice text.txt"))) {
                
                String line;
                // line variable get the line by line with the help of readLine() method if it exists
                while ((line = br.readLine()) != null) {
                    Matcher m = p.matcher(line);
                    if (m.find()) { // Check if there's at least one match
                        pw.println(m.group()); // Print the matched phone number to the output.txt file 
                    }
                }
            } catch (FileNotFoundException e) {
                System.err.println("File not found: " + e.getMessage());
            } catch (IOException e) {
                System.err.println("IOException: " + e.getMessage());
            }
        }
    }

    regex practice phone numbers output.txt:
        8993475623
        7562389934
        7934562389

```

### Example of Using external txt file (Email IDs)

```java
    import java.io.BufferedReader;
    import java.io.FileNotFoundException;
    import java.io.FileReader;
    import java.io.IOException;
    import java.io.PrintWriter;
    import java.util.regex.Matcher;
    import java.util.regex.Pattern;

    public class TestingNoEmail {
        public static void main(String[] args) throws IOException {
            /*
             * The below regular expression pattern will search for email ids 
             * 
            */
            String emailIdRegexPattern = "[a-zA-Z0-9][a-zA-Z0-9_\-$%]*@[a-zA-Z0-9]+\.[a-zA-Z]*";

            Pattern p = Pattern.compile(emailIdRegexPattern);
            try (PrintWriter pw = new PrintWriter("regex practice email ids output.txt");
                // It search for a txt file called input.txt and get the content inside of the file
                BufferedReader br = new BufferedReader(new FileReader("regex practice text.txt"))) {
                
                String line;
                // line variable get the line by line with the help of readLine() method if it exists
                while ((line = br.readLine()) != null) {
                    Matcher m = p.matcher(line);
                    if (m.find()) { // Check if there's at least one match
                        pw.println(m.group()); // Print the matched phone number to the output.txt file 
                    }
                }
            } catch (FileNotFoundException e) {
                System.err.println("File not found: " + e.getMessage());
            } catch (IOException e) {
                System.err.println("IOException: " + e.getMessage());
            }
        }
    }

    regex practice email ids output.txt:
        user@example.com
        doe@example.com
        jane_smith123@domain.co
        tag@sub.domain
```