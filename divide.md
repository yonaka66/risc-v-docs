# Division

<table>
    <tr>
        <th>Instruction</th>
        <th>Syntax</th>
        <th>Result</th>
        <th>Instruction Format</th>
        <th>Description</th>
    </tr>
    <tr>
    <td>div</td>
    <td>div rd, rs1, rs2</td>
    <td>rd = rs1 / rs2</td>
    <td>R</td>
    <td>Division (signed)</td>
    </tr>
    <tr>
    <td>rem</td>
    <td>rem rd, rs1, rs2</td>
    <td>rd = rs1 % rs2</td>
    <td>R</td>
    <td>Remainder (signed)</td>
    </tr>
</table>

Division is used to divide rs1 by rs2, **rounding towards zero**, if applicable. Both values are treated as signed integers.

The Remainder-Instruction provides the reaminder of the corresponding integer division.
The sign of the result is the same as the sign of the dividend.

If both quotient and remainder are needed, the recommended sequence of code is to first divide then calculate the remainder. In this case rd of the quotient cannot be the same as rs1 or rs2.

**Division by zero** as well as **overflow** will not cause any traps, instead it has to be detected based on the instructions result:

<table>
    <tr>
        <th>Condition</th>
        <th>Dividend</th>
        <th>Divisor</th>
        <th>DIVU</th>
        <th>REMU</th>
        <th>DIV</th>
        <th>REM</th>
    </tr>
    <tr>
        <td>Division by zero</td>
        <td>x</td>
        <td>0</td>
        <td>-1</td>
        <td>x</td>
        <td>-1</td>
        <td>x</td>
    </tr>
    <tr>
        <td>Overflow (signed only)</td>
        <td>-2147483648</td>
        <td>-1</td>
        <td>-</td>
        <td>-</td>
        <td>-2147483648</td>
        <td>0</td>
    </tr>
</table>

As the table depicts, division by zero can easily be checked for and an overflow only occurs if the most-negative integer is divided by -1, so it actually can already be avoided before the division takes place. Unsigned division overflow cannot occur.

#### pseudo-instructions
<table>
    <tr>
        <th>Instruction</th>
        <th>Syntax</th>
        <th>Result</th>
        <th>Description</th>
    </tr>
    <tr>
    <td>divu</td>
    <td>divu rd, rs1, rs2</td>
    <td>rd = rs1 / rs2</td>
    <td>Division (unsigned)</td>
    </tr>
    <tr>
    <td>remu</td>
    <td>remu rd, rs1, rs2</td>
    <td>rd = rs1 % rs2</td>
    <td>Remainder (unsigned)</td>
    </tr>
</table>