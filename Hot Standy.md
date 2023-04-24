we all need a way to avoid a total failure. Our backup plan MUST include a Hot swap / Hot standy solution.
Inherited by Industrial Automation solutions for redundancy, reliability and availability

# The importance in having a Hot stanby

## **What is Cold Standby?**

Suppose you have two PLCs. One PLC is working as a primary one. The same program running in primary PLC is present in standby [PLC](https://instrumentationtools.com/feedback-monitoring-in-safety-plc/), but it is not powered on. Also, no communication cables have been connected to it. It can thus be considered as a spare PLC, waiting to come into action when the primary PLC fails.

Now, when the primary PLC fails, the operator will shut down the system, connect the cables to the standby PLC and power it on. The standby PLC will now control the process. This system is called **cold standby**. The system takes a very long time to get back up again when there is a sudden interruption. So, cold standby systems are useful where the process is non-critical and some downtime can be bearable.

ust you need to have a standby system in place, whenever the primary system fails. Do remember to immediately bring the primary system into a running state once again by either repairing it or replacing it.

![Industrial Automation Cold and Hot Standby](https://instrumentationtools.com/wp-content/uploads/2023/03/Industrial-Automation-Cold-and-Hot-Standby.png?ezimgfmt=rs:778x479/rscb2/ngcb2/notWebP)

Image Courtesy: [Siemens](https://www.siemens.com/)

## **What is Hot Standby**

Suppose you have two PLCs. One PLC is working as a primary one. The same program running in primary PLC is present in standby PLC. But, it is powered up and continuously communicating with primary PLC.

Now, when the primary PLC fails, the standby PLC will instantly become primary and take-over the in-charge of the process. It happens in microseconds. This system is called **hot standby**. It’s a [redundant method](https://instrumentationtools.com/plc-redundancy/) that runs an identical backup system constantly, bouncing data back super-fast; so in the event of system failure, both sites have identical data and can still deliver optimum quality whilst the primary system recovers.

Once the primary system becomes normal again and when the standby system fails, then the primary will again take-over the in-charge and the cycle repeats itself.

## **Difference between Cold Standby and Hot Standby**

The main differences between hot and cold standby systems are mentioned below.

-   A cold standby system is cheaper than hot standby.
    
-   A hot standby system is used in critical projects, whereas a cold standby system is used in non-critical projects.
    
-   Cold standby can be considered as it is taking over the primary system in seconds; but hot standby works in redundancy in microseconds, which is super-fast.
    
-   A cold standby system requires the presence of operators to bring back the system to normalcy in event of failure; whereas a hot standby system does not require any operator intervention.
    
-   Cold standby is less reliable than hot standby systems.
    

In this way, we understand the difference between hot standby and a cold standby system.



![[Hot standby.jpg]]