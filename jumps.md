# Jumps

<table>
    <tr>
        <th>Instruction</th>
        <th>Syntax</th>
        <th>Result</th>
        <th>Instruction Format</th>
        <th>Description</th>
    </tr>
    <tr>
        <td>jal</td>
        <td>jal rd, imm</td>
        <td>rd = pc+4; pc += imm</td>
        <td>UJ</td>
        <td>Jump and link</td>
    </tr>
        <tr>
        <td>jalr</td>
        <td>jalr rd, rs1, imm</td>
        <td>rd = pc+4; pc = rs1 + imm</td>
        <td>UJ</td>
        <td>Jump and link register</td>
    </tr>
</table>

Jumps are unconditional branches, here the branch is always taken. Unlike conditional branches, the return address is saved in rd, before the sign-extended immediate offset is added to the pc, therefore returning to the previous part of the code is easily possible.

Instead of an immediate value, using a label is also possible, see [loops and functions](loops.md) for more information.

The standard software calling convention uses x1 as the return address register, if no other register is specified in the instruction.

#### pseudo-instructions

<table>
    <tr>
        <th>Instruction</th>
        <th>Syntax</th>
        <th>Result</th>
        <th>Description</th>
    </tr>
    <tr>
        <td>j</td>
        <td>j imm</td>
        <td>pc += imm</td>
        <td>Jump</td>
    </tr>
</table>

When using this pseudoinstruction the return address is discarded by using x0 as rd, making it a useful tool for [loops](loops.md).