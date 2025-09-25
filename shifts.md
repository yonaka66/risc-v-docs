# Shifts
<table>
  <tr>
    <th>Instruction</th>
    <th>Syntax</th>
    <th>Result</th>
    <th>Instruction Format</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>sll</td>
    <td>sll rd, rs1, rs2</td>
    <td>rd = rs1 << rs2</td>
    <td>R</td>
    <td>Shift left logical</td>
  </tr>
  <tr>
    <td>slli</td>
    <td>slli rd, rs1, imm</td>
    <td>rd = rs << imm</td>
    <td>I</td>
    <td>Shift left logical immediate</td>
  </tr>

  <tr>
    <td>srl</td>
    <td>srl rd, rs1, rs2</td>
    <td>rd = rs1 >> rs2</td>
    <td>R</td>
    <td>Shift right logical</td>
  </tr>

  <tr>
    <td>srli</td>
    <td>srl rd, rs1, imm</td>
    <td>rd = rs1 >> imm</td>
    <td>I</td>
    <td>Shift right logical immediate</td>
  </tr>

  <tr>
    <td>sra</td>
    <td>sra rd, rs1, rs2</td>
    <td>rd = rs1 >>> rs2</td>
    <td>R</td>
    <td>Shift right arithmetic</td>
  </tr>

  <tr>
    <td>srai</td>
    <td>srai rd, rs1, imm</td>
    <td>rd = rs1 >>> imm</td>
    <td>I</td>
    <td>Shift right arithmetic immediate</td>
  </tr>
</table>

A shift operation to the left discards the MSB, moves all other bits to the left by one position and fills the LSB with zero. The amount held in the lower 5 bits of \\(rs2\\) or \\(imm\\) specify how many of these shifts are performed.

When shifting to the right there are two cases: logical and arithmetic shift. Logical shift always fills free bit positions with zeroes while arithmetic shift instead fills with the sign.

Shifts can also be used to perform specific mathematical operations. The result of a left shift by \\(n\\) bits is a **multiplication** by \\(2^n\\). In the same way a right shift can perform **division** by \\(2^n\\) if the appropriate variant is used.

#### Rotations
A variant of shifts are rotations, where instead of discarding the bits that are pushed out of the register they are instead **re-added** into the register at the other end. There is, however, no specific instruction to perform rotations, instead multiple instructions have to be used.

A more detailed explanation of shifts and rotations along with a tool to perform these can be found <a href="https://onlinetoolz.net/bitshift" target="_blank">here</a>.