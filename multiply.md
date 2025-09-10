# Multiplication

<table>
    <tr>
        <th>Instruction</th>
        <th>Syntax</th>
        <th>Result</th>
        <th>Instruction Format</th>
        <th>Description</th>
    </tr>
    <tr>
        <td>mul</td>
        <td>mul rd, rs1, rs2</td>
        <td>rd = (rs1*rs2)[31:0]</td>
        <td>R</td>
        <td>Multiply lower half</td>
    </tr>
        <tr>
        <td>mulh</td>
        <td>mulh rd, rs1, rs2</td>
        <td>rd = (rs1*rs2)[63:32]</td>
        <td>R</td>
        <td>Multiply upper half (signed)</td>
    </tr>
     <tr>
        <td>mulhu</td>
        <td>mulhu rd, rs1, rs2</td>
        <td>rd = (rs1*rs2)[63:32]</td>
        <td>R</td>
        <td>Multiply upper half (unsigned)</td>
    </tr>
         <tr>
        <td>mulhsu</td>
        <td>mulhsu rd, rs1, rs2</td>
        <td>rd = (rs1*rs2)[63:32]</td>
        <td>R</td>
        <td>Multiply upper half of signed rs1 by unsigned rs2</td>
    </tr>
</table>

Multiply-Instructions are used to multiply rs1 by rs2. If one or both of the register values consist of more than 16 bits the result of their multiplication needs more than one register. Therefore, there are instructions to **multiply the upper half** as well. The result consists of the values in both rd's in order.

Depending on the operands either the signed, unsigned or rs1 signed, rs2 unsigned instruction might be needed. All upper half instructions only produce a result if they are needed.

If both the upper and lower half of the same product are required, the recommended code sequence is to first calculate the upper, then the lower half. In this case, the source registers must be specified in the same order and the first rd cannot be rs1 or rs2