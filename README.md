# VSD Static Time Analysis - 1

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

6. <I> recovery/removal : </I> Path between a clock of flipflop that is driving reset pin to the reset pin is called recovery/removal path. <br>

![image](https://user-images.githubusercontent.com/62461290/190439696-dd8d1c9a-2378-4633-8740-46456a9e12fa.png) <br>


7. <I> 

