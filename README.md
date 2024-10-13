# Formula Exchange Format (FEF)

Specification for the Formula Exchange Format (FEF) version 1.0.0

## Abstract

The Formula Exchange Format (FEF) is a binary format for saving and loading mathematical formulas.

## Goals

The goals of FEF are:
- Provide a stable, versioned a backwards-compatible format
- Have minimal size
- Be able to be integrated into other formats
- Be language agnostic
 
## Format

### Part

As a binary format, FEF is a sequence of bytes. Bacause most data in the FEF format is variable length, the format will be described by an ordered sequence of *parts*, where a *part* is a sequence of bytes in known format. When a part is mentioned, it will include a link to the description of that *part*.

### Sequence of parts

The first [*part*](#part) of the sequence is a [variable length enum](/datatypes/Variable%20Length%20Enum.md), that indicates the version of the FEF format (in this case coresponing to the number `1`).

Second part is a [variable length enum](/datatypes/Variable%20Length%20Enum.md) that indicates the file content type. If the value of the enum is not in this table, the behaviour of any parser is undefined. This allows for the introduction of more file content types in the future without introducing breaking changes.

In this version the following content types are defined:

| Integer value | Content Type                                              | Description                                                     |
| ------------- | --------------------------------------------------------- | --------------------------------------------------------------- |
| 1             | [Single Formula](/file_content_types/Single%20Formula.md) | A single evaluatable mathematical formula with no attached data |
