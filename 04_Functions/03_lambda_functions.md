# Lambda, Map, Filter

## Simple Explanation (Hinglish)
Normal functions dher saari jagah aur lines lete hain. Agar koi aisa function banayana ho jo chota sa ho aur uska sirf ek bar use ho, to hum **lambda** use karte hain. Yeh 'anonymous' function hota hai jiska koi naam nahi hota.

## Theory (Clear + Structured)
- **Lambda Functions**: Small, anonymous functions created using the `lambda` keyword. They can take any number of arguments, but can only have **one expression**.
- **`map(function, iterable)`**: Applies the function to every item in the iterable (like list).
- **`filter(function, iterable)`**: Filters out elements from an iterable where the function returns False.

## Syntax
```python
lambda arguments : expression
```

## Examples

```python
# Example 1: Lambda basic
add = lambda x, y: x + y
print(add(5, 3)) # Output: 8

# Example 2: Map function
numbers = [1, 2, 3, 4]
squared = list(map(lambda x: x**2, numbers))
print(squared) # Output: [1, 4, 9, 16]

# Example 3: Filter function
ages = [12, 18, 24, 16, 30]
adults = list(filter(lambda x: x >= 18, ages))
print(adults) # Output: [18, 24, 30]
```

## Dry Run / Explanation
* `lambda x, y: x + y`: Humne function bina naam ka banaya jo 2 input `x` and `y` lega aur unka sum return karega. Uski definition ko hi variable `add` mein store kar diya.
* `map()`: Ye line by line kaam karta hai. numbers array uthaya, sabhi numbers ko individually lambda function mein feed kiya, answer nikala, aur new map object return kiya (`list()` usko array format mei laata hai).
* `filter()`: `ages` nikalega as `x`. Agar `x >= 18` True ho gaya, toh select kar lega, False ko hata dega.

## Common Mistakes
1. Trying to add multiple lines of logic in Lambda: Lambda strictly restricts you to a single expression. No loop or complex `if...else` statements can be nested directly.
2. Forgetting to cast `map` or `filter` objects to `list`. Doing `print(map(...))` will print a memory reference instead of values.

## Interview Notes
1. Why use Lambda? Lambda is extremely useful as arguments to higher-order functions like `sort()`, `map()`, and `filter()`. E.g., `data.sort(key=lambda x: x['age'])`.
2. **List Comprehension**: Map/Filter can usually be replaced by List Comprehensions which are more "Pythonic" (`[x**2 for x in numbers]`).

## Practice Questions

**Easy:**
1. Write a lambda function that multiples an argument `n` by 10.
2. Create lambda to add two numbers and return sum.
3. Write lambda to check if number is positive.
4. Create lambda that returns square of a number.
5. Use lambda with map() to double all elements in list.
6. Create lambda to concatenate two strings.
7. Write lambda that returns last character of string.
8. Use lambda with filter() to get numbers > 10 from list.
9. Create lambda to find maximum of two numbers.
10. Write lambda that converts string to uppercase.

**Medium:**
1. Given a list of numbers, use `filter()` and `lambda` to extract only the even numbers.
2. Use map() with lambda to convert list of temperatures from Celsius to Fahrenheit.
3. Sort list of strings by their length using sorted() with lambda key.
4. Filter out None values from list using filter() and lambda.
5. Use reduce() with lambda to find product of all list elements.
6. Sort dictionary items by value using sorted() and lambda.
7. Use map() with lambda to extract first letter of each word in list.
8. Filter palindrome strings from list using filter() and lambda.
9. Chain multiple lambdas: filter odd numbers, then square them using map().
10. Use lambda with sorted() to sort list of dicts by specific key.

**Hard:**
1. Sort a list of tuples `[(1, 'B'), (3, 'A'), (2, 'C')]` primarily based on the second item in each tuple (string character) using `sorted()` and `lambda`.
2. Implement custom sorting: sort by multiple criteria using lambda tuple key.
3. Create higher-order function that takes lambda as parameter and applies conditionally.
4. Use lambda with itertools.groupby() to group consecutive identical elements.
5. Implement quicksort one-liner using list comprehension and lambda for pivot.
6. Create lambda that works as closure capturing outer variable.
7. Use functools.partial with lambda to create specialized functions.
8. Implement currying using nested lambda functions.
9. Create dynamic validator using lambda expressions for form fields.
10. Build pipeline of transformations using reduce() with lambda composition.
