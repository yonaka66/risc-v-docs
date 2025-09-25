# Example 1: Parity-Bit Calculator
This program can be used to calculate the necessary parity bit for the input in \\(t0\\) and output it in \\(t1\\). It works, by counting the number of set bits in the input. This parity bit calculator can decide the parity bit for both even and odd parity, which mode is used is specified in \\(t1\\), where \\(1\\) enables odd parity and \\(1\\) even parity.

```asm
# Input
li t0, 1

# Initialize mode and additional register values
li t1, 1                 # Mode + Counter for set bits in t0
li t2, 31                # Counter for looping over all bits of t0

loop:
    andi t3, t0, 1       # Extract LSB from t0
    add t1, t1, t3       # Add LSB to t1 (Increase t1, if bit is 1)
    srli t0, t0, 1       # Shift t0 to the right to get new LSB
    
    beq t2, zero, end    # Loop until t2 = 0
    addi t2, t2, -1      # t2 = t2-1
    j loop               # Jump to loop
    
end:
    andi t1, t1, 1       # Pass LSB of set-bits counter as result
``` 