# Float

## Abstract

A float is a binary type that represents a number with a fractional part. The exact format of the float is determined by the type of the float as per the [IEEE 754 standard](https://ieeexplore.ieee.org/document/8766229).

If the parameters are not specified in the context, the values is determined by the [Float Format](/configuration/Float%20Format.md) key in the [configuration](/configuration/Configuration.md#configuration-table).

## Format

Float is a sequence of bytes in Big-Endian byte order. The length of the float is determined by the [Float Format](/configuration/Float%20Format.md) key in the [configuration](/configuration/Configuration.md#configuration-table). The possible values of this key correspond to types specified in the [IEEE 754 standard](https://ieeexplore.ieee.org/document/8766229).