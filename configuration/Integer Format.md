# Integer Format

The Integer Format configuration key defines the format of integer literals. 

## Possible Values

| Value | Identifier | Description             |
| ----- | ---------- | ----------------------- |
| `i8`  | `0x00`     | 8 bit signed integer    |
| `i16` | `0x01`     | 16 bit signed integer   |
| `i32` | `0x02`     | 32 bit signed integer   |
| `i64` | `0x03`     | 64 bit signed integer   |
| `u8`  | `0x10`     | 8 bit unsigned integer  |
| `u16` | `0x11`     | 16 bit unsigned integer |
| `u32` | `0x12`     | 32 bit unsigned integer |
| `u64` | `0x13`     | 64 bit unsigned integer |

## Format

This configuration value is in standard format - a single [variable length enum](/binary_type/Variable%20Length%20Enum.md) with the *identifier* of the selected value. 