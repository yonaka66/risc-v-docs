# RISC-V Registers

Our RISC-V processor has 32 registers that each have a length of 32 bits. Register values can be interpreted as binary, decimal, hexadecimal or octal values. It is important to note that this interpretation is not wired into the registers, instead it has to be reflected in our programs.

Register **x0** is **hardwired** with all bits set to 0. Note that writes to x0 will not throw an exception or error, but will also not change the content of the register.
<br>
<br>
<table style="display: flex; justify-content: center;">
  <tr>
    <th>Register</th>
    <th>Alias</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>x0</td>
    <td>zero</td>
    <td>hard-wired zero</td>
  </tr>
  <tr>
    <td>x1</td>
    <td>ra</td>
    <td>return address</td>
  </tr>
  <tr>
    <td>x2</td>
    <td>sp</td>
    <td>stack pointer</td>
  </tr>
  <tr>
    <td>x3</td>
    <td>gp</td>
    <td>global pointer</td>
  </tr>
  <tr>
    <td>x4</td>
    <td>tp</td>
    <td>thread pointer</td>
  </tr>
  <tr>
    <td>x5-7</td>
    <td>t0-2</td>
    <td>temporaries</td>
  </tr>
  <tr>
    <td>x8</td>
    <td>s0/fp</td>
    <td>saved register/frame pointer</td>
  </tr>
  <tr>
    <td>x9</td>
    <td>s1</td>
    <td>saved register</td>
  </tr>
  <tr>
    <td>x10-11</td>
    <td>a0-1</td>
    <td>Function arguments/return values</td>
  </tr>
  <tr>
    <td>x12-17</td>
    <td>a2-7</td>
    <td>function arguments</td>
  </tr>
  <tr>
    <td>x18-27</td>
    <td>s2-11</td>
    <td>saved registers</td>
  </tr>
   <tr>
    <td>x28-31</td>
    <td>t3-6</td>
    <td>temporaries</td>
  </tr>
</table>

Registers can be accessed by their name or their **alias**, therefore the following instuctions are equivalent:

```asm
li x5, 4
li t0, 4

```
