# Integer Literal Expression

## Abstract

An integer literal expression is used to specify a constant integer. Different types of integer literals can represent different length and format of the data.

## Format

All integer literals are sequences of bytes in Big-Endian byte order, if signed they should be parsed as signed integers in the [Two's complement](https://en.wikipedia.org/wiki/Two%27s_complement) format. 

Defined formats are:

### 8-bit Signed

An 8-bit signed integer literal expression is a sequence of 1 byte. It should be parsed as an 8-bit signed integer in the [Two's complement](https://en.wikipedia.org/wiki/Two%27s_complement) format.

### 8-bit Unsigned

An 8-bit unsigned integer literal expression is a sequence of 1 byte. It should be parsed as an 8-bit unsigned integer.

### 16-bit Signed

A 16-bit signed integer literal expression is a sequence of 2 bytes in Big-Endian byte order. It should be parsed as a 16-bit signed integer in the [Two's complement](https://en.wikipedia.org/wiki/Two%27s_complement) format.

### 16-bit Unsigned

A 16-bit unsigned integer literal expression is a sequence of 2 bytes in Big-Endian byte order. It should be parsed as a 16-bit unsigned integer.

### 32-bit Signed

A 32-bit signed integer literal expression is a sequence of 4 bytes in Big-Endian byte order. It should be parsed as a 32-bit signed integer in the [Two's complement](https://en.wikipedia.org/wiki/Two%27s_complement) format.

### 32-bit Unsigned

A 32-bit unsigned integer literal expression is a sequence of 4 bytes in Big-Endian byte order. It should be parsed as a 32-bit unsigned integer.

### 64-bit Signed

A 64-bit signed integer literal expression is a sequence of 8 bytes in Big-Endian byte order. It should be parsed as a 64-bit signed integer in the [Two's complement](https://en.wikipedia.org/wiki/Two%27s_complement) format.

### 64-bit Unsigned

A 64-bit unsigned integer literal expression is a sequence of 8 bytes in Big-Endian byte order. It should be parsed as a 64-bit unsigned integer.

## Equivalency

Two integer literals should only be treated as equivalent if they have the same signedness and value. For example `int8(1)` and `int16(1)` are equivalent, but `int8(1)` and `uint8(1)` are not. No integer literal should also ever be considered equivalent to a float literal, even if they represent the same real number.

All parsers/evaluators must treat equivalent integer literals as equivalent, regardless of their size. This allows for general integer compression.
