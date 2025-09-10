# Logical Operations
<table>
  <tr>
    <th>Instruction</th>
    <th>Syntax</th>
    <th>Result</th>
    <th>Instruction Format</th>
    <th>Description</th>
  </tr>

  <tr>
    <td>and</td>
    <td>and rd, rs1, rs2</td>
    <td>rd = rs1 & rs2</td>
    <td>R</td>
    <td>Bitwise and</td>
  </tr>

  <tr>
    <td>andi</td>
    <td>andi rd, rs1, imm</td>
    <td>rd = rs1 & imm</td>
    <td>I</td>
    <td>Bitwise and with immediate value</td>
  </tr>

  <tr>
    <td>or</td>
    <td>or rd, rs1, rs2</td>
    <td>rd = rs1 | rs2</td>
    <td>R</td>
    <td>Bitwise or</td>
  </tr>

  <tr>
    <td>ori</td>
    <td>ori rd, rs1, imm</td>
    <td>rd = rs1 | imm</td>
    <td>I</td>
    <td>Bitwise or with immediate value</td>
  </tr>

  <tr>
    <td>xor</td>
    <td>xor rd, rs1, rs2</td>
    <td>rd = rs1 ^ rs2</td>
    <td>R</td>
    <td>Bitwise xor</td>
  </tr>

  <tr>
    <td>xori</td>
    <td>xori rd, rs1, imm</td>
    <td>rd = rs1 ^ imm</td>
    <td>I</td>
    <td>Bitwise xor with immediate value</td>
  </tr>

</table>

These instructions are used to perform bitwise logical operations on the specified registers.
 Their immediate variants operate on sign-extended 12-bit immediate values.

#### Pseudo-Instructions
<table>
  <tr>
    <th>Instruction</th>
    <th>Syntax</th>
    <th>Result</th>
    <th>Description</th>
  </tr>

  <tr>
    <td>not</td>
    <td>not rd, rs1</td>
    <td>rd = ~rs1</td>
    <td>Bitwise not</td>
  </tr>
</table>

Logical operations can also be used to extract or set bits and compare values by using **bitmasks**. The term bitmask refers to a binary pattern used as a mask that only performs the desired operation on the specified bits. One example of a bitmask operation is the not instruction:

<table>
<tr>
  <th>Code</th>
   <th>Disassembled View</th>
  
</tr>
<tr>
  <td><pre><code class="inline-code lang-asm">not t0, t0</code></pre></td>
  <td><pre><code class="inline-code lang-asm">1:  xori t0, t0, -1</code></pre></td>
</tr>
</table>

Since pseudo-instructions can be translated to more than one instruction, a distinct instruction format cannot be specified, instead it must be used according to the instruction formats of the underlying instructions. The ripes disassembled view can help with that.