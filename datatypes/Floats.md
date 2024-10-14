# Floating point number datatypes

Floating point number datatypes are in accordance with the [IEEE 754 standard](https://ieeexplore.ieee.org/document/8766229). Other than standard, nothing is guaranteed about the exact format of the floating point numbers in the evaluation of expressions.

## Supported types

The following floating point formats can be passed to expressions and returned by expressions:

| Short name (identifier) | Name                     | Usual bit width |
| ----------------------- | ------------------------ | --------------- |
| `f16`                   | Half prescision binary   | 16 bits         |
| `f32`                   | Single prescision binary | 32 bits         |
| `f64`                   | Double prescision binary | 64 bits         |