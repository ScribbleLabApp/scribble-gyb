# SharedUtilities

<!--@START_MENU_TOKEN@-->Summary<!--@END_MENU_TOKEN@-->

## Overview

In the Scribble GYB configuration, the `gyb_utils.py` file serves as a centralized location for declaring global variables, helper functions, and imports that can be reused across various GYB templates. By leveraging this utility file, developers can create a more organized and maintainable codebase, reducing redundancy and enhancing the overall functionality of their templates. This documentation provides a detailed guide on how to effectively use `gyb_utils.py` in your GYB templates.

### Purpose of `gyb_utils.py`

The primary purpose of the `gyb_utils.py` file is to facilitate the sharing of common utilities among GYB templates. This is particularly beneficial in scenarios where you need to:

- **Define Constants:** Establish shared constants that are used in multiple templates, ensuring consistent values throughout your codebase.
- **Implement Helper Functions:** Create utility functions that can perform repeated tasks or calculations, streamlining your GYB templates and promoting code reusability.
- **Organize Imports:** Manage common imports that might be required across different templates, keeping your GYB files clean and focused on template-specific logic.

### Declaring Global Utilities in `gyb_utils.py`

To utilize `gyb_utils.py`, you first need to modify the file to include any global variables, helper functions, or imports that you intend to share across your GYB templates. Here's a step-by-step approach to setting up your utility file:

1. **Create or Modify `gyb_utils.py`:** If it doesn't already exist, create a file named `gyb_utils.py` in the same directory as your GYB templates or in a designated utilities directory.
2. **Define Global Variables and Functions:** You can declare constants and utility functions as shown in the example below:
    
    ```py
    # gyb_utils.py - Source start
    
    # Shared Constants
    PI = 3.14159
    EULER = 2.71828

    # Utility Functions
    def square(x):
        """Return the square of a number."""
        return x * x

    def cube(x):
        """Return the cube of a number."""
        return x * x * x

    def factorial(n):
        """Return the factorial of a number."""
        if n == 0:
            return 1
        return n * factorial(n - 1)

    # gyb_utils.py - Source end
    ```

### Importing and Using Utilities in GYB Templates

Once you have declared your utilities in `gyb_utils.py`, you can easily import and utilize them in any of your GYB templates. Here’s how to do it:

1. **Import Utilities:** At the beginning of your GYB template, include an import statement to bring in your utilities:
    
    ```py
    %{
        from gyb_utils import *
    }%
    ```

2. **Use Shared Variables and Functions:** You can then access the declared variables and call functions directly within your GYB template. Here’s an example of how to use the utilities:

    ```swift
    %{
        from gyb_utils import *
    }%
    
    // MARK: - Utilizing shared constants
    print("The value of PI is ${PI}")                // ~> Output: The value of PI is 3.14159
    print("The value of Euler's number is ${EULER}") // ~> Output: The value of Euler's number is 2.71828
    
    // MARK: - Utilizing shared functions
    print("The square of 4 is ${square(4)}")         // ~> Output: The square of 4 is 16
    print("The cube of 3 is ${cube(3)}")             // ~> Output: The cube of 3 is 27
    print("The factorial of 5 is ${factorial(5)}")   // ~> Output: The factorial of 5 is 120
    ```

### Benefits of Using `gyb_utils.py`

By using `gyb_utils.py`, you can achieve several advantages such as **(a)** *Code Reusability*, **(b)** *Centralized Management* and **(c)** *Improved Readability*. 

Shared utilities eliminate the need to duplicate code across multiple GYB templates, promoting cleaner and more maintainable templates. Having a single location for common functions and constants makes it easier to manage changes. If you need to update a constant value or modify a utility function, you only need to do it once in `gyb_utils.py`. GYB templates can focus on their specific logic without being cluttered by repetitive code, making them easier to read and understand.

### Best Practices

1. **Keep Utilities Relevant:** Only include functions and variables in `gyb_utils.py` that are commonly used across multiple templates. This helps maintain clarity and relevance.
2. **Document Your Utilities:** Add docstrings to your functions to describe their purpose and usage. This documentation will be beneficial for both current and future developers working with your templates.
3. **Organize Complex Logic:** If you have complex utilities, consider organizing them into separate modules or classes within your utility file for better structure and encapsulation.

### Example Use Case

To illustrate the utility of `gyb_utils.py`, consider a scenario where you are developing multiple GYB templates for generating mathematical computations. Instead of writing the logic for squaring numbers or calculating factorials in each template, you can encapsulate this logic within `gyb_utils.py` and easily reuse it across all templates, thereby streamlining your development process.

### Conclusion

Utilizing `gyb_utils.py for shared utilities in Scribble GYB greatly enhances the maintainability and reusability of your GYB templates. By organizing your global variables and functions in a centralized location, you can reduce redundancy, promote cleaner code, and streamline the development process. Following the guidelines and best practices outlined in this documentation will help you maximize the benefits of using shared utilities in your GYB workflow.

## See Also

- <doc:Syntax>
- <doc:Supported-Types>
