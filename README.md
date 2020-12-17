# computer_architecture_ex3

## Step 1

#### 1.
Dynamic power is the power used for gate operations of the transistors, which the cpu consists of. Hence it is proportional to the gate operations (more gate operations → more power).

Leakage is an unwanted loss of energy. This mainly happens because electronic charges dissipate over time and currents flow where they are not supposed to.

With a different program, leakage power should remain at about the same value. The dynamic power, assuming that the number of transistor gates that change per clock tick is different, will change. And since our program calculates the peak dynamic power, the only clock cycle that should matter is the one with the most gate logic changes. So the duration of the program should not matter.

#### 2.
The output of McPAT gives us only the peak power of the cpu. To calculate the life of a battery supplying power to the cpu we need to divide its capacity with the average power consumption of that cpu. 

To answer this question we had to make some assumptions:
* The battery has no internal resistance
* The battery can handle the current
* The leakage power of the cpu(s) is the same in every case
* The cpus are given the same tasks and they can both finish them before the battery is dead

So if a cpu that consumes 10 times more peak power than another, it can require less energy to complete a task if it completes it in less than 1/10 of the time of the other one.

If we want to calculate the battery life from the McPAT output, it should give us enough information to calculate the total energy consumption of the cpu for the program. So it could either give us that number or an average power consumption and an estimated time that it would take to run the program.

#### 3.

Since the tow systems will not turn off after the completion of the program, even if the arm cpu would run only on its peak power(1.74W) and the xeon cpu on its leakage power(36.8W), the xeon cpu would have no chance on consuming less energy over time. The difference only increases when we factor in the 134.9W of peak power for the xeon.

## Step 2
