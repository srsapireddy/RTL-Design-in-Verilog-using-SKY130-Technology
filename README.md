# RTL-Design-in-Verilog-using-SKY130-Technology

### Project Scope </br>

SKY130 is the hardware industry's first open-source process design kit (PDK) released by SkyWater Technology Foundry in collaboration with Google giving all hardware design experts and aficionados: worldwide access to their IP functions and open-source ASICs. </br>

Beginning with an introduction to digital design using Verilog HDL, the instructors cover digital design steps, including design, functional simulation, test bench-based validation of the design functionality, and logic Synthesis with optimization. Further, we learn about efficient verilog coding styles that result in predictable logic in Silicon.</br>

### Getting Started </br>
Users interested in practicing design using open-source tools need a Linux-based OS and a host of open-source EDA tools. </br>

Basic knowledge of Verilog HDL is required to follow the content without any difficulties. </br>

## Introduction to Verilog RTL Design and Synthesis</br>
On the first day, we cover the basics of RTL Design, Testbench, Simulation, and Synthesis. Open-Source software like Verilog (simulator) and YOSYS (Synthesis) .</br>

RTL Design - It consists of an actual verilog code / a set of Verilog codes that have the functionality to meet the required design specifications of the circuit. TestBench - Testbench is a setup that applies a set of stimuli (test-case vector) to check the functional working of the design file.</br>

In the digital circuit design, register-transfer level (RTL) is a design abstraction that models a synchronous digital circuit in terms of the data flow between hardware registers, and the logical operations performed on those signals. RTL abstraction is used in HDL to create high-level circuit representations, from which lower-level representations and ultimately, actual wiring can be derived.</br>

Simulator: It is a tool that is used for checking the design. In this workshop, we are using iverilog tool. Simulation is creating models that mimic the behavior of the device you are designing (simulation models) and creating models to exercise the device (test benches). RTL Design: It consists of an actual verilog code / a set of Verilog codes that have the functionality to meet the required design specifications of the circuit.</br>

Test Bench: It is the setup to apply a stimulus(test vectors) to design to check its functionality.

We do the above processes using simulator software. The simulator is loaded with the design and its respective testbench file, after which it looks for changes in the input signals. Depending on the change, the output is evaluated. These changes in input and corresponding output values are dumped in a special format file called "value change dump" (.vcd) file. This file can be pictorially represented in waveforms using a waveform tool like gtkwave.</br>

#### How Simulation Works
![image](https://github.com/srsapireddy/RTL-Design-in-Verilog-using-SKY130-Technology/assets/32967087/0915652a-c25e-401a-93bb-961dda164f39)

The design may have 1 or more primary inputs and primary outputs, but TB doesn't have.)</br>

#### Simulation Flow

![image](https://github.com/srsapireddy/RTL-Design-in-Verilog-using-SKY130-Technology/assets/32967087/119dc8b5-1f88-43b7-9360-2670d3d398dc)

Simulator continuously checks for changes in the input. If there is an input change, the output is evaluated; else the simulator will never evaluate the output.</br>

### Part 1 - Setup the lab instance with libraries and Verilog files</br>
Firstly, we have to clone 2 separate repositories, namely vsdflow, and sky130RTLDesignAndSynthesisWorkshop, which contain the required library files and Verilog design files to perform the simulations and logic synthesis parts of the workshop. It can be done using the basic Linux command git clone ex: `git clone https://github.com/kunalg123/vsdflow.git`. We are given a default set of files and libraries shown below to work on using the practical lab instance.</br>

### Cloning the Repos
![image](https://github.com/srsapireddy/RTL-Design-in-Verilog-using-SKY130-Technology/assets/32967087/67810a07-2499-4c27-b7c5-b2468a00efae)</br>

### Verilog Files
![image](https://github.com/srsapireddy/RTL-Design-in-Verilog-using-SKY130-Technology/assets/32967087/1577ef9d-a79e-4c91-9c16-9b5b8a5deced)</br>

### Part 2 - Simulation using iverilog simulator - 2:1 multiplexer rtl design</br>
After cloning the respective repositories in our lab instance, we perform a simulation run of a 2:1 multiplexer rtl file, namely good_mux.v and its corresponding testbench file tb_good_mux.v to obtain .vcd files and analyze the waveform in gtkwave to see the change in output instances concerning change in input values.</br>

#### Verilog file of a simple 2:1 multiplexer</br>
![image](https://github.com/srsapireddy/RTL-Design-in-Verilog-using-SKY130-Technology/assets/32967087/918ec0bf-a438-4306-b387-dc3b52a305ea)

#### Verilog testbench file of the corresponding 2:1 multiplexer with stimuli
![image](https://github.com/srsapireddy/RTL-Design-in-Verilog-using-SKY130-Technology/assets/32967087/f2ff4bb6-7210-44a5-ae31-05e28f829dfd)

#### Waveform using gtkwave
![image](https://github.com/srsapireddy/RTL-Design-in-Verilog-using-SKY130-Technology/assets/32967087/4e9f03c8-352e-45be-9ef5-7e54ae7b5dc9)

![image](https://github.com/srsapireddy/RTL-Design-in-Verilog-using-SKY130-Technology/assets/32967087/234d41ea-4918-4dcd-b263-b7b66d26ed66)</br>

### Part 3 - Synthesis using YOSYS open-source tool</br>
After the simulation of the rtl design with the respective testbench, we perform a synthesis of the design using Synthesizer. A Synthesizer is a tool to convert the RTL Design into a netlist file (Standard Cell Format). Specifically, a netlist is a standard gate-level file comprising nets, sequential and combinational cells, and their connectivity of the corresponding RTL file coded using an HDL. In simple words, an rtl file is a code that describes the functionality of the design, and a netlist is a file that expresses the same code in the form of logic cells like logic gates, flipflops, multiplexers with net connections, etc.</br>

![image](https://github.com/srsapireddy/RTL-Design-in-Verilog-using-SKY130-Technology/assets/32967087/238f93a7-1b33-4637-98ba-39771c4f8c66)

![image](https://github.com/srsapireddy/RTL-Design-in-Verilog-using-SKY130-Technology/assets/32967087/2796e27c-e499-4194-bc41-e15bc68e4179)

Synthesizer is a tool for converting the RTL to Netlist, and here we are using the Yosys Synthesizer.</br>
Here, we use a synthesizer tool called YOSYS, a part of the Qflow (open-source) toolchain for complete RTL2GDS transformation. The primary input files to YOSYS include the RTL Design and .lib (library) files.</br>

#### What is a .lib file?</br>

--> .lib files are a collection of logical modules which include logic gates like AND, OR, NOT, NAND, NOR, etc. Each logic gate is stored in one or more flavors depending on the number of inputs and speed of the circuit (slow, fast & medium).</br>

#### Why do we need different flavors of the same logic gate?</br>

--> Combinational delays present in a logic path determine a logic circuit's maximum speed and performance. For Example, to get maximum performance from a circuit, we need to design the circuit with minimum clock delays.</br>

We require very fast cells to minimize the clock delays to obtain minimum clock delays.</br>

In the same way, to avoid Hold violations in a logic path, we have to use SLOW cells to synchronize the hold time for the logic path.</br>

All these different types of fast and slow cells are present in a .lib file to be used by the synthesis software tool.</br>

#### Faster Cells vs. Slower Cells</br>
A cell delay in the digital logic circuit depends on the circuit's load, Capacitance.</br>

Faster the charging/discharging of the capacitance --> Lesser the Cell Delay.</br>

To charge/discharge the capacitance faster, we use wider transistors that can source more current. This will help us reduce the cell delay, but wider transistors simultaneously consume more power and area. Similarly, narrower transistors help reduce area and power, but the circuit will have a higher cell delay. Hence, we must compromise on area and power to design a circuit with low cell delay.</br>

#### Constraints</br>
A Constraint is a guidance file given to a synthesizer to enable an optimum implementation of the logic circuit by selecting the appropriate flavor of cells (fast or slow).</br>

#### Practical Synthesis using YOSYS</br>
We synthesize the 2:1 Multiplexer RTL design using YOSYS with appropriate library files from SKY130 technology that we cloned into the directory.</br>

#### Coding scripts for Synthesis using YOSYS</br>
```
$yosys                                                                             --> invokes YOSYS 

yosys> read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib                  --> reads the corresponding library file

yosys> read_verilog good_mux.v                                                     --> reads the Verilog script

yosys> synth -top good_mux                                                         --> reads the top level module

yosys> abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib                       --> converts the logic file to netlist

yosys> show                                                                        --> Final netlist output display
```
</br>

![image](https://github.com/srsapireddy/RTL-Design-in-Verilog-using-SKY130-Technology/assets/32967087/acc38137-8bf1-4f83-a304-a89e3eaf7a0e)

![image](https://github.com/srsapireddy/RTL-Design-in-Verilog-using-SKY130-Technology/assets/32967087/3cfccf87-e09a-4e07-b7a1-c3e775e83259)

![image](https://github.com/srsapireddy/RTL-Design-in-Verilog-using-SKY130-Technology/assets/32967087/9e077014-30f1-4a09-b9db-16e208854c36)

![image](https://github.com/srsapireddy/RTL-Design-in-Verilog-using-SKY130-Technology/assets/32967087/a38d9d38-e2c5-4e59-85d3-06ddf4705788)

The final synthesized netlist shows that the 2:1 multiplexer RTL is translated to a gate-level representation using buffers and a MUX gate</br>

### Timing libs, Hierarchical vs. Flat Synthesis & Efficient FlipFlop coding styles</br>
#### Part 1 - More about the .lib file</br>
We have seen that a .lib file is a collection of different flavors of standard cells with nets. In this workshop, we use the sky130_fd_sc_hd_tt_025C_1v80.lib. Looking in-depth into the naming of this lib file, it denotes the following:</br>

fd --> Foundry</br>

sd --> Standard Cell</br>

hd --> High Density</br>

tt --> Typical Process</br>

025C --> Temperature</br>

1v80 --> Voltage</br>

Here, the tt_025C_1v80 denotes the library design's PVT (Process, Voltage & Temperature corners).</br>

Upon opening the .lib file for reference, using</br>

`vim ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`</br>

We get to see detailed parameter values of all the different flavors of standard cells (logic gates etc.). The parameters include the leakage power of each input value of the cell, the area of the cell, cell footprint, cell leakage power, driver waveform, etc. These parameters vary for each flavor of the same cell with the same functionality.</br>

For Example, A 2 input or gate has different flavors like or2_0, or2_1, or2_2, and so on. Each cell has different values of leakage power, area, etc. This is shown below:</br>

![image](https://github.com/srsapireddy/RTL-Design-in-Verilog-using-SKY130-Technology/assets/32967087/679b930a-2084-4560-a2ce-aef81f95469a)

![image](https://github.com/srsapireddy/RTL-Design-in-Verilog-using-SKY130-Technology/assets/32967087/f2b4d3c5-e1b4-421c-a809-4201621aed60)


#### 2-input OR Gate: sky130_fd_s_hd.v file
![image](https://github.com/srsapireddy/RTL-Design-in-Verilog-using-SKY130-Technology/assets/32967087/ffe89187-73b3-4485-a852-ed6c9d469fcd)

Based on the above images, it can be inferred that even though the behavioral logic of the 2-input-OR gates or2_0 and or2_4 are the same, they differ in their internal parameters like leakage power and area. The higher area of or2_4 infers that it employs wider transistors, thereby confirming that it is a `fast cell.`</br>

#### GVIM Installation: `sudo apt install vim-gtk3`</br>

### Part 2 - Hierarchical vs Flat Synthesis</br>
Let us consider an example code, `multiple_modules,` which instantiates an `AND` & `OR` gate logic in separate sub-modules: `sub_module1` & `sub_module2`. The Verilog code for the same is displayed below:</br>

![image](https://github.com/srsapireddy/RTL-Design-in-Verilog-using-SKY130-Technology/assets/32967087/e62bb5d9-8515-4e2f-aa0f-d8f2264ef063)

#### Hierarchical Synthesis</br>
When we synthesize this verilog code using `YOSYS` with the following code blocks:</br>

```
$yosys
yosys> read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib           

yosys> read_verilog multiple_modules.v                                                     

yosys> synth -top multiple_modules                                                         

yosys> abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib                    

yosys> show multiple_modules 
```

We get a netlist comprising sub_module1 & sub_module2 instead of the logic gates AND & OR-based netlist. This is because in the multiple_modules RTL design, even though it is implementing two logic gates-based circuits, the gates are instances inside two separate sub_modules that are instantiated to obtain the specific logic. This type of sub_module level synthesis is known as Hierarchical Synthesis, as the sub_modules are preserved in its hierarchy.</br>

![image](https://github.com/srsapireddy/RTL-Design-in-Verilog-using-SKY130-Technology/assets/32967087/0523471c-ca0f-435f-a40f-45a58b4cceea)

Now, we can write out the netlist of the hierarchical netlist file and look at the behavioral implementation of the same.</br>

```
write_verilog -noattr multiple_modules_hier.v
!gvim multiple_modules_hier.v
```
![image](https://github.com/srsapireddy/RTL-Design-in-Verilog-using-SKY130-Technology/assets/32967087/c8cadeda-cdd4-42bf-9b07-621e19e8e775)


It can be seen that the OR gate is implemented using 2 `INV` and 1 `NAND` gate. This is because of a technical logic known as a Stacked PMOS issue. Implementing a logic gate using the Stacked PMOS concept results in poor mobility and is always avoided. That is why the OR gate was not implemented using 2 INV and 1 NOR gate logic, as PMOS transistors are stacked in NOR gate implementation using transistors.</br>

#### Flat Synthesis</br>
We implement the Flat Synthesis technique using the flatten command to obtain a gate-based synthesized netlist file without preserving any of the sub_module hierarchy.</br>

```
yosys> flatten
```

This command will implement the synthesis procedure without preserving the sub_module hierarchy, and we obtain a netlist file of the multiple_modules RTL design implemented using the `AND` & `OR` gates</br>

The flattened netlist and verilog module of the netlist file are obtained and listed as follows:</br>
```
write_verilog -noattr multiple_modules_flat.v
!gvim multiple_modules_flat.v
```

![image](https://github.com/srsapireddy/RTL-Design-in-Verilog-using-SKY130-Technology/assets/32967087/1e19b18b-0a3e-4f85-b5b0-1a460ced5ec6)

![image](https://github.com/srsapireddy/RTL-Design-in-Verilog-using-SKY130-Technology/assets/32967087/f1556a0f-130e-498a-b469-53e2c214ae36)

#### When do we need sub_module level Synthesis?</br>
- Multiple Instances of the same module within the top-level design:</br>
When a design consists of multiple instances of the same module, we can use sub-module level synthesis and replicate the same for all the other instances of the same module and stitch it together to obtain the complete netlist file. This can be done using one module instance in the `synth -top` command.</br>

Massive Complex Design:</br>
- When there is a very large complex design consisting of several modules, running a complete synthesis will cause a tool like `YOSYS` not to provide the expected results. In such a case, the massive design can be split into small fragments into sub-modules and synthesized separately to obtain simple netlist files and stitch back to get the netlist file of the complex design. </br>

### Part 3 - Efficient Flip-flop coding styles and Optimizations</br>

#### Flip-flop overview</br>

`Flipflops` store a single bit (binary digit) of data in two states, '1' or '0'. One common application of these flip-flops is in large combinational circuits to avoid glitch errors due to propagation delays between logic gates which cause instability in output. The most common flip-flops are D-Flipflop, SR-Flipflop, JK Flipflop, and T-Flipflop. Various methods of implementing these flip-flops, like synchronous reset and synchronous set or asynchronous reset and set, etc. Listed below are different implementation/coding styles of D-flipflop with async-reset or sync-reset or async set etc.</br>

A D flip-flop is a sequential element following the input pin d at the clock's edge. D flip-flop is a fundamental component in digital logic circuits. Two types of D Flip-Flops are being implemented: Rising-Edge D Flip Flop and Falling-Edge D Flip Flop.</br>

![image](https://github.com/srsapireddy/RTL-Design-in-Verilog-using-SKY130-Technology/assets/32967087/24c05140-e7a0-415c-83c8-5373debe4a82)


Every flop element needs an initial state; else, the combinational circuit will evaluate to a garbage value. To achieve this, there are control pins in the flop: Set and Reset, which can be Synchronous or Asynchronous.</br>

![image](https://github.com/srsapireddy/RTL-Design-in-Verilog-using-SKY130-Technology/assets/32967087/21219efc-461f-45e1-9f5d-088590a3e41a)

To simulate the RTL designs, we use the `iverilog` simulator to obtain simulated .vcd files that can be viewed using `gtkwave` analyzer.</br>

#### Example Snippet:</br>
```
iverilog dff_asyncres.v tb_dff_asyncres.v
./a.out
gtkwave tb_dff_asyncres.vcd
```

#### Async Reset</br>
![image](https://github.com/srsapireddy/RTL-Design-in-Verilog-using-SKY130-Technology/assets/32967087/3cb01524-1fad-45f5-8b39-1213fe58786b)

#### Sync Reset</br>
![image](https://github.com/srsapireddy/RTL-Design-in-Verilog-using-SKY130-Technology/assets/32967087/d31721dc-dd74-4f95-8cae-3c019c050c64)

#### Async Sync Reset</br>
![image](https://github.com/srsapireddy/RTL-Design-in-Verilog-using-SKY130-Technology/assets/32967087/705a419f-efb0-4b7b-b300-386292dd0170)

Further, the design files can be synthesized in YOSYS as we have done in the previous sessions. The one new command we use here is the `dfflibmap` command used when we deploy D-FlipFlops in the RTL design. The dfflibmap command links or maps the library files containing D-Flipflops' details for synthesis. The coding snippet for synthesizing a D-Flipflop in YOSYS is given below:</br>

```
$yosys

yosys> read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib           

yosys> read_verilog dff_asyncres.v                                                     

yosys> synth -top dff_asyncres                                                         

yosys> dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib

yosys> abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib                    

yosys> show 
```

The Synthesized netlist of an Asynchronous Reset based D-Flipflop is displayed as follows.</br>

![image](https://github.com/srsapireddy/RTL-Design-in-Verilog-using-SKY130-Technology/assets/32967087/640f752a-b101-4d8c-8257-05d1c6496843)


In the above netlist, it can be seen that the asynchronous reset D-Flipflop is implemented as a D-Flipflop with Active Low reset. This Active low reset is fed with an inverter to convert it into an Active High reset as an input to reset the flop port. Similarly, synthesis can be done for other D-Flipflop models in the verilog_models folder using the above snippet, and a netlist can be obtained for your study.</br>

### Day 3 - Combinational and Sequential Optimizations</br>
#### Part 1 - Intro to Combinational Logic Optimizations</br>
##### Why do we need Combinational Logic Optimizations?</br>

- Primarily to squeeze the logic to get the most optimized design</br>
- An optimized design results in comprehensive Area and Power saving</br>

##### Types of Combinational Optimizations</br>
- Constant Propagation
  - Direct Optimization Technique
- Boolean Logic Optimization
  - K-Map based
  - Quine Mckluskey Algorithms

##### CONSTANT PROPAGATION</br>

In Constant propagation techniques, unrelated inputs or affecting the changes in the output are ignored/optimized to simplify the combination logic, thereby saving area and power usage by those input pins.</br>

##### BOOLEAN LOGIC OPTIMIZATION</br>

Boolean logic optimization is simplifying a complex boolean expression into a simplified expression by utilizing the laws of boolean logic algebra.</br>

```
assign y = a?(b?c:(c?a:0)):(!c)
```
The above equation can be very much simplified into</br>
```
y = a'c' + a(bc + b'ca) 
y = a'c' + abc + ab'c 
y = a'c' + ac(b+b') 
y = a'c' + ac
y = a xor c
```

Thus, the complex ternary operator-based equation is simplified into a simple xor gate with two inputs, a and c</br>

The following pictures depict the various versions of combination logic expressions simplified using Combinational logic optimization techniques.</br>

![image](https://github.com/srsapireddy/RTL-Design-in-Verilog-using-SKY130-Technology/assets/32967087/c22e0a20-1847-4fca-8b7a-7851d765f081)

```
$yosys

yosys> read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib           

yosys> read_verilog opt_check.v                                                     

yosys> synth -top opt_check                                                         

yosys> opt_clean -purge

yosys> abc -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib                    

yosys> show 
```

In the above snippet, we see a new code, `opt_clean -purge`, which is used to optimize the design by removing un-used net and components in the design after the design top level is synthesized using `synt -top`</br>

![image](https://github.com/srsapireddy/RTL-Design-in-Verilog-using-SKY130-Technology/assets/32967087/e9adc101-9dcd-4fac-9f51-75f9df6ca482)

![image](https://github.com/srsapireddy/RTL-Design-in-Verilog-using-SKY130-Technology/assets/32967087/5ec46baf-2ffb-44c6-845d-8833ee294d59)

![image](https://github.com/srsapireddy/RTL-Design-in-Verilog-using-SKY130-Technology/assets/32967087/299034dd-720d-44ab-9c3c-30712b75c07c)

![image](https://github.com/srsapireddy/RTL-Design-in-Verilog-using-SKY130-Technology/assets/32967087/9f23aebe-93ba-41ef-abf4-462e68a78918)

The above images depict various optimizations done on the expressions simplified by boolean logic optimization.</br>

Similarly, if we use multiple modules in a single code, we use flatten command in Flat Synthesis to optimize multiple modules' logic after they are reduced to simple modules using `flatten`.</br>

Some examples implemented are listed below:</br>

![image](https://github.com/srsapireddy/RTL-Design-in-Verilog-using-SKY130-Technology/assets/32967087/e2f5c41a-0ba8-42f1-9343-9b8e23a5ceec)

![image](https://github.com/srsapireddy/RTL-Design-in-Verilog-using-SKY130-Technology/assets/32967087/c5206325-d546-47d4-ab8a-0af513782930)

![image](https://github.com/srsapireddy/RTL-Design-in-Verilog-using-SKY130-Technology/assets/32967087/9aad53a3-67fb-4d22-9439-1e2365a89e9b)










