# Metadata

Metadata is a collection of key-value pairs with predefined keys, that can describe a file content. Individual file content types can specify which metadata keys can be used with them. If other keys are present, they should be parsed and shouldn't cause fatal errors. Their interpretation is however undefined.

## Binary encoding of metadata keys

The binary encoding of metadata keys is as follows:
1. A [variable length enum](/binary_types/Variable%20Length%20Enum.md) describing the metadata *identifier*.
2. A [variable length enum](/binary_types/Variable%20Length%20Enum.md) describing the number of bytes the metadata value takes.
3. Value of the metadata key as described in the metadata key's documentation.

## Binary encoding of metadata

A whole set of metadata is encoded as a single [variable length enum](/binary_types/Variable%20Length%20Enum.md) describing the number of metadata pairs. If this number in non-zero, it is followed by a [variable length enum](/binary_types/Variable%20Length%20Enum.md) describing the number of bytes the metadata takes, followed by the binary [encoding of each metadata key-value pair](#binary-encoding-of-metadata-keys). If after reading the specified number of bytes, not all metadata pairs are read, the file is considered invalid. If all metadata pairs are read and there are still bytes left, these bytes are skipped and ignored. This can be useful to create a padding for in-place editing of the file. No parser should infer any meaning from these bytes and they should be safe to remove.

## Duplicate keys

It is possible some metadata keys may be included multiple times. This is always specified as part of the metadata key documentation. If a key is not documented as being able to be included multiple times and it is and one must be selected automatically, the last occurrence of the key should be used by default.

## Metadata keys

Keys are predefined as part of the specification. Individual applications can also define their own keys. There are specified ranges where no official keys will be defined to allow for custom keys without the risk of collision with future official keys. There will also be third-party key ranges for keys defined by third-party applications. Key ranges not defined in the specification are reserved for future official keys.

Some keys can be used in multiple contexts. The exact meaning might change slightly depending on the context. Their format, however, remains the same, thus parsing is context-independent.

### Defined metadata keys

| Key (range)                                     | Name                                       | Description                                                                                     | Used with                                                   | Can be repeated |
| ----------------------------------------------- | ------------------------------------------ | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------- | --------------- |
| `1` (`0x01`)                                    | [Name](./keys/Name.md)                     | A name                                                                                          | [Single formula](../file_content_types/Single%20Formula.md) | `false`         |
| `2` (`0x02`)                                    | [Variable Name](./keys/Variable%20Name.md) | Short name of a variable                                                                        | [Single formula](../file_content_types/Single%20Formula.md) | `true`          |
| `16384` (`0x4000`) - `1048575` (`0xFFFFF`)      | 3rd Party keys                             | Can be claimed by third parties                                                                 | Depends on key                                              | Depends on key  |
| `1048576` (`0x100000`) - `2097151` (`0x1FFFFF`) | Custom keys                                | Can be freely used by closed applications without fear of collision with official metadata keys | Depends on key                                              | Depends on key  |