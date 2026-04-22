# Lists and Tuples

## Simple Explanation (Hinglish)
List aur Tuple dono collection of items hote hain. Jaise aap bazaar jane se pehle ek shopping list banate ho jisme items hote hain, Python mein bhi list waisi hi hoti hai. 
List aur Tuple mein main farq kya hai? List ke items ko aap baad mein change kar sakte ho (modify/add/remove), par Tuple ek baar ban gaya toh fix ho jata hai, usko change nahi kar sakte.

## Theory (Clear + Structured)
- **List**: An ordered, mutable (changeable) collection of items. Enclosed in square brackets `[]`.
- **Tuple**: An ordered, immutable (unchangeable) collection of items. Enclosed in parentheses `()`.

Both lists and tuples can hold heterogenous data types (a mix of int, strings, floats, etc.).

## Syntax
```python
# List syntax
my_list = [item1, item2, item3]

# Tuple syntax
my_tuple = (item1, item2, item3)
```

## Examples

```python
# Example 1: Lists Methods
fruits = ["apple", "banana", "cherry"]
fruits.append("orange")    # Adds to the end
fruits.insert(1, "mango")  # Inserts at index 1
fruits.pop()               # Removes the last item
fruits[0] = "kiwi"         # Modifying an item
print(fruits) # Output: ['kiwi', 'mango', 'banana', 'cherry']

# Example 2: Tuples
coordinates = (10.0, 20.0)
# coordinates[0] = 15.0  --> This will throw a TypeError!
print(coordinates[1]) # Output: 20.0

# Example 3: Unpacking a Tuple
a, b = coordinates
print("X:", a, "Y:", b)
```

## Dry Run / Explanation
* `fruits.insert(1, "mango")`: List mein index 0 se shuru hota hai. Toh ye "mango" ko 1st index par daal dega, aur "banana", "cherry" sab aage shift ho jayenge.
* `tuple error`: Tuple banne ke baad update nahi hota. Agar aap `coordinates[0] = 15` karoge, Python gussa ho jayega kyunki Tuple 'immutable' hai.

## Common Mistakes
1. **Index Boundary**: Trying to access an element that does not exist (`IndexError: list index out of range`).
2. **Single Element Tuple**: Writing `tup = (5)` creates an integer, not a tuple. For a one-element tuple, you MUST add a comma: `tup = (5,)`.

## Interview Notes
1. **List vs Tuple memory**: Tuples take slightly less memory and are faster than lists because of immutability.
2. Tuples can be used as keys in a dictionary because they are immutable; lists cannot.

## Practice Questions

**Easy:**
1. Create a list of your 3 favorite movies. Try adding a new movie to the end of the list.
2. Create a tuple with 5 numbers and print the first and last element.
3. Add an element at index 2 in a list using insert() method.
4. Create a list of fruits, remove last item using pop().
5. Check if an element exists in a list using 'in' operator.
6. Create a tuple with single element (hint: use comma).
7. Slice a list to get first 3 elements.
8. Count occurrences of an element in list using count() method.
9. Find length of tuple using len() function.
10. Create a list of numbers 1-10, print elements at even indices.

**Medium:**
1. Given a list `numbers = [10, 20, 30, 40, 50]`, reverse the list using slicing or built-in methods.
2. Merge two lists into one without using + operator (use extend()).
3. Sort a list of tuples based on second element using sorted() with key.
4. Remove duplicates from a list while maintaining order.
5. Find common elements between two lists using list comprehension.
6. Rotate a list by n positions (move first n elements to end).
7. Flatten a nested list [[1,2], [3,4], [5]] into single list.
8. Swap first and last elements of a list.
9. Create list of squares from 1 to 10 using list comprehension.
10. Unpack tuple values into multiple variables.

**Hard:**
1. Write a program to find the second largest number in a given list of integers without using the `max()` default function twice.
2. Implement list rotation using slicing for both left and right rotation.
3. Find all pairs in list that sum to target value using nested loops.
4. Group consecutive identical elements into sublists [[1,1], [2], [3,3,3]].
5. Implement custom sort for list of strings by length without using key parameter.
6. Check if tuple contains another tuple as nested element.
7. Find intersection, union, and difference of two lists without sets.
8. Transpose a matrix (list of lists) using zip() function.
9. Implement run-length encoding for list: [a,a,b,c,c,c] → [(a,2), (b,1), (c,3)].
10. Merge k sorted lists into single sorted list efficiently.
