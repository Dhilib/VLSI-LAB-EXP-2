# SIMULATION AND IMPLEMENTATION OF COMBINATIONAL LOGIC CIRCUITS

**AIM:**<br>

&emsp;&emsp;To simulate and implement ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using VIVADO 2023.3.<br>

**APPARATUS REQUIRED:**<br>

&emsp;&emsp;VIVADO 2023.2<br>

**PROCEDURE:**<br>

 STEP:1 Launch the Vivado 2023.2 software.<br>
 STEP:2 Click on “create project ” from the starting page of vivado.<br>
 STEP:3 Choose the design entry method:RTL(verilog/VHDL).<br>
 STEP:4 Crete design source and give name to it and click finish.<br>
 STEP:5 Write the verilog code and check the syntax.<br>
 STEP:6 Click “run simulation” in the navigator window and click “Run behavioral simulation”.<br>
 STEP:7 Verify the output in the simulation window.<br>

**ENCODER:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/3cd1f95e-7531-4cad-9154-fdd397ac439e)

**VERILOG CODE:**

```
module enc8to3(e0,e1,e2,e3,e4,e5,e6,e7,d0,d1,d2);
input e0,e1,e2,e3,e4,e5,e6,e7;
output d0,d1,d2;
or g1(d0,e1,e3,e5,e7);
or g2(d1,e2,e3,e6,e7);
or g3(d2,e4,e5,e6,e7);
endmodule
```

**OUTPUT:**

![324332570-05a0f646-cc08-46b0-b7a6-b22362007a26](https://github.com/Subash190/VLSI-LAB-EXP-2/assets/162429716/e5a489d3-6e3b-48f1-8def-23831be4150a)



**DECODER:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/45a5e6cf-bbe0-4fd5-ac84-e5ad4477483b)

**VERILOG CODE:**

```
module dec3to8(in_data,out_select);
input [7:0] in_data;
output reg [2:0] out_select;
always @* begin
  case (in_data)
    8'b00000001: out_select = 3'b000; 
    8'b00000010: out_select = 3'b001; 
    8'b00000100: out_select = 3'b010; 
    8'b00001000: out_select = 3'b011; 
    8'b00010000: out_select = 3'b100; 
    8'b00100000: out_select = 3'b101; 
    8'b01000000: out_select = 3'b110; 
    8'b10000000: out_select = 3'b111; 
    default: out_select = 3'b000; 
  endcase
end
endmodule
```

**OUTPUT:**

![324332641-c9512cb8-404a-49fb-a078-6b5cf2dd60f6](https://github.com/Subash190/VLSI-LAB-EXP-2/assets/162429716/3110fbd3-aed2-48f4-a24e-81b75d008d85)

**MULTIPLEXER:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/427f75b2-8e67-44b9-ac45-a66651787436)

**VERILOG CODE:**

```
module mux8t01(a,s,y);
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

**OUTPUT:**

![324332703-35a65651-bfaa-4acb-87c6-39e8e0ac38b0](https://github.com/Subash190/VLSI-LAB-EXP-2/assets/162429716/3af17118-e444-4ba7-83e8-1e08ec0978ce)


**DEMULTIPLEXER:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/1c45a7fc-08ac-4f76-87f2-c084e7150557)

**VERILOG CODE:**

```
module demux1t08(din,s,d);
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

**OUTPUT:**
![324332775-04f0fcd5-d9ae-4684-9556-9fd8b711cfed](https://github.com/Subash190/VLSI-LAB-EXP-2/assets/162429716/0d8323da-9378-4a3a-8b56-cd9b8f5707ab)


**MAGNITUDE COMPARATOR:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/b2fe7a05-6bf7-4dcb-8f5d-28abbf7ea8c2)

**VERILOG CODE:**

```
module magcomp(a, b, a_eq_b, a_lt_b,a_gt_b);
  input [3:0] a, b;
  output a_eq_b,a_lt_b,a_gt_b;
assign a_lt_b=(a<b);
assign a_gt_b=(a>b);
assign a_eq_b=(a==b);
endmodule
```

**OUTPUT:**
![322246484-3670a201-865c-49d0-842c-3a9c12143b07](https://github.com/Subash190/VLSI-LAB-EXP-2/assets/162429716/ae04ec2a-1af8-4de2-a844-c5ede8a6805f)

**RESULT:**<br>
&emsp;&emsp; Thus the simulation and implementation of combinational logic circuit is done and outputs are verified successfully.


