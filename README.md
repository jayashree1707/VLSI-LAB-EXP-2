## EX.NO:-2          SIMULATION AND IMPLEMENTATION OF  COMBINATIONAL LOGIC CIRCUITS

## AIM: 
To simulate and synthesis ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using Xilinx ISE.

## APPARATUS REQUIRED:
Xilinx 14.7
Spartan6 FPGA

## LOGIC DIAGRAM:

### ENCODER:-
![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/3cd1f95e-7531-4cad-9154-fdd397ac439e)

### DECODER:-
![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/45a5e6cf-bbe0-4fd5-ac84-e5ad4477483b)

### MULTIPLEXER:-
![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/427f75b2-8e67-44b9-ac45-a66651787436)

### DEMULTIPLEXER:-
![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/1c45a7fc-08ac-4f76-87f2-c084e7150557)

### MAGNITUDE COMPARATOR:-
![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/b2fe7a05-6bf7-4dcb-8f5d-28abbf7ea8c2)

## PROCEDURE:
STEP:1  Start  the Xilinx navigator, Select and Name the New project.
STEP:2  Select the device family, device, package and speed.       
STEP:3  Select new source in the New Project and select Verilog Module as the Source type.                       
STEP:4  Type the File Name and Click Next and then finish button. Type the code and save it.
STEP:5  Select the Behavioral Simulation in the Source Window and click the check syntax.                       
STEP:6  Click the simulation to simulate the program and  give the inputs and verify the outputs as per the truth table.               
STEP:7  Select the Implementation in the Sources Window and select the required file in the Processes Window.
STEP:8  Select Check Syntax from the Synthesize  XST Process. Double Click in the  FloorplanArea/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. 
STEP:9  In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu.
STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here.
STEP:11  On the board, by giving required input, the LEDs starts to glow light, indicating the output.

## VERILOG CODE:

### ENCODER:
```
module encoder8_3(a,y);
input [7:0]a;
output [7:0]y;
reg [7:0]y;
always@(*)
   begin
      case(a)
         8'b00000001: y=3'b000;
         8'b00000010: y=3'b001;
         8'b00000100: y=3'b010;
         8'b00001000: y=3'b011;
         8'b00010000: y=3'b100;
         8'b00100000: y=3'b101;
         8'b01000000: y=3'b110;
         8'b10000000: y=3'b111;
       endcase
   end     
endmodule
```
### DECODER:
```
module decoder3_8(a,y);
input [2:0]a;
output [7:0]y;
reg [7:0]y;
always@ (*)
  begin
     case(a)
        3'b000: y=8'b00000001;
        3'b001: y=8'b00000010;
        3'b010: y=8'b00000100;
        3'b011: y=8'b00001000;
        3'b100: y=8'b00010000;
        3'b101: y=8'b00100000;
        3'b110: y=8'b01000000;
        3'b111: y=8'b10000000;
      endcase
   end    
endmodule
```
### MULTIPLEXER:
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
### DEMULTIPLEXER:
```
module demux(din,s,d);
input din;
input[2:0]s;
output [7:0]d;
assign d[0]=(din&~s[2]&~s[1]&~s[0]);
assign d[1]=(din&~s[2]&~s[1]&s[0]);
assign d[2]=(din&~s[2]&s[1]&~s[0]);
assign d[3]=(din&~s[2]&s[1]&s[0]);
assign d[4]=(din&s[2]&~s[1]&~s[0]);
assign d[5]=(din&s[2]&~s[1]&s[0]);
assign d[6]=(din&s[2]&s[1]&~s[0]);
assign d[7]=(din&s[2]&s[1]&s[0]);
endmodule
```
### MAGNITUDE COMPARATOR:
```
module comparator(a,b,eq,lt,gt);
input [3:0]a,b;
output reg eq,lt,gt;
always@({a,b})
begin
 if(a==b)
 begin
eq=1'b1;
lt=1'b0;
gt=1'b0;
 end
 else if (a>b)
 begin
eq=1'b0;
lt=1'b0;
gt=1'b1;
 end
 else
 begin
eq=1'b0;
lt=1'b1;
gt=1'b0;
 end
end
endmodule
```
## OUTPUT WAVEFORM:

### ENCODER:
![WhatsApp Image 2024-04-12 at 20 34 04_aad04d0d](https://github.com/jayashree1707/VLSI-LAB-EXP-2/assets/160314881/ea4c7ee8-0f1e-42e1-b4bb-09fcc3476a88)

### DECODER:
![WhatsApp Image 2024-04-12 at 20 33 42_ed551bde](https://github.com/jayashree1707/VLSI-LAB-EXP-2/assets/160314881/03cf09e3-edc2-48ea-ac8c-2f347f0f6e7f)

### MULTIPLEXER:
![WhatsApp Image 2024-04-12 at 20 35 08_b42726e7](https://github.com/jayashree1707/VLSI-LAB-EXP-2/assets/160314881/1993f42d-7e7c-4970-b936-524958ba1888)

### DEMULTIPLEXER:
![WhatsApp Image 2024-04-12 at 20 33 25_9f2672b0](https://github.com/jayashree1707/VLSI-LAB-EXP-2/assets/160314881/621e2eed-910b-485b-8799-b3e3e20cfe0c)

### MAGNITUDE COMPARATOR:
![WhatsApp Image 2024-04-12 at 20 34 36_950d8076](https://github.com/jayashree1707/VLSI-LAB-EXP-2/assets/160314881/b2cdbeb1-b183-4dcc-9989-32d356ad7aed)

## RESULT:
Hence ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR is stimulated and synthesised using Xilinx ISE.


