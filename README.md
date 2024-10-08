# Scribble GYB (Generate Your Boilerplate)

## Overview

This repository provides a GYB (Generate Your Boilerplate) configuration tailored for ScribbleLabApp projects. GYB is a tool for generating Swift code using templates, which helps in maintaining a consistent and DRY (Don't Repeat Yourself) codebase. This setup automates boilerplate code generation, reducing manual coding effort and minimizing errors.

## Purpose 

The Scribble GYB configuration streamlines the generation of boilerplate code for Swift projects. By using this configuration, you can ensure repetitive code patterns are handled efficiently and consistently across your projects.

## Getting Started

### Installation

To use the Scribble GYB configuration, you can either add it to your project as a submodule or manually copy the necessary files.

#### Option 1: Add scribble-gyb as git submodule

1. Navigate to your project you want to use scribble-gyb in:

   ```shell
   cd your-project
   ```

2. Clone the repository into your project as a submodule:

    ```shell
    git clone https://github.com/ScribbleLabApp/scribble-gyb.git
    ```
3. Initialize and update the submodule:
    
    ```shell
    git submodule init
    git submodule update
    ```

#### Option 2: Manually Copy Files `(recommended)`

1. Clone the scribble-gyb config repository:

    ```shell
    git clone https://github.com/ScribbleLabApp/scribble-gyb.git
    ```

2. Create a utils directory in your project:   
   ```shell
   mkdir -p utils
   ```

3. Navigate to the cloned repository and copy the required files:

   ```shell
   cd scribble-gyb
   cp generate-sources.sh gyb.py gyb_utils.py gyb location-to-your-project/utils/
   ```

4. Navigate to your project directory and ensure the files are in place under the utils directory.

## Usage

The GYB (Generate Your Boilerplate) tool is configured in this repository to allow you to integrate Python scripting with Swift code generation. This setup provides a flexible and powerful way to generate boilerplate code dynamically.

### Scribble-GYB Syntax

In GYB templates, you can mix Python code with Swift code. The syntax allows you to embed Python code within Swift files using special markers and placeholders.

#### Python Code Blocks

To include Python code in your Swift files, use the following markers:

```python
%{
    import random
    random_value = random.randint(1, 100)
}%
```

#### Variables and Placeholders

You can define Python variables and use them as placeholders in your Swift code. Use the `${var}` syntax to insert Python variable values into your Swift code.

```swift
%{
my_variable = "Hello, GYB!"
}%

public struct Greeting {
    public let message: String = "${my_variable}"
}

print(Greeting.message) // ~> Hello, GYB!
```

#### Conditional Logic

You can use Python's if statements within your templates to include or exclude code based on conditions:

```swift
%{
    x = 10
}%

% if x > 5:
public struct LargeNumber {
    public let value: Int = ${x}
}

% else:
public struct SmallNumber {
    public let value: Int = 0
}
% end
```

In this example, if x is greater than 5, the LargeNumber struct is included in the generated Swift code. Otherwise, SmallNumber is included.

### Loops

Use Python's for loops to iterate over a range or collection and generate repetitive code:

```swift
%{
    items = ['a', 'b', 'c']
}%

public struct Letters {
    % for item in items:
        public let ${item}: String = "${item}"
    % end
}
```

### Running Scribble-GYB

To process your GYB templates and generate Swift code, use the generate-sources.sh script.

#### Generate Source code

GYB is a preprocessor, so you need to run it to generate the actual Swift source code files. Use the `generate-sources.sh` script provided in this repository.

The `generate-sources.sh` script processes GYB templates and generates the corresponding Swift source code files.

##### Running the Script

1. **Ensure GYB Templates are in Place:** Place your GYB template files in the `Sources` or `Tests` directory either with a `.swift.gyb` (Swift), `.m.gyb` (ObjC) or `.mm.gyb` (ObjC++) extension.

2. **Execute the Script:** Run the generate-sources.sh script to generate Swift source files from your GYB templates.

    ```shell
    chmod +x generate-sources.sh
    ./generate-sources.sh
    ```

3. Verify Generated Files: The generated Swift, ObjC or ObjC++ files will be placed in autogenerated subdirectories under Sources or Tests wherever your gyb template is placed.

## Copyright Notice

Copyright (c) 2024, ScribbleLabApp LLC. All rights reserved.

Copyright (c) 2014 - 2024, Apple Inc. -
Swift is a trademark of Apple Inc. All rights reserved.

Copyright (c) 2001-2024, Python Software Foundation -
Python is a trademark of the Python Software Foundation. All rights reserved.

## Support Us

Your support is valuable to us and helps us dedicate more time to enhancing and maintaining this repository. Here's how you can contribute:

⭐️ **Leave a Star:** If you find this repository useful or interesting, please consider leaving a star on GitHub. Your stars help us gain visibility and encourage others in the community to discover and benefit from this work.

✨ **Follow us on Social Media:** If you find this repository useful or interesting, please consider leaving a sub on YouTube or Instagram. Your sub help us gain visibility and encourage others in the community to discover and benefit from this work.

📲 **Share with Friends:** If you like the idea behind this project, please share it with your friends, colleagues, or anyone who might find it valuable.
