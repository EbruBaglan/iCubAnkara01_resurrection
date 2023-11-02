## Reviving the iCub 1.x: Step1 – Power Supply.
## Brief Description
Q1. xantrex XFR 60-46 goes into S/D when the motors are turned on. How to spot the cause of the problem?
Devices at Hand
----
-	iCub 1.x (version not exactly known)
-	Power Supply 1: xantrex XFR 35-35
-	Power Supply 2: xantrex XFR 60-46
-	iCub Laptop: DELL Latitude E4300

Detailed Context
-----
I have found an iCub in a research institution in Ankara, which is from around 20 years ago. Since I have done an internship at IIT, I thought of giving it a second life.
The model seems to be iCub 1.x, which the documentation does not support anymore. You can find photos below to make sure. I even made a diagram of connections to spot the exact version of it, hopefully.
(fig1. Icub, fig2. connection, fig3. diagram)
I have two power supplies at hand. From a previous mailing with iCub Tech, I received the following voltage and amp values to set.
Xantrex XFR 35-35: 12/12.5V-15A
Xantrex XFR 60-46: 40V-20A
First I set the limits as these and then I power the iCub. I have an extra switch for turning on/off the CPU and motors. I turn on CPU and no problem. But the moment I turn on the motors switch, the xantrex XFR 60-46 goes into S/D.
There is a problem with the motors and I am looking for a solution to spot the cause.
I pressed the Standby Switch to turn it off, but the light does not turn off whatever I do. I assume this is a problem since the power supply does not provide any voltage when Shutdown functionality is enabled. I found the necessary info here in the user manual. (http://wiki.icub.eu/images/5/5e/XANTREX_-_Power_supply_2.8Kw_XFR_60_46.pdf)
