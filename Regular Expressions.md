> Learn how to identify, search, validate, extract, and manipulate text using pattern-matching expressions.

## 1. Introduction

A Regular Expression (Regex or RegExp) is a sequence of characters that defines a search pattern.

Regex is used to find specific patterns inside text without manually checking every character.

For example, Regex can help identify:

- Email addresses.
    
- Phone numbers.
    
- IP addresses.
    
- Dates.
    
- Password patterns.
    
- URLs.
    
- Suspicious strings in log files.
    

Regex is supported by many programming languages, including Python, JavaScript, Java, and PHP.

## 2. Why Regular Expressions Matter

Regular expressions are useful for:

- Searching text.
    
- Validating user input.
    
- Extracting information.
    
- Replacing matching text.
    
- Cleaning datasets.
    
- Analyzing application logs.
    
- Detecting suspicious patterns.
    

In cybersecurity, Regex is commonly used for log analysis, data extraction, input validation, and security monitoring.

## 3. Basic Regex Syntax

A regular expression consists of characters and special symbols that define a pattern.

Example:

```
cat
```

This pattern matches the text `cat`.

Example text:

```
The cat is sleeping.
The dog is running.
```

The pattern matches `cat` in the first sentence.

## 4. Common Regex Metacharacters

Metacharacters have special meanings in regular expressions.

|Symbol|Meaning|Example|
|---|---|---|
|`.`|Any character except newline by default|`c.t`|
|`^`|Beginning of string or line|`^Hello`|
|`$`|End of string or line|`end$`|
|`*`|Zero or more repetitions|`ab*`|
|`+`|One or more repetitions|`ab+`|
|`?`|Zero or one repetition|`colou?r`|
|`{n}`|Exactly n repetitions|`a{3}`|
|`{n,}`|At least n repetitions|`a{2,}`|
|`{n,m}`|Between n and m repetitions|`a{2,4}`|
|`[]`|Character class|`[abc]`|
|`()`|Grouping|`(ab)+`|
|`|`|Alternative|`cat|dog`|
|`\`|Escape or special sequence|`\.`|

## 5. Character Classes

Character classes define which characters are allowed at a particular position.

|Pattern|Meaning|
|---|---|
|`[abc]`|a, b, or c|
|`[a-z]`|Lowercase letters|
|`[A-Z]`|Uppercase letters|
|`[0-9]`|Digits|
|`[a-zA-Z]`|Uppercase or lowercase letters|
|`[^0-9]`|Any character except a digit|

Example:

```
[0-9]
```

Matches a single digit.

Example text:

```
Room 204
```

The pattern matches `2`, `0`, and `4` individually.

## 6. Character Shorthand Classes

Regex provides shorthand patterns for commonly used character groups.

|Pattern|Meaning|
|---|---|
|`\d`|Digit|
|`\D`|Non-digit|
|`\w`|Word character|
|`\W`|Non-word character|
|`\s`|Whitespace|
|`\S`|Non-whitespace|

The exact definition of a word character can vary between regex engines.

## 7. Quantifiers

Quantifiers specify how many times a character or group may appear.

|Quantifier|Meaning|
|---|---|
|`*`|Zero or more|
|`+`|One or more|
|`?`|Zero or one|
|`{3}`|Exactly three|
|`{2,5}`|Between two and five|
|`{2,}`|Two or more|

Examples:

```
a*
```

Matches zero or more occurrences of `a`.

```
a+
```

Matches one or more occurrences of `a`.

```
[0-9]{4}
```

Matches exactly four consecutive digits.

## 8. Anchors

Anchors identify positions instead of matching ordinary characters.

### Beginning Anchor — `^`

```
^Hello
```

Matches `Hello` only at the beginning of the relevant string or line.

### Ending Anchor — `$`

```
world$
```

Matches `world` at the end of the relevant string or line.

### Word Boundary — `\b`

```
\bcat\b
```

Matches the word `cat` as a separate word, rather than matching it inside `category`.

## 9. Groups and Alternatives

### Grouping

Parentheses create a group.

```
(ab)+
```

Matches one or more repetitions of `ab`.

Examples:

- `ab`
    
- `abab`
    
- `ababab`
    

### Alternative

The `|` symbol means OR.

```
cat|dog
```

Matches either `cat` or `dog`.

### Capturing Groups

Capturing groups allow matched portions of text to be extracted.

```
(\d{2})-(\d{2})-(\d{4})
```

Can capture a date such as:

```
23-11-2026
```

The three groups capture the day, month, and year.

## 10. Greedy and Lazy Matching

Quantifiers are generally greedy by default. They try to match as much text as possible while still allowing the complete pattern to match.

Example:

```
<.*>
```

Given:

```
<b>Hello</b>
```

A greedy match may capture the entire string.

A lazy quantifier adds `?`:

```
<.*?>
```

It matches the shortest portion that allows the pattern to succeed.

**Important:** Lazy matching does not automatically make a regex safe or suitable for parsing HTML. Use an HTML parser for structured HTML.

## 11. Regular Expressions in Python

Python provides the built-in `re` module for working with regular expressions.

Import it:

```
import re
```

### Search

Find the first matching occurrence anywhere in the string.

```
import re

text = "My ID is 12345"

result = re.search(r"\d+", text)

if result:
    print(result.group())
```

Output:

```
12345
```

### Match

Checks for a match at the beginning of the string.

```
import re

text = "Hello World"

result = re.match(r"Hello", text)

if result:
    print("Matched")
```

### Full Match

Checks whether the entire string matches the pattern.

```
import re

text = "12345"

result = re.fullmatch(r"\d+", text)

if result:
    print("Valid number")
```

### Find All

Returns all non-overlapping matches.

```
import re

text = "Room 101, Room 202, Room 303"

result = re.findall(r"\d+", text)

print(result)
```

Output:

```
['101', '202', '303']
```

### Replace

Replaces matching text.

```
import re

text = "My phone number is 9876543210"

result = re.sub(r"\d", "*", text)

print(result)
```

### Split

Splits text using a regular expression as the separator.

```
import re

text = "apple,banana;orange mango"

result = re.split(r"[,;\s]+", text)

print(result)
```

## 12. Raw Strings in Python

Python interprets backslashes in ordinary string literals as escape sequences.

For Regex patterns, raw strings are generally recommended.

Example:

```
pattern = r"\d+"
```

The `r` prefix tells Python to treat backslashes as literal characters rather than interpreting them as ordinary string escapes.

## 13. Common Regex Examples

### Email-Like Pattern

```
^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}$
```

This checks for a common email-address structure.

It is not a complete implementation of all valid email-address rules.

### Phone Number — Exactly 10 Digits

```
^\d{10}$
```

Matches exactly ten digits.

This validates length and digit format, not whether the number is real or assigned.

### IPv4-Like Pattern

```
^(?:(?:25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)\.){3}(?:25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)$
```

Checks the decimal range of each IPv4 octet.

For production applications, use a dedicated IP-address parsing library where possible.

### Date Format — DD-MM-YYYY

```
^\d{2}-\d{2}-\d{4}$
```

Checks the format only. It does not verify that the date exists.

### Extract URLs

```
https?://[^\s]+
```

Finds simple HTTP and HTTPS URL-like strings.

It is not a complete URL validator.

## 14. Regular Expressions for Cybersecurity

Regex is useful in security operations and defensive analysis.

### 1. Log Analysis

Extract IP addresses, timestamps, usernames, and event identifiers from logs.

### 2. Suspicious Input Detection

Identify patterns that may require additional security inspection.

### 3. File Analysis

Search text files for specific indicators, keywords, or structured identifiers.

### 4. Data Loss Prevention

Identify patterns that resemble sensitive information, such as phone numbers or identification numbers.

### 5. Security Monitoring

Create pattern-based detection rules for log-processing systems.

**Important:** A Regex match is not proof of malicious activity. Patterns can produce false positives and false negatives.

## 15. Regex Security Risks

Regular expressions can introduce security problems if used carelessly.

### ReDoS — Regular Expression Denial of Service

ReDoS occurs when a vulnerable regex pattern causes excessive processing time for certain inputs.

Some patterns with ambiguous nested repetition can trigger catastrophic backtracking.

Example of a potentially dangerous pattern:

```
^(a+)+$
```

An attacker may provide specially crafted input that causes the regex engine to perform an excessive amount of work.

### Prevention

- Avoid ambiguous nested quantifiers.
    
- Prefer simpler patterns.
    
- Limit input length.
    
- Use regex engine timeouts where supported.
    
- Test patterns with adversarial inputs.
    
- Consider linear-time regex engines for untrusted input.
    

## 16. Limitations of Regular Expressions

Regex is powerful, but it is not the right tool for every problem.

Limitations include:

- Complex patterns can become difficult to maintain.
    
- Regex can produce false positives.
    
- Some patterns may be computationally expensive.
    
- Validation may require more than matching a text format.
    
- Nested structured formats are often better handled by dedicated parsers.
    

Examples:

- Use a JSON parser for JSON.
    
- Use an HTML parser for HTML.
    
- Use a URL or IP-address library for robust validation.
    

## 17. Practical Lab

**Objective:** Practice extracting and validating information using Python Regex.

Create a file named:

```
regex_lab.py
```

### Lab A — Extract Numbers

```
import re

text = "User 101 logged in. User 202 failed login."

numbers = re.findall(r"\d+", text)

print(numbers)
```

Expected output:

```
['101', '202']
```

### Lab B — Extract IP Addresses

```
import re

log = """
Connection from 192.168.1.10
Connection from 10.0.0.5
Connection from 172.16.0.20
"""

ips = re.findall(
    r"\b(?:\d{1,3}\.){3}\d{1,3}\b",
    log
)

print(ips)
```

This is a simple extraction pattern. It does not validate that each octet is between 0 and 255.

### Lab C — Find Failed Login Events

```
import re

logs = """
SUCCESS: User admin logged in
FAILED: User guest login attempt
FAILED: User root login attempt
SUCCESS: User student logged in
"""

failed = re.findall(r"FAILED:.*", logs)

for event in failed:
    print(event)
```

### Lab D — Validate a Phone Number

```
import re

phone = input("Enter a 10-digit phone number: ")

if re.fullmatch(r"\d{10}", phone):
    print("Valid format")
else:
    print("Invalid format")
```

### Lab E — Extract Email-Like Strings

```
import re

text = """
Contact admin@example.com
Support: help@example.org
Invalid: user@
"""

pattern = r"[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}"

emails = re.findall(pattern, text)

print(emails)
```

## 18. Key Takeaways

- Regex defines patterns for matching text.
    
- Metacharacters provide special matching behavior.
    
- Character classes define allowed characters.
    
- Quantifiers control repetition.
    
- Anchors identify positions in text.
    
- Groups allow portions of matches to be captured.
    
- Python provides Regex functionality through the `re` module.
    
- Regex is useful for log analysis and security monitoring.
    
- Regex validation does not always prove that data is valid.
    
- Poorly designed patterns can introduce ReDoS vulnerabilities.
    

## 19. Related Topics

- [[Introduction to python]]
    
- [[Python Functions]]
    
- [[Python File Handling]]
    
- [[Python Exception Handling]]
    
- [[Algorithms]]
    
- [[Time and Space Complexity]]
    
- [[Log Analysis with Python]]
    
- [[Input Validation]]
    
- [[Secure Error Handling]]
    
- [[Digital Forensics]]