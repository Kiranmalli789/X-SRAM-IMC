# IMC:In-memory Boolean computation using 8T-SRAM

In this project,we are using IMC technique by replacing the existing conventional von-neumann Architecture to compute basic logic operations such as NAND,NOR and XOR Operations.

# Table of Contents

1.[Introduction](#Introduction)

2.[Circuit Design and Details](#Circuit-Design-and-Details)

3.[Circuit Operation](#Circuit-Operation)
   
4.[Simulation Waveforms](#Simulation-Waveforms)

5.[Conclution](#Conclution)

6.[References](#References)

7.[Acknowledgement](#Acknowledgement)

8.[Author](#Author)

## Introduction

Now-a-days among different memory elements
SRAM(Static Random Access Memory) became very popular
because of their high speed operations and low power consumption.
And for faster performimg of complex computations,
digital boolean logic became necessary.But we know that most
of the computers follow von-neumann computer architecture in
which computing any boolean logic involves memory read,Data
movement and data execution through which the overall power
consumption and throughput degrades and this is known as
von-neumann bottleneck.And in our project we implemented
In-memory computing(IMC) scheme to reduce these overheads
associated with von-neumann bottleneck.Therefore,in this present
work by replacing the conventional 6T SRAM with the 8T SRAM
which has the ability to perform in-memory, vector Boolean
computations without any limitations occured in von-neumann
bottleneck.

## Circuit Design and Details


The 8T SRAM circuit is shown in fig.1.This circuit avoids
the read operation noise by isolating the memory part(latch)
of the cell from external environment by disabling the access
transistors during read operation and the memory read
operation is done by adding additional circuitry as shown in
fig.1.In our present project, by using IMC scheme we implement
four in-memory vector computations which includes
NAND,NOR,IMC,XOR.

## Circuit Operation

Whenever the RWL=1, then only the in-memory computations
takes place and intially the RBL is precharged and the
dicharging of RBL voltage depends on the data stored in the
cell1(A) and cell2(B), shown in fig.2.
1.NOR OPERATION: When A and B both are 0’s then the
precharged value of RBL remains same and it’s considered as
logic 1 and for remaining combinations of A and B RBL gets
discharged and it’s considered as logic 0 and this is shown in
fig.2.
2.NAND OPERATION: When A=1 and B=1, RBL gets
discharged and output is logic 0; when A=0,B=1 or A=1,B=0
then the RWL signal had to be timed such that RBL doesn’t
discharge completely and the trip point of INV3 in fig.2 is
chosen that the output goes only high for the case A=1,B=1.
3.XOR OPERATION: By making the source of M1 transistor
of Cell1 ”VDD” and source of M1 transistor of Cell2
”GND”, M1-M2-M3-M4 form a voltage divider, shown in
fig.3.And if A and B are both 0’s or 1’s then the RBL voltage
remains close to precharge value and if A=1,B=0 RBL voltage
is VDD and if A=0,B=1 then RBL voltage is 0 and by ORing
the INV3 and INV2 we get the XOR operation of A and B.
4.IMP Operation: This also achieved by forming voltage
divider and INV1 implements ’A IMP B’.

## Simulation Waveforms

### 1.Write Operation

As we have discussed earlier when WL=1,then the write operation is possible and the Q gets the BL value and Qb gets the inverted value of Q.And when WL=0,the data stored in
the memory element doesn't change because of the access transistors are in inactive state.

![write operation](https://user-images.githubusercontent.com/99113992/152926807-6d204d6f-d516-4b4b-bc15-90d63d32310e.PNG)

### 2.READ Operation

When RE=1 and REB=0, then the READ operation will takes place with the Transmission gate is in active state and the the data present in the memory element(Q) is passed through the inverter and then transimission gate to the RD terminal.Note that the RD terminal gets the inverted value of Q(i.e, Qb) because of the inverter, but if we want the Q to 
comeout at the RD terminal we need to connect that extra circuit to the Qb instead of Q.

![READ output](https://user-images.githubusercontent.com/99113992/152926529-253768c3-2502-4da1-b278-3e1437624971.PNG)

Note that there is a small disturbance in the RD terminal during when the transmission gate is in off state(i.e, when RE=0 and REB=1), it's because when the transmission gate is in inactive condition there will be some leakage current since both of the nmos and pmos is in off state and moreover what we actually interested is during when transmission gate is in active state at which the READ Operation will takes place, So it doesn't matter to us when the transmission gate is in inactive state even if there is small disturbance in the output waveform. 

## Conclution

In 10T SRAM, since the inverter is directly connect with the memory element to make the READ operation independent of access transistors, we can actually reduce the read delay 
because now we don't need to wait for the access transistors to turn on for read operation.But the write operation still takes time because it still depends on Access transistors.In this section we are going to prove that the READ speed is increased by making the READ operation independent on Access Transistors.

For measuring the read and write operation delay we simulated the same circuit, but by keeping the Timeperiod of input waveforms in nanometers we got the following results.

![compare read and write](https://user-images.githubusercontent.com/99113992/152933868-f7727778-3dd6-4ef7-bc85-453e18634cd9.png)

From the figure, 

A = write 0 delay (i.e.,Time taken for BL=0 passes through the Access transistor to memory element(latch) and make Q=0)  

B = write 1 delay (i.e.,Time taken for BL=1 passes through the Access transistor to memory element(latch) and make Q=1)

C = Read 0 delay  (i.e.,Time taken for Q=0 passes through the inverter and transmission gate and make RD=1)

D = Read 1 delay  (i.e.,Time taken for Q=1 passes through the inverter and transmission gate and make RD=0)

From the above waveform we can say that both the Read 0 and Read 1 delay is less than write 0 and write 1 respectively.Therefore, by making the read operation independent of Access transistors by adding the additional circuit for measuring READ operation we increased the READ Operation speed and hence reduced the leakage power.And through this we increase the read stability since we isolated 
the memory element from external noise.

## References

PN.V.Kiran, N.Saxena, "Parameter Analysis of different SRAM Cell Topologies and Design of 10T SRAM Cell at 45nm Technology with Improved Read Speed",International Journal of Hybrid Information Technology,Vol.9, No.2 (2016).

## Acknowledgement

Kunal Ghosh,Co-founder of VLSI System Design Corporation Pvt. Ltd.

## Author

Malli Chenchu Kiran, Final Year B.TECH, ECE, Indian Institute of Information Technology,Design and Manufacturing,(IIITDM) Kancheepuram

Email: Kiran.malli789@gmail.com
