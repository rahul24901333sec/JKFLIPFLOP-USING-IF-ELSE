### NAME: RAHUL.R
### REG NO: 212224050034
### EXP NO 7: IMPLEMENTATION OF JKFLIPFLOP 

### **AIM:** 

To implement  JK flipflop using verilog and validating their functionality using their functional tables

### **SOFTWARE REQUIRED:**

Quartus prime

### **THEORY:**

### **JK Flip-Flop**

JK flip-flop is the modified version of SR flip-flop. It operates with only positive clock transitions or negative clock transitions. The circuit diagram of JK flip-flop is shown in the following figure.

![image](https://github.com/naavaneetha/JKFLIPFLOP-USING-IF-ELSE/assets/154305477/a649c30b-232b-4558-b188-fd6c09845180)


This circuit has two inputs J & K and two outputs Qtt & Qtt’. The operation of JK flip-flop is similar to SR flip-flop. Here, we considered the inputs of SR flip-flop as S = J Qtt’ and R = KQtt in order to utilize the modified SR flip-flop for 4 combinations of inputs. The following table shows the state table of JK flip-flop.

![image](https://github.com/naavaneetha/JKFLIPFLOP-USING-IF-ELSE/assets/154305477/c4360742-e8a8-4937-b089-c46c0433f9a3)

 
Here, Qtt & Qt+1t+1 are present state & next state respectively. So, JK flip-flop can be used for one of these four functions such as Hold, Reset, Set & Complement of present state based on the input conditions, when positive transition of clock signal is applied. The following table shows the characteristic table of JK flip-flop. Present Inputs Present State Next State
 
![image](https://github.com/naavaneetha/JKFLIPFLOP-USING-IF-ELSE/assets/154305477/6c275261-a6d5-4c37-a3a7-1e88ca11c4cd)

By using three variable K-Map, we can get the simplified expression for next state, Qt+1t+1. Three variable K-Map for next state, Qt+1t+1 is shown in the following figure.
 
![image](https://github.com/naavaneetha/JKFLIPFLOP-USING-IF-ELSE/assets/154305477/5174f41b-0ce0-4329-a372-6d1943ea6673)

The maximum possible groupings of adjacent ones are already shown in the figure. Therefore, the simplified expression for next state Qt+1t+1 is Q(t+1)=JQ(t)′+K′Q(t)Q(t+1)=JQ(t)′+K′Q(t)

### **PROCEDURE**
1. Go to quartus software.

2. Set new environment.

3. Type the code to implement JK flipflop using verilog and validating their functionality using their functional tables.

4. Run the program.

5. Give inputs in the waveform table .

6. Run the program.

### **PROGRAM**
// JK flip-flop, synchronous active-low reset
module JK_FF(
    input  wire j,
    input  wire k,
    input  wire clock,
    input  wire reset_n, // active-low synchronous reset (0 = reset)
    output reg  q,
    output wire qb
);

assign qb = ~q;

always @(posedge clock) begin
    if (!reset_n) begin
        // synchronous reset: put Q to 0 (and QB = 1 via assign)
        q <= 1'b0;
    end else begin
        // JK behavior
        if (j == 1'b0 && k == 1'b0) begin
            // hold: q <= q; (no change)
            q <= q;
        end else if (j != k) begin
            // set or reset depending on J (if J=1,K=0 => set; J=0,K=1 => reset)
            q <= j;
        end else /* j==1 && k==1 */ begin
            // toggle
            q <= ~q;
        end
    end
end

endmodule




### **RTL LOGIC FOR FLIPFLOPS**
<img width="1167" height="563" alt="Screenshot 2025-10-16 204549" src="https://github.com/user-attachments/assets/74731697-36e8-42fa-bffb-c94a56a85587" />

### **TIMING DIGRAMS FOR FLIP FLOPS**
<img width="1176" height="599" alt="Screenshot 2025-10-16 204615" src="https://github.com/user-attachments/assets/fe25e9e7-6536-469d-b9a3-6783bd851cd2" />
### **RESULTS**
THE OUTPUT FOR JK FLIPFLOP IS TESTED AND VERIFIED.
