# Classes and Objects

## Simple Explanation (Hinglish)
Socho ek car ki factory hai. Factory mein ek 'blueprint' (naksha) hota hai jisme likha hota hai ki car mein 4 pahiye honge, ek steering hoga, aur color red hoga. Is nakshan (blueprint) ko **Class** bolte hain. 
Ab us blueprint ko dekh kar factroy waalon ne 10 real cars bana di. In real cars ko **Objects** bolte hain. Class bas ek idea hai, Object ek sacchi cheez hai jo memory leti hai.

## Theory (Clear + Structured)
Object-Oriented Programming (OOP) is a paradigm based on the concept of "objects".
- **Class**: A blueprint for creating objects, providing initial values for state (member variables or attributes), and implementations of behavior (member functions or methods).
- **Object**: An instance of a class. When a class is defined, no memory is allocated until an object of that class is created.
- **`__init__()` (Constructor)**: A special method automatically called when an object is created. Used to initialize attributes.
- **`self`**: Represents the instance of the class itself. It binds the attributes with the given arguments.

## Syntax
```python
class ClassName:
    def __init__(self, parameters):
        self.attribute = parameters
    
    def method_name(self):
        # logic

object_name = ClassName(arguments)
```

## Examples

```python
# Example 1: Basic Class and Object
class Dog:
    # Constructor
    def __init__(self, name, breed):
        self.name = name
        self.breed = breed
    
    # Method
    def bark(self):
        print(f"{self.name} is barking! Woof!")

# Creating objects
dog1 = Dog("Tommy", "Pug")
dog2 = Dog("Max", "Husky")

print(dog1.name) # Output: Tommy
dog2.bark()      # Output: Max is barking! Woof!
```

## Dry Run / Explanation
* `class Dog`: Humne Dog naam ka naya blueprint banaya. (Humesha Class ka naam capital letter se start karte hain).
* `__init__`: Jaise hi main line 12 pe `dog1 = Dog("Tommy", "Pug")` likhunga, python immediately `__init__` ko run karega. `name` mein "Tommy" aayega aur wo `self.name` mein save ho jayega hamesha ke liye. 
* `self`: `self` bas ye batata hai ki value kis specific object ki hai (e.g. `dog1` ki ya `dog2` ki).

## Common Mistakes
1. Forgetting `self` in method definitions inside a class will throw a TypeError: `bark() takes 0 positional arguments but 1 was given`.
2. Initializing attributes outside of `__init__` making them class-level variables (shared amongst all objects) instead of instance-level variables.

## Interview Notes
1. **Class vs Instance Attributes**: Variables defined inside `__init__` using `self` are instance variables (unique for each object). Variables defined directly inside the class but outside any method are Class variables (shared by all).
2. `self` is not a keyword. You can name it anything (like `this`), but `self` is a universally accepted convention.

## Practice Questions

**Easy:**
1. Create a `Student` class with attributes `name` and `age`. Create an object and print its name.
2. Define a class `Car` with brand and model attributes, create two objects.
3. Create class `Rectangle` with length and breadth, add method to calculate area.
4. Make class `Dog` with name attribute and bark() method that prints "Woof!".
5. Create class `Book` with title, author, and pages attributes.
6. Define class `Person` with __init__ that sets name and email.
7. Create class `Calculator` with add() method taking two parameters.
8. Make class `Circle` with radius attribute and circumference() method.
9. Create class `Employee` with id, name, salary attributes and display_info() method.
10. Define class `Phone` with brand, price attributes and call() method.

**Medium:**
1. Add a method `is_adult()` in the Student class that returns True if age >= 18, else False.
2. Create class `BankAccount` with balance, deposit(), withdraw() methods with validation.
3. Implement class `ComplexNumber` with real, imaginary parts and add/multiply methods.
4. Create class `Date` with day, month, year and method to check valid date.
5. Make class `ShoppingCart` with items list, add_item(), remove_item(), total() methods.
6. Create class `Fraction` with numerator, denominator and simplify() method using GCD.
7. Implement class `Vector2D` with x, y coordinates and dot product method.
8. Create class `Temperature` with celsius attribute and convert_to_fahrenheit() method.
9. Make class `Library` with books list, add_book(), search_book(), display_books() methods.
10. Create class `Counter` with count attribute and increment(), decrement(), reset() methods.

**Hard:**
1. Create a `BankAccount` class with `balance`. Add methods to `deposit(amount)` and `withdraw(amount)`. Ensure balance doesn't go below zero.
2. Implement class `Stack` using list with push(), pop(), peek(), is_empty() methods.
3. Create class `Queue` with enqueue(), dequeue(), front(), rear() operations.
4. Make class `Matrix` with 2D list, implement add() and multiply() for matrices.
5. Implement class `LinkedList` with Node inner class, append() and display() methods.
6. Create class `Polynomial` with coefficients dict, add() and evaluate(x) methods.
7. Design class `DeckOfCards` with shuffle(), deal_card(), cards_remaining() methods.
8. Implement class `HashTable` with insert(), search(), delete() using chaining.
9. Create class `BinaryTree` with insert(), inorder_traversal(), search() methods.
10. Design class `LRUCache` with get() and put() operations using OrderedDict.
