# Floating point number datatypes

Floating point number datatypes are in accordance with the [IEEE 754 standard](https://ieeexplore.ieee.org/document/8766229). Other than standard, nothing is guaranteed about the exact format of the floating point numbers in the evaluation of expressions.

## Supported types

The following floating point formats can be passed to expressions and returned by expressions:

| Short name (identifier) | Name                     | Usual bit width |
| ----------------------- | ------------------------ | --------------- |
| `f16`                   | Half prescision binary   | 16 bits         |
| `f32`                   | Single prescision binary | 32 bits         |
| `f64`                   | Double prescision binary | 64 bits         |

## Other float-like types

Some other types can "act" like floating point numbers, but cannot be described by the previous categories.

| Short name (identifier) | Name                    | Description                                                                                                                                                                                                                                        |
| ----------------------- | ----------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `f`                     | Dynamic precision float | Type used mostly for constants. It stores enough information to be converted to any other float type. This conversion is done implicitly. Behaviour with in respect to a given expression can be further specifed in the expression specification. |