# Computer Architecture

## Lab 3
18/12/2020\
Ilia Zarka 9289\
Iosif Chrysostomou 9130

---

## Step 1

#### 1. Dynamic Power and Leakage
Dynamic power is the power used for gate operations of the transistors, which the CPU consists of. Hence it is proportional to the gate operations (more gate operations -> more power).

Leakage is an unwanted loss of energy. This mainly happens because electronic charges dissipate over time and currents flow where they are not supposed to.

With a different program, leakage power should remain at about the same value. The dynamic power, assuming that the number of transistor gates that change per clock tick is different, will change. And since our program calculates the peak dynamic power, the only clock cycle that should matter is the one with the most gate logic changes. So the duration of the program should not matter.

#### 2. Power, Energy and Performance
The output of McPAT gives us only the peak power of the cpu. To calculate the life of a battery supplying power to the cpu we need to divide its capacity with the average power consumption of that CPU. 

To answer this question we had to make some assumptions:
* The battery has no internal resistance
* The battery can handle the current
* The leakage power of the cpu(s) is the same in every case
* The cpus are given the same tasks and they can both finish them before the battery is dead

So if a CPU that consumes 10 times more peak power than another, it can require less energy to complete a task if it completes it in less than 1/10 of the time of the other one.

If we want to calculate the battery life from the McPAT output, it should give us enough information to calculate the total energy consumption of the cpu for the program. So it could either give us that number or an average power consumption and an estimated time that it would take to run the program.

#### 3. Power consumption in different architectures

* Intel Xeon
* ARM A9

Since the two systems will not turn off after the completion of the program, even if the arm cpu would run only on its peak power(1.74W) and the xeon cpu on its leakage power(36.8W), the xeon cpu would have no chance on consuming less energy over time. The difference only increases when we factor in the 134.9W of peak power for the xeon.

## Step 2 EDP, Possible Errors, Combining 2 simulators

Power-Delay Product (PDP) and Energy-Delay Product (EDP) are two figures of merit which are used to assess power and energy efficiency relatively to performance. In the case of this exercise, in our MinorCPU model we examined Runtime Dynamic, Subthreshold Leakage and Gate Leakage as the power used by each component in every stage of its cycle. Τhe compoments used are the Core (single processor model), which includes L1 caches and L2 cache since they take up most of the area of the modeled chip.

* PDP was calculated by this formula: `PDP = (coreRtDyn + coreSubLeakage + coreGateLeakage + L2RtDyn + L2SubLeakage + L2GateLeakage) * Runtime`
* EDP was calculated by this formula: `EDP = (coreRtDyn + coreSubLeakage + coreGateLeakage + L2RtDyn + L2SubLeakage + L2GateLeakage) * Runtime^2` or simply `PDP * Rutime`

**Power** values where extracted from the output of McPAT tool and **time** value (Runtime) was extracted from gem5 stats output.
