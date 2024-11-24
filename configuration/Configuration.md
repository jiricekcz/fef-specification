# Configuration

Configuration is a set of rules for the parser of a FEF file. It can modify its behavior across the parsing of multiple files. It can be agreed upon beforehand, sent together with multiple formulas, or be included in some file, that uses the FEF format itself.  
It can be useful to modify the default configuration, for example, when sending a large number of formulas, that need little precision, thus using f16 as all the numbers.

Configuration is a list of key-value pairs. If the parsing of an expression is affected by a configuration, it is noted in the expression's description.

## Binary encoding of configuration keys

The binary encoding of configuration keys is as follows:
1. A [variable length enum](/binary_types/Variable%20Length%20Enum.md) describing the configuration *identifier*.
2. Value of the configuration key as described in the configuration key's documentation.

## Binary encoding of a configuration 

A whole set of configurations are encoded as a single [variable length enum](/binary_types/Variable%20Length%20Enum.md) describing the number of configurations, followed by the binary [encoding of each configuration key-value pair](#binary-encoding-of-configuration-keys).

## Configuration Table

| Name                                                 | Identifier   | Possible Values                                                     | Default Value |
| ---------------------------------------------------- | ------------ | ------------------------------------------------------------------- | ------------- |
| [Float format](/configuration/Float%20Format.md)     | `0` (`0x00`) | `b16`, `b32`, `b64`                                                 | `b64`         |
| [Integer format](/configuration/Integer%20Format.md) | `1` (`0x01`) | `i8`, `i16`, `i32`, `i64`, `i128`,`u8`, `u16`, `u32`, `u64`, `u128` | `i32`         |