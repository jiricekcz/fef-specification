# Float Literal Expressions

## Abstract

A float literal expression is used to specify a constant float. Different types of float literals can represent different length and format of the data. 

## Format

### 32-bit Binary

A 32-bit float literal expression is a sequence of 4 bytes in Big-Endian byte order. It should be parsed as a 32-bit binary float as per the [IEEE 754 standard](https://ieeexplore.ieee.org/document/8766229).

### 64-bit Binary

A 64-bit float literal expression is a sequence of 8 bytes in Big-Endian byte order. It should be parsed as a 64-bit binary float as per the [IEEE 754 standard](https://ieeexplore.ieee.org/document/8766229).

## Equivalency

Two float literals should only be treated as equivalent if they have the same type and value. Even if two floats represent the same real number (eg. `1`), they should not be considered equivalent if they have different types (eg. `32-bit` and `64-bit`). No floating point literal should also ever be considered equivalent to an integer literal, even if they represent the same real number.

This is because some parsers/evaluators may decide to propagate the type and/or precision of operands to the result of an operation and it is not always possible to determine whether converting between different floating point formats will result in a loss of precision or not.