# UnrealScript Insulting Players Style Guide

This guide is for any project developed by us.
It is a result of trial and error, combined with ideas borrowed from some other languages.
You might find a lot of code in our repos that do not follow this style, this is because this
document was formulated after a lot of projects were finished and its specification differs greatly
from them.
As of 26.02.2023 none of the projects follow these guidelines.

*However* all new code from now on should conform to them.
Old code, ideally, should also be updated to use them, but that might take awhile due to the lack
of the specialized tooling for that.

## Formatting guidelines

### Naming rules

#### Code

* Names of classes, methods, enumerations, public fields: `PascalCase`;
* Filenames and directory names are `PascalCase`, e.g. `MyFile.uc`;
* Names of local variables, parameters: `camelCase`;
* Names of private, protected, internal and protected internal fields and properties: `_camelCase`;
* Naming convention is unaffected by variable/return type or modifiers such as `const`, `static`,
    `out`, etc;
* `none`, `default`, `super`, `false`/`true` and all other keywords should be in lower case;
* For casing, a “word” is anything written without internal spaces, including acronyms.
    For example, `MyJSON` instead of ~~`MyRPC`~~;
* Except for cycle counters such as `i`, `j` and `k`, always use meaningful variable names -
    there is no need to be stingy with characters.
    But do try not to make names longer than 20 characters
    (soft limit, can be broken if necessary).

#### Organization

Modifiers (for a single function/variable) occur in the following order:
`public`, `protected`, `private`, `abstract`, `final`, `static`, `simulated`, `function`;

Class member ordering:

* Group class members in the following order:
    1. `struct`s, `enum`s and `delegate`s;
    2. `static` and `const` fields;
    3. Other fields;
    4. If applicable, methods that can at least in some sense be thought of as constructors and
        finalizers for the instances of the class.
    5. Methods.
* Within each group, elements should be in the following order:
    1. Public.
    2. Protected.
    3. Private.

#### Whitespace rules

Developed from Google Java style.

* No trailing whitespaces are allowed;
* A maximum of one statement per line;
* A maximum of one assignment per statement;
* Indentation of 4 spaces, no tabs;
* Column limit: 100;
* One empty line between functions;
* No line break before opening brace;
* No line break between closing brace and `else`;
* Braces used even when optional;
* Space after `if`/`for`/`while` etc., and after commas;
* Inside `for` cycle's declaration put space after each semicolon;
* No space after an opening parenthesis or before a closing parenthesis;
* No space between a unary operator and its operand.
    One space between the operator and each operand of all other operators;
* In case class has any modifiers (`abstract`, `config`, etc.), each modifier
    has to be specified on its own line in the following order (with specified casing):
    `native`, `abstract`, `within`, `transient`, `config`, `perObjectConfig`, `dependsOn`.
    Semicolon must appear after the last modifier without any space or line break;
* Names of enumeration variants should start with common sequence of upper-case characters
    (if possible, abbreviation of the enumeration's name, e.g. for `JustCoolEnum`
    it should be `JCE`),
    then underscore, then `CamelCase` name (e.g. `JCE_SubType1`, `JCE_SubType2`);
* Each enumeration variant should appear on its own line;
* Line wrapping rules:
    1. In general, line continuations are indented 4 additional spaces;
    2. For function definitions and calls, if the arguments do not all fit on one line they
        should be broken up onto multiple lines, with each argument on its own line, indented by
        4 spaces.
        In that case, there should be line breaks after opening parenthesis and before closing one.
        The code example below illustrates this;
* Any function's body can consist of three different parts that have to be separated by line breaks:
    1. `local` variable definitions;
    2. Set of guard checks - `if` block with a single `return` instruction.
        These guard checks have special syntax - `return` instruction shouldn't be surrounded by
        braces, but all of the `return` instructions should be aligned on the same vertical level
        (equal to the minimal possible multiple of 4).
        They can also be interspersed with assignment instruction to variables, as long as resulting
        values of said variables are immediately tested in the next `if` check.

```unrealscript
class MyCoolClass
    abstract
    config(MyCoolConfig);

struct MyStruct {
    public int openField;
    public string closedField;
};

enum JustCoolEnum {
    JCE_SubType1,
    JCE_SubType2,
    JCE_WhateverThisIs
};

protected abstract simulated function bool LongEnoughFunctionNameSoThatArgumentsDoNotFitIntoTheLine(
    int argument1,
    int argument2
    int argument3
) {
    local bool booleanVariable;
    local int anotherVariable;

    if (argument1 < 0) return false;
    booleanVariable = (argument2 > 13);
    if (booleanVariable) return true;
    if (argument3 == 7) return true;

    booleanVariable = (argument2 > 13);
    if (argument1 > 10) {
        return (argument1 + argument2 * argument3) > 12;
    }
    else {
        anotherVariable = argument1 * argument2 - argument3;
        if (booleanVariable) {
            return anotherVariable;
        }
        else {
            return anotherVariable * 10;
        }
    }
}
```

## Coding guidelines

### Constants

* Variables and fields that can be made `const` should always be made `const`;
* Prefer named constants to magic numbers.

### Function complexity

* Try not to make functions with more than 30 lines in them
    (only lines with actual instructions and `local` variable declarations count;
    not empty lines, comments or lines with single parenthesis/braces);
* Prefer nesting code blocks at most 2 times, avoid nesting more than 3 blocks.

```unrealscript
function MyFunc() {
    local int i;

    if (/*...*/) {
        for (i = 0; i < 100; i += 1) {
            //  Avoid nesting anything else inside this `if` block
            if (i == 5) {
                Log("`i` is equal to 5! Huzzah!");
            } else {
                Log("What a sad world we live in... without fives at all...");
            }
        }
    } else {
        /*...*/
    }
}
```

If your function is complex enough that these conditions cannot be satisfied -
consider moving some of the logic into auxiliary functions.

### Argument checks

Always check `Object` parameters for being `none`.
This check can only be dropped in internal methods that will only be called by other methods
within the same class and can guarantee that passed argument isn't `none`
(for example if they've already performed the check).

**NOTE** that execution of any code that doesn't come from your own code package might destroy
`Actor` objects, so checks on them might need to be redone.
If you have a reason to believe they won't - add a comment with an explanation why.

### Returning values from functions

* If function returns a value - it should be assigned to a variable, *especially* if that value
    is an `Object` or `struct`.
    Not following this rule might cause rare, but hard to debug bugs;
* If you call a function with an `out` parameter - explicitly mark such parameter with /*out*/.

### Increment/decrement operators

Avoid `--` or `++` operators and use `+=` and `-=` instead.

### Files and directories

* Content of the files should be limited to ASCII, allowing use of any compatible encoding.
    In rare circumstances (when one needs to define `string` with non-ASCII characters)
    one can use UTF-16 BE;
* Top level structure of the project should consist of:
    1. `configs` directory with default configuration files for your project;
    2. `classes` or `sources` (but not both) for directory with source code;
    3. `docs` for any documentation you've decided to package along with your project.
    Their names should be in lower case.
* Large enough projects should further group their code files into sub-directories,
    which is possible when using [our tool](https://github.com/InsultingPros/KFCompileTool)
    for compilation.

### Other safety considerations

All following instructions are not simple preference, but vital requirements to avoid bugs or flaws
with UnrealScript implementation:

* Never store `Actor` instances in non-`Actor` objects;
* Make sure to clean up any `Object` references from `default` values before level change;
* Do not change dynamic array's `length` with `--`, `++`, `+=` or `-=` and use explicit assignment:
    `array.length = array.length + 1`;
* Do not use `%` - it works on `float` argument, making it ill-suitable for integer arithmetic;
* Do not use recursion.

## Documentation guidelines

Three slashes `///` denote documentation comment - a comment that can potentially be used to
generate external [reference documentation](https://documentation.divio.com/reference/).
It should come as a sequence of `///`-prefixed comments right before field/struct/enum/function's
declaration without any empty lines in between.
Class comments are special and should come right after its declaration in the sequence of
line comments that start with `//!`.

Somewhat unrelated, but copyright and license info should be specified in the
`/** */` block comment, where each line starts with ` *`:

```unrealscript
/**
 * Copyright 2022-2023 Some guy
 *------------------------------------------------------------------------------
 * Optional license info: GPL, MIT, whatever.
 */
class MyClass;

//! Documenting class: first explanatory sentence.
//!
//! This is and extensive class doc!

/// This is a struct: first explanatory sentence.
///
/// Here is what it does!
struct MyStruct {
    public int field;
};

/// Also documentation for the function: first explanatory sentence.
///
/// It should describe what it does and what is the meaning of its arguments and return value.
public function float MyFunc(int arg1, bool arg2) {
    /*...*/
}
```

### Summary sentence

In API documentation, the first line should be a single-line short sentence providing
a summary of the code and should be kept short.

The summary line should be written in third person singular present indicative form.
Basically, this means write ‘Returns’ instead of ‘Return’.

It should be separated from the rest of the documentation by an empty comment line:
simply `///` or `//!`.

### Rest of item's documentation

Rest of documentation should describe the method as a whole, along with the meaning of
its parameters and return value.
This is in contrast to javadoc, where they have had their own descriptions specified via
`@param` or `@return`, which in a lot of cases had to simply duplicate the rest of the description.

### Using Markdown

Within documentation comments, use Markdown to format your documentation.

Use top level headings (`#`) to indicate sections within your comment.
Common headings:

* `Examples` - for examples to illustrate usage.
    They should not attempt to explain basic concepts (or how to achieve common tasks),
    but simply how to use the method.
* `Errors` - for describing in which cases function can log an error.

Even if you only include one example, use the plural form: ‘Examples’ rather than ‘Example’.

Use backticks (`) to denote a code fragment within a sentence.
Use triple backticks (```) to write longer examples.
You don't need to specify UnrealScript as a language for triple backticks.

### Referring to types

To refer to a type, field or enum variant use combination of square brackets and backticks:

```unrealscript
/// The [`String`] passed in lorum ipsum...
/// To refer for a function use [`MyClass::MyFunction`].
```
