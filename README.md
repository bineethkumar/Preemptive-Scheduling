# Operating Systems Final Project

## Topic: Devlop/Simulate an Preemptive Scheduling Algorithm

### Problem Statement  
Currently prevalent round robin preemptive scheduling algorithms are not applicable in real 
time operating systems because of their large waiting time, large turnaround time, large 
response time, high context switch rates and less throughput. The primary aim of this project 
is to come up with a method for round robin scheduling which enhances the CPU 
performance in a real time operating system. The proposed algorithm for real time systems is 
a hybrid of priority and round-robin scheduling algorithms. It combines the merits of round 
robin, like elimination of starvation, and priority scheduling. The proposed algorithm also 
deals with aging by assigning variable priorities to the processes. Thus, the algorithm corrects 
all the limitations of round robin scheduling algorithm. We will also present a comparative 
analysis of our new algorithm with the existing algorithm i.e., round robin based on average 
turnaround time, average waiting time, varying time quantum and number of context 
switches. 

### Algorithm:
We calculate an Intelligent Time Slice (ITS) is calculated based on the priority, shortest CPU burst time and context switch. We have a pre-defined time slice which is the Original Time Slice (OTS), if the process needs special consideration, the Priority Component (PC) is assigned to 0 or 1 according to the pre-defined priority by the user. We define a Shortness Component (SC) which is the difference between the burst time of the current process and its previous process. If the difference is negative, we make SC as 1 else 0. To calculate Context Switch Component (CSC) we add PC, SC and OTP and the resulting sum is subtracted from the burst time of the process. If the result obtained is less than the OTS, we consider it as CSC. Adding all the calculated components we get our ITS.

1.	Sort the processes according to priority as well as shortness and assign a new priority to each process which is the sum of the original priority and shortness rank.

2.	Calculate priority component. If there are n processes, for a process i in n  
PCi=0 if its new priority is > 2n/3 (Not Important)   
PCi=1 if its new priority is > n/3 (Moderately Important)   
PCi=2 if its new priority is >= 1 (Important) 

3.	 Calculate shortness component. If there are n processes, for a process i in n   
SCi=0 if the (Burst Time)i>(Burst Time)i-1 (Longer)   
SCi=1 if the (Burst Time)i<=(Burst Time)i-1 (Shorter)

4.	Calculate the intelligent time slice (ITS) for each process as the sum of the initial time slice, burst time, priority component and shortness component

5.	Repeat Step 6 until all processes are completed. 

6.	If the Round number(j) is 1, calculate time quantum as  
TQj,i=ITSi if SCi=1   
TQj,i=ITSi/2 if SCi=0   
If the Round number(j) is not 1, calculate time quantum as  
TQj,i=TQj-1,i * 2 if SCi=1   
TQj,i=TQj-1,i * 1.5 if SCi=0  

7.Calculate average waiting time and average turnaround time.

**Preemptive Schedules Used:** _Round Robin_ and _Priority Scheduling_
