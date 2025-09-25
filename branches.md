# Branches
<table>
    <tr>
        <th>Instruction</th>
        <th>Syntax</th>
        <th>Result</th>
        <th>Instruction Format</th>
        <th>Description</th>
    </tr>
    <tr>
        <td>beq</td>
        <td>beq rs1, rs2, imm</td>
        <td>if(rs1 == rs2): pc += imm</td>
        <td>SB</td>
        <td>Branch equal</td>
    </tr>
    <tr>
        <td>bne</td>
        <td>bne rs1, rs2, imm</td>
        <td>if(rs1 != rs2): pc += imm</td>
        <td>SB</td>
        <td>Branch not equal</td>
    </tr>
    <tr>
        <td>blt</td>
        <td>blt rs1, rs2, imm</td>
        <td>if(rs1 < rs2): pc += imm</td>
        <td>SB</td>
        <td>Branch less than</td>
    </tr>
    <tr>
        <td>bltu</td>
        <td>bltu rs1, rs2, imm</td>
        <td>if(rs1 < rs2): pc += imm</td>
        <td>SB</td>
        <td>Branch less than unsigned</td>
    </tr>
    <tr>
        <td>bge</td>
        <td>bge rs1, rs2, imm</td>
        <td>if(rs1 >= rs2): pc += imm</td>
        <td>SB</td>
        <td>Branch greater equal</td>
    </tr>
    <tr>
        <td>bgeu</td>
        <td>bgeu rs1, rs2, imm</td>
        <td>if(rs1 >= rs2): pc += imm</td>
        <td>SB</td>
        <td>Branch greater equal unsigned</td>
    </tr>
        <tr>
        <td>auipc</td>
        <td>auipc rd, imm</td>
        <td>rd = pc + (imm << 12)</td>
        <td>U</td>
        <td>Add upper immediate to PC</td>
    </tr>
</table>

Branch instructions are useful tools to manipulate the control flow of a program. They compare two registers and "take" the branch if the condition evaluates to true. The program then continues at the specified location in the code. The immediate offset is sign-extended.


This works by making use of the **program counter** \\((pc)\\). The pc works like an arrow, always pointing to the instruction that is to be executed. However, by increasing (or decreasing) the program counter it is possible to break out of this sequence. 
By default, the \\(pc\\) increments by 4 after each finished instruction, since all instructions are stored in a segment of 4 bytes in memory. 

In Ripes, the address of each instruction can be taken from the disassembled view, the program counter is indicated by the red rectangle, that marks the current instruction. The current program counter can also be extracted by using the instruction [`auipc rd, 0` asm].

Instead of using an immediate value, it is also possible to use **labels**, see [loops and functions](loops.md) for more information.

If a branch with a condition that always evaluates to true is desirable, **jumps** are the more appropriate tool.


#### Pseudo-instructions
<table>
    <tr>
        <th>Instruction</th>
        <th>Syntax</th>
        <th>Result</th>
        <th>Description</th>
    </tr>
    <tr>
        <td>beqz</td>
        <td>beqz rs1, imm</td>
        <td>if(rs1 ==  0): pc += imm</td>
        <td>Branch equal zero </td>
    </tr>
    <tr>
        <td>bnez</td>
        <td>bnez rs1, imm</td>
        <td>if(rs1 !=  0): pc += imm</td>
        <td>Branch not equal zero</td>
    </tr>
    <tr>
        <td>bltz</td>
        <td>bltz rs1, imm</td>
        <td>if(rs1 <  0): pc += imm</td>
        <td>Branch less than zero</td>
    </tr>
    <tr>
        <td>bgt</td>
        <td>bgt rs1, rs2, imm</td>
        <td>if(rs1 >  rs2): pc += imm</td>
        <td>Branch greater than</td>
    </tr>
    <tr>
        <td>bgtu</td>
        <td>bgtu rs1, rs2, imm</td>
        <td>if(rs1 >  rs2): pc += imm</td>
        <td>Branch greater than unsigned</td>
    </tr>
    <tr>
        <td>bgtz</td>
        <td>bgtz rs1, imm</td>
        <td>if(rs1 >  0): pc += imm</td>
        <td>Branch greater than zero</td>
    </tr>
    <tr>
        <td>ble</td>
        <td>ble rs1, rs2, imm</td>
        <td>if(rs1 <=  rs2): pc += imm</td>
        <td>Branch less or equal</td>
    </tr>
    <tr>
        <td>bleu</td>
        <td>bleu rs1, rs2, imm</td>
        <td>if(rs1 <=  rs2): pc += imm</td>
        <td>Branch less or equal unsigned</td>
    </tr>
    <tr>
        <td>blez</td>
        <td>blez rs1, imm</td>
        <td>if(rs1 <=  0): pc += imm</td>
        <td>Branch less or equal zero</td>
    </tr>
    <tr>
        <td>bgez</td>
        <td>bgez rs1, imm</td>
        <td>if(rs1 >= 0): pc += imm</td>
        <td>Branch greater equal zero</td>
    </tr>
</table>

Branch-pseudo-instructions are useful in making the code more readable, but they can easily be disassembled into the above depicted branches as well.

It is advisable to structure your programs so that the sequential code path is the most common path, less frequently taken paths being the ones out of line. Additionally it should be assumed that backward branches are likely to be taken while forward branches are not.