
# Regex Patterns for Validation

> Here are several examples of different regular expressions (regex) designed to achieve the same goal, each with its own specific constraints.

## Email Validation

### Basic Email Regex
```regex
^[\w\.-]+@[\w\.-]+\.\w{2,}$
```

### Comprehensive Email Regex
```regex
^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$
```

### RFC 5322 Compliant Email Regex
```regex
^(?=.{1,256})(?=.{1,64}@.{1,255})[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$
```

### Simple Email Regex
```regex
^[^@\s]+@[^@\s]+\.[^@\s]+$
```

---

## Password Validation

### Basic Password Regex
```regex
^.{6,}$
```

### Password with Uppercase, Lowercase, and Digits
```regex
^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)[A-Za-z\d]{8,}$
```

### Password with Special Characters
```regex
^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$
```

### Strong Password Regex
```regex
^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{12,20}$
```

---

## File Input Validation

### Basic File Name Validation
```regex
^[\w\.-]+$
```

### File Extension Validation
```regex
^[\w\.-]+\.(jpg|jpeg|png|pdf)$
```

### Multiple File Extensions
```regex
^[\w\.-]+\.(doc|docx|xls|xlsx|ppt|pptx)$
```

### General File Type Validation
```regex
^[\w\.-]+\.(txt|csv|json|xml|html|jpg|jpeg|png|gif|pdf|doc|docx|xls|xlsx|ppt|pptx|zip|rar)$
```

### File Name Length Validation
```regex
^(?=.{1,255}$)[\w\.-]+\.(jpg|jpeg|png|pdf)$
```

---

## Phone Number Validation

### Basic Phone Number Validation
```regex
^\d{10}$
```

### Phone Number with Optional Country Code
```regex
^\+?\d{1,3}?\s?\d{10}$
```

### Phone Number with Different Formats
```regex
^(\+?\d{1,3}?\s?)?(\(\d{3}\)|\d{3})[-.\s]?\d{3}[-.\s]?\d{4}$
```

### International Phone Number Validation
```regex
^\+?[1-9]\d{1,14}$
```