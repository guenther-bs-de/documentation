# Global Rules for FileMaker-AI

These rules establish guidelines that any AI should follow when performing tasks in or for FileMaker, incorporating the Günther Business Solutions GmbH coding conventions and ensuring compatibility with FileMaker systems and practices.

## General Vocabulary and Conventions

GBS
: acronym used for Günther Business Solutions GmbH

Advanter
: The ERP software system developed by Günther Business Solutions GmbH.

Script
: Always spelled with a `c`and never a 'k'.

## Rules for Valid FileMaker-Compatible Code

1. The code must be FileMaker compatible.
2. Follow Günther Business Solutions GmbH's naming conventions for fields, scripts, and layouts.
   - Use descriptive, concise names that convey purpose without excessive length.
   - Naming conventions can - sadly - vary and should be adjusted to fir the surrounding code


### Variable name conventions

- Standard variable name conventions
  - Global var: `$$GlobalVariableName`
  - Script var: `$ScriptVariableName`
  - Let var: `vLetVariablename`
  - CF-parameter var: `pParameterName`
  - JSON key: `json_key_name`
    - In some cases, for example 'JVars', variable names are used as json keys in which case the JSON key may look like `$ScriptVariableName` (inclusive of the `$` symbol!)

- Script variables (together with script parameter passing) should be prefered to Global variables in order to avoid scope problems / unclarity
- Variable names must NOT use spaces or dots
- JSON keys must NOT use dots

  
- `Zähler`
  - The standard looping variable for 1-based operations
  - Global var: `$$Zähler`
  - Script var: `$Zähler`
  - Let var: `vZähler`
  - CF-parameter var: `pZähler`
  - JSON key: `zähler`
- `ZählerMax`
  - The standard looping variable end for 1-based operations that include `$Zähler = $ZählerMax`
- `Index`
  - The standard looping variable for 0-based operations (primarily JSON arrays)
  - Global var: `$$Index`
  - Script var: `$Index`
  - Let var: `vIndex`
  - CF-parameter var: `pIndex`
  - JSON key: `index`
- `IndexCount`
  - The standard looping variable end for 1-based operations that include `$Index = $IndexCount`


### Calculations and Custom Functions

Example Custom Function including a Let statement

```filemaker
/* G_NR_Hypotenuse ( pLength1 ; pLength2 )

returns the length of the hypothenuse of a right angle triangle with side lengths of pLength1 and pLength2.

Parameters
- pLength1 (Number) - length of side 1
- pLength2 (Number) - length of side 2

Returns
Length of the hypotenuse

2026-02-10 RW: v1.0
*/
Let (
[

vLength1 = GetAsNumber ( pLength1 ) ;
vLength2 = GetAsNumber ( pLength2 ) ;
vResult  = Sqrt ( vLength1^2 + vLength2^2 )

];

vResult

)
```

Example typical While function to iterate over a values-string, demonstrating spacing, indenting, standard looping variable name (vZähler for 1-based operations and vIndex for 0-based operations)

```filemaker
While (
[

/* function params */
pText = "Some¶Input¶Text¶input¶alsdo¶counts" ;
pSearchLine = "Input" ;

/* read params */
vText = pText ;
vSearchTerm = pSearchLine ;

vResult = 0 ;

vZähler = 1;
vZählerMax = ValueCount ( vText )

]; vZähler ≤ vZählerMax ; [

vValue = GetValue ( vText ; vZähler ) ;

vResult = vResult + (vValue = pSearchLine ) ;

vZähler = vZähler + 1

];

vResult

)
```

- Calulation comments
   - Calculations comments should always use `/* block comment */` syntax rather than `// line comment` syntax. This avoids two problems:
     1. where calculations are displayed as a single line it is not possible to see where a `// comment` endsa and the next line begins
     2. when copying code from mac to windows, incorrectly copied EOL characters can lead to everythibng after a `// comment` being commented out
- Custom functions
  - Should start with a block comment detailing the function
        /* CustomFunction Name ( pParam1 ; pParam2 ; … )
        «What the Function does or returns»
       
  - CF-Parameters should have the form `pParameterName` (lowerCamelCase with prefix `p`).
  - Let-Variables should have the form `vVariableName` (lowerCamelCase with prefix `v`).
  - JSON keys on the other hand should be `lower_snake_case`
    - JSON keys are case-sensitive, and this convention simply avoids case-based key reference problems by requiring lowercase.
  - Spacing for parentheses and operators should use a single space. For calculations:
   - Minimal hardcoding—use parameters and modular design principles.
   - Clearly commented code with explanations of parameters and returned values.


## General Aims

- Maintainability and readability is foremost, above performance
- Where possible use the 'code is documentation' ethic
  - Prefer well named code over comments
  - Because comments are 'dead', age badly, and after time diverge from the reality of the code
- DRY code is to be preferred
  - Where a function is required both for the current record or for the current found set, use a loop with a `$aktDS` parameter to either process the entire found set or skip out after the current record.

## Script Conventions

- Scripts should start with `Perform Script [ “SYS Line 1“ ]`
- Script Parameters
  - Read Parameters at the top of the script
- Where scripts need hard-coded settings (that may later be developed into a system setting (`Voreinst`) make a `Scripteinstellungen` section at the top of the script
- Guard blocks
  - Scripts that return no result - or a very simple result - may use guard blocks to exit before the script gets started
- Use single pass loops for TRY - CATCH
- Script Result
  - Preferably store the result in a variable before returning
    - helps debugging
- Every script should have an empty line at the very end
  - This makes it possible to scip the entire script in the debugger
- Scripts which set an OnTimer script call
  - should have an Exit Script step followed by the OnTimer script step to cancel the OnTimer step at the end
  - so that OnTimer processes can be caught and cancelled in the debugger
