# Stores

<table>
    <tr>
        <th>Instruction</th>
        <th>Syntax</th>
        <th>Result</th>
        <th>Instruction Format</th>
        <th>Description</th>
    </tr>
    <tr>
        <td>sw</td>
        <td>sw rs2, imm(rs1)</td>
        <td>mem[rs1+imm] = rs2</td>
        <td>S</td>
        <td>Store word</td>
    </tr>
    <tr>
        <td>sh</td>
        <td>sh rs2, imm(rs1)</td>
        <td>mem[rs1+imm][0:15] = rs2</td>
        <td>S</td>
        <td>Store halfword</td>
    </tr>
        <tr>
        <td>sb</td>
        <td>sb rs2, imm(rs1)</td>
        <td>mem[rs1+imm][0:7] = rs2</td>
        <td>S</td>
        <td>Store byte</td>
    </tr>
</table>

Stores are used to copy data from registers and write it into memory. Along with loads, these are the only instructions that can access memory. All other instructions operate on registers only.

 One can store either a full 32 bit value (word), the lower 16 bits of a value (halfword) or the lowest 8 bits of a value (byte).

 The address at which the value is stored is calculated by adding the sign-extended 12-bit immediate offset to \\(rs1\\).