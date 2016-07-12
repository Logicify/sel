# SEL
SEL - is a simple and lightweight expression language which can be used in your application for extending configuration abilities.

# Examples

Simple interpolation

```
Hello, $username.
```

Invoke function

```
Uppercased value of test is $upper(test)
```

Invoke function with variable argument

```
Uppercased username is $upper($username)
```

Logical operations (conjunction)

```
$allOf(true, false, false)
```

More complex logical operations

```
$anyOf($not($myVar), $myVar)
```

## Key Features
* Simple syntax make it possible to keep lexer very light and quick.
* Easy extensible via custom handlers
* Default library contains handlers for logical operations.
* Evaluation result could be non-serializable value.

## Syntax

The only entity which can be interpreted is a "Function". Function invocation is an alphanumeric sequence followed by "$" sign. Optionally it could have 1 argument which should be wrapped in brackets.
Here is invocation of function called ```upper``` with value ```some str``` passed as argument:

```
$upper(some str)
```

Another example is invocation of the function without arguments.

```
$myFunc
```

## Evaluator

Each function should be registered in context. All language capabilities are based on this concept.
SEL evaluator comes with default function library which provides logical operations and some utilities.

If function invocation is the root of the syntax tree the result of evaluation of the top level function will become a result of evaluation of whole expression.
For example:

```
$allOf(true, false) -> FALSE
```
Result should be of type Boolean

However for expression which contains string in ther root of the syntax tree result will be a string:
```
Value is: $allOf(true, false) -> "Value is: False"
```

Credits
-------
* Dmitry Berezovsky, Logicify (<http://logicify.com/>)
* Alex Beskrovny, Logicify (<http://logicify.com/>)
