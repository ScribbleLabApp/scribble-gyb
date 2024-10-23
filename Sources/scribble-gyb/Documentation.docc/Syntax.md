# Syntax

<!--@START_MENU_TOKEN@-->Summary<!--@END_MENU_TOKEN@-->

## Overview

The GYB (Generate Your Boilerplate) syntax is designed to facilitate the dynamic generation of boilerplate code in various programming languages, including Swift, Objective-C, and Objective-C++. GYB templates combine Python code for logic and control flow with placeholders for inserting dynamic values into the generated code. This allows developers to create flexible and reusable templates that simplify the coding process.

### Template Syntax

GYB templates are composed of two primary elements:

1. Python Code Blocks for logic and control flow.
2. Code Placeholders that insert Python values into generated code.

### Python Code Blocks

Python code is encapsulated within `%{ ... }%` or `${...}$` blocks. These blocks are executed at the time of template processing, enabling the generation of code based on runtime values or logic.

```py
%{
    import random
    random_value = random.randint(1, 100)
}%
```

In this example, a random integer between 1 and 100 is generated when the template is processed.

### Variables and Placeholders

Variables defined within a GYB template can be inserted into Swift, Objective-C, or Objective-C++ code using the `${var}` syntax.

@TabNavigator {
    @Tab("Swift GYB") {
        ```swift
        %{
            py_greeting = "Hello, GYB!"
        }%

        public struct Greeting {
            public let message: String = "${py_greeting}"
        }

        print(Greeting.message) // ~> Output: Hello, GYB!
        ```

        In this Swift example, the variable `py_greeting` is defined in a Python block and then used in the generated Swift code.
    }
    
    @Tab("ObjC GYB") {
        ```objc
        %{
        message = "Hello, GYB ObjC!"
        }%
        
        NSString *greeting = @"${message}"; // ~> Output: Hello, GYB ObjC!
        ```
        
        In this Objective-C example, the variable `message` is defined and used in the generated code.
    }
}
        
### Conditional Logic
        
GYB supports Python control flow constructs, such as if statements, to enable conditional code generation based on certain conditions. 

Conditional statements start with a `%` prefix, followed by the keyword `if` and the type or variable. After completing a conditional operation, it should end with the `%` prefix and the `end` keyword.

@TabNavigator {
    @Tab("Swift GYB") {
        ```swift
        %{
            is_logged_in = True
        }%
                
        % if is_logged_in:
            print("Welcome back!")
        % else:
            print("Please log in.")
        % end
        ```
                
        In this example, if is_logged_in is True, the message `"Welcome back!"` is printed; otherwise, `"Please log in."` is printed.
    }
    
    @Tab("ObjC GYB") {
        ```objc
        %{
            use_large_buffer = True
        }%
        
        % if use_large_buffer:
            #define BUFFER_SIZE 1024
        % else:
            #define BUFFER_SIZE 256
        % end
        
        char buffer[BUFFER_SIZE];
        ```
        
        In this ObjC/C code example, the `BUFFER_SIZE` is conditionally defined based on the `boolean` value of `use_large_buffer`.
    }
}
        
### Loops
        
GYB templates can leverage Python's `for` loops to generate repeated code blocks dynamically.
        
Scribble GYB's loops can be useful when conforming a type to multiple protocols. To do this, create a collection of the conforming protocols. Then, pass the type in the `% for <?protocol?> in <?collection?>` loop. Use placeholders to access the values from `<?protocol?>`. End the loop with the `%` prefix followed by the `end` keyword.

@TabNavigator {
    @Tab("Swift GYB") {
        ```swift
        %{
            fields = ['name', 'age', 'email']
        }%
                
        struct User {
            % for field in fields:
                var ${field}: String
            % end
        }
        ```
                
        This Swift code generates a User struct with properties for each field in the fields list, resulting in:

        ```swift
        struct User {
            var name: String
            var age: String
            var email: String
        }
        ```
    }
    
    @Tab("ObjC GYB") {
        ```obj
        %{
            methods = ['getName', 'getAge', 'getEmail']
        }%

        @interface User : NSObject
        % for method in methods:
        - (NSString *)${method};
        % end
        @end
        ```

        This Objective-C code generates method declarations for the User class, resulting in:

        ```objc
        @interface User : NSObject

        - (NSString *)getName;
        - (NSString *)getAge;
        - (NSString *)getEmail;

        @end
        ```
    }
}


## See Also

- <doc:Supported-Types>
- <doc:SharedUtilities>
