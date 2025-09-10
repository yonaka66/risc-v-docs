
# Compares 
<table>
    <tr>
        <th>Instruction</th>
        <th>Syntax</th>
        <th>Result</th>
        <th>Instruction Format</th>
        <th>Description</th>
    </tr>
    <tr>
        <td>slt</td>
        <td>slt rd, rs1, rs2</td>
        <td>rd = (rs1 < rs2)</td>
        <td>R</td>
        <td>Set less than</td>
    </tr>
    <tr>
        <td>slti</td>
        <td>slti rd, rs1, imm</td>
        <td>rd = (rs1 < imm)</td>
        <td>I</td>
        <td>Set less than Immediate</td>
    </tr>
    <tr>
        <td>sltu</td>
        <td>sltu rd, rs1, rs2</td>
        <td>rd = (rs1 < rs2)</td>
        <td>R</td>
        <td>Set less than unsigned</td>
    </tr>
    <tr>
        <td>sltiu</td>
        <td>sltiu rd, rs1, imm</td>
        <td>rd = (rs1 < imm)</td>
        <td>I</td>
        <td>Set less than Immediate Unsigned</td>
    </tr>
</table>

Set-comparisons are used to decide if the specified condition applies to rs1. If that is the case, the value 1 is placed into rd, otherwise 0. There are also different instructions for signed and unsigned register values. Comparisons are very useful when checking for **overflow** in signed and unsigned addition.

#### Pseudo-Instructions

<table>
    <tr>
        <th>Instruction</th>
        <th>Syntax</th>
        <th>Result</th>
        <th>Description</th>
    </tr>
    <tr>
        <td>seqz</td>
        <td>seqz rd, rs1</td>
        <td>rd = (rs1 == 0)</td>
        <td>Set equal zero (unsigned)</td>
    </tr>
    <tr>
        <td>snez</td>
        <td>snez rd, rs1</td>
        <td>rd = (rs1 != 0)</td>
        <td>Set not equal zero (unsigned)</td>
    </tr>
    <tr>
        <td>sltz</td>
        <td>sltz rd, rs1</td>
        <td>rd = (rs1 < 0)</td>
        <td>Set less than zero (signed)</td>
    </tr>
    <tr>
        <td>sgtz</td>
        <td>sgtz rd, rs1</td>
        <td>rd = (rs1 > 0)</td>
        <td>Set greater than zero (signed)</td>
    </tr>

</table>

Set-pseudo-instructions can be used to compare register values to 0. Note that the underlying instructions differ in regards to signed and unsigned arithmetic, see the table for what each instructions uses.