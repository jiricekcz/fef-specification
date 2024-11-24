# Variable Length Enum

## Abstract

A variable length enum is a binary representation of a variable, non-fixed length unsigned integer with the focus on efficiently encoding small numbers.

## Format

A variable length enum is a sequence of bytes in the following format:
- First bit is a flag indicating if there are more bytes to read.
- The next 7 bits are the value of the enum.

| Bit 7 | Bit 6 | Bit 5 | Bit 4 | Bit 3 | Bit 2 | Bit 1 | Bit 0 |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| More  | Value | Value | Value | Value | Value | Value | Value |

Both bit order and byte order are big-endian.

## Parsing a Variable Length Enum into an Integer

Parsing a variable length enum into an integer can be expressed with the following pseudocode:
```pseudo
function Parse_Variable_Length_Enum(byte_stream) {
    set value to 0 
    read byte from byte_stream {
        bit-shift value left by 7
        set part to (byte AND 0x7F)
        add part to value
        if byte AND 0x80 is 0 {
            return value
        }
    }
}
```


## Converting an Integer into a Variable Length Enum

Converting an integer into a variable length enum can be expressed with the following pseudocode:
```pseudo
function Convert_Integer_To_Variable_Length_Enum(value) {
    while value > 0x7F {
        set byte to (value AND 0x7F) OR 0x80
        write byte to output
        bitshift value right by 7
    }
    write value as byte to output
}
```
## Example

The representation of the number `66` (`0b01000010`) is equal to its binary representation (`0b01000010` = `0x42`).

The representation of the number `128` (`0b10000000`) are two bytes (`0b10000001 0b00000001`) which is equal to `0x81 0x01`. 

The representation of the number `255` (`0b11111111`) are two bytes (`0b10000001 0b01111111`) which is equal to `0x81 0x7F`.

## Notes

- Any value <= 127 can be represented as a single byte.
- It is allowed to prefix any value with any number of `0x80` bytes to alter the length of the variable length enum without changing the value.
  - This can be useful when changing the value of an enum in place.
  - It is not allowed to convey information in the number of `0x80` bytes.
  - Compression algorithms can remove these bytes to save space.
- When parsing a variable length enum, the parser is able to detect when it should stop reading.