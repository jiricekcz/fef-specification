# Float Literal Expression

## Abstract

A float literal expression is used to specify a constant float.

## Configuration

The parsing of this expression is determined by the [Float Format](/configuration/Float%20Format.md) key in the [configuration](/configuration/Configuration.md#configuration-table).

## Expression Data

The expression parses a single [float](/binary_types/Float.md) with parameters based on the [configuration](#configuration).

## Expression Result

Expression result varies based on the [configuration](#configuration). Described by this table:

| [Float Format](/configuration/Float%20Format.md) | [Result Type](/datatypes/Floats.md) |
| ------------------------------------------------ | ----------------------------------- |
| `b16`                                            | `f16`                               |
| `b32`                                            | `f32`                               |
| `b64`                                            | `f64`                               |
