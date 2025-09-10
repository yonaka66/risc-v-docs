# Loads

<table>
    <tr>
        <th>Instruction</th>
        <th>Syntax</th>
        <th>Result</th>
        <th>Instruction Format</th>
        <th>Description</th>
    </tr>
    <tr>
        <td>lw</td>
        <td>lw rd, imm(rs1)</td>
        <td>rd = mem[rs1+imm]</td>
        <td>I</td>
        <td>Load word</td>
    </tr>
        <tr>
        <td>lh</td>
        <td>lh rd, imm(rs1)</td>
        <td>rd = mem[rs1+imm][0:15]</td>
        <td>I</td>
        <td>Load halfword</td>
    </tr>
    </tr>
        <tr>
        <td>lhu</td>
        <td>lhu rd, imm(rs1)</td>
        <td>rd = mem[rs1+imm][0:15]</td>
        <td>I</td>
        <td>Load halfword unsigned</td>
    </tr>
    <tr>
        <td>lb</td>
        <td>lb rd, imm(rs1)</td>
        <td>rd = mem[rs1+imm][0:7]</td>
        <td>I</td>
        <td>Load byte</td>
    </tr>
    <tr>
        <td>lbu</td>
        <td>lbu rd, imm(rs1)</td>
        <td>rd = mem[rs1+imm][0:7]</td>
        <td>I</td>
        <td>Load byte unsigned</td>
    </tr>
</table>

Loads are used to copy data from memory and write it into a register. Along with stores, these are the only instructions that can access memory. All other instructions operate on registers only.

 One can retrieve either a full 32-bit value (word), the lower 16 bits of a value (halfword) or the lowest 8 bits of a value (byte). When lh and lb are used, the retrieved value is sign extended before being put into rd, using lhu and lbu the value is zero-extended.

 The address from which the value is retrieved is calculated by adding the sign-extended 12-bit immediate offset to rs1.