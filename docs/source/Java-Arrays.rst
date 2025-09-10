Java Arrays
===========

Table of Contents
-----------------

1.  `Introduction to Arrays <#introduction-to-arrays>`__
2.  `One-Dimensional Arrays <#one-dimensional-arrays>`__
3.  `Array Initialization Methods <#array-initialization-methods>`__
4.  `Array Operations and
    Properties <#array-operations-and-properties>`__
5.  `Two-Dimensional Arrays <#two-dimensional-arrays>`__
6.  `Jagged Arrays <#jagged-arrays>`__
7.  `Multi-Dimensional Arrays <#multi-dimensional-arrays>`__
8.  `Advanced Array Concepts <#advanced-array-concepts>`__
9.  `Array Algorithms and Patterns <#array-algorithms-and-patterns>`__
10. `Best Practices and Common
    Pitfalls <#best-practices-and-common-pitfalls>`__
11. `Real-World Applications <#real-world-applications>`__
12. `Quiz Solutions <#quiz-solutions>`__

--------------

Introduction to Arrays
----------------------

What is an Array?
~~~~~~~~~~~~~~~~~

An **array** is a container object that holds a **fixed number of values
of a single type**. Arrays are one of the most fundamental data
structures in Java and provide an efficient way to store and manipulate
collections of data.

Think of an array as a row of containers, where each container can hold one item of the same type. 
These containers are numbered starting from 0, allowing you to access each item using its position (index).

.. code:: java

   public class ArrayIntroduction {
       public static void main(String[] args) {
           // An array of 5 integers
           int[] numbers = new int[5];
           
           // Storing values
           numbers[0] = 10;
           numbers[1] = 20;
           numbers[2] = 30;
           numbers[3] = 40;
           numbers[4] = 50;
           
           // Accessing values
           System.out.println("First element: " + numbers[0]);
           System.out.println("Third element: " + numbers[2]);
           
           // Getting array length
           System.out.println("Array length: " + numbers.length);
       }
   }

**Output:**

::

   First element: 10
   Third element: 30
   Array length: 5

Key Characteristics of Arrays:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. **Fixed Size**: Once created, the length of an array cannot be
   changed. You need to create a new array if you want a different size.

2. **Homogeneous**: All elements must be of the same data type. You cannot
   mix integers and strings in the same array.

3. **Indexed Access**: Elements are accessed using zero-based indexing. The first
   element is at index 0, the second at index 1, and so on.

4. **Reference Type**: Arrays are objects in Java. When you create an array,
   you are creating a reference to the array object.

5. **Default Initialization**: Elements are automatically initialized
   with default values when an array is created.

**Example of Array Characteristics:**

.. code:: java

   public class ArrayCharacteristics {
       public static void main(String[] args) {
           // 1. Fixed Size
           int[] fixed = new int[5];
           System.out.println("Fixed size: " + fixed.length);
           // fixed.length = 10; // ERROR: length is final and cannot be changed
           
           // 2. Homogeneous
           int[] numbers = new int[3];
           numbers[0] = 10;
           numbers[1] = 20;
           numbers[2] = 30;
           // numbers[1] = "Hello"; // ERROR: String cannot be stored in int array
           
           // 3. Indexed Access
           System.out.println("Element at index 0: " + numbers[0]);
           System.out.println("Element at index 2: " + numbers[2]);
           
           // 4. Reference Type
           int[] original = {1, 2, 3};
           int[] reference = original; // Both variables refer to the same array
           reference[0] = 99;
           System.out.println("Original array's first element: " + original[0]); // Will print 99
           
           // 5. Default Initialization
           int[] defaultValues = new int[3];
           System.out.println("Default int value: " + defaultValues[0]); // Prints 0
           
           boolean[] boolDefaults = new boolean[1];
           System.out.println("Default boolean value: " + boolDefaults[0]); // Prints false
           
           String[] stringDefaults = new String[1];
           System.out.println("Default String value: " + stringDefaults[0]); // Prints null
       }
   }

**Output:**

::

   Fixed size: 5
   Element at index 0: 10
   Element at index 2: 30
   Original array's first element: 99
   Default int value: 0
   Default boolean value: false
   Default String value: null

Default Values by Type:
~~~~~~~~~~~~~~~~~~~~~~~

+----------------------------------+----------------------------------+
| Data Type                        | Default Value                    |
+==================================+==================================+
| ``int``, ``byte``, ``short``,    | 0                                |
| ``long``                         |                                  |
+----------------------------------+----------------------------------+
| ``float``, ``double``            | 0.0                              |
+----------------------------------+----------------------------------+
| ``boolean``                      | false                            |
+----------------------------------+----------------------------------+
| ``char``                         | ‘:raw-latex:`\u0`000’ (null      |
|                                  | character)                       |
+----------------------------------+----------------------------------+
| ``Object`` references            | null                             |
+----------------------------------+----------------------------------+

--------------

One-Dimensional Arrays
----------------------

Array Declaration and Creation
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

There are multiple ways to declare and create arrays in Java. Each approach has specific use cases and advantages.

Method 1: Declaration and Instantiation Separately
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code:: java

   // Array declaration
   int[] numbers;              // Preferred syntax
   int numbers[];              // Alternative syntax (C-style)

   // Array instantiation
   numbers = new int[5];       // Creates array with 5 integer elements

   // Combined
   int[] scores = new int[10]; // Declare and create in one line

Method 2: Declaration with Initialization
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code:: java

   // Array literal initialization
   int[] numbers = {1, 2, 3, 4, 5};

   // Anonymous array initialization
   int[] scores = new int[]{85, 92, 78, 96, 88};

   // String array examples
   String[] names = {"Alice", "Bob", "Charlie"};

**Complete Example:**

.. code:: java

   public class ArrayCreationExample {
       public static void main(String[] args) {
           // Method 1: Declaration only
           int[] firstArray;
           
           // Now we initialize it
           firstArray = new int[3];
           firstArray[0] = 1;
           firstArray[1] = 2;
           firstArray[2] = 3;
           
           System.out.println("First array contents:");
           for (int i = 0; i < firstArray.length; i++) {
               System.out.println("Index " + i + ": " + firstArray[i]);
           }
           
           // Method 2: Declaration and creation in one step
           int[] secondArray = new int[4];
           secondArray[0] = 10;
           secondArray[1] = 20;
           secondArray[2] = 30;
           secondArray[3] = 40;
           
           System.out.println("\nSecond array contents:");
           for (int value : secondArray) { // Enhanced for loop
               System.out.println(value);
           }
           
           // Method 3: Declaration, creation, and initialization in one step
           int[] thirdArray = {100, 200, 300, 400, 500};
           
           System.out.println("\nThird array contents:");
           for (int i = 0; i < thirdArray.length; i++) {
               System.out.println("Index " + i + ": " + thirdArray[i]);
           }
           
           // Method 4: Alternative initialization syntax
           int[] fourthArray = new int[] {1000, 2000, 3000};
           
           System.out.println("\nFourth array contents:");
           for (int value : fourthArray) {
               System.out.println(value);
           }
       }
   }

**Output:**

::

   First array contents:
   Index 0: 1
   Index 1: 2
   Index 2: 3

   Second array contents:
   10
   20
   30
   40

   Third array contents:
   Index 0: 100
   Index 1: 200
   Index 2: 300
   Index 3: 400
   Index 4: 500

   Fourth array contents:
   1000
   2000
   3000

**Memory Visualization:**

When you create an array, Java allocates memory for it:

.. code:: java

   int[] numbers = new int[4];
   numbers[0] = 10;
   numbers[1] = 20;
   numbers[2] = 30;
   numbers[3] = 40;

In memory, this looks like:

::

   +--------+--------+--------+--------+
   |   10   |   20   |   30   |   40   |
   +--------+--------+--------+--------+
   ^
   |
   numbers (reference points to the first element)
   String[] cities = new String[]{"New York", "London", "Tokyo"};

Basic Array Example
~~~~~~~~~~~~~~~~~~~

This example demonstrates the fundamental operations on arrays including declaration, memory allocation, element assignment, element access, and retrieving array length.

.. code:: java

   // Basic array operations
   public class ArrayDemo {
       public static void main(String[] args) {
           // Step 1: Declare the array reference
           int[] x;                    // declares an array of integers
           
           // Step 2: Allocate memory for the array
           x = new int[5];             // allocates memory for 5 integers
           
           // Step 3: Assign values to array elements
           x[0] = 11;                  // First element
           x[4] = 22;                  // Last element
           // Note: x[1], x[2], and x[3] keep their default value (0)
           
           // Step 4: Access and print array elements
           System.out.println("Element at index 0: " + x[0]);  // 11
           System.out.println("Element at index 1: " + x[1]);  // 0 (default)
           System.out.println("Element at index 4: " + x[4]);  // 22
           
           // Step 5: Get array length
           System.out.println("Array length: " + x.length);    // 5
           
           // Step 6: Attempt to access all elements with a loop
           System.out.println("\nAll array elements:");
           for (int i = 0; i < x.length; i++) {
               System.out.println("Element at index " + i + ": " + x[i]);
           }
       }
   }

**Output:**

::

   Element at index 0: 11
   Element at index 1: 0
   Element at index 4: 22
   Array length: 5

   All array elements:
   Element at index 0: 11
   Element at index 1: 0
   Element at index 2: 0
   Element at index 3: 0
   Element at index 4: 22

**Key Points:**
1. Array indices start at 0, not 1
2. The array length is fixed when created
3. Elements not explicitly assigned receive default values (0 for int)
4. The `.length` property gives the size of the array
5. Accessing an index outside the array bounds will cause an `ArrayIndexOutOfBoundsException`

Comprehensive Array Examples
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   // Comprehensive one-dimensional array examples
   public class ArrayExamplesBasic {
       public static void main(String[] args) {
           // Different ways to create and initialize arrays
           
           // 1. Integer arrays
           int[] numbers1 = new int[5];                    // [0, 0, 0, 0, 0]
           int[] numbers2 = {10, 20, 30, 40, 50};         // Direct initialization
           int[] numbers3 = new int[]{1, 3, 5, 7, 9};     // Anonymous array
           
           // 2. String arrays
           String[] fruits = {"Apple", "Banana", "Cherry", "Date"};
           String[] colors = new String[3];               // [null, null, null]
           colors[0] = "Red";
           colors[1] = "Green";
           colors[2] = "Blue";
           
           // 3. Boolean arrays
           boolean[] flags = new boolean[4];              // [false, false, false, false]
           boolean[] states = {true, false, true, false};
           
           // 4. Character arrays
           char[] vowels = {'a', 'e', 'i', 'o', 'u'};
           char[] alphabet = new char[26];
           for (int i = 0; i < alphabet.length; i++) {
               alphabet[i] = (char) ('A' + i);
           }
           
           // 5. Double arrays
           double[] prices = {19.99, 29.99, 9.99, 49.99};
           double[] temperatures = new double[7];         // Week temperatures
           
           // Display arrays
           System.out.println("Numbers2: " + java.util.Arrays.toString(numbers2));
           System.out.println("Fruits: " + java.util.Arrays.toString(fruits));
           System.out.println("Colors: " + java.util.Arrays.toString(colors));
           System.out.println("Vowels: " + java.util.Arrays.toString(vowels));
           System.out.println("First 10 letters: " + java.util.Arrays.toString(
               java.util.Arrays.copyOf(alphabet, 10)));
       }
   }

--------------

Array Initialization Methods
----------------------------

Static Initialization (Compile-time)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   public class ArrayInitialization {
       public static void main(String[] args) {
           // Static initialization - values known at compile time
           
           // Method 1: Array literals
           int[] fibonacci = {1, 1, 2, 3, 5, 8, 13, 21};
           
           // Method 2: Anonymous arrays
           String[] weekdays = new String[]{"Mon", "Tue", "Wed", "Thu", "Fri"};
           
           // Method 3: Multi-line initialization for readability
           int[] primes = {
               2, 3, 5, 7, 11, 13, 17, 19, 23, 29,
               31, 37, 41, 43, 47, 53, 59, 61, 67, 71
           };
           
           // Method 4: Mixed data types (using Object array)
           Object[] mixed = {"Hello", 42, 3.14, true, 'A'};
           
           System.out.println("Fibonacci: " + java.util.Arrays.toString(fibonacci));
           System.out.println("Weekdays: " + java.util.Arrays.toString(weekdays));
           System.out.println("First 10 primes: " + java.util.Arrays.toString(
               java.util.Arrays.copyOf(primes, 10)));
       }
   }

Dynamic Initialization (Runtime)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   import java.util.Scanner;
   import java.util.Random;

   public class DynamicArrayInit {
       public static void main(String[] args) {
           Scanner scanner = new Scanner(System.in);
           Random random = new Random();
           
           // 1. User input initialization
           System.out.print("Enter array size: ");
           int size = scanner.nextInt();
           int[] userArray = new int[size];
           
           System.out.println("Enter " + size + " numbers:");
           for (int i = 0; i < userArray.length; i++) {
               System.out.print("Element " + i + ": ");
               userArray[i] = scanner.nextInt();
           }
           
           // 2. Random initialization
           int[] randomArray = new int[10];
           for (int i = 0; i < randomArray.length; i++) {
               randomArray[i] = random.nextInt(100) + 1; // 1-100
           }
           
           // 3. Mathematical sequence initialization
           int[] squares = new int[10];
           for (int i = 0; i < squares.length; i++) {
               squares[i] = (i + 1) * (i + 1); // 1, 4, 9, 16, ...
           }
           
           // 4. Pattern-based initialization
           String[] pattern = new String[5];
           for (int i = 0; i < pattern.length; i++) {
               pattern[i] = "*".repeat(i + 1);
           }
           
           // Display results
           System.out.println("User array: " + java.util.Arrays.toString(userArray));
           System.out.println("Random array: " + java.util.Arrays.toString(randomArray));
           System.out.println("Squares: " + java.util.Arrays.toString(squares));
           System.out.println("Pattern: " + java.util.Arrays.toString(pattern));
           
           scanner.close();
       }
   }

--------------

Array Operations and Properties
-------------------------------

Array Length and Bounds
~~~~~~~~~~~~~~~~~~~~~~~

Understanding array length and bounds is crucial for working with arrays safely. Arrays in Java have a fixed size once created, and attempting to access elements outside these bounds will cause runtime errors.

.. code:: java

   public class ArrayBounds {
       public static void main(String[] args) {
           int[] numbers = {10, 20, 30, 40, 50};
           
           // 1. Array length property
           System.out.println("Array length: " + numbers.length);
           
           // 2. Valid array access (indices range from 0 to length-1)
           System.out.println("First element (index 0): " + numbers[0]);           
           System.out.println("Last element (index " + (numbers.length - 1) + "): " + 
                              numbers[numbers.length - 1]); 
           
           // 3. Array bounds checking - what happens when we go out of bounds
           System.out.println("\nDemonstrating bounds checking:");
           try {
               System.out.println("Attempting to access index 5...");
               System.out.println("Value at index 5: " + numbers[5]); // This will cause an exception
           } catch (ArrayIndexOutOfBoundsException e) {
               System.out.println("Error caught: " + e.getMessage());
               System.out.println("The valid range is 0 to " + (numbers.length - 1));
           }
           
           // 4. Safe array access pattern - always check bounds before accessing
           System.out.println("\nSafe array access pattern:");
           int[] indices = {2, 4, 10, -1};
           
           for (int index : indices) {
               if (index >= 0 && index < numbers.length) {
                   System.out.println("Element at index " + index + ": " + numbers[index]);
               } else {
                   System.out.println("Index " + index + " is out of bounds (valid range: 0-" + 
                                      (numbers.length - 1) + ")");
               }
           }
           
           // 5. Common bounds-related patterns
           System.out.println("\nCommon array patterns:");
           System.out.println("First element: " + numbers[0]);
           System.out.println("Last element: " + numbers[numbers.length - 1]);
           System.out.println("Middle element: " + numbers[numbers.length / 2]);
       }
   }

**Output:**

::

   Array length: 5
   First element (index 0): 10
   Last element (index 4): 50

   Demonstrating bounds checking:
   Attempting to access index 5...
   Error caught: Index 5 out of bounds for length 5
   The valid range is 0 to 4

   Safe array access pattern:
   Element at index 2: 30
   Element at index 4: 50
   Index 10 is out of bounds (valid range: 0-4)
   Index -1 is out of bounds (valid range: 0-4)

   Common array patterns:
   First element: 10
   Last element: 50
   Middle element: 30

**Important Points About Array Bounds:**

1. The valid indices for an array of length `n` are `0` to `n-1`
2. Accessing an index outside this range will throw an `ArrayIndexOutOfBoundsException`
3. Java does not perform automatic bounds checking - it's the programmer's responsibility
4. Always validate user input or calculated indices before using them to access array elements
5. Use defensive programming by checking bounds when the index might be out of range
   }

Array Resizing and Reference Reassignment
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   // Array resizing demonstration (from course material)
   public class ArrayResizing {
       public static void main(String[] args) {
           // Original array
           int[] x = new int[5];
           for (int i = 0; i < x.length; i++) {
               x[i] = i * 10;
           }
           System.out.println("Original array: " + java.util.Arrays.toString(x));
           
           // Can't resize array, but can reassign reference (from course material)
           x = new int[10];  // New array, old one eligible for garbage collection
           
           // Initialize new array
           for (int i = 0; i < x.length; i++) {
               x[i] = i * 5;
           }
           System.out.println("New array: " + java.util.Arrays.toString(x));
           
           // Manual "resizing" by copying elements
           int[] originalArray = {1, 2, 3, 4, 5};
           int[] largerArray = new int[10];
           
           // Copy elements from original to larger array
           for (int i = 0; i < originalArray.length; i++) {
               largerArray[i] = originalArray[i];
           }
           
           System.out.println("Original: " + java.util.Arrays.toString(originalArray));
           System.out.println("Resized: " + java.util.Arrays.toString(largerArray));
           
           // Using System.arraycopy() for better performance
           int[] source = {10, 20, 30, 40, 50};
           int[] destination = new int[8];
           System.arraycopy(source, 0, destination, 0, source.length);
           
           System.out.println("System.arraycopy result: " + java.util.Arrays.toString(destination));
           
           // Using Arrays.copyOf() method
           int[] copied = java.util.Arrays.copyOf(source, 8);
           System.out.println("Arrays.copyOf result: " + java.util.Arrays.toString(copied));
       }
   }

Array Traversal Methods
~~~~~~~~~~~~~~~~~~~~~~~

There are several ways to traverse (iterate through) arrays in Java. Each method has its own advantages and use cases. Understanding these different approaches will help you write more efficient and cleaner code.

.. code:: java

   public class ArrayTraversal {
       public static void main(String[] args) {
           // Sample array for demonstration
           int[] numbers = {15, 23, 8, 42, 7, 19, 34};
           
           System.out.println("=== Array Traversal Methods ===");
           
           // 1. Traditional for loop
           // Advantages: Access to index, flexible iteration (step size, direction)
           System.out.println("1. Traditional for loop:");
           for (int i = 0; i < numbers.length; i++) {
               System.out.print(numbers[i] + " ");
           }
           System.out.println();
           
           // 2. Enhanced for loop (for-each)
           // Advantages: Cleaner syntax, less error-prone, better for reading-only
           System.out.println("2. Enhanced for loop (for-each):");
           for (int number : numbers) {
               System.out.print(number + " ");
           }
           System.out.println();
           
           // 3. While loop
           // Advantages: Good when iteration depends on a condition
           System.out.println("3. While loop:");
           int i = 0;
           while (i < numbers.length) {
               System.out.print(numbers[i] + " ");
               i++;
           }
           System.out.println();
           
           // 4. Reverse traversal
           // Advantage: Processing elements in reverse order
           System.out.println("4. Reverse traversal:");
           for (int j = numbers.length - 1; j >= 0; j--) {
               System.out.print(numbers[j] + " ");
           }
           System.out.println();
           
           // 5. Traversal with index and value
           // Advantage: When you need both index and value
           System.out.println("5. Index and value:");
           for (int k = 0; k < numbers.length; k++) {
               System.out.println("Index " + k + ": " + numbers[k]);
           }
           
           // 6. Skip elements (every other element)
           System.out.println("6. Skip elements (every other):");
           for (int m = 0; m < numbers.length; m += 2) {
               System.out.print(numbers[m] + " ");
           }
           System.out.println();
           
           // 7. Partial traversal
           System.out.println("7. Partial traversal (middle portion):");
           int start = 2;
           int end = 5;
           for (int n = start; n < end && n < numbers.length; n++) {
               System.out.print(numbers[n] + " ");
           }
           System.out.println();
       }
   }

**Output:**

::

   === Array Traversal Methods ===
   1. Traditional for loop:
   15 23 8 42 7 19 34 
   2. Enhanced for loop (for-each):
   15 23 8 42 7 19 34 
   3. While loop:
   15 23 8 42 7 19 34 
   4. Reverse traversal:
   34 19 7 42 8 23 15 
   5. Index and value:
   Index 0: 15
   Index 1: 23
   Index 2: 8
   Index 3: 42
   Index 4: 7
   Index 5: 19
   Index 6: 34
   6. Skip elements (every other):
   15 8 7 34 
   7. Partial traversal (middle portion):
   8 42 7 

**Choosing the Right Traversal Method:**

1. **Enhanced for-loop (for-each)** 
   - Best for: Reading all elements in order
   - Limitations: No access to index, cannot modify the array structure

2. **Traditional for-loop** 
   - Best for: When you need the index, skip elements, or custom iteration order
   - Advantages: Most flexible method, can iterate in any direction or pattern

3. **While loop** 
   - Best for: When the exit condition is complex or not known in advance
   - Use case: When you might need to exit early based on conditions

4. **Reverse traversal** 
   - Best for: Processing elements from the end to the beginning
   - Use case: Stack-like processing, reversing an array

5. **Partial traversal** 
   - Best for: When you only need to process a specific range of elements
   - Use case: Working with subarrays or segments
           }
       }
   }

--------------

Two-Dimensional Arrays
----------------------

Basic Two-Dimensional Arrays
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   // Two-dimensional arrays (from course material)
   public class TwoDimensionalArrays {
       public static void main(String[] args) {
           // Different ways to create 2D arrays
           
           // 1. Standard rectangular array
           int[][] matrix1 = new int[3][3];
           
           // 2. Array literal initialization (from course material)
           int[][] matrix2 = { {1,2,3}, {4,5,6}, {7,8,9} };
           
           // 3. Anonymous array initialization (from course material)
           int[][] matrix3 = new int[][] { {1,2,3}, {4,5,6}, {7,8,9} };
           
           // Fill matrix1 with values
           int value = 1;
           for (int i = 0; i < matrix1.length; i++) {
               for (int j = 0; j < matrix1[i].length; j++) {
                   matrix1[i][j] = value++;
               }
           }
           
           // Display matrices
           System.out.println("Matrix 1 (3x3):");
           displayMatrix(matrix1);
           
           System.out.println("\nMatrix 2 (initialized with values):");
           displayMatrix(matrix2);
           
           System.out.println("\nMatrix 3 (anonymous array):");
           displayMatrix(matrix3);
       }
       
       // Helper method to display 2D array
       public static void displayMatrix(int[][] matrix) {
           for (int i = 0; i < matrix.length; i++) {
               for (int j = 0; j < matrix[i].length; j++) {
                   System.out.print(matrix[i][j] + " ");
               }
               System.out.println();
           }
       }
   }

Advanced Two-Dimensional Array Operations
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   // Advanced 2D array operations
   public class Advanced2DArrays {
       public static void main(String[] args) {
           // Create and populate a 2D array
           int[][] matrix = {
               {1, 2, 3, 4},
               {5, 6, 7, 8},
               {9, 10, 11, 12}
           };
           
           System.out.println("Original Matrix:");
           displayMatrix(matrix);
           
           // Matrix operations
           System.out.println("\n=== Matrix Analysis ===");
           
           // 1. Sum of all elements
           int totalSum = 0;
           for (int[] row : matrix) {
               for (int element : row) {
                   totalSum += element;
               }
           }
           System.out.println("Sum of all elements: " + totalSum);
           
           // 2. Row sums
           System.out.println("Row sums:");
           for (int i = 0; i < matrix.length; i++) {
               int rowSum = 0;
               for (int j = 0; j < matrix[i].length; j++) {
                   rowSum += matrix[i][j];
               }
               System.out.println("Row " + i + ": " + rowSum);
           }
           
           // 3. Column sums
           System.out.println("Column sums:");
           for (int j = 0; j < matrix[0].length; j++) {
               int colSum = 0;
               for (int i = 0; i < matrix.length; i++) {
                   colSum += matrix[i][j];
               }
               System.out.println("Column " + j + ": " + colSum);
           }
           
           // 4. Find maximum element
           int max = matrix[0][0];
           int maxRow = 0, maxCol = 0;
           for (int i = 0; i < matrix.length; i++) {
               for (int j = 0; j < matrix[i].length; j++) {
                   if (matrix[i][j] > max) {
                       max = matrix[i][j];
                       maxRow = i;
                       maxCol = j;
                   }
               }
           }
           System.out.println("Maximum element: " + max + " at position (" + maxRow + ", " + maxCol + ")");
           
           // 5. Transpose matrix
           int[][] transpose = new int[matrix[0].length][matrix.length];
           for (int i = 0; i < matrix.length; i++) {
               for (int j = 0; j < matrix[i].length; j++) {
                   transpose[j][i] = matrix[i][j];
               }
           }
           System.out.println("\nTranspose Matrix:");
           displayMatrix(transpose);
       }
       
       public static void displayMatrix(int[][] matrix) {
           for (int[] row : matrix) {
               for (int element : row) {
                   System.out.printf("%3d ", element);
               }
               System.out.println();
           }
       }
   }

--------------

Jagged Arrays
-------------

Understanding Jagged Arrays
~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   // Jagged arrays (from course material)
   public class JaggedArrays {
       public static void main(String[] args) {
           // Example from course material
           int[][] x = new int[3][];   // initialize number of rows only
           x[0] = new int[3];          // define number of columns in each row
           x[1] = new int[2];
           x[2] = new int[5];
           
           // Fill with values (from course material)
           for (int i = 0; i < x.length; i++) {
               for (int j = 0; j < x[i].length; j++) {
                   x[i][j] = i;
               }
           }
           
           // Display jagged array
           System.out.println("Jagged Array (from course):");
           for (int i = 0; i < x.length; i++) {
               for (int j = 0; j < x[i].length; j++) {
                   System.out.print(x[i][j]);
               }
               System.out.println();
           }
           
           // Alternative initialization methods (from course material)
           System.out.println("\nAlternative Jagged Array Initialization:");
           
           // Example 2 from course material
           int[][] y = new int[3][];
           y[0] = new int[]{0, 1, 2, 3};
           y[1] = new int[]{0, 1, 2};
           y[2] = new int[]{0, 1, 2, 3, 4};
           
           displayJaggedArray(y);
       }
       
       public static void displayJaggedArray(int[][] array) {
           for (int i = 0; i < array.length; i++) {
               System.out.print("Row " + i + ": ");
               for (int j = 0; j < array[i].length; j++) {
                   System.out.print(array[i][j] + " ");
               }
               System.out.println();
           }
       }
   }

Advanced Jagged Array Applications
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   // Real-world jagged array applications
   public class JaggedArrayApplications {
       public static void main(String[] args) {
           // 1. Student grades - different number of subjects per student
           String[] studentNames = {"Alice", "Bob", "Charlie", "Diana"};
           int[][] grades = {
               {85, 92, 78, 88, 95},           // Alice: 5 subjects
               {76, 81, 85},                   // Bob: 3 subjects
               {95, 98, 94, 96, 97, 89, 93},  // Charlie: 7 subjects
               {88, 82, 90, 87}               // Diana: 4 subjects
           };
           
           System.out.println("=== Student Grade Analysis ===");
           for (int i = 0; i < studentNames.length; i++) {
               System.out.print(studentNames[i] + "'s grades: ");
               int sum = 0;
               for (int grade : grades[i]) {
                   System.out.print(grade + " ");
                   sum += grade;
               }
               double average = (double) sum / grades[i].length;
               System.out.printf("| Average: %.2f\n", average);
           }
           
           // 2. Monthly sales data - different number of days per month
           String[] months = {"Jan", "Feb", "Mar", "Apr"};
           double[][] sales = {
               {1500.50, 2300.75, 1800.25, 2100.00},  // Jan: 4 weeks
               {1750.25, 2250.50, 1950.75},           // Feb: 3 weeks
               {2100.00, 2400.25, 1850.50, 2300.75, 2050.25}, // Mar: 5 weeks
               {1900.50, 2150.25}                     // Apr: 2 weeks (partial)
           };
           
           System.out.println("\n=== Monthly Sales Analysis ===");
           for (int i = 0; i < months.length; i++) {
               System.out.print(months[i] + " sales: ");
               double monthlyTotal = 0;
               for (double sale : sales[i]) {
                   System.out.printf("$%.2f ", sale);
                   monthlyTotal += sale;
               }
               System.out.printf("| Total: $%.2f\n", monthlyTotal);
           }
           
           // 3. Pascal's Triangle using jagged arrays
           System.out.println("\n=== Pascal's Triangle ===");
           int rows = 6;
           int[][] pascal = new int[rows][];
           
           for (int i = 0; i < rows; i++) {
               pascal[i] = new int[i + 1];
               pascal[i][0] = 1; // First element is always 1
               pascal[i][i] = 1; // Last element is always 1
               
               for (int j = 1; j < i; j++) {
                   pascal[i][j] = pascal[i-1][j-1] + pascal[i-1][j];
               }
           }
           
           // Display Pascal's triangle
           for (int i = 0; i < rows; i++) {
               // Add spaces for formatting
               for (int k = 0; k < rows - i - 1; k++) {
                   System.out.print(" ");
               }
               for (int j = 0; j < pascal[i].length; j++) {
                   System.out.print(pascal[i][j] + " ");
               }
               System.out.println();
           }
       }
   }

--------------

Multi-Dimensional Arrays
------------------------

Three-Dimensional Arrays and Beyond
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   // Multi-dimensional arrays
   public class MultiDimensionalArrays {
       public static void main(String[] args) {
           // 3D Array: [depth][rows][columns]
           // Think of it as a cube or multiple 2D arrays stacked
           
           // Example: RGB color values for a 3x3 image (R, G, B channels)
           int[][][] image = new int[3][3][3]; // 3x3 pixels, 3 color channels
           
           // Initialize with sample color values
           for (int row = 0; row < 3; row++) {
               for (int col = 0; col < 3; col++) {
                   image[row][col][0] = (row + col) * 50;     // Red channel
                   image[row][col][1] = (row * col) * 30;     // Green channel
                   image[row][col][2] = (row + col * 2) * 20; // Blue channel
               }
           }
           
           System.out.println("=== 3D Array: RGB Image Data ===");
           for (int row = 0; row < 3; row++) {
               for (int col = 0; col < 3; col++) {
                   System.out.printf("Pixel[%d][%d]: R=%d, G=%d, B=%d\n", 
                       row, col, image[row][col][0], image[row][col][1], image[row][col][2]);
               }
           }
           
           // Another example: 3D coordinate system
           double[][][] coordinates = {
               {{1.0, 2.0, 3.0}, {4.0, 5.0, 6.0}},   // Layer 0
               {{7.0, 8.0, 9.0}, {10.0, 11.0, 12.0}} // Layer 1
           };
           
           System.out.println("\n=== 3D Coordinates ===");
           for (int layer = 0; layer < coordinates.length; layer++) {
               System.out.println("Layer " + layer + ":");
               for (int row = 0; row < coordinates[layer].length; row++) {
                   for (int col = 0; col < coordinates[layer][row].length; col++) {
                       System.out.printf("  [%d][%d][%d] = %.1f\n", 
                           layer, row, col, coordinates[layer][row][col]);
                   }
               }
           }
           
           // 4D Array example: Time-series data with multiple metrics
           // [time_period][location][metric_type][value]
           int[][][][] timeSeries = new int[2][3][2][1]; // 2 periods, 3 locations, 2 metrics
           
           // Fill with sample data
           for (int time = 0; time < 2; time++) {
               for (int location = 0; location < 3; location++) {
                   for (int metric = 0; metric < 2; metric++) {
                       timeSeries[time][location][metric][0] = 
                           (time + 1) * (location + 1) * (metric + 1) * 10;
                   }
               }
           }
           
           System.out.println("\n=== 4D Array: Time Series Data ===");
           String[] locations = {"NYC", "LA", "Chicago"};
           String[] metrics = {"Temperature", "Humidity"};
           
           for (int time = 0; time < 2; time++) {
               System.out.println("Time Period " + (time + 1) + ":");
               for (int location = 0; location < 3; location++) {
                   for (int metric = 0; metric < 2; metric++) {
                       System.out.printf("  %s - %s: %d\n", 
                           locations[location], metrics[metric], 
                           timeSeries[time][location][metric][0]);
                   }
               }
           }
       }
   }

--------------

Advanced Array Concepts
-----------------------

Array Copying Techniques
~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   import java.util.Arrays;

   public class ArrayCopying {
       public static void main(String[] args) {
           int[] original = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
           
           System.out.println("Original array: " + Arrays.toString(original));
           
           // 1. Manual copying with loop
           int[] copy1 = new int[original.length];
           for (int i = 0; i < original.length; i++) {
               copy1[i] = original[i];
           }
           System.out.println("Manual copy: " + Arrays.toString(copy1));
           
           // 2. System.arraycopy() - most efficient
           int[] copy2 = new int[original.length];
           System.arraycopy(original, 0, copy2, 0, original.length);
           System.out.println("System.arraycopy: " + Arrays.toString(copy2));
           
           // 3. Arrays.copyOf() - creates new array
           int[] copy3 = Arrays.copyOf(original, original.length);
           System.out.println("Arrays.copyOf: " + Arrays.toString(copy3));
           
           // 4. Arrays.copyOfRange() - copy portion
           int[] copy4 = Arrays.copyOfRange(original, 2, 8); // indices 2-7
           System.out.println("Arrays.copyOfRange(2,8): " + Arrays.toString(copy4));
           
           // 5. Clone method
           int[] copy5 = original.clone();
           System.out.println("Clone method: " + Arrays.toString(copy5));
           
           // Demonstrate shallow vs deep copy with 2D arrays
           int[][] matrix2D = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};
           
           // Shallow copy - only copies references
           int[][] shallowCopy = matrix2D.clone();
           shallowCopy[0][0] = 999; // This modifies the original too!
           
           System.out.println("\n=== Shallow vs Deep Copy Demo ===");
           System.out.println("Original after shallow copy modification:");
           for (int[] row : matrix2D) {
               System.out.println(Arrays.toString(row));
           }
           
           // Deep copy - copies all elements
           int[][] deepCopy = new int[matrix2D.length][];
           for (int i = 0; i < matrix2D.length; i++) {
               deepCopy[i] = matrix2D[i].clone(); // Clone each row
           }
           deepCopy[0][1] = 888; // This doesn't affect the original
           
           System.out.println("Original after deep copy modification:");
           for (int[] row : matrix2D) {
               System.out.println(Arrays.toString(row));
           }
           System.out.println("Deep copy:");
           for (int[] row : deepCopy) {
               System.out.println(Arrays.toString(row));
           }
       }
   }

Array Utility Methods
~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   import java.util.Arrays;
   import java.util.Collections;

   public class ArrayUtilities {
       public static void main(String[] args) {
           // Sample arrays for demonstration
           int[] numbers = {64, 34, 25, 12, 22, 11, 90, 88, 76, 50, 42};
           String[] names = {"Alice", "Charlie", "Bob", "Diana", "Eve"};
           
           System.out.println("Original numbers: " + Arrays.toString(numbers));
           System.out.println("Original names: " + Arrays.toString(names));
           
           // 1. Sorting arrays
           int[] sortedNumbers = numbers.clone();
           Arrays.sort(sortedNumbers);
           System.out.println("Sorted numbers: " + Arrays.toString(sortedNumbers));
           
           String[] sortedNames = names.clone();
           Arrays.sort(sortedNames);
           System.out.println("Sorted names: " + Arrays.toString(sortedNames));
           
           // 2. Binary search (array must be sorted first)
           int searchValue = 42;
           int index = Arrays.binarySearch(sortedNumbers, searchValue);
           System.out.println("Index of " + searchValue + ": " + index);
           
           String searchName = "Charlie";
           int nameIndex = Arrays.binarySearch(sortedNames, searchName);
           System.out.println("Index of " + searchName + ": " + nameIndex);
           
           // 3. Filling arrays
           int[] filled = new int[10];
           Arrays.fill(filled, 7);
           System.out.println("Filled array: " + Arrays.toString(filled));
           
           // 4. Comparing arrays
           int[] array1 = {1, 2, 3, 4, 5};
           int[] array2 = {1, 2, 3, 4, 5};
           int[] array3 = {1, 2, 3, 4, 6};
           
           System.out.println("array1 equals array2: " + Arrays.equals(array1, array2));
           System.out.println("array1 equals array3: " + Arrays.equals(array1, array3));
           
           // 5. Converting arrays to lists and back
           Integer[] boxedNumbers = {1, 2, 3, 4, 5};
           java.util.List<Integer> numberList = Arrays.asList(boxedNumbers);
           System.out.println("Array to List: " + numberList);
           
           // Reverse using Collections
           Collections.reverse(numberList);
           System.out.println("Reversed list: " + numberList);
           
           // 6. Multi-dimensional array operations
           int[][] matrix = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};
           System.out.println("2D array toString: " + Arrays.deepToString(matrix));
           
           int[][] matrixCopy = new int[matrix.length][];
           for (int i = 0; i < matrix.length; i++) {
               matrixCopy[i] = Arrays.copyOf(matrix[i], matrix[i].length);
           }
           System.out.println("Deep copy equals: " + Arrays.deepEquals(matrix, matrixCopy));
       }
   }

--------------

Array Algorithms and Patterns
-----------------------------

Searching Algorithms
~~~~~~~~~~~~~~~~~~~~

.. code:: java

   public class ArraySearching {
       public static void main(String[] args) {
           int[] numbers = {64, 34, 25, 12, 22, 11, 90, 88, 76, 50, 42};
           int target = 22;
           
           System.out.println("Array: " + java.util.Arrays.toString(numbers));
           System.out.println("Searching for: " + target);
           
           // 1. Linear Search
           int linearResult = linearSearch(numbers, target);
           System.out.println("Linear search result: " + linearResult);
           
           // 2. Binary Search (requires sorted array)
           java.util.Arrays.sort(numbers);
           System.out.println("Sorted array: " + java.util.Arrays.toString(numbers));
           int binaryResult = binarySearch(numbers, target);
           System.out.println("Binary search result: " + binaryResult);
           
           // 3. Find all occurrences
           int[] numbersWithDuplicates = {1, 3, 5, 3, 7, 3, 9, 3};
           java.util.List<Integer> indices = findAllOccurrences(numbersWithDuplicates, 3);
           System.out.println("All occurrences of 3: " + indices);
           
           // 4. Find min and max
           int[] minMax = findMinMax(numbers);
           System.out.println("Min: " + minMax[0] + ", Max: " + minMax[1]);
       }
       
       // Linear search implementation
       public static int linearSearch(int[] array, int target) {
           for (int i = 0; i < array.length; i++) {
               if (array[i] == target) {
                   return i;
               }
           }
           return -1; // Not found
       }
       
       // Binary search implementation
       public static int binarySearch(int[] array, int target) {
           int left = 0;
           int right = array.length - 1;
           
           while (left <= right) {
               int mid = left + (right - left) / 2;
               
               if (array[mid] == target) {
                   return mid;
               } else if (array[mid] < target) {
                   left = mid + 1;
               } else {
                   right = mid - 1;
               }
           }
           return -1; // Not found
       }
       
       // Find all occurrences of a value
       public static java.util.List<Integer> findAllOccurrences(int[] array, int target) {
           java.util.List<Integer> indices = new java.util.ArrayList<>();
           for (int i = 0; i < array.length; i++) {
               if (array[i] == target) {
                   indices.add(i);
               }
           }
           return indices;
       }
       
       // Find minimum and maximum values
       public static int[] findMinMax(int[] array) {
           if (array.length == 0) return new int[]{0, 0};
           
           int min = array[0];
           int max = array[0];
           
           for (int i = 1; i < array.length; i++) {
               if (array[i] < min) min = array[i];
               if (array[i] > max) max = array[i];
           }
           
           return new int[]{min, max};
       }
   }

Sorting Algorithms
~~~~~~~~~~~~~~~~~~

.. code:: java

   public class ArraySorting {
       public static void main(String[] args) {
           int[] original = {64, 34, 25, 12, 22, 11, 90, 88, 76, 50, 42};
           
           System.out.println("Original: " + java.util.Arrays.toString(original));
           
           // Test different sorting algorithms
           testBubbleSort(original.clone());
           testSelectionSort(original.clone());
           testInsertionSort(original.clone());
           testQuickSort(original.clone());
       }
       
       public static void testBubbleSort(int[] array) {
           bubbleSort(array);
           System.out.println("Bubble Sort: " + java.util.Arrays.toString(array));
       }
       
       public static void testSelectionSort(int[] array) {
           selectionSort(array);
           System.out.println("Selection Sort: " + java.util.Arrays.toString(array));
       }
       
       public static void testInsertionSort(int[] array) {
           insertionSort(array);
           System.out.println("Insertion Sort: " + java.util.Arrays.toString(array));
       }
       
       public static void testQuickSort(int[] array) {
           quickSort(array, 0, array.length - 1);
           System.out.println("Quick Sort: " + java.util.Arrays.toString(array));
       }
       
       // Bubble Sort - O(n²)
       public static void bubbleSort(int[] array) {
           int n = array.length;
           for (int i = 0; i < n - 1; i++) {
               boolean swapped = false;
               for (int j = 0; j < n - i - 1; j++) {
                   if (array[j] > array[j + 1]) {
                       // Swap elements
                       int temp = array[j];
                       array[j] = array[j + 1];
                       array[j + 1] = temp;
                       swapped = true;
                   }
               }
               if (!swapped) break; // Array is already sorted
           }
       }
       
       // Selection Sort - O(n²)
       public static void selectionSort(int[] array) {
           int n = array.length;
           for (int i = 0; i < n - 1; i++) {
               int minIndex = i;
               for (int j = i + 1; j < n; j++) {
                   if (array[j] < array[minIndex]) {
                       minIndex = j;
                   }
               }
               // Swap minimum element with first element
               int temp = array[minIndex];
               array[minIndex] = array[i];
               array[i] = temp;
           }
       }
       
       // Insertion Sort - O(n²) but efficient for small arrays
       public static void insertionSort(int[] array) {
           int n = array.length;
           for (int i = 1; i < n; i++) {
               int key = array[i];
               int j = i - 1;
               
               // Move elements greater than key one position ahead
               while (j >= 0 && array[j] > key) {
                   array[j + 1] = array[j];
                   j = j - 1;
               }
               array[j + 1] = key;
           }
       }
       
       // Quick Sort - O(n log n) average case
       public static void quickSort(int[] array, int low, int high) {
           if (low < high) {
               int pivotIndex = partition(array, low, high);
               quickSort(array, low, pivotIndex - 1);
               quickSort(array, pivotIndex + 1, high);
           }
       }
       
       private static int partition(int[] array, int low, int high) {
           int pivot = array[high];
           int i = (low - 1);
           
           for (int j = low; j < high; j++) {
               if (array[j] <= pivot) {
                   i++;
                   int temp = array[i];
                   array[i] = array[j];
                   array[j] = temp;
               }
           }
           
           int temp = array[i + 1];
           array[i + 1] = array[high];
           array[high] = temp;
           
           return i + 1;
       }
   }

Array Manipulation Patterns
~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   public class ArrayPatterns {
       public static void main(String[] args) {
           // 1. Array rotation
           int[] array1 = {1, 2, 3, 4, 5, 6, 7};
           System.out.println("Original: " + java.util.Arrays.toString(array1));
           
           rotateLeft(array1, 3);
           System.out.println("Rotated left by 3: " + java.util.Arrays.toString(array1));
           
           // 2. Array reversal
           int[] array2 = {1, 2, 3, 4, 5, 6, 7, 8};
           System.out.println("Before reverse: " + java.util.Arrays.toString(array2));
           reverse(array2);
           System.out.println("After reverse: " + java.util.Arrays.toString(array2));
           
           // 3. Remove duplicates from sorted array
           int[] sortedWithDuplicates = {1, 1, 2, 2, 2, 3, 4, 4, 5, 5, 5, 5};
           int newLength = removeDuplicates(sortedWithDuplicates);
           System.out.println("Array after removing duplicates: " + 
               java.util.Arrays.toString(java.util.Arrays.copyOf(sortedWithDuplicates, newLength)));
           
           // 4. Merge two sorted arrays
           int[] arr1 = {1, 3, 5, 7, 9};
           int[] arr2 = {2, 4, 6, 8, 10, 12};
           int[] merged = mergeSortedArrays(arr1, arr2);
           System.out.println("Merged arrays: " + java.util.Arrays.toString(merged));
           
           // 5. Find subarray with maximum sum (Kadane's algorithm)
           int[] arrayWithNegatives = {-2, 1, -3, 4, -1, 2, 1, -5, 4};
           int maxSum = maxSubarraySum(arrayWithNegatives);
           System.out.println("Maximum subarray sum: " + maxSum);
       }
       
       // Rotate array to the left by k positions
       public static void rotateLeft(int[] array, int k) {
           int n = array.length;
           k = k % n; // Handle k > n
           
           // Create temporary array for first k elements
           int[] temp = new int[k];
           for (int i = 0; i < k; i++) {
               temp[i] = array[i];
           }
           
           // Shift remaining elements to the left
           for (int i = k; i < n; i++) {
               array[i - k] = array[i];
           }
           
           // Put back the first k elements at the end
           for (int i = 0; i < k; i++) {
               array[n - k + i] = temp[i];
           }
       }
       
       // Reverse array in place
       public static void reverse(int[] array) {
           int left = 0;
           int right = array.length - 1;
           
           while (left < right) {
               int temp = array[left];
               array[left] = array[right];
               array[right] = temp;
               left++;
               right--;
           }
       }
       
       // Remove duplicates from sorted array
       public static int removeDuplicates(int[] array) {
           if (array.length == 0) return 0;
           
           int writeIndex = 1;
           for (int readIndex = 1; readIndex < array.length; readIndex++) {
               if (array[readIndex] != array[readIndex - 1]) {
                   array[writeIndex] = array[readIndex];
                   writeIndex++;
               }
           }
           return writeIndex;
       }
       
       // Merge two sorted arrays
       public static int[] mergeSortedArrays(int[] arr1, int[] arr2) {
           int[] merged = new int[arr1.length + arr2.length];
           int i = 0, j = 0, k = 0;
           
           while (i < arr1.length && j < arr2.length) {
               if (arr1[i] <= arr2[j]) {
                   merged[k++] = arr1[i++];
               } else {
                   merged[k++] = arr2[j++];
               }
           }
           
           // Copy remaining elements
           while (i < arr1.length) {
               merged[k++] = arr1[i++];
           }
           while (j < arr2.length) {
               merged[k++] = arr2[j++];
           }
           
           return merged;
       }
       
       // Maximum subarray sum (Kadane's algorithm)
       public static int maxSubarraySum(int[] array) {
           int maxSoFar = array[0];
           int maxEndingHere = array[0];
           
           for (int i = 1; i < array.length; i++) {
               maxEndingHere = Math.max(array[i], maxEndingHere + array[i]);
               maxSoFar = Math.max(maxSoFar, maxEndingHere);
           }
           
           return maxSoFar;
       }
   }

--------------

Best Practices and Common Pitfalls
----------------------------------

Best Practices
~~~~~~~~~~~~~~

.. code:: java

   public class ArrayBestPractices {
       public static void main(String[] args) {
           // 1. Always check array bounds
           demonstrateBoundsChecking();
           
           // 2. Use enhanced for loops when possible
           demonstrateEnhancedForLoops();
           
           // 3. Prefer Arrays utility methods
           demonstrateArraysUtility();
           
           // 4. Handle null arrays gracefully
           demonstrateNullHandling();
           
           // 5. Use appropriate data types
           demonstrateDataTypeSelection();
       }
       
       public static void demonstrateBoundsChecking() {
           System.out.println("=== Bounds Checking ===");
           int[] array = {1, 2, 3, 4, 5};
           int index = 10;
           
           // Bad: No bounds checking
           // System.out.println(array[index]); // ArrayIndexOutOfBoundsException
           
           // Good: Always check bounds
           if (index >= 0 && index < array.length) {
               System.out.println("Element at index " + index + ": " + array[index]);
           } else {
               System.out.println("Index " + index + " is out of bounds for array of length " + array.length);
           }
       }
       
       public static void demonstrateEnhancedForLoops() {
           System.out.println("\n=== Enhanced For Loops ===");
           String[] names = {"Alice", "Bob", "Charlie"};
           
           // Good: Use enhanced for loop when you don't need index
           System.out.println("Names:");
           for (String name : names) {
               System.out.println("- " + name);
           }
           
           // Use traditional for loop when you need index
           System.out.println("Names with indices:");
           for (int i = 0; i < names.length; i++) {
               System.out.println(i + ": " + names[i]);
           }
       }
       
       public static void demonstrateArraysUtility() {
           System.out.println("\n=== Arrays Utility Methods ===");
           int[] numbers = {3, 1, 4, 1, 5, 9, 2, 6, 5, 3};
           
           // Use Arrays.toString() for debugging
           System.out.println("Original: " + java.util.Arrays.toString(numbers));
           
           // Use Arrays.sort() instead of implementing your own
           int[] sorted = numbers.clone();
           java.util.Arrays.sort(sorted);
           System.out.println("Sorted: " + java.util.Arrays.toString(sorted));
           
           // Use Arrays.binarySearch() for sorted arrays
           int index = java.util.Arrays.binarySearch(sorted, 5);
           System.out.println("Index of 5 in sorted array: " + index);
       }
       
       public static void demonstrateNullHandling() {
           System.out.println("\n=== Null Handling ===");
           
           // Always check for null before operations
           int[] nullArray = null;
           
           if (nullArray != null && nullArray.length > 0) {
               System.out.println("Array length: " + nullArray.length);
           } else {
               System.out.println("Array is null or empty");
           }
           
           // Safe array processing method
           printArraySafely(new int[]{1, 2, 3});
           printArraySafely(null);
           printArraySafely(new int[0]);
       }
       
       public static void printArraySafely(int[] array) {
           if (array == null) {
               System.out.println("Array is null");
           } else if (array.length == 0) {
               System.out.println("Array is empty");
           } else {
               System.out.println("Array: " + java.util.Arrays.toString(array));
           }
       }
       
       public static void demonstrateDataTypeSelection() {
           System.out.println("\n=== Data Type Selection ===");
           
           // Choose appropriate primitive types for efficiency
           byte[] smallNumbers = {1, 2, 3, 4, 5}; // For values -128 to 127
           int[] normalNumbers = {1000, 2000, 3000}; // For typical integers
           long[] largeNumbers = {1000000000L, 2000000000L}; // For large values
           
           // Use object arrays only when necessary
           Integer[] objectNumbers = {1, 2, 3, null, 5}; // When null values needed
           
           System.out.println("Memory usage comparison:");
           System.out.println("byte array (5 elements): ~5 bytes + overhead");
           System.out.println("int array (5 elements): ~20 bytes + overhead");
           System.out.println("Integer array (5 elements): ~20 bytes + object overhead per element");
       }
   }

Common Pitfalls and How to Avoid Them
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   public class ArrayPitfalls {
       public static void main(String[] args) {
           // 1. ArrayIndexOutOfBoundsException
           demonstrateIndexOutOfBounds();
           
           // 2. Null pointer exceptions
           demonstrateNullPointerIssues();
           
           // 3. Shallow vs deep copy problems
           demonstrateCopyIssues();
           
           // 4. Modifying array while iterating
           demonstrateModificationIssues();
           
           // 5. Off-by-one errors
           demonstrateOffByOneErrors();
       }
       
       public static void demonstrateIndexOutOfBounds() {
           System.out.println("=== Index Out of Bounds Issues ===");
           int[] array = {1, 2, 3, 4, 5};
           
           // Common mistake: using <= instead of <
           try {
               for (int i = 0; i <= array.length; i++) { // BUG: should be i < array.length
                   System.out.println(array[i]);
               }
           } catch (ArrayIndexOutOfBoundsException e) {
               System.out.println("Caught exception: " + e.getMessage());
           }
           
           // Correct approach
           System.out.println("Correct iteration:");
           for (int i = 0; i < array.length; i++) {
               System.out.print(array[i] + " ");
           }
           System.out.println();
       }
       
       public static void demonstrateNullPointerIssues() {
           System.out.println("\n=== Null Pointer Issues ===");
           
           // Jagged array with null rows
           int[][] jaggedArray = new int[3][];
           jaggedArray[0] = new int[]{1, 2, 3};
           // jaggedArray[1] is still null
           jaggedArray[2] = new int[]{7, 8, 9};
           
           // Dangerous: Not checking for null
           try {
               for (int i = 0; i < jaggedArray.length; i++) {
                   System.out.println("Row " + i + " length: " + jaggedArray[i].length); // NPE on row 1
               }
           } catch (NullPointerException e) {
               System.out.println("Caught NPE: Row 1 is null");
           }
           
           // Safe approach
           System.out.println("Safe iteration:");
           for (int i = 0; i < jaggedArray.length; i++) {
               if (jaggedArray[i] != null) {
                   System.out.println("Row " + i + " length: " + jaggedArray[i].length);
               } else {
                   System.out.println("Row " + i + " is null");
               }
           }
       }
       
       public static void demonstrateCopyIssues() {
           System.out.println("\n=== Copy Issues ===");
           
           // Shallow copy problem with 2D arrays
           int[][] original = {{1, 2, 3}, {4, 5, 6}};
           
           // Shallow copy - dangerous!
           int[][] shallowCopy = original.clone();
           shallowCopy[0][0] = 999; // Modifies original too!
           
           System.out.println("Original after shallow copy modification:");
           System.out.println(java.util.Arrays.deepToString(original));
           
           // Proper deep copy
           int[][] original2 = {{1, 2, 3}, {4, 5, 6}};
           int[][] deepCopy = new int[original2.length][];
           for (int i = 0; i < original2.length; i++) {
               deepCopy[i] = original2[i].clone();
           }
           deepCopy[0][0] = 777; // Safe - doesn't affect original
           
           System.out.println("Original2 after deep copy modification:");
           System.out.println(java.util.Arrays.deepToString(original2));
       }
       
       public static void demonstrateModificationIssues() {
           System.out.println("\n=== Modification During Iteration ===");
           
           // Problem: Modifying array size during iteration (with ArrayList)
           java.util.ArrayList<Integer> list = new java.util.ArrayList<>();
           list.add(1); list.add(2); list.add(3); list.add(4); list.add(5);
           
           // Dangerous: Modifying collection while iterating
           try {
               for (Integer num : list) {
                   if (num % 2 == 0) {
                       list.remove(num); // ConcurrentModificationException
                   }
               }
           } catch (java.util.ConcurrentModificationException e) {
               System.out.println("Caught ConcurrentModificationException");
           }
           
           // Safe approach: Use iterator or iterate backwards
           list.clear();
           list.add(1); list.add(2); list.add(3); list.add(4); list.add(5);
           
           java.util.Iterator<Integer> iterator = list.iterator();
           while (iterator.hasNext()) {
               Integer num = iterator.next();
               if (num % 2 == 0) {
                   iterator.remove(); // Safe removal
               }
           }
           System.out.println("List after safe removal: " + list);
       }
       
       public static void demonstrateOffByOneErrors() {
           System.out.println("\n=== Off-by-One Errors ===");
           
           int[] array = {10, 20, 30, 40, 50};
           
           // Common mistake: wrong loop bounds
           System.out.println("Common off-by-one mistakes:");
           
           // Mistake 1: Starting from 1 instead of 0
           System.out.println("Starting from 1 (missing first element):");
           for (int i = 1; i < array.length; i++) { // BUG: should start from 0
               System.out.print(array[i] + " ");
           }
           System.out.println();
           
           // Mistake 2: Using <= instead of <
           System.out.println("Correct bounds:");
           for (int i = 0; i < array.length; i++) { // Correct
               System.out.print(array[i] + " ");
           }
           System.out.println();
           
           // Mistake 3: Array copying with wrong bounds
           int[] source = {1, 2, 3, 4, 5};
           int[] destination = new int[5];
           
           // Wrong: This will miss the last element
           for (int i = 0; i < source.length - 1; i++) { // BUG: should be i < source.length
               destination[i] = source[i];
           }
           System.out.println("Incomplete copy: " + java.util.Arrays.toString(destination));
           
           // Correct
           for (int i = 0; i < source.length; i++) {
               destination[i] = source[i];
           }
           System.out.println("Complete copy: " + java.util.Arrays.toString(destination));
       }
   }

--------------

Real-World Applications
-----------------------

Example 1: Student Grade Management System
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   import java.util.Arrays;
   import java.util.Scanner;

   public class StudentGradeManager {
       private String[] studentNames;
       private double[][] grades; // [student][subject]
       private String[] subjectNames;
       private int studentCount;
       private int subjectCount;
       
       public StudentGradeManager(int maxStudents, int maxSubjects) {
           this.studentNames = new String[maxStudents];
           this.grades = new double[maxStudents][maxSubjects];
           this.subjectNames = new String[maxSubjects];
           this.studentCount = 0;
           this.subjectCount = 0;
       }
       
       public static void main(String[] args) {
           StudentGradeManager manager = new StudentGradeManager(10, 5);
           Scanner scanner = new Scanner(System.in);
           
           // Sample data
           manager.initializeSampleData();
           
           boolean running = true;
           while (running) {
               manager.displayMenu();
               int choice = scanner.nextInt();
               scanner.nextLine(); // Consume newline
               
               switch (choice) {
                   case 1:
                       manager.displayAllGrades();
                       break;
                   case 2:
                       manager.calculateStudentAverages();
                       break;
                   case 3:
                       manager.calculateSubjectAverages();
                       break;
                   case 4:
                       manager.findTopStudent();
                       break;
                   case 5:
                       manager.generateGradeReport();
                       break;
                   case 6:
                       System.out.println("Goodbye!");
                       running = false;
                       break;
                   default:
                       System.out.println("Invalid choice!");
               }
           }
           
           scanner.close();
       }
       
       private void initializeSampleData() {
           // Initialize subjects
           subjectNames[0] = "Math";
           subjectNames[1] = "Science";
           subjectNames[2] = "English";
           subjectNames[3] = "History";
           subjectNames[4] = "Art";
           subjectCount = 5;
           
           // Initialize students and grades
           String[] names = {"Alice", "Bob", "Charlie", "Diana", "Eve"};
           double[][] sampleGrades = {
               {85.5, 92.0, 78.5, 88.0, 95.5}, // Alice
               {76.0, 81.5, 85.0, 79.5, 82.0}, // Bob
               {95.0, 98.5, 94.0, 96.5, 97.0}, // Charlie
               {88.5, 82.0, 90.5, 87.0, 85.5}, // Diana
               {79.0, 75.5, 83.0, 81.5, 78.0}  // Eve
           };
           
           for (int i = 0; i < names.length; i++) {
               studentNames[i] = names[i];
               for (int j = 0; j < subjectCount; j++) {
                   grades[i][j] = sampleGrades[i][j];
               }
           }
           studentCount = names.length;
       }
       
       private void displayMenu() {
           System.out.println("\n=== Student Grade Management System ===");
           System.out.println("1. Display All Grades");
           System.out.println("2. Calculate Student Averages");
           System.out.println("3. Calculate Subject Averages");
           System.out.println("4. Find Top Student");
           System.out.println("5. Generate Grade Report");
           System.out.println("6. Exit");
           System.out.print("Choose an option: ");
       }
       
       private void displayAllGrades() {
           System.out.println("\n=== All Student Grades ===");
           
           // Header
           System.out.printf("%-10s", "Student");
           for (int j = 0; j < subjectCount; j++) {
               System.out.printf("%-8s", subjectNames[j]);
           }
           System.out.println();
           
           // Separator
           for (int i = 0; i < 10 + subjectCount * 8; i++) {
               System.out.print("-");
           }
           System.out.println();
           
           // Data
           for (int i = 0; i < studentCount; i++) {
               System.out.printf("%-10s", studentNames[i]);
               for (int j = 0; j < subjectCount; j++) {
                   System.out.printf("%-8.1f", grades[i][j]);
               }
               System.out.println();
           }
       }
       
       private void calculateStudentAverages() {
           System.out.println("\n=== Student Averages ===");
           
           for (int i = 0; i < studentCount; i++) {
               double sum = 0;
               for (int j = 0; j < subjectCount; j++) {
                   sum += grades[i][j];
               }
               double average = sum / subjectCount;
               char letterGrade = getLetterGrade(average);
               
               System.out.printf("%s: %.2f (%c)\n", studentNames[i], average, letterGrade);
           }
       }
       
       private void calculateSubjectAverages() {
           System.out.println("\n=== Subject Averages ===");
           
           for (int j = 0; j < subjectCount; j++) {
               double sum = 0;
               for (int i = 0; i < studentCount; i++) {
                   sum += grades[i][j];
               }
               double average = sum / studentCount;
               System.out.printf("%s: %.2f\n", subjectNames[j], average);
           }
       }
       
       private void findTopStudent() {
           System.out.println("\n=== Top Student Analysis ===");
           
           double highestAverage = 0;
           int topStudentIndex = 0;
           double[] studentAverages = new double[studentCount];
           
           for (int i = 0; i < studentCount; i++) {
               double sum = 0;
               for (int j = 0; j < subjectCount; j++) {
                   sum += grades[i][j];
               }
               studentAverages[i] = sum / subjectCount;
               
               if (studentAverages[i] > highestAverage) {
                   highestAverage = studentAverages[i];
                   topStudentIndex = i;
               }
           }
           
           System.out.printf("Top Student: %s with average %.2f\n", 
               studentNames[topStudentIndex], highestAverage);
           
           // Show top student's individual grades
           System.out.println("Subject breakdown:");
           for (int j = 0; j < subjectCount; j++) {
               System.out.printf("  %s: %.1f\n", subjectNames[j], grades[topStudentIndex][j]);
           }
       }
       
       private void generateGradeReport() {
           System.out.println("\n=== Complete Grade Report ===");
           
           // Overall statistics
           double totalSum = 0;
           int totalGrades = 0;
           
           for (int i = 0; i < studentCount; i++) {
               for (int j = 0; j < subjectCount; j++) {
                   totalSum += grades[i][j];
                   totalGrades++;
               }
           }
           
           double overallAverage = totalSum / totalGrades;
           
           System.out.printf("Total Students: %d\n", studentCount);
           System.out.printf("Total Subjects: %d\n", subjectCount);
           System.out.printf("Overall Class Average: %.2f\n", overallAverage);
           
           // Grade distribution
           int[] gradeDistribution = new int[5]; // A, B, C, D, F
           
           for (int i = 0; i < studentCount; i++) {
               double sum = 0;
               for (int j = 0; j < subjectCount; j++) {
                   sum += grades[i][j];
               }
               double average = sum / subjectCount;
               
               if (average >= 90) gradeDistribution[0]++;
               else if (average >= 80) gradeDistribution[1]++;
               else if (average >= 70) gradeDistribution[2]++;
               else if (average >= 60) gradeDistribution[3]++;
               else gradeDistribution[4]++;
           }
           
           System.out.println("\nGrade Distribution:");
           char[] letterGrades = {'A', 'B', 'C', 'D', 'F'};
           for (int i = 0; i < letterGrades.length; i++) {
               System.out.printf("  %c: %d students\n", letterGrades[i], gradeDistribution[i]);
           }
       }
       
       private char getLetterGrade(double average) {
           if (average >= 90) return 'A';
           else if (average >= 80) return 'B';
           else if (average >= 70) return 'C';
           else if (average >= 60) return 'D';
           else return 'F';
       }
   }

Example 2: Sales Data Analysis System
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: java

   import java.util.Arrays;
   import java.text.DecimalFormat;

   public class SalesAnalyzer {
       private String[] products;
       private String[] salespeople;
       private double[][] salesData; // [salesperson][product]
       private String[] months;
       private double[][][] monthlySales; // [month][salesperson][product]
       
       public static void main(String[] args) {
           SalesAnalyzer analyzer = new SalesAnalyzer();
           analyzer.initializeData();
           analyzer.runAnalysis();
       }
       
       private void initializeData() {
           // Initialize products
           products = new String[]{"Laptops", "Phones", "Tablets", "Accessories"};
           
           // Initialize salespeople
           salespeople = new String[]{"John", "Sarah", "Mike", "Lisa", "David"};
           
           // Initialize months
           months = new String[]{"Jan", "Feb", "Mar", "Apr", "May", "Jun"};
           
           // Initialize sample sales data
           salesData = new double[][]{
               {15000, 25000, 8000, 3000},   // John
               {18000, 28000, 10000, 4000},  // Sarah
               {12000, 22000, 7000, 2500},   // Mike
               {20000, 30000, 12000, 5000},  // Lisa
               {16000, 24000, 9000, 3500}    // David
           };
           
           // Initialize monthly sales data (6 months)
           monthlySales = new double[6][][];
           for (int month = 0; month < 6; month++) {
               monthlySales[month] = new double[salespeople.length][products.length];
               for (int person = 0; person < salespeople.length; person++) {
                   for (int product = 0; product < products.length; product++) {
                       // Add some variation to base sales data
                       double variation = 0.8 + Math.random() * 0.4; // 80% to 120% of base
                       monthlySales[month][person][product] = salesData[person][product] * variation;
                   }
               }
           }
       }
       
       private void runAnalysis() {
           System.out.println("=== Sales Data Analysis System ===");
           
           displaySalesMatrix();
           analyzeTopPerformers();
           analyzeProductPerformance();
           analyzeTrends();
           generateSummaryReport();
       }
       
       private void displaySalesMatrix() {
           System.out.println("\n=== Current Month Sales Matrix ===");
           DecimalFormat df = new DecimalFormat("#,###");
           
           // Header
           System.out.printf("%-12s", "Salesperson");
           for (String product : products) {
               System.out.printf("%12s", product);
           }
           System.out.printf("%12s\n", "Total");
           
           // Separator
           for (int i = 0; i < 12 + products.length * 12 + 12; i++) {
               System.out.print("-");
           }
           System.out.println();
           
           // Data rows
           for (int i = 0; i < salespeople.length; i++) {
               System.out.printf("%-12s", salespeople[i]);
               double rowTotal = 0;
               for (int j = 0; j < products.length; j++) {
                   System.out.printf("%12s", "$" + df.format(salesData[i][j]));
                   rowTotal += salesData[i][j];
               }
               System.out.printf("%12s\n", "$" + df.format(rowTotal));
           }
           
           // Column totals
           System.out.printf("%-12s", "TOTAL");
           double grandTotal = 0;
           for (int j = 0; j < products.length; j++) {
               double columnTotal = 0;
               for (int i = 0; i < salespeople.length; i++) {
                   columnTotal += salesData[i][j];
               }
               System.out.printf("%12s", "$" + df.format(columnTotal));
               grandTotal += columnTotal;
           }
           System.out.printf("%12s\n", "$" + df.format(grandTotal));
       }
       
       private void analyzeTopPerformers() {
           System.out.println("\n=== Top Performers Analysis ===");
           
           // Calculate total sales per salesperson
           double[] totalSales = new double[salespeople.length];
           for (int i = 0; i < salespeople.length; i++) {
               for (int j = 0; j < products.length; j++) {
                   totalSales[i] += salesData[i][j];
               }
           }
           
           // Find top performer
           int topPerformerIndex = 0;
           for (int i = 1; i < totalSales.length; i++) {
               if (totalSales[i] > totalSales[topPerformerIndex]) {
                   topPerformerIndex = i;
               }
           }
           
           System.out.printf("Top Salesperson: %s with $%,.0f in sales\n", 
               salespeople[topPerformerIndex], totalSales[topPerformerIndex]);
           
           // Show all salespeople ranked
           System.out.println("\nAll Salespeople Ranked:");
           
           // Create array of indices for sorting
           Integer[] indices = new Integer[salespeople.length];
           for (int i = 0; i < indices.length; i++) {
               indices[i] = i;
           }
           
           // Sort by total sales (descending)
           Arrays.sort(indices, (a, b) -> Double.compare(totalSales[b], totalSales[a]));
           
           for (int rank = 0; rank < indices.length; rank++) {
               int index = indices[rank];
               System.out.printf("%d. %s: $%,.0f\n", rank + 1, salespeople[index], totalSales[index]);
           }
       }
       
       private void analyzeProductPerformance() {
           System.out.println("\n=== Product Performance Analysis ===");
           
           // Calculate total sales per product
           double[] productTotals = new double[products.length];
           for (int j = 0; j < products.length; j++) {
               for (int i = 0; i < salespeople.length; i++) {
                   productTotals[j] += salesData[i][j];
               }
           }
           
           // Find best-selling product
           int bestProductIndex = 0;
           for (int j = 1; j < productTotals.length; j++) {
               if (productTotals[j] > productTotals[bestProductIndex]) {
                   bestProductIndex = j;
               }
           }
           
           System.out.printf("Best-selling Product: %s with $%,.0f in sales\n", 
               products[bestProductIndex], productTotals[bestProductIndex]);
           
           // Show market share
           double totalRevenue = Arrays.stream(productTotals).sum();
           System.out.println("\nMarket Share:");
           for (int j = 0; j < products.length; j++) {
               double marketShare = (productTotals[j] / totalRevenue) * 100;
               System.out.printf("%s: $%,.0f (%.1f%%)\n", 
                   products[j], productTotals[j], marketShare);
           }
       }
       
       private void analyzeTrends() {
           System.out.println("\n=== Monthly Trends Analysis ===");
           
           // Calculate monthly totals
           double[] monthlyTotals = new double[months.length];
           for (int month = 0; month < months.length; month++) {
               for (int person = 0; person < salespeople.length; person++) {
                   for (int product = 0; product < products.length; product++) {
                       monthlyTotals[month] += monthlySales[month][person][product];
                   }
               }
           }
           
           System.out.println("Monthly Sales Totals:");
           for (int month = 0; month < months.length; month++) {
               System.out.printf("%s: $%,.0f", months[month], monthlyTotals[month]);
               
               if (month > 0) {
                   double growth = ((monthlyTotals[month] - monthlyTotals[month-1]) / monthlyTotals[month-1]) * 100;
                   System.out.printf(" (%.1f%% %s)", Math.abs(growth), growth >= 0 ? "↑" : "↓");
               }
               System.out.println();
           }
           
           // Calculate average monthly growth
           double totalGrowth = 0;
           for (int month = 1; month < months.length; month++) {
               double growth = ((monthlyTotals[month] - monthlyTotals[month-1]) / monthlyTotals[month-1]) * 100;
               totalGrowth += growth;
           }
           double avgGrowth = totalGrowth / (months.length - 1);
           System.out.printf("\nAverage Monthly Growth: %.1f%%\n", avgGrowth);
       }
       
       private void generateSummaryReport() {
           System.out.println("\n=== Executive Summary Report ===");
           
           // Calculate key metrics
           double totalRevenue = 0;
           double maxMonthlySale = 0;
           double minMonthlySale = Double.MAX_VALUE;
           
           for (int month = 0; month < months.length; month++) {
               double monthlyTotal = 0;
               for (int person = 0; person < salespeople.length; person++) {
                   for (int product = 0; product < products.length; product++) {
                       monthlyTotal += monthlySales[month][person][product];
                   }
               }
               totalRevenue += monthlyTotal;
               maxMonthlySale = Math.max(maxMonthlySale, monthlyTotal);
               minMonthlySale = Math.min(minMonthlySale, monthlyTotal);
           }
           
           double avgMonthlySale = totalRevenue / months.length;
           
           System.out.printf("Total Revenue (6 months): $%,.0f\n", totalRevenue);
           System.out.printf("Average Monthly Revenue: $%,.0f\n", avgMonthlySale);
           System.out.printf("Best Month Revenue: $%,.0f\n", maxMonthlySale);
           System.out.printf("Lowest Month Revenue: $%,.0f\n", minMonthlySale);
           
           // Calculate team performance
           System.out.println("\nTeam Performance Metrics:");
           System.out.printf("Number of Active Salespeople: %d\n", salespeople.length);
           System.out.printf("Average Revenue per Salesperson: $%,.0f\n", totalRevenue / salespeople.length);
           System.out.printf("Number of Products: %d\n", products.length);
           System.out.printf("Average Revenue per Product: $%,.0f\n", totalRevenue / products.length);
       }
   }

--------------

Quiz Solutions
--------------

Quiz 1: Valid Array Definitions
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Question:** Select which of the following are valid array definitions:

1. ``int[] a; a = new int[5];``
2. ``int a[] = new int[5]``
3. ``int a[5] = new int[5];``
4. ``int a[] = {1,2,3};``
5. ``int[] a = new int[]{1,2,3};``
6. ``int[] a = new int[5]{1,2,3,4};``

**Answers:** - **✅ Valid:** 1, 2, 4, 5 - **❌ Invalid:** 3, 6

**Explanations:**

.. code:: java

   public class ArrayDefinitionQuiz {
       public static void main(String[] args) {
           // 1. ✅ Valid: Separate declaration and instantiation
           int[] a;
           a = new int[5];
           System.out.println("1. Valid: " + java.util.Arrays.toString(a));
           
           // 2. ✅ Valid: C-style declaration with instantiation
           int b[] = new int[5];
           System.out.println("2. Valid: " + java.util.Arrays.toString(b));
           
           // 3. ❌ Invalid: Cannot specify size in declaration
           // int c[5] = new int[5]; // Compilation error!
           System.out.println("3. Invalid: Cannot specify size in declaration");
           
           // 4. ✅ Valid: Array literal initialization
           int d[] = {1, 2, 3};
           System.out.println("4. Valid: " + java.util.Arrays.toString(d));
           
           // 5. ✅ Valid: Anonymous array initialization
           int[] e = new int[]{1, 2, 3};
           System.out.println("5. Valid: " + java.util.Arrays.toString(e));
           
           // 6. ❌ Invalid: Cannot specify both size and initializer
           // int[] f = new int[5]{1,2,3,4}; // Compilation error!
           System.out.println("6. Invalid: Cannot specify both size and initializer");
       }
   }

Quiz 2: Array with Size and Initializer
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Question:** What will be the result if we try to compile and execute
the following code?

.. code:: java

   class Sample {
       public static void main(String[] args) {
           int[] a = new int[5]{1,2,3};
           for(int i : a)
               System.out.println(i);
       }
   }

**Answer:** **Compilation Error**

**Explanation:** - Java does not allow specifying both array size
``[5]`` and initializer values ``{1,2,3}`` in the same statement - You
can either specify the size: ``new int[5]`` (elements default to 0) - Or
provide initializer: ``new int[]{1,2,3}`` (size determined by number of
elements) - But not both together

**Correct alternatives:**

.. code:: java

   public class ArrayInitializerQuiz {
       public static void main(String[] args) {
           System.out.println("=== Correct Ways to Initialize Arrays ===");
           
           // Option 1: Specify size only (elements default to 0)
           int[] a1 = new int[5];
           System.out.println("Option 1 - Size only: " + java.util.Arrays.toString(a1));
           
           // Option 2: Provide initializer (size determined automatically)
           int[] a2 = new int[]{1, 2, 3};
           System.out.println("Option 2 - With initializer: " + java.util.Arrays.toString(a2));
           
           // Option 3: Array literal
           int[] a3 = {1, 2, 3};
           System.out.println("Option 3 - Array literal: " + java.util.Arrays.toString(a3));
           
           // What the quiz code was trying to do
           int[] a4 = new int[5];
           a4[0] = 1; a4[1] = 2; a4[2] = 3; // Remaining elements stay 0
           System.out.println("Manual assignment: " + java.util.Arrays.toString(a4));
       }
   }

Quiz 3: Default Array Values
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Question:** What will be the result if we try to compile and execute
the following code?

.. code:: java

   class Test {
       public static void main(String [] args) {
           int [] x=new int[10];
           System.out.println(x[4]);
       }
   }

**Answer:** **Compiles and runs successfully, prints: 0**

**Explanation:** - Integer arrays are automatically initialized with
default value ``0`` - ``x[4]`` accesses the 5th element (index 4) which
has the default value - No ArrayIndexOutOfBoundsException because index
4 is valid (0-9)

.. code:: java

   public class DefaultValuesQuiz {
       public static void main(String[] args) {
           // Demonstrate default values for different array types
           
           int[] intArray = new int[5];
           double[] doubleArray = new double[5];
           boolean[] boolArray = new boolean[5];
           char[] charArray = new char[5];
           String[] stringArray = new String[5];
           
           System.out.println("Default values for different array types:");
           System.out.println("int array: " + java.util.Arrays.toString(intArray));
           System.out.println("double array: " + java.util.Arrays.toString(doubleArray));
           System.out.println("boolean array: " + java.util.Arrays.toString(boolArray));
           System.out.println("char array: " + java.util.Arrays.toString(charArray));
           System.out.println("String array: " + java.util.Arrays.toString(stringArray));
           
           // Quiz answer
           int[] x = new int[10];
           System.out.println("\nQuiz answer - x[4]: " + x[4]); // Prints: 0
       }
   }

Quiz 4: Uninitialized Jagged Array
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Question:** What will be the result if we try to compile and execute
the following code?

.. code:: java

   class Test {
       public static void main(String [] args) {
           int x[ ][ ]=new int[10] [ ];
           System.out.println(x[4][0]);
       }
   }

**Answer:** **Runtime Error (NullPointerException)**

**Explanation:** - ``int[][] x = new int[10][];`` creates an array of 10
integer arrays - Each element ``x[i]`` is initialized to ``null`` (not
to an actual array) - Attempting to access ``x[4][0]`` tries to access
the first element of ``x[4]`` - Since ``x[4]`` is ``null``, this throws
a NullPointerException

**Demonstration and fix:**

.. code:: java

   public class JaggedArrayQuiz {
       public static void main(String[] args) {
           System.out.println("=== Jagged Array Quiz Demonstration ===");
           
           // The problematic code from quiz
           int[][] x = new int[10][];
           
           System.out.println("x.length: " + x.length); // 10
           System.out.println("x[4]: " + x[4]); // null
           
           try {
               System.out.println("x[4][0]: " + x[4][0]); // NullPointerException!
           } catch (NullPointerException e) {
               System.out.println("NullPointerException caught: " + e.getMessage());
           }
           
           // Correct approach: Initialize each row
           System.out.println("\n=== Correct Jagged Array Usage ===");
           
           int[][] y = new int[3][];
           y[0] = new int[2]; // Row 0 has 2 columns
           y[1] = new int[4]; // Row 1 has 4 columns  
           y[2] = new int[3]; // Row 2 has 3 columns
           
           // Now we can safely access elements
           y[0][0] = 10;
           y[1][0] = 20;
           y[2][0] = 30;
           
           System.out.println("y[0][0]: " + y[0][0]); // 10
           System.out.println("y[1][0]: " + y[1][0]); // 20
           System.out.println("y[2][0]: " + y[2][0]); // 30
           
           // Display the jagged array structure
           System.out.println("\nJagged array structure:");
           for (int i = 0; i < y.length; i++) {
               if (y[i] != null) {
                   System.out.println("Row " + i + " has " + y[i].length + " columns: " + 
                       java.util.Arrays.toString(y[i]));
               } else {
                   System.out.println("Row " + i + " is null");
               }
           }
       }
   }

--------------

Summary
-------

This comprehensive guide covers all aspects of Java arrays:

Key Concepts Mastered:
~~~~~~~~~~~~~~~~~~~~~~

| **Array Fundamentals:** - Array declaration, instantiation, and
  initialization - Fixed size and homogeneous element requirements
| - Zero-based indexing and bounds checking - Default value
  initialization by data type

**One-Dimensional Arrays:** - Multiple initialization syntaxes and best
practices - Array traversal patterns and enhanced for loops - Array
copying techniques and reference vs. value semantics - Common
operations: searching, sorting, manipulation

**Multi-Dimensional Arrays:** - Two-dimensional arrays as arrays of
arrays - Jagged arrays with varying row lengths - Higher-dimensional
arrays for complex data structures - Matrix operations and mathematical
computations

| **Advanced Operations:** - Array utility methods (Arrays class) -
  Searching algorithms (linear, binary search)
| - Sorting algorithms (bubble, selection, insertion, quick sort) -
  Array manipulation patterns (rotation, reversal, merging)

**Best Practices:** - Proper bounds checking and null handling -
Choosing appropriate data types for efficiency - Avoiding common
pitfalls and off-by-one errors - Understanding shallow vs. deep copying

**Real-World Applications:** - Student grade management systems - Sales
data analysis and reporting - Multi-dimensional data processing -
Performance optimization techniques

Programming Skills Developed:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

- Efficient array manipulation and processing
- Complex algorithm implementation
- Data structure design and organization
- Professional error handling and validation
- Performance-conscious programming practices

This foundation provides the essential knowledge for working with arrays
in Java and prepares you for more advanced data structures and
algorithms.

--------------

*Continue practicing with the provided examples and implement your own
variations to master Java arrays completely.*
