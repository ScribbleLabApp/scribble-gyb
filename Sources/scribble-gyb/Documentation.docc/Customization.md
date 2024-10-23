# Customization (in planning)

Customization of Scribble GYB's Processing Configuration

## Overview

The customization of the Scribble GYB's processing configuration aims to enhance the flexibility and functionality of the GYB template processing. While this feature is currently in planning, we envision using a `.gyb_config` file formatted as XML to allow developers to tailor the behavior of GYB templates to meet their specific needs. This documentation outlines the intended structure, potential configurations, and usage of the `.gyb_config` file for customizing Scribble GYB.

> IMPORTANT:
> The customization of Scribble GYB's processing configuration is currently not available as it is in planning. This article should rather be seen as a descriptive proposal. 
>
> Customization will be available in v1.0 of Scribble GYB. For more information visit our [GitHub repository](https://github.com/ScribbleLabApp/scribble-gyb).

### Purpose of the .gyb_config File

The `.gyb_config` file will serve as a centralized configuration point for various GYB processing options. By utilizing an XML format, developers will be able to define custom settings, such as:

- **Template Directives:** Set directives that modify how templates are processed, such as enabling or disabling certain features.
- **Output Configuration:** Control how the generated files are structured, named, or stored.
- **Import Management:** Define which utility modules or functions should be imported by default in all templates.

### Proposed Structure of the .gyb_config File

The configuration file will follow a well-defined XML structure, making it easy to read and modify. Below is an example of what a `.gyb_config` file might look like:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<gybConfig>
    <templateDirectives>
        <directive name="enableCaching" value="true" />
        <directive name="disableLineDirectives" value="false" />
    </templateDirectives>
    <outputConfiguration>
        <projectroot>../.</projectroot>
        <fileNamingConvention>
            <namePattern>{templateName}_{timestamp}</namePattern>
        </fileNamingConvention>
    </outputConfiguration>
    <importManagement>
        <module>gyb_utils</module>
        <module>gyb_helpers</module>
    </importManagement>
</gybConfig>
```

### Configuration Elements

##### Template Directives (templateDirectives)

Template Directives will contain directives that modify the behavior of template processing. Each directive will have a name attribute (to identify the directive) and a value attribute (to specify its state).

| Attribute         | Description                             | Type |
| :---------------: | :-------------------------------------: | :----: |
| directive         | Specifies the name of the directive to modify template processing. | `string` |


@Comment {
    **Parameters:**
    - `directive_name`: Attribute of type `templateDirectives/directive`
    - `value`: State of the specified attribute (`directive_name`)
}

```xml
<templateDirectives>
    <directive name="" value="" />
</templateDirectives>
```

###### Directive (templateDirectives/directive)

Directives can significantly impact the processing of templates. For instance, enabling verbose logging can provide detailed insights into the GYB processing flow, while disabling line directives can simplify the output structure.

**Parameters:**

- `name`: A `string` that identifies the directive being set. This name is used within the GYB processing engine to apply specific behaviors.
- `value`: A `boolean` value that indicates the state of the directive. A value of `true` activates the directive, while `false` deactivates it.

The directive element specifies individual processing behaviors through its name and value attributes. Each directive is designed to control specific aspects of template processing.

| directive_name         | Description                             | Type |
| :---------------: | :-------------------------------------: | :----: |
| `enableVerboseLogging` | When set to `true`, enables verbose logging for the GYB process, providing detailed output for debugging purposes. | `bool` |
| `disableLineDirectives` | When set to `true`, disables the use of line directives within templates, which may simplify the output. | `bool` |
| `enableCaching` | When set to true, enables caching of processed templates to improve performance on subsequent requests. | `bool` |
| `disableOutputMinification` | When set to `true`, disables any output minification processes that may reduce file sizes but complicate readability. | `bool` |

```xml
<templateDirectives>
    <directive name="enableVerboseLogging" value="true" />
    <directive name="disableLineDirectives" value="true" />
    <directive name="enableCaching" value="true" />
    <directive name="disableOutputMinification" value="false" />
</templateDirectives>
```

##### Output Configuration (outputConfiguration)

Output Configuration will define settings related to the output of generated files. It can specify the directory for generated files and how filenames should be formatted.

| Attribute         | Description                             | Type |
| :---------------: | :-------------------------------------: | :----: |
| outputPath         | Specifies the directory where generated files will be stored. | `string` |
| projectRoot | | `string` |
| fileNamingConvention | Defines the naming pattern for generated files. | `string` |
| buildFlags | Optional flags to pass to the build process, if applicable. | `string` |

```xml
<outputConfiguration>
    <outputPath></outputPath>
    <fileNamingConvention></fileNamingConvention>
    <buildFlags></buildFlags>
</outputConfiguration>
```

###### Output Path (outputConfiguration/outputPath)

The `outputPath` specifies the directory where the generated files will be stored. This path can be either absolute or relative to the project root.

**Parameters:**
- `_path`: The path where the generated files will be saved.

```xml
<outputConfiguration>
    <outputPath>*.gyb/autogenerated</outputPath>
</outputConfiguration>
```

###### Project Root (projectRoot)

The `projectRoot` defines the root directory of the project. This is helpful for resolving relative paths within the project structure.

**Parameters:**
- `_path`: The root directory of the project, which can be used to construct relative paths for the output.

```xml
<outputConfiguration>
    <projectRoot>../.</projectRoot>
</outputConfiguration>

```

###### File Naming Convention (outputConfiguration/fileNamingConvention)

The `fileNamingConvention` specifies how the generated files will be named based on a naming pattern. This allows for consistent file naming that can include dynamic elements like the template name and timestamps.

| Attribute         | Description                             | Type |
| :---------------: | :-------------------------------------: | :----: |
| namingPattern | The pattern used to name generated files, supporting placeholders. | `string` |

```xml
<outputConfiguration>
    <namePattern>{templateName}_generated</namePattern>
</outputConfiguration>
```

###### Build Flags (outputConfiguration/buildFlags)

The `buildFlags element contains optional flags that can be passed to the build process. These flags can control various aspects of how files are compiled or processed.

| Attribute         | Description                             | Type |
| :---------------: | :-------------------------------------: | :----: |
| flag         | A specific flag to be passed to the build process. | `string` |

```xml
<outputConfiguration>
    <buildFlags>
        <flag></flag>
    </buildFlags>
</outputConfiguration>
```

**Overview of Build Flags:**

| flag         | Description                             | 
| :---------------: | :-------------------------------------: |
| `-O1`        | Enables optimization level 1 for performance improvement. |
| `-C` | Enables compile-time checks for better error reporting. |
| `-Wall` | Enables all compiler's warning messages, helping developers identify potential issues early. |
| `-Werror` | Treats all warnings as errors, enforcing stricter code quality and prompting fixes before compilation. |
| `-g` | Generates debug information for use with debuggers, allowing easier troubleshooting.
| `-ddb` | Defines a macro named DEBUG, typically used to enable or disable debugging code sections in the project. |


Build flags provide developers with the ability to customize the build process, allowing for optimizations, debugging aids, or other specific configurations needed for different environments.

```xml
<outputConfiguration>
    <buildFlags>
        <flag>-O1</flag>
        <flag>-C</flag>
    </buildFlags>
</outputConfiguration>
```

##### Import Management (importManagement)

The Import Management section is crucial for specifying utility modules or files that should be automatically imported into all GYB (Generate Your Boilerplate) templates. This feature simplifies template development by ensuring that common dependencies are consistently available, reducing the need for repetitive import statements in individual templates.

| Attribute         | Description                             | Type |
| :---------------: | :-------------------------------------: | :----: |
| module         | Specifies the name of the module to be imported into GYB templates. | `string` |

```xml
<importManagement>
    <module></module>
</importManagement>
```

###### Module (importManagement/Module)

Modules are predefined sets of functions, classes, or variables that encapsulate specific functionalities to be reused across different templates. By importing these modules, developers can leverage existing utility functions or libraries without needing to redefine or re-import them in every template file.

**Parameters:**
- `_moduleName`: The name of the module to be imported. This should match the actual module name in the project structure or within the GYB framework.

When a module is imported, all its exported functions, classes, and variables become available in the GYB template's scope. This allows developers to utilize the module's capabilities seamlessly, promoting code reuse and modular design.

###### Advantages of using auto import Models

By managing imports centrally, all templates can maintain a consistent set of available utilities. This minimizes discrepancies between different templates and helps ensure that they all function uniformly.

With automatic imports, GYB templates remain cleaner and more focused on their specific logic, as common utility imports do not clutter the top of each template file.

```xml
<importManagement>
    <module>gyb_utils</module>
    <module>gyb_foundation</module>
</importManagement>
```

In the example above, two modules, gyb_utils and gyb_foundation, are specified for import. This means that in every GYB template, functions or classes defined in these modules will be readily available for use.

### Using the .gyb_config File

Once the .gyb_config file is properly structured and placed within the project, the Scribble GYB processing engine will read and apply the configurations during template processing. Developers will need to ensure that the path to the .gyb_config file is correctly specified in their GYB processing script.

1. **Create the .gyb_config File:** Create a new file named `.gyb_config` in the root directory of your GYB templates.
2. **Define Configuration Settings:** Populate the file with the necessary configurations following the proposed XML structure
3. **Integrate with GYB Processing:** Ensure your GYB processing script is set up to read the `.gyb_config` file. This integration will involve parsing the XML and applying the settings before processing the templates.

### Conclusion

The `.gyb_config` file is an exciting enhancement to Scribble GYB's processing capabilities, providing developers with a powerful tool for customizing their GYB template processing. Although this feature is still in planning, the proposed XML structure and functionality outlined in this documentation will lay the groundwork for a more flexible and efficient GYB development experience. As this feature progresses towards implementation, further refinements and enhancements will be explored to ensure it meets the needs of the Scribble GYB community.
