# Loops and Functions

Both loops and functions are actions that change the control flow of a program.


This works by making use of the **program counter** \\((pc)\\). The \\(pc\\) works like an arrow, always pointing to the instruction that is to be executed. However, by increasing (or decreasing) the program counter it is possible to break out of this sequence. 
By default, the \\(pc\\) increments by 4 after each finished instruction, since all instructions are stored in a segment of 4 bytes in memory. 

#### Loops

While there are no native instructions to perform loops in RISC-V assembly they can be implemented by using jumps or branches.

To avoid mistakes when updating the program counter, **labels** can be used instead of the immediate offset:

```asm
loop:
    addi t0, t0, 1
    j loop
```
This program makes use of an (infinite) loop to increase the value in register \\(t0\\).

Since never terminating programs are undesireable, there should always be an **exit condition**:

```asm
loop: 
    addi t0, t0, 1
    bne t0, t1, loop
```

This program increases the value of register \\(t0\\) until it is equal to the value of register \\(t0\\). In this case, instead of jumping via a `j` instruction, a branch is used.

Note that unless there is a branch that is taken, the program will be executed in sequential order, meaning that as soon as the above branch evaluates to false, code that comes after the loop will be executed. This can be circumvented:

```asm
bgez t0, gez
li t1, -1
j end

gez:
    beqz t0, equal
    li t1, 1
    j end

equal:
    li t1, 0

end:
    nop

```

The program writes into register \\(t1\\) indicating if the value of register \\(t0\\) is positive (1), negative (-1) or equal to zero (0). it makes use of a section with the label "end" to prevent sequential execution after the code based on the value in \\(t0\\) is finished. Since ripes does not allow for empty labels, a [nop](arithmetic.md) is used.

#### Functions

At heart, functions are manipulations of the program counter and can be done using jumps and branches. To increase readability these pseudo-instructions can also be used:

<table>
  <tr>
    <th>Instruction</th>
    <th>Syntax</th>
    <th>Result</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>call</td>
    <td>call label</td>
    <td>ra = pc + 4; pc = &label</td>
    <td>call function</td>
  </tr>
  <tr>
    <td>ret</td>
    <td>ret</td>
    <td>pc = ra</td>
    <td>return from function call</td>
 </tr>
</table>

The instructions `call` and `ret`use \\(x1\\) \\((ra)\\) as link register, meaning that the return address is saved in it.

Since there are no parameters, needed values have to be stored in a register beforehand.

```asm
li t0, 4
call subtractOne
j end

subtractOne:
    addi t0, t0, -1
    ret

end:
    nop
```

The program calls the function "subtractOne", then returns to its sequential execution.