# If-Else Conditional Statements

## Simple Explanation (Hinglish)
Life mein hum kaafi decisions lete hain conditions ke base par. Jaise "Agar baarish hui, toh chhatri le jaunga, warna nahi". Code mein yahi logic likhne ke liye hum `if-else` ka use karte hain. Yeh code ko batata hai ki kab kaunsa hissa chalana hai.

## Theory (Clear + Structured)
Conditional statements allow a program to execute certain pieces of code depending on whether a condition is true or false.

- **`if` statement**: Executes if the condition is True.
- **`elif` (else if)**: Used to check multiple conditions sequentially if the previous conditions were False.
- **`else` statement**: Executes when all previous `if`/`elif` conditions are False.

Indentation is highly important in Python to define blocks of code inside these statements.

## Syntax
```python
if condition1:
    # code to execute if condition1 is True
elif condition2:
    # code to execute if condition2 is True
else:
    # code to execute if all conditions are False
```

## Examples

```python
# Example 1: Basic If-Else
marks = 75

if marks >= 90:
    print("Grade: A")
elif marks >= 70:
    print("Grade: B")
elif marks >= 50:
    print("Grade: C")
else:
    print("Grade: F (Fail)")
```

## Dry Run / Explanation
* `marks = 75`. Pehla check `marks >= 90` false hai, toh yeh `if` block skip ho jayega.
* Dusra check `marks >= 70` true ho gaya (`75 >= 70`), toh loop uske andar ghusega aur "Grade: B" print karega.
* Ek baar `True` mil gaya, toh baaki ke `elif` aur `else` block automatically chhod diye jayenge.

## Common Mistakes
1. **IndentationError**: Python uses spaces/tabs to define scope. Forgetting to indent code inside `if` block is a common mistake.
2. **Using `=` instead of `==` in conditions**: Writing `if x = 5:` instead of `if x == 5:`.
3. **Missing Colons**: Forgetting the `:` at the end of `if`, `elif`, or `else` lines.

## Interview Notes
1. **Ternary Operator**: Mention the inline if-else representation which is helpful in making code concise: `result = "Pass" if marks > 50 else "Fail"`
2. Always write conditions from the most restrictive to the least restrictive for logic to work correctly in `if-elif` ladders.

## Practice Questions

**Easy:**
1. Write code to check if a person is eligible to vote (age >= 18).
2. Check if a number is positive, negative, or zero using if-else.
3. Write a program to check if a number is even or odd.
4. Check if a character entered by user is vowel or consonant.
5. Find maximum of two numbers using if-else.
6. Check if a year is leap year or not.
7. Verify if a student passed or failed based on marks (passing marks = 35).
8. Check if a number is divisible by both 3 and 5.
9. Determine if a triangle is equilateral (all sides equal) using if condition.
10. Check if a person is teenager (13-19 years), adult (20-59), or senior citizen (60+).

**Medium:**
1. Find the largest among three numbers using if-elif-else statements.
2. Create a grade calculator: A (90-100), B (80-89), C (70-79), D (60-69), F (<60).
3. Check if three angles form a valid triangle (sum = 180).
4. Calculate electricity bill with slabs: 0-100 units (₹2), 101-200 (₹3), 201+ (₹5).
5. Check if a number is Armstrong number (sum of cubes of digits = number itself).
6. Determine profit or loss given cost price and selling price.
7. Check if a quadrilateral is square, rectangle, or other based on sides.
8. Find middle number among three different numbers.
9. Validate password: Check if length >= 8 and contains at least one digit.
10. Calculate discount based on shopping amount: 10% (>5000), 5% (>2000), else 0%.

**Hard:**
1. Write a calculator program that takes two numbers and an operator (+, -, *, /) as input and returns the result using nested if-else.
2. Solve quadratic equation ax² + bx + c = 0 and determine nature of roots (real, imaginary, equal).
3. Check if four points form a square, rectangle, rhombus, or general quadrilateral.
4. Implement rock-paper-scissors game logic between two players.
5. Determine zodiac sign based on birth date and month using complex if-elif conditions.
6. Check if a number is palindrome without converting to string.
7. Validate date format (DD/MM/YYYY) and check if it's a valid calendar date.
8. Calculate income tax based on age and income slabs with different tax rates.
9. Check if three points are collinear (lie on same straight line) using slope formula.
10. Implement ATM withdrawal logic with balance check, denomination limits, and daily limit validation.
