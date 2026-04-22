# String Deep Dive

## Simple Explanation (Hinglish)
Python mein strings par kaam karna bohot simple aur mazedar hai. String sirf text hoti hai (letters mili hui list ki tarah). Python humein bohot saare methods deta hai text ko format karne, todne (split), jodna (join), aur slice karne ke liye.

## Theory (Clear + Structured)
Strings in Python are immutable arrays of characters. 
- **Immutability**: Once a string object is created, you cannot change its specific characters.
- **Slicing**: You can extract a part of a string using `[start : stop : step]`.
- **Useful Methods**: `upper()`, `lower()`, `strip()`, `split()`, `join()`, `replace()`.

## Syntax
```python
my_string = "Hello World"
slice = my_string[start_index:end_index]
```

## Examples

```python
# Example 1: Basic String Methods
text = "   Python is fun!   "
print(text.strip())           # Removes leading/trailing whitespaces
print(text.lower())           # Converts to lowercase
print(text.replace("fun", "easy")) # Replaces a substring

# Example 2: Split and Join
sentence = "I love coding"
words = sentence.split()      # Splits by spaces -> ['I', 'love', 'coding']
print(words)

new_sentence = "-".join(words) # Joins list with hyphens
print(new_sentence)           # Output: I-love-coding

# Example 3: Slicing
word = "DEVELOPER"
print(word[0:3])   # DEV (from index 0 to 2)
print(word[::-1])  # REPOLEVED (Reverses the string!)
```

## Dry Run / Explanation
* `split()`: Default roop se spaces par string ko todta hai aur list return karta hai.
* `"-".join(words)`: Us list ke har item ke beech mein `-` daal kar wapas ek new string bana deta hai.
* `[::-1]`: Slicing ka advanced concept. Start aur stop humne khali chhod diya isliye puri string lega, par step `-1` diya toh string ko peeche se reverse read karega.

## Common Mistakes
1. Trying to change a character: `string[0] = 'a'` throws a `TypeError`. You must create a new string.
2. Mixing up `split` and `join` object types: `join` is called *on* the separator string, passing the list as argument (`",".join(list)`).

## Interview Notes
1. **String Reversal**: `string[::-1]` is the fastest and most pythonic way to reverse a string. Interviewers explicitly ask this!
2. **Palindrome Check**: Easy one-liner: `is_palindrome = word == word[::-1]`.

## Practice Questions

**Easy:**
1. Take a string input, remove all leading/trailing whitespaces, and convert it to uppercase.
2. Reverse a string using slicing [::-1].
3. Check if a string is palindrome using string reversal.
4. Count total characters in a string without using len().
5. Replace all occurrences of 'a' with 'b' in a string.
6. Convert string to lowercase and check if it equals another string.
7. Extract first 5 characters from a string using slicing.
8. Check if string starts with "Hello" using startswith() method.
9. Split a sentence into words using split() method.
10. Join list of words into single string with space separator.

**Medium:**
1. Write a program to count total vowels in a given string.
2. Find first non-repeating character in a string.
3. Check if two strings are anagrams of each other.
4. Count frequency of each character in string using dictionary.
5. Remove all digits from a string.
6. Capitalize first letter of each word in sentence.
7. Find longest word in a sentence.
8. Check if string contains only alphabets using isalpha().
9. Rotate string by n positions (left and right).
10. Validate if string is valid email format (basic check with @ and .).

**Hard:**
1. Write a program that converts a snake_case string (e.g., `my_variable_name`) to camelCase (`myVariableName`).
2. Implement run-length encoding: "aaabbcccc" → "a3b2c4".
3. Find all permutations of a string using recursion.
4. Check if string is valid parenthesis expression (balanced brackets).
5. Implement string compression: "aabcccccaaa" → "a2b1c5a3".
6. Find length of longest substring without repeating characters.
7. Implement custom string tokenizer similar to split() but with multiple delimiters.
8. Check if one string is rotation of another string.
9. Find all starting indices of pattern in text (naive pattern search).
10. Convert integer to Roman numeral and vice versa.
