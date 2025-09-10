# RISC-V Instruction Formats
Each instruction is encoded in 32 bits. However since different instructions need different types and quantities of operands there are instruction formats.

<table>
  <tr class="thin-padding">
    <th></th>
    <th>31</th>
    <th>30</th>
    <th>29</th>
    <th>28</th>
    <th>27</th>
    <th>26</th>
    <th>25</th>
    <th>24</th>
    <th>23</th>
    <th>22</th>
    <th>21</th>
    <th>20</th>
    <th>19</th>
    <th>18</th>
    <th>17</th>
    <th>16</th>
    <th>15</th>
    <th>14</th>
    <th>13</th>
    <th>12</th>
    <th>11</th>
    <th>10</th>
    <th>9</th>
    <th>8</th>
    <th>7</th>
    <th>6</th>
    <th>5</th>
    <th>4</th>
    <th>3</th>
    <th>2</th>
    <th>1</th>
    <th>0</th>
  </tr>
  <tr>
    <th><abbr title="Instructions using 3 registers">R</abbr></th>
    <td colspan="7">funct7</td>
    <td colspan="5">rs2</td>
    <td colspan="5">rs1</td>
    <td colspan="3">funct3</td>
    <td colspan="5">rd</td>
    <td colspan="7">opcode</td>
  </tr>

  <tr>
    <th><abbr title="Instructions with Immediates/Loads">I</abbr></th>
    <td colspan="12">imm[11:0]</td>
    <td colspan="5">rs1</td>
    <td colspan="3">funct3</td>
    <td colspan="5">rd</td>
    <td colspan="7">opcode</td>
  </tr>

  <tr>
    <th><abbr title="Store Instructions">S</abbr></th>
    <td colspan="7">imm[11:5]</td>
    <td colspan="5">rs2</td>
    <td colspan="5">rs1</td>
    <td colspan="3">funct3</td>
    <td colspan="5">imm[4:0]</td>
    <td colspan="7">opcode</td>
  </tr>

  <tr>
    <th><abbr title="Branch Instructions">SB</abbr></th>
    <td colspan="1">imm[12]</td>
    <td colspan="6">imm[10:5]</td>
    <td colspan="5">rs2</td>
    <td colspan="5">rs1</td>
    <td colspan="3">funct3</td>
    <td colspan="4">imm[4:1]</td>
    <td colspan="1">imm[11]</td>
    <td colspan="7">opcode</td>
  </tr>

  <tr>
    <th><abbr title="Instructions with upper immediates">U</abbr></th>
    <td colspan="20">imm[31:12]</td>
    <td colspan="5">rd</td>
    <td colspan="7">opcode</td>
  </tr>

  <tr>
    <th><abbr title="Jump Instructions">UJ</abbr></th>
    <td colspan="1">imm[20]</td>
    <td colspan="10">imm[10:1]</td>
    <td colspan="1">imm[11]</td>
    <td colspan="8">imm[19:12]</td>
    <td colspan="5">rd</td>
    <td colspan="7">opcode</td>
  </tr>

</table>

#### Instruction Terminology
- rs1: Source register 1
- rs2: Source register 2
- rd: Destination register
- imm[n:m]: Bits m to n of an immediate
- opcode: Determines the instruction
- funct3/funct7: function bit fields

RISC-V Instructions consist of registers, opcode, immediates and function bit fields. An instruction can contain up to 3 registers that are encoded in the bits specified by the instruction format that is used, e.g. [`add t0, t1, t2` asm] uses 3 registers that are then encoded in the instruction (rd=t0, rs1=t1, rs2=t2). 

The **opcode** works in a similar manner as the name of the instruction. However, for Instructions using the R, I, S or SB format it is not unique. Therefore we need the function bit fields **funct3** and **funct7**, these provide additional information on what exact operation to perform. 

Finally, **immediates** are values that are specified directly in the instruction, they therefore have to be stored in the instruction. When using an instruction format with immediates, the highest possible bit of said immediate is always in bit 31. Keep in mind that you can only encode integer equal or below that bit maximum in these instructions. If you want to work on an integer that uses more bits, you need to find a workaround.

