# Supported Types

A comprehensive guide to the supported data types in Scribble GYB for efficient boilerplate code generation.

## Overview

GYB (Generate Your Boilerplate) is designed to simplify code generation by supporting a variety of data types across Swift, Objective-C, and Objective-C++. Below is a comprehensive overview of the supported types, along with their descriptions, valid ranges, and examples for easy reference.

@TabNavigator {
    @Tab("Swift GYB") {
        ### Supported Swift Types

        **Swift** is a powerful programming language that supports a wide range of data types. Here are the key types available in GYB:

        | **Type**       | **Description**                                   | **Value Range**                             | **Example**                |
        |----------------|---------------------------------------------------|---------------------------------------------|----------------------------|
        | `String`       | A sequence of characters representing textual data. Ideal for handling words, sentences, and any string manipulations. | N/A                                         | `"Hello, World!"`         |
        | `Int`          | A signed integer type used for whole numbers. It can represent both positive and negative values and is suitable for general-purpose arithmetic. | `-9223372036854775808` to `9223372036854775807` | `42`                       |
        | `Int8`         | An 8-bit signed integer, useful for storing small integer values. It provides a limited range, making it suitable for scenarios with constrained memory usage. | `-128` to `127`                             | `Int8(127)`               |
        | `Int16`        | A 16-bit signed integer, providing a larger range than `Int8`. It is often used for situations where moderate integer values are necessary. | `-32768` to `32767`                         | `Int16(32767)`            |
        | `Int32`        | A 32-bit signed integer, which can hold larger values than `Int16`, making it suitable for a broader range of applications. | `-2147483648` to `2147483647`               | `Int32(2147483647)`       |
        | `Int64`        | A 64-bit signed integer that can accommodate very large integers, useful for calculations requiring high precision. | `-9223372036854775808` to `9223372036854775807` | `Int64(9223372036854775807)` |
        | `UInt8`        | An 8-bit unsigned integer, suitable for small non-negative values. It is often used in scenarios where negative values are not needed. | `0` to `255`                                | `UInt8(255)`              |
        | `UInt16`       | A 16-bit unsigned integer, allowing for moderately sized non-negative integers. This type is beneficial for scenarios like counting or indexing. | `0` to `65535`                              | `UInt16(65535)`           |
        | `UInt32`       | A 32-bit unsigned integer, providing a larger range of non-negative values than `UInt16`. Ideal for applications where larger counts are required. | `0` to `4294967295`                         | `UInt32(4294967295)`      |
        | `UInt64`       | A 64-bit unsigned integer, accommodating very large non-negative integers, suitable for extensive numerical computations. | `0` to `18446744073709551615`               | `UInt64(18446744073709551615)` |
        | `Bool`         | A Boolean type representing truth values, which can either be `true` or `false`. This type is commonly used in conditional statements. | `true` or `false`                           | `true`                     |
        | `Double`       | A double-precision floating-point number that can handle a wide range of values, making it suitable for high-precision calculations, such as scientific computations. | ~±1.7e308                                  | `3.14159`                  |
        | `Float`        | A single-precision floating-point number, used for calculations where less precision is acceptable. It's generally used in graphics and simple calculations. | ~±3.4e38                                   | `2.71828f`                 |

    }
    
    @Tab("ObjC GYB") {
        ### Supported Objective-C Types

        **Objective-C** supports a variety of types that are essential for developing robust applications. Below are the supported types in GYB:

        | **Type**       | **Description**                                   | **Value Range**                             | **Example**                |
        |----------------|---------------------------------------------------|---------------------------------------------|----------------------------|
        | `NSString`     | Represents a string object in Objective-C. It allows for rich string manipulation and is essential for handling text. | N/A                                         | `@"Hello, World!"`        |
        | `NSInteger`    | A signed integer type, commonly used for array indexing and general numeric operations in Objective-C. It adapts to the platform's word size, providing flexibility. | `-9223372036854775808` to `9223372036854775807` | `NSInteger value = 42;`   |
        | `NSUInteger`   | An unsigned integer type, used for non-negative counts, particularly when dealing with collections. It is guaranteed to never be negative, making it ideal for indexing. | `0` to `18446744073709551615`               | `NSUInteger count = 10;`  |
        | `BOOL`         | Represents a Boolean value, allowing for true or false states in Objective-C. Commonly used in conditional logic and state management. | `YES` or `NO`                               | `BOOL isActive = YES;`    |
        | `CGFloat`      | A floating-point type, typically used for UI measurements. It adapts its precision based on the platform, providing flexibility in graphics calculations. | Varies depending on the platform            | `CGFloat width = 100.0;`  |
    }
    
    @Tab("ObjC++ GYB") {
        ### Supported Objective-C++ Types

        **Objective-C++** combines the features of C++ with those of Objective-C, allowing for a rich set of types:

        | **Type**       | **Description**                                   | **Value Range**                             | **Example**                |
        |----------------|---------------------------------------------------|---------------------------------------------|----------------------------|
        | `std::string`  | A string class from the C++ Standard Library, providing powerful string manipulation capabilities. It is essential for modern C++ applications. | N/A                                         | `std::string name = "John";` |
        | `int`          | A signed integer type, standard in C++. It provides a basic numeric type for general arithmetic operations. | `-2147483648` to `2147483647`              | `int age = 30;`            |
        | `unsigned int` | An unsigned integer type used for non-negative integer values. This is commonly used in counting operations and array indexing. | `0` to `4294967295`                         | `unsigned int count = 5;`  |
        | `bool`         | A Boolean type that represents truth values, either `true` or `false`. It is widely used in conditional expressions and logical operations. | `true` or `false`                           | `bool isValid = true;`     |
        | `float`        | A single-precision floating-point number in C++, suitable for simpler numerical calculations where high precision is not critical. | ~±3.4e38                                   | `float pi = 3.14f;`        |
        | `double`       | A double-precision floating-point number that provides higher precision for complex calculations, often used in scientific computations. | ~±1.7e308                                  | `double e = 2.71828;`      |
    }
}

### Conclusion

Understanding the supported data types in GYB empowers developers to efficiently generate boilerplate code that is both type-safe and optimized for performance. By leveraging these types, you can ensure that your generated code meets the specific requirements of your Swift, Objective-C, or Objective-C++ projects, enhancing code quality and maintainability.


## See Also

- <doc:Syntax>
