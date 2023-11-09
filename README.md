# iCubAnkara01_resurrection
The diary to register all my steps to give a second chance in life to the iCub residing in ROMER @ METU, Ankara.

# The HitchHiker's Guideline to the iCub so far
## Quick Recap
- iCub at hand is 1.x, whereas the most recent is iCub 3. So, [the documentation](https://icub-tech-iit.github.io/documentation/icub_starter_kits/first_steps/) is not valid anymore for iCub 1.x. GitHub issues should be used for questions to IIT.
- Power settings are obtained from IIT through [an email](#day4) and is as follows.
  - xantrex XFR 35-35: **12-12.5V, 15A**
  - xantrex XFR 60-46:      **40V, 20A**
- xantrex XFR 60-46 had a trouble providing output, now it is fixed.
- Powering the motors causes S/D of power supply. This is the latest issue that I'm dealing with.

## About
**The list of devices**
- iCub 1.x
- iCub Laptop: DELL Latitude E4300 (username: icub password: icub)
- Power Supplies:
  - xantrex XFR 35-35: max 35V 35A
  - xantrex XFR 60-46: max 60V 46A  

The connection of the overall system can be seen below.

<div align="center">

| <img src="https://github.com/EbruBaglan/iCubAnkara01_resurrection/assets/71343894/6f8cf266-9de2-4d7e-b8c4-39350d4dd8c9" alt="drawing" width="600"/> |
|:--:|
| *The connection diagram* |
</div>

<!---
| ![image.jpg](https://github.com/EbruBaglan/icub_rebranded/assets/71343894/00a7ca81-beb2-42e6-baa5-95e89d9476a9) |
|:--:|
| *The connection diagram* |
-->

## Powering the iCub
The power supplies should set to the following values **BEFORE** connecting the main cord of iCub.
- xantrex XFR 35-35: **12-12.5V, 15A**
- xantrex XFR 60-46:      **40V, 20A**

The user's manuel for the power supplies:
- [xantrex XFR 35-35 User's Manual](http://wiki.icub.org/images/3/36/XANTREX_-_Power_supply_1.2Kw_XFR_35-35.pdf)
- [xantrex XFR 60-46 User's Manual](http://wiki.icub.eu/images/5/5e/XANTREX_-_Power_supply_2.8Kw_XFR_60_46.pdf)


# Log
## Day6 (11.2.23)
- Starting a discussion at iCub Tech like [this one](https://github.com/orgs/robotology/discussions/378). iCub's nickname convention is `iCub<City><Num>`, so its nickname is iCubAnkara01.
- Started an issue [here](https://github.com/robotology/icub-tech-support/issues/1671) for the motors turning on causes shutting down of the power supply. Waiting for the reply :crossed_fingers:
- 11.2.23
## Day5
- Started writing the guideline.
- S/D LED does not turn off and I think this is a problem, as the power supply wont be able to provide power to the system when S/D is on. Decided to make Functional Tests for Power Supply stated in the [xantrex XFR 60-46 User's Manual](http://wiki.icub.eu/images/5/5e/XANTREX_-_Power_supply_2.8Kw_XFR_60_46.pdf), page 43.
  Functional Tests are
  - Power-on Check: ✔️
  - Voltage Mode Operation Check: ❌ **Turning the knobs, wont increase the voltage nor amps.**
  - Current Mode Operation Check:
  - Front Panel Function Checks: ❌
    **The following won't happen for our power supply. The S/D Led just dont turn off when STANDBY Switch is its OUT position.**

    | <img src="https://github.com/EbruBaglan/iCubAnkara01_resurrection/assets/71343894/7a12c322-7b4d-43e9-ae9c-5bcd7ab497e6" alt="drawing" width="600"/> |
    |:--:|
    | *The front panel check fails because STANDBY Switch does not affect S/D Led* |

    **Also, the following(loading the power) is not possible either, so the robot won't get the power.**
 
    | <img src="https://github.com/EbruBaglan/iCubAnkara01_resurrection/assets/71343894/c5f1e8d2-39b7-4e03-afd3-d7e532b105cb" alt="drawing" width="600"/> |
    |:--:|
    | *Supplying the power to the robot fails because STANDBY Switch does not affect S/D Led* |

- Due to the above problems, I am checking User Diagnostics.

  | <img src="https://github.com/EbruBaglan/icub_rebranded/assets/71343894/69804f5d-2d81-45df-926c-69bee7b70c12" alt="drawing" width="600"/> |
  |:--:|
  | *User Diagnostics at page 72, directing to the page 63* |


- Checking page 63+64 to figure out why S/D won't turn off and how to turn off wrongly-set S/D function.

  | <img src="https://github.com/EbruBaglan/iCubAnkara01_resurrection/assets/71343894/259a6b59-a970-4c43-9f41-036a8bd57f31" alt="drawing" width="600"/> |
  |:--:|
  | *S/D Function at page 63* |

- Decided to change `Remote shutdown circuit logic` because it is remotely set to S/D ON as I understand(even if nothing is connected and nothing causes S/D ON). I checked the SW1 switch configuration and realized it has been changed from the factory default. **Factory default** and other states for switches are as follows.

  | SWITCH #  | FACTORY DEFAULT  | PREVIOUS  | NOW|
  |---|---|---|---|
  | SW1-1  | UP  |  UP | UP |
  | SW1-2  | UP  |  UP |  UP |
  | SW1-3  | DOWN  | DOWN  | DOWN  |
  | SW1-4  | DOWN  | DOWN  | DOWN  |
  | SW1-5  | DOWN  | DOWN  | DOWN  |
  | SW1-6  | DOWN  | DOWN  | DOWN  |
  | SW1-7  | **UP**  | **DOWN**  | **UP**  |
  | SW1-8  |  DOWN | DOWN  | DOWN  |

| FACTORY DEFAULT  | PREVIOUS  |
  |---|---|
  | <img src="https://github.com/EbruBaglan/iCubAnkara01_resurrection/assets/71343894/9b6a76ce-16a7-4391-b6d0-cb29b7f8b4bb" alt="drawing" width="600"/>  | <img src="https://github.com/EbruBaglan/iCubAnkara01_resurrection/assets/71343894/9b38e66d-aa39-4e37-99f9-0dd6174fb68b" alt="drawing" width="600"/> |

-  **I changed SW1-7 to ON and S/D Led problem solved!**
- Repeating the functional tests:
  - Power-on Check: ✔️
  - Voltage Mode Operation Check: ✔️
  - Current Mode Operation Check: :white_check_mark:
  - Front Panel Function Checks: ❌
-  11.1.23

## Day4
- IIT replied my email. It is as follows.

| ![space-1.jpg](https://github.com/EbruBaglan/iCubAnkara01_resurrection/assets/71343894/0aca9306-3294-4edf-a998-c36d1db4cfcc) | 
|:--:| 
| *The mail from IIT* |
- 10.30.23

## Day3
- Turns out they had iCub Laptop! Received the laptop yesterday. YARP and all others are set up already, yay!
- Documentation specifies 1 power supply providing `40V 20A` as seems below
  | <img src="https://github.com/EbruBaglan/iCubAnkara01_resurrection/assets/71343894/cd9aa4f9-11f5-45ae-b45f-425cee191ec5" alt="drawing" width="600"/> |
  |:--:|
  | *The power specs in docs* |

- But there are 2 power supplies with one of them providing max of `35V` which is `< 40V`
  | <img src="https://github.com/EbruBaglan/iCubAnkara01_resurrection/assets/71343894/f0742837-c699-47cd-87b6-7382622a8bd6" alt="drawing" width="400"/> |
  |:--:|
  | *The power supplies at hand* |
 
- Time for guidance from iCub Tech!
- 10.26.23
## Day2
- Checking [installation page](https://icub-tech-iit.github.io/documentation/sw_installation/)
- Turns out need to install [robotology-superbuild](https://github.com/robotology/robotology-superbuild)
  - Turns out I need to install [Cmake](https://cmake.org/download/) and [YCM](https://github.com/robotology/ycm) first. Check if you have cmake installed:
        ```bash
        cmake --version
        ```
  - [YCM installing](https://robotology.github.io/ycm/gh-pages/latest/manual/ycm-installing.7.html)
  - [Source installation](https://github.com/robotology/robotology-superbuild#source-installation)
  - Turns out it just creates a file to be sourced. Append it to the .bashrc file by hitting:
      ```bash
      source /home/ebrub/robotology-superbuild/build/install/share/robotology-superbuild/setup.sh
      ```
  - To use the updated `.bashrc` in your terminal you should run the following command:
      ```bash
      source ~/.bashrc
      ```
  - It may also be necessary to update the cache of the dynamic linker:
      ```bash
      sudo ldconfig
      ```
  - (Check your installation)[https://icub-tech-iit.github.io/documentation/sw_installation/check_your_installation/]
      ```bash
      ...
      ```
Resistance is futile, I need a laptop with Ubuntu 22-.
- 10.25.23
## Day1
- Cables checked, no cable lost. Though the connection scheme is different than the one in [the documentation](https://icub-tech-iit.github.io/documentation/icub_starter_kits/first_steps/). The docs show 3 different cables(power+eth+fault) exiting iCub, but the iCub here has a single output.
- Cables and power sources are cleaned.
- Power sources are put on table thanks to Harika Hanim and Umut and Mehmet.
- 10.23.23
## trial
