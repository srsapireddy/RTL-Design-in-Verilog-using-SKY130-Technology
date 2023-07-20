# RTL-Design-in-Verilog-using-SKY130-Technology

### Project Scope </br>

SKY130 is the hardware industry's first open-source process design kit (PDK) released by SkyWater Technology Foundry in collaboration with Google giving all hardware design experts and aficionados, a worldwide access to their IP functions and open-source ASICs. </br>

Beginning with an introduction to digital design using Verilog HDL, the instructors cover digital design steps, including design, functional simulation, test bench-based validation of the design functionality, and logic Synthesis with optimization. Further, we learn about efficient verilog coding styles that result in predictable logic in Silicon.</br>

### Getting Started </br>
Users interested in practicing design using open-source tools need a Linux-based OS and a host of open-source EDA tools. </br>

Basic knowledge of Verilog HDL is required to follow the content without any difficulties. </br>

## Introduction to Verilog RTL Design and Synthesis</br>
On the first day, we cover the basics of RTL Design, Testbench, Simulation, and Synthesis. Open-Source software like Verilog (simulator) and YOSYS (Synthesis) are provided through remote access in the portal to practice labs.</br>

RTL Design - It consists of an actual verilog code / a set of Verilog codes that have the functionality to meet the required design specifications of the circuit. TestBench - Testbench is a setup that applies a set of stimuli (test-case vector) to check the functional working of the design file.</br>

We do the above processes using simulator software. The simulator is loaded with the design and its respective testbench file, after which it looks for changes in the input signals. Depending on the change, the output is evaluated. These changes in input and corresponding output values are dumped in a special format file called "value change dump" (.vcd) file. This file can be pictorially represented in waveforms using a waveform tool like gtkwave.</br>

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
![image](https://github.com/srsapireddy/RTL-Design-in-Verilog-using-SKY130-Technology/assets/32967087/234d41ea-4918-4dcd-b263-b7b66d26ed66)


















