# Sets and Dictionaries

## Simple Explanation (Hinglish)
- **Set**: Samajh lo ek bag jisme sirf unique items rakh sakte ho. Agar aap isme 2 baar 'apple' daloge, yeh ek 'apple' ko chup-chap phek dega. Order matter nahi karta yahan.
- **Dictionary**: Yeh ek real-life dictionary jaisa hai jahan ek 'word' (Key) aur uska 'meaning' (Value) hota hai. Key ki madad se hum value search karte hain.

## Theory (Clear + Structured)
- **Set**: An unordered, mutable collection of **unique** elements. Enclosed in `{}`. Sets represent mathematical sets.
- **Dictionary (Dict)**: An unordered, mutable collection of **key-value pairs**. Enclosed in `{}` but structured as `key: value`. Keys must be unique and immutable, values can be anything.

## Syntax
```python
# Set syntax
my_set = {item1, item2, item3}

# Dictionary syntax
my_dict = {"key1": "value1", "key2": "value2"}
```

## Examples

```python
# Example 1: Sets
my_set = {1, 2, 2, 3, 4, 4, 5}
print(my_set) # Output: {1, 2, 3, 4, 5} (Duplicates removed)

my_set.add(6)
print(3 in my_set) # True (Fast membership testing)

# Example 2: Dictionaries
student = {
    "name": "Arjun",
    "age": 21,
    "course": "B.Tech"
}
# Accessing Value using Key
print(student["name"])     # Output: Arjun

# Modifying and Adding
student["age"] = 22        # Updates age
student["city"] = "Pune"   # Adds new key-value pair

# Example 3: Dictionary looping
for key, value in student.items():
    print(f"{key}: {value}")
```

## Dry Run / Explanation
* `my_set`: Start mein humne `2` aur `4` do baar dala, par set automatically duplicates hata deta hai.
* `student["city"] = "Pune"`: Puraani dictionary mein `city` naam ki key nahi thi toh usne isko add kar diya. Agar pehle se hoti toh replace (update) kar deta.
* `.items()`: Ek dictionary ke keys aur values ko pair (tuple) mein loop karne ki property deta hai.

## Common Mistakes
1. **KeyError in Dictionary**: Using `my_dict["wrong_key"]` when the key doesn't exist throws an error. Use `my_dict.get("wrong_key")` instead, which returns `None`.
2. **Accessing set with index**: E.g., `my_set[0]` will fail because sets are unordered, they don't have indexes.

## Interview Notes
1. Dictionary lookup `my_dict[key]` and Set lookup `value in my_set` take O(1) time complexity physically because they work on Hashing. That makes them extremely fast compared to Lists.
2. In Python 3.7+, Dictionaries preserve the insertion order, but historically they were unordered.

## Practice Questions

**Easy:**
1. Convert a list `[1, 1, 2, 3, 3, 4]` into a set to remove duplicates.
2. Create a dictionary with your name, age, and city as key-value pairs.
3. Add an element to a set using add() method.
4. Access value from dictionary using get() method (safe access).
5. Check if a key exists in dictionary using 'in' operator.
6. Remove an element from set using discard() method.
7. Create empty dictionary and add 3 key-value pairs.
8. Find union of two sets using | operator.
9. Get all keys from dictionary using keys() method.
10. Clear all elements from a set using clear() method.

**Medium:**
1. Create a frequency counter dictionary that counts how many times each character appears in the string "programming".
2. Merge two dictionaries into one using update() or ** operator.
3. Find common elements between two sets using intersection().
4. Sort dictionary by values in ascending order.
5. Remove duplicate words from sentence using set.
6. Create dictionary from two lists (keys list and values list) using zip().
7. Find difference between two sets (elements in A but not in B).
8. Count word frequency in a paragraph using dictionary.
9. Swap keys and values in a dictionary (if values are unique).
10. Check if two sets are disjoint (no common elements) using isdisjoint().

**Hard:**
1. Given two sets A and B, write a program to find the items that exist in both sets (Intersection) and items present only in A (Difference).
2. Implement phonebook: Add, search, delete contacts using dictionary.
3. Find symmetric difference of sets (elements in either A or B but not both).
4. Group anagrams from list of words using dictionary with sorted tuple as key.
5. Implement cache/memoization using dictionary for Fibonacci calculation.
6. Flatten nested dictionary: {'a': {'b': 1}} → {'a.b': 1}.
7. Find all pairs of sets that have non-empty intersection from list of sets.
8. Implement LRU (Least Recently Used) cache logic using OrderedDict.
9. Merge multiple dictionaries with conflict resolution (sum values of same keys).
10. Check if dictionary values form a valid set (all unique) without converting to set.
