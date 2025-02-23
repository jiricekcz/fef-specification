# Formula Exchange Format (FEF)

Specification for the Formula Exchange Format (FEF) [version](./Versioning.md) 0.3.0

## Abstract

The Formula Exchange Format (FEF) is a binary format for saving and loading mathematical formulas.

## Goals

The goals of FEF are:
- Provide a stable, versioned and where possible backwards and forwards compatible format
- Have minimal size
- Be able to be integrated into other formats
- Be language agnostic
 
## Format

### Part

As a binary format, FEF is a sequence of bytes. Because most data in the FEF format is variable length, the format will be described by an ordered sequence of *parts*, where a *part* is a sequence of bytes in known format. When a part is mentioned, it will include a link to the description of that *part*.

### Sequence of parts

The first [*part*](#part) of the sequence is a [variable length enum](/binary_types/Variable%20Length%20Enum.md), that indicates the major version of the FEF format (in this case corresponding to the number `0`).

Second part is the file content itself. It is described by a [variable length enum](/binary_types/Variable%20Length%20Enum.md) that indicates the file content type and then the data of such file. Format of this data is specified by the file content type.

If the file content type is not in this table, the parser should notify the caller that the file content type is not recognized and should not attempt to parse the file content. This is a fatal parsing error.

In this version the following content types are defined:

| Integer value | Content Type                                              | Description                                                                                 | Short name       |
| ------------- | --------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ---------------- |
| `1` (`0x01`)  | [Raw Formula](/file_content_types/Raw%20Formula.md)       | A single evaluatable mathematical formula with no attached data                             | `RAW_FORMULA`    |
| `2` (`0x02`)  | [Single Formula](/file_content_types/Single%20Formula.md) | A single evaluatable mathematical formula with possible metadata and configuration attached | `SINGLE_FORMULA` |
