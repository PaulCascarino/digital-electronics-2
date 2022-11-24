# Lab 8: CASCARINO Paul

### Instruction set

1. Complete the conversion table with selected instructions:

   | **Instruction** | **Binary opcode** | **Hex opcode** | **Compiler Hex opcode** |
   | :-- | :-: | :-: | :-: |
   | `add r24, r0` | `0000_1101_1000_0000` | `0x0D80` | `0x0D80` |
   | `com r26` | `1001_0101_1010_0000` | `0x95A0` | `0x95A0` |
   | `eor r26, r27` | `0010_0111_1010_1011` | `0x27AB` | `0x27AB` |
   | `mul r22, r20` | `1001_1111_0110_0100` | `0x9F64` | `0x9F64` |
   | `ret` | `1001_0101_0000_1000` | `0x9508` | `0x9508` |

### 4-bit LFSR

2. Complete table with 4-bit LFSR values for different Tap positions:

   | **Tap position** | **Generated values** | **Length** |
   | :-: | :-- | :-: |
   | 4, 3 | `1100_110` | 7 |
   | 4, 2 | `1100_11` | 6 |
   | 4, 1 | `1100_1` | 5 |

### Variable number of short pulses

3. Draw a flowchart of function `void burst_c(uint8_t number)` which generates a variable number of short pulses at output pin. Let the pulse width be the shortest one. The image can be drawn on a computer or by hand. Use clear descriptions of the individual steps of the algorithms.

https://photos.app.goo.gl/dbvzwFU5CdaKkUHC6
