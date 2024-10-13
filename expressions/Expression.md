# Expression

An expression is the building block of a formula. It consists of an *indetifier* and *data*. The *identifier* is a [variable length enum](/datatypes/Variable%20Length%20Enum.md) that indicates the type of the expression. The *data* is a sequence of bytes that is interpreted based on the *identifier*. Usually the shorter the *data*, the lower value the *identifier* will be to provide a lower percentage overhead. 

If an *identifier* present in the format is not described by this specification, the behaviour of any parser is undefined. This allows for the introduction of more expressions in the future without introducing breaking changes.

## Expression Sets

An expression set is a set of expression with some common use or functionality. Expression sets are used to group expressions that are used together into well defined groups. A parser can then only **partialy** implement the specification by only implementing the expression sets that are needed for the specific use case, when, for example, the size of the parser is a concern. By default, it is expected that all parsers implement all expression sets. All parsers must implement the [Core Expression Set](#core-expression-set).

### Core Expression Set

The core expression set is the most basic set of expressions. It contains basic literals and operators as well as variables. It **must** be implemented by all parsers.

## Expression Types

An expression type is a fairly arbitrary grouping of expressions based on our understanding of the expressions. It has no rigid definition, so it is mostly used for organization and documentation purposes.

### Literal Expressions

A literal expression is an expression that represents a constant value - most commonly a number. Different types of literals can represent different length and format of the data.

### Unary Operator Expressions

A unary operator expression is an expression that represents an operation that takes one operand (an expression).

### Binary Operator Expressions

A binary operator expression is an expression that represents an operation that takes two operands (expressions).

### n-ary Operator Expressions

An n-ary operator expression is an expression that represents an operation that takes n operands (expressions), where n is a fixed number larger than 2.

### Variable Expressions

A variable expression is an expression that represents a variable. It is used to refer to a non-constant value.

## Expressions

Here are the tables of expressions that are defined in this version of the specification.

### Elementary Expressions (*identifier* < 128)

Elementary expressions are either used very often, or benefit from a very low overhead (e.g. common literals and operators, variables or single byte literals).

| Identifier | Expression | Expression Type | Expression Set |
| ---------- | ---------- | --------------- | -------------- |

### Extended Expressions (*identifier* >= 128)

