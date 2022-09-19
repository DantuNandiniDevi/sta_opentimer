# VSD Static Time Analysis - 1

## Section 1: Introduction and Agenda

### Timing Path

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

#### Slack 

<b> Slack : </b> Difference between arrival time and require time <br>

`Slack(S) = RAT - AAT`

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

### Types of Analysis

<p align="center">
<img src="https://user-images.githubusercontent.com/62461290/190980344-a74f3bf0-1482-4a42-9ba3-78c0564f12f2.png">
</p>

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

#### Slew/Transition Analysis

Slew/Transition should cover between a minimum and maximum value. It mainly controls the power of the circuit.

<b> Types of slew/transition analysis : </b>

* <I> Data (max/min) : </I>

![image](https://user-images.githubusercontent.com/62461290/190467735-0c3eec71-6df3-46c5-9595-34d08bc3eda4.png) <br>

* <I> Clock (max/min) : </I>

![image](https://user-images.githubusercontent.com/62461290/190467955-2c211a54-1f08-4a78-a116-da218d337e46.png) <br>

#### Load Analysis

Analyses the charge and discharge of the amount of load. <br>

* <I> FanOut (max/min) </I> <br>
* <I> Capacitance (max/min) </I> <br>

#### Clock Analysis

* <I> Skew : </I> Latency difference between L1, L2, L3, L4. <br>

![image](https://user-images.githubusercontent.com/62461290/190468861-b79cae1c-5f51-4728-aa3b-ca8b91b99b0d.png) <br>

* <I> Pulse Width : </I> Analysis on the best possible fit for the pulse width. <br>

![image](https://user-images.githubusercontent.com/62461290/190469402-ff5fc3a0-d3fa-4979-976e-40db0b754897.png) <br>


## Section 2: Introduction to timing graph

`Specifications: Clock Frequency(F) = 1GHz, Clock Period(T)=1/F=1ns`
### reg2reg setup (max) analysis - Single Clock

<b> Combination logic delay : </b>

Cell delays, wire delays, signal arrival time at inputs in real scenarios are usually in ps.<br>

![image](https://user-images.githubusercontent.com/62461290/190559641-3c6e7240-8499-4338-a27e-e4e723d25307.png) <br>

Convert the above circuit to a 'Direct Acyclic Graph (DAG)' shown below:
 
 ![image](https://user-images.githubusercontent.com/62461290/190561519-9900cb60-fac0-40dc-8793-090623fa42be.png) <br>
 
* <I> Actual Arrival Time (AAT) </I> = Time at any node where we see latest transition after first rise clock edge. (Worst if a node has multiple paths)<br>

![image](https://user-images.githubusercontent.com/62461290/190631553-4fc605de-dcea-48ff-8055-2b58623d9d98.png) <br>

* <I> Required Arrival Time (RAT) </I> = Time at any node where we expect latest transition within clock cycle. (Best if a node has multiple paths) <br>

![image](https://user-images.githubusercontent.com/62461290/190632660-ebadfa91-3233-445f-a4b6-ac2bb111d5f2.png) <br>

AAT is expected to be less than RAT at every node for meeting design expectations. <br>

* <I> Slack </I> = Required arrival time - Actual arrival time <br>

![image](https://user-images.githubusercontent.com/62461290/190657779-a50877dc-7c4c-4d95-b4a1-e913297d4707.png) <br>

* <I> Path Based Analysis : </I> It takes into account the actual path followed to reach an end point. <br>

* <I> Graph Based Analysis : </I> It takes into account the worst possible path to reach an end point. <br>

![image](https://user-images.githubusercontent.com/62461290/190659029-1d45c606-48ad-4966-bb22-42c2a9d3237e.png) <br>

![image](https://user-images.githubusercontent.com/62461290/190661563-4f051417-5179-4aa0-85b0-97c4cf5b40a2.png) <br>

Path based analysis is more realistic than graph based analysis. <br>

Pin node conventions <br>

![image](https://user-images.githubusercontent.com/62461290/190666816-3f808fdd-92d1-4b3c-b74a-98d5673bb9fb.png) <br>

![image](https://user-images.githubusercontent.com/62461290/190668545-a66d7253-9bcf-46da-945a-28bc4e6ea19b.png) <br>

The calculation of arrival time, require time and slack remains same.

![image](https://user-images.githubusercontent.com/62461290/190668975-88c923a1-b0c1-4fc1-bb8d-b0564dd8dfc9.png)

## Section 3: Clk-to-q delay, library setup, hold time and jitter

| &Delta;<sub>1</sub> - &Delta;<sub>2</sub> | = Skew <br>

![image](https://user-images.githubusercontent.com/62461290/190689424-cd87624c-72ef-449c-b1d7-3c66395895da.png) <br>

Mux level implementation of capture flop. <br>

![image](https://user-images.githubusercontent.com/62461290/190690335-38470d16-a3c2-4caf-ad5b-4b64a3ba1ebf.png) <br>

-> <b> Negative Latch </b> <br>

Transistor level implementation of negative latch. <br>

![image](https://user-images.githubusercontent.com/62461290/190690443-2bcedb68-9edd-4d72-b42d-b8c5c92571ba.png) <br>

When CLK is low, Tr1 turns on and input D is latched to output Q. <br>

![image](https://user-images.githubusercontent.com/62461290/190841128-de7f0e7e-c45b-4ba1-bdf7-da1ac7b24087.png) <br>

-> <b> Positive latch </b> <br>

Transistor level implementation of positive latch. <br>

![image](https://user-images.githubusercontent.com/62461290/190841212-01fe3415-aba3-4dac-b3f6-f2c36e5e12d5.png)<br>

When CLK is high, Tr4 turns on and input Qm is latched to output Q. <br>

![image](https://user-images.githubusercontent.com/62461290/190841270-88fd8e39-c041-4a83-b1b5-88c8f13f7d8e.png)<br>

Clock signals that go to positive latch and negative latch are different, Hence the difference in names. <br>

-> <b> Positive edge triggered flip-flop using master-slave configuration </b> <br>

![image](https://user-images.githubusercontent.com/62461290/190841620-7a1a30f7-ebf0-406c-8652-9ce26214dbf6.png) <br>

Working for the negative level of the clock. D reaches from input of negative latch to input of positive latch. <br>

When CLK is low, Tr1 and Tr3 turns ON. Hence, input D is latched to output Qm of negative latch. Inv4, Inv6 holds the Q state of slave positive latch. Also D' is ready at the output of Inv5 to propagate till Q when CLK becomes high.<br>

![image](https://user-images.githubusercontent.com/62461290/190841716-67b9935e-b4a1-4cf4-bdda-4cf286a570ac.png) <br>

<I><b> Setup Time </b></I> is the time before rising edge of CLK, that input D becomes valid i.e D input has to be stable such that Qm is sent out, to Q reliably. <br>

Input D takes atleast 3 inverter delays+ 1 transmission gate delay to become stable before rising edge of CLK. Atleast this much amount of time is needed by flipflop to accept the data. If the data comes in between this time frame the data will get corrupted. Therefore a certain amount of <b><I> library setup time </I></b> is needed for the data to be stable at the interiors of the flop. <br>

`Setup Time  = 3 Inverter delay + 1 Transmission gate delay`

Working for the positive level of the clock. D reaches from input of positive latch to output port Q. <br>

When CLK  is high, TR2 and TR4 turns on. Hence input Qm is latched to output Q of negative latch through Tr4 and Inv6. Inv2, Inv3 hold the Qm state of master negative latch. <br>

![image](https://user-images.githubusercontent.com/62461290/190850579-d42f3a21-8fbe-4885-afe2-e318019ad806.png) <br>

<b><I> Clock to Q delay </I></b> is the time needed to propagate 'Qm' to 'Q'. (D was stable till output of Inv5). Therefore time required, to propogate is 1 transmission gate delay + 1 inverter delay. <br>

`Clk-Q = 1 transmission gate delay + 1 inverter delay`

Hold Time is the time for which D input remain valid after clock edge. In this case Tr1 is off after rising CLK. So, D is allowed to change or can change immediately after rise CLK edge. So Hold time is zero.

`Hold Time = zero`

The Analysis is accounted by the following equation <b> &Theta;+&Delta;<sub>1</sub> < T+&Delta;<sub>2</sub> - S </b> <br>

![image](https://user-images.githubusercontent.com/62461290/190851682-3e4401d9-394e-457c-a63d-6e2fd47addfa.png) <br>

#### Generating jitter values - Eye diagram

Eye diagram is given by the foundry.<br>

![image](https://user-images.githubusercontent.com/62461290/190887256-debe28a7-fa98-47af-b19a-0fdef2456d95.png) <br>

Count the number of edges and combine the two versions of clk to form a eye diagram. This eye diagram is the ideal eye diagram. <br>

![image](https://user-images.githubusercontent.com/62461290/190887272-33e0477d-389a-4207-986f-add9ac6aeccf.png)<br>

In practical scenario considering the clock network. The clock does not appear at 0ns at every flipflop. It is bound to arrive at different time. This consideration gives one step better realistic/practical eye diagram. <br>

![image](https://user-images.githubusercontent.com/62461290/190887681-14f1e8ff-84ed-4098-8db1-4d73830ce733.png) <br>

Another important consideration to be taken is the power rails. In the above cases it is assumed that the power is constant and ideal which is not practical. Power Supply variations cause voltage drop and ground bounce. <br>

![image](https://user-images.githubusercontent.com/62461290/190887815-abac1c2a-395d-4e05-9f30-0b40feb2b00d.png) <br>

This is the most realistic eye diagram one can expect. <br>

![image](https://user-images.githubusercontent.com/62461290/190887833-3fde63ed-e163-42d3-ba37-1cefc821d478.png) <br>

![image](https://user-images.githubusercontent.com/62461290/190887893-49c81405-4e73-40c5-bc12-6872b3554953.png) <br>

* <I> Noise Margin: </I> Amount of distortion allowed. It is considered as logic 1 or logic 0 if the received signal lies in between the respective noise margin range. <br>

![image](https://user-images.githubusercontent.com/62461290/190888206-884c7e44-3466-435e-a5f0-1a004815a27f.png) <br>

* <I>Window where data is reliable : </I> It is the region outside which the distortion is observed. The non-corrupted data is observed in this area. If the data is launched or captured in this window it is considered as reliable data.<br>

![image](https://user-images.githubusercontent.com/62461290/190888390-57efccee-cf8a-4303-a9ef-dd8c3ad3a442.png) <br>

* <b><I> Jitter : </I></b> The window where the distortion is observed is called jitter. This has to be accounted for in the clock period as well. The new clock period can be 0&plusmn;&Delta; to T&plusmn;&Delta; 

![image](https://user-images.githubusercontent.com/62461290/190888576-b0fc4818-c794-411c-a8b6-f018643bab37.png) <br>

Jitter has to be acccounted for in the timing reports. We model this using one more parameter called Uncertainty. <br>

Example : Uncertainty = 90ps = 0.09ns <br>

![image](https://user-images.githubusercontent.com/62461290/190888874-147cbad4-7acc-4202-b8fa-e5662fd926d9.png) <br>

The Analysis is now accounted by the following equation <b> &Theta;+&Delta;<sub>1</sub> < T+&Delta;<sub>2</sub> - S - SU </b> <br>

![image](https://user-images.githubusercontent.com/62461290/190888967-24e46dfa-a59e-4bcd-8a9a-1e600f88677e.png) <br>

Data Arrival Time should be less than Data Required time. (Slack = Data Required Time - Data Arrival Time) <br>

Slack should be zero or positive. <br>

## Section 4: Textual Timing Reports and Hold Analysis

<b> Setup Analysis Textual Representation </b> <br>

Inputs (b1/a,b2/a etc) represents net delay and Outputs (b1/y,b2/y etc) represents cell delay. <br>

![image](https://user-images.githubusercontent.com/62461290/190898233-e1989fc2-bcc8-4ec5-a62f-bf8d7959bac0.png) <br>

![image](https://user-images.githubusercontent.com/62461290/190898253-2880efe8-acda-4b1b-ad90-0d7ac20f9d1d.png) <br>

Example of textual representation <br>

![image](https://user-images.githubusercontent.com/62461290/190898353-450f824c-d9c8-491e-9125-788bb8c9ca71.png) <br>

### reg2reg Hold (min) analysis - Single Clock

Hold analysis is mostly dependent on launch flop. It is the time required to launch the data. In this analysis only the edge of the clock is considered not the whole period. In case of setup time the whole period was considered. <br>

Clock is ideal below. <br>
![image](https://user-images.githubusercontent.com/62461290/190898518-933ae73c-5b36-40f9-9213-94258465c067.png) <br>

By adding clock buffers the condition changes to  <b> &Theta;+&Delta;<sub>1</sub> > H+&Delta;<sub>2</sub> </b> <br>

![image](https://user-images.githubusercontent.com/62461290/190898649-0a3adb47-4e69-466c-9cd7-3f51e20c142f.png) <br>

The uncertainity caused because of the jitter has less impact in hold analysis because we consider only the launch edge of the clk, incase of setup analysis we consider both the launch edge and capture edge of the flop hence increasing the jitter thereby increasing the uncertainity. Hence incase of hold analysis we will have a lower uncertainty value. <br>

Considering Uncertainity : <b> &Theta;+&Delta;<sub>1</sub> < T+&Delta;<sub>2</sub> + SU </b> <br>

![image](https://user-images.githubusercontent.com/62461290/190899159-df695baf-1945-4cd6-bc8d-51c10c481742.png) <br>

Data Arrival Time should be greater than Data Required time. (Slack = Data Arrival Time - Data Required Time) <br>

Slack should be zero or positive. <br>

<b> Hold Analysis Textual Representation </b> <br>

![image](https://user-images.githubusercontent.com/62461290/190899291-935a8399-82c3-4984-80a5-70e6ee66df32.png) <br>

![image](https://user-images.githubusercontent.com/62461290/190899315-b321a649-a141-48d8-9e9b-2dbc56d06ae4.png)

Example of textual representation <br>

![image](https://user-images.githubusercontent.com/62461290/190899449-1cda5439-f766-4636-963d-56f03d6fcfbf.png) <br>

## Section 5 : On-chip Variation

-> <b><I> Etching Process Variation </I></b> <br>

 <I> Etching process effecting the behaviour of single inverter. </I> <br>
 
 ![image](https://user-images.githubusercontent.com/62461290/190911055-b2effb80-8eeb-4ae7-a8f4-c544a620597e.png) <br>
 
 Inverter chain: <br>
 
 ![image](https://user-images.githubusercontent.com/62461290/190911089-c585bacb-15eb-4584-9def-8958f7c7c3bd.png) <br>
 
 Etching process: <br>
 
![image](https://user-images.githubusercontent.com/62461290/190911216-69113c65-c633-4408-b1c0-a6c4885d0108.png) <br>

This variation can be present for each and every structure. This modified W/L ratio will effect the drain current. <br>

![image](https://user-images.githubusercontent.com/62461290/190911357-a7af4569-db96-46d2-9287-a2f28671ae10.png) <br>

-> <b><I> Oxide Thickness Variation </I></b> <br>

<I> Oxide Thickness Variation effecting the behaviour of single inverter. </I> <br>

![image](https://user-images.githubusercontent.com/62461290/190911408-be4133bc-9c53-4610-acd2-6bc67fc2cc57.png) <br>

 Oxide process: oxide thickness is not constant and will persist for all the transistors. <br>

![image](https://user-images.githubusercontent.com/62461290/190911473-0968d8e8-9963-414c-a9cc-9adcc681c520.png) <br>

The variation in thickness directly impacts the Drain Current. <br>

![image](https://user-images.githubusercontent.com/62461290/190912824-99f93937-96b9-4f26-af18-f017b434c743.png) <br>

<b><I> Propagatin Delay of Inverter Cell  </b></I> <br>

The inverter can be modelled as a switch with RC components. The charging and discharging of the capacitor is the output of the inverter. The charging takes place based on the current Id. <br>

![image](https://user-images.githubusercontent.com/62461290/190913051-0c96d8a9-f7ec-41a5-852c-902dfaaecac4.png) <br>

Output Voltage depends on the amount of current supplied to the capacitor, Which inturns becomes a function of the R and C values. <br>

![image](https://user-images.githubusercontent.com/62461290/190913147-df1d8568-369c-4082-b8f6-f6df4a5034d8.png) <br>

We have to get the Drain current in terms of resistance. <br>

![image](https://user-images.githubusercontent.com/62461290/190913476-a050ee2b-be0c-49c3-a760-df3a0574fb5a.png) <br>

<I> R of inverter cell : </I> R is not constant but varies with Id. <br>

![image](https://user-images.githubusercontent.com/62461290/190913581-2bbad35f-3472-4fea-aedc-af4e62a46af4.png)

Connecting all the parameters together. <br>

![image](https://user-images.githubusercontent.com/62461290/190913617-37f36d75-b8c0-4efc-b353-75ce73dbecf9.png) <br>

Each inverter can give different delays based on the above parameters. The inverters in the corner might deviate more because the cell they are connected to on the other end might have a significant impact on these cells. <br>

![image](https://user-images.githubusercontent.com/62461290/190913710-67b201dd-e3ab-4822-b1d8-640b0ad7306c.png) <br>

Graphically plotting these variations in inverter. <br>

Combining these variations together give a factor called on-chip derates. <br>

![image](https://user-images.githubusercontent.com/62461290/190913961-29f218ca-3a86-4c87-99c3-3a971c405b08.png) <br>

## Section 6: OCV timing and pessimism removal

-> <b><I> OCV for Setup analysis </I></b>

![image](https://user-images.githubusercontent.com/62461290/190919502-519015cf-38f2-4138-98ab-ddbf266e4425.png) <br>

OCV can be compensated in 4 different ways. <br>

1. DRT &uarr; DAT &uarr; <br>
2. DRT &uarr; DAT &darr; <br>
3. DRT &darr; DAT &uarr; <br>
4. DRT &darr; DAT &darr; <br>

When DRT is reduced it is called clock pull-in. <br>

![image](https://user-images.githubusercontent.com/62461290/190919605-2be34cc0-e523-4742-a8f5-fae5aa72e956.png) <br>

When DAT is increased it is called clock push-out. <br>

![image](https://user-images.githubusercontent.com/62461290/190919625-5fcf2c21-62d3-4ca1-9216-a3ef96837c7b.png) <br>

This gives a more realistic and conservative analysis. <br>

![image](https://user-images.githubusercontent.com/62461290/190919548-09848964-d48f-4bce-a2ee-5845058780e8.png) <br>

Pull in DRT by 20%. <br>

![image](https://user-images.githubusercontent.com/62461290/190919739-bfc92934-dc85-4c9b-ae90-abd9bb90d816.png) <br>

The similar sections have to be considered which was ignored before. <br>

![image](https://user-images.githubusercontent.com/62461290/190919805-2870074d-a6f7-4730-aa05-f5b291c00785.png) <br>

<I> A cell cannot have 2 delay values at same instance of time. </I> <br> 

Example: At a time instant the delay of cell 'b1' can be either 0.043ns or 0.0344ns. So there is an additional pessimism of |0.043ns - 0.0344ns| = 0.0086ns. We need to remove this pessimism. <br>

![image](https://user-images.githubusercontent.com/62461290/190919873-19a913c0-b67b-4d2c-aa76-015f263f6fa3.png) <br>

After adding pessimism to DRT we get positive slack. <br>

![image](https://user-images.githubusercontent.com/62461290/190920013-794464b2-cd92-443c-8a4f-542008f0c956.png) <br>

Additional pessimism has to be accounted while doing calculations. It is one of the important factor. <br>


-> <b><I> OCV for Hold analysis </I></b>

![image](https://user-images.githubusercontent.com/62461290/190921433-b1f400de-ed6c-4aa0-8ab6-9f63c31f8833.png)

OCV can be compensated in 4 different ways here as well. <br>

Here, When DAT is reduced it is called clock pull-in. When DRT is increased it is called clock push-out. Here we will do both pull-in and push-out to get the worst case analysis. <br>

![image](https://user-images.githubusercontent.com/62461290/190921562-272bdd39-4e56-4073-8d0d-f682ef7b8996.png) <br>

![image](https://user-images.githubusercontent.com/62461290/190921579-fb056a06-3bdb-4770-b2fa-774a8e4093fd.png) <br>

If hold analysis fails we cannot recover and the whole chip will fail. <br>

performed push-out by 20% and pull-in by 20% together. <br>
![image](https://user-images.githubusercontent.com/62461290/190921644-9c82d12a-7dec-40a3-a37b-336791bb3b04.png) <br>

Additional pessimism has to be considered here as well. 

![image](https://user-images.githubusercontent.com/62461290/190921692-225cc1b2-779b-4f09-8611-1aa4f9aab76a.png)

After considering additonal pessimism. <br>

![image](https://user-images.githubusercontent.com/62461290/190921740-f2d318f6-ba5d-4485-99a3-db67ccde5ed1.png) <br>

## Section 7 : Conclusion

- We summarized rer2reg timing analysis. The concepts we learned for reg2reg analysis can be applied to any other setup/hold analysis. <br>

- While doing Slew/Transition analysis we will be using library setup and hold time. <br>

- Clock analysis is highly dependent on on-chip variation and pessimism removal. <br>

<br>

<br>

<br>

# VSD Static Time Analysis - 2

## Section 1: Introduction to sta-2 and opentimer tool

This course is a hands-on approach to do the analysis using opentimer.<br>

Install all the requirements.<br>

The circuit we will be working on for analysis in OpenTimer.<br>


<b> System Requirements </b>

OpenTimer is very self-contained and has very few dependencies.
To compile OpenTimer, you need a [C++17][C++17] compiler. 
We currently support:

+ GNU C++ Compiler v7.3 with -std=c++1z
+ Clang C++ Compiler v6.0 with -std=c++17

In addition, you need a tcl shell interpreter:

+ [tclsh](https://www.tcl.tk/about/language.html) 
(most Unix/Linux/OSX distributions already include tclsh)

OpenTimer has been tested to run well on Linux distributions and MAC OSX.

<b> Build through CMake </b>

We use [CMake](https://cmake.org/) to manage the source and tests.
We recommend using out-of-source build.

```bash
$ git clone https://github.com/OpenTimer/OpenTimer.git
$ cd OpenTimer
$ mkdir build
$ cd build
$ cmake ../
$ make 
$ make test #to test if the installation was successful.
```

After successful build, you can find binaries and libraries in the folders `bin` 
and `lib`, respectively.

The following circuit will be the circuit we will be performing analysis on. <br>

![image](https://user-images.githubusercontent.com/62461290/190990640-d2d11ff1-4a4f-4784-ae3a-80c49f170592.png) <br>

Open the OpenTimer Shell.<br>

![image](https://user-images.githubusercontent.com/62461290/190993034-ed76d86f-9de1-4561-bce9-fb3003525c50.png) <br>

## Section 2: Constraints creation commands for Opentimer

<b> Clock constrains for the Clk pin </b>

`clock clk 1000 50`
<br>
<br>
<I>clock</I> - Keyword understood by opentimer which says these are clock contrains.<br>
<I>clk</I> -  It is the net/port name.<br>
<I>1000</I> - Period of the clock is 1000ps/1ns.<br>
<I>50</I> - Represents the duty cycle of the clock, (100-50) is the duty.<br>
Example if the above number was 30, The clock would have been low for 30% and high for 70% making the duty cycle 70%. <br>

![image](https://user-images.githubusercontent.com/62461290/190996489-c00eccf1-093d-46ff-8c5b-d002a986b92d.png)<br>

<b> Arrival Time for the Clock Port </b>

`at clk 0 500 0 500`
<br>
<br>
<I>at</I> - Keyword understood by opentimer which says these are the arrival time constrains. <br>
<I>clk</I> -  It is the net/port name.<br>
<I>0</I> - Early Rise Arrival time.<br>
<I>500</I> - Early Fall Arrival time.<br>
<I>0</I> - Late Rise Arrival time.<br>
<I>500</I> - Late Fall Arrival time.<br>

![image](https://user-images.githubusercontent.com/62461290/190996395-6c04c817-4045-44d9-abd8-f22c7bb539be.png) <br>

The above convention for at is followed for most of the constraints in the timing files. <br>

Present `my_netlist.timing` file.<br>

```
clock clk 1000 50
at clk 0 500 0 500
at in 50 50 100 100
slew clk 70 50 70 50
slew in 150 100 150 100
load out 40
rat out 160 160 180 180
```

Modified `my_run.tcl` for the OpenTimer present format.<br>

```
set_num_threads 1
read_celllib -max my_early.lib
read_celllib -min my_late.lib
read_spef blank.spef
read_verilog my_netlist.v
read_timing my_netlist.timing

```

Running the above commands in OpenTimer

![image](https://user-images.githubusercontent.com/62461290/191006390-bfb5d240-ee93-4e9e-8d21-01f3dee304c3.png) <br>

![image](https://user-images.githubusercontent.com/62461290/191006629-83a52a35-eb61-4edc-9894-c3997a5337b8.png) <br>


modified `my_netlist.timing` file. <br>

```
clock clk 1000 50
at clk 12 45 18 72
at in 50 50 100 100
slew clk 70 50 70 50
slew in 150 100 150 100
load out 40
rat out 160 160 180 180
```

![image](https://user-images.githubusercontent.com/62461290/191007275-ee76c325-e57a-46c5-97c1-eeb35dac207f.png) <br>

<b> Arrival Time for Input Port</b> 

`at in 50 50 100 100`
<br>

<I>at</I> - Keyword understood by opentimer which says these are the arrival time constrains. <br>
<I>in</I> -  It is the net/port name.<br>
<I>50</I> - Early Rise Arrival time.<br>
<I>50</I> - Early Fall Arrival time.<br>
<I>100</I> - Late Rise Arrival time.<br>
<I>100</I> - Late Fall Arrival time.<br>

Here the delays are respect to the arrival of the edge of the clock.<br>


<table>
  <tr>
    <td><img src="https://user-images.githubusercontent.com/62461290/191010095-e3c26aac-ecbd-4dff-9089-3f8e89781999.png"></td>
    <td><img src="https://user-images.githubusercontent.com/62461290/191013614-4e6abcc4-8fd8-41b5-93b6-d7caa6b99499.png"></td>
  </tr>
 </table>


<table>
  <tr>
    <td><img src="https://user-images.githubusercontent.com/62461290/191010712-09d81ffd-e8b9-4781-8b53-9a1b29e612f4.png"></td>
    <td><img src="https://user-images.githubusercontent.com/62461290/191012731-49ce8719-d90e-47de-a475-a256e22016c5.png"></td>
  </tr>
 </table>
 
 <br>
 
 <b> Clock Slew </b>
 
 `slew clk 70 50 70 50`
 <br>
 
<I>slew</I> - Keyword understood by opentimer which says these are the slew constrains. <br>
<I>clk</I> -  It is the net/port name.<br>
<I>70</I> - Early Rise Slew.<br>
<I>50</I> - Early Fall Slew.<br>
<I>70</I> - Late Rise Slew.<br>
<I>50</I> - Late Fall Slew.<br>

![image](https://user-images.githubusercontent.com/62461290/191015953-d926e227-ad46-4a7e-a014-6a269d222557.png)<br>

The slew mentioned is the difference between the 80% and 20% time. <br>

![image](https://user-images.githubusercontent.com/62461290/191016450-40e2387e-ecf1-4e21-9eaf-707c53b36e67.png) <br>

 <b> Input Slew </b>
 
 `slew in 150 100 150 100`
 <br>
 
<I>slew</I> - Keyword understood by opentimer which says these are the slew constrains. <br>
<I>in</I> -  It is the net/port name.<br>
<I>150</I> - Early Rise Slew.<br>
<I>100</I> - Early Fall Slew.<br>
<I>150</I> - Late Rise Slew.<br>
<I>100</I> - Late Fall Slew.<br>

Here the delays are respect to the arrival of the edge of the clock.<br>

<table>
  <tr>
    <td><img src="https://user-images.githubusercontent.com/62461290/191017135-9170d72c-f528-4401-b5df-dfc653e2855f.png"></td>
    <td><img src="https://user-images.githubusercontent.com/62461290/191017262-e26150ca-ac18-462a-a91e-3762e459c185.png"></td>
  </tr>
 </table>
 

<table>
  <tr>
    <td><img src="https://user-images.githubusercontent.com/62461290/191017611-561638c5-f0cd-4ce1-934f-b10e1955309d.png"></td>
    <td><img src="https://user-images.githubusercontent.com/62461290/191017861-e37d2d76-a04b-4457-9f32-1d5262f9d668.png"></td>
  </tr>
 </table>


<b> Output Load </b> <br>

`load out 40`

<I> load </I> : Keyword understood by opentimer which says this the load to be considered.<br>
<I> out </I> : It is the net/port name.<br>
<I> 40 </I> : Specifies load is 40fF.<br>

![image](https://user-images.githubusercontent.com/62461290/191019699-75d95a93-b2ce-466b-ae60-8cf222fbf6c2.png) <br>

<b> Output delay constrains </b> <br>

`rat out 160 160 180 180`<br>


<I>rat</I> - Keyword understood by opentimer which says these are the output constrains. <br>
<I>out</I> -  It is the net/port name.<br>
<I>160</I> - Early Rise Required Arrival Time.<br>
<I>160</I> - Early Fall Required Arrival Time.<br>
<I>180</I> - Late Rise Required Arrival Time.<br>
<I>180</I> - Late Fall Required Arrival Time.<br>

<table>
  <tr>
    <td><img src="https://user-images.githubusercontent.com/62461290/191020579-1a4951b1-c918-47f2-b594-9c30d3b2b27e.png"></td>
    <td><img src="https://user-images.githubusercontent.com/62461290/191021676-00a61c8a-ec93-4670-b0cc-9e8a30da41e3.png"></td>
  </tr>
 </table>
 
 modified `my_netlist.timing`
 
 ```
 clock clk 1000 50
at clk 12 45 18 72
at in 53 34 121 125
slew clk 70 50 70 50
slew in 150 100 150 100
load out 40
rat out 160 160 180 180
```

## Section 3 : Full reg2reg analysis using OpenTimer tool

