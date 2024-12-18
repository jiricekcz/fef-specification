# Float Format

The Float Format configuration key defines the format of float literals as per the [IEEE 754 standard](https://ieeexplore.ieee.org/document/8766229). The full standard is not yet implemented, but values may be added in the future.

## Possible Values

| Value | Identifier | Description                    |
| ----- | ---------- | ------------------------------ |
| `b32` | `0x01`     | Single precision binary 32 bit |
| `b64` | `0x02`     | Double precision binary 64 bit |

## Format

This configuration value is in standard format - a single [variable length enum](/binary_type/Variable%20Length%20Enum.md) with the *identifier* of the selected value. 