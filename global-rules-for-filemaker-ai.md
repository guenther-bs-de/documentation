# Global Rules for FileMaker-AI

These rules establish guidelines that any AI should follow when performing tasks in or for FileMaker, incorporating the Günther Business Solutions GmbH coding conventions and ensuring compatibility with FileMaker systems and practices.

## General Vocabulary and Conventions
- **Advanter**: The ERP software system developed by Günther Business Solutions GmbH.
- **Script**: Always spelled without a 'K'.

## Rules for Valid FileMaker-Compatible Code
1. Follow Günther Business Solutions GmbH's naming conventions for fields, scripts, and layouts.
   - Use descriptive, concise names that convey purpose without excessive length.

2. When creating custom functions or calculations, ensure:
   - Parameters for custom functions should start with a lowercase `p`, followed by a capitalized letter, and use CamelCase (e.g., `pParameterName`).
   - Variables created within Let calculations should start with a lowercase `v`, followed by a capitalized letter, and use CamelCase (e.g., `vVariableName`).
   - Spacing for parentheses and operators should use a single space. For calculations:

     ```
     Let (
     [
         vVariable = pParameter ;
         vVariableTwo = pParameterTwo ;
         vResult = vVariable + vVariableTwo
     ];
     vResult
     )
     ```

   - Minimal hardcoding—use parameters and modular design principles.
   - Clearly commented code with explanations of parameters and returned values.

3. Maintain proper indentation and readability as per the organization's style guide.

4. Any FileMaker script or calculation logic must opt for compatibility and performance optimization.
   - Use functions efficiently to prevent unnecessary database calculations.
   - Prefer "Exit Script" with defined error codes.

5. For repeating operations, modular scripts or looping constructs should be reviewed to ensure proper handling of recursion depth or database performance impacts.

6. Include date/time formats that conform to localized or Advanter-compatible configurations.

7. Every AI-generated FileMaker operation must log any change requests clearly for functional and implementation trails.

## Reserved Terms and Localizations
Avoid using keywords or reserved terms that conflict with localized internal value names used by Advanter.

This document will serve as the standard guide for all automated processes related to FileMaker within Günther Business Solutions GmbH.