# Integer

## Abstract

An integer is a binary type that represents a number without a fractional part. It range and exact format is determined by two parameters:
- *bit length* - the length of the integer in bits.
- *signedness* - whether the integer can represent negative numbers.

## Format

Integer is a sequence *bit lenght*/2 bytes in Big-Endian byte order. If the integer is signed, it should be parsed as a signed *bit length*-bit integer. If the integer is unsigned, it should be parsed as an unsigned *bit length*-bit integer.

If the parameters are not specified in the context, the values is determined by the [Integer Format](/configuration/Integer%20Format.md) key in the [configuration](/configuration/Configuration.md#configuration-table).

