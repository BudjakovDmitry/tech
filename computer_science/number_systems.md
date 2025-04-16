# Number systems

## Decimal system

This is a base 10 system.

There is ten different numbers in the decimal system: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9.

People use decimal system for everyday counting.

## Binary system

This is a base 2 system.

There is only two numbers here: 0, 1.

This system is widely spread in the modern computers.

## Octal system

This is a base 8 system.

Octal system contains: 0, 1, 2, 3, 4, 5, 6, 7.

## Hexadecimal system

Hexa means six, and decimal means ten. So hexadecimal system is a base 16 (6 + 10)
system.

Hexadecimal numbers: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, F.

```
Hexidecimal: 0  1  2  3  4  5  6  7  8  9  A   B   C   D   E   F
Decimal:     0  1  2  3  4  5  6  7  8  9  10  11  12  13  14  15
```

## Converting using successive division method

348<sub>10</sub> to binary.

| Action  | Result | Reminder | Explanation                 |
|---------|--------|----------|-----------------------------|
| 348 / 2 | 174    | 0        | Least significant bit (LSB) |
| 174 / 2 | 87     | 0        |                             |
| 87 / 2  | 43     | 1        |                             |
| 43 / 2  | 21     | 1        |                             |
| 21 / 2  | 10     | 1        |                             |
| 10 / 2  | 5      | 0        |                             |
| 5 / 2   | 2      | 1        |                             |
| 2 / 1   | 1      | 0        |                             |
| 1 / 2   | 0      | 1        | Most significant bit (MSB)  |

Answer reads from the bottom to the top (from MSB to LSB): 101011100

348<sub>10</sub> = 101011100<sub>2</sub>

---

348<sub>10</sub> to octal.

| Action  | Result | Reminder | Explanation                   |
|---------|--------|----------|-------------------------------|
| 348 / 8 | 43     | 4        | Least significant digit (LSD) | 
| 43 / 8  | 5      | 3        |                               |
| 5 / 8   | 0      | 5        | Most significant digit (MSD)  |

348<sub>10</sub> = 543<sub>8</sub>

---

348<sub>10> to hex.

| Action   | Result | Reminder | Explanation |
|----------|--------|----------|-------------|
| 348 / 16 | 21     | 12 (C)   | |
| 21 / 16  | 1      | 5        | |
| 1 / 16   | 0      | 1        | |

348<sub>10</sub> = 15C<sub>16</sub>
