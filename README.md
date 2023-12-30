### NAME: M.Lokesh
### REF.NO: 23001615
# Exp-6-Synchornous counters  up counter and down counter 
### AIM:
To implement 4 bit up and down counters and validate  functionality.
### HARDWARE REQUIRED:
PC, Cyclone II , USB flasher
### SOFTWARE REQUIRED:   
Quartus prime
### THEORY 
## UP COUNTER 
The counter is a digital sequential circuit and here it is a 4 bit counter, which simply means it can count from 0 to 15 and vice versa based upon the direction of counting (up/down). 

The counter (“count“) value will be evaluated at every positive (rising) edge of the clock (“clk“) cycle.
The Counter will be set to Zero when “reset” input is at logic high.
The counter will be loaded with “data” input when the “load” signal is at logic high. Otherwise, it will count up or down.
The counter will count up when the “up_down” signal is logic high, otherwise count down

Since we know that binary count sequences follow a pattern of octave (factor of 2) frequency division, and that J-K flip-flop multivibrators set up for the “toggle” mode are capable of performing this type of frequency division, we can envision a circuit made up of several J-K flip-flops, cascaded to produce four bits of output.
The main problem facing us is to determine how to connect these flip-flops together so that they toggle at the right times to produce the proper binary sequence.
Examine the following binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1:
Binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1.

Note that each bit in this four-bit sequence toggles when the bit before it (the bit having a lesser significance, or place-weight), toggles in a particular direction: from 1 to 0.



 
 

Starting with four J-K flip-flops connected in such a way to always be in the “toggle” mode, we need to determine how to connect the clock inputs in such a way so that each succeeding bit toggles when the bit before it transitions from 1 to 0.

The Q outputs of each flip-flop will serve as the respective binary bits of the final, four-bit count:

  
 

Four-bit “Up” Counter
![image](https://user-images.githubusercontent.com/36288975/169644758-b2f4339d-9532-40c5-af40-8f4f8c942e2c.png)



## DOWN COUNTER 

As well as counting “up” from zero and increasing or incrementing to some preset value, it is sometimes necessary to count “down” from a predetermined value to zero allowing us to produce an output that activates when the zero count or some other pre-set value is reached.

This type of counter is normally referred to as a Down Counter, (CTD). In a binary or BCD down counter, the count decreases by one for each external clock pulse from some preset value. Special dual purpose IC’s such as the TTL 74LS193 or CMOS CD4510 are 4-bit binary Up or Down counters which have an additional input pin to select either the up or down count mode.
![image](https://user-images.githubusercontent.com/36288975/169644844-1a14e123-7228-4ed8-81a9-eb937dff4ac8.png)


4-bit Count Down Counter
### Procedure

1.Create a new project in Quartus II software.

2.Name the project as uc for upcounter and dc for downcounter.

3.Create a new Verilog HDL file in the project file.

4.Name the module as dc and uc for downcounter and upcounter.

5.Within the module declare input and output variables.

6.Complete the program.

7.End the module.

### PROGRAM 
#### UP Counter:

module UP_counter(clk, A);

input clk;

output reg [2:0]A;

always @(posedge clk)

begin

A[2]=(((A[0])&(A[1]))^A[2]);
 
A[1]=(A[0])^A[1];
 
A[0]=A[0]^1;
 
end

endmodule

#### Down counter:

module Down_counter(clk,A);

input clk;

output reg [2:0]A;

always @(posedge clk)

begin

A[2]=(((~A[0])&(~A[1]))^A[2]);

A[1]=(~A[0])^A[1];

A[0]=1^A[0];

end

endmodule

### RTL LOGIC
#### UP Counter:
![UP_counter-RTL](https://github.com/anandarakshan/Exp-7-Synchornous-counters-/assets/139217934/49cf5858-4e14-4fac-8648-ff8d9e9c3225)

#### Down Counter:
![Down_counter-RTL](https://github.com/anandarakshan/Exp-7-Synchornous-counters-/assets/139217934/4e65060f-7265-40c0-8d9e-4c2caf9191cc)

### TIMING DIGRAMS
#### UP Counter:
![UP_counter-timing_diagram](https://github.com/anandarakshan/Exp-7-Synchornous-counters-/assets/139217934/9b8d609f-edbf-4764-9d3f-4d6dcb38febd)

#### Down Counter:
![Down_counter-timing Diagram](https://github.com/anandarakshan/Exp-7-Synchornous-counters-/assets/139217934/c5c50286-ff33-49e4-acf6-84447d09e688)

### TRUTH TABLE 
#### UP Counter:
![UP_counter-Truth table](https://github.com/anandarakshan/Exp-7-Synchornous-counters-/assets/139217934/1c50d6bc-b90d-4cfa-99b9-8d54411ebfa7)


#### Down Counter:
![Down_counter-Truth table](https://github.com/anandarakshan/Exp-7-Synchornous-counters-/assets/139217934/533606ac-1ac3-4e76-92ea-eb0480d78784)


### RESULTS 
Thus, the flipflops are implemented using verilog.
