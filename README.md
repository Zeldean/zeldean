# Object-Oriented Programming (OOP)
Object-Oriented Programming (OOP) is a programming paradigm that organizes software design around objects rather than functions or logic. An object can represent a real-world entity (like a car or a person) or a concept (like a bank account), and it combines data (attributes) and behavior (methods) in a single unit.

## Key Concepts of OOP:
1. **Classes**: Blueprints for creating objects. They define the properties (attributes) and behaviors (methods) that the objects will have.

2. **Objects**: Instances of classes. Each object can have different attribute values, but they share the same structure and behavior as defined by the class.

3. **Encapsulation**: Bundling the data (attributes) and methods (behavior) together, and restricting direct access to some of the object's components. This protects the integrity of the object.

4. **Inheritance**: A way to create a new class based on an existing class. The new class (child) inherits attributes and methods from the existing class (parent) but can also have additional features.

5. **Polymorphism**: The ability to treat objects of different classes in a similar way. Polymorphism allows methods to behave differently based on the object calling them, even if they share the same name.

6. **Abstraction**: Hiding complex implementation details and showing only the necessary features of an object. This simplifies interaction with objects by focusing on what they do rather than how they do it.

## Example:
In C#, you might have a `Car` class that defines the attributes and behaviors of a car, like this:

```csharp
public class Car
{
    // Attributes (Fields)
    public string Make { get; set; }
    public string Model { get; set; }

    // Constructor
    public Car(string make, string model)
    {
        Make = make;
        Model = model;
    }

    // Behavior (Method)
    public void Drive()
    {
        Console.WriteLine($"{Make} {Model} is driving!");
    }
}

// Creating an object of the Car class
Car myCar = new Car("Toyota", "Corolla");
myCar.Drive();  // Output: Toyota Corolla is driving!
```

---

# Classes and Objects in C#

In C#, **classes** and **objects** are fundamental building blocks of Object-Oriented Programming (OOP). 

- A **class** is like a blueprint for creating objects. It defines the structure (attributes) and behavior (methods) that the objects created from the class will have.
- An **object** is an instance of a class. When you create an object from a class, you are using that blueprint to create something tangible in memory.

## Classes:
- A class in C# is a user-defined data type that holds data and methods.
- It defines the attributes (fields) and behaviors (methods) that the objects created from it will have.

**Syntax**:
```csharp
public class ClassName
{
    // Fields (attributes)
    private string name;
    private int age;

    // Constructor
    public ClassName(string name, int age)
    {
        this.name = name;
        this.age = age;
    }

    // Methods (behaviors)
    public void DisplayInfo()
    {
        Console.WriteLine($"Name: {name}, Age: {age}");
    }
}
```

## Objects:
- An object is an instance of a class. It is created using the `new` keyword followed by the class constructor.
- Objects represent the real-world entities created based on the blueprint (class).

**Example**:
```csharp
// Creating an object of the class
ClassName obj = new ClassName("John", 30);

// Calling a method on the object
obj.DisplayInfo();  // Output: Name: John, Age: 30
```

## Example Explained:
1. **Class Definition**: The class `ClassName` has two fields (`name` and `age`), a constructor to initialize those fields, and a method `DisplayInfo()` to print the values.
2. **Object Creation**: We create an object `obj` of the `ClassName` class using the `new` keyword.
3. **Method Call**: We call the `DisplayInfo()` method on the `obj` object to print the values of `name` and `age`.

## Important Points:
- **Constructor**: A special method used to initialize objects. It has the same name as the class and no return type.
- **Fields**: Variables that hold the data of a class. They represent the state of the object.
- **Methods**: Functions defined inside a class that define the behavior of the objects.

---

# Constructors in C#

A **constructor** is a special method in a class that gets called automatically when an object of that class is created. Its main purpose is to initialize the object, setting up any initial values for its fields or performing any setup steps that are needed before the object can be used.

## Key Points about Constructors:
1. **Name**: A constructor has the same name as the class.
2. **No Return Type**: Constructors do not have a return type, not even `void`.
3. **Called Automatically**: The constructor is called automatically when an object is created using the `new` keyword.
4. **Can Be Overloaded**: You can define multiple constructors with different parameters (constructor overloading) to allow objects to be initialized in different ways.

## Types of Constructors:
1. **Default Constructor**: A constructor that takes no parameters. If you do not define any constructors in your class, C# automatically provides a default constructor that initializes fields with default values (e.g., `0` for numeric types, `null` for reference types).

2. **Parameterized Constructor**: A constructor that takes one or more parameters. This allows you to pass specific values when creating an object, giving you more control over the initialization process.

## Example of Constructors:

```csharp
public class Person
{
    // Fields (attributes)
    public string Name;
    public int Age;

    // Default Constructor
    public Person()
    {
        Name = "Unknown";
        Age = 0;
        Console.WriteLine("Default constructor called!");
    }

    // Parameterized Constructor
    public Person(string name, int age)
    {
        Name = name;
        Age = age;
        Console.WriteLine("Parameterized constructor called!");
    }

    // Method to display information
    public void DisplayInfo()
    {
        Console.WriteLine($"Name: {Name}, Age: {Age}");
    }
}

public class Program
{
    public static void Main()
    {
        // Using the default constructor
        Person person1 = new Person();
        person1.DisplayInfo();  // Output: Name: Unknown, Age: 0

        // Using the parameterized constructor
        Person person2 = new Person("Alice", 25);
        person2.DisplayInfo();  // Output: Name: Alice, Age: 25
    }
}
```

## Explanation:

1. **Default Constructor**:
   - `Person()` is a default constructor with no parameters. It initializes the `Name` field to `"Unknown"` and the `Age` field to `0`.
   - When `person1` is created using the default constructor, the `Name` and `Age` fields are set to these default values.

2. **Parameterized Constructor**:
   - `Person(string name, int age)` is a parameterized constructor that accepts two parameters: `name` and `age`. It initializes the `Name` and `Age` fields with the values provided when the object is created.
   - When `person2` is created using this constructor, its `Name` and `Age` fields are set to `"Alice"` and `25`, respectively.

## Constructor Overloading:
- In the above example, we have two constructors with the same name (`Person`), but with different parameter lists. This is called **constructor overloading**. The correct constructor is chosen based on the arguments passed when the object is created.

### Important Notes:
- **Optional Constructors**: If you define a constructor with parameters, the default constructor is no longer automatically provided by C#. You will need to define it explicitly if needed.
- **`this` Keyword**: Inside the constructor, you can use the `this` keyword to refer to the current object instance. This is useful when parameter names conflict with field names.

## Example Using `this` Keyword:

```csharp
public class Person
{
    public string Name;
    public int Age;

    // Constructor with parameters, using 'this' keyword to avoid name conflicts
    public Person(string name, int age)
    {
        this.Name = name;  // 'this.Name' refers to the class field, 'name' refers to the constructor parameter
        this.Age = age;
    }
}
```

## Constructor Chaining:
You can also chain constructors, meaning one constructor can call another constructor in the same class. This is done using the `this` keyword.

Example:

```csharp
public class Person
{
    public string Name;
    public int Age;

    // Default constructor
    public Person() : this("Unknown", 0)  // Calls the parameterized constructor
    {
    }

    // Parameterized constructor
    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }
}
```

In this case, the default constructor calls the parameterized constructor with default values `"Unknown"` and `0`.

---
# Inheritance in C#
Inheritance in C# is a fundamental concept of object-oriented programming (OOP) where one class (the child or derived class) inherits the properties and methods of another class (the parent or base class). This allows code reuse, reduces redundancy, and helps in organizing code more logically.

Here’s an overview with examples:

## Key Concepts:
1. **Base Class (Parent Class):**
   The class whose members (properties, methods, etc.) are inherited. It represents the general characteristics.

2. **Derived Class (Child Class):**
   The class that inherits members from the base class. It represents more specific characteristics.

3. **Access Modifiers:**
   - `public`: Accessible from anywhere.
   - `protected`: Accessible within the class and derived classes.
   - `private`: Accessible only within the class.

4. **Single Inheritance:**
   C# supports single inheritance, meaning a class can only inherit from one other class.

5. **`base` Keyword:**
   Used to access the members of the base class from the derived class.

## Example of Inheritance:
```csharp
// Base class
public class Animal
{
    public string Name { get; set; }
    
    public void Eat()
    {
        Console.WriteLine($"{Name} is eating.");
    }
}

// Derived class
public class Dog : Animal
{
    public void Bark()
    {
        Console.WriteLine($"{Name} is barking.");
    }
}

// Usage
class Program
{
    static void Main()
    {
        Dog dog = new Dog();
        dog.Name = "Buddy";
        dog.Eat(); // Inherited from Animal
        dog.Bark(); // Defined in Dog
    }
}
```

## Key Points in the Example:
- The `Dog` class inherits the `Name` property and `Eat` method from the `Animal` class.
- The `Dog` class has its own method, `Bark`, which is specific to it.

## Types of Inheritance:
1. **Single Inheritance:** One class inherits from one parent class.
2. **Hierarchical Inheritance:** Multiple classes inherit from a single base class.

## Polymorphism with Inheritance:
When combined with polymorphism (method overriding), inheritance becomes even more powerful.

## Method Overriding:
You can override methods in the base class using the `virtual` keyword in the base class and `override` in the derived class:
```csharp
public class Animal
{
    public virtual void Sound()
    {
        Console.WriteLine("Animal makes a sound");
    }
}

public class Dog : Animal
{
    public override void Sound()
    {
        Console.WriteLine("Dog barks");
    }
}
```
Inheritance in C# can take various forms, each with its unique structure and implications. Here’s a breakdown of each type:

### 1. **Single Inheritance**
   - **Definition:** A single class inherits from one base class.
   - **Example:**

```csharp
public class Animal
{
    public void Eat() => Console.WriteLine("Animal is eating.");
}

public class Dog : Animal
{
    public void Bark() => Console.WriteLine("Dog is barking.");
}

// Usage
Dog dog = new Dog();
dog.Eat(); // Inherited from Animal
dog.Bark(); // Defined in Dog
```

### 2. **Multiple Inheritance**
   - **Definition:** A class can inherit from multiple classes. 
   - **Note:** C# does **not** support multiple inheritance directly to avoid complexity and ambiguity (like the "Diamond Problem"). However, it can be achieved through interfaces.
   - **Example:**

```csharp
public interface IAnimal
{
    void Eat();
}

public interface IPet
{
    void Play();
}

public class Dog : IAnimal, IPet
{
    public void Eat() => Console.WriteLine("Dog is eating.");
    public void Play() => Console.WriteLine("Dog is playing.");
}

// Usage
Dog dog = new Dog();
dog.Eat();
dog.Play();
```

### 3. **Hierarchical Inheritance**
   - **Definition:** Multiple derived classes inherit from the same base class.
   - **Example:**

```csharp
public class Animal
{
    public void Eat() => Console.WriteLine("Animal is eating.");
}

public class Dog : Animal
{
    public void Bark() => Console.WriteLine("Dog is barking.");
}

public class Cat : Animal
{
    public void Meow() => Console.WriteLine("Cat is meowing.");
}

// Usage
Dog dog = new Dog();
dog.Eat(); // Inherited from Animal
dog.Bark(); // Specific to Dog

Cat cat = new Cat();
cat.Eat(); // Inherited from Animal
cat.Meow(); // Specific to Cat
```

### 4. **Multilevel Inheritance**
   - **Definition:** A class inherits from a derived class, forming a chain of inheritance.
   - **Example:**

```csharp
public class Animal
{
    public void Eat() => Console.WriteLine("Animal is eating.");
}

public class Mammal : Animal
{
    public void Walk() => Console.WriteLine("Mammal is walking.");
}

public class Dog : Mammal
{
    public void Bark() => Console.WriteLine("Dog is barking.");
}

// Usage
Dog dog = new Dog();
dog.Eat(); // Inherited from Animal
dog.Walk(); // Inherited from Mammal
dog.Bark(); // Specific to Dog
```

### 5. **Hybrid Inheritance**
   - **Definition:** A combination of more than one type of inheritance (e.g., hierarchical + multiple inheritance).
   - **Note:** In C#, hybrid inheritance is achieved mainly through interfaces since C# does not support multiple inheritance with classes.
   - **Example:**

```csharp
public interface IAnimal
{
    void Eat();
}

public class Mammal : IAnimal
{
    public void Eat() => Console.WriteLine("Mammal is eating.");
}

public class Bird : IAnimal
{
    public void Eat() => Console.WriteLine("Bird is eating.");
}

public class Bat : Mammal
{
    public void Fly() => Console.WriteLine("Bat is flying.");
}

// Usage
Bat bat = new Bat();
bat.Eat(); // Inherited from Mammal
bat.Fly(); // Specific to Bat
```

### Summary:
- **Single Inheritance:** One class inherits from one base class.
- **Multiple Inheritance:** Achieved using interfaces, where a class can implement multiple interfaces.
- **Hierarchical Inheritance:** Multiple classes inherit from one base class.
- **Multilevel Inheritance:** A chain of inheritance, where a derived class is further inherited by another class.
- **Hybrid Inheritance:** A combination of hierarchical and multiple inheritance, usually handled via interfaces.

Would you like to explore any of these types in more detail or focus on specific use cases?

---

# Abstraction in C#

**Abstraction** is one of the four fundamental principles of object-oriented programming (OOP), along with encapsulation, inheritance, and polymorphism. It focuses on hiding the complex implementation details and showing only the essential features of an object.

In C#, abstraction can be achieved using **abstract classes** and **interfaces**.

## 1. **Abstract Classes**
   - An abstract class cannot be instantiated directly. It can have abstract methods (without implementation) and non-abstract methods (with implementation).
   - Abstract methods must be implemented by derived classes.
   - An abstract class provides a common base structure for derived classes while allowing them to override or extend functionality.

### Example:

```csharp
// Abstract base class
public abstract class Animal
{
    // Abstract method (no implementation)
    public abstract void MakeSound();

    // Non-abstract method (with implementation)
    public void Eat() => Console.WriteLine("Animal is eating.");
}

// Derived class implementing the abstract method
public class Dog : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Dog barks.");
    }
}

// Usage
Dog dog = new Dog();
dog.Eat();        // Inherited from the base class (non-abstract)
dog.MakeSound();  // Implemented by the derived class
```

### Key Points:
- The `Animal` class is abstract and serves as a blueprint for other classes.
- The `MakeSound` method is abstract and must be implemented in the derived class.
- The `Eat` method is non-abstract and can be used as is.

## 2. **Interfaces**
   - An interface only defines a contract (method signatures, properties, etc.) without implementation.
   - A class that implements an interface must provide the implementation for all its members.
   - A class can implement multiple interfaces, providing flexibility.

### Example:

```csharp
// Interface definition
public interface IAnimal
{
    void MakeSound();
    void Eat();
}

// Class implementing the interface
public class Dog : IAnimal
{
    public void MakeSound()
    {
        Console.WriteLine("Dog barks.");
    }

    public void Eat()
    {
        Console.WriteLine("Dog is eating.");
    }
}

// Usage
Dog dog = new Dog();
dog.MakeSound();
dog.Eat();
```

### Key Points:
- Interfaces are purely abstract and cannot have any implementation.
- A class can implement multiple interfaces, achieving a form of multiple inheritance.

## When to Use Abstract Classes vs. Interfaces:
- **Abstract Classes:** Use when you need to share common functionality among derived classes while still allowing specific behavior in subclasses. They are also useful when you want to provide default behavior that derived classes can override.
- **Interfaces:** Use when you need to define a contract that multiple classes can implement, regardless of whether they share common behavior.

### Practical Example of Abstraction:
Imagine you are building a payment processing system. You can define a common interface or abstract class for all payment methods, ensuring that any new payment method adheres to the same structure.

```csharp
public interface IPaymentProcessor
{
    void ProcessPayment(double amount);
}

public class CreditCardPayment : IPaymentProcessor
{
    public void ProcessPayment(double amount)
    {
        Console.WriteLine($"Processing credit card payment of {amount}.");
    }
}

public class PayPalPayment : IPaymentProcessor
{
    public void ProcessPayment(double amount)
    {
        Console.WriteLine($"Processing PayPal payment of {amount}.");
    }
}

// Usage
IPaymentProcessor payment = new CreditCardPayment();
payment.ProcessPayment(100.00);

payment = new PayPalPayment();
payment.ProcessPayment(150.00);
```

### Summary:
- Abstraction hides unnecessary details and only exposes the relevant parts of an object.
- **Abstract classes** can have both abstract and non-abstract members, while **interfaces** only define a contract without any implementation.
- Both abstract classes and interfaces provide flexibility, allowing you to build scalable and maintainable applications.

Would you like more examples or a deeper dive into the differences between abstract classes and interfaces?
<!--
## Hi there 👋


**Zeldean/zeldean** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
