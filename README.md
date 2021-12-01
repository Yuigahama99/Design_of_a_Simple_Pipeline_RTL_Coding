# Design of a Simple Pipeline (RTL Coding)
## Objective
* To understand and appreciate the improved readability provided by RTL coding (Register Transfer Language style of coding) compared to structural coding at block-level design.
* To understand where to use Blocking assignments and where to use Non-Blocking assignments in RTL coding.
* To pay attention to the fact that you need to produce an intermediate variable before you attempt to consume it.
* To pay attention to the fact that combinational paths in a pipeline may go across stages. 
* To note that an intermediate signal (in the NSL combinational logic) generated in a clocked procedural block should not be accessed outside that procedural block either for viewing in waveform or for actual logic coding
***
## Introduction
This lab, Lab #7 Part #3 Subparts #3 and #4, is a continuation of the earlier Lab #7 Part #3 Subparts #1 and #2. Subparts #1 and #2 utilized the structural coding technique. Commonly structural coding is used at higher-level of design integration and not at block-level. In industry, a major design is first divided into 5 to 20 majors blocks and each block is assigned to an engineer for HDL coding. Individual blocks are usually coded in RTL. After proving the design of individual blocks, they are instantiated
in the TOP level design file in the structural coding style. You will experience this in EE560. 

There are some important issues in RTL coding which can easily be missed unless they are taught/demonstrated carefully. This lab intends to cover these issues.

In this lab the operations to be performed (the instructions to be executed) are very simple. Using a pipelined system, a series of such simple instructions are to be executed very much like in a CPU. We need to take care of data dependencies by designing appropriate forwarding unit (FU) and hazard detection and stalling unit (HDU).

The design has 5 pipeline stages: Instruction Fetch (IF), Instruction Decode (ID), Execution Stage 1 (EX1), Execution Stage 2 (EX2), and Write Back Stage (WB). In EX1 we have a subtractor to subtract a constant of 3 (given A, it produces A - 3). In EX2, we have an adder to add a constant of 4 (given A, it produces A + 4). Using these resources, we can perform a
MOV or a SUB3 or a ADD4 or even a ADD1. The ADD1 operation requires performing both operations, SUB3 and ADD4. The MOV operation requires neither operation.
![image](https://user-images.githubusercontent.com/76589915/144181712-f7372916-f320-4d7c-b018-fe60ae0152a9.png)
