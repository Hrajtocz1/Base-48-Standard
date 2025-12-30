# Base-48 Technical Specification (v1.0.0)

This document defines the official standard for **Base-48 (B48)** encoding. 

## 1. Goal
The primary goal of Base-48 is to provide a more compact alternative to Hexadecimal (Base-16) while ensuring maximum human readability by excluding visually ambiguous characters.

## 2. The Alphabet
The Base-48 alphabet consists of 48 alphanumeric characters. The character set is carefully selected to avoid confusion between similar-looking glyphs (like `0`/`O` or `I`/`l`).

**Official Character Map:**
| Index | Character | Index | Character | Index | Character | Index | Character |
|-------|-----------|-------|-----------|-------|-----------|-------|-----------|
| 0     | 0         | 12    | C         | 24    | N         | 36    | Z         |
| 1     | 1         | 13    | D         | 25    | P         | 37    | a         |
| 2     | 2         | 14    | E         | 26    | Q         | 38    | b         |
| 3     | 3         | 15    | F         | 27    | R         | 39    | c         |
| 4     | 4         | 16    | G         | 28    | S         | 40    | d         |
| 5     | 5         | 17    | H         | 29    | T         | 41    | e         |
| 6     | 6         | 18    | J         | 30    | U         | 42    | f         |
| 7     | 7         | 19    | K         | 31    | V         | 43    | g         |
| 8     | 8         | 20    | L         | 32    | W         | 44    | h         |
| 9     | 9         | 21    | M         | 33    | X         | 45    | j         |
| 10    | A         | 22    | N         | 34    | Y         | 46    | k         |
| 11    | B         | 23    | P         | 35    | Z         | 47    | r         |

*Note: Characters 'I', 'O', 'l', and 'm-q' are intentionally omitted to prevent transcription errors.*

## 3. Encoding Algorithm
To encode a decimal integer $N$ into Base-48:
1. Divide $N$ by 48.
2. The remainder determines the character from the alphabet.
3. Use the quotient for the next iteration.
4. Repeat until the quotient is 0.
5. The final string is the sequence of characters in reverse order of generation.

## 4. Implementation Requirements
- **BigInt Support:** Implementations MUST support arbitrary-precision integers (BigInt) to handle large memory addresses accurately.
- **Prefix (Optional):** When used in technical documentation, it is recommended to prefix addresses with `B48:` (e.g., `B48:1ZcU5HdG`).
- **Case Sensitivity:** Base-48 is **case-sensitive**. `a` (index 37) is different from `A` (index 10).

## 5. Efficiency Reference
Base-48 is approximately **29.2% more space-efficient** than Hexadecimal. 
A 64-bit integer requires:
- **Decimal:** up to 20 chars
- **Hex:** 16 chars
- **Base-48:** ~12 chars
