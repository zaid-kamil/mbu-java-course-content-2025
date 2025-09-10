Java Flow Control Statements
============================

Table of Contents
-----------------

1. `Introduction to Flow Control <#introduction-to-flow-control>`__
2. `Selection Statements <#selection-statements>`__

   - `Simple if Statement <#simple-if-statement>`__
   - `if-else Statement <#if-else-statement>`__
   - `Cascading if-else <#cascading-if-else>`__
   - `switch Statement <#switch-statement>`__

3. `Iteration Statements <#iteration-statements>`__

   - `while Loop <#while-loop>`__
   - `do-while Loop <#do-while-loop>`__
   - `for Loop <#for-loop>`__
   - `Enhanced for Loop <#enhanced-for-loop>`__

4. `Jumping Statements <#jumping-statements>`__

   - `break Statement <#break-statement>`__
   - `continue Statement <#continue-statement>`__
   - `return Statement <#return-statement>`__

5. `Advanced Flow Control Concepts <#advanced-flow-control-concepts>`__
6. `Best Practices and Common
   Pitfalls <#best-practices-and-common-pitfalls>`__
7. `Real-World Applications <#real-world-applications>`__
8. `Quiz Solutions <#quiz-solutions>`__

--------------

Introduction to Flow Control
----------------------------

**Flow control statements** are programming constructs that alter the
normal sequential execution flow of a program. They allow programs to
make decisions, repeat operations, and jump to different parts of code
based on conditions.

Without flow control, programs would execute sequentially from top to bottom,
making it impossible to create dynamic and responsive applications. Flow control
is the foundation of logical decision-making in programming.

Types of Flow Control Statements
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Java provides three main categories of flow control statements:

1. **Selection Statements** - Make decisions based on conditions

   - ``if``, ``if-else``, ``switch``
   
   These statements evaluate conditions and execute different code blocks based on the results.
   For example, an ATM program might use selection statements to determine whether a user has
   sufficient funds for a withdrawal.

2. **Iteration Statements** - Repeat code blocks

   - ``while``, ``do-while``, ``for``, enhanced ``for``
   
   These statements allow you to execute a block of code multiple times. For instance,
   a program might use a loop to process each item in a shopping cart or to validate
   user input until correct data is provided.

3. **Jumping Statements** - Transfer control to different parts of the program

   - ``break``, ``continue``, ``return``
   
   These statements alter the normal flow by jumping to a different part of the code.
   For example, a ``break`` statement can exit a loop early when a specific condition is met.

**Example: Using Different Flow Control Types**

.. code:: java

   public class FlowControlDemo {
       public static void main(String[] args) {
           // Selection statement example
           int temperature = 28;
           if (temperature > 25) {
               System.out.println("It's a hot day!");
           } else {
               System.out.println("It's not too hot today.");
           }
           
           // Iteration statement example
           System.out.println("\nCounting from 1 to 5:");
           for (int i = 1; i <= 5; i++) {
               System.out.println("Count: " + i);
           }
           
           // Jumping statement example
           System.out.println("\nSearching for the number 3:");
           for (int i = 1; i <= 10; i++) {
               if (i == 3) {
                   System.out.println("Found 3! Stopping the search.");
                   break; // Exit the loop when 3 is found
               }
               System.out.println("Checking number: " + i);
           }
       }
   }

**Output:**

::

   It's a hot day!
   
   Counting from 1 to 5:
   Count: 1
   Count: 2
   Count: 3
   Count: 4
   Count: 5
   
   Searching for the number 3:
   Checking number: 1
   Checking number: 2
   Found 3! Stopping the search.

This example demonstrates all three types of flow control statements working together in a single program.
The selection statement checks the temperature, the iteration statement counts numbers, and the jumping
statement stops the search when a specific value is found.

--------------

Selection Statements
--------------------

Selection statements allow programs to execute different code blocks
based on boolean conditions.

Simple if Statement
~~~~~~~~~~~~~~~~~~~

The ``if`` statement executes a block of code only when a specified
condition is true. This is the most basic form of selection statement in Java.

When the condition evaluates to ``true``, the code block inside the braces is executed.
When the condition evaluates to ``false``, the code block is skipped completely.

Syntax:
^^^^^^^

.. code:: java

   if (boolean_expression) {
       // statements to execute when condition is true
   }

Basic Examples:
^^^^^^^^^^^^^^^

.. code:: java

   // Example 1: Simple age check
   public class IfExample {
       public static void main(String[] args) {
           int age = 18;
           
           if (age >= 18) {
               System.out.println("You are an adult!");
           }
           
           System.out.println("Program continues here regardless of the condition.");
       }
   }

**Output:**

::

   You are an adult!
   Program continues here regardless of the condition.

In this example, the condition ``age >= 18`` evaluates to ``true`` since age is 18.
Therefore, the message "You are an adult!" is printed. The second message is outside
the if block, so it's always printed regardless of the condition.

.. code:: java

   // Example 2: Grade validation
   public class GradeCheck {
       public static void main(String[] args) {
           int score = 85;
           
           if (score >= 90) {
               System.out.println("Excellent! You got an A grade.");
           }
           
           if (score >= 60) {
               System.out.println("You passed the exam.");
           }
           
           if (score < 60) {
               System.out.println("You need to retake the exam.");
           }
       }
   }

**Output:**

::

   You passed the exam.

In this example, the program checks multiple independent conditions:
- First if: score >= 90 is false (85 is not ≥ 90), so nothing is printed
- Second if: score >= 60 is true (85 is ≥ 60), so "You passed the exam" is printed
- Third if: score < 60 is false (85 is not < 60), so nothing is printed

**When to use simple if statements:**
- When you need to execute code only under specific conditions
- When there's no alternative action needed for the false condition
- When checking multiple independent conditions

Advanced if Examples:
^^^^^^^^^^^^^^^^^^^^^

.. code:: java

   // Example 3: Multiple conditions
   public class ComplexIfExample {
       public static void main(String[] args) {
           int temperature = 25;
           boolean isRaining = false;
           boolean hasUmbrella = true;
           
           if (temperature > 20 && !isRaining) {
               System.out.println("Perfect weather for a walk!");
           }
           
           if (isRaining && hasUmbrella) {
               System.out.println("You can still go out with your umbrella.");
           }
           
           // String comparison
           String day = "Sunday";
           if (day.equals("Sunday") || day.equals("Saturday")) {
               System.out.println("It's weekend!");
           }
           
           // Null check
           String name = null;
           if (name != null && name.length() > 0) {
               System.out.println("Hello, " + name);
           }
           
           // Using parentheses for clarity
           int a = 5, b = 10, c = 15;
           if ((a < b) && ((b + 2) < c)) {
               System.out.println("Both conditions are true!");
           }
       }
   }

**Output:**

::

   Perfect weather for a walk!
   It's weekend!
   Both conditions are true!

This example demonstrates more complex conditional expressions:

1. **Logical Operators**: 
   - AND operator (&&): Both conditions must be true
   - OR operator (||): At least one condition must be true
   - NOT operator (!): Inverts the boolean value

2. **String Comparison**:
   - Use `equals()` method instead of `==` to compare string content
   - `==` compares object references, not string content

3. **Short-circuit Evaluation**:
   - In the null check example, if `name != null` is false, the second condition `name.length() > 0` is not evaluated
   - This prevents a NullPointerException
   
4. **Using Parentheses**:
   - Parentheses clarify the order of evaluation
   - They improve code readability for complex conditions

**Common Mistakes to Avoid:**
- Using `==` instead of `equals()` for string comparison
- Not using short-circuit evaluation for null checks
- Forgetting that `=` is assignment while `==` is comparison


if-else Statement
~~~~~~~~~~~~~~~~~

The ``if-else`` statement provides an alternative execution path when
the condition is false. Unlike the simple ``if`` statement, the ``if-else``
statement ensures that exactly one of the two code blocks will be executed.

This is particularly useful when you need to perform one action if a condition
is true, and a different action if the condition is false.

.. _syntax-1:

Syntax:
^^^^^^^

.. code:: java

   if (boolean_expression) {
       // statements when condition is true
   } else {
       // statements when condition is false
   }

.. _basic-examples-1:

Basic Examples:
^^^^^^^^^^^^^^^

.. code:: java

   // Example 1: Voting eligibility
   public class VotingEligibility {
       public static void main(String[] args) {
           int age = 16;
           
           if (age >= 18) {
               System.out.println("You are eligible to vote");
           } else {
               System.out.println("You are not eligible to vote");
               System.out.println("You need to wait " + (18 - age) + " more years");
           }
       }
   }

**Output:**

::

   You are not eligible to vote
   You need to wait 2 more years

This example checks if a person is eligible to vote based on their age.
Since age is 16, which is less than 18, the condition evaluates to false,
and the code in the else block executes.

.. code:: java

   // Example 2: Even or odd number
   public class EvenOddChecker {
       public static void main(String[] args) {
           int number = 17;
           
           if (number % 2 == 0) {
               System.out.println(number + " is even");
           } else {
               System.out.println(number + " is odd");
           }
       }
   }

**Output:**

::

   17 is odd

This example checks if a number is even or odd using the modulo operator (%).
When a number is divided by 2, if the remainder is 0, it's even; otherwise, it's odd.
Since 17 % 2 equals 1 (not 0), the condition is false, and the else block executes.

Advanced if-else Examples:
^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code:: java

   // Example 3: Bank account operations
   public class BankAccount {
       public static void main(String[] args) {
           double balance = 1000.0;
           double withdrawAmount = 1500.0;
           
           if (withdrawAmount <= balance) {
               balance -= withdrawAmount;
               System.out.println("Withdrawal successful!");
               System.out.println("Remaining balance: $" + balance);
           } else {
               System.out.println("Insufficient funds!");
               System.out.println("Available balance: $" + balance);
               System.out.println("Required amount: $" + withdrawAmount);
           }
       }
   }

**Output:**

::

   Insufficient funds!
   Available balance: $1000.0
   Required amount: $1500.0

This example simulates a bank withdrawal operation. Since the withdraw amount ($1500)
is greater than the available balance ($1000), the condition evaluates to false, and
the system displays an "Insufficient funds" message with relevant details.

.. code:: java

   // Example 4: Password validation
   public class PasswordValidator {
       public static void main(String[] args) {
           String password = "MySecure123";
           
           if (password.length() >= 8 && 
               password.matches(".*[A-Z].*") && 
               password.matches(".*[a-z].*") && 
               password.matches(".*[0-9].*")) {
               System.out.println("Strong password!");
           } else {
               System.out.println("Weak password. Requirements:");
               System.out.println("- At least 8 characters");
               System.out.println("- Contains uppercase letter");
               System.out.println("- Contains lowercase letter");
               System.out.println("- Contains at least one digit");
           }
       }
   }

**Output:**

::

   Strong password!

This example demonstrates a more complex password validation using multiple conditions with logical AND (&&):
1. The password must be at least 8 characters long
2. It must contain at least one uppercase letter (using regex `.*[A-Z].*`)
3. It must contain at least one lowercase letter (using regex `.*[a-z].*`)
4. It must contain at least one digit (using regex `.*[0-9].*`)

Since "MySecure123" meets all these requirements, the condition evaluates to true,
and the program indicates it's a strong password.

**Key Points About if-else Statements:**

1. **Mutual Exclusivity**: Only one of the blocks (if or else) will execute, never both.

2. **Default Behavior**: The else block provides a default action when the condition is false.

3. **Code Structure**: Using if-else improves code readability by clearly separating the two possible execution paths.

4. **Error Handling**: if-else is commonly used for validation and error handling scenarios.

Cascading if-else
~~~~~~~~~~~~~~~~~

Multiple conditions can be checked using cascading if-else statements
(also known as if-else ladder). This structure is used when you need to check
multiple conditions in sequence and execute the code block associated with the first
condition that evaluates to true.

When more than two options exist, using cascading if-else statements provides a 
more readable and maintainable solution than nested if-else statements.

.. _syntax-2:

Syntax:
^^^^^^^

.. code:: java

   if (condition1) {
       // statements for condition1
   } else if (condition2) {
       // statements for condition2
   } else if (condition3) {
       // statements for condition3
   } else {
       // default statements when no condition is true
   }

Examples:
^^^^^^^^^

.. code:: java

   // Example 1: Season determination
   public class SeasonFinder {
       public static void main(String[] args) {
           int month = 4; // April
           
           if (month == 12 || month == 1 || month == 2) {
               System.out.println("It's Winter");
           } else if (month >= 3 && month <= 5) {
               System.out.println("It's Spring");
           } else if (month >= 6 && month <= 8) {
               System.out.println("It's Summer");
           } else if (month >= 9 && month <= 11) {
               System.out.println("It's Fall");
           } else {
               System.out.println("Invalid month");
           }
       }
   }

**Output:**

::

   It's Spring

This example determines the season based on the month number. Since month is 4 (April), 
the condition `month >= 3 && month <= 5` evaluates to true, and "It's Spring" is printed.
Notice how the conditions are checked in sequence, and only the first true condition's
block is executed.


.. code:: java

   // Example 2: Grade calculator
   public class GradeCalculator {
       public static void main(String[] args) {
           int score = 85;
           char grade;
           String description;
           
           if (score >= 90) {
               grade = 'A';
               description = "Excellent";
           } else if (score >= 80) {
               grade = 'B';
               description = "Good";
           } else if (score >= 70) {
               grade = 'C';
               description = "Average";
           } else if (score >= 60) {
               grade = 'D';
               description = "Below Average";
           } else {
               grade = 'F';
               description = "Fail";
           }
           
           System.out.println("Score: " + score);
           System.out.println("Grade: " + grade + " (" + description + ")");
       }
   }

.. code:: java

   // Example 3: BMI Calculator
   public class BMICalculator {
       public static void main(String[] args) {
           double weight = 70.0; // kg
           double height = 1.75;  // meters
           double bmi = weight / (height * height);
           
           System.out.printf("Your BMI is: %.2f\n", bmi);
           
           if (bmi < 18.5) {
               System.out.println("Category: Underweight");
               System.out.println("Recommendation: Consider gaining weight");
           } else if (bmi < 25.0) {
               System.out.println("Category: Normal weight");
               System.out.println("Recommendation: Maintain current weight");
           } else if (bmi < 30.0) {
               System.out.println("Category: Overweight");
               System.out.println("Recommendation: Consider losing weight");
           } else {
               System.out.println("Category: Obese");
               System.out.println("Recommendation: Consult a healthcare provider");
           }
       }
   }

switch Statement
~~~~~~~~~~~~~~~~

The ``switch`` statement provides a clean way to handle multiple
discrete values of a variable.

.. _syntax-3:

Syntax:
^^^^^^^

.. code:: java

   switch (expression) {
       case value1:
           // statements
           break;
       case value2:
           // statements
           break;
       default:
           // default statements
           break;
   }

.. _basic-examples-2:

Basic Examples:
^^^^^^^^^^^^^^^

.. code:: java

   // Example 1: Day of week (from course material)
   public class DayOfWeek {
       public static void main(String[] args) {
           if (args.length == 0) {
               System.out.println("Please provide day number (1-7)");
               return;
           }
           
           int weekday = Integer.parseInt(args[0]);
           
           switch (weekday) {
               case 1:
                   System.out.println("Sunday");
                   break;
               case 2:
                   System.out.println("Monday");
                   break;
               case 3:
                   System.out.println("Tuesday");
                   break;
               case 4:
                   System.out.println("Wednesday");
                   break;
               case 5:
                   System.out.println("Thursday");
                   break;
               case 6:
                   System.out.println("Friday");
                   break;
               case 7:
                   System.out.println("Saturday");
                   break;
               default:
                   System.out.println("Invalid day");
           }
       }
   }

Advanced switch Examples:
^^^^^^^^^^^^^^^^^^^^^^^^^

.. code:: java

   // Example 2: Calculator with switch
   public class SimpleCalculator {
       public static void main(String[] args) {
           double num1 = 10.0;
           double num2 = 5.0;
           char operator = '+';
           double result = 0;
           boolean validOperation = true;
           
           switch (operator) {
               case '+':
                   result = num1 + num2;
                   break;
               case '-':
                   result = num1 - num2;
                   break;
               case '*':
                   result = num1 * num2;
                   break;
               case '/':
                   if (num2 != 0) {
                       result = num1 / num2;
                   } else {
                       System.out.println("Error: Division by zero!");
                       validOperation = false;
                   }
                   break;
               case '%':
                   if (num2 != 0) {
                       result = num1 % num2;
                   } else {
                       System.out.println("Error: Modulo by zero!");
                       validOperation = false;
                   }
                   break;
               default:
                   System.out.println("Invalid operator: " + operator);
                   validOperation = false;
           }
           
           if (validOperation) {
               System.out.println(num1 + " " + operator + " " + num2 + " = " + result);
           }
       }
   }

.. code:: java

   // Example 3: Menu-driven program
   public class RestaurantMenu {
       public static void main(String[] args) {
           int choice = 3;
           
           System.out.println("=== Restaurant Menu ===");
           System.out.println("1. Pizza - $12.99");
           System.out.println("2. Burger - $8.99");
           System.out.println("3. Pasta - $10.99");
           System.out.println("4. Salad - $7.99");
           System.out.println("5. Exit");
           System.out.println("Your choice: " + choice);
           
           switch (choice) {
               case 1:
                   System.out.println("You ordered Pizza!");
                   System.out.println("Total: $12.99");
                   break;
               case 2:
                   System.out.println("You ordered Burger!");
                   System.out.println("Total: $8.99");
                   break;
               case 3:
                   System.out.println("You ordered Pasta!");
                   System.out.println("Total: $10.99");
                   break;
               case 4:
                   System.out.println("You ordered Salad!");
                   System.out.println("Total: $7.99");
                   break;
               case 5:
                   System.out.println("Thank you for visiting!");
                   break;
               default:
                   System.out.println("Invalid choice! Please select 1-5.");
           }
       }
   }

switch with Strings (Java 7+):
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code:: java

   // Example 4: String-based switch
   public class StringSwitchExample {
       public static void main(String[] args) {
           String day = "MONDAY";
           String activity;
           
           switch (day.toLowerCase()) {
               case "monday":
                   activity = "Team meeting at 9 AM";
                   break;
               case "tuesday":
                   activity = "Code review session";
                   break;
               case "wednesday":
                   activity = "Project planning";
                   break;
               case "thursday":
                   activity = "Training workshop";
                   break;
               case "friday":
                   activity = "Sprint retrospective";
                   break;
               case "saturday":
               case "sunday":
                   activity = "Weekend - Rest and relax!";
                   break;
               default:
                   activity = "Invalid day";
           }
           
           System.out.println(day + ": " + activity);
       }
   }

Fall-through behavior in switch:
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code:: java

   // Example 5: Switch fall-through
   public class SwitchFallthrough {
       public static void main(String[] args) {
           int month = 2;
           String season;
           
           switch (month) {
               case 12:
               case 1:
               case 2:
                   season = "Winter";
                   break;
               case 3:
               case 4:
               case 5:
                   season = "Spring";
                   break;
               case 6:
               case 7:
               case 8:
                   season = "Summer";
                   break;
               case 9:
               case 10:
               case 11:
                   season = "Fall";
                   break;
               default:
                   season = "Invalid month";
           }
           
           System.out.println("Month " + month + " is in " + season);
           
           // Example of intentional fall-through
           int number = 2;
           System.out.println("Processing number: " + number);
           
           switch (number) {
               case 1:
                   System.out.println("One");
                   // Fall through intentionally
               case 2:
                   System.out.println("Two or continuation from One");
                   // Fall through intentionally
               case 3:
                   System.out.println("Three or continuation from above");
                   break;
               default:
                   System.out.println("Other number");
           }
       }
   }

--------------

Iteration Statements
--------------------

Iteration statements (loops) allow you to execute a block of code
repeatedly based on a condition.

while Loop
~~~~~~~~~~

The ``while`` loop executes a block of code as long as a specified
condition is true.

.. _syntax-4:

Syntax:
^^^^^^^

.. code:: java

   while (condition) {
       // loop body
   }

.. _basic-examples-3:

Basic Examples:
^^^^^^^^^^^^^^^

.. code:: java

   // Example 1: Basic counting (from course material)
   public class WhileLoopBasic {
       public static void main(String[] args) {
           int i = 0;
           
           while (i < 5) {
               System.out.println("i: " + i);
               i = i + 1; // or i++
           }
           
           System.out.println("Loop finished. Final value of i: " + i);
       }
   }

.. code:: java

   // Example 2: Sum calculation
   public class SumCalculator {
       public static void main(String[] args) {
           int sum = 0;
           int number = 1;
           
           while (number <= 10) {
               sum += number;
               System.out.println("Adding " + number + ", sum so far: " + sum);
               number++;
           }
           
           System.out.println("Final sum of 1 to 10: " + sum);
       }
   }

Advanced while Examples:
^^^^^^^^^^^^^^^^^^^^^^^^

.. code:: java

   // Example 3: Input validation
   import java.util.Scanner;

   public class InputValidation {
       public static void main(String[] args) {
           Scanner scanner = new Scanner(System.in);
           int age = -1;
           
           while (age < 0 || age > 150) {
               System.out.print("Enter your age (0-150): ");
               age = scanner.nextInt();
               
               if (age < 0 || age > 150) {
                   System.out.println("Invalid age! Please try again.");
               }
           }
           
           System.out.println("Valid age entered: " + age);
           scanner.close();
       }
   }

.. code:: java

   // Example 4: Number guessing game
   import java.util.Scanner;
   import java.util.Random;

   public class NumberGuessingGame {
       public static void main(String[] args) {
           Scanner scanner = new Scanner(System.in);
           Random random = new Random();
           
           int targetNumber = random.nextInt(100) + 1; // 1-100
           int guess = 0;
           int attempts = 0;
           
           System.out.println("Guess a number between 1 and 100!");
           
           while (guess != targetNumber) {
               System.out.print("Enter your guess: ");
               guess = scanner.nextInt();
               attempts++;
               
               if (guess < targetNumber) {
                   System.out.println("Too low! Try again.");
               } else if (guess > targetNumber) {
                   System.out.println("Too high! Try again.");
               } else {
                   System.out.println("Congratulations! You found it in " + attempts + " attempts!");
               }
           }
           
           scanner.close();
       }
   }

do-while Loop
~~~~~~~~~~~~~

The ``do-while`` loop executes the code block at least once, then
continues as long as the condition is true.

.. _syntax-5:

Syntax:
^^^^^^^

.. code:: java

   do {
       // loop body
   } while (condition);

Basic Example:
^^^^^^^^^^^^^^

.. code:: java

   // Example 1: Basic do-while (from course material)
   public class DoWhileBasic {
       public static void main(String[] args) {
           int i = 5;
           
           do {
               System.out.println("i: " + i);
               i = i + 1;
           } while (i < 5);
           
           System.out.println("Loop finished. Final value of i: " + i);
       }
   }

Advanced do-while Examples:
^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code:: java

   // Example 2: Menu system
   import java.util.Scanner;

   public class MenuSystem {
       public static void main(String[] args) {
           Scanner scanner = new Scanner(System.in);
           int choice;
           
           do {
               System.out.println("\n=== Main Menu ===");
               System.out.println("1. Create Account");
               System.out.println("2. Login");
               System.out.println("3. Reset Password");
               System.out.println("4. Help");
               System.out.println("0. Exit");
               System.out.print("Enter your choice: ");
               
               choice = scanner.nextInt();
               
               switch (choice) {
                   case 1:
                       System.out.println("Creating account...");
                       break;
                   case 2:
                       System.out.println("Logging in...");
                       break;
                   case 3:
                       System.out.println("Resetting password...");
                       break;
                   case 4:
                       System.out.println("Displaying help information...");
                       break;
                   case 0:
                       System.out.println("Goodbye!");
                       break;
                   default:
                       System.out.println("Invalid choice! Please try again.");
               }
           } while (choice != 0);
           
           scanner.close();
       }
   }

.. code:: java

   // Example 3: Password retry system
   import java.util.Scanner;

   public class PasswordRetry {
       public static void main(String[] args) {
           Scanner scanner = new Scanner(System.in);
           String correctPassword = "secret123";
           String enteredPassword;
           int maxAttempts = 3;
           int attempts = 0;
           boolean authenticated = false;
           
           do {
               attempts++;
               System.out.print("Enter password (Attempt " + attempts + "/" + maxAttempts + "): ");
               enteredPassword = scanner.nextLine();
               
               if (enteredPassword.equals(correctPassword)) {
                   System.out.println("Access granted!");
                   authenticated = true;
               } else {
                   System.out.println("Incorrect password!");
                   if (attempts < maxAttempts) {
                       System.out.println("You have " + (maxAttempts - attempts) + " attempts remaining.");
                   }
               }
           } while (!authenticated && attempts < maxAttempts);
           
           if (!authenticated) {
               System.out.println("Account locked due to too many failed attempts.");
           }
           
           scanner.close();
       }
   }

for Loop
~~~~~~~~

The ``for`` loop is ideal when you know in advance how many times you
want to execute the loop.

.. _syntax-6:

Syntax:
^^^^^^^

.. code:: java

   for (initialization; condition; increment/decrement) {
       // loop body
   }

.. _basic-examples-4:

Basic Examples:
^^^^^^^^^^^^^^^

.. code:: java

   // Example 1: Basic counting (from course material)
   public class ForLoopBasic {
       public static void main(String[] args) {
           for (int i = 1; i <= 5; i++) {
               System.out.println("i: " + i);
           }
           
           System.out.println("Loop finished");
       }
   }

.. code:: java

   // Example 2: Multiplication table
   public class MultiplicationTable {
       public static void main(String[] args) {
           int number = 7;
           
           System.out.println("Multiplication table for " + number + ":");
           for (int i = 1; i <= 10; i++) {
               System.out.println(number + " x " + i + " = " + (number * i));
           }
       }
   }

Advanced for Examples:
^^^^^^^^^^^^^^^^^^^^^^

.. code:: java

   // Example 3: Factorial calculation
   public class FactorialCalculator {
       public static void main(String[] args) {
           int number = 5;
           long factorial = 1;
           
           for (int i = 1; i <= number; i++) {
               factorial *= i;
               System.out.println("Step " + i + ": " + factorial);
           }
           
           System.out.println(number + "! = " + factorial);
       }
   }

.. code:: java

   // Example 4: Pattern printing
   public class PatternPrinter {
       public static void main(String[] args) {
           int rows = 5;
           
           // Right triangle pattern
           System.out.println("Right Triangle Pattern:");
           for (int i = 1; i <= rows; i++) {
               for (int j = 1; j <= i; j++) {
                   System.out.print("* ");
               }
               System.out.println();
           }
           
           // Inverted triangle pattern
           System.out.println("\nInverted Triangle Pattern:");
           for (int i = rows; i >= 1; i--) {
               for (int j = 1; j <= i; j++) {
                   System.out.print("* ");
               }
               System.out.println();
           }
           
           // Number pyramid
           System.out.println("\nNumber Pyramid:");
           for (int i = 1; i <= rows; i++) {
               // Print spaces
               for (int j = rows - i; j > 0; j--) {
                   System.out.print(" ");
               }
               // Print numbers
               for (int j = 1; j <= i; j++) {
                   System.out.print(j + " ");
               }
               System.out.println();
           }
       }
   }

.. code:: java

   // Example 5: Nested loops - Matrix operations
   public class MatrixOperations {
       public static void main(String[] args) {
           int[][] matrix1 = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};
           int[][] matrix2 = {{9, 8, 7}, {6, 5, 4}, {3, 2, 1}};
           int rows = matrix1.length;
           int cols = matrix1[0].length;
           int[][] sum = new int[rows][cols];
           
           // Matrix addition
           for (int i = 0; i < rows; i++) {
               for (int j = 0; j < cols; j++) {
                   sum[i][j] = matrix1[i][j] + matrix2[i][j];
               }
           }
           
           // Display matrices
           System.out.println("Matrix 1:");
           printMatrix(matrix1);
           
           System.out.println("\nMatrix 2:");
           printMatrix(matrix2);
           
           System.out.println("\nSum:");
           printMatrix(sum);
       }
       
       public static void printMatrix(int[][] matrix) {
           for (int i = 0; i < matrix.length; i++) {
               for (int j = 0; j < matrix[i].length; j++) {
                   System.out.print(matrix[i][j] + " ");
               }
               System.out.println();
           }
       }
   }

Variations of for Loop:
^^^^^^^^^^^^^^^^^^^^^^^

.. code:: java

   // Example 6: Different for loop variations
   public class ForLoopVariations {
       public static void main(String[] args) {
           // Standard for loop
           System.out.println("Standard for loop:");
           for (int i = 0; i < 5; i++) {
               System.out.print(i + " ");
           }
           System.out.println();
           
           // Counting backwards
           System.out.println("\nCounting backwards:");
           for (int i = 10; i > 0; i--) {
               System.out.print(i + " ");
           }
           System.out.println();
           
           // Step by 2
           System.out.println("\nStep by 2:");
           for (int i = 0; i <= 20; i += 2) {
               System.out.print(i + " ");
           }
           System.out.println();
           
           // Multiple variables
           System.out.println("\nMultiple variables:");
           for (int i = 0, j = 10; i <= 5; i++, j--) {
               System.out.println("i = " + i + ", j = " + j);
           }
           
           // Infinite loop (use with caution)
           System.out.println("\nInfinite loop example (limited iterations):");
           int count = 0;
           for (;;) {  // Infinite loop
               System.out.print(count + " ");
               count++;
               if (count >= 5) break;  // Exit condition
           }
           System.out.println();
       }
   }

Enhanced for Loop
~~~~~~~~~~~~~~~~~

The enhanced for loop (for-each loop) provides a simpler way to iterate
over arrays and collections.

.. _syntax-7:

Syntax:
^^^^^^^

.. code:: java

   for (datatype variable : array/collection) {
       // loop body
   }

.. _basic-examples-5:

Basic Examples:
^^^^^^^^^^^^^^^

.. code:: java

   // Example 1: Basic enhanced for loop (from course material)
   public class EnhancedForBasic {
       public static void main(String[] args) {
           int[] numbers = {10, 20, 30, 40, 50};
           
           for (int i : numbers) {
               System.out.println("i: " + i);
           }
       }
   }

Advanced Enhanced for Examples:
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code:: java

   // Example 2: Working with different data types
   public class EnhancedForAdvanced {
       public static void main(String[] args) {
           // String array
           String[] fruits = {"Apple", "Banana", "Cherry", "Date", "Elderberry"};
           System.out.println("Fruits:");
           for (String fruit : fruits) {
               System.out.println("- " + fruit);
           }
           
           // Double array - calculating average
           double[] scores = {85.5, 92.3, 78.9, 96.2, 88.7};
           double sum = 0;
           int count = 0;
           
           System.out.println("\nScores:");
           for (double score : scores) {
               System.out.println("Score " + (++count) + ": " + score);
               sum += score;
           }
           
           double average = sum / scores.length;
           System.out.println("Average score: " + average);
           
           // Character array
           char[] vowels = {'a', 'e', 'i', 'o', 'u'};
           System.out.println("\nVowels:");
           for (char vowel : vowels) {
               System.out.print(vowel + " ");
           }
           System.out.println();
       }
   }

.. code:: java

   // Example 3: Multi-dimensional arrays
   public class TwoDimensionalArray {
       public static void main(String[] args) {
           int[][] matrix = {
               {1, 2, 3},
               {4, 5, 6},
               {7, 8, 9}
           };
           
           System.out.println("Matrix elements:");
           for (int[] row : matrix) {
               for (int element : row) {
                   System.out.print(element + " ");
               }
               System.out.println();
           }
           
           // Finding maximum element
           int max = Integer.MIN_VALUE;
           for (int[] row : matrix) {
               for (int element : row) {
                   if (element > max) {
                       max = element;
                   }
               }
           }
           System.out.println("Maximum element: " + max);
       }
   }

.. code:: java

   // Example 4: Working with collections
   import java.util.*;

   public class CollectionIteration {
       public static void main(String[] args) {
           // ArrayList
           List<String> cities = Arrays.asList("New York", "London", "Tokyo", "Paris", "Sydney");
           
           System.out.println("Cities:");
           for (String city : cities) {
               System.out.println("- " + city + " (length: " + city.length() + ")");
           }
           
           // HashMap
           Map<String, Integer> populations = new HashMap<>();
           populations.put("New York", 8336817);
           populations.put("London", 8982000);
           populations.put("Tokyo", 13929286);
           
           System.out.println("\nCity populations:");
           for (Map.Entry<String, Integer> entry : populations.entrySet()) {
               System.out.println(entry.getKey() + ": " + entry.getValue());
           }
           
           // Set
           Set<String> uniqueWords = new HashSet<>(Arrays.asList("java", "python", "javascript", "java", "c++"));
           
           System.out.println("\nUnique programming languages:");
           for (String language : uniqueWords) {
               System.out.println("- " + language.toUpperCase());
           }
       }
   }

--------------

Jumping Statements
------------------

Jumping statements transfer control to different parts of the program.

break Statement
~~~~~~~~~~~~~~~

The ``break`` statement terminates the nearest enclosing loop or switch
statement.

.. _examples-1:

Examples:
^^^^^^^^^

.. code:: java

   // Example 1: Basic break in for loop (from course material)
   public class BreakExample {
       public static void main(String[] args) {
           for (int i = 1; i <= 5; i++) {
               if (i == 2) {
                   break;
               }
               System.out.println("i: " + i);
           }
           System.out.println("Loop terminated");
       }
   }

.. code:: java

   // Example 2: Finding first even number
   public class FindFirstEven {
       public static void main(String[] args) {
           int[] numbers = {1, 3, 7, 8, 5, 12, 9, 4};
           int firstEven = -1;
           
           for (int number : numbers) {
               System.out.println("Checking: " + number);
               if (number % 2 == 0) {
                   firstEven = number;
                   System.out.println("Found first even number: " + firstEven);
                   break;
               }
           }
           
           if (firstEven == -1) {
               System.out.println("No even number found");
           }
       }
   }

.. code:: java

   // Example 3: Break in nested loops
   public class NestedLoopBreak {
       public static void main(String[] args) {
           System.out.println("Break in nested loops:");
           
           for (int i = 1; i <= 3; i++) {
               System.out.println("Outer loop i = " + i);
               
               for (int j = 1; j <= 5; j++) {
                   if (j == 3) {
                       System.out.println("Breaking inner loop at j = " + j);
                       break; // Only breaks the inner loop
                   }
                   System.out.println("  Inner loop j = " + j);
               }
           }
           
           // Using labeled break for outer loop
           System.out.println("\nUsing labeled break:");
           
           outerLoop: 
           for (int i = 1; i <= 3; i++) {
               System.out.println("Outer loop i = " + i);
               
               for (int j = 1; j <= 5; j++) {
                   if (i == 2 && j == 3) {
                       System.out.println("Breaking outer loop at i = " + i + ", j = " + j);
                       break outerLoop; // Breaks the outer loop
                   }
                   System.out.println("  Inner loop j = " + j);
               }
           }
       }
   }

.. code:: java

   // Example 4: Interactive search
   import java.util.Scanner;

   public class InteractiveSearch {
       public static void main(String[] args) {
           String[] names = {"Alice", "Bob", "Charlie", "David", "Eve"};
           Scanner scanner = new Scanner(System.in);
           
           while (true) {
               System.out.print("Enter name to search (or 'quit' to exit): ");
               String searchName = scanner.nextLine();
               
               if (searchName.equalsIgnoreCase("quit")) {
                   System.out.println("Goodbye!");
                   break;
               }
               
               boolean found = false;
               for (int i = 0; i < names.length; i++) {
                   if (names[i].equalsIgnoreCase(searchName)) {
                       System.out.println("Found " + names[i] + " at position " + i);
                       found = true;
                       break;
                   }
               }
               
               if (!found) {
                   System.out.println("Name not found");
               }
           }
           
           scanner.close();
       }
   }

continue Statement
~~~~~~~~~~~~~~~~~~

The ``continue`` statement skips the current iteration and moves to the
next iteration of the loop.

.. _examples-2:

Examples:
^^^^^^^^^

.. code:: java

   // Example 1: Basic continue (from course material)
   public class ContinueExample {
       public static void main(String[] args) {
           int[] numbers = {1, 2, 3, 4, 5};
           
           for (int i : numbers) {
               if (i == 3) {
                   continue;
               }
               System.out.println("i: " + i);
           }
       }
   }

.. code:: java

   // Example 2: Skip negative numbers
   public class SkipNegatives {
       public static void main(String[] args) {
           int[] numbers = {1, -2, 3, -4, 5, -6, 7, 8, -9, 10};
           int sum = 0;
           int count = 0;
           
           System.out.println("Processing positive numbers only:");
           for (int number : numbers) {
               if (number < 0) {
                   System.out.println("Skipping negative number: " + number);
                   continue;
               }
               
               sum += number;
               count++;
               System.out.println("Added: " + number + ", Running sum: " + sum);
           }
           
           System.out.println("Total positive numbers: " + count);
           System.out.println("Sum of positive numbers: " + sum);
       }
   }

.. code:: java

   // Example 3: Continue in nested loops
   public class NestedContinue {
       public static void main(String[] args) {
           System.out.println("Multiplication table (skipping multiples of 5):");
           
           for (int i = 1; i <= 5; i++) {
               System.out.println("\nTable for " + i + ":");
               
               for (int j = 1; j <= 10; j++) {
                   int product = i * j;
                   if (product % 5 == 0) {
                       continue; // Skip multiples of 5
                   }
                   System.out.println(i + " x " + j + " = " + product);
               }
           }
       }
   }

.. code:: java

   // Example 4: Data validation and processing
   public class DataProcessor {
       public static void main(String[] args) {
           String[] data = {"123", "abc", "456", "", "789", null, "0", "999"};
           int sum = 0;
           int validCount = 0;
           
           for (String item : data) {
               // Skip null values
               if (item == null) {
                   System.out.println("Skipping null value");
                   continue;
               }
               
               // Skip empty strings
               if (item.isEmpty()) {
                   System.out.println("Skipping empty string");
                   continue;
               }
               
               // Try to parse as integer
               try {
                   int number = Integer.parseInt(item);
                   
                   // Skip zero values
                   if (number == 0) {
                       System.out.println("Skipping zero value");
                       continue;
                   }
                   
                   sum += number;
                   validCount++;
                   System.out.println("Processed: " + number);
                   
               } catch (NumberFormatException e) {
                   System.out.println("Skipping non-numeric value: " + item);
                   continue;
               }
           }
           
           System.out.println("\nProcessing complete:");
           System.out.println("Valid numbers processed: " + validCount);
           System.out.println("Sum: " + sum);
           if (validCount > 0) {
               System.out.println("Average: " + (double) sum / validCount);
           }
       }
   }

return Statement
~~~~~~~~~~~~~~~~

The ``return`` statement exits from a method and optionally returns a
value.

.. _examples-3:

Examples:
^^^^^^^^^

.. code:: java

   // Example 1: Basic return statement
   public class ReturnExamples {
       public static void main(String[] args) {
           System.out.println("Square of 5: " + square(5));
           System.out.println("Maximum of 10 and 15: " + max(10, 15));
           
           int[] numbers = {1, 2, 3, 4, 5};
           int target = 3;
           int index = findIndex(numbers, target);
           
           if (index != -1) {
               System.out.println("Found " + target + " at index " + index);
           } else {
               System.out.println(target + " not found in array");
           }
           
           // Demonstrating void method with return
           printPositiveNumbers(new int[]{-1, 2, -3, 4, 5});
       }
       
       // Method returning a calculated value
       public static int square(int number) {
           return number * number;
       }
       
       // Method with multiple return statements
       public static int max(int a, int b) {
           if (a > b) {
               return a;
           } else {
               return b;
           }
       }
       
       // Method returning -1 if not found
       public static int findIndex(int[] array, int target) {
           for (int i = 0; i < array.length; i++) {
               if (array[i] == target) {
                   return i; // Early return when found
               }
           }
           return -1; // Not found
       }
       
       // Void method with early return
       public static void printPositiveNumbers(int[] numbers) {
           if (numbers == null || numbers.length == 0) {
               System.out.println("No numbers to process");
               return; // Early exit
           }
           
           System.out.println("Positive numbers:");
           for (int number : numbers) {
               if (number > 0) {
                   System.out.print(number + " ");
               }
           }
           System.out.println();
       }
   }

.. code:: java

   // Example 2: Factorial with return
   public class FactorialRecursive {
       public static void main(String[] args) {
           for (int i = 0; i <= 5; i++) {
               System.out.println(i + "! = " + factorial(i));
           }
       }
       
       public static long factorial(int n) {
           if (n < 0) {
               return -1; // Error case
           }
           if (n == 0 || n == 1) {
               return 1; // Base case
           }
           return n * factorial(n - 1); // Recursive case
       }
   }

.. code:: java

   // Example 3: Grade calculator with validation
   public class GradeValidator {
       public static void main(String[] args) {
           int[] scores = {85, 92, 78, -5, 105, 88};
           
           for (int score : scores) {
               String grade = calculateGrade(score);
               if (grade != null) {
                   System.out.println("Score: " + score + " -> Grade: " + grade);
               } else {
                   System.out.println("Score: " + score + " -> Invalid score");
               }
           }
       }
       
       public static String calculateGrade(int score) {
           // Validate input
           if (score < 0 || score > 100) {
               return null; // Invalid score
           }
           
           if (score >= 90) return "A";
           if (score >= 80) return "B";
           if (score >= 70) return "C";
           if (score >= 60) return "D";
           return "F";
       }
   }

--------------

Advanced Flow Control Concepts
------------------------------

Nested Control Structures
~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   // Complex nested example: Student grade analysis
   public class GradeAnalysis {
       public static void main(String[] args) {
           int[][] studentScores = {
               {85, 92, 78, 88, 90}, // Student 1
               {76, 81, 85, 79, 82}, // Student 2
               {95, 98, 94, 96, 97}, // Student 3
               {65, 70, 68, 72, 69}  // Student 4
           };
           
           String[] subjects = {"Math", "Science", "English", "History", "Art"};
           
           for (int student = 0; student < studentScores.length; student++) {
               System.out.println("\n=== Student " + (student + 1) + " Analysis ===");
               
               int totalScore = 0;
               int passedSubjects = 0;
               String failedSubjects = "";
               
               for (int subject = 0; subject < studentScores[student].length; subject++) {
                   int score = studentScores[student][subject];
                   totalScore += score;
                   
                   System.out.print(subjects[subject] + ": " + score);
                   
                   if (score >= 80) {
                       System.out.println(" (Excellent)");
                       passedSubjects++;
                   } else if (score >= 70) {
                       System.out.println(" (Good)");
                       passedSubjects++;
                   } else if (score >= 60) {
                       System.out.println(" (Pass)");
                       passedSubjects++;
                   } else {
                       System.out.println(" (Fail)");
                       if (!failedSubjects.isEmpty()) {
                           failedSubjects += ", ";
                       }
                       failedSubjects += subjects[subject];
                   }
               }
               
               double average = (double) totalScore / studentScores[student].length;
               System.out.printf("Average: %.2f\n", average);
               System.out.println("Passed subjects: " + passedSubjects + "/" + subjects.length);
               
               if (!failedSubjects.isEmpty()) {
                   System.out.println("Failed subjects: " + failedSubjects);
               }
               
               // Overall grade
               if (average >= 90) {
                   System.out.println("Overall Grade: A (Outstanding)");
               } else if (average >= 80) {
                   System.out.println("Overall Grade: B (Good)");
               } else if (average >= 70) {
                   System.out.println("Overall Grade: C (Average)");
               } else if (average >= 60) {
                   System.out.println("Overall Grade: D (Below Average)");
               } else {
                   System.out.println("Overall Grade: F (Fail)");
               }
           }
       }
   }

Loop Control with Flags
~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   // Using boolean flags for complex loop control
   import java.util.Scanner;

   public class FlagControlExample {
       public static void main(String[] args) {
           Scanner scanner = new Scanner(System.in);
           boolean continueProgram = true;
           boolean validInput = false;
           
           System.out.println("=== Number Processing System ===");
           
           while (continueProgram) {
               int number = 0;
               validInput = false;
               
               // Input validation loop
               while (!validInput) {
                   System.out.print("Enter a positive number (or 0 to exit): ");
                   try {
                       number = Integer.parseInt(scanner.nextLine());
                       if (number < 0) {
                           System.out.println("Please enter a positive number!");
                       } else {
                           validInput = true;
                       }
                   } catch (NumberFormatException e) {
                       System.out.println("Invalid input! Please enter a valid number.");
                   }
               }
               
               if (number == 0) {
                   continueProgram = false;
                   System.out.println("Exiting program...");
                   continue;
               }
               
               // Process the number
               System.out.println("\nProcessing number: " + number);
               
               // Check if prime
               boolean isPrime = true;
               if (number <= 1) {
                   isPrime = false;
               } else {
                   for (int i = 2; i <= Math.sqrt(number); i++) {
                       if (number % i == 0) {
                           isPrime = false;
                           break;
                       }
                   }
               }
               
               System.out.println("Is prime: " + isPrime);
               
               // Find factors
               System.out.print("Factors: ");
               for (int i = 1; i <= number; i++) {
                   if (number % i == 0) {
                       System.out.print(i + " ");
                   }
               }
               System.out.println();
           }
           
           scanner.close();
       }
   }

--------------

Best Practices and Common Pitfalls
----------------------------------

Best Practices
~~~~~~~~~~~~~~

.. code:: java

   // Best practices demonstration
   public class BestPractices {
       public static void main(String[] args) {
           // 1. Always use braces for clarity
           int x = 5;
           
           // Good: Always use braces
           if (x > 0) {
               System.out.println("Positive");
           }
           
           // Avoid: Single statement without braces (error-prone)
           // if (x > 0)
           //     System.out.println("Positive"); // Can cause issues when adding more statements
           
           // 2. Proper variable scope
           // Declare loop variables in the loop when possible
           for (int i = 0; i < 5; i++) {
               // i is only available within this loop
               System.out.println("Loop iteration: " + i);
           }
           
           // 3. Meaningful variable names in loops
           String[] studentNames = {"Alice", "Bob", "Charlie"};
           for (String studentName : studentNames) { // Clear what we're iterating over
               System.out.println("Student: " + studentName);
           }
           
           // 4. Avoid infinite loops without clear exit conditions
           int attempts = 0;
           int maxAttempts = 5;
           while (attempts < maxAttempts) {
               System.out.println("Attempt: " + (attempts + 1));
               attempts++;
               // Clear increment and exit condition
           }
           
           // 5. Use appropriate loop type
           // Use for loop when count is known
           for (int i = 0; i < 10; i++) {
               // Do something 10 times
           }
           
           // Use while loop when condition-based
           boolean condition = true;
           int counter = 0;
           while (condition) {
               counter++;
               if (counter >= 3) {
                   condition = false;
               }
           }
           
           // 6. Proper break and continue usage
           int[] numbers = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
           
           // Find first even number greater than 5
           for (int number : numbers) {
               if (number <= 5) {
                   continue; // Skip numbers <= 5
               }
               if (number % 2 == 0) {
                   System.out.println("Found: " + number);
                   break; // Found what we need, exit
               }
           }
       }
   }

Common Pitfalls and How to Avoid Them
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   // Common mistakes and solutions
   public class CommonPitfalls {
       public static void main(String[] args) {
           // 1. Off-by-one errors
           System.out.println("=== Off-by-one Error Examples ===");
           
           int[] array = {1, 2, 3, 4, 5};
           
           // Wrong: This will cause IndexOutOfBoundsException
           // for (int i = 0; i <= array.length; i++) {
           //     System.out.println(array[i]);
           // }
           
           // Correct: Use < instead of <=
           for (int i = 0; i < array.length; i++) {
               System.out.println("Element " + i + ": " + array[i]);
           }
           
           // 2. Infinite loops
           System.out.println("\n=== Infinite Loop Prevention ===");
           
           // Wrong: This creates an infinite loop
           // int i = 0;
           // while (i < 5) {
           //     System.out.println(i);
           //     // Forgot to increment i!
           // }
           
           // Correct: Always ensure loop variable changes
           int i = 0;
           while (i < 5) {
               System.out.println("Safe loop: " + i);
               i++; // Don't forget to increment!
           }
           
           // 3. Switch statement without break
           System.out.println("\n=== Switch Fall-through Issue ===");
           
           int day = 2;
           System.out.println("Without proper breaks:");
           
           // Demonstrating fall-through (usually unintended)
           switch (day) {
               case 1:
                   System.out.println("Monday");
                   // Missing break - falls through to next case
               case 2:
                   System.out.println("Tuesday");
                   // Missing break - falls through to next case
               case 3:
                   System.out.println("Wednesday");
                   break; // Finally breaks here
               default:
                   System.out.println("Other day");
           }
           
           System.out.println("With proper breaks:");
           // Correct version
           switch (day) {
               case 1:
                   System.out.println("Monday");
                   break;
               case 2:
                   System.out.println("Tuesday");
                   break;
               case 3:
                   System.out.println("Wednesday");
                   break;
               default:
                   System.out.println("Other day");
           }
           
           // 4. Modifying collection while iterating
           System.out.println("\n=== Collection Modification Issues ===");
           
           java.util.List<Integer> numbers = new java.util.ArrayList<>();
           numbers.add(1);
           numbers.add(2);
           numbers.add(3);
           numbers.add(4);
           numbers.add(5);
           
           // Wrong: Modifying list while iterating
           // for (Integer number : numbers) {
           //     if (number % 2 == 0) {
           //         numbers.remove(number); // ConcurrentModificationException!
           //     }
           // }
           
           // Correct: Use iterator or collect indices to remove
           java.util.Iterator<Integer> iterator = numbers.iterator();
           while (iterator.hasNext()) {
               Integer number = iterator.next();
               if (number % 2 == 0) {
                   iterator.remove(); // Safe removal
                   System.out.println("Removed even number: " + number);
               }
           }
           
           System.out.println("Remaining numbers: " + numbers);
           
           // 5. Variable scope issues
           System.out.println("\n=== Variable Scope Issues ===");
           
           // Wrong: Trying to use loop variable outside its scope
           // for (int j = 0; j < 5; j++) {
           //     // j is only available here
           // }
           // System.out.println(j); // Compilation error - j not in scope
           
           // Correct: Declare variable in appropriate scope
           int j; // Declare outside if needed outside
           for (j = 0; j < 5; j++) {
               // Use j here
           }
           System.out.println("Final value of j: " + j);
       }
   }

--------------

Real-World Applications
-----------------------

Example 1: ATM Transaction System
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   import java.util.Scanner;

   public class ATMSystem {
       private static double balance = 1000.0; // Initial balance
       private static Scanner scanner = new Scanner(System.in);
       
       public static void main(String[] args) {
           System.out.println("=== Welcome to ATM System ===");
           
           boolean continueTransaction = true;
           int failedAttempts = 0;
           final int MAX_ATTEMPTS = 3;
           
           // PIN verification
           while (failedAttempts < MAX_ATTEMPTS) {
               System.out.print("Enter your PIN: ");
               String enteredPIN = scanner.nextLine();
               
               if (enteredPIN.equals("1234")) {
                   System.out.println("PIN verified successfully!");
                   break;
               } else {
                   failedAttempts++;
                   System.out.println("Incorrect PIN. Attempts remaining: " + (MAX_ATTEMPTS - failedAttempts));
                   
                   if (failedAttempts >= MAX_ATTEMPTS) {
                       System.out.println("Too many failed attempts. Card blocked!");
                       return;
                   }
               }
           }
           
           // Main transaction loop
           while (continueTransaction) {
               displayMenu();
               
               int choice = getValidChoice();
               
               switch (choice) {
                   case 1:
                       checkBalance();
                       break;
                   case 2:
                       withdraw();
                       break;
                   case 3:
                       deposit();
                       break;
                   case 4:
                       System.out.println("Thank you for using our ATM. Goodbye!");
                       continueTransaction = false;
                       break;
                   default:
                       System.out.println("Invalid choice. Please try again.");
               }
               
               if (continueTransaction) {
                   System.out.print("Do you want to perform another transaction? (y/n): ");
                   String response = scanner.nextLine().toLowerCase();
                   if (!response.equals("y") && !response.equals("yes")) {
                       continueTransaction = false;
                       System.out.println("Thank you for using our ATM. Goodbye!");
                   }
               }
           }
           
           scanner.close();
       }
       
       private static void displayMenu() {
           System.out.println("\n=== ATM Menu ===");
           System.out.println("1. Check Balance");
           System.out.println("2. Withdraw Money");
           System.out.println("3. Deposit Money");
           System.out.println("4. Exit");
       }
       
       private static int getValidChoice() {
           int choice = 0;
           boolean validInput = false;
           
           while (!validInput) {
               System.out.print("Enter your choice (1-4): ");
               try {
                   choice = Integer.parseInt(scanner.nextLine());
                   if (choice >= 1 && choice <= 4) {
                       validInput = true;
                   } else {
                       System.out.println("Please enter a number between 1 and 4.");
                   }
               } catch (NumberFormatException e) {
                   System.out.println("Invalid input. Please enter a number.");
               }
           }
           
           return choice;
       }
       
       private static void checkBalance() {
           System.out.printf("Your current balance is: $%.2f\n", balance);
       }
       
       private static void withdraw() {
           double amount = getValidAmount("Enter amount to withdraw: $");
           
           if (amount > balance) {
               System.out.println("Insufficient funds!");
               System.out.printf("Available balance: $%.2f\n", balance);
           } else {
               balance -= amount;
               System.out.printf("Successfully withdrawn $%.2f\n", amount);
               System.out.printf("Remaining balance: $%.2f\n", balance);
           }
       }
       
       private static void deposit() {
           double amount = getValidAmount("Enter amount to deposit: $");
           balance += amount;
           System.out.printf("Successfully deposited $%.2f\n", amount);
           System.out.printf("New balance: $%.2f\n", balance);
       }
       
       private static double getValidAmount(String prompt) {
           double amount = 0;
           boolean validInput = false;
           
           while (!validInput) {
               System.out.print(prompt);
               try {
                   amount = Double.parseDouble(scanner.nextLine());
                   if (amount <= 0) {
                       System.out.println("Amount must be positive!");
                   } else if (amount > 10000) {
                       System.out.println("Maximum transaction limit is $10,000");
                   } else {
                       validInput = true;
                   }
               } catch (NumberFormatException e) {
                   System.out.println("Invalid amount. Please enter a valid number.");
               }
           }
           
           return amount;
       }
   }

Example 2: Simple Inventory Management System
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   import java.util.*;

   public class InventoryManagement {
       private static Map<String, Integer> inventory = new HashMap<>();
       private static Scanner scanner = new Scanner(System.in);
       
       public static void main(String[] args) {
           // Initialize some sample inventory
           inventory.put("laptop", 10);
           inventory.put("mouse", 25);
           inventory.put("keyboard", 15);
           inventory.put("monitor", 8);
           
           System.out.println("=== Inventory Management System ===");
           
           boolean running = true;
           while (running) {
               displayMenu();
               int choice = getChoice();
               
               switch (choice) {
                   case 1:
                       displayInventory();
                       break;
                   case 2:
                       addItem();
                       break;
                   case 3:
                       updateQuantity();
                       break;
                   case 4:
                       removeItem();
                       break;
                   case 5:
                       searchItem();
                       break;
                   case 6:
                       generateReport();
                       break;
                   case 7:
                       System.out.println("Exiting system. Goodbye!");
                       running = false;
                       break;
                   default:
                       System.out.println("Invalid choice. Please try again.");
               }
           }
           
           scanner.close();
       }
       
       private static void displayMenu() {
           System.out.println("\n=== Main Menu ===");
           System.out.println("1. Display Inventory");
           System.out.println("2. Add New Item");
           System.out.println("3. Update Quantity");
           System.out.println("4. Remove Item");
           System.out.println("5. Search Item");
           System.out.println("6. Generate Report");
           System.out.println("7. Exit");
       }
       
       private static int getChoice() {
           int choice = 0;
           boolean validInput = false;
           
           while (!validInput) {
               System.out.print("Enter your choice: ");
               try {
                   choice = Integer.parseInt(scanner.nextLine());
                   validInput = true;
               } catch (NumberFormatException e) {
                   System.out.println("Invalid input. Please enter a number.");
               }
           }
           
           return choice;
       }
       
       private static void displayInventory() {
           if (inventory.isEmpty()) {
               System.out.println("Inventory is empty!");
               return;
           }
           
           System.out.println("\n=== Current Inventory ===");
           System.out.printf("%-15s %s\n", "Item", "Quantity");
           System.out.println("-------------------------");
           
           for (Map.Entry<String, Integer> entry : inventory.entrySet()) {
               System.out.printf("%-15s %d\n", entry.getKey(), entry.getValue());
           }
       }
       
       private static void addItem() {
           System.out.print("Enter item name: ");
           String itemName = scanner.nextLine().toLowerCase().trim();
           
           if (itemName.isEmpty()) {
               System.out.println("Item name cannot be empty!");
               return;
           }
           
           if (inventory.containsKey(itemName)) {
               System.out.println("Item already exists! Use 'Update Quantity' to modify.");
               return;
           }
           
           int quantity = getValidQuantity("Enter quantity: ");
           inventory.put(itemName, quantity);
           System.out.println("Item '" + itemName + "' added successfully with quantity " + quantity);
       }
       
       private static void updateQuantity() {
           if (inventory.isEmpty()) {
               System.out.println("Inventory is empty!");
               return;
           }
           
           System.out.print("Enter item name to update: ");
           String itemName = scanner.nextLine().toLowerCase().trim();
           
           if (!inventory.containsKey(itemName)) {
               System.out.println("Item not found in inventory!");
               return;
           }
           
           System.out.println("Current quantity: " + inventory.get(itemName));
           int newQuantity = getValidQuantity("Enter new quantity: ");
           
           inventory.put(itemName, newQuantity);
           System.out.println("Quantity updated successfully!");
       }
       
       private static void removeItem() {
           if (inventory.isEmpty()) {
               System.out.println("Inventory is empty!");
               return;
           }
           
           System.out.print("Enter item name to remove: ");
           String itemName = scanner.nextLine().toLowerCase().trim();
           
           if (inventory.containsKey(itemName)) {
               inventory.remove(itemName);
               System.out.println("Item '" + itemName + "' removed successfully!");
           } else {
               System.out.println("Item not found in inventory!");
           }
       }
       
       private static void searchItem() {
           if (inventory.isEmpty()) {
               System.out.println("Inventory is empty!");
               return;
           }
           
           System.out.print("Enter item name to search: ");
           String itemName = scanner.nextLine().toLowerCase().trim();
           
           boolean found = false;
           for (Map.Entry<String, Integer> entry : inventory.entrySet()) {
               if (entry.getKey().contains(itemName)) {
                   System.out.printf("Found: %s - Quantity: %d\n", entry.getKey(), entry.getValue());
                   found = true;
               }
           }
           
           if (!found) {
               System.out.println("No items found matching '" + itemName + "'");
           }
       }
       
       private static void generateReport() {
           if (inventory.isEmpty()) {
               System.out.println("Inventory is empty!");
               return;
           }
           
           System.out.println("\n=== Inventory Report ===");
           
           int totalItems = 0;
           int lowStockItems = 0;
           final int LOW_STOCK_THRESHOLD = 5;
           
           for (Map.Entry<String, Integer> entry : inventory.entrySet()) {
               totalItems += entry.getValue();
               if (entry.getValue() <= LOW_STOCK_THRESHOLD) {
                   lowStockItems++;
               }
           }
           
           System.out.println("Total different items: " + inventory.size());
           System.out.println("Total quantity: " + totalItems);
           System.out.println("Low stock items (≤5): " + lowStockItems);
           
           if (lowStockItems > 0) {
               System.out.println("\nLow Stock Alert:");
               for (Map.Entry<String, Integer> entry : inventory.entrySet()) {
                   if (entry.getValue() <= LOW_STOCK_THRESHOLD) {
                       System.out.printf("- %s: %d units remaining\n", entry.getKey(), entry.getValue());
                   }
               }
           }
       }
       
       private static int getValidQuantity(String prompt) {
           int quantity = 0;
           boolean validInput = false;
           
           while (!validInput) {
               System.out.print(prompt);
               try {
                   quantity = Integer.parseInt(scanner.nextLine());
                   if (quantity < 0) {
                       System.out.println("Quantity cannot be negative!");
                   } else {
                       validInput = true;
                   }
               } catch (NumberFormatException e) {
                   System.out.println("Invalid input. Please enter a valid number.");
               }
           }
           
           return quantity;
       }
   }

--------------

Quiz Solutions
--------------

Quiz 1: Boolean if Statement
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Question:** What will be the result if we try to compile and execute
the following code?

.. code:: java

   class Sample{
       public static void main(String[]args) {
           boolean b = true;
           if(b){
               System.out.println(" if block ");
           }
           else {
               System.out.println(" else block ");
           }
       }
   }

**Answer:** The program will **compile and execute successfully** and
print:

::

    if block 

**Explanation:** - The boolean variable ``b`` is set to ``true`` - The
if condition ``if(b)`` evaluates to ``true`` - Therefore, the if block
executes and prints ” if block ” - The else block is skipped

Quiz 2: Loop Compilation Issues
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Question:** What will be the result if we try to compile and execute
the following code snippets:

**a.**

.. code:: java

   class Sample {
       public static void main(String[] args) {
           while(false)
               System.out.println("while loop");
       }
   }

**Answer:** **Compilation Error**

**Explanation:** - The compiler detects that ``while(false)`` creates
unreachable code - The statement ``System.out.println("while loop");``
will never be executed - Java compiler prevents compilation of
unreachable code - Error message: “Unreachable statement”

**b.**

.. code:: java

   class Sample {
       public static void main(String[] args) {
           for( ; ; )
               System.out.println("For loop");
       }
   }

**Answer:** **Compiles successfully but creates an infinite loop**

**Explanation:** - ``for( ; ; )`` is a valid infinite loop syntax - No
initialization, no condition (defaults to true), no increment - The
program will compile successfully - When executed, it will print “For
loop” infinitely until manually terminated - This is different from
``while(false)`` because the condition isn’t explicitly false

**Complete demonstration:**

.. code:: java

   // Quiz solutions with detailed explanation
   public class QuizSolutions {
       public static void main(String[] args) {
           System.out.println("=== Quiz 1 Solution ===");
           
           // Quiz 1: Boolean if statement
           boolean b = true;
           if(b){
               System.out.println(" if block ");
           }
           else {
               System.out.println(" else block ");
           }
           
           System.out.println("\n=== Quiz 2a Explanation ===");
           System.out.println("while(false) causes compilation error due to unreachable code");
           
           // This would cause compilation error:
           // while(false)
           //     System.out.println("This is unreachable");
           
           System.out.println("\n=== Quiz 2b Explanation ===");
           System.out.println("for(;;) compiles but creates infinite loop");
           
           // This compiles but would run forever:
           // for(;;)
           //     System.out.println("Infinite loop");
           
           // Safe demonstration with break
           int count = 0;
           for(;;) {
               System.out.println("Infinite loop iteration: " + count);
               count++;
               if (count >= 3) break; // Safety exit
           }
           
           System.out.println("\n=== Additional Examples ===");
           
           // Similar unreachable code scenarios
           System.out.println("Other unreachable code examples:");
           
           // This would also cause compilation error:
           // if (false) {
           //     System.out.println("This is also unreachable");
           // }
           
           // But this compiles (variable could change):
           boolean condition = false;
           if (condition) {
               System.out.println("This compiles because condition is variable");
           }
           
           // do-while with false still executes once
           do {
               System.out.println("do-while executes at least once");
           } while (false);
       }
   }

--------------

Summary
-------

This comprehensive guide covers all aspects of Java flow control
statements:

Key Concepts Mastered:
~~~~~~~~~~~~~~~~~~~~~~

| **Selection Statements:** - ``if`` statements for simple conditions -
  ``if-else`` for binary decisions
| - Cascading ``if-else`` for multiple conditions - ``switch``
  statements for discrete value matching - String-based switch (Java 7+)
  - Fall-through behavior and break statements

**Iteration Statements:** - ``while`` loops for condition-based
iteration - ``do-while`` loops for at-least-once execution - ``for``
loops for counter-based iteration - Enhanced ``for`` loops for
array/collection iteration - Nested loops and complex iteration patterns

**Jumping Statements:** - ``break`` for loop/switch termination -
``continue`` for skipping iterations - ``return`` for method exit and
value return - Labeled breaks for nested loop control

**Advanced Topics:** - Nested control structures - Flag-based loop
control - Input validation patterns - Menu-driven programming - Error
handling in loops - Performance considerations

Best Practices Learned:
~~~~~~~~~~~~~~~~~~~~~~~

- Always use braces for clarity and maintainability
- Choose appropriate loop types for specific scenarios
- Avoid infinite loops with proper exit conditions
- Use meaningful variable names in loop constructs
- Handle edge cases and invalid input gracefully
- Implement proper error handling and validation

.. _real-world-applications-1:

Real-World Applications:
~~~~~~~~~~~~~~~~~~~~~~~~

- ATM transaction systems with user interaction
- Inventory management with menu-driven interfaces
- Data validation and processing workflows
- Interactive console applications
- Complex business logic implementation

This foundation enables you to build sophisticated programs with proper
control flow, user interaction, and robust error handling mechanisms.

--------------

*Continue practicing with the provided examples and create your own
variations to master Java flow control statements completely.*
