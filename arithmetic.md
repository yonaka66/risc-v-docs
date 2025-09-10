# Arithmetic Operations

<table>
  <tr>
    <th>Instruction</th>
    <th>Syntax</th>
    <th>Result</th>
    <th>Instruction Format</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>add</td>
    <td>add rd, rs1, rs2</td>
    <td>rd = rs1 + rs2</td>
    <td>R</td>
    <td>Add values of registers</td>
  </tr>
  <tr>
    <td>addi</td>
    <td>addi rd, rs1, imm</td>
    <td>rd = rs1 + imm</td>
    <td>I</td>
    <td>Add immediate value to register</td>
  </tr>
  <tr>
    <td>sub</td>
    <td>sub rd, rs1, rs2</td>
    <td>rd = rs1 - rs2</td>
    <td>R</td>
    <td>Subtract rs2 from rs1</td>
  </tr>
  <tr>
    <td>lui</td>
    <td>lui rd, imm</td>
    <td>rd = imm << 12</td>
    <td>U</td>
    <td>Load immediate as upper bits (also see <a href="/#/shifts">shifts </a>)</td>
  </tr>
</table>

All these instructions can be used to perform simple arithmetic operations on the specified registers. Their immediate variants operate on sign-extended 12-bit immediate values.

When using integer arithmetic operations, note that there is no special instruction to check for **overflow**, instead you have to manually implement this check.

#### Pseudo-Instructions
<table>
  <tr>
    <th>Instruction</th>
    <th>Syntax</th>
    <th>Result</th>
    <th>Description</th>
  </tr>
    <tr>
    <td>neg</td>
    <td>neg rd, rs1</td>
    <td>rd = -rs1</td>
    <td>Negate register</td>
  </tr>
  <tr>
    <td>li</td>
    <td>li rd, imm</td>
    <td>rd = imm</td>
    <td>Put immediate value into register</td>
  </tr>
  <tr>
    <td>mv</td>
    <td>mv rd, rs1</td>
    <td>rd = rs1</td>
    <td>Move value to another register</td>
  </tr>
  <tr>
    <td>nop</td>
    <td>nop</td>
    <td>-</td>
    <td>No operation phase</td>
  </tr>

</table>

The `li` instruction can be used to set a register value of up to 32 bits in a register. Even though it is called load immediate it is not a load-instruction which becomes clear when having a look at the disassembled view:

<table>
<tr>
  <th>Code</th>
   <th>Disassembled View</th>
  
</tr>
<tr>
  <td><pre><code class="inline-code lang-asm">li t0, 0xFF45AB43</code></pre></td>
  <td><pre><code class="inline-code lang-asm">1:  lui x5, 0xff45b
2:  addi x5, x5, -1213</code></pre></td>
</tr>
</table>
     
The **NOP** instruction is disassembled into <pre><code class="inline-code lang-asm">addi x0, x0, 0</code></pre> and does not perform any architectually visible change except for increasing the program counter.

Since pseudo-instructions can be translated to more than one instruction, a distinct instruction format cannot be specified, instead it must be used according to the instruction formats of the underlying instructions. The ripes disassembled view can help with that.