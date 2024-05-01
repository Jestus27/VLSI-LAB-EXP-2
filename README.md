 # simulation of ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR 

# AIM:
 
     To simulate ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using VIVADO 2023.1.

# APPARATUS REQUIRED:

                  VIVADO 2023.1

# PROCEDURE:

1. Open Vivado: Launch Xilinx Vivado software on your computer.

2. Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".

3. Project Settings: Follow the prompts to set up your project. Specify the project name, location, and select RTL project type.

4. Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on "Design Sources" in the Sources window, then selecting "Add Sources". Choose your Verilog files from the file browser.

5. Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation language (Verilog in this case) and simulation tool (Vivado Simulator).

6. Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch the Vivado Simulator and compile your design for simulation.

7. Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set automatically. This determines how long the simulation will run.

8. Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

9. View Results: After the simulation completes, you can view waveforms, debug signals, and analyze the behavior of your design.
**LOGIC DIAGRAM**

# ENCODER

![320398937-fa882883-2e67-479b-a819-3eac5cb5fead](https://github.com/Jestus27/VLSI-LAB-EXP-2/assets/167751233/2800c862-2254-49c4-b730-6ca3c8df6584)


# VERILOG CODE
```
module encoder_8_to_3(a0,a1,a2,d7,d6,d5,d4,d3,d2,d1,d0);
input d7,d6,d5,d4,d3,d2,d1,d0;
output a0,a1,a2;
or g1(a0,d1,d3,d5,d7);
or g2(a1,d2,d3,d6,d7);
or g3(a2,d4,d5,d6,d7);
endmodule
```
# OUTPUT WAVEFORM

![320403877-05ec9b4d-9070-4345-932f-b231d15ee1bf](https://github.com/Jestus27/VLSI-LAB-EXP-2/assets/167751233/093d7b33-591b-437a-ac30-233c13229c13)

# RTL DESIGN

<img width="764" alt="324393129-54ddc383-ee27-4cfb-b4e4-bcc3e2720b04" src="https://github.com/Jestus27/VLSI-LAB-EXP-2/assets/167751233/a9451518-1a93-4213-8629-5463eb6fc874">

# DECODER

![320398869-02726cc5-fca2-4bd1-bbcf-9b3f1eabd2e3](https://github.com/Jestus27/VLSI-LAB-EXP-2/assets/167751233/fa3da222-2ecf-46a0-9a50-99e5c8a75bf2)

# VERILOG CODE
```
module decoder(input [2:0] a,output [7:0] d );
assign d[0]=(~a[2])&(~a[1])&(~a[0]);
assign d[1]=(~a[2])&(~a[1])&(a[0]);
assign d[2]=(~a[2])&(a[1])&(~a[0]);
assign d[3]=(~a[2])&(a[1])&(a[0]);
assign d[4]=(a[2])&(~a[1])&(~a[0]);
assign d[5]=(a[2])&(~a[1])&(a[0]);
assign d[6]=(a[2])&(a[1])&(~a[0]);
assign d[7]=(a[2])&(a[1])&(a[0]);
endmodule
```
# OUTPUT WAVEFORM

![320404355-9e9cca30-a733-4aa8-a777-f0c742f2c5ba](https://github.com/Jestus27/VLSI-LAB-EXP-2/assets/167751233/2e93b773-1d07-42c6-b913-967dc0e8e424)

# RTL DESIGN

<img width="766" alt="324393344-2e4fd12c-b731-49f8-ad9d-370a70d33e8f" src="https://github.com/Jestus27/VLSI-LAB-EXP-2/assets/167751233/535c512f-cdce-49dd-89ed-8d78b04ac04c">


# MULTIPLEXER

![320399097-832ec041-3668-4bf7-a1d7-78bb0d72d36f](https://github.com/Jestus27/VLSI-LAB-EXP-2/assets/167751233/74429fb9-d2c7-46a3-bf13-0043073176e8)

# VERILOG CODE 
```
module mux(a,s,y);
input [7:0]a;
input [2:0]s;
output y;
reg y;
always@({s ,a})
   begin
      case(s)
         3'b000: y=a[0];
         3'b001: y=a[1];
         3'b010: y=a[2];
         3'b011: y=a[3];
         3'b100: y=a[4];
         3'b101: y=a[5];
         3'b110: y=a[6];
         3'b111: y=a[7];
      endcase
   end
endmodule
```
# WAVEFORM OUTPUT

![320405647-2cb4c5bb-4b2d-490a-bede-ae9dd80afa64](https://github.com/Jestus27/VLSI-LAB-EXP-2/assets/167751233/27eada58-a6d5-4c26-ba1f-9fc52152f674)

# RTL DESIGN

<img width="761" alt="324393560-d1c0f5dc-bfb6-4f7a-9eea-ad050207e06c" src="https://github.com/Jestus27/VLSI-LAB-EXP-2/assets/167751233/f1d139ab-d189-4969-9740-82a2c8241453">

# DEMULTIPLEXER

![320399139-8eed2415-e7c0-4333-9e62-196da9a19469](https://github.com/Jestus27/VLSI-LAB-EXP-2/assets/167751233/c7b7c879-da86-4f65-b99b-63b84aaee593)

# VERILOG CODE 
```
module demux(din,s,d);
input din;
input[2:0]s;
output [7:0]d;
assign d[0]=(din&~s [2]&~s[1]&~s[0]);
assign d[1]=(din&~s[2]&~s[1]&s[0]);
assign d[2]=(din&~s[2]&s[1]&~s[0]);
assign d[3]=(din&~s[2]&s[1]&s[0]);
assign d[4]=(din&s[2]&~s[1]&~s[0]);
assign d[5]=(din&s[2]&~s[1]&s[0]);
assign d[6]=(din&s[2]&s[1]&~s[0]);
assign d[7]=(din&s[2]&s[1]&s[0]);
endmodule
```

# WAVEFORM OUTPUT

![320405879-bc728cb1-db21-4278-b4eb-cabe9613a993](https://github.com/Jestus27/VLSI-LAB-EXP-2/assets/167751233/8c1ade22-30fc-4597-8b9c-fac61a6a77c4)

# RTL DESIGN

<img width="767" alt="324393740-38db4464-72f1-4155-ae71-93c6773a9a00" src="https://github.com/Jestus27/VLSI-LAB-EXP-2/assets/167751233/d528750e-746e-4db1-8090-906e14ea4757">

# MAGNITUDE COMPARATOR

![320399226-fcc8fedc-cb20-4e7c-b696-adcdb4dcba3c](https://github.com/Jestus27/VLSI-LAB-EXP-2/assets/167751233/401c5867-2c0f-4451-9bcb-1adf9cfb9763)

# VERILOG CODE
```
module comparator(a,b,eq,lt,gt);
input [3:0] a,b;
output reg eq,lt,gt;
always @(a,b)
begin
if (a==b)
begin
eq = 1'b1;
lt = 1'b0;
gt = 1'b0;
end
else if (a>b)
begin
eq = 1'b0;
lt = 1'b0;
gt = 1'b1;
end
else
begin
eq = 1'b0;
lt = 1'b1;
gt = 1'b0;
end
end
endmodule
```
# WAVEFORM OUTPUT

![320406840-cbc09a3b-15f2-4a0f-9a5d-eb11c1e57a91](https://github.com/Jestus27/VLSI-LAB-EXP-2/assets/167751233/d2adb194-5e9b-446c-9eea-7d63687e90ee)

# RTL DESIGN

<img width="761" alt="324393962-4b937b7a-c5ec-43b3-8f7a-27ca463738b3" src="https://github.com/Jestus27/VLSI-LAB-EXP-2/assets/167751233/e79737ec-7619-414a-8427-9f9570283885">

# RESULT
simulation and synthesis ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using Xilinx ISE is verified.


