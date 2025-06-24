# RISC-V-RV32I-Processor

<p align="left">
  <a href="https://riscv.org/">
    <img src="https://img.shields.io/badge/ISA-RISC--V%20RV32I-green.svg" alt="RISC-V RV32I">
  </a>
  <a href="https://www.verilog.com/">
    <img src="https://img.shields.io/badge/HDL-Verilog-yellow.svg" alt="Verilog HDL">
  </a>
  <a href="https://www.veripool.org/wiki/verilator">
    <img src="https://img.shields.io/badge/Simulator-Verilator-lightgrey.svg" alt="Verilator">
  </a>
  <a href="https://www.gnu.org/software/make/">
    <img src="https://img.shields.io/badge/Build-Make-orange.svg" alt="Make Build Tool">
  </a>
  <a href="https://plotly.com/python/">
    <img src="https://img.shields.io/badge/Graphing-Plotly-blueviolet.svg" alt="Plotly for Graphs">
  </a>
  <a href="https://gtkwave.sourceforge.net/">
    <img src="https://img.shields.io/badge/Debugging-GTKWave-purple.svg" alt="GTKWave">
  </a>
</p>

This project was done as a team of 4.
We are team 2 (H.A.D.E.S), each with distinct roles for the coursework (we had different roles for lab4, single cycle, pipelining, cache, branch prediction):
  - Elson Tho: completing full RISC-V instruction set by editing the control unit, ALU & register file, instruction memory, testing & verification, MUX, pipelining, f1_lights, made the new top file for the pipeline branch
  - Ahmed Hamid: program counter, sign extension, ROM, instruction memory, control unit, data memory (assembly, module & testbench), pipelining (forwarding, flushing, stalling; hazard unit), PDF
  - Antoine Divet: top module and testbench, assembly instructions (xor, or, counter), doit script, data memory, cache (1-set and 2-set), admin work (README, team statements, logbooks), branch prediction
  - Jihwan Shin: building the modules & testbenches for the initial instruction memory V1(ROM) and sign extension (I-type) as well as the PDF, worked on the direct-mapped cache
  
There was a lot of teamwork evolved, so despite some members focused on their own role, they also helped out others. 

We used five different branches (one for lab4, one for single cycle, one for pipelining, one for cache and one for branch prediction) to explicitly show the evolution of our work.

## Team 2 Statement

| Antoine Divet (repo manager) | Elson Tho | Ahmed Hamid | Jihwan Shin |
|-|-|-|-|

## Final submission

Our team has successfully completed and verified the following for our RV32I 
  processor:

| Branch                                                         | Description  | Statement |
| -------------------------------------------------------------- |------------- |-----------|
| [lab4](https://github.com/aa6dcc/RISC-V-Team2/tree/lab4)       | Lab4         | [lab4_statement.md](https://github.com/aa6dcc/RISC-V-Team2/blob/cache-branch/docs/team_statement_sections/lab4_statement.md) | 
| [Single-cycle](https://github.com/aa6dcc/RISC-V-Team2/tree/Single-cycle) | Single-Cycle | [single_cycle_statement.md](https://github.com/aa6dcc/RISC-V-Team2/blob/cache-branch/docs/team_statement_sections/single_cycle_statement.md) |
| [Pipeline](https://github.com/aa6dcc/RISC-V-Team2/tree/pipeline) | Pipelined    | [pipeline_statement.md](https://github.com/aa6dcc/RISC-V-Team2/blob/cache-branch/docs/team_statement_sections/pipeline_statement.md) |
| [Cache-branch](https://github.com/aa6dcc/RISC-V-Team2/tree/cache-branch) | Cache      | [cache_statement.md](https://github.com/aa6dcc/RISC-V-Team2/blob/cache-branch/docs/team_statement_sections/cache_statement.md) |
| [Cache-branch](https://github.com/aa6dcc/RISC-V-Team2/tree/cache-branch) | Extra      | [extra_statement.md](https://github.com/aa6dcc/RISC-V-Team2/blob/cache-branch/docs/team_statement_sections/extra_statement.md) |

## Quick Start

Note: before running **ANY** script (including the first time script), execute this 
command.

```bash
cd tb
```

### First Time

If you are using this for the first time, you need to install dependencies.

```bash
./install.sh
```

For wsl users, some packages may need to be installed, which can be found in [Bash Script instuctions](https://github.com/aa6dcc/RISC-V-Team2/blob/main/tb/bash_script_instructions.md)

## Logs

| Member    | Personal statement | Logbook |
|-----------|--------------------|---------|
| Antoine     | [Personal statement](docs/personal_statements/antoine_statement.md) | [Logbook](docs/logbooks/antoine_log.md) |
| Elson   | [Personal statement](docs/personal_statements/elson_statement.md) | [Logbook](docs/logbooks/elson_log.md) |
| Ahmed     | [Personal statement](docs/personal_statements/ahmed_statement.md) | [Logbook](docs/logbooks/ahmed_log.md) |
| Jihwan      | [Personal statement](docs/personal_statements/jihwan_statement.md) | [Logbook](docs/logbooks/jihwan_log.md) |


## Team Workflow

### Repo management (using `git`)

- The functions of `git` were fully utilised in this project
- `Branches` were created for implementations of different features to avoid 
  conflict and pushing faulty / poorly written code to `main`
- A statement was made for the team but also after each section was successfully implemented

### Repo organisation 

- [`docs`](docs/): logbooks, statements, references
- [`images`](images/): images for [`docs`](docs/)
- [`rtl`](rtl/): RV32I processor modules
- [`tb`](tb/): Testbench and scripts

General specifications:

| Property                              | Value                 |
| ------------------------------------- |---------------------- |
| Instruction Memory Size               | 2^12 bits             |
| Instruction Width                     | 32 bits               |
| Data Memory Size                      | 2^20 bits             |
| Data Width                            | 32 bits               |
| Data Cache Size                       | 61 bits               |
| Data Cache Sets                       | 4                     |
| Data Cache Ways                       | 2                     |


### Workflow

- After `lab4`, modules / work were dynamically allocated to team members
- Team meetings, discussion and progress are logged in 
[`team_log.md`](docs/logbooks/team_log.md)
- All personal contributions and progress (such as debugging notes) are noted 
  down in personal logbooks in [`docs/logbooks`](docs/logbooks/)

### Testbench

Here are the relevant commands. More can be found in the documentation.

| Command                               | Explanation                           |
| ------------------------------------- |-------------------------------------- |
| `./doit.sh`                           | Runs the entire testbench.            |
| `./doit.sh test/top_tb_lab4.cpp`      | Runs the entire testbench for lab 4   |
| `./doit.sh test/top_tb_data_mem.cpp`  | Runs the entire testbench for single cycle|
| `./doit.sh test/top_pdf_tb.cpp`       | Runs the PDF testbench* (stdout)      |
| `./doit.sh test/top_pdf_Vbuddy.cpp`   | Runs the PDF testbench* (vBuddy)      |
| `./doit.sh test/top_f1lights_tb.cpp`  | Runs the F1 lights testbench (stdout) |
| `./doit.sh test/top_f1lights_Vbuddy.cpp`| Runs the F1 lights testbench (vBuddy) |
| `./doit.sh test/top_tb_pdf_gtk.cpp`   | Purely used for debugging using GTKwave|
| `./graphs.py`                         | Creates PDF graphs of all reference data

## Working Evidence

- If you want to check our [`testbenches`](tb/)
- Here is a proof of our PDF testbench being fully functional, as it outputs the following graphs using plotly:

![WhatsApp Image 2024-12-06 at 20 26 17_3822e0e1](https://github.com/user-attachments/assets/9058539d-87ef-4f9b-a326-ce6913300366)

- Below are links to the videos of the f1_lights script running for both the single cycle and pipelined branch:

[Single Cycle](https://github.com/aa6dcc/RISC-V-Team2/blob/cache-branch/docs/videos/single_cycle.md)

[Pipeline](https://github.com/aa6dcc/RISC-V-Team2/tree/cache-branch/docs/videos)


## Team Contribution

- Work Contribution Table
- `x` (one x) refers to **a contribution**

|              |                               | Antoine | Elson | Ahmed | Jihwan |
| ------------ | ----------------------------- | ------------------ | ---------------- | ------------------------ | ---------------- |
| Lab 4        | Program Counter               |                  |                  | x                         |                  |
|              | ALU                           |  x                 |  x                |                        |                  |
|              | Register File                 |                    | x                 |                        |                  |
|              | Instruction Memory            |                    |                  |                         |  x               |
|              | Control Unit                  |                    |                  |  x                      |                  |
|              | Sign Extend                   |                    |                  |                         |  x               |
|              | Top                           |   x                 |                |                           |                 |
|              | Testbench(Top)                |   x                 |                 |                          |                  |
|              | Testbench                     |   x                 |     x           |    x                     |   x              |
|              | Doit.sh                       |   x                |      x           |                          |                  |
| Single Cycle | Data Memory                   |   x                |    x             |    x                     |               |
|              | Program Counter               |                    |                  |   x                      |   x              |
|              | ALU                           |   x                |                  |                          |                  |
|              | Register File                 |                    |    x             |                          |                  |
|              | Instruction Memory            |                    |                  |     x                    |   x              |
|              | Control Unit                  |                    |    x             |                          |                  |
|              | Sign Extend                   |                    |                  |       x                  |   x              |
|              | Verification                  |                    |     x            |                          |   x              |
|              | Doit.sh                       |   x                |                  |                          |                  |
|              | Top                           |                    |       x          |                          |                  |
| Pipeline & Cache | Pipeline Registers        |                    |    x             |    x                     |                  |
|              | Hazard Unit                   |                    |                  |    x                     |                  |
|              | Testbenching & Integration    |                    |   x              |         x                |                  |                  
|              | One-way associative cache     |       x            |   x              |                          |   x              |
|              | Two-way associative cache     |       x            |                  |                          |                 |
| Extra        | Branch Prediction             |   x                |                  |                         |                  |
|              | Interrupts                    |                    |                  |         x               |                  |
