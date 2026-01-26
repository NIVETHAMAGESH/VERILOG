###### 1.Module nestings are illegal instead instances(copies) are allowed

eg :Not alowed

&nbsp;    

&nbsp;    module xxx();

&nbsp;	module yyy();



&nbsp;	-------------



&nbsp;	endmodule

&nbsp;    endmodule 



###### 2\. Default values



* &nbsp;	reg - x (unknown - empty storage box )
* &nbsp;	wire - z (high impedance - unconnected net)





###### 3.The difference between the operators



* == and ===
* != and !==



Left - Logical equivalence check 

Right - case equivalence check ( sees for exact match of each bits - answers in 0/1 only)





###### 4.Non-synthesizable Verilog constructs (few to be remembered)



* &nbsp;	initial
* &nbsp;	UDPs
* &nbsp;	Fork and join



[*Refer here*](https://asic-soc.blogspot.com/2013/06/synthesizable-and-non-synthesizable.html)



###### 5.Operator that maps to specific hardwares



* &nbsp;	Conditional operator - MUX
* &nbsp;	always @( posedge or negedge ) - a storage element(reg)











