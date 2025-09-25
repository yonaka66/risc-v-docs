# RISC-V Introduction

RISC-V is an open-source Instruction Set Architecture (ISA) designed to be simple and modular. Unlike proprietary ISAs such as x86 or ARM, RISC-V is available for anyone to use, implement and modify without licensing fees or restrictions.

At its core, an ISA defines the set of instructions a processor can execute, along with how it interacts with memory and performs basic operations. As the name implies, RISC-V follows the RISC design philosophy.

In RISC-V, most operations are performed using a small set of fast storage locations called registers. These hold the data the processor is currently working with, such as numbers to calculate or memory addresses to access. Instructions operate directly on these registers. Each instruction follows a specific binary layout, known as its format, which determines how the processor interprets it.

To experiment with RISC-V programs and understand how they execute, we will use Ripes, a visual simulator that shows how instructions affect registers and memory.

In this guide you can find information on [instruction formats](formats.md) and [registers]([registers.md) as well as all instructions from the base instruction set and [multiplication](multiplication.md) and [division](division.md) instructions from the M-Extension.

An **overview** of all this information is available <a  href="_media/RISC-V%20Cheat%20Sheet%20CA.pdf" target="_blank">here</a>. 
This Cheat Sheet will be provided in the exam as well.