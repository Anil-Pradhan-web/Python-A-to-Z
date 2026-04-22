# Inheritance and Polymorphism

## Simple Explanation (Hinglish)
- **Inheritance**: Jaise aapko apne parents se aakhen ya baal aate hain (traits milte hain), waise hi programming mein ek Parent Class se uski Child Class saari properties le sakti hai. Isse baar baar code nahi likhna padta.
- **Polymorphism**: "Poly" yani bahot, "morph" yani form. Ek hi cheez ka alag-alag roop. Jaise "+" operator numbers ko add karta hai par strings ko join kar deta hai. Waise hi ek function parent mein kuch aur kaam karega aur child mein usko override karke kuch naya kaam kara sakte hain.

## Theory (Clear + Structured)
- **Inheritance**: Allows us to define a class that inherits all the methods and properties from another class.
  - **Parent class** (Base class): The class being inherited from.
  - **Child class** (Derived class): The class that inherits from another class.
  - **`super()`**: Used to call methods and constructors of the parent class.
- **Polymorphism**: The ability of an object to take on many forms. In Python, this is mostly achieved via **Method Overriding**, where a child class provides a specific implementation of a method that is already provided by its parent class.

## Syntax
```python
class ParentClass:
    # methods here

class ChildClass(ParentClass):
    # methods here
```

## Examples

```python
# Inheritance and Polymorphism Example
class Animal:
    def __init__(self, name):
        self.name = name

    def make_sound(self):
        print("Some generic sound")

class Cat(Animal):
    def __init__(self, name, color):
        # Calling parent constructor
        super().__init__(name)  
        self.color = color

    # Method Overriding (Polymorphism)
    def make_sound(self):
        print(f"{self.name} says Meow!")

class Dog(Animal):
    def make_sound(self):
        print(f"{self.name} says Bark!")

# Testing
pet1 = Cat("Kitty", "White")
pet2 = Dog("Bruno")

pet1.make_sound() # Kitty says Meow!
pet2.make_sound() # Bruno says Bark!
```

## Dry Run / Explanation
* `class Cat(Animal)`: Isse Cat class, Animal ki child ban gayi.
* `super().__init__(name)`: Isne explicitly parent class `Animal` ka `__init__` call kiya taaki `self.name` set ho jaye bina wapas wohi code likhe.
* `make_sound`: Parent aur child dono mein same naam ka function hai. Par jab main `pet1.make_sound()` bulata hu jo ki ek `Cat` hai, toh hamesha Child ka rule chalta hai (override). Ese Polymorphism kehte hain.

## Common Mistakes
1. Forgetting to pass the parent class as an argument in the class definition (e.g., writing `class Cat:` instead of `class Cat(Animal):`).
2. Not using `super().__init__()` in the child class, which prevents parent attributes from being initialized, leading to AttributeErrors later.

## Interview Notes
1. Multiple Inheritance (`class Child(Parent1, Parent2):`) is fully supported in Python, unlike Java.
2. Interviewers might ask about the **MRO (Method Resolution Order)**. It's the order in which base classes are searched when executing a method. You can check it using `ClassName.__mro__`.

## Practice Questions

**Easy:**
1. Create a `Vehicle` parent class with a `start_engine()` method. Create a `Car` child class that inherits from it.
2. Define class `Animal` with sound attribute, create `Dog` and `Cat` subclasses.
3. Create base class `Shape` with area() method, derive `Circle` and `Rectangle`.
4. Make parent class `Person` with name, age; child class `Student` adds grade.
5. Create class `Bird` with fly() method, subclass `Penguin` overrides fly().
6. Define `Appliance` class, inherit `WashingMachine` with wash_cycle() method.
7. Create `Fruit` base class, derive `Apple` and `Banana` with color attribute.
8. Make `User` class, inherit `Admin` with additional permissions list.
9. Create `Instrument` class, subclass `Guitar` with strings_count attribute.
10. Define `Food` class, derive `Pizza` with toppings list attribute.

**Medium:**
1. Override the `start_engine()` method in the `Car` class to print "Car uses a push button start".
2. Implement multiple inheritance: `AmphibiousCar` inherits from both `Car` and `Boat`.
3. Create class hierarchy: `Person` → `Employee` → `Manager` with increasing attributes.
4. Use super() to call parent __init__ and add child-specific initialization.
5. Implement method overriding for `display_info()` in 3-level inheritance chain.
6. Create abstract-like base class `Payment` with pay() method, implement in `Card`, `UPI`, `Cash`.
7. Design `Device` → `SmartDevice` → `Smartphone` with cumulative methods.
8. Implement polymorphism: list of different shapes, call area() on each.
9. Create mixin class `Loggable` with log() method, combine with other classes.
10. Use isinstance() and issubclass() to check inheritance relationships.

**Hard:**
1. Create an `Employee` base class and two child classes `Manager` and `Developer`. Add a polymorphic method `calculate_salary()` that works differently for each role.
2. Implement diamond inheritance problem and demonstrate MRO using __mro__ attribute.
3. Create deep inheritance tree (4+ levels) with proper super() chaining.
4. Design plugin system using inheritance: BasePlugin → various specific plugins.
5. Implement strategy pattern using inheritance for different sorting algorithms.
6. Create framework with template method pattern: base class defines skeleton, subclasses fill details.
7. Build ORM-like structure: BaseModel → User, Post, Comment with CRUD operations.
8. Implement visitor pattern using double dispatch with inheritance.
9. Create factory pattern: Factory base class with concrete factories for products.
10. Design event system: Event base class with specialized events (ClickEvent, KeyEvent, etc.).
