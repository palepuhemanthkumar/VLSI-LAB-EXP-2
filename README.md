# EXPERIMENT-2 SIMULATION AND IMPLEMENTATION OF COMBINATIONAL LOGIC CIRCUITS
# DATE:
# AIM:
To simulate and synthesis ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using vivado.

# APPARATUS REQUIRED:
vivado 2023.2.

# PROCEDURE
STEP:1 Start the vivado software, Select and Name the New project.

STEP:2 Select the device family, device, package and speed.

STEP:3 Select new source in the New Project and select Verilog Module as the Source type.

STEP:4 Type the File Name and module name and Click Next and then finish button. Type the code and save it.

STEP:5 Select the run simulation and then run Behavioral Simulation in the Source Window and click the check syntax.

STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table.

STEP:7 compare the output with truth table.

# LOGIC DIAGRAM

# ENCODER
![image](https://github.com/Irakamchaitanya/VLSI-LAB-EXP-2/assets/161814091/d2bb078c-7ed1-4aab-b6e6-1b939e2ac2ea)


# DECODER
![image](https://github.com/Irakamchaitanya/VLSI-LAB-EXP-2/assets/161814091/60f703fd-e45e-405f-a7e3-5f41f0ffc972)


# MULTIPLEXER
![image](https://github.com/Irakamchaitanya/VLSI-LAB-EXP-2/assets/161814091/f0f67633-d533-4ce1-ae2c-33d4f85f5e30)


# DEMULTIPLEXER
![image](https://github.com/Irakamchaitanya/VLSI-LAB-EXP-2/assets/161814091/12846950-6bb9-4c2c-b72a-d260c9a20b15)

# MAGNITUDE COMPARATOR
![image](https://github.com/Irakamchaitanya/VLSI-LAB-EXP-2/assets/161814091/2d44d34e-da18-4c23-b3da-4033a8e60336)


# VERILOG CODE
# 8-3 ENCODER:
module encoder(d,a,b,c);

input [7:0]d; output a,b,c;

or (a,d[4],d[5],d[6],d[7]);

or (b,d[2],d[3],d[6],d[7]);

or (c,d[1],d[3],d[5],d[7]);

endmodule

# 3-8 DECODER:
module decoder(A,E,Y);

input [1:0]A;

input E;

output [3:0]Y;

assign Y[0]=~A[1]&~A[0]&E;

assign Y[1]=~A[1]&A[0]&E;

assign Y[2]=A[1]&~A[0]&E;

assign Y[3]=A[1]&A[0]&E;

endmodule

module decoder(A,Y);

input[2:0]A;

output[7:0]Y;

decoder_2_4 d1(A[1:0],~A[2],Y[3:0]);

decoder_2_4 d2(A[1:0],~A[2],Y[7:4]);

endmodule

# 8-1 MULTIPLEXER:
module multi(i,s,y);

input[7:0]i;

input[2:0]s;

output reg y;

always@(*)

begin

case({s[2],s[1],s[0]})

3'b000:y=i[0];

3'b001:y=i[1];

3'b010:y=i[2];

3'b011:y=i[3];

3'b100:y=i[4];

3'b101:y=i[5];

3'b110:y=i[6];

3'b111:y=i[7];

endcase

end

endmodule

# 1-8 DEMULTIPLEXER:
module demultiplexer(d1,d2,d3,d4,d5,d6,d7,d8,i,s0,s1,s2);

input i,s0,s1,s2;

output d1,d2,d3,d4,d5,d6,d7,d8;

wire w1,w2,w3;

not g1(w1,s0);

not g2(w2,s1);

not g3(w3,s2);

and g4(d1,w1,w2,w3,i);

and g5(d2,w1,w2,s2,i);

and g6(d3,w1,s1,w3,i);

and g7(d4,w1,s1,s2,i);

and g8(d5,s0,w2,w3,i);

and g9(d6,s0,w2,s2,i);

and g10(d7,s0,s1,w3,i);

and g11(d8,s0,s1,s2,i);

endmodule

# 2 BIT MAGNITUDE COMPARATOR :
module mag_com(a,b,gt,it,eq);

input [3:0]a,b;

output reg gt,it,eq;

always @(a,b)

begin

if(a>b)

begin

gt = 1'b1;

it = 1'b0;

eq = 1'b0;

end

else if(a<b)

begin

gt = 1'b0;

it = 1'b1;

eq = 1'b0;

end

else

begin

gt = 1'b0;

it = 1'b0;

eq = 1'b1;

end

end

endmodule

# OUTPUT WAVEFORM:
# ENCODER:
![image](https://github.com/Irakamchaitanya/VLSI-LAB-EXP-2/assets/161814091/54e5a725-6f25-41be-947e-1a434a4974b3)


# DECODER:
![image](https://github.com/Irakamchaitanya/VLSI-LAB-EXP-2/assets/161814091/de6f459a-1e3b-4010-a82c-291cf2cd3eaf)


# MULTIPLEXER:
![image](https://github.com/Irakamchaitanya/VLSI-LAB-EXP-2/assets/161814091/a682d4c8-a96d-43a3-a5c2-bcadaeea7f54)


# DEMULTIPLEXER:
![image](https://github.com/Irakamchaitanya/VLSI-LAB-EXP-2/assets/161814091/df7c94ab-73cf-4d32-9aed-84dfaf2ec0ce)


# 2 BIT MAGNITUDE COMPARATOR:
![image](https://github.com/Irakamchaitanya/VLSI-LAB-EXP-2/assets/161814091/cbe6fee4-1f88-4a03-993b-f4b796ce9a8e)


# RESULT
Thus the simulation and synthesis of ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, 2bit MAGNITUDE COMPARATOR using vivado is successfully completed and executed.

