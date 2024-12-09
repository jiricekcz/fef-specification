# Configuration

Configuration is a set of rules for the parser of a FEF file. It can modify its behavior across the parsing of multiple files. It can be agreed upon beforehand, sent together with multiple formulas, or be included in some file, that uses the FEF format itself.  
It can be useful to modify the default configuration, for example, when sending a large number of formulas, that need little precision, thus using f16 as all the numbers.

Configuration is a list of key-value pairs. If the parsing of an expression is affected by a configuration, it is noted in the expression's description.

## Binary encoding of configuration keys

The binary encoding of configuration keys is as follows:
1. A [variable length enum](/binary_types/Variable%20Length%20Enum.md) describing the configuration *identifier*.
2. If the identifier is greater than `127` (`0x7F`), then a [variable length enum](/binary_types/Variable%20Length%20Enum.md) describing the number of bytes the configuration value takes.
3. Value of the configuration key as described in the configuration key's documentation. If the identifier is `127` (`0x7F`) or less, then the value is **always** a variable length enum (these are called *enum* configurations).

## Binary encoding of a configuration 

A whole set of configurations are encoded as a single [variable length enum](/binary_types/Variable%20Length%20Enum.md) describing the number of configurations, followed by the binary [encoding of each configuration key-value pair](#binary-encoding-of-configuration-keys).

## Configuration Table

### Enum configurations

Enum configurations have identifiers less than or equal to `127` (`0x7F`). Their values are encoded as a variable length enum. This ensures that the configuration can always be parsed correctly (and ignored if needed), even if the interpretation of the identifier is not specified by the version of the specification the parser uses. It also ensures low overhead for the most common configurations that take little space by them selves. 
| Name                                                 | Identifier   | Possible Values                                                     | Default Value | Short Name      |
| ---------------------------------------------------- | ------------ | ------------------------------------------------------------------- | ------------- | --------------- |
| [Float format](/configuration/Float%20Format.md)     | `0` (`0x00`) | `b16`, `b32`, `b64`                                                 | `b64`         | `FLOAT_FORMAT ` |
| [Integer format](/configuration/Integer%20Format.md) | `1` (`0x01`) | `i8`, `i16`, `i32`, `i64`, `i128`,`u8`, `u16`, `u32`, `u64`, `u128` | `i32`         | `INT_FORMAT`    |

### Non-enum configurations

Non-enum configurations have identifiers greater than `127` (`0x7F`). They are encoded as described in the [binary encoding of configuration keys](#binary-encoding-of-configuration-keys) section. There are currently no non-enum configurations defined.

## Notes

- If a configuration block is created in accordance with a newer version of the specification, it is still possible to parse the configuration block with an older version of the specification and skip the keys, that are not defined in the older version. This ensures very robust forward compatibility of the configuration block. It also theoretically allows for easier backward compatibility in case a configuration key is removed.