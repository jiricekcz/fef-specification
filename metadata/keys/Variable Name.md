# Variable Name

A metadata key used to store a short name of a variable used for inlining when showing a formula.

## Format of value

Value for this metadata key is made of two parts:
1. A single [Variable Length Enum](../../binary_types/Variable%20Length%20Enum.md) describing the variable id this name is for.
2. A single [string](../../binary_types/String.md) that is the name of the variable.
