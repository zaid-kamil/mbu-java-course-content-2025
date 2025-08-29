Java Language Basics
====================

Table of Contents
-----------------

1.  `Environment Setup <#environment-setup>`__
2.  `Your First Java Program <#your-first-java-program>`__
3.  `Command Line Arguments <#command-line-arguments>`__
4.  `Good Programming Practices <#good-programming-practices>`__
5.  `Java Language Features <#java-language-features>`__
6.  `Keywords <#keywords>`__
7.  `Data Types and Variables <#data-types-and-variables>`__
8.  `Operators <#operators>`__
9.  `Advanced Examples <#advanced-examples>`__
10. `Quiz Solutions <#quiz-solutions>`__

--------------

Environment Setup
-----------------

PATH Configuration
~~~~~~~~~~~~~~~~~~

**PATH** is an environmental variable that tells the operating system
which directories to search for executable files when commands are
issued by a user.

Setting PATH on Windows:
^^^^^^^^^^^^^^^^^^^^^^^^

1. Right-click “My Computer” → Properties
2. Select “Advanced” tab → Environment Variables
3. Find “Path” in System Variables → Edit
4. Add your JDK bin directory: ``C:\Program Files\Java\jdk-11.0.x\bin;``
5. Click OK to save

Setting PATH on Linux/Mac:
^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code:: bash

   # Add to ~/.bashrc or ~/.zshrc
   export PATH=$PATH:/usr/lib/jvm/java-11-openjdk/bin

   # For temporary session
   export PATH=$PATH:/path/to/your/jdk/bin

Verification:
^^^^^^^^^^^^^

.. code:: bash

   # Check if Java compiler is accessible
   javac -version

   # Check if Java runtime is accessible
   java -version

CLASSPATH Configuration
~~~~~~~~~~~~~~~~~~~~~~~

**CLASSPATH** tells the JVM or compiler where to locate classes that are
not part of the Java Development Toolkit (JDK).

Setting CLASSPATH:
^^^^^^^^^^^^^^^^^^

**Windows:** 1. Right-click “My Computer” → Properties → Advanced →
Environment Variables 2. Click “New” under System Variables 3. Variable
Name: ``CLASSPATH`` 4. Variable Value: ``.`` (dot for current directory)

**Linux/Mac:**

.. code:: bash

   # Add to ~/.bashrc or ~/.zshrc
   export CLASSPATH=.:$CLASSPATH

   # Include specific JAR files
   export CLASSPATH=.:lib/mylib.jar:$CLASSPATH

Command Line CLASSPATH:
^^^^^^^^^^^^^^^^^^^^^^^

.. code:: bash

   # Temporary classpath for current execution
   javac -cp .:lib/somelib.jar MyClass.java
   java -cp .:lib/somelib.jar MyClass

   # Multiple paths
   java -cp ".:lib/*:config/" MyClass

--------------

Your First Java Program
-----------------------

Basic Structure
~~~~~~~~~~~~~~~

Every Java application starts with a class containing a main method:

.. code:: java

   public class Welcome {
       public static void main(String[] args) {
           System.out.println("Welcome to Java Programming!");
       }
   }

Compilation and Execution Process
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: bash

   # 1. Create source file: Welcome.java
   # 2. Compile the source code
   javac Welcome.java

   # 3. Execute the compiled bytecode
   java Welcome

Multiple Classes in One File
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   // File: Sample.java
   class A {
       void methodA() {
           System.out.println("Method in class A");
       }
   }

   class B {
       void methodB() {
           System.out.println("Method in class B");
       }
   }

   class C {
       public static void main(String[] args) {
           A a = new A();
           B b = new B();
           a.methodA();
           b.methodB();
       }
   }

**Result:** Compiling ``Sample.java`` creates three ``.class`` files:
``A.class``, ``B.class``, and ``C.class``.

Common Compilation Errors
~~~~~~~~~~~~~~~~~~~~~~~~~

Missing String[] args:
^^^^^^^^^^^^^^^^^^^^^^

.. code:: java

   // This will cause a runtime error
   class Sample {
       public static void main() {  // Missing String[] args
           System.out.println("Welcome");
       }
   }

**Error:** ``Error: Main method not found in class Sample``

Correct Version:
^^^^^^^^^^^^^^^^

.. code:: java

   class Sample {
       public static void main(String[] args) {
           System.out.println("Welcome");
       }
   }

--------------

Command Line Arguments
----------------------

Basic Command Line Argument Handling
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   class ArgumentDemo {
       public static void main(String[] args) {
           System.out.println("Number of arguments: " + args.length);
           
           if (args.length > 0) {
               System.out.println("First argument: " + args[0]);
           }
           
           // Display all arguments
           for (int i = 0; i < args.length; i++) {
               System.out.println("Argument " + i + ": " + args[i]);
           }
       }
   }

**Execution:**

.. code:: bash

   java ArgumentDemo Hello World Java

**Output:**

::

   Number of arguments: 3
   First argument: Hello
   Argument 0: Hello
   Argument 1: World
   Argument 2: Java

Numeric Command Line Arguments
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   class Calculator {
       public static void main(String[] args) {
           if (args.length < 3) {
               System.out.println("Usage: java Calculator <num1> <operator> <num2>");
               return;
           }
           
           try {
               double num1 = Double.parseDouble(args[0]);
               String operator = args[1];
               double num2 = Double.parseDouble(args[2]);
               double result = 0;
               
               switch (operator) {
                   case "+":
                       result = num1 + num2;
                       break;
                   case "-":
                       result = num1 - num2;
                       break;
                   case "*":
                       result = num1 * num2;
                       break;
                   case "/":
                       if (num2 != 0) {
                           result = num1 / num2;
                       } else {
                           System.out.println("Division by zero!");
                           return;
                       }
                       break;
                   default:
                       System.out.println("Invalid operator: " + operator);
                       return;
               }
               
               System.out.println(num1 + " " + operator + " " + num2 + " = " + result);
               
           } catch (NumberFormatException e) {
               System.out.println("Invalid number format!");
           }
       }
   }

**Execution:**

.. code:: bash

   java Calculator 15.5 * 2.5
   # Output: 15.5 * 2.5 = 38.75

Advanced Argument Processing
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   import java.util.*;

   class ArgumentProcessor {
       public static void main(String[] args) {
           if (args.length == 0) {
               System.out.println("No arguments provided. Length = 0");
               return;
           }
           
           Map<String, String> options = new HashMap<>();
           List<String> positionalArgs = new ArrayList<>();
           
           for (int i = 0; i < args.length; i++) {
               if (args[i].startsWith("-")) {
                   if (i + 1 < args.length && !args[i + 1].startsWith("-")) {
                       options.put(args[i], args[i + 1]);
                       i++; // Skip next argument as it's the value
                   } else {
                       options.put(args[i], "true");
                   }
               } else {
                   positionalArgs.add(args[i]);
               }
           }
           
           System.out.println("Options: " + options);
           System.out.println("Positional arguments: " + positionalArgs);
       }
   }

--------------

Good Programming Practices
--------------------------

Naming Conventions
~~~~~~~~~~~~~~~~~~

Class Names
^^^^^^^^^^^

.. code:: java

   // Good examples
   public class Student { }
   public class BankAccount { }
   public class DatabaseConnection { }

   // Poor examples
   public class student { }           // Should start with uppercase
   public class Bank_Account { }      // Avoid underscores
   public class DBConn { }           // Too abbreviated

Variable Names
^^^^^^^^^^^^^^

.. code:: java

   public class NamingExample {
       // Good variable names
       private String firstName;
       private int accountBalance;
       private boolean isActive;
       private List<String> studentNames;
       
       // Poor variable names
       private String fn;           // Too abbreviated
       private int $balance;        // Avoid $ prefix
       private boolean _isActive;   // Avoid _ prefix
       private List<String> list1;  // Not descriptive
       
       public void demonstrateVariables() {
           // Good local variables
           int totalScore = 0;
           String userInput = "";
           
           // Poor local variables
           int x, y, z;           // Not descriptive
           String s1, s2;         // Not meaningful
       }
   }

Method Names
^^^^^^^^^^^^

.. code:: java

   public class MethodNaming {
       // Good method names (verbs, camelCase)
       public void calculateTotal() { }
       public String getUserName() { }
       public void setAccountBalance(double balance) { }
       public boolean isValidEmail(String email) { return true; }
       
       // Poor method names
       public void Calculate() { }        // Should be lowercase first letter
       public String user_name() { }      // Avoid underscores
       public void process() { }          // Too generic
   }

Comments and Documentation
~~~~~~~~~~~~~~~~~~~~~~~~~~

Block Comments
^^^^^^^^^^^^^^

.. code:: java

   /**
    * This class represents a bank account with basic operations.
    * It provides methods for deposits, withdrawals, and balance inquiry.
    * 
    * @author John Doe
    * @version 1.0
    * @since 2024-01-01
    */
   public class BankAccount {
       private double balance;
       
       /**
        * Creates a new bank account with the specified initial balance.
        * 
        * @param initialBalance the starting balance for the account
        * @throws IllegalArgumentException if initialBalance is negative
        */
       public BankAccount(double initialBalance) {
           if (initialBalance < 0) {
               throw new IllegalArgumentException("Initial balance cannot be negative");
           }
           this.balance = initialBalance;
       }
       
       /*
        * Block comment explaining complex algorithm:
        * This method uses a compound interest formula to calculate
        * the projected balance after a specified period.
        */
       public double calculateProjectedBalance(double interestRate, int years) {
           return balance * Math.pow(1 + interestRate, years);
       }
   }

Single Line Comments
^^^^^^^^^^^^^^^^^^^^

.. code:: java

   public class CommentExample {
       public void processData() {
           // Initialize counters
           int processedItems = 0;
           int errorCount = 0;
           
           // TODO: Implement error handling logic
           // FIXME: This method needs optimization for large datasets
           
           // Process each item in the collection
           for (Data item : dataCollection) {
               if (item.isValid()) {
                   processItem(item);  // Process valid items
                   processedItems++;
               } else {
                   errorCount++;       // Count invalid items
               }
           }
           
           // Log processing results
           System.out.println("Processed: " + processedItems + ", Errors: " + errorCount);
       }
   }

Declaration Best Practices
~~~~~~~~~~~~~~~~~~~~~~~~~~

One Declaration Per Line
^^^^^^^^^^^^^^^^^^^^^^^^

.. code:: java

   public class DeclarationExample {
       // Preferred: One declaration per line
       private int width;
       private int height;
       private int depth;
       
       // Not recommended: Multiple declarations on one line
       private int width, height, depth;
       
       // Never mix types on same line
       // private int width, height[];  // DON'T DO THIS
       
       // Proper array declarations
       private int[] coordinates;
       private String[] names;
       
       public void methodExample() {
           // Good: Clear, separate declarations
           String firstName = "John";
           String lastName = "Doe";
           int age = 25;
           
           // Poor: Confusing multiple declarations
           // String firstName = "John", lastName = "Doe";
       }
   }

--------------

Java Language Features
----------------------

Java Buzzwords and Characteristics
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Object-Oriented Programming
^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code:: java

   // Encapsulation example
   class Student {
       private String name;        // Private field
       private int age;           // Private field
       
       // Public getter and setter methods
       public String getName() {
           return name;
       }
       
       public void setName(String name) {
           if (name != null && !name.trim().isEmpty()) {
               this.name = name;
           }
       }
       
       public int getAge() {
           return age;
       }
       
       public void setAge(int age) {
           if (age >= 0 && age <= 120) {
               this.age = age;
           }
       }
   }

   // Inheritance example
   class GraduateStudent extends Student {
       private String researchTopic;
       
       public void conductResearch() {
           System.out.println("Researching: " + researchTopic);
       }
   }

Platform Independence
^^^^^^^^^^^^^^^^^^^^^

.. code:: java

   // This code runs on any platform with JVM
   import java.io.File;

   public class PlatformIndependentExample {
       public static void main(String[] args) {
           // File separator is automatically handled
           String path = "data" + File.separator + "files" + File.separator + "document.txt";
           System.out.println("Path: " + path);
           
           // System properties work across platforms
           System.out.println("OS: " + System.getProperty("os.name"));
           System.out.println("Java Version: " + System.getProperty("java.version"));
           System.out.println("User Home: " + System.getProperty("user.home"));
       }
   }

Multithreading
^^^^^^^^^^^^^^

.. code:: java

   // Simple multithreading example
   class CounterThread extends Thread {
       private String threadName;
       
       public CounterThread(String name) {
           this.threadName = name;
       }
       
       @Override
       public void run() {
           for (int i = 1; i <= 5; i++) {
               System.out.println(threadName + ": " + i);
               try {
                   Thread.sleep(1000); // Sleep for 1 second
               } catch (InterruptedException e) {
                   System.out.println(threadName + " interrupted");
               }
           }
       }
   }

   public class MultiThreadExample {
       public static void main(String[] args) {
           CounterThread thread1 = new CounterThread("Thread-1");
           CounterThread thread2 = new CounterThread("Thread-2");
           
           thread1.start();
           thread2.start();
       }
   }

--------------

Keywords
--------

Java Reserved Keywords
~~~~~~~~~~~~~~~~~~~~~~

Java has **50 reserved keywords** that cannot be used as identifiers:

.. code:: java

   // All Java keywords (cannot be used as variable/method/class names)
   /*
   abstract    continue    for          new         switch
   assert      default     goto*        package     synchronized
   boolean     do          if           private     this
   break       double      implements   protected   throw
   byte        else        import       public      throws
   case        enum        instanceof   return      transient
   catch       extends     int          short       try
   char        final       interface    static      void
   class       finally     long         strictfp    volatile
   const*      float       native       super       while
   */

*Note: ``goto`` and ``const`` are reserved but not used.*

Keyword Usage Examples
~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   // Access modifiers
   public class KeywordDemo {
       private int privateField;
       protected int protectedField;
       public int publicField;
       static int staticField;
       final int CONSTANT = 100;
       
       // Control flow keywords
       public void controlFlowExample(int value) {
           if (value > 0) {
               System.out.println("Positive");
           } else if (value < 0) {
               System.out.println("Negative");
           } else {
               System.out.println("Zero");
           }
           
           switch (value) {
               case 1:
                   System.out.println("One");
                   break;
               case 2:
                   System.out.println("Two");
                   break;
               default:
                   System.out.println("Other");
           }
           
           // Loop keywords
           for (int i = 0; i < 5; i++) {
               if (i == 3) continue;
               if (i == 4) break;
               System.out.println(i);
           }
           
           int j = 0;
           while (j < 3) {
               System.out.println("While: " + j);
               j++;
           }
           
           do {
               System.out.println("Do-while: " + j);
               j++;
           } while (j < 5);
       }
       
       // Exception handling keywords
       public void exceptionExample() {
           try {
               int result = 10 / 0;
           } catch (ArithmeticException e) {
               System.out.println("Division by zero!");
           } finally {
               System.out.println("Finally block executed");
           }
       }
   }

   // Inheritance keywords
   abstract class Animal {
       abstract void makeSound();
       
       final void sleep() {
           System.out.println("Animal is sleeping");
       }
   }

   class Dog extends Animal {
       @Override
       void makeSound() {
           System.out.println("Woof!");
       }
   }

   // Interface keywords
   interface Flyable {
       void fly();
   }

   class Bird implements Flyable {
       @Override
       public void fly() {
           System.out.println("Bird is flying");
       }
   }

Invalid Keyword Usage
~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   // These will cause compilation errors:

   class Test {
       public static void main(String[] args) {
           // int for = 2;        // ERROR: 'for' is a keyword
           // int class = 5;      // ERROR: 'class' is a keyword
           // String if = "test"; // ERROR: 'if' is a keyword
           
           // Correct usage:
           int forLoop = 2;       // OK
           String className = ""; // OK
           boolean ifCondition;   // OK
       }
   }

--------------

Data Types and Variables
------------------------

Primitive Data Types
~~~~~~~~~~~~~~~~~~~~

Java has **8 primitive data types**:

+------+---------------+-------------+-------------+------------------+
| Type | Size (bits)   | Min Value   | Max Value   | Default Value    |
+======+===============+=============+=============+==================+
| ``by | 8             | -128        | 127         | 0                |
| te`` |               |             |             |                  |
+------+---------------+-------------+-------------+------------------+
| `    | 16            | -32,768     | 32,767      | 0                |
| `sho |               |             |             |                  |
| rt`` |               |             |             |                  |
+------+---------------+-------------+-------------+------------------+
| ``i  | 32            | -2,         | 2,          | 0                |
| nt`` |               | 147,483,648 | 147,483,647 |                  |
+------+---------------+-------------+-------------+------------------+
| ``lo | 64            | -9,2        | 9,2         | 0L               |
| ng`` |               | 23,372,036, | 23,372,036, |                  |
|      |               | 854,775,808 | 854,775,807 |                  |
+------+---------------+-------------+-------------+------------------+
| `    | 32            | 1.4E-45     | 3           | 0.0f             |
| `flo |               |             | .4028235E38 |                  |
| at`` |               |             |             |                  |
+------+---------------+-------------+-------------+------------------+
| ``   | 64            | 4.9E-324    | 1.797693134 | 0.0d             |
| doub |               |             | 8623157E308 |                  |
| le`` |               |             |             |                  |
+------+---------------+-------------+-------------+------------------+
| ``ch | 16            | 0           | 65,535      | ‘:raw            |
| ar`` |               | (           | (           | -latex:`\u0`000’ |
|      |               | ‘:raw-latex | ‘:raw-latex |                  |
|      |               | :`\u0`000’) | :`\uffff`’) |                  |
+------+---------------+-------------+-------------+------------------+
| ``b  | 1             | -           | -           | false            |
| oole |               |             |             |                  |
| an`` |               |             |             |                  |
+------+---------------+-------------+-------------+------------------+

Data Type Examples
~~~~~~~~~~~~~~~~~~

.. code:: java

   public class DataTypeDemo {
       public static void main(String[] args) {
           // Integer types
           byte byteVar = 127;              // Max byte value
           short shortVar = 32767;          // Max short value
           int intVar = 2147483647;         // Max int value
           long longVar = 9223372036854775807L; // Max long value (note 'L')
           
           // Floating point types
           float floatVar = 3.14159f;       // Note 'f' suffix
           double doubleVar = 3.14159265359; // Default for decimals
           
           // Character type
           char charVar1 = 'A';             // Character literal
           char charVar2 = 65;              // ASCII value
           char charVar3 = '\u0041';        // Unicode
           
           // Boolean type
           boolean boolVar = true;
           
           System.out.println("Byte: " + byteVar);
           System.out.println("Short: " + shortVar);
           System.out.println("Int: " + intVar);
           System.out.println("Long: " + longVar);
           System.out.println("Float: " + floatVar);
           System.out.println("Double: " + doubleVar);
           System.out.println("Char1: " + charVar1);
           System.out.println("Char2: " + charVar2);
           System.out.println("Char3: " + charVar3);
           System.out.println("Boolean: " + boolVar);
       }
   }

Number System Representations
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   public class NumberSystems {
       public static void main(String[] args) {
           // Decimal (base 10) - default
           int decimal = 26;
           
           // Binary (base 2) - prefix with 0b or 0B
           int binary = 0b11010;    // 26 in binary
           
           // Octal (base 8) - prefix with 0
           int octal = 032;         // 26 in octal
           
           // Hexadecimal (base 16) - prefix with 0x or 0X
           int hex = 0x1A;          // 26 in hexadecimal
           
           System.out.println("Decimal: " + decimal);
           System.out.println("Binary: " + binary);
           System.out.println("Octal: " + octal);
           System.out.println("Hexadecimal: " + hex);
           
           // All print: 26
       }
   }

Type Conversion and Casting
~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   public class TypeConversion {
       public static void main(String[] args) {
           // Implicit conversion (widening)
           int intVal = 100;
           long longVal = intVal;       // int to long
           float floatVal = longVal;    // long to float
           double doubleVal = floatVal; // float to double
           
           System.out.println("Implicit conversions:");
           System.out.println("int: " + intVal);
           System.out.println("long: " + longVal);
           System.out.println("float: " + floatVal);
           System.out.println("double: " + doubleVal);
           
           // Explicit conversion (narrowing) - requires casting
           double d = 123.456;
           long l = (long) d;        // 123 (decimal part lost)
           int i = (int) l;          // 123
           short s = (short) i;      // 123
           byte b = (byte) s;        // 123
           
           System.out.println("\nExplicit conversions:");
           System.out.println("double: " + d);
           System.out.println("long: " + l);
           System.out.println("int: " + i);
           System.out.println("short: " + s);
           System.out.println("byte: " + b);
           
           // Overflow example
           byte maxByte = 127;
           // byte overflow = 128;  // Compilation error
           byte overflow = (byte) 128;  // -128 (wraps around)
           System.out.println("Overflow: " + overflow);
       }
   }

Variable Types
~~~~~~~~~~~~~~

Local Variables
^^^^^^^^^^^^^^^

.. code:: java

   public class LocalVariableExample {
       public void method() {
           int localVar;           // Declaration
           // System.out.println(localVar); // ERROR: Must initialize before use
           
           localVar = 10;          // Initialization
           System.out.println(localVar); // OK: Now initialized
           
           if (true) {
               int blockVar = 20;  // Block-scoped variable
               System.out.println(blockVar);
           }
           // System.out.println(blockVar); // ERROR: Out of scope
       }
   }

Instance Variables
^^^^^^^^^^^^^^^^^^

.. code:: java

   public class InstanceVariableExample {
       // Instance variables (non-static fields)
       private int instanceInt;        // Default: 0
       private String instanceString;  // Default: null
       private boolean instanceBoolean; // Default: false
       
       public void displayValues() {
           System.out.println("Int: " + instanceInt);
           System.out.println("String: " + instanceString);
           System.out.println("Boolean: " + instanceBoolean);
       }
       
       public static void main(String[] args) {
           InstanceVariableExample obj = new InstanceVariableExample();
           obj.displayValues(); // Shows default values
       }
   }

Static Variables
^^^^^^^^^^^^^^^^

.. code:: java

   public class StaticVariableExample {
       // Static variable (class variable)
       private static int instanceCount = 0;
       public static final String COMPANY_NAME = "TechCorp"; // Static constant
       
       private String name;
       
       public StaticVariableExample(String name) {
           this.name = name;
           instanceCount++; // Increment for each new instance
       }
       
       public static int getInstanceCount() {
           return instanceCount;
       }
       
       public static void main(String[] args) {
           System.out.println("Initial count: " + getInstanceCount());
           
           StaticVariableExample obj1 = new StaticVariableExample("Object 1");
           StaticVariableExample obj2 = new StaticVariableExample("Object 2");
           
           System.out.println("Final count: " + getInstanceCount());
           System.out.println("Company: " + COMPANY_NAME);
       }
   }

--------------

Operators
---------

Arithmetic Operators
~~~~~~~~~~~~~~~~~~~~

.. code:: java

   public class ArithmeticOperators {
       public static void main(String[] args) {
           int a = 15, b = 4;
           
           // Basic arithmetic operations
           System.out.println("a + b = " + (a + b));  // Addition: 19
           System.out.println("a - b = " + (a - b));  // Subtraction: 11
           System.out.println("a * b = " + (a * b));  // Multiplication: 60
           System.out.println("a / b = " + (a / b));  // Integer division: 3
           System.out.println("a % b = " + (a % b));  // Modulus: 3
           
           // Floating point division
           double c = 15.0, d = 4.0;
           System.out.println("c / d = " + (c / d));  // 3.75
           
           // Mixed operations
           System.out.println("a + b * 2 = " + (a + b * 2)); // 23 (multiplication first)
           System.out.println("(a + b) * 2 = " + ((a + b) * 2)); // 38
           
           // String concatenation with +
           String str1 = "Java";
           String str2 = "Programming";
           System.out.println(str1 + " " + str2); // "Java Programming"
           
           // Be careful with operator precedence
           System.out.println("Result: " + a + b);    // "Result: 154" (string concat)
           System.out.println("Result: " + (a + b));  // "Result: 19" (arithmetic first)
       }
   }

Unary Operators
~~~~~~~~~~~~~~~

.. code:: java

   public class UnaryOperators {
       public static void main(String[] args) {
           int x = 10;
           int y = -5;
           
           // Unary plus and minus
           System.out.println("x = " + x);       // 10
           System.out.println("+x = " + (+x));   // 10
           System.out.println("-x = " + (-x));   // -10
           System.out.println("-y = " + (-y));   // 5
           
           // Pre-increment and post-increment
           int a = 5;
           System.out.println("a = " + a);           // 5
           System.out.println("++a = " + (++a));     // 6 (increment first, then use)
           System.out.println("a after ++a = " + a); // 6
           
           int b = 5;
           System.out.println("b++ = " + (b++));     // 5 (use first, then increment)
           System.out.println("b after b++ = " + b); // 6
           
           // Pre-decrement and post-decrement
           int c = 5;
           System.out.println("--c = " + (--c));     // 4 (decrement first, then use)
           System.out.println("c-- = " + (c--));     // 4 (use first, then decrement)
           System.out.println("c after c-- = " + c); // 3
           
           // Complex expressions
           int p = 10, q = 5;
           int result = ++p + q++;  // 11 + 5 = 16
           System.out.println("++p + q++ = " + result); // 16
           System.out.println("p = " + p + ", q = " + q); // p = 11, q = 6
           
           // Logical NOT
           boolean flag = true;
           System.out.println("flag = " + flag);     // true
           System.out.println("!flag = " + (!flag)); // false
       }
   }

Relational Operators
~~~~~~~~~~~~~~~~~~~~

.. code:: java

   public class RelationalOperators {
       public static void main(String[] args) {
           int a = 10, b = 20;
           
           System.out.println("a = " + a + ", b = " + b);
           System.out.println("a == b: " + (a == b)); // false
           System.out.println("a != b: " + (a != b)); // true
           System.out.println("a > b: " + (a > b));   // false
           System.out.println("a < b: " + (a < b));   // true
           System.out.println("a >= b: " + (a >= b)); // false
           System.out.println("a <= b: " + (a <= b)); // true
           
           // String comparison (reference vs content)
           String str1 = new String("Hello");
           String str2 = new String("Hello");
           String str3 = "Hello";
           String str4 = "Hello";
           
           System.out.println("\nString Comparisons:");
           System.out.println("str1 == str2: " + (str1 == str2));         // false (different objects)
           System.out.println("str1.equals(str2): " + str1.equals(str2)); // true (same content)
           System.out.println("str3 == str4: " + (str3 == str4));         // true (string pool)
           System.out.println("str3.equals(str4): " + str3.equals(str4)); // true (same content)
           
           // Comparing with null
           String nullStr = null;
           System.out.println("nullStr == null: " + (nullStr == null)); // true
           // System.out.println("nullStr.equals(\"test\"): " + nullStr.equals("test")); // NullPointerException
           System.out.println("\"test\".equals(nullStr): " + "test".equals(nullStr)); // false (safe)
           
           // Numeric comparisons with different types
           int intVal = 42;
           double doubleVal = 42.0;
           System.out.println("intVal == doubleVal: " + (intVal == doubleVal)); // true (automatic conversion)
           
           // Character comparisons (ASCII values)
           char char1 = 'A';
           char char2 = 'B';
           System.out.println("'A' < 'B': " + (char1 < char2)); // true (65 < 66)
       }
   }

Logical Operators
~~~~~~~~~~~~~~~~~

.. code:: java

   public class LogicalOperators {
       public static void main(String[] args) {
           boolean a = true;
           boolean b = false;
           
           // Basic logical operations
           System.out.println("a = " + a + ", b = " + b);
           System.out.println("a && b = " + (a && b)); // false (AND)
           System.out.println("a || b = " + (a || b)); // true (OR)
           System.out.println("!a = " + (!a));         // false (NOT)
           System.out.println("!b = " + (!b));         // true (NOT)
           
           // Truth table demonstration
           System.out.println("\nTruth Table for AND (&&):");
           System.out.println("true && true = " + (true && true));   // true
           System.out.println("true && false = " + (true && false)); // false
           System.out.println("false && true = " + (false && true)); // false
           System.out.println("false && false = " + (false && false)); // false
           
           System.out.println("\nTruth Table for OR (||):");
           System.out.println("true || true = " + (true || true));   // true
           System.out.println("true || false = " + (true || false)); // true
           System.out.println("false || true = " + (false || true)); // true
           System.out.println("false || false = " + (false || false)); // false
           
           // Short-circuit evaluation
           int x = 5, y = 10;
           System.out.println("\nShort-circuit evaluation:");
           if (x < 10 && ++y > 10) {  // ++y is evaluated because x < 10 is true
               System.out.println("Condition true");
           }
           System.out.println("y after && = " + y); // y = 11
           
           y = 10; // Reset
           if (x > 10 && ++y > 10) {  // ++y is NOT evaluated because x > 10 is false
               System.out.println("Condition true");
           }
           System.out.println("y after && (short-circuit) = " + y); // y = 10
           
           // Complex logical expressions
           int age = 25;
           boolean hasLicense = true;
           boolean hasInsurance = false;
           
           boolean canDrive = age >= 18 && hasLicense && hasInsurance;
           System.out.println("\nCan drive: " + canDrive); // false
           
           boolean canRentCar = age >= 21 && hasLicense;
           System.out.println("Can rent car: " + canRentCar); // true
       }
   }

Assignment Operators
~~~~~~~~~~~~~~~~~~~~

.. code:: java

   public class AssignmentOperators {
       public static void main(String[] args) {
           // Simple assignment
           int a = 10;
           System.out.println("a = " + a); // 10
           
           // Compound assignment operators
           a += 5;  // a = a + 5
           System.out.println("a += 5: " + a); // 15
           
           a -= 3;  // a = a - 3
           System.out.println("a -= 3: " + a); // 12
           
           a *= 2;  // a = a * 2
           System.out.println("a *= 2: " + a); // 24
           
           a /= 4;  // a = a / 4
           System.out.println("a /= 4: " + a); // 6
           
           a %= 4;  // a = a % 4
           System.out.println("a %= 4: " + a); // 2
           
           // String concatenation assignment
           String str = "Hello";
           str += " World";
           str += "!";
           System.out.println("String: " + str); // "Hello World!"
           
           // Multiple assignments
           int x, y, z;
           x = y = z = 5;  // All assigned 5
           System.out.println("x = " + x + ", y = " + y + ", z = " + z);
           
           // Bitwise assignment operators
           int bits = 12; // Binary: 1100
           System.out.println("\nBitwise assignments:");
           System.out.println("bits = " + bits + " (binary: " + Integer.toBinaryString(bits) + ")");
           
           bits &= 10; // bits = bits & 10 (1100 & 1010 = 1000 = 8)
           System.out.println("bits &= 10: " + bits + " (binary: " + Integer.toBinaryString(bits) + ")");
           
           bits |= 5;  // bits = bits | 5 (1000 | 0101 = 1101 = 13)
           System.out.println("bits |= 5: " + bits + " (binary: " + Integer.toBinaryString(bits) + ")");
           
           bits ^= 3;  // bits = bits ^ 3 (1101 ^ 0011 = 1110 = 14)
           System.out.println("bits ^= 3: " + bits + " (binary: " + Integer.toBinaryString(bits) + ")");
           
           bits <<= 1; // bits = bits << 1 (left shift by 1: 1110 -> 11100 = 28)
           System.out.println("bits <<= 1: " + bits + " (binary: " + Integer.toBinaryString(bits) + ")");
           
           bits >>= 2; // bits = bits >> 2 (right shift by 2: 11100 -> 111 = 7)
           System.out.println("bits >>= 2: " + bits + " (binary: " + Integer.toBinaryString(bits) + ")");
       }
   }

Bitwise Operators
~~~~~~~~~~~~~~~~~

.. code:: java

   public class BitwiseOperators {
       public static void main(String[] args) {
           int a = 12; // Binary: 1100
           int b = 10; // Binary: 1010
           
           System.out.println("a = " + a + " (binary: " + Integer.toBinaryString(a) + ")");
           System.out.println("b = " + b + " (binary: " + Integer.toBinaryString(b) + ")");
           
           // Bitwise AND (&)
           int andResult = a & b; // 1100 & 1010 = 1000 (8)
           System.out.println("a & b = " + andResult + " (binary: " + Integer.toBinaryString(andResult) + ")");
           
           // Bitwise OR (|)
           int orResult = a | b; // 1100 | 1010 = 1110 (14)
           System.out.println("a | b = " + orResult + " (binary: " + Integer.toBinaryString(orResult) + ")");
           
           // Bitwise XOR (^)
           int xorResult = a ^ b; // 1100 ^ 1010 = 0110 (6)
           System.out.println("a ^ b = " + xorResult + " (binary: " + Integer.toBinaryString(xorResult) + ")");
           
           // Bitwise NOT (~)
           int notA = ~a; // ~1100 = ...11110011 (-13 in two's complement)
           System.out.println("~a = " + notA);
           
           // Left shift (<<)
           int leftShift = a << 2; // 1100 << 2 = 110000 (48)
           System.out.println("a << 2 = " + leftShift + " (binary: " + Integer.toBinaryString(leftShift) + ")");
           
           // Right shift (>>)
           int rightShift = a >> 2; // 1100 >> 2 = 11 (3)
           System.out.println("a >> 2 = " + rightShift + " (binary: " + Integer.toBinaryString(rightShift) + ")");
           
           // Unsigned right shift (>>>)
           int negativeNum = -8;
           System.out.println("\nNegative number operations:");
           System.out.println("negativeNum = " + negativeNum + " (binary: " + Integer.toBinaryString(negativeNum) + ")");
           System.out.println("negativeNum >> 1 = " + (negativeNum >> 1)); // Sign-extended
           System.out.println("negativeNum >>> 1 = " + (negativeNum >>> 1)); // Zero-filled
           
           // Practical bitwise operations
           System.out.println("\nPractical bitwise examples:");
           
           // Check if number is even or odd
           int num = 17;
           if ((num & 1) == 0) {
               System.out.println(num + " is even");
           } else {
               System.out.println(num + " is odd");
           }
           
           // Multiply by power of 2 using left shift
           System.out.println("5 * 8 = " + (5 << 3)); // 5 * 2^3 = 5 * 8 = 40
           
           // Divide by power of 2 using right shift
           System.out.println("40 / 4 = " + (40 >> 2)); // 40 / 2^2 = 40 / 4 = 10
           
           // Swap two numbers without temporary variable
           int x = 25, y = 30;
           System.out.println("Before swap: x = " + x + ", y = " + y);
           x = x ^ y;
           y = x ^ y;
           x = x ^ y;
           System.out.println("After swap: x = " + x + ", y = " + y);
       }
   }

Ternary Operator
~~~~~~~~~~~~~~~~

.. code:: java

   public class TernaryOperator {
       public static void main(String[] args) {
           // Basic ternary operator: condition ? value_if_true : value_if_false
           int a = 10, b = 20;
           int max = (a > b) ? a : b;
           System.out.println("Max of " + a + " and " + b + " is: " + max);
           
           // Ternary with different data types
           String result = (a > b) ? "a is greater" : "b is greater or equal";
           System.out.println(result);
           
           // Nested ternary operators
           int x = 15, y = 10, z = 20;
           int maximum = (x > y) ? ((x > z) ? x : z) : ((y > z) ? y : z);
           System.out.println("Max of " + x + ", " + y + ", " + z + " is: " + maximum);
           
           // Ternary in method calls
           int num = -5;
           System.out.println("Absolute value: " + ((num < 0) ? -num : num));
           
           // Ternary for assignment
           boolean isWeekend = true;
           String activity = isWeekend ? "Relax" : "Work";
           System.out.println("Activity: " + activity);
           
           // Ternary with method calls
           String str = null;
           int length = (str != null) ? str.length() : 0;
           System.out.println("String length: " + length);
           
           // Grade calculation example
           int score = 85;
           char grade = (score >= 90) ? 'A' : 
                       (score >= 80) ? 'B' : 
                       (score >= 70) ? 'C' : 
                       (score >= 60) ? 'D' : 'F';
           System.out.println("Score: " + score + ", Grade: " + grade);
       }
   }

Operator Precedence
~~~~~~~~~~~~~~~~~~~

.. code:: java

   public class OperatorPrecedence {
       public static void main(String[] args) {
           // Operator precedence demonstration
           System.out.println("Operator Precedence Examples:");
           
           // Arithmetic precedence: *, /, % before +, -
           int result1 = 2 + 3 * 4;        // 2 + 12 = 14
           int result2 = (2 + 3) * 4;      // 5 * 4 = 20
           System.out.println("2 + 3 * 4 = " + result1);
           System.out.println("(2 + 3) * 4 = " + result2);
           
           // Unary operators have higher precedence
           int a = 5;
           int result3 = -a + 2;           // -5 + 2 = -3
           int result4 = -(a + 2);         // -(5 + 2) = -7
           System.out.println("-a + 2 = " + result3);
           System.out.println("-(a + 2) = " + result4);
           
           // Comparison operators have lower precedence than arithmetic
           boolean result5 = 3 + 4 > 5 + 1;    // 7 > 6 = true
           boolean result6 = 3 + (4 > 5) ? true : false + 1; // Complex expression
           System.out.println("3 + 4 > 5 + 1 = " + result5);
           
           // Logical operators precedence: ! before && before ||
           boolean b1 = true, b2 = false, b3 = true;
           boolean result7 = !b1 && b2 || b3;     // false && false || true = true
           boolean result8 = !(b1 && b2 || b3);   // !(true && false || true) = false
           System.out.println("!b1 && b2 || b3 = " + result7);
           System.out.println("!(b1 && b2 || b3) = " + result8);
           
           // Assignment has lowest precedence
           int x = 0;
           x = 3 + 4 > 5 ? 10 : 20;        // x = (3 + 4 > 5) ? 10 : 20 = 10
           System.out.println("x = 3 + 4 > 5 ? 10 : 20; x = " + x);
           
           // Complete precedence table (high to low):
           System.out.println("\nOperator Precedence (High to Low):");
           System.out.println("1. () [] .");
           System.out.println("2. ++ -- ! ~ unary+ unary-");
           System.out.println("3. * / %");
           System.out.println("4. + -");
           System.out.println("5. << >> >>>");
           System.out.println("6. < <= > >= instanceof");
           System.out.println("7. == !=");
           System.out.println("8. &");
           System.out.println("9. ^");
           System.out.println("10. |");
           System.out.println("11. &&");
           System.out.println("12. ||");
           System.out.println("13. ?:");
           System.out.println("14. = += -= *= /= %= etc.");
       }
   }

--------------

Advanced Examples
-----------------

Complex Data Type Usage
~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   public class AdvancedDataTypes {
       public static void main(String[] args) {
           // Array examples
           int[] numbers = {10, 20, 30, 40, 50};
           char[] chars = {'J', 'a', 'v', 'a'};
           
           System.out.println("Array operations:");
           for (int i = 0; i < numbers.length; i++) {
               System.out.println("numbers[" + i + "] = " + numbers[i]);
           }
           
           // Enhanced for loop
           System.out.println("Characters:");
           for (char c : chars) {
               System.out.print(c + " ");
           }
           System.out.println();
           
           // Multi-dimensional arrays
           int[][] matrix = {
               {1, 2, 3},
               {4, 5, 6},
               {7, 8, 9}
           };
           
           System.out.println("Matrix:");
           for (int i = 0; i < matrix.length; i++) {
               for (int j = 0; j < matrix[i].length; j++) {
                   System.out.print(matrix[i][j] + " ");
               }
               System.out.println();
           }
           
           // String operations
           String text = "Java Programming";
           System.out.println("String operations:");
           System.out.println("Length: " + text.length());
           System.out.println("Uppercase: " + text.toUpperCase());
           System.out.println("Substring: " + text.substring(5));
           System.out.println("Contains 'Program': " + text.contains("Program"));
           
           // String comparison
           String str1 = "Hello";
           String str2 = "hello";
           System.out.println("Case-sensitive comparison: " + str1.equals(str2));
           System.out.println("Case-insensitive comparison: " + str1.equalsIgnoreCase(str2));
           
           // StringBuilder for efficient string operations
           StringBuilder sb = new StringBuilder();
           sb.append("Java");
           sb.append(" is");
           sb.append(" awesome!");
           System.out.println("StringBuilder result: " + sb.toString());
       }
   }

Comprehensive Operator Usage
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   public class OperatorShowcase {
       public static void main(String[] args) {
           // Combine multiple operator types
           int a = 15, b = 25, c = 10;
           
           // Complex arithmetic with precedence
           int result1 = a + b * c / 5 - 3; // 15 + (25 * 10 / 5) - 3 = 15 + 50 - 3 = 62
           System.out.println("Complex arithmetic: " + result1);
           
           // Bitwise operations for flags
           final int READ_PERMISSION = 1;    // 001
           final int WRITE_PERMISSION = 2;   // 010
           final int EXECUTE_PERMISSION = 4; // 100
           
           int userPermissions = READ_PERMISSION | WRITE_PERMISSION; // 011 (3)
           System.out.println("User has read permission: " + ((userPermissions & READ_PERMISSION) != 0));
           System.out.println("User has write permission: " + ((userPermissions & WRITE_PERMISSION) != 0));
           System.out.println("User has execute permission: " + ((userPermissions & EXECUTE_PERMISSION) != 0));
           
           // Conditional assignment with multiple conditions
           int age = 22;
           boolean hasJob = true;
           boolean hasGoodCredit = false;
           
           String loanEligibility = (age >= 18 && age <= 65) && hasJob && hasGoodCredit ? 
                                   "Eligible" : "Not Eligible";
           System.out.println("Loan eligibility: " + loanEligibility);
           
           // Complex increment operations
           int x = 10, y = 5;
           int complexResult = ++x * y-- + x++ - --y; // 11*5 + 11 - 3 = 55 + 11 - 3 = 63
           System.out.println("Complex increment result: " + complexResult);
           System.out.println("Final values: x=" + x + ", y=" + y);
           
           // Type casting in operations
           double pi = 3.14159;
           int roundedPi = (int) (pi + 0.5); // Manual rounding
           System.out.println("Rounded PI: " + roundedPi);
           
           // Character operations
           char letter = 'A';
           System.out.println("Letter: " + letter);
           System.out.println("ASCII value: " + (int) letter);
           System.out.println("Next letter: " + (char) (letter + 1));
           
           // Boolean operations with short-circuiting
           boolean result = checkCondition1() && checkCondition2() || checkCondition3();
           System.out.println("Complex boolean result: " + result);
       }
       
       private static boolean checkCondition1() {
           System.out.println("Checking condition 1");
           return false;
       }
       
       private static boolean checkCondition2() {
           System.out.println("Checking condition 2");
           return true;
       }
       
       private static boolean checkCondition3() {
           System.out.println("Checking condition 3");
           return true;
       }
   }

Real-World Application Example
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   import java.util.Scanner;

   public class StudentGradeCalculator {
       public static void main(String[] args) {
           Scanner scanner = new Scanner(System.in);
           
           System.out.println("=== Student Grade Calculator ===");
           
           // Get student information
           System.out.print("Enter student name: ");
           String studentName = scanner.nextLine();
           
           System.out.print("Enter number of subjects: ");
           int numSubjects = scanner.nextInt();
           
           if (numSubjects <= 0) {
               System.out.println("Invalid number of subjects!");
               return;
           }
           
           double[] scores = new double[numSubjects];
           double totalScore = 0;
           
           // Input scores
           for (int i = 0; i < numSubjects; i++) {
               System.out.print("Enter score for subject " + (i + 1) + ": ");
               scores[i] = scanner.nextDouble();
               
               // Validate score range
               if (scores[i] < 0 || scores[i] > 100) {
                   System.out.println("Invalid score! Please enter a value between 0 and 100.");
                   i--; // Repeat this iteration
                   continue;
               }
               
               totalScore += scores[i];
           }
           
           // Calculate average
           double average = totalScore / numSubjects;
           
           // Determine letter grade using multiple approaches
           char letterGrade;
           String gradeDescription;
           
           // Using if-else chain
           if (average >= 90) {
               letterGrade = 'A';
               gradeDescription = "Excellent";
           } else if (average >= 80) {
               letterGrade = 'B';
               gradeDescription = "Good";
           } else if (average >= 70) {
               letterGrade = 'C';
               gradeDescription = "Average";
           } else if (average >= 60) {
               letterGrade = 'D';
               gradeDescription = "Below Average";
           } else {
               letterGrade = 'F';
               gradeDescription = "Fail";
           }
           
           // Using ternary operator for pass/fail
           boolean passed = average >= 60 ? true : false;
           
           // Display results
           System.out.println("\n=== Grade Report ===");
           System.out.println("Student Name: " + studentName);
           System.out.println("Number of Subjects: " + numSubjects);
           
           System.out.println("\nIndividual Scores:");
           for (int i = 0; i < scores.length; i++) {
               System.out.printf("Subject %d: %.2f\n", (i + 1), scores[i]);
           }
           
           System.out.printf("\nTotal Score: %.2f\n", totalScore);
           System.out.printf("Average Score: %.2f\n", average);
           System.out.println("Letter Grade: " + letterGrade);
           System.out.println("Grade Description: " + gradeDescription);
           System.out.println("Status: " + (passed ? "PASSED" : "FAILED"));
           
           // Performance analysis using bitwise operations for categorization
           int performanceFlags = 0;
           final int EXCELLENT = 1;  // 001
           final int GOOD = 2;       // 010
           final int NEEDS_HELP = 4; // 100
           
           if (average >= 90) performanceFlags |= EXCELLENT;
           if (average >= 70) performanceFlags |= GOOD;
           if (average < 60) performanceFlags |= NEEDS_HELP;
           
           System.out.println("\nPerformance Analysis:");
           if ((performanceFlags & EXCELLENT) != 0) {
               System.out.println("- Excellent performance!");
           }
           if ((performanceFlags & GOOD) != 0) {
               System.out.println("- Good academic standing");
           }
           if ((performanceFlags & NEEDS_HELP) != 0) {
               System.out.println("- Needs academic assistance");
           }
           
           scanner.close();
       }
   }

--------------

Quiz Solutions
--------------

Quiz 1: Multiple Classes Compilation
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Question:** Sample.java file contains class A, B and C. How many
.class files will be created after compiling Sample.java?

**Answer:** **3 .class files** will be created: A.class, B.class, and
C.class

**Explanation:** Each class definition in Java, regardless of whether
it’s public or not, gets compiled into its own separate .class file.

Quiz 2: Missing String[] args
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Question:** What will be the result if you try to compile and execute
the following program?

.. code:: java

   class Sample {
       public static void main() {
           System.out.println("Welcome");
       }
   }

**Answer:** **b. Runtime Error**

**Explanation:** The program will compile successfully, but when you try
to run it, you’ll get a runtime error: “Error: Main method not found in
class Sample, please define the main method as: public static void
main(String[] args)”. The main method signature must include String[]
args.

Quiz 3: No Command Line Arguments
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Question:** What will be the result if you try to compile and execute
the following code without passing any command line argument?

.. code:: java

   class Sample {
       public static void main(String[] args) {
           int len = args.length;
           System.out.println(len);
       }
   }

**Answer:** **d. The program compiles and executes successfully & prints
0.**

**Explanation:** When no command line arguments are passed, args.length
returns 0.

Quiz 4: Using Keyword as Variable
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Question:** What will be the result if we try to compile and execute
the following code?

.. code:: java

   class Test {
       public static void main(String[] ar) {
           int for=2;
           System.out.println(for);
       }
   }

**Answer:** **Compilation Error**

**Explanation:** ‘for’ is a reserved keyword in Java and cannot be used
as a variable name.

Quiz 5: Byte Overflow
~~~~~~~~~~~~~~~~~~~~~

**Question:** What will be the result if we try to compile and execute
the following code?

.. code:: java

   class Test {
       public static void main(String[] ar) {
           byte b=128;
           System.out.println(b);
       }
   }

**Answer:** **Compilation Error**

**Explanation:** byte can only hold values from -128 to 127. 128 is
outside this range, causing a compilation error.

Quiz 6: Float and Boolean Assignment
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Question:** What will be the result if we try to compile and execute
the following code?

.. code:: java

   class Test {
       public static void main(String ar[]) {
           float f=1.2;
           boolean b=1;
           System.out.println(f);
           System.out.println(b);
       }
   }

**Answer:** **Compilation Error**

**Explanation:** Two errors: 1. float f=1.2; - should be float f=1.2f;
(1.2 is double by default) 2. boolean b=1; - boolean can only be true or
false, not numeric values

Quiz 7: Double with D suffix
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Question:** What will be the result if we try to compile and execute
the following code?

.. code:: java

   class Test {
       public static void main(String ar[]) {
           double d=1.2D;
           System.out.println(d);
       }
   }

**Answer:** **Compiles and runs successfully, prints: 1.2**

**Explanation:** The ‘D’ suffix explicitly makes it a double literal,
which is valid.

Quiz 8: Number Systems
~~~~~~~~~~~~~~~~~~~~~~

**Question:** What will be the result if we try to compile and execute
the following code?

.. code:: java

   class Test {
       public static void main(String[] ar) {
           int a=10,b=017,c=0X3A;
           System.out.println(a+","+b+","+c);
       }
   }

**Answer:** **Prints: 10,15,58**

**Explanation:** - a=10 (decimal) - b=017 (octal) = 1×8¹ + 7×8⁰ = 8 + 7
= 15 - c=0X3A (hexadecimal) = 3×16¹ + 10×16⁰ = 48 + 10 = 58

Quiz 9: Invalid Variable Name
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Question:** What will be the result if we try to compile and execute
the following code?

.. code:: java

   class Test {
       public static void main(String[] args) {
           int 9A=10;
           System.out.println(9A);
       }
   }

**Answer:** **Compilation Error**

**Explanation:** Variable names cannot start with a digit. Valid
identifiers must start with a letter, underscore, or dollar sign.

Quiz 10: Uninitialized Local Variable
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Question:** What will be the result if we try to compile and execute
the following code?

.. code:: java

   class Test {
       public static void main(String[] args) {
           int x;
           System.out.println(x);
       }
   }

**Answer:** **Compilation Error**

**Explanation:** Local variables must be initialized before use. Unlike
instance variables, local variables don’t have default values.

Quiz 11: Data Type Sizes
~~~~~~~~~~~~~~~~~~~~~~~~

**Question:** Match the following table:

========== ===========
DATA TYPES SIZE(bytes)
========== ===========
char       4
byte       2
int        1
double     8
========== ===========

| **Answer:** - char: 2 bytes - byte: 1 byte
| - int: 4 bytes - double: 8 bytes

Quiz 12: Pre-increment Operations
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Question:** What will be the result if we try to compile and execute
the following code?

.. code:: java

   class Test {
       public static void main(String[] args) {
           int x=10;
           int y=5;
           System.out.println(++x+(++y));
       }
   }

**Answer:** **Prints: 17**

**Explanation:** ++x increments x to 11, ++y increments y to 6, then 11
+ 6 = 17

Quiz 13: Missing String[] args in main
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Question:** What will be the output for the below code?

.. code:: java

   public class Sample {
       public static void main() {
           int i_val = 10, j_val = 20;
           boolean chk;
           chk = i_val < j_val;
           System.out.println("chk value: "+chk);
       }
   }

**Answer:** **Runtime Error**

**Explanation:** The main method is missing String[] args parameter. The
program will compile but fail at runtime with “Main method not found”
error.

--------------

Summary
-------

This comprehensive guide covers all fundamental aspects of Java language
basics:

Key Topics Covered:
~~~~~~~~~~~~~~~~~~~

1. **Environment Setup** - PATH and CLASSPATH configuration
2. **Program Structure** - Basic Java program anatomy and compilation
3. **Command Line Arguments** - Accessing and processing user input
4. **Programming Practices** - Naming conventions and documentation
5. **Language Features** - Java’s core characteristics and benefits
6. **Keywords** - All 50 reserved words and their usage
7. **Data Types** - Primitive types, ranges, and conversions
8. **Variables** - Local, instance, and static variables
9. **Operators** - Complete coverage of all operator types with examples

Best Practices Learned:
~~~~~~~~~~~~~~~~~~~~~~~

- Use descriptive naming conventions
- One declaration per line
- Proper commenting and documentation
- Understanding operator precedence
- Type safety and conversion rules
- Error handling and validation

Programming Skills Developed:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

- Writing and compiling Java programs
- Working with different data types
- Using operators effectively
- Processing command line arguments
- Understanding variable scope
- Applying good coding practices

This foundation prepares you for more advanced Java concepts like
object-oriented programming, exception handling, collections, and
advanced language features.

--------------

*Continue practicing with the provided examples and create your own
variations to solidify your understanding of Java language basics.*
