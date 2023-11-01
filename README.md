# icub_rebranded
The diary to register all my steps to revive the icub residing in ROMER @ METU.

# The HitchHiker's Guideline to the iCub so far
## About
**The list of devices**
- iCub 1.x
- iCub Laptop: DELL Latitude E4300 (username: icub password: icub)
- Power Supplies:
  - xantrex XFR 35-35: max 35V 35A
  - xantrex XFR 60-46: max 60V 46A  

The connection of the overall system can be seen below.

<div align="center">
  
| <img src="https://github.com/EbruBaglan/icub_rebranded/assets/71343894/00a7ca81-beb2-42e6-baa5-95e89d9476a9" alt="drawing" width="600"/> |
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


# Diary
## Day5 (11.1.23):
- Started writing the guideline.
- S/D LED does not turn off and I think this is a problem, as the power supply wont be able to provide power to the system when S/D is on. Decided to make Functional Tests for Power Supply stated in the [xantrex XFR 60-46 User's Manual](http://wiki.icub.eu/images/5/5e/XANTREX_-_Power_supply_2.8Kw_XFR_60_46.pdf), page 43.
  Functional Tests are
  - Power-on Check: ✔️
  - Voltage Mode Operation Check: ❌ **Turning the knobs, wont increase the voltage nor amps.**
  - Current Mode Operation Check:
  - Front Panel Function Checks: ❌
    **The following won't happen for our power supply. The S/D Led just dont turn off when STANDBY Switch is its OUT position.**
  
    | <img src="https://github.com/EbruBaglan/icub_rebranded/assets/71343894/e7717978-7aaf-4884-94ee-9172671cd988" alt="drawing" width="600"/> |
    |:--:|
    | *The front panel check fails because STANDBY Switch does not affect S/D Led* |


    **Also, the following(loading the power) is not possible either, so the robot won't get the power.**
 
    | <img src="https://github.com/EbruBaglan/icub_rebranded/assets/71343894/9b2a65f3-9edf-400c-ab4c-e45994996479" alt="drawing" width="600"/> |
    |:--:|
    | *Supplying the power to the robot fails because STANDBY Switch does not affect S/D Led* |

- Due to the above problems, I am checking User Diagnostics.

  | <img src="https://github.com/EbruBaglan/icub_rebranded/assets/71343894/69804f5d-2d81-45df-926c-69bee7b70c12" alt="drawing" width="600"/> |
  |:--:|
  | *User Diagnostics at page 72, directing to the page 63* |


- Checking page 63+64 to figure out why S/D won't turn off and how to turn off S/D function.

  | <img src="https://github.com/EbruBaglan/icub_rebranded/assets/71343894/e716defb-d5f2-47a0-82b1-dc956fd49af6" alt="drawing" width="600"/> |
  |:--:|
  | *S/D Function at page 63* |

- Decided to change `Remote shutdown circuit logic` because it is remotely set to S/D ON as I understand. I checked the SW1 switch configuration and realized it has been changed from the factory default. **Factory default** is shown as
  - SW1-1: UP
  - SW1-2: UP
  - SW1-3: DOWN
  - SW1-4: DOWN
  - SW1-5: DOWN
  - SW1-6: DOWN
  - **SW1-7: UP**
  - SW1-8: UP
  - 
    ![image](https://github.com/EbruBaglan/icub_rebranded/assets/71343894/ad0e20d3-fde8-47d2-8588-2de2e5e0d33a)

- However, it was changed as below in the current settings as seen below.
  - SW1-1: UP
  - SW1-2: UP
  - SW1-3: DOWN
  - SW1-4: DOWN
  - SW1-5: DOWN
  - SW1-6: DOWN
  - **SW1-7: DOWN**
  - SW1-8: DOWN
 
    ![image](https://github.com/EbruBaglan/icub_rebranded/assets/71343894/bb2f2a6c-792f-451f-8bcc-eba14902182e)

-  **I changed SW1-7 to ON and S/D Led problem solved!**
- Repeating the functional tests:
  - Power-on Check: ✔️
  - Voltage Mode Operation Check: ✔️
  - Current Mode Operation Check: :white_check_mark:
  - Front Panel Function Checks: ❌ 


## Day4 (10.30.23):
- IIT replied my email. It is as follows.

| ![space-1.jpg](https://github.com/EbruBaglan/icub_rebranded/assets/71343894/438cb177-dae2-4072-9ace-73d315d5079b) | 
|:--:| 
| *The mail from IIT* |


## Day3 (10.26.23):
 - Received the laptop yesterday. YARP and all others are set up already, yay!
 - Documentation specifies 1 power supply providing `40V 20A` as seems below ![image](https://github.com/EbruBaglan/icub_rebranded/assets/71343894/8302d2d8-a784-41c6-8980-a83c2881731a)
 - But there are 2 power supplies with one of them providing max of `35V` which is `<40V` ![image](https://github.com/EbruBaglan/icub_rebranded/assets/71343894/4852d25e-4601-448f-ba7b-acc4f4a5ae90)
 - Time for guidance from IIT Tech!

## Day2 (10.25.23):
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

## Day1 (10.23.23):
- Cables checked, no cable lost. Though the connection scheme is different, no 3 different cables, just single one
- Cables and power sources cleaned.
- Power sources are put on table thanks to Harika hanim and umut and mehmet?
- 
