# Variables and Data Types

## Simple Explanation (Hinglish)
Variables programming mein "containers" ki tarah hote hain jahan hum data store karte hain. Jaise ghar mein chini (sugar) rakhne ke liye ek dabba hota hai, wese hi data ko rakhne ke liye variable ka use hota hai. Python mein variable banana bohot simple hai, aapko type batane ki zaroorat nahi hoti (kyunki Python dynamically typed hai).

## Theory (Clear + Structured)
A **variable** is a named location in memory used to store data. In Python, you don't need to declare the variable type explicitly. 

**Data Types** define the type of data a variable holds. Common data types in Python include:
- **Integer (`int`)**: Whole numbers (e.g., 5, -10)
- **Float (`float`)**: Decimal numbers (e.g., 3.14, -0.5)
- **String (`str`)**: Text data enclosed in quotes (e.g., "Hello", 'Python')
- **Boolean (`bool`)**: Represents `True` or `False`

## Syntax
```python
variable_name = value
```

## Examples

```python
# Example 1: Basic Variables
age = 20          # int
price = 99.99     # float
name = "Rahul"    # str
is_student = True # bool

print(name)
print(age)

# Example 2: Multiple Assignments
a, b, c = 1, 2, "Hello"
print(a, b, c)

# Example 3: Checking type
print(type(price)) # class <'float'>
```

## Dry Run / Explanation
* `age = 20`: Yahan humne `age` naam ka ek variable banaya aur usme `20` assign kiya. Python automatically samajh gaya ki yeh integer hai.
* `print(name)`: `name` variable ki value console mein dikha dega.
* `type()`: Ek in-built function hai jo batata hai variable mein kis tarah ka data rakha hai.

## Common Mistakes
1. **Naming Variables Incorrectly**: Variable names cannot start with a number (e.g., `1name = "Rahul"` will throw an error).
2. **Case Sensitivity**: `Age` and `age` are two different variables. Beginners often confuse them.
3. **Forgetting Quotes for Strings**: Writing `name = Rahul` instead of `name = "Rahul"` will cause a `NameError`.

## Interview Notes
1. **Dynamic Typing**: Interviewer might ask "Why is Python called dynamically typed?". Answer: Because we don't need to declare the data type explicitly. The interpreter infers it at runtime.
2. **Immutability**: Strings and integers are immutable in Python. Changing a string creates a new object in memory.

## Practice Questions

**Easy:**
1. Create a variable `city` and assign your city name to it. Print the variable.
2. Find the data type of the value `3.14159` using a built-in function.
3. Create three variables: `name` (string), `age` (int), and `height` (float). Print all three.
4. What will be the output of `type(10)` and `type("10")`? Explain the difference.
5. Create a boolean variable `is_raining` with value `False` and print its type.
6. Assign the same value `"Python"` to three different variables in a single line.
7. Create a variable with value `100` and convert it to string type explicitly.
8. Check if a variable `x = 50` is of integer type using `type()` function.
9. Create variables for your favorite color, number, and food. Print them together.
10. What happens when you assign `None` to a variable? Check its type.

**Medium:**
1. Swap the values of two variables `a = 10` and `b = 20` without using a third variable.
2. Create two variables `num1 = "100"` and `num2 = "200"` (as strings). Add them after converting to integers.
3. Given `x = 10`, `y = 20`, `z = 30`, swap values so that `x=30`, `y=10`, `z=20`.
4. Create a variable `price = 99.999`. Round it to 2 decimal places and store in new variable.
5. Take input from user for their name and age. Print a message: "Hello [name], you are [age] years old."
6. Create variables `a = 5`, `b = 2`. Perform all arithmetic operations and store results in separate variables.
7. Given `text = "Hello World"`, extract and store first word and last word in separate variables.
8. Create a complex number variable and extract its real and imaginary parts separately.
9. Chain assignment: Create three variables with same value `100` using single statement, then change one to `200`.
10. Create variables for student's name, roll number, marks in 3 subjects. Calculate total and average.

**Hard:**
1. Write a program to take complex numbers as input and print their real and imaginary parts.
2. Create a temperature converter: Take Celsius as input and convert to Fahrenheit using formula `F = C * 9/5 + 32`.
3. Given `a = 10`, `b = 3`, demonstrate integer division, float division, modulo, and power operations.
4. Create a program that swaps first and last digits of a 4-digit number (e.g., 1234 → 4231).
5. Take three numbers as input and find the largest without using `max()` function.
6. Create a currency converter: Convert USD to INR (assume 1 USD = 83 INR) with proper formatting.
7. Given a number, check if it's divisible by both 3 and 5 using modulo operator.
8. Create variables for rectangle's length and breadth. Calculate area, perimeter, and diagonal length.
9. Implement a simple interest calculator: Take principal, rate, time as input and calculate SI.
10. Create a program to extract middle digit from a 3-digit number (e.g., 456 → 5).
