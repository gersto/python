# Python Interview Questions

1. **What Are the Differences Between List, Tuple, Set, and Dictionary?**<br>   
   Python provides different data structures to store collections of data, and choosing the right one matters in real projects.

   - List<br>
     A list is an ordered and mutable collection. It allows duplicate values and can be changed after creation.
     Lists are commonly used when the order of elements matters and when data needs to be updated frequently.

   - Tuple<br>
     A tuple is similar to a list but immutable, meaning its values cannot be changed once created.
     Tuples are faster than lists and are often used for fixed data.

   - Set<br>
     A set is an unordered collection that does not allow duplicate values.
     It is useful when you want unique elements or need fast membership checking.

   - Dictionary<br>
     A dictionary stores data in key–value pairs. Keys are unique and used to retrieve values efficiently.
     Dictionaries are widely used for mappings and counting frequencies.
     Use lists for flexibility, tuples for fixed data, sets for uniqueness, and dictionaries for fast lookups.

2. **When Would You Use a Tuple Instead of a List?**<br>
   A tuple is preferred over a list when data should not be changed.

   Since tuples are immutable:
   - They prevent accidental modification of data
   - They are slightly faster than lists
   - They can be used as dictionary keys (lists cannot)
   
   Common use cases:
   - Returning multiple values from a function
   - Storing constant configuration values
   - Representing fixed records like (latitude, longitude)

3. **What Are Modules and Packages in Python?**<br>
   A module is a single Python file that contains code such as functions, classes, or variables.<br>
   It helps organize code into reusable components.

   A package is a collection of related modules stored inside a directory.<br>
   It allows large projects to be structured cleanly.

   Why they are important:
   - Improve code organization
   - Encourage reuse
   - Make large projects manageable
   - In ML projects, libraries like NumPy and pandas are examples of packages made up of many modules.

4. **What Are Decorators in Python?**<br>
   A decorator is a function that modifies the behaviour of another function without changing its code.

   Decorators are commonly used for:
   - Logging
   - Authentication and authorization
   - They are written using the @ symbol and help keep code clean and reusable.

5. **What Are Namespaces in Python?**<br>
   A namespace is a container that holds variable names and maps them to objects.

   Python uses namespaces to avoid naming conflicts.

   Types of namespaces:
   - Local — inside a function
   - Global — defined at the module level
   - Built-in — provided by Python itself

6. **How Does Python Manage Memory?**<br>
   Python manages memory automatically using:
   - Private heap space
   - Garbage collection
   - Memory is allocated dynamically, and unused objects are removed automatically.

   Garbage collector removes unused objects<br>
   Developers don’t manually free memory<br>
   This simplifies development but requires awareness to avoid memory leaks in long-running programs.

7. **What Is split() and join() in Python?**<br>
   - split() is used to break a string into a list based on a separator.
   - join() is used to combine a list of strings into a single string.

   These functions are commonly used in:
   - Text processing
   - Data cleaning
   - Log analysis

8. **What Is Pickling and Unpickling in Python?**<br>
   Pickling is the process of converting a Python object into a byte stream so it can be stored or transmitted.

   Unpickling is the reverse process i.e. converting the byte stream back into the original object.

   In ML:
   - Models are often pickled to save trained models
   - Unpickling is used to load models for inference

9. **What Is Multithreading in Python?**<br>
   Multithreading is a programming technique where a program run multiple threads at the same time within a single process.

   A thread is the smallest unit of execution.
    
   All threads in a process:
   - Share the same memory
   - Share variables and resources
   - Run concurrently
    
   This helps improve performance when a program has to wait for external operations, such as file reading or network requests.

   Python provides a built-in threading module to create and manage threads.

   Each thread runs independently, but because they share memory, they can communicate easily.

   When Should You Use Multithreading?<br>
   Multithreading is best used when your program:
   - Waits for I/O operations
   - Makes network or API calls
   - Reads or writes files
   - Performs logging or background tasks
    
   Examples:
   - Downloading multiple files
   - Calling multiple APIs
   - Reading large datasets from disk

10. **What Is the Difference Between Multithreading and Multiprocessing in Python?**<br>
    Multithreading
    - Multiple threads within the same process
    - Shares memory
    - Best for I/O-bound tasks (file reading, API calls)
    
    Multiprocessing
    - Multiple processes
    - Separate memory space
    - True parallelism
    - Best for CPU-bound tasks
   
11. **Explain Pass by Value vs Pass by Reference in Python**<br>
    This is a tricky question, but interviewers mainly want conceptual clarity.

    Python uses pass by object reference.

    What this means:<br>
    - When you pass an object to a function, Python passes a reference to that object
    - If the object is mutable (like a list or dictionary), changes inside the function affect the original object
    - If the object is immutable (like an integer or string), changes create a new object instead
    
    So:
    - Mutable objects → changes reflect outside the function
    - Immutable objects → original object remains unchanged
   
12. **What Is Dynamic Typing in Python?**<br>
    Dynamic typing means that you don’t need to declare variable types explicitly in Python.

    The type of a variable is determined at runtime, based on the value assigned to it.

    For example:<br>
    A variable can hold an integer at one point. The same variable can later hold a string
    
    Advantages:
    - Faster development
    - Cleaner and shorter code
    
    Disadvantages:
    - Type-related errors may appear at runtime
    - Requires careful coding in large applications
    - Dynamic typing improves flexibility but demands discipline in production code.

13. **What Are Python Functions? How Do You Define One?**<br>
    A function is a reusable block of code that performs a specific task.
    Functions help in writing clean, modular, and readable code.

    In Python, functions are defined using the def keyword.
    They can take inputs (parameters), perform operations, and return outputs.

    Why functions are important:
    - Avoid code repetition
    - Improve readability
    - Make debugging and testing easier
    - Functions are widely used in ML pipelines for data cleaning, feature creation, and model evaluation.

14. **What Is a Lambda Function and When Would You Use It?**<br>
    A lambda function is a small, anonymous function written in a single line.

    It is used when:
    - The logic is simple
    - The function is used only once
    - Readability is not compromised
    - Lambda functions are commonly used with functions like map, filter, and sorted.

    Avoid using lambda for complex logic

15. **What Are *args and kwargs?**<br>
    *args and **kwargs allow functions to accept a variable number of arguments.

    - *args is used for positional arguments
    - **kwargs is used for keyword arguments
    
    They are useful when:
    - You don’t know the number of inputs beforehand
    - Writing flexible and reusable functions
    - In real-world ML code, they are often used in model training and configuration functions.

16. **What Is List Comprehension? Give an Example.**<br>
    List comprehension is a concise way to create lists using a single line of code.

    It replaces longer loops while keeping the logic clear.

    Why it’s useful:
    - Shorter and cleaner code
    - Better readability when used properly
    - However, list comprehensions should be avoided if the logic becomes too complex.

17. **What Is a Generator? How Is It Different from a List?**<br>
    A generator is an object that produces values one at a time, instead of storing all values in memory.

    Key differences:
    - Lists store all elements in memory
    - Generators generate values on demand
    
    Why generators matter:
    - Memory efficient
    - Ideal for large datasets
    - Useful in data pipelines
    - Generators are especially helpful when working with large files or streaming data.

18. **What Is range() and How Does It Work?**<br>
    The range() function generates a sequence of numbers.

    It is commonly used in loops to control the number of iterations.

    Key points:
    - range(start, stop, step)
    - Stop value is not included
    - Returns a range object, not a list
    - range() is memory efficient and often combined with loops and indexing operations.

Object-Oriented Programming (OOP) in Python — Interview Essentials
OOP questions are asked to check whether you can structure code properly, not whether you can write complex systems.
For AI / ML roles, interviewers expect basic clarity, not deep theory.

19. **What Is Object-Oriented Programming (OOP) in Python?**<br>
    Object-Oriented Programming is a way of organizing code by grouping related data and behaviour together.

    Instead of writing loose functions, OOP allows us to model real-world entities as objects. Each object contains:
    - Attributes (data)
    - Methods (functions)
    
    OOP helps in:
    - Writing modular code
    - Improving readability
    - Making code reusable and maintainable
   
20. **What Is a Class and an Object?**<br>
    A class is a blueprint or template that defines the structure of an object.
    
    An object is an instance of that class.

    Class defines what an object will have
    
    Object represents a real example of that class
    
    For example:
    - A class defines a model such Animal class
    - An object is an instance belonging to it such as Cats
   
21. **What Is Inheritance?**<br>
    Inheritance allows a class to reuse properties and methods of another class.

    The original class is called the parent (base) class
    
    The new class is called the child (derived) class
    
    This helps:
    - Reduce code duplication
    - Create hierarchical relationships
    - Extend existing functionality
   
22. **What Is init() in Python?**<br>
    __init__() is a special method that runs automatically when an object is created.

    It is used to:
    - Initialize object attributes
    - Set default values
    - Think of __init__() as a constructor that prepares the object for use.

23. **Difference Between a Method and a Function**<br>
    A function is a standalone block of code that performs a task.
    
    A method is a function that belongs to a class and operates on an object.

    Key difference:
    - Functions are independent
    - Methods use object data through self
    - This distinction helps organize code logically when using OOP.

24. **What Is Encapsulation?**<br>
    Encapsulation means hiding internal details and exposing only what is necessary.

    In Python, this is done by:
    - Keeping variables inside a class
    
    Encapsulation helps:
    - Protect data from accidental changes
    - Make code safer and easier to maintain
   
25. **What Is Exception Handling? Explain try–except–finally**<br>
    Exception handling is used to handle runtime errors gracefully, without crashing the program.

    In Python, this is done using:
    - try → code that may cause an error
    - except → code that runs if an error occurs
    - finally → code that always runs, whether an error occurs or not
    
    Why exception handling is important:
    - Prevents program crashes
    - Makes debugging easier
    - Improves user experience
   
26. **What Are Common Python Exceptions?**<br>
    Some commonly found Python exceptions include:
    - ZeroDivisionError — dividing by zero
    - TypeError — invalid operation between data types
    - ValueError — correct type but invalid value
    - IndexError — accessing an invalid index
    - KeyError — accessing a missing dictionary key
    - FileNotFoundError — file does not exist
   
27. **How Do You Read and Write Files in Python?**<br>
    File handling allows Python programs to store and retrieve data.

    Common operations:
    - Open a file in read (r), write (w), or append (a) mode
    - Read content from files
    - Write processed data back
    
    Using file handling ensures:
    - Persistent data storage
    - Logging results
    - Saving model outputs
   
28. **Why Is Python Preferred for Machine Learning?**<br>
    Python is widely used in ML because:
    - Simple and readable syntax
    - Large ecosystem of ML libraries
    - Strong community support
    - Easy integration with data tools
    
    Popular ML libraries include:
    - NumPy
    - pandas
    - scikit-learn
    - TensorFlow and PyTorch
   
29. **Difference Between NumPy Array and Python List**<br>
    While both store collections of elements, they are designed for different purposes.

    Python Lists:
    - Can store different data types
    - Slower for numerical computations
    - More flexible
    
    NumPy Arrays:
    - Store homogeneous data
    - Faster and memory-efficient
    - Support vectorized operations
    - NumPy arrays are preferred for mathematical and ML computations due to better performance.

30. **What Is pandas and Why Is It Used?**<br>
    Pandas is a Python library used for data manipulation and analysis.

    It provides:
    - DataFrame and Series data structures
    - Easy handling of missing values
    - Powerful filtering and aggregation
    - Simple data cleaning tools
    - Pandas is essential in ML workflows because raw data is rarely clean.
    
    Most ML projects spend more time in pandas than in modeling itself.
