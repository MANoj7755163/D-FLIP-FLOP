# D-FLIP-FLOP
D FLIP FLOP USING MASTER SLAVE CONFIGURATION
The D flip flop is designed using 28nm CMOS technology by using Synopsys Custom Compiler


# Table of Content 
- ABSTRACT 
- INTRODUCTION
- TOOLS USED
- D FLIP FLOP CIRCUIT DESIGN
- DESIGNING ON SYNOPSYS TOOL
- SETUP & HOLD TIME
- PROPAGATION DELAY 
- SIMULATION RESULT
- NETLIST
- ACKNOWLEDGEMENT 
- REFERENCE 


# ABSTRACT

Flip Flops are basic building blocks of digital electronic circuits used in communications, Computers, and many circuits and have stable states that store binary data. The stored data can be changed by applying varying inputs. In this paper, the D flip flop is designed using 28nm CMOS technology by using Synopsys Custom Compiler.

# INTRODUCTION

A D (or Delay) Flip Flop shown in Figure is a digital electronic circuit used to delay the change of state of its output signal (Q) until the next rising edge of a clock timing input signal occurs. Flip Flop is a sequential circuit, which is used to store a single bit of information. Flip-Flop is an edgetriggered sequential block. The major applications of D flipflop are to introduce delay in timing circuit, as a buffer, sampling data at specific intervals.

![image](https://user-images.githubusercontent.com/100668140/156182917-820b9942-7f82-46f7-92da-b14550992017.png)


When the D input is provided to the Flip Flop, the circuit check for the clock signal is the signal of the clock is high (for level triggered d flip-flop) then with every clock pulse, the input D propagates to the output Q. For edge-triggered flipflop, the circuit check for the transition of clock pulse according to which the flip Flop propagates the input to the output; edge-triggered can be positive edge-triggered or negative triggered. Positive edge-triggered D flip-flop changes its output according to input with every transition of the clock pulse from 0 to 1. As for the negative edge-triggered D, flip-flop changes its output according to input with every transition of the clock pulse from 1 to 0.

# TOOL USED
•Synopsys Custom Compiler:  The Synopsys Custom Compiler™ design environment is a modern solution for full-custom analog, custom digital, and mixed-signal IC design. As the heart of the Synopsys Custom Design Platform, Custom Compiler provides design entry, simulation management and analysis, and custom layout editing features. This tool was used to design the circuit on a transistor level.

•Synopsys Prime wave:  Prime Wave™ Design Environment is a comprehensive and flexible environment for simulation setup and analysis of analog, RF, mixed-signal design, custom-digital and memory designs within the Synopsys Custom Design Platform. This tool helped in various types of simulations of the above designed circuit. 

•Synopsys 28nm PDK:  The Synopsys 28nm Process Design Kit(PDK) was used in creation and simulation of the above designed circuit.

# D FLIP FLOP CIRCUIT DESIGN
The most common approach for constructing an edge-triggered register is to use a master slave configuration, as shown in Figure. The register consists of cascading a negative
latch (master stage) with a positive latch (slave stage). A multiplexer-based latch is used in this particular implementation, although any latch could be used. On the low phase of the clock, the master stage is transparent, and the D input is passed to the master stage output,QM. During this period, the slave stage is in the hold mode, keeping its previous value using feedback. On the rising edge of the clock, the master slave stops sampling the input,and the slave stage starts sampling. During the high phase of the clock, the slave stage samples the output of the master stage (QM), while the master stage remains in a hold mode. Since QM is constant during the high phase of the clock, the output Q makes only one transition per cycle. The value of Q is the value of D right before the rising edge of the clock, achieving the positive edge-triggered effect. A negative edge-triggered register can be constructed using the same principle by simply switching the order of the positive and negative latch (this is, placing the positive latch first).
![image](https://user-images.githubusercontent.com/100668140/156124003-3d86ecaf-9bc4-465e-b460-9d973d785a4f.png)
                         GENERIC MASTER SLAVE CONFIGURATION
                         
A complete transistor-level implementation of a the master slave positive edge-triggered register is shown in Figure . The multiplexer is implemented using transmission
gates as discussed in the previous section. When the clock is low (CLK = 1), T1 is on and T2 is off, and the D input is sampled onto node QM. During this period, T3 is off and T4 is on and the cross-coupled inverters (I5, I6) holds the state of the slave latch. When the clockgoes high, the master stage stops sampling the input and goes into a hold mode. T1 is off and T2 is on, and the cross coupled inverters I3 and I4 holds the state of QM. Also, T3 is on and T4is off, and QM is copied to the output Q.
![image](https://user-images.githubusercontent.com/100668140/156124110-6f923d31-cd6c-40ca-bbd9-0df5ef84a4aa.png)
                               USING TRANSMISSION GATES
                               
 #  D FLIP DLOP USING MASTER SLAVE CONFIGURATION
 # Schematic
 
 ![Capture1](https://user-images.githubusercontent.com/100668140/156143662-ee39ab7f-6e2d-4994-97f5-f3b136a7085a.PNG)
 
 # Symbol
 
 ![Capture18](https://user-images.githubusercontent.com/100668140/156144413-64676cfd-89e0-4983-902c-6142d01a455e.PNG)
 
 # Testbench Symbol
 
 ![Capture17](https://user-images.githubusercontent.com/100668140/156144851-92a2dbde-98d3-421c-b40e-a7c6067c8cd9.PNG)
 ![Capture16](https://user-images.githubusercontent.com/100668140/156144897-bcfe8a87-6613-4b99-bca7-4c23c5444594.PNG)

# Primewave window

![Capture15](https://user-images.githubusercontent.com/100668140/156155378-bc530ca5-bfa3-4204-a0f4-322771da6558.PNG)


# Testbench waveform

![Capture5](https://user-images.githubusercontent.com/100668140/156152356-5ef9d2e3-385a-4ba4-b0e8-388ce97de0be.PNG)

![Capture14](https://user-images.githubusercontent.com/100668140/156156304-8fd1c603-1511-417c-b22d-dd34cccea7f8.PNG)


# SETUP AND HOLD TIME

 Setup time  

Minimum time requires for which the data should be stable before the active edge of the clock. Tcq is clock to output delay. Tdc is data to active edge difference. 


- Setup Rise time

 To obtain the set-up time of the register, we progressively skew the input with
respect to the clock edge until the circuit fails.The set-up time simulation
assuming a skew of 144 psec and 134 psec. For the 144 psec case, the correct value of input D
is sampled (in this case, the Q output remains at the value of VDD). For a skew of 134 psec, an
incorrect value propagates to the output (in this case, the Q output transitions to 0). Node QM
starts to go high while the output of I2
 (the input to transmission gate T2
) starts to fall. However, the clock is enabled before the two nodes across the transmission gate (T2
) settle to the same value and therefore, results in an incorrect value written into the master latch.The set-up
time for this register is therefore 144 psec. 

To calculate the setup rise time the output should be logic 0. So when the active edge comes the output becomes logic 1, for given high input. When we shift the data from left to right across the active edge of the clock, if data is far from the active edge Tcq(Clock to output delay) is stable. When data comes near to the active edge of the clock, the Tcq will start increasing after some time it fails. When data is far from the active edge the Tcq is said to be base delay. So when Tcq = 110% of base delay, At that time the value of Tdc is called setup rise time.

- PRIMEWAVE PARAMETERS

Here we have varried the input voltate coordinate t1 from 4.8n to 5.1n sec.

![Capture15](https://user-images.githubusercontent.com/100668140/156154118-3319c9ce-61ac-4bfa-851b-4b03f444fb18.PNG)

- WAVEFORM

![Capture9](https://user-images.githubusercontent.com/100668140/156156228-6e2838c9-fd33-4af7-9acc-96528086e630.PNG)


- TESTBENCH RESULTS

From the results we have observed the tcq is 49.5p sec.
Then for 110% of tcq is 54.45p sec. 

![Capture12](https://user-images.githubusercontent.com/100668140/156155108-127212b8-8efb-47d6-b6ca-b30197bf0a2b.PNG)

- PRIMEWAVE PARAMETERS
Here we have varried the input voltage coordinate t1 from 5.080n to 5.085n sec.

![Capture15](https://user-images.githubusercontent.com/100668140/156155634-882bf70b-a74d-4196-b04f-2bb141a4484f.PNG)

- TESTBENCH RESULTS

From the testbench result we can observe that for tcq =54.45p sec the calculated tcd= -144p sec
Calculated Set up time = -144p sec

![Capture13](https://user-images.githubusercontent.com/100668140/156155884-4a418938-8a81-47e6-8580-76a797375e94.PNG)
- Hold time 

Minimum time required for which the data should be stable after the active edge of the clock.


- Hold Rise time

In a similar fashion, the hold time can be simulated. The D input edge is once again
skewed relative to the clock signal till the circuit stop functioning. For this design, the hold
time is 0 - i.e., the inputs can be changed on the clock edge.

# Propagation Delay

Finally, for the propagation
delay, the inputs transition at least one set-up time before the rising edge of the clock and the
delay is measured from the 50% point of the CLK edge to the 50% point of the Q output.
From this simulation  t
c-q (lh) was 45.5 psec and t
c-q(hl) was 49.5 psec. 

![d2](https://user-images.githubusercontent.com/100668140/156168590-36fe23fc-9ba4-4e9f-a4b1-abe582bcf374.PNG)

![d1](https://user-images.githubusercontent.com/100668140/156168645-9e8918e6-3460-4d27-ac14-b68f2be702b6.PNG)

# POWER CALCULATION

Steps to calculate the Avg Current
Take Vdd node Current from the output option(Select from the Design). I have named it as current_ff
Open the calculator from output option and select mean filter.
Give Required values (current_ff, 200ps, 4.2n). We need to give the 3rd value as integer multiple of time period thats why i took it for 4 cycles(you can take any number of cycles)
Now netlist and run the simulation
Open viewer from the results option
We can see the Avg Current value is 91.8704 amp
POWER=VDD.Iavg=0.75*91.8704n=68.9028nW
- PRIMEWAVE PARAMETERS
The value of average current at Node vdd is calucalted for 1 GHZ clock frequency.
![Capture30](https://user-images.githubusercontent.com/100668140/156200758-8ba87151-6d85-4363-b019-543957b42b4a.PNG)

- TESTBENCH RESULTS
The value of average current is 91.8704 amp.
![Capture29](https://user-images.githubusercontent.com/100668140/156201031-6ad8f247-2842-41f3-a069-94a498cf11e6.PNG)

- TESTBENCH WAVEFORM
 ![Capture28](https://user-images.githubusercontent.com/100668140/156201221-8c1a5ee5-e808-44f6-a5c3-5c33addbac54.PNG)


# SIMULATION RESULT

- Set up time = -144p sec
- Hold time = 0 p sec
- Propagation delay,tcq(lh) =  45.5 p sec
                    tcq(hl) =  49.5 p sec 
- Iavg= 91.8704n amp
- power=68.9028n watts                    
                    
                    
# AUTHOR
MANOJ KUMAR SINGH,MEC2021027, MTech(2021-23) Microelectronics, Indian Institute of Information Technology,Allahabad

# ACKNOWLEDGEMENT 

- Kunal Ghosh, Co-founder, VSD Corp. Pvt. Ltd.
- Synopsys, India
- VLSI System Design(VSD) Corporation Private Limited India
- Indian Institute of Technology, Hyderabad 
- Cloud Based Analog IC Design Hackathon
- Sameer Durgoji, NIT Karnataka
- Chinmay panda, IIT Hyderabad
- Dr. Kavindra Kandpal ,Assistant Professor,
Department of Electronics and Communication Engineering, 
Indian Institute of Information Technology- Allahabad


# REFERENCES                    
- "Digital Integrated circuits-A design perspective " by Jan M.Rabaey,Anantha Chandrakasan,Borvoje Nkouc.
-  https://github.com/sonuagrawaljr/D_FlipFlop
-  NPTEL video lectures on "CMOS DIGITAL VLSI DESIGN " by Prof.Sudeb Dasgupta
- ”Analysis of Various Master-Slave 
Configuration based D Flip-Flops “ by Shivali, 
Shobha Sharma, Amita Dev.
- Kanchan Sharma, K.G. Sharma and Tripti 
Sharma, “Single Edge Triggered Static D Flip Flops: Performance Comparison”,Innovative 
Systems Design and Engineering, 2015.















                               
                              
