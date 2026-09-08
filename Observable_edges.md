###### 1.Module nestings are illegal instead instances(copies) are allowed

eg :Not allowed

 ```verilog
module xxx();
module yyy();

--------------

endmodule
endmodule
``` 



Modules communicate through ports



###### 2\. Default values



*  	reg --> x (unknown    empty storage box )
*  	wire --> z (high impedance    unconnected net)





###### 3.The difference between the operators



* == and ===
* != and !==



Left --> Logical equivalence check

Right--> case equivalence check ( sees for exact match of each bits---> answers in 0/1 only)





###### 4.Non  synthesizable Verilog constructs (few to be remembered)



*  	initial
*  	UDPs
*  	Fork and join



[*Refer here*](https://asic-soc.blogspot.com/2013/06/synthesizable-and-non-synthesizable.html)



###### 5.Operator that maps to specific hardware



*  	Conditional operator-->MUX
*  	always @( posedge or negedge )--> a storage element(reg)



###### 6\. Generic rule



* Blocking assignments (=) for combo logic
* Non  blocking assignments (<=) for sequential logic



###### 7.Challenge 1 : Without using the "always" keyword illustrate its behaviour using "initial" construct



|always @()<br />   begin<br />        ---------        <br />   end|initial<br />    forever <br />       begin<br />          --------           <br />       end<br />|
|-|-|



Note :  always is synthesizable but forever is not

 	always is event  driven and synthesizable, while forever creates infinite loops for simulation purposes.

 	forever is not synthesizable; use event  driven constructs for hardware implementation.



###### 8.Chanllenge 2 : Having a full adder module constructed



To have a 4  bit FA: instantiate 4 copies

To have a 8  bit FA: instantiate 8 copies



what if the adder is of 32 bits / 64 bits ?



* use : generate , endgenerate construct (synthesizable)



###### 9.Leaving output port unconnected-->Not an error

######   Leaving input port unconnected--> Error ( since 'Z' induces unexpected behaviour)

###### 

###### 10.wire A ;

######    input wire A ;   statements mean the same



Eg:

 

|wire B ;<br />assign B = sel;|wire B = sel;|assign wire B = sel;|
|-|-|-|



Note : multiple assignments to a single **net** can be resolved using wand/wor else it leads to **unknown value(X)**

       multiple assignments to a **reg** eventually evaluates to **0/1 .**





###### 11\. SYNTHESIS :

 	The tool infers logic from the HDL source ,maps the inferred logic to the technology library macros and optimizes the circuit to meet constraints

###### 

###### 12\. Challenge 3: What does the following Verilog snippet maps to ?



always@(posedge clk)

begin

 	if(enb)

 	  q<= d;

end



a FF  or a Latch ? ----> A latch : what if the 'enb' holds 0 ---> infers a hidden storage(latch)





###### 13.Can You Declare and Initialize a wire in the Same Statement?



No, the statement wire d = 0; is not valid in Verilog. A wire cannot be initialized directly during its declaration.



 Explanation   :

   A wire represents a physical connection in hardware. It is driven by continuous assignments or outputs from other modules or gates.

   wire cannot hold a value by itself and therefore cannot be initialized directly.



 Correct Usage   :

To assign a constant value to a wire, use the "assign" keyword:



verilog

wire d;

assign d = 0; // Correct way to assign a constant value to a wire





Alternatively, if you need to hold a value, use the "reg "type (or logic in SystemVerilog):



verilog

reg d = 0; // Valid: 'd' is initialized to 0



 

###### 14\. Difference Between always and forever Loops





|Feature|                 always Block|forever Loop|
|-|-|-|
|Purpose<br />Control<br />Context<br />Scope|  <br />Describes a repeating hardware process   <br />  Triggered by events in a sensitivity list    <br />  Used in combinational or sequential logic  <br /> Ends when simulation ends or block is disabled    <br /> |Implements an infinite software  style loop<br />Executes continuously without a condition<br />Used for testbenches or signal generation<br />Runs infinitely unless manually terminated|

###### 

main difference between forever and always 🡪 synthesizability




######  

