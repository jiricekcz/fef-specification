# Single Formula

Single formula is a file content type that represents a single evaluatable and can have attached data. This is the most basic file content type that should be used on its own.

## Format

The format of a single formula is 3 parts:
1. [Configuration](../configuration/Configuration.md#binary-encoding-of-a-configuration) for this formula.
2. [Expression](../expressions/Expression.md) that represents the formula.
3. [Metadata](../metadata/Metadata.md) for this formula.

### Valid metadata keys

| Key                                                  | Contextual usage                                                   |
| ---------------------------------------------------- | ------------------------------------------------------------------ |
| [Name](../metadata/keys/Name.md)                     | Name of the formula.                                               |
| [Variable Name](../metadata/keys/Variable%20Name.md) | Short name of a variable used for inlining when showing a formula. |