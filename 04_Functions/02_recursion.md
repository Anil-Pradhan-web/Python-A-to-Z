# Recursion

## Simple Explanation (Hinglish)
Inception movie dekhi hai? Usme dream ke andar ek aur dream hota hai. Recursion ka matlab hota hai, ek function apne andar se khud ko hi wapas bula leta hai. Ye tab tak khud ko bulata rehta hai jab tak ek final "stop condition" (Base case) na mil jaye.

## Theory (Clear + Structured)
Recursion is a programming technique where a function calls itself directly or indirectly.
A valid recursive function needs two strict rules:
1. **Base Case**: The condition where the function stops calling itself to avoid an infinite loop.
2. **Recursive Step**: The logic where the function calls itself with a modified parameter moving closer to the base case.

## Syntax
```python
def recursive_func(parameters):
    if base_condition:
        return result
    else:
        return recursive_func(modified_parameters)
```

## Examples

```python
# Example 1: Factorial (5! = 5 * 4 * 3 * 2 * 1)
def factorial(n):
    if n == 0 or n == 1:       # Base Case
        return 1
    else:
        return n * factorial(n - 1)  # Recursive Step

print(factorial(5)) # Output: 120

# Example 2: Fibonacci sequence (0, 1, 1, 2, 3, 5...)
def fibonacci(n):
    if n <= 0:
        return 0
    elif n == 1:
        return 1
    else:
        return fibonacci(n - 1) + fibonacci(n - 2)

print(fibonacci(6)) # Output: 8
```

## Dry Run / Explanation
* **Factorial(5) ka Dry run**:
    * `factorial(5)` dekhta hai return kya karna hai: `return 5 * factorial(4)`
    * `factorial(4)` banta hai: `4 * factorial(3)`
    * Yahi chalta jayega `factorial(1)` tak, jo `1` return karega kyunki n==1 mil gaya (Base Case!).
    * Phir values open hoti jayengi reverse mein: `1 * 2 * 3 * 4 * 5 = 120`.

## Common Mistakes
1. **Missing Base Case**: Without a base case, recursion runs infinitely until Python exhausts its call stack, resulting in a `RecursionError: maximum recursion depth exceeded`.
2. Passing the exact same arguments: Calling `factorial(n)` inside `factorial(n)` will lead to an infinite loop.

## Interview Notes
1. Interviewers ask Recursion mainly inside Data Structures & Algorithms interviews (like recursion in Trees and Graphs).
2. Remember that recursive solutions use more memory (Stack memory) than iterative (`while` loop) equivalents!

## Practice Questions

**Easy:**
1. Write a recursive function to print numbers from `n` down to 1.
2. Calculate sum of first n natural numbers using recursion.
3. Find factorial of number using recursive approach.
4. Print all elements of list using recursion.
5. Calculate sum of digits of number recursively.
6. Find nth Fibonacci number using simple recursion.
7. Count occurrences of character in string using recursion.
8. Check if string is palindrome using recursion.
9. Calculate power of number (base^exp) recursively.
10. Find maximum element in list using recursion.

**Medium:**
1. Write a recursive function to calculate `base` to the power of `exponent` (e.g., `power(2, 3)` = 8).
2. Implement binary search using recursion on sorted array.
3. Generate all permutations of a string using backtracking.
4. Solve Tower of Hanoi problem with n disks.
5. Calculate GCD of two numbers using Euclidean algorithm recursively.
6. Flatten nested list structure using recursion.
7. Implement recursive function to reverse linked list (conceptual).
8. Find all subsets of a set using recursion (power set).
9. Calculate combination nCr using recursive formula.
10. Implement recursive insertion sort algorithm.

**Hard:**
1. Write a recursive function to reverse a string (without using the `[::-1]` trick).
2. Solve N-Queens problem using backtracking and recursion.
3. Implement quicksort algorithm using recursion.
4. Generate valid parentheses combinations for n pairs.
5. Find all paths in maze from start to end using recursion.
6. Implement merge sort using recursive divide and conquer.
7. Solve Sudoku puzzle using recursive backtracking.
8. Calculate edit distance (Levenshtein distance) between two strings.
9. Implement recursive descent parser for simple arithmetic expressions.
10. Find longest increasing subsequence using recursion with memoization.
