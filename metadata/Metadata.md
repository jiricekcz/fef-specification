# Metadata

Metadata is a collection of key-value pairs with predefined keys, that can describe a file content. Individual file content types can specify which metadata keys can be used with them. If other keys are present, they should be parsed and shouldn't cause fatal errors. Their interpretation is however undefined.

## Binary encoding of metadata keys

The binary encoding of metadata keys is as follows:
1. A [variable length enum](/binary_types/Variable%20Length%20Enum.md) describing the metadata *identifier*.
2. A [variable length enum](/binary_types/Variable%20Length%20Enum.md) describing the number of bytes the metadata value takes.
3. Value of the metadata key as described in the metadata key's documentation.

## Binary encoding of metadata

A whole set of metadata is encoded as a single [variable length enum](/binary_types/Variable%20Length%20Enum.md) describing the number of metadata pairs. If this number in non-zero, it is followed by a [variable length enum](/binary_types/Variable%20Length%20Enum.md) describing the number of bytes the metadata takes, followed by the binary [encoding of each metadata key-value pair](#binary-encoding-of-metadata-keys). If after reading the specified number of bytes, not all metadata pairs are read, the file is considered invalid. If all metadata pairs are read and there are still bytes left, these bytes are skipped and ignored. This can be useful to create a padding for in-place editing of the file. No parser should infer any meaning from these bytes and they should be safe to remove.

