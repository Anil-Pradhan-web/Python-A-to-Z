# Input / Output in Python

## Simple Explanation (Hinglish)
Jab humein user se kuch value leni hoti hai (jaise unka naam ya age), toh hum `input()` ka use karte hain. Aur jab humein screen par kuch dikhana hota hai, toh `print()` ka use karte hain. Samajh lo, `input()` sunne ka kaam karta hai aur `print()` bolne ka.

## Theory (Clear + Structured)
- **Output (`print()`)**: Used to display information on the console. It can take multiple arguments, separated by commas.
- **Input (`input()`)**: Used to take input from the user. By default, `input()` always reads the data as a **String**. If you need an integer or float, you must typecast it.

## Syntax
```python
# For Output
print("Message", variable)

# For Input
variable = input("Prompt message: ")
```

## Examples

```python
# Example 1: Basic Input and Output
name = input("Enter your name: ")
print("Hello", name)

# Example 2: Typecasting Input
age = int(input("Enter your age: "))
years_left = 100 - age
print("You will turn 100 in", years_left, "years.")

# Example 3: F-strings (Modern way to format strings)
city = "Delhi"
print(f"I live in {city}.")
```

## Dry Run / Explanation
* `input("Enter your age: ")`: Yeh user ko prompt show karega aur value enter karne ka wait karega.
* Agar user ne `25` enter kiya, toh woh pehle ek string `"25"` banega.
* `int()` us `"25"` ko integer `25` mein convert karega, kyunki string ke saath math operations (jaise `100 - "25"`) nahi ho sakte.
* F-string (`f"..."`) variables ko directly string ke andar `{}` brackets mein likhne ki facility deta hai. Use f-strings for clean output formatting.

## Common Mistakes
1. **Forgetting to Typecast**: Trying to add numbers from input without converting them (e.g., `num1 + num2` where both are strings will result in concatenation, not mathematical addition).
2. **Missing `f` in F-strings**: Using `{var}` without writing `f` before the string throws no error, but literally `{var}` is printed as it is.

## Interview Notes
1. **Default Type of Input**: Always remember to tell the interviewer that `input()` returns a string by default.
2. **End and Sep parameters in Print**: 
   - `print("A", "B", sep='-')` outputs `A-B`.
   - `print("A", end=' ')` prevents a new line after printing.

## Practice Questions

**Easy:**
1. Take the user's first name and last name as input and print them together.
2. Ask user for their favorite color and print "Your favorite color is [color]".
3. Take a number as input and print its square using multiplication.
4. Ask user for two numbers and print which one is larger.
5. Take input of your city and country, then print "I live in [city], [country]".
6. Ask user for their birth year and calculate their age (assuming current year is 2024).
7. Take a string input and print it in uppercase using `.upper()` method.
8. Ask user for a number and print whether it's positive, negative, or zero.
9. Take three subject marks as input and calculate total marks.
10. Ask user for their name and print it 5 times using string multiplication.

**Medium:**
1. Write a program to take two numbers as input and print their sum, difference, and product.
2. Take temperature in Celsius as input and convert to Fahrenheit. Print with 2 decimal places.
3. Ask user for radius of circle and calculate area (πr²) and circumference (2πr).
4. Take input of length and breadth of rectangle, calculate area and perimeter.
5. Create a simple calculator: Take two numbers and an operator (+, -, *, /) as input.
6. Take user's salary as input and calculate HRA (10%), DA (5%), and net salary.
7. Ask for distance in km and convert to meters, centimeters, and millimeters.
8. Take input of principal, rate, and time. Calculate simple interest and total amount.
9. Create a marksheet program: Take 5 subject marks, calculate percentage and grade.
10. Take a 4-digit number as input and find sum of its digits.

**Hard:**
1. Format a print statement using `f-strings` to display: "My name is [Name], I am [Age] years old, and my salary is [Salary] LPA." padded with leading zeros for salary.
2. Create a currency converter: Take amount in INR and convert to USD, EUR, GBP (use fixed rates).
3. Take a number as input and reverse it (e.g., 1234 → 4321) without using string conversion.
4. Create a compound interest calculator with user input for P, R, T and compounding frequency.
5. Take input of base and exponent, calculate power without using `**` operator or `pow()`.
6. Create a program that takes time in seconds and converts to HH:MM:SS format.
7. Take 3 sides of triangle as input, check if it's valid triangle and calculate area using Heron's formula.
8. Create a GST calculator: Take price and GST rate, calculate final price with CGST and SGST.
9. Take input of speed in km/h and convert to m/s. Also calculate time to cover 100km.
10. Create a BMI calculator: Take weight (kg) and height (m), calculate BMI and categorize health status.
