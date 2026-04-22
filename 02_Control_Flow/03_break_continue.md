# Break, Continue, and Pass

## Simple Explanation (Hinglish)
Maan lo aap ek long journey pe ho (loop). 
- `break`: Achanak car kharab ho gayi, aap journey wahi rok dete ho (loop khatam). 
- `continue`: Raste mein gadha aa gaya, aap us gadhe ko chhod kar aage thoda jump kar lete ho, par journey chalu rehti hai.
- `pass`: Yeh bass ek placeholder hai. Agar aapko lagta hai baad mein kuch likhoge, to waha `pass` daal do warna error aayegi.

## Theory (Clear + Structured)
Loop control statements change execution from its normal sequence. 

- **`break`**: Terminates the loop entirely and transfers execution to the statement immediately following the loop.
- **`continue`**: Skips the rest of the code inside the current iteration and jumps back to the top to check the condition for the next iteration.
- **`pass`**: A null operation. Nothing happens when it is executed. It's used as a placeholder when a statement is syntactically required but you have no code to execute yet.

## Syntax
```python
for item in sequence:
    if condition:
        break     # or continue, or pass
```

## Examples

```python
# Example 1: Break
for i in range(1, 10):
    if i == 5:
        break
    print(i) # Output: 1 2 3 4
print("Loop exited")

# Example 2: Continue
for i in range(1, 6):
    if i == 3:
        continue
    print(i) # Output: 1 2 4 5

# Example 3: Pass
for i in range(5):
    pass     # Will write logic here later
```

## Dry Run / Explanation
* **Break Example**: Loop 1 se 9 tak chalna chahiye tha. Par jab `i` ki value 5 hoti hai, `break` run ho jata hai. Loop wahi turant band ho jata hai aur aage ka print nahi chalta.
* **Continue Example**: Jab `i == 3` hua, `continue` run hua. Usne print ko skip kar diya aur wapas upar loop mein chala gaya next value (4) lekar. Isliye 3 print nahi hua.

## Common Mistakes
1. Placing `break` or `continue` outside a loop. They ONLY work inside `for` or `while` loops.
2. In while loops, using `continue` before updating the increment variable can cause an infinite loop because the update step gets skipped.

## Interview Notes
1. Understand the exact difference: `break` exits the whole loop, while `continue` only jumps to the next iteration.
2. Be prepared to dry-run logic featuring loops combined with `break`.

## Practice Questions

**Easy:**
1. Write a loop from 1 to 10 but break the loop if the number is 7.
2. Print numbers 1 to 15, skip number 8 using continue.
3. Use pass statement in an empty if block without error.
4. Create infinite while loop that breaks when user enters 'quit'.
5. Print first 5 vowels from a string using break.
6. Skip negative numbers in a list using continue.
7. Use break to exit loop when element 'stop' is found in list.
8. Print numbers 1-20 but skip multiples of 3 using continue.
9. Create for loop with pass as placeholder for future logic.
10. Break out of loop when sum exceeds 50 while adding numbers 1 to 100.

**Medium:**
1. Write a loop that prints only odd numbers from 1 to 20 by using `continue` for even numbers.
2. Find first prime number greater than 50 using break and continue.
3. Print multiplication tables 1-5, but skip table of 3 using continue.
4. Search for a number in list, print position and break when found.
5. Count consonants in string, skip vowels using continue.
6. Sum numbers from list until negative number encountered, then break.
7. Print pattern but skip middle row using continue.
8. Find all numbers divisible by 7 between 1-100, stop after finding 5 such numbers.
9. Validate password: Keep asking until valid (min 8 chars), use break on success.
10. Process list of orders, skip cancelled ones using continue, break on out of stock.

**Hard:**
1. Write a program to find the first number divisible by 7 and 11 between 100 and 500, and immediately stop searching once found.
2. Implement linear search with break, return -1 if not found using else with loop.
3. Create number guessing game: Give hints, break on correct guess, limit to 5 attempts.
4. Process nested list, flatten it but skip None values using continue.
5. Find LCM of two numbers using break when common multiple found.
6. Check if string is pangram (contains all alphabets), break early if all found.
7. Implement bubble sort with break optimization (no swaps = sorted).
8. Parse log file lines, skip comments (#), break on ERROR keyword.
9. Generate Fibonacci series, break when number exceeds 1000.
10. Menu-driven program: Keep showing menu until user chooses Exit option using break.
