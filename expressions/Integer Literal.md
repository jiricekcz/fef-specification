# Integer Literal Expression

## Abstract

An integer literal expression is used to specify a constant integer.

## Configuration

The parsing of this expression is determined by the [Integer Format](/configuration/Integer%20Format.md) key in the [configuration](/configuration/Configuration.md#configuration-table).

## Expression Data

The expression parses a single [integer](/binary_types/Integer.md) with parameters based on the [configuration](#configuration).

## Expression Result

Expression result varies based on the [configuration](#configuration). Described by this table:

| [Integer Format](/configuration/Integer%20Format.md) | [Result Type](/datatypes/Integer.md) |
| ---------------------------------------------------- | ------------------------------------ |
| `i8`                                                 | `i8`                                 |
| `i16`                                                | `i16`                                |
| `i32`                                                | `i32`                                |
| `i64`                                                | `i64`                                |
| `i128`                                               | `i128`                               |
| `u8`                                                 | `u8`                                 |
| `u16`                                                | `u16`                                |
| `u32`                                                | `u32`                                |
| `u64`                                                | `u64`                                |
| `u128`                                               | `u128`                               |

