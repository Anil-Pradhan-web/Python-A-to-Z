# Regular Expressions (RegEx)

## Simple Explanation (Hinglish)
RegEx ek bhaut powerful tool hai jo string ke andar khaas pattern dhoondhne ke kaam aata hai. Jaise agar aapko kisi badi text file mein se saare email IDs ya phone numbers nikalne hain, to aap RegEx pattern ka use kar sakte hain. Yeh shuru mein thoda complex dikhta hai par ek baar pattern samajh gaye, to data extraction bohot easy ho jata hai.

## Theory (Clear + Structured)
A Regular Expression (RegEx) is a sequence of characters that forms a search pattern. Python has a built-in package called `re`, which can be used to work with Regular Expressions.

Common `re` functions:
- `re.search()`: Returns a Match object if there is a match anywhere in the string.
- `re.findall()`: Returns a list containing all matches.
- `re.sub()`: Replaces one or many matches with a string.
- `re.split()`: Returns a list where the string has been split at each match.

Common Metacharacters:
- `\d`: Returns a match where the string contains digits (numbers from 0-9)
- `\w`: Match word characters (a-z, A-Z, 0-9, _)
- `+`: One or more occurrences
- `*`: Zero or more occurrences
- `^`: Starts with
- `$`: Ends with

## Syntax
```python
import re

pattern = r"your_regex_pattern"
result = re.findall(pattern, text)
```

## Examples

```python
import re

text = "My phone number is 9876543210 and my friend's is 1234567890. Email: test@email.com"

# Example 1: Find all digits (phone numbers)
# \d means digit, {10} means exactly 10 times
phones = re.findall(r"\d{10}", text)
print("Phones:", phones) 
# Output: ['9876543210', '1234567890']

# Example 2: Find Email
# \w+ means one or more word character, @ is literal, \. is literal dot
email_pattern = r"\w+@\w+\.\w+"
emails = re.findall(email_pattern, text)
print("Emails:", emails) 
# Output: ['test@email.com']

# Example 3: Find and Replace
redacted = re.sub(r"\d{10}", "**********", text)
print("Redacted:", redacted)
```

## Dry Run / Explanation
* The `r"..."` prefix means a "raw string". It tells Python not to handle backslashes as escape characters naturally so that the regex engine gets them directly.
* `re.findall(r"\d{10}", text)`: Yeh function text ko line-by-line padhega aur jahan bhi usko exactly 10 digits ka block milega, usko list mein daal dega.
* `re.sub`: Yeh kisi specific pattern ko kisi aur string se replace kar deta hai (jaise phone number ko stars `*` se replace karna).

## Common Mistakes
1. **Forgetting `import re`**: RegEx is not inherently available without importing the module.
2. **Not using raw strings (`r"..."`)**: This leads to issues like `\n` being interpreted as a newline character instead of a regex token.
3. Over-complicating RegEx: Writing a regex that is extremely hard to read. Use online tools like regex101.com to test patterns!

## Interview Notes
1. **Greedy vs Non-Greedy**: Interviewers often ask about this. Adding `?` after a quantifier makes it non-greedy (it matches as little text as possible).
2. RegEx is highly sought after in Data Science and Backend tasks for validation and scraping.

## Practice Questions

**Easy:**
1. Write a regex to extract all uppercase letters from a string.
2. Find all digits in a string using \d pattern.
3. Extract all words from a sentence using \w+ pattern.
4. Check if string starts with specific word using ^ anchor.
5. Find all email addresses in text using basic email pattern.
6. Replace all whitespace with underscore using re.sub().
7. Check if string ends with .com or .in using $ anchor.
8. Extract all numbers (including decimals) from text.
9. Split string by multiple delimiters (comma, semicolon, space).
10. Find all 3-character words in a sentence.

**Medium:**
1. Write a regex to validate if an input string is a valid Indian vehicle number plate (e.g., MH12AB1234).
2. Validate phone number formats: +91-XXXXXXXXXX, XXXXXXXXXX, (XXX) XXX-XXXX.
3. Extract dates in DD/MM/YYYY format from text.
4. Find and highlight all occurrences of a word with <mark> tags.
5. Validate URL format (http/https, domain, optional path).
6. Extract hashtags from social media post text.
7. Parse log file to extract timestamp, level, and message.
8. Find repeated words in text (e.g., "the the") using backreferences.
9. Extract currency amounts with symbols ($, ₹, €) and decimals.
10. Validate IP address format (IPv4: XXX.XXX.XXX.XXX).

**Hard:**
1. Write a regex to match strong passwords (at least 8 chars, 1 uppercase, 1 lowercase, 1 number, 1 special character).
2. Extract nested HTML tags content using non-greedy matching.
3. Parse complex JSON-like structure without JSON parser using regex.
4. Validate and extract credit card numbers with proper Luhn check pattern.
5. Find balanced parentheses expressions using recursive patterns.
6. Extract multiline comments from code (/* ... */).
7. Parse CSV with quoted fields containing commas using regex.
8. Validate international phone numbers with country codes.
9. Extract version numbers from changelog (v1.2.3-beta.4 format).
10. Implement custom template parser: {{variable}} and {%if condition%} blocks.
