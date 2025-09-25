# Simple Pseudo-Random Number Generator
This program emulates a Linear Congruential Generator (LCG) and generates the nexr pseudo-random number based on the formula \\(x_{n+1} = (a \cdot x_n + c) \mod m\\) with previous parameters: <br>
\\(x_n\\): current random number <br>
\\(a\\): multiplier <br>
\\(c\\): increment <br>
\\(m\\): modulus ( here: \\(m= 32\\))
```asm  
# Input
li t0, 1234

# Initialize parameters
li t1, 166452     # Multiplier
li t2, 12454813   # Increment

mul t0, t0, t1    # a*x
add t0, t0, t2    # +c

# no rem needed since 32-bit overflow is mod 2^32

```