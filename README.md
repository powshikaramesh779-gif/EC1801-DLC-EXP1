# EC1801-DLC-EXP1
### EXPERIMENT 1 
### MINIMIZATION AND IMPLEMENTATION OF BOOLEAN FUNCTION
## Aim
To minimize and implement a Boolean function using logic gates and verify the functionality using Synopsys VCS and DVE.
## Software Required
•	Synopsys VCS
•	Synopsys DVE
•	Linux Terminal
•	Verilog HDL
## Boolean Function
Consider the Boolean function:
F(A,B,C,D)=Σm(0,2,5,7,8,10,13,15)
The minimized Boolean expression is: F=B'D'+BD
The function is implemented using Verilog HDL.
## Files Used
File	Description
exp1_boolean_min.v	Verilog design file
exp1_boolean_min_tb.v	Verilog testbench
exp1_boolean_min.vcd	VCD waveform dump generated during simulation

## Verilog Program
module boolean_function (input A, B, C, D, output F);
assign F = (~B&~D)| (B & D);
endmodule


## TestBench Program
`timescale 1ns/1ps

module tb_boolean_function;

reg A, B, C, D;
wire F;

boolean_function uut (
    .A(A),
    .B(B),
    .C(C),
    .D(D),
    .F(F)
);

initial begin
    $monitor("A=%b B=%b C=%b D=%b | F=%b",
              A, B, C, D, F);

    {A,B,C,D} = 4'b0000;
    repeat (16) begin
        #10;
        {A,B,C,D} = {A,B,C,D} + 1'b1;
    end

    #10;
    $finish;
end

endmodule








    
## Truth Table
 
<img width="622" height="675" alt="WhatsApp Image 2026-10-21 at 13 21 50" src="https://github.com/user-attachments/assets/57f79ae5-d0dc-41bc-be8b-a7495d807cc4" />


## Simulation Procedure
STEP 1-open Terminal open a terminal in the experiment folder ,bash
STEP 2- Load Synopsys Environment source /synopsys/start.sh
STEP 3- Compile using VCS vcs exp1_boolean_min.v exp1_boolean_min_tb.v-full64
If compilation is successful, vcs generates the simulation executable: simv
STEP 4 - Run simulation /simv the terminal displays the input combination and corresponding output F ,A VCD waveform file is also generated exp 1_boolean_min vcd
STEP 5- Open DVE due -full64 other option dve -full64 & A DVE environment will open.
OUTPUT
## DVE Waveform Verification
In DVE:
1.	Open the testbench hierarchy.
2.	Locate the signals:
o	A
o	B
o	C
o	D
o	F
3.	Add the signals to the waveform window.
4.	Run/inspect the waveform.
5.	Verify that F = 1 whenever B and D are equal.
6.	Verify that F = 0 whenever B and D are different.
The waveform should agree with the truth table.
<img width="1366" height="1157" alt="WhatsApp Image 2026-10-21 at 13 24 46" src="https://github.com/user-attachments/assets/efe4fecf-dc67-4910-9a19-7d3ba8327604" />

 
### Expected Result
The Boolean function
F(A,B,C,D)=Σm(0,2,5,7,8,10,13,15), which simplifies to F=B'D'+BD.
was minimized to F=B'D'+BD.
and successfully implemented using Verilog HDL.
<img width="598" height="369" alt="WhatsApp Image 2026-10-21 at 13 20 49" src="https://github.com/user-attachments/assets/a1627d3f-06a2-48cc-85e3-2b30d2aa2974" />


Result
Thus, the Boolean function was minimized, implemented using Verilog HDL, successfully simulated using Synopsys VCS, and verified using Synopsys DVE.

