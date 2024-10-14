# Addition Expression

## Abstract

Performs addition on two operands.

## Expression Data

Expression reads two expressions as operands.

## Expression Result

The expression result depends on the operand. If the combination of operands is not described by this table, the result is undefined behaviour.

| Operand 1                          | Operand 2                                                                              | Result Type                                                                                                                                                  | How the value is obtained                                                                              | Special Cases                                 |
| ---------------------------------- | -------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ | --------------------------------------------- |
| [`integer`](/datatypes/Integer.md) | [`integer`](/datatypes/Integer.md) of the same type                                    | [`integer`](/datatypes/Integer.md) of the same type                                                                                                          | Integer addition                                                                                       | Overflow [throws an error](/errors/Errors.md) |
| [`integer`](/datatypes/Integer.md) | [`integer`](/datatypes/Integer.md) of different length, but same sign                  | [`integer`](/datatypes/Integer.md) of the longer type                                                                                                        | Convert shorter integer to longer, then add                                                            | Overflow [throws an error](/errors/Errors.md) |
| [`integer`](/datatypes/Integer.md) | [`integer`](/datatypes/Integer.md) of different sign and length                        | signed [`integer`](/datatypes/Integer.md) of the longer type                                                                                                 | Convert shorter integer to the same length as the longer, keeping the sign. Add using integer addition | Overflow [throws an error](/errors/Errors.md) |
| [`float`](/datatypes/Floats.md)    | [`float`](/datatypes/Floats.md)                                      of the same type  | [`float`](/datatypes/Floats.md) of the same type                                                                                                             | [IEEE 754](https://ieeexplore.ieee.org/document/8766229)              float addition                   | None                                          |
| [`float`](/datatypes/Floats.md)    | [`float`](/datatypes/Floats.md)                                      of different type | [`float`](/datatypes/Floats.md) that can without loss of precision represent both operands. If none available, which float is picked is undefined behaviour. | Convert both to the result type, then add using float addition.                                        | None                                          |
| [`integer`](/datatypes/Integer.md) | [`float`](/datatypes/Floats.md)                                                        | [`float`](/datatypes/Floats.md) of the same type as the float operand                                                                                        | Convert integer to float, then add using float addition                                                | None                                          |
| [`float`](/datatypes/Floats.md)    | [`integer`](/datatypes/Integer.md)                                                     | [`float`](/datatypes/Floats.md) of the same type as the float operand                                                                                        | Convert integer to float, then add using float addition                                                | None                                          |
