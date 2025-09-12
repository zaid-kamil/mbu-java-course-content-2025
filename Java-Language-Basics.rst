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

**Explanation:**

1. **Class Declaration**: `public class Welcome` - Defines a class named "Welcome"
2. **Main Method**: `public static void main(String[] args)` - The entry point of the program
   - `public`: Accessible from anywhere
   - `static`: Belongs to the class, not to objects of the class
   - `void`: Does not return any value
   - `main`: Special method name recognized by the JVM as the starting point
   - `String[] args`: Command line arguments passed to the program
3. **Statement**: `System.out.println("Welcome to Java Programming!");` - Prints the text to the console
   - `System`: A predefined class in the java.lang package
   - `out`: A static member of the System class, representing the standard output
   - `println()`: A method that prints the argument and adds a new line

Compilation and Execution Process in IntelliJ IDEA
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Creating and Running Your First Java Program:**

1. **Create a New Java Class**:
   - Right-click on your project's ``src`` folder
   - Select New → Java Class
   - Enter a name (e.g., "Welcome") and click OK
   - IntelliJ will create a basic class structure for you

2. **Write Your Code**:
   - Add a main method to make your class executable:

   .. code:: java

      public class Welcome {
          public static void main(String[] args) {
              System.out.println("Welcome to Java Programming!");
          }
      }

3. **Run Your Program**:
   - Click the green "Run" icon in the gutter next to your main method, or
   - Right-click anywhere in the editor and select "Run 'Welcome.main()'"
   - Use the keyboard shortcut: Shift+F10 (Windows/Linux) or Control+R (Mac)

**Output** (appears in the Run tool window at the bottom of the IDE):

::

   Welcome to Java Programming!

**What happens behind the scenes:**

1. **Compilation**: IntelliJ automatically compiles your Java source code
   - Converts your .java file into bytecode (.class files)
   - Performs real-time syntax checking and highlights errors as you type
   - Stores compiled files in the project's "out" or "target" directory

2. **Execution**: When you run the program, IntelliJ:
   - Creates a run configuration (if one doesn't exist)
   - Launches the JVM with the appropriate classpath
   - Loads your compiled class
   - Executes the main method

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

**Running in IntelliJ IDEA:**

1. Create a file named ``Sample.java`` with the code above
2. After typing the code, IntelliJ will recognize the class with the main method (class C)
3. Click the green "Run" icon next to the main method in class C
4. IntelliJ automatically compiles and runs the program

**Output:**

::

   Method in class A
   Method in class B

**Behind the Scenes:** When IntelliJ compiles ``Sample.java``, it creates three ``.class`` files:
``A.class``, ``B.class``, and ``C.class`` in the output directory.

**Key Points:**
- You can define multiple classes in a single .java file
- IntelliJ shows all classes in the Project view but distinguishes the class with the main method
- Only one class in the file can be public, and if present, its name must match the filename
- Only one class in the file can be declared as public
- The public class name must match the filename
- Each class is compiled into its own separate .class file
- To run the program, specify the class containing the main method

Common Compilation Errors
~~~~~~~~~~~~~~~~~~~~~~~~~

When writing your first Java programs, you might encounter several common errors. Understanding these errors will help you debug your code more efficiently.

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

**Explanation:** The JVM specifically looks for a method with the signature `public static void main(String[] args)`. If the parameter is missing, the JVM won't recognize it as the entry point, resulting in a runtime error.

Correct Version:
^^^^^^^^^^^^^^^^

.. code:: java

   class Sample {
       public static void main(String[] args) {
           System.out.println("Welcome");
       }
   }

**Other Common Errors:**

1. **Class Name Mismatch:**
   
   .. code:: java
   
      // Filename: Test.java
      public class Sample {
          public static void main(String[] args) {
              System.out.println("Hello");
          }
      }
   
   **Error:** ``class Sample is public, should be declared in a file named Sample.java``
   
   **Fix:** Either rename the file to Sample.java or change the class name to Test.

2. **Missing Semicolons:**
   
   .. code:: java
   
      public class Test {
          public static void main(String[] args) {
              System.out.println("Hello")  // Missing semicolon
              System.out.println("World");
          }
      }
   
   **Error:** ``; expected``

3. **Mismatched Braces:**
   
   .. code:: java
   
      public class Test {
          public static void main(String[] args) {
              System.out.println("Hello");
          // Missing closing brace
      }
   
   **Error:** ``reached end of file while parsing``

--------------

Command Line Arguments
----------------------

Understanding Command Line Arguments
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Command line arguments are values you can pass to your program when you run it. These are stored in the `String[] args` parameter of the main method.

.. code:: java

   class ArgumentDemo {
       public static void main(String[] args) {
           // Print the number of arguments provided
           System.out.println("Number of arguments: " + args.length);
           
           // Print the first argument (if any)
           if (args.length > 0) {
               System.out.println("First argument: " + args[0]);
           } else {
               System.out.println("No arguments provided");
           }
           
           // Print a message using the argument
           if (args.length > 0) {
               System.out.println("Hello, " + args[0] + "!");
           }
       }
   }

**Running with Command Line Arguments in IntelliJ IDEA:**

There are two ways to run a Java program with command line arguments in IntelliJ IDEA:

1. **Using a Temporary Run Configuration:**
   - Right-click on your Java class with the main method
   - Select "Modify Run Configuration"
   - In the "Program arguments" field, enter your arguments (e.g., "John")
   - Click "Run"

2. **Creating a Permanent Run Configuration:**
   - Go to Run → Edit Configurations
   - Find your class's run configuration or create a new one
   - In the "Program arguments" field, enter your arguments
   - Click "Apply" and then "Run"

**Output** (when run with argument "John"):

::

   Number of arguments: 1
   First argument: John
   Hello, John!

Debugging in IntelliJ IDEA
--------------------------

One of the biggest advantages of using an IDE like IntelliJ IDEA is its powerful debugging capabilities, which can help you find and fix errors in your code more efficiently.

Basic Debugging Concepts
~~~~~~~~~~~~~~~~~~~~~~~

Debugging allows you to:

- Pause program execution at specific points
- Examine variable values during runtime
- Step through code line by line
- Identify logical errors that don't cause compilation failures

Setting Up Breakpoints
~~~~~~~~~~~~~~~~~~~~~

Breakpoints are markers that tell the debugger where to pause execution:

1. **Adding Breakpoints**:
   - Click in the gutter (the area to the left of your code) next to the line number where you want to pause execution
   - A red circle appears, indicating a breakpoint
   - You can add multiple breakpoints throughout your code

2. **Starting Debug Mode**:
   - Instead of using the Run button (▶), click the Debug button (🐞)
   - Or right-click and select "Debug [ClassName].main()"
   - The program will run until it reaches a breakpoint

Debugging Controls
~~~~~~~~~~~~~~~~~

When the program pauses at a breakpoint, you have several controls available:

1. **Step Over** (F8): Execute the current line and move to the next line
2. **Step Into** (F7): If the current line contains a method call, jump into that method
3. **Step Out** (Shift+F8): Complete the current method and return to the calling method
4. **Resume Program** (F9): Continue execution until the next breakpoint or program end

Examining Variables
~~~~~~~~~~~~~~~~~~

During debugging, you can inspect the state of your program:

1. **Variables Window**: Shows all local variables and their current values
2. **Watches**: Allow you to monitor specific expressions
3. **Evaluate Expression** (Alt+F8): Calculate the value of any valid Java expression on the fly

Example Debugging Session
~~~~~~~~~~~~~~~~~~~~~~~~

Consider this buggy code:

.. code:: java

   public class DebugDemo {
       public static void main(String[] args) {
           int[] numbers = {1, 2, 3, 4, 5};
           int sum = 0;
           
           // Bug: loop goes beyond array bounds
           for (int i = 0; i <= numbers.length; i++) {
               sum += numbers[i];
           }
           
           System.out.println("Sum: " + sum);
       }
   }

To find the bug:

1. Set a breakpoint at the line `for (int i = 0; i <= numbers.length; i++)`
2. Start debugging
3. Use Step Over to execute the loop iterations one by one
4. Watch the `i` variable as it reaches the value 5 (which is equal to `numbers.length`)
5. At this point, `numbers[i]` attempts to access an element at index 5, causing an `ArrayIndexOutOfBoundsException`
6. Fix the bug by changing `<=` to `<` in the loop condition
   Hello, John!

Using Multiple Arguments
~~~~~~~~~~~~~~~~~~~~~~~

You can access different arguments by their position in the array:

.. code:: java

   class GreetingDemo {
       public static void main(String[] args) {
           // Check if we have the expected number of arguments
           if (args.length == 2) {
               String firstName = args[0];
               String lastName = args[1];
               
               System.out.println("Hello, " + firstName + " " + lastName + "!");
           } else {
               System.out.println("Please provide your first name and last name");
           }
       }
   }

**Execution:**

.. code:: bash

   java GreetingDemo John Doe

**Output:**

::

   Hello, John Doe!

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

   // Basic thread concept introduction
   class SimpleThread extends Thread {
       private String threadName;
       
       public SimpleThread(String name) {
           this.threadName = name;
       }
       
       @Override
       public void run() {
           System.out.println(threadName + " is running");
       }
   }

   public class ThreadExample {
       public static void main(String[] args) {
           SimpleThread thread1 = new SimpleThread("Thread-1");
           SimpleThread thread2 = new SimpleThread("Thread-2");
           
           // Start the threads
           thread1.start();
           thread2.start();
           
           System.out.println("Main thread continues execution");
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
       
       // Example method demonstrating keywords
       public void demonstrateKeywords() {
           // This is a simple method to show keyword usage
           int localVariable = 10;
           System.out.println("Local variable: " + localVariable);
           System.out.println("Constant value: " + CONSTANT);
       }
   }

   // Class inheritance example
   class Animal {
       void makeSound() {
           System.out.println("Animal makes a sound");
       }
   }

   class Dog extends Animal {
       @Override
       void makeSound() {
           System.out.println("Dog barks");
       }
   }

   // Interface example
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
+--------------+-------------+----------------------------+----------------------------+----------------+
| Type         | Size (bits) | Min Value                  | Max Value                  | Default Value  |
+==============+=============+============================+============================+================+
| ``byte``     | 8           | -128                       | 127                        | 0              |
+--------------+-------------+----------------------------+----------------------------+----------------+
| ``short``    | 16          | -32,768                    | 32,767                     | 0              |
+--------------+-------------+----------------------------+----------------------------+----------------+
| ``int``      | 32          | -2,147,483,648             | 2,147,483,647              | 0              |
+--------------+-------------+----------------------------+----------------------------+----------------+
| ``long``     | 64          | -9,223,372,036,854,775,808 | 9,223,372,036,854,775,807  | 0L             |
+--------------+-------------+----------------------------+----------------------------+----------------+
| ``float``    | 32          | 1.4E-45                    | 3.4028235E38               | 0.0f           |
+--------------+-------------+----------------------------+----------------------------+----------------+
| ``double``   | 64          | 4.9E-324                   | 1.7976931348623157E308     | 0.0d           |
+--------------+-------------+----------------------------+----------------------------+----------------+
| ``char``     | 16          | 0 (``\u0000``)             | 65,535 (``\uffff``)        | ``'\u0000'``   |
+--------------+-------------+----------------------------+----------------------------+----------------+
| ``boolean``  | 1           | —                          | —                          | false          |
+--------------+-------------+----------------------------+----------------------------+----------------+


Primitive Data Types
~~~~~~~~~~~~~~~~~~~~

Java has **8 primitive data types**:



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
           
           // Short-circuit examples with simple values
           boolean result1 = true && true;    // Both evaluated
           boolean result2 = false && true;   // Second part not evaluated
           boolean result3 = true || false;   // Second part not evaluated
           boolean result4 = false || true;   // Both evaluated
           
           System.out.println("\nShort-circuit results:");
           System.out.println("true && true: " + result1);
           System.out.println("false && true: " + result2);
           System.out.println("true || false: " + result3);
           System.out.println("false || true: " + result4);
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
           
           // Simple nested ternary example
           int x = 15, y = 10, z = 20;
           int largest = (x > y) ? x : y;
           System.out.println("Larger of " + x + " and " + y + " is: " + largest);
           
           // Ternary for assignment
           boolean isWeekend = true;
           String activity = isWeekend ? "Relax" : "Work";
           System.out.println("Activity: " + activity);
           
           // Safe string length example
           String str = "Hello";
           String nullStr = null;
           int length1 = (str != null) ? str.length() : 0;
           int length2 = (nullStr != null) ? nullStr.length() : 0;
           System.out.println("String length of '" + str + "': " + length1);
           System.out.println("String length of null string: " + length2);
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
           
           // Print first element
           System.out.println("First number: " + numbers[0]);
           System.out.println("First character: " + chars[0]);
           
           // Multi-dimensional array example
           int[][] matrix = {
               {1, 2, 3},
               {4, 5, 6}
           };
           
           // Access specific elements
           System.out.println("Matrix[0][0]: " + matrix[0][0]);
           System.out.println("Matrix[1][2]: " + matrix[1][2]);
           
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
           
           // Assignment with concatenation
           String message = "Hello";
           message += " World";
           System.out.println("Message: " + message);
           
           // Type casting in operations
           double pi = 3.14159;
           int roundedPi = (int) (pi + 0.5); // Manual rounding
           System.out.println("Rounded PI: " + roundedPi);
           
           // Character operations
           char letter = 'A';
           System.out.println("Letter: " + letter);
           System.out.println("ASCII value: " + (int) letter);
           System.out.println("Next letter: " + (char) (letter + 1));
       }
   }

Real-World Application Example
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   public class SimpleCalculator {
       public static void main(String[] args) {
           // This is a simple calculator application that shows language basics
           
           // Variable declarations
           double num1 = 25.5;
           double num2 = 10.0;
           
           // Arithmetic operations
           double sum = num1 + num2;
           double difference = num1 - num2;
           double product = num1 * num2;
           double quotient = num1 / num2;
           
           // Display results
           System.out.println("=== Simple Calculator ===");
           System.out.println("First number: " + num1);
           System.out.println("Second number: " + num2);
           System.out.println("\nResults:");
           System.out.println("Sum: " + sum);
           System.out.println("Difference: " + difference);
           System.out.println("Product: " + product);
           System.out.println("Quotient: " + quotient);
           
           // Using different number formats
           int intValue = (int)num1;
           long longValue = (long)product;
           
           System.out.println("\nConverted Values:");
           System.out.println("Int value of " + num1 + ": " + intValue);
           System.out.println("Long value of product: " + longValue);
           
           // Using String operations
           String message = "The result is: ";
           String finalResult = message + sum;
           System.out.println("\nFormatted output:");
           System.out.println(finalResult);
       }
   }

--------------

Practice Exercises
-----------------

Question 1: Hello World Program
~~~~~~~~~~~~~~~~~~~~~~~~~~

**Question:** What will be the output of the following program?

.. code:: java

   public class HelloWorld {
       public static void main(String[] args) {
           System.out.println("Hello, World!");
       }
   }

**Hint:** Look at what is inside the println() method.

Question 2: Basic Variable Assignment
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Question:** What will be the output of the following program?

.. code:: java

   public class Variables {
       public static void main(String[] args) {
           int x = 10;
           int y = 20;
           int sum = x + y;
           System.out.println("Sum: " + sum);
       }
   }

**Hint:** The program adds two variables and prints the result.

Question 3: String Concatenation
~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Question:** What will be the output of the following program?

.. code:: java

   public class StringExample {
       public static void main(String[] args) {
           String firstName = "John";
           String lastName = "Doe";
           System.out.println(firstName + " " + lastName);
       }
   }

**Hint:** The + operator with strings performs concatenation.
it’s public or not, gets compiled into its own separate .class file.

Question 2: Missing String[] args
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

Question 3: No Command Line Arguments
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

Question 4: Using Keyword as Variable
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

Question 5: Byte Overflow
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

Question 6: Float and Boolean Assignment
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

Question 7: Double with D suffix
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

Question 8: Number Systems
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

Question 9: Invalid Variable Name
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

Question 10: Uninitialized Local Variable
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

Question 11: Data Type Sizes
~~~~~~~~~~~~~~~~~~~~~~
**Question:** What will be the result if we try to compile and execute
the following code?
.. code:: java

    class Test {
        public static void main(String[] args) {
            System.out.println("Size of int: " + Integer.SIZE);
           
        }
    }

**Answer:** **Prints:**
Size of int: 32


Question 12: Pre-increment Operations
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

Question 13: Missing String[] args in main
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

1. **Environment Setup** - Installing and configuring IntelliJ IDEA
2. **Program Structure** - Basic Java program anatomy and compilation in an IDE
3. **Command Line Arguments** - Using program arguments in IntelliJ IDEA
4. **Debugging** - Using IntelliJ's powerful debugging features
5. **Programming Practices** - Naming conventions and documentation
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
