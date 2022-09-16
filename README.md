# VSD Static Time Analysis - 1

# Section 1: Introduction and Agenda

## Timing Path

![image](https://user-images.githubusercontent.com/62461290/190420448-a233362a-fce2-4158-8b91-1bb541baee4d.png) <br>

<b> Start Point : </b> Eg - Flop clock pin or input ports <br>

<b> End Point : </b> Eg - Flop d pin/output ports <br>

![image](https://user-images.githubusercontent.com/62461290/190419078-56a3eb1b-3d46-45fa-a59d-a488e361d51f.png) <br>

The above circuit has 4 valid timing paths. <br>

* <I> Timing path 1 : </I> Input port to D pin of Lauch Flop. <br>
* <I> Timing path 2 : </I> Clock port of capture flop to Output port <br>
* <I> Timing path 3 : </I> Clock port of lauch flop to D pin of Capture flop <br>
* <I> Timing path 4 : </I> Input port to Output port <br>

<b> Arrival time : </b> The time required by a signal tp start at start point and reach the end point is called arrival time. It is calculated at the end point. <br>

![image](https://user-images.githubusercontent.com/62461290/190420734-d7db557b-f816-4c1c-8a20-64946c8f7b91.png) <br>

<b> Require time : </b> Expected time for signal to arrive. <br>

![image](https://user-images.githubusercontent.com/62461290/190424771-e242e99b-f2d3-4436-bf31-b4a336690237.png)<br>

<ins>Example of require time</ins> : 

![image](https://user-images.githubusercontent.com/62461290/190424600-ea0e375e-e40e-4add-bc97-1babc78517cd.png) <br>

### Slack 

<b> Slack : </b> Difference between arrival time and require time <br>

-> <I> Max Slack (Setup Timing, Setup Slack, Setup Analysis) : </I> The difference between expected maximum require time and actual arrival time. <br>

-> <I> Min Slack (Hold Timing, Hold Slack, Hold Analysis) : </I> The difference between actual arrival time and expected minimum require time. <br>


<ins> Example 1</ins> :

![image](https://user-images.githubusercontent.com/62461290/190431165-83bc4713-2b6a-4beb-a17d-6944258c8ff2.png) <br>

`Max Slack = 3ns - 3.5ns = -0.5ns`

![image](https://user-images.githubusercontent.com/62461290/190429835-58719349-dfe6-4a48-a97c-cd1403a7c864.png)<br>

`Min Slack = 3.5ns - 0.5ns = 3ns`

<ins> Example 2</ins> :

![image](https://user-images.githubusercontent.com/62461290/190434143-0b421273-c59b-4926-bf26-92e58ae02069.png) <br>

`Max Slack = 1ns - 0.2ns = 0.8ns`

![image](https://user-images.githubusercontent.com/62461290/190433799-0e17d633-518c-44a7-b92f-8fd36a6d680e.png) <br>

`Min slack = 0.2ns - 0.3ns = -0.1ns`


<b> Types of setup/hold analysis : </b>

1. <I> reg2reg : </I> Any path that starts at a register and end at a register is called reg2reg path. <br>

![image](https://user-images.githubusercontent.com/62461290/190436869-395360d3-37b5-4490-9248-dcd04471b026.png)<br>

2. <I> in2reg : </I> Any path that starts at a input port and end at a register is called in2reg path. <br>

![image](https://user-images.githubusercontent.com/62461290/190437220-79303d9c-c41b-4827-bef4-67d121b2abcf.png)<br>

3. <I> reg2out : </I> Any path that starts at a register and end at a output port is called out2reg path. <br>

![image](https://user-images.githubusercontent.com/62461290/190437614-f1ee053b-1de1-49eb-9b53-bb2f3cc50eb9.png)<br>

4. <I> in2out : </I> Any path that starts at a input port and end at a output port is called out2reg path. <br>

![image](https://user-images.githubusercontent.com/62461290/190438268-c83677a9-b361-4253-ad3e-5931937d5b50.png)<br>

5. <I> clock gating : </I> Path that starts from clock and ends at and gate output is called clock gating timing path. <br>

![image](https://user-images.githubusercontent.com/62461290/190438984-51a8ecc5-a45a-4987-8ea3-be1bcf47cd6e.png)<br>

6. <I> recovery/removal : </I> Path between clock of flipflop that is driving reset pin to the reset pin is called recovery/removal path. <br>

![image](https://user-images.githubusercontent.com/62461290/190439696-dd8d1c9a-2378-4633-8740-46456a9e12fa.png) <br>


7. <I> data-to-data : </I> The requirement of a to arrive a particular point and ctrl to arrive at a different point. <br>

![image](https://user-images.githubusercontent.com/62461290/190460805-258982bf-a65f-4618-8e0d-864ea31e4745.png)<br>

`Latch is level triggered and flop is edge triggered` <br>

8. <I> Latch timings : </I> it either gives time or borrows times in the circuit. <br>

Flipflop borrows time from latch. <br>
![image](https://user-images.githubusercontent.com/62461290/190462109-b07a16c3-417e-467d-897b-3314a3adbefb.png)

Latch give time to the flipflop <br>
![image](https://user-images.githubusercontent.com/62461290/190461805-737c19f3-34ec-4feb-a131-90b444e59f46.png)<br>

### Slew/Transition Analysis

Slew/Transition should cover between a minimum and maximum value. It mainly controls the power of the circuit.

<b> Types of slew/transition analysis : </b>

* <I> Data (max/min) : </I>

![image](https://user-images.githubusercontent.com/62461290/190467735-0c3eec71-6df3-46c5-9595-34d08bc3eda4.png) <br>

* <I> Clock (max/min) : </I>

![image](https://user-images.githubusercontent.com/62461290/190467955-2c211a54-1f08-4a78-a116-da218d337e46.png) <br>

### Load Analysis

Analyses the charge and discharge of the amount of load. <br>

* <I> FanOut (max/min) </I> <br>
* <I> Capacitance (max/min) </I> <br>

### Clock Analysis

* <I> Skew : </I> Latency difference between L1, L2, L3, L4. <br>

![image](https://user-images.githubusercontent.com/62461290/190468861-b79cae1c-5f51-4728-aa3b-ca8b91b99b0d.png) <br>

* <I> Pulse Width : </I> Analysis on the best possible fit for the pulse width. <br>

![image](https://user-images.githubusercontent.com/62461290/190469402-ff5fc3a0-d3fa-4979-976e-40db0b754897.png) <br>


# Section 2: Introduction to timing graph

`Specifications: Clock Frequency(F) = 1GHz
                Clock Period(T)=1/F=1ns`

## reg2reg setup analysis

