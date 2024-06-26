# SIMULATION AND IMPLEMENTATION OF  COMBINATIONAL LOGIC CIRCUITS

AIM: 
 To simulate and synthesis ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using Xilinx ISE.

APPARATUS REQUIRED:

                  VIVADO 2023.1
                  
PROCEDURE:

 1.Open Vivado: Launch Xilinx Vivado software on your computer.

 2.Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".
 
 3.Project Settings: Follow the prompts to set up your project. Specify the project name, location,
 and select RTL project type.
 
 4.Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on
 "Design Sources" in the Sources window, then selecting "Add Sources". Choose your Verilog files
 from the file browser.

 5.Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation
 language (Verilog in this case) and simulation tool (Vivado Simulator).

 6.Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch
 the Vivado Simulator and compile your design for simulation.

 7.Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set
 automatically. This determines how long the simulation will run.

 8.Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

 9.View Results: After the simulation completes, you can view waveforms, debug signals, and analyze
 the behavior of your design.

**LOGIC DIAGRAM**

ENCODER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/3cd1f95e-7531-4cad-9154-fdd397ac439e)


DECODER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/45a5e6cf-bbe0-4fd5-ac84-e5ad4477483b)


MULTIPLEXER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/427f75b2-8e67-44b9-ac45-a66651787436)


DEMULTIPLEXER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/1c45a7fc-08ac-4f76-87f2-c084e7150557)


MAGNITUDE COMPARATOR

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/b2fe7a05-6bf7-4dcb-8f5d-28abbf7ea8c2)


VERILOG CODE
# 3to8 Decoder
```
module decoder(
   input [2:0] a,
   output [7:0] d );
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

# Demultiplexer1to8
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

# Encoder8to3
```
module encoder_8_to_3(a0,a1,a2,d7,d6,d5,d4,d3,d2,d1,d0);
input d7,d6,d5,d4,d3,d2,d1,d0;
output a0,a1,a2;
or g1(a0,d1,d3,d5,d7);
or g2(a1,d2,d3,d6,d7);
or g3(a2,d4,d5,d6,d7);
endmodule
```
# Magnitude Comparator
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

# Multiplexer8to1
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

OUTPUT WAVEFORM
# OUTPUT WAVEFORM
# Multiplexer
![Screenshot 2024-04-08 134842](https://github.com/lakshanad1306/VLSI-LAB-EXP-2/assets/161121355/696c86c7-292d-43ed-b2b5-afebc1482c4c)


![Screenshot 2024-05-16 203517](https://github.com/lakshanad1306/VLSI-LAB-EXP-2/assets/161121355/689c8134-639a-4849-ae5c-e7b7c8bf08be)



# Magnitude Comparator
![Screenshot 2024-04-08 134925](https://github.com/lakshanad1306/VLSI-LAB-EXP-2/assets/161121355/89f75878-c4a2-44f0-a7af-6d1157d4faa8)


![Screenshot 2024-05-16 203534](https://github.com/lakshanad1306/VLSI-LAB-EXP-2/assets/161121355/f73b8eb4-ad26-4c63-8a79-8d657cd2554b)

# Demultiplier
![Screenshot 2024-04-08 134944](https://github.com/lakshanad1306/VLSI-LAB-EXP-2/assets/161121355/8693dde4-53a2-48f2-9690-f30e90e7d8fb)


![Screenshot 2024-05-16 203431](https://github.com/lakshanad1306/VLSI-LAB-EXP-2/assets/161121355/8a6582b4-3dc1-45fa-9c9d-0858191f6ccf)

# 8 to 3 Encoder
![Screenshot 2024-04-08 135006](https://github.com/lakshanad1306/VLSI-LAB-EXP-2/assets/161121355/9f691e70-312c-4673-bb62-d830c5b717bd)

<img width="571" alt="image" src="https://github.com/lakshanad1306/VLSI-LAB-EXP-2/assets/161121355/601d8071-90c2-4403-852a-ac17d6d1cddd">

# 3 to 8 Decoder
![Screenshot 2024-04-08 135025](https://github.com/lakshanad1306/VLSI-LAB-EXP-2/assets/161121355/db86bde2-719f-4b6e-9537-a032b9fd525c)


![Screenshot 2024-05-16 203404](https://github.com/lakshanad1306/VLSI-LAB-EXP-2/assets/161121355/46bf42fd-7c80-4a75-aa2e-d2b0881242fe)





RESULT

Thus the simulation and synthesis ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using Xilinx ISE is verified successfully.






