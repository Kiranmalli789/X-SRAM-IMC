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

![1](https://user-images.githubusercontent.com/99113992/156103652-cac5bf4b-8bd8-4dad-a428-a66f4bd467bb.PNG)
The 8T SRAM circuit is shown in fig.1.This circuit avoids
the read operation noise by isolating the memory part(latch)
of the cell from external environment by disabling the access
transistors during read operation and the memory read
operation is done by adding additional circuitry as shown in
fig.1.In our present project, by using IMC scheme we implement
four in-memory vector computations which includes
NAND,NOR,IMC,XOR.
### SRAM circuit
![sram sch](https://user-images.githubusercontent.com/99113992/156110098-13c60c32-8fe8-47cf-8a2d-17521f8991bc.PNG)

## Circuit Operation

Whenever the RWL=1, then only the in-memory computations
takes place and intially the RBL is precharged and the
dicharging of RBL voltage depends on the data stored in the
cell1 (Q1) and cell2 (Q2).
### 1.NOR OPERATION
[nor netlist.txt](https://github.com/Kiranmalli789/X-SRAM-IMC/files/8159069/nor.netlist.txt)

![nor sch](https://user-images.githubusercontent.com/99113992/156104263-c76ae031-c6b3-4905-9b25-834a731a1afa.PNG)

When A and B both are 0’s then the
precharged value of RBL remains same and it’s considered as
logic 1 and for remaining combinations of A and B RBL gets
discharged and it’s considered as logic 0.

### 2.NAND OPERATION
[nand netlist.txt](https://github.com/Kiranmalli789/X-SRAM-IMC/files/8159059/nand.netlist.txt)

![nand sch](https://user-images.githubusercontent.com/99113992/156104194-a79e34e6-7826-4321-aa10-10e947430a43.PNG)

When A=1 and B=1, RBL gets
discharged and output is logic 0; when A=0,B=1 or A=1,B=0
then the RWL signal had to be timed such that RBL doesn’t
discharge completely and the trip point of INV3 in fig.2 is
chosen that the output goes only high for the case A=1,B=1.We obtained this by skewing the inveter connected to RBL.

### 3.XOR OPERATION
![xor sch](https://user-images.githubusercontent.com/99113992/156104321-7081955b-7346-4b88-b463-dcc32bfdb976.PNG)

By making the source of M1 transistor
of Cell1 ”VDD” and source of M1 transistor of Cell2
”GND”, M1-M2-M3-M4 form a voltage divider, shown in
fig.3.And if A and B are both 0’s or 1’s then the RBL voltage
remains close to precharge value and if A=1,B=0 RBL voltage
is VDD and if A=0,B=1 then RBL voltage is 0 and by ORing
the INV3 and INV2 we get the XOR operation of A and B.

## Simulation Waveforms

### 1.NOR Operation

#### a.Q1Q2 = 00 or 11
![nor 00,11](https://user-images.githubusercontent.com/99113992/156104696-d0e2530e-d8b8-47f2-b9be-a4a49d11de91.PNG)

#### b.Q1Q2 = 01
![nor 0,1](https://user-images.githubusercontent.com/99113992/156104741-ba97b459-19ac-462a-9738-2d04379aa1fe.PNG)

#### c.Q1Q2 = 10
![nor 10](https://user-images.githubusercontent.com/99113992/156104782-5bc95f18-797b-45ca-b7b5-afdcbfee6242.PNG)


### 2.NAND Operation

#### a.Q1Q2 = 01 or 10
![nand 01,10 correct](https://user-images.githubusercontent.com/99113992/156104403-ca1918e8-ee22-4a5c-90a2-e81b90d91f8e.PNG)

#### b.Q1Q2 = 00
![nand 00](https://user-images.githubusercontent.com/99113992/156104571-279ffbc9-26f6-4c00-a44f-6481c3a0c66c.PNG)

#### b.Q1Q2 = 11
![nand 11,correct](https://user-images.githubusercontent.com/99113992/156104642-495e5a95-b8e6-4403-94ff-7cae7b594020.PNG)


### 2.XOR Operation

#### a.Q1Q2 = 01 or 10
![xor 01,10](https://user-images.githubusercontent.com/99113992/156104886-006d1fc3-dcff-4c2d-b68f-38bc77fd6917.PNG)

## Conclution

By replacing the existing CVN Architecture with the IMC technique we can reduce the latency and power consumption of the boolean expression, since in IMC scheme all the rows 
are simultaneously on at a time there by reducing the time required for over memory read and also there is no need for the data movememts from memory to ALU, since the arthmetic 
operation is calculated in the memory itself by modifying the basic SRAM circuit to perform the required operation.

In our present project, we modified the conventional 6T SRAM by adding additional circuit so that it performs the basic boolean logic such as xor,nand,nor and imp functions.We
simulated the X-SRAM circuit and performed the NAND,NOR and XOR operation and obtained results.

## References

A.Agrawal, A.Jaiswal, C.Lee, K.Roy ”X-SRAM: Enabling
In-Memory Boolean Computations in CMOS Static Random
Access Memories”,IEEE TRANSACTIONS ON CIRCUITS
AND SYSTEMS–I: REGULAR PAPERS, VOL. 65, NO. 12,
DECEMBER 2018

## Acknowledgement

Kunal Ghosh,Co-founder of VLSI System Design Corporation Pvt. Ltd.

Cloud Based Analog IC Design Hackathon and IIT Hyderabad

Synopsys India

## Author

Malli Chenchu Kiran, Final Year B.TECH, ECE, Indian Institute of Information Technology,Design and Manufacturing,(IIITDM) Kancheepuram

Email: Kiran.malli789@gmail.com
