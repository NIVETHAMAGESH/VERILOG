###### 1.Module nestings are illegal instead instances(copies) are allowed

eg :Not allowed

 

     module xxx();

 	module yyy();



 	-------------



 	endmodule

     endmodule



###### 2\. Default values



*  	reg - x (unknown - empty storage box )
*  	wire - z (high impedance - unconnected net)





###### 3.The difference between the operators



* == and ===
* != and !==



Left - Logical equivalence check

Right - case equivalence check ( sees for exact match of each bits - answers in 0/1 only)





###### 4.Non-synthesizable Verilog constructs (few to be remembered)



*  	initial
*  	UDPs
*  	Fork and join



[*Refer here*](https://asic-soc.blogspot.com/2013/06/synthesizable-and-non-synthesizable.html)



###### 5.Operator that maps to specific hardware



*  	Conditional operator - MUX
*  	always @( posedge or negedge ) - a storage element(reg)



###### 6\. Generic rule



* Blocking assignments (=) for combo logic
* Non-blocking assignments (<=) for sequential logic



###### 7.Challenge 1 : Without using the "always" keyword illustrate its behaviour using "initial" construct



|always @()<br />   begin<br />      -----<br />   end|initial<br />    forever <br />       begin<br />         ------<br />       end<br />|
|-|-|



Note : always is synthesizable but forever is not



###### 8.Chanllenge 2 : Having a full adder module constructed



To have a 4-bit FA: instantiate 4 copies

To have a 8-bit FA: instantiate 8 copies



what if the adder is of 32 bits / 64 bits ?



* use : generate , endgenerate construct (synthesizable)



###### 9.Leaving output port unconnected - Not an error

&nbsp; Leaving input port unconnected - Error ( since 'Z' induces unexpected behaviour)

###### 

###### 10.wire A ;

###### &nbsp;  input wire A ;   statements mean the same



Eg: 

&nbsp;		

|wire B ;<br />assign B = sel;|wire B = sel;|assign wire B = sel;|
|-|-|-|



Note : multiple assignments to a single net can be resolved using wand/wor else it leads to unknown value(X)

&nbsp;      multiple assignments to a reg eventually evaluates to 0/1 .





###### 11\. SYNTHESIS :

&nbsp;	The tool infers logic from the HDL source ,maps the inferred logic to the technology library macros and optimizes the circuit to meet constraints

###### 

###### 12\. Challenge 3: What does the following Verilog snippet maps to ?



always@(posedge clk)

begin

&nbsp;	if(enb)

&nbsp;	  q<= d;

end



a FF  or a Latch ? --> A latch : what if the 'enb' holds 0 --> infers a hidden storage(latch)





