# String

A string is a sequence of characters (text).

## Format

A string is a sequence of bytes in UTF-8 encoding. Its format is as follows:
1. A [Variable Length Enum](/binary_types/Variable%20Length%20Enum.md) describing the number of **bytes** (not characters) the string takes.
2. A valid UTF-8 encoded string of the specified byte-length length.