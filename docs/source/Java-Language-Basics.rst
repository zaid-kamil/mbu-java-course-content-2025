Java Language Basics
====================


Table of Contents
-----------------


1.  `Your First Java Program <#your-first-java-program>`__
2.  `Command Line Arguments <#command-line-arguments>`__
3.  `Good Programming Practices <#good-programming-practices>`__
4.  `Java Language Features <#java-language-features>`__
5.  `Keywords <#keywords>`__
6.  `Data Types and Variables <#data-types-and-variables>`__
7.  `Operators <#operators>`__
8.  `Advanced Examples <#advanced-examples>`__
9.  `Practice Exercises <#practice-exercises>`__


Your First Java Program
------------------------

Every Java program starts with a class and a main method.

Example: HelloWorld.java
^^^^^^^^^^^^^^^^^^^^^^^^^
.. code-block:: java

    public class HelloWorld {
        public static void main(String[] args) {
            System.out.println("Hello, World!");
        }
    }

- ``public class HelloWorld`` creates a class named HelloWorld
- ``public static void main(String[] args)`` is the starting point of the program
- ``System.out.println`` prints text to the screen


Command Line Arguments
----------------------

Programs can receive input when they start.

Example: PrintName.java
^^^^^^^^^^^^^^^^^^^^^^^
.. code-block:: java

    public class PrintName {
        public static void main(String[] args) {
            System.out.println("First argument: " + args[0]);
            System.out.println("Second argument: " + args[1]);
        }
    }

- ``args[0]`` gets the first argument
- ``args[1]`` gets the second argument


Good Programming Practices
---------------------------

Write clean and readable code.

- Use meaningful names for classes and variables
- Add comments to explain your code
- Keep proper spacing and indentation

Example: Good vs Bad Names
^^^^^^^^^^^^^^^^^^^^^^^^^^
.. code-block:: java

    // Bad naming
    int a = 20;
    int b = 85;
    
    // Good naming
    int studentAge = 20;
    int testScore = 85;

- Choose names that describe what the variable stores


Java Language Features
----------------------

Java has several important features:

- **Platform Independent**: Runs on Windows, Mac, Linux
- **Object-Oriented**: Uses classes and objects
- **Secure**: Has built-in security features
- **Simple**: Easy to learn and use

Example: Simple Program
^^^^^^^^^^^^^^^^^^^^^^^
.. code-block:: java

    public class Welcome {
        public static void main(String[] args) {
            System.out.println("Welcome to Java Programming!");
        }
    }

- This program will run on any computer with Java installed


Keywords
--------

Keywords are special words in Java that have specific meanings.

Common Keywords:

- ``public`` - makes something accessible
- ``class`` - creates a new class
- ``static`` - belongs to the class, not an object
- ``void`` - returns nothing
- ``int`` - integer number type
- ``String`` - text type

Example: Using Keywords
^^^^^^^^^^^^^^^^^^^^^^^
.. code-block:: java

    public class Demo {
        public static void main(String[] args) {
            int number = 42;
            String message = "Java is fun!";
            System.out.println(message);
            System.out.println(number);
        }
    }

- Keywords cannot be used as variable names


Data Types and Variables
------------------------

Java has different types of data storage.

Primitive Data Types:

- ``int`` - whole numbers (1, 2, 100)
- ``float`` - decimal numbers (3.14, 2.5)
- ``double`` - large decimal numbers (2.29319299292)
- ``char`` - single character ('A', '1')
- ``boolean`` - true or false
- ``String`` - text ("Hello")


Example: Variable Declaration
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
.. code-block:: java

    public class Variables {
        public static void main(String[] args) {
            int age = 18;
            double price = 99.99;
            char grade = 'A';
            boolean isStudent = true;
            String name = "John";
            
            System.out.println("Age: " + age);
            System.out.println("Price: " + price);
            System.out.println("Grade: " + grade);
            System.out.println("Is Student: " + isStudent);
            System.out.println("Name: " + name);
        }
    }

- Each variable must be declared with its type before use


Operators
---------

Operators are special symbols that perform operations on variables and values.

Example: Basic Operation
^^^^^^^^^^^^^^^^^^^^^^^^
.. code-block:: java

    public class SimpleOperation {
        public static void main(String[] args) {
            int result = 5 + 3;
            System.out.println("Result: " + result);
        }
    }

- The ``+`` symbol is an operator that adds two numbers

Types of Operators
------------------

Java has several types of operators:

- **Arithmetic Operators**: For mathematical calculations
- **Assignment Operators**: For assigning values to variables
- **Comparison Operators**: For comparing values
- **Logical Operators**: For logical operations
- **Unary Operators**: Work with single operands

Arithmetic Operators
--------------------

Used for basic mathematical operations.

**Operators:**

- ``+`` Addition
- ``-`` Subtraction
- ``*`` Multiplication
- ``/`` Division
- ``%`` Modulus (remainder)

Example: All Arithmetic Operations
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
.. code-block:: java

    public class ArithmeticDemo {
        public static void main(String[] args) {
            int a = 20;
            int b = 6;
            
            System.out.println("a + b = " + (a + b));    // 26
            System.out.println("a - b = " + (a - b));    // 14
            System.out.println("a * b = " + (a * b));    // 120
            System.out.println("a / b = " + (a / b));    // 3
            System.out.println("a % b = " + (a % b));    // 2
        }
    }

Example: Decimal Division
^^^^^^^^^^^^^^^^^^^^^^^^^
.. code-block:: java

    public class DecimalMath {
        public static void main(String[] args) {
            double x = 15.0;
            double y = 4.0;
            
            System.out.println("15.0 / 4.0 = " + (x / y));    // 3.75
            System.out.println("15 / 4 = " + (15 / 4));       // 3
        }
    }

- Integer division gives integer result
- Double division gives decimal result

Assignment Operators
--------------------

Used to assign values to variables.

**Basic Assignment:**

- ``=`` Simple assignment

**Compound Assignment:**

- ``+=`` Add and assign
- ``-=`` Subtract and assign
- ``*=`` Multiply and assign
- ``/=`` Divide and assign
- ``%=`` Modulus and assign

Example: Assignment Operations
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
.. code-block:: java

    public class AssignmentDemo {
        public static void main(String[] args) {
            int num = 10;
            System.out.println("Initial value: " + num);    // 10
            
            num += 5;    // same as: num = num + 5
            System.out.println("After += 5: " + num);       // 15
            
            num -= 3;    // same as: num = num - 3
            System.out.println("After -= 3: " + num);       // 12
            
            num *= 2;    // same as: num = num * 2
            System.out.println("After *= 2: " + num);       // 24
            
            num /= 4;    // same as: num = num / 4
            System.out.println("After /= 4: " + num);       // 6
        }
    }

Comparison Operators
--------------------

Used to compare two values. Result is always true or false.

**Operators:**

- ``==`` Equal to
- ``!=`` Not equal to
- ``>`` Greater than
- ``<`` Less than
- ``>=`` Greater than or equal to
- ``<=`` Less than or equal to

Example: Comparison Operations
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
.. code-block:: java

    public class ComparisonDemo {
        public static void main(String[] args) {
            int a = 15;
            int b = 10;
            
            System.out.println("a == b: " + (a == b));    // false
            System.out.println("a != b: " + (a != b));    // true
            System.out.println("a > b: " + (a > b));      // true
            System.out.println("a < b: " + (a < b));      // false
            System.out.println("a >= b: " + (a >= b));    // true
            System.out.println("a <= b: " + (a <= b));    // false
        }
    }

Example: String Comparison
^^^^^^^^^^^^^^^^^^^^^^^^^^
.. code-block:: java

    public class StringComparison {
        public static void main(String[] args) {
            String name1 = "Java";
            String name2 = "Python";
            
            System.out.println("Are they equal? " + name1.equals(name2));    // false
            System.out.println("Are they equal? " + name1.equals("Java"));   // true
        }
    }

- Use ``.equals()`` method for comparing Strings, not ``==``

Logical Operators
-----------------

Used to combine multiple conditions.

**Operators:**

- ``&&`` AND (both conditions must be true)
- ``||`` OR (at least one condition must be true)
- ``!`` NOT (reverses the result)

Example: Logical Operations
^^^^^^^^^^^^^^^^^^^^^^^^^^^
.. code-block:: java

    public class LogicalDemo {
        public static void main(String[] args) {
            boolean isStudent = true;
            boolean hasID = false;
            int age = 20;
            
            System.out.println("Is student AND has ID: " + (isStudent && hasID));        // false
            System.out.println("Is student OR has ID: " + (isStudent || hasID));         // true
            System.out.println("NOT student: " + (!isStudent));                          // false
            System.out.println("Age > 18 AND is student: " + (age > 18 && isStudent));  // true
        }
    }

Unary Operators
---------------

Work with a single operand.

**Operators:**

- ``++`` Increment (add 1)
- ``--`` Decrement (subtract 1)
- ``+`` Positive
- ``-`` Negative
- ``!`` Logical NOT

Example: Increment and Decrement
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
.. code-block:: java

    public class UnaryDemo {
        public static void main(String[] args) {
            int count = 5;
            System.out.println("Initial count: " + count);    // 5
            
            count++;    // same as: count = count + 1
            System.out.println("After count++: " + count);    // 6
            
            count--;    // same as: count = count - 1
            System.out.println("After count--: " + count);    // 5
            
            int positive = +10;
            int negative = -10;
            System.out.println("Positive: " + positive);      // 10
            System.out.println("Negative: " + negative);      // -10
        }
    }

Operator Precedence
-------------------

When multiple operators are used, Java follows a specific order (precedence).

**Order of Precedence (Highest to Lowest):**

1. **Unary operators**: ``++``, ``--``, ``+``, ``-``, ``!``
2. **Multiplicative**: ``*``, ``/``, ``%``
3. **Additive**: ``+``, ``-``
4. **Comparison**: ``<``, ``>``, ``<=``, ``>=``
5. **Equality**: ``==``, ``!=``
6. **Logical AND**: ``&&``
7. **Logical OR**: ``||``
8. **Assignment**: ``=``, ``+=``, ``-=``, etc.

Example: Precedence in Action
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
.. code-block:: java

    public class PrecedenceDemo {
        public static void main(String[] args) {
            int result1 = 10 + 5 * 2;        // 20 (not 30)
            int result2 = (10 + 5) * 2;      // 30
            
            System.out.println("10 + 5 * 2 = " + result1);         // 20
            System.out.println("(10 + 5) * 2 = " + result2);       // 30
            
            boolean test = 5 > 3 && 8 < 10;  // true && true = true
            System.out.println("5 > 3 && 8 < 10 = " + test);       // true
        }
    }

- Multiplication happens before addition
- Use parentheses ``()`` to change the order

Type Casting
------------

Sometimes you need to convert one data type to another. In Java, this is called type casting. There are two types:

- **Implicit Casting**: Automatic conversion (smaller to larger type)
- **Explicit Casting**: Manual conversion (larger to smaller type)

Example: Type Casting
^^^^^^^^^^^^^^^^^^^^^
.. code-block:: java

    public class TypeCasting {
        public static void main(String[] args) {
            // Implicit Casting
            int numInt = 100;
            double numDouble = numInt;    // int to double
            System.out.println("Implicit Casting: " + numDouble); // 100.0
            
            // Explicit Casting
            double price = 99.99;
            int priceInt = (int) price;   // double to int
            System.out.println("Explicit Casting: " + priceInt);  // 99
        }
    }


- Implicit casting is safe and automatic
- Explicit casting may lose data (like decimal part)


Examples and Practice
---------------------

**Practice Problems:**

1. **Calculator Program**: Create a program that adds, subtracts, multiplies, and divides two numbers.

.. code-block:: java

    public class Calculator {
        public static void main(String[] args) {
            double num1 = 25.5;
            double num2 = 4.2;
            
            System.out.println("Addition: " + (num1 + num2));
            System.out.println("Subtraction: " + (num1 - num2));
            System.out.println("Multiplication: " + (num1 * num2));
            System.out.println("Division: " + (num1 / num2));
        }
    }

2. **Grade Checker**: Check if a student passes (score >= 60).

.. code-block:: java

    public class GradeChecker {
        public static void main(String[] args) {
            int score = 75;
            boolean passed = score >= 60;
            
            System.out.println("Score: " + score);
            System.out.println("Passed: " + passed);
        }
    }

3. **Age Validator**: Check if person is adult (age >= 18) and has license.

.. code-block:: java

    public class AgeValidator {
        public static void main(String[] args) {
            int age = 20;
            boolean hasLicense = true;
            boolean canDrive = age >= 18 && hasLicense;
            
            System.out.println("Age: " + age);
            System.out.println("Has License: " + hasLicense);
            System.out.println("Can Drive: " + canDrive);
        }
    }


Advanced Examples
-----------------

Combining concepts learned so far.

Example: Student Information
^^^^^^^^^^^^^^^^^^^^^^^^^^^^
.. code-block:: java

    public class StudentInfo {
        public static void main(String[] args) {
            String studentName = "Alice";
            int studentAge = 20;
            double gpa = 3.85;
            char section = 'A';
            
            System.out.println("Student Name: " + studentName);
            System.out.println("Age: " + studentAge);
            System.out.println("GPA: " + gpa);
            System.out.println("Section: " + section);
        }
    }

- Demonstrates multiple data types in one program

Example: Simple Math
^^^^^^^^^^^^^^^^^^^^
.. code-block:: java

    public class SimpleMath {
        public static void main(String[] args) {
            int length = 5;
            int width = 3;
            int area = length * width;
            int perimeter = 2 * (length + width);
            
            System.out.println("Length: " + length);
            System.out.println("Width: " + width);
            System.out.println("Area: " + area);
            System.out.println("Perimeter: " + perimeter);
        }
    }

- Shows how to store calculation results in variables


Practice Exercises
------------------

Try these programs in IntelliJ IDEA. Use only basic concepts - no loops or conditions.

**Basic Output Programs:**

1. Write a program to display "Hello Java!"
2. Write a program to display your name and city
3. Write a program to display three different messages
4. Write a program to print numbers 1, 2, 3 on separate lines
5. Write a program to display your favorite color and food

**Variable Programs:**

6. Create variables for your age, height, and weight, then display them
7. Store two numbers in variables and display both
8. Create a String variable with your school name and display it
9. Store the current year in a variable and display it
10. Create variables for length and width of a room and display both

**Calculation Programs:**

11. Add two numbers (like 15 + 25) and display the result
12. Subtract two numbers (like 50 - 20) and display the result
13. Multiply two numbers (like 7 * 8) and display the result
14. Divide two numbers (like 100 / 5) and display the result
15. Calculate the area of a rectangle (length * width)

**Operators Program**

16. Create a program that calculates compound interest using multiple operators
17. Write a program to check if a number is even using the modulus operator
18. Create a program that demonstrates all assignment operators
19. Write a program to compare two students' grades
20. Create a program that uses logical operators to check multiple conditions
21. Write a program showing operator precedence with complex expressions
22. Create a counter program using increment/decrement operators
23. Write a program to calculate the area and perimeter of different shapes
24. Create a program that validates user age and membership status
25. Write a program demonstrating the difference between ``++i`` and ``i++``



**Advanced Practice:**

26. Calculate simple interest using: amount = principal * rate * time / 100
27. Convert temperature: fahrenheit = celsius * 9/5 + 32
28. Calculate the area of a circle: area = 3.14 * radius * radius
29. Calculate total marks by adding marks of 3 subjects
30. Calculate average of two numbers: average = (num1 + num2) / 2

Tips for Students
----------------------

1. Run each program to see the output
2. Try changing the values and run again
3. Make sure class names match file names
4. Use meaningful variable names