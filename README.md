**1. SIMULATION AND IMPLEMENTATION OF LOGIC GATES,ADDERS AND SUBTRACTOR**

**AIM:**

To simulate and synthesis Logic Gates,Adders and Subtractor using Xilinx ISE.

**APPARATUS REQUIRED:** 

VIVADO 2023.2

**PROCEDURE:**

1. Open Vivado: Launch Xilinx Vivado software on your computer.

2. Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".

3. Project Settings: Follow the prompts to set up your project. Specify the project name, location, and select RTL project type.

4. Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on "Design Sources" in the Sources window, then selecting "Add Sources". Choose your Verilog files from the file browser.

5. Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation language (Verilog in this case) and simulation tool (Vivado Simulator).

6. Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch the Vivado Simulator and compile your design for simulation.

7. Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set automatically. This determines how long the simulation will run.

8. Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

9. View Results: After the simulation completes, you can view waveforms, debug signals, and analyze the behavior of your design.


**LOGIC GATES:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)

**VERILOG CODE:**

```
module logicgate (a,b,andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate);
input a,b;  
output andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate;
and(andgate,a,b);
or(orgate,a,b);
xor(xorgate,a,b);
nand(nandgate,a,b); 
nor(norgate,a,b);
xnor(xnorgate,a,b);
not(notgate,a);
endmodule
```

**OUTPUT:**

![image](https://github.com/DSVishal0407/VLSI-LAB-EXP-1/assets/163637297/b06bb643-591f-418c-bae7-6654d045421d)

**HALF ADDER:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/0e1ecb96-0c25-4556-832b-aeeedfdfe7b9)

**VERILOG CODE:**

```
module halfadder(a,b,sum,carry);
input a,b;
output sum,carry;
xor g1(sum,a,b);
and g2(carry,a,b);
endmodule
```

**OUTPUT:**

![WhatsApp Image 2024-03-16 at 2 29 54 PM](https://github.com/DSVishal0407/VLSI-LAB-EXP-1/assets/163637297/e5d6a25e-29d3-4a01-bfc8-cd357f8f602a)

**HALF SUBTRACTOR:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/731470b7-eb4e-49f8-8bb7-2994052a7184)

**VERILOG CODE:**

```
module halfsubtractor(a,b,diff,borrow);
input a,b;
output diff,borrow;
xor g1(diff,a,b);
and g2(borrow,~a,b);
endmodule
```

**OUTPUT:**

![WhatsApp Image 2024-03-16 at 2 30 02 PM](https://github.com/DSVishal0407/VLSI-LAB-EXP-1/assets/163637297/4076f4a5-bb76-4b15-adfa-08297419da6f)

**FULL ADDDER:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/9bb3964c-438f-469d-a3de-c1cca6f323fb)

**VERILOG CODE:**

```
module fadd(a,b,c,sum,carry);
input a,b,c;
output sum,carry;
wire w1,w2,w3;
xor g1(w1,a,b);
and g2(w2,a,b);
xor g3(sum,w1,c);
and g4(w3,w1,c);
or g5(carry,w3,w2);
endmodule
```

**OUTPUT:**

![WhatsApp Image 2024-03-16 at 2 30 02 PM (1)](https://github.com/DSVishal0407/VLSI-LAB-EXP-1/assets/163637297/28c49453-cfc3-4d91-b3b1-5b31ef431325)

**FULL SUBTRACTOR:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/d66f874b-c1f2-44b3-a035-7149b56430c1)

**VERILOG CODE:**

```
module fs(a,b,bin,d,bout);
input a,b,bin; 
output d,bout;
wire w1,w2,w3;
xor g1(w1,b,bin; 
xor g2(d,w1,a);
and g3(w2,a,~w1);
and g4(w3,~b,bin);
or g5(bout,w2,w3);
endmodule
```

**OUTPUT:**

![WhatsApp Image 2024-03-16 at 2 29 54 PM (1)](https://github.com/DSVishal0407/VLSI-LAB-EXP-1/assets/163637297/4fe3f468-d4ba-4c14-8b6c-6d1afa01294c)


**8 BIT RIPPLE CARRY ADDER**

**LOGIC DIAGRAM**

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/7385a408-40a5-4203-8050-b72818622d79)

**VERILOG CODE:**

```
module ripplemod(a, b, cin, sum, cout);
input [07:0] a;
input [07:0] b;
input cin;
output [7:0]sum;
output cout;
wire[6:0] c;
fulladd a1(a[0],b[0],cin,sum[0],c[0]);
fulladd a2(a[1],b[1],c[0],sum[1],c[1]);
fulladd a3(a[2],b[2],c[1],sum[2],c[2]);
fulladd a4(a[3],b[3],c[2],sum[3],c[3]);
fulladd a5(a[4],b[4],c[3],sum[4],c[4]);
fulladd a6(a[5],b[5],c[4],sum[5],c[5]);
fulladd a7(a[6],b[6],c[5],sum[6],c[6]);
fulladd a8(a[7],b[7],c[6],sum[7],cout);
endmodule
module fulladd(a, b, cin, sum, cout);
input a;
input b;
input cin;
output sum;
output cout;
assign sum=(a^b^cin);
assign cout=((a&b)|(b&cin)|(a&cin));
endmodule
```

**OUTPUT:**

![WhatsApp Image 2024-03-16 at 2 29 55 PM](https://github.com/DSVishal0407/VLSI-LAB-EXP-1/assets/163637297/0b646151-9904-41d3-8396-40ac70a2d750)

**RESULT:**

 Hence Logic Gates,Adders and Subtractor are simulated and synthesised using Xilinx ISE.

