# EditorConfig Configurations

This directory contains a collection of `.editorconfig` files designed to enforce consistent coding styles across various programming languages and frameworks. Each file is tailored to specific use cases, with detailed settings to ensure clarity, maintainability, and compatibility with EditorConfig-supported editors.

## Overview

The `configs/` directory houses EditorConfig files that define formatting and coding conventions for your projects. Currently, this repository includes a configuration for **C#**, with plans to expand to other languages and frameworks in the future. Each file is crafted to align with common style guides and best practices, making it easy to integrate into your workflow.

For a general introduction to the repository, see the [main README](../README.md).

## Available Configurations

### C# EditorConfig (`csharp.editorconfig`)

The `csharp.editorconfig` file provides a comprehensive set of coding conventions and formatting rules for C# projects. It is designed to enforce modern C# best practices, ensuring consistency across teams and projects. Below is a detailed breakdown of its settings.

#### File Location
- Path: `configs/csharp.editorconfig`
- Target: C# files (`*.cs`)

#### Key Features
- **Core Formatting**:
  - Uses spaces for indentation with a width of 4 (`indent_style = space`, `indent_size = 4`).
  - Enforces CRLF line endings (`end_of_line = crlf`) for consistency with Windows-based development environments.
  - Disables insertion of final newlines (`insert_final_newline = false`).

- **.NET Coding Conventions**:
  - Organizes `using` directives with system directives first (`dotnet_sort_system_directives_first = true`).
  - Prefers modern C# features like null-coalescing (`dotnet_style_coalesce_expression = true`), null propagation (`dotnet_style_null_propagation = true`), and simplified interpolation (`dotnet_style_prefer_simplified_interpolation = true`).
  - Enforces PascalCase for types, properties, and methods (`dotnet_naming_rule.types_should_be_pascal_case`).
  - Requires camelCase for variables and parameters (`dotnet_naming_rule.variables_and_parameters_should_be_camel_case`).
  - Mandates `Async` suffix for async methods (`dotnet_naming_rule.async_methods_end_in_async`).
  - Enforces private readonly fields to start with an underscore (`dotnet_naming_rule.private_readonly_fields_should_start_with_underscore`).

- **C# Specific Conventions**:
  - Disables `var` usage for built-in types or apparent types to improve code clarity (`csharp_style_var_* = false:error`).
  - Encourages expression-bodied accessors, indexers, and lambdas (`csharp_style_expression_bodied_* = true:silent`).
  - Promotes pattern matching over traditional `as` or `is` checks (`csharp_style_pattern_matching_* = true:suggestion`).
  - Requires braces for code blocks (`csharp_prefer_braces = true:suggestion`) and prefers simple `using` statements (`csharp_prefer_simple_using_statement = true:suggestion`).

- **Formatting Rules**:
  - Places new lines before `catch`, `else`, `finally`, and other key constructs (`csharp_new_line_before_* = true`).
  - Configures spacing preferences, such as no spaces before commas or dots (`csharp_space_before_comma = false`, `csharp_space_before_dot = false`).
  - Preserves single-line blocks and statements for readability (`csharp_preserve_single_line_* = true`).

- **Naming Rules**:
  - Interfaces must begin with `I` (`dotnet_naming_rule.interface_should_be_begins_with_i`).
  - Public members must use PascalCase (`dotnet_naming_rule.public_members_must_be_capitalized`).
  - Test classes and methods follow PascalCase (`dotnet_naming_rule.test_*_should_be_pascal_case`).
  - Namespaces use PascalCase and match folder structure (`dotnet_style_namespace_match_folder = true`).

- **Code Analysis**:
  - Enforces strict rules for unused variables (`dotnet_code_quality_unused_parameters = all:error`).
  - Enables diagnostics for common issues, such as unused expressions (`dotnet_diagnostic.CS0219.severity = error`) and missing XML documentation (`dotnet_diagnostic.CS1591.severity = error`).

#### Usage
1. Copy `configs/csharp.editorconfig` to your project's root directory as `.editorconfig`.
2. Ensure your editor supports EditorConfig (see [Supported Editors](#supported-editors)).
3. Verify the settings align with your team's style guide. Customize as needed by editing the file (e.g., adjust `indent_size` or `end_of_line`).

#### Example
```csharp
// Example C# code formatted with csharp.editorconfig
namespace MyProject.Utilities // PascalCase, matches folder structure
{
    public class DataProcessor // PascalCase
    {
        private readonly int _maxRetries; // Underscore prefix for private readonly fields

        public DataProcessor(int maxRetries) // PascalCase, no 'this.' qualification
        {
            _maxRetries = maxRetries;
        }

        public async Task ProcessAsync() // Async suffix for async methods
        {
            int attemptCount = 0; // camelCase for local variables
            while (attemptCount < _maxRetries)
            {
                // Modern C# features encouraged (e.g., null-coalescing, pattern matching)
                await Task.Delay(1000);
                attemptCount++;
            }
        }
    }
}
```

#### Customization
- Adjust indentation settings (`indent_size`, `tab_width`) to match your team's preferences.
- Modify severity levels (e.g., `error`, `warning`, `suggestion`) for diagnostics to align with your CI/CD pipeline.
- Update naming rules to reflect your project's conventions (e.g., change `pascal_case` to `camel_case` for specific symbols).
