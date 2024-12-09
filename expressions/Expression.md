# Expression

An expression is the building block of a formula. It consists of an *identifier* and *data*. The *identifier* is a [variable length enum](/binary_type/Variable%20Length%20Enum.md) that indicates the type of the expression. The *data* is a sequence of bytes that is interpreted based on the *identifier*. Usually the shorter the *data*, the lower value the *identifier* will be to provide a lower percentage overhead. 

If an *identifier* present in the format is not described by this specification, the parser should notify the caller that the *identifier* is not recognized and should not attempt to parse the expression. This is a fatal parsing error.

## Expression Sets

An expression set is a set of expression with some common use or functionality. Expression sets are used to group expressions that are used together into well defined groups. A parser can then only **partially** implement the specification by only implementing the expression sets that are needed for the specific use case, when, for example, the size of the parser is a concern. By default, it is expected that all parsers implement all expression sets. All parsers must implement the [Core Expression Set](#core-expression-set).

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

| Identifier    | Expression                                             | Expression Type                                 | Expression Set               | Short name |
| ------------- | ------------------------------------------------------ | ----------------------------------------------- | ---------------------------- | ---------- |
| `4` (`0x04`)  | [Variable](/expressions/Variable.md)                   | [Variable](#variable-expressions)               | [Core](#core-expression-set) | `VAR`      |
| `8` (`0x08`)  | [Integer Literal](/expressions/Integer%20Literal.md)   | [Literal](#literal-expressions)                 | [Core](#core-expression-set) | `INT`      |
| `9` (`0x09`)  | [Float Literal](/expressions/Float%20Literal.md)       | [Literal](#literal-expressions)                 | [Core](#core-expression-set) | `FLOAT`    |
| `10` (`0x0A`) | [True Literal](/expressions/True%20Literal.md)         | [Literal](#literal-expressions)                 | [Core](#core-expression-set) | `TRUE`     |
| `11` (`0x0B`) | [False Literal](/expressions/False%20Literal.md)       | [Literal](#literal-expressions)                 | [Core](#core-expression-set) | `FALSE`    |
| `16` (`0x10`) | [Addition](/expressions/Addition.md)                   | [Binary Operator](#binary-operator-expressions) | [Core](#core-expression-set) | `ADD`      |
| `17` (`0x11`) | [Subtraction](/expressions/Subtraction.md)             | [Binary Operator](#binary-operator-expressions) | [Core](#core-expression-set) | `SUB`      |
| `18` (`0x12`) | [Multiplication](/expressions/Multiplication.md)       | [Binary Operator](#binary-operator-expressions) | [Core](#core-expression-set) | `MULT`     |
| `19` (`0x13`) | [Division](/expressions/Division.md)                   | [Binary Operator](#binary-operator-expressions) | [Core](#core-expression-set) | `DIV`      |
| `20` (`0x14`) | [Integer Division](/expressions/Integer%20Division.md) | [Binary Operator](#binary-operator-expressions) | [Core](#core-expression-set) | `IDIV`     |
| `21` (`0x15`) | [Modulo](/expressions/Modulo.md)                       | [Binary Operator](#binary-operator-expressions) | [Core](#core-expression-set) | `MOD`      |
| `22` (`0x16`) | [Power](/expressions/Power.md)                         | [Binary Operator](#binary-operator-expressions) | [Core](#core-expression-set) | `POW`      |
| `23` (`0x17`) | [Negation](/expressions/Negation.md)                   | [Unary Operator](#unary-operator-expressions)   | [Core](#core-expression-set) | `NEG`      |
| `24` (`0x18`) | [Root](/expressions/Root.md)                           | [Binary Operator](#binary-operator-expressions) | [Core](#core-expression-set) | `ROOT`     |
| `25` (`0x19`) | [Integer Root](/expressions/Integer%20Root.md)         | [Binary Operator](#binary-operator-expressions) | [Core](#core-expression-set) | `IROOT`    |
| `32` (`0x20`) | [Square](/expressions/Square.md)                       | [Unary Operator](#unary-operator-expressions)   | [Core](#core-expression-set) | `SQUARE`   |
| `33` (`0x21`) | [Cube](/expressions/Cube.md)                           | [Unary Operator](#unary-operator-expressions)   | [Core](#core-expression-set) | `CUBE`     |
| `34` (`0x22`) | [Square Root](/expressions/Square%20Root.md)           | [Unary Operator](#unary-operator-expressions)   | [Core](#core-expression-set) | `SQRT`     |
| `35` (`0x23`) | [Cube Root](/expressions/Cube%20Root.md)               | [Unary Operator](#unary-operator-expressions)   | [Core](#core-expression-set) | `CBRT`     |
| `36` (`0x24`) | [Reciprocal](/expressions/Reciprocal.md)               | [Unary Operator](#unary-operator-expressions)   | [Core](#core-expression-set) | `RECIP`    |

### Extended Expressions (*identifier* >= 128)

