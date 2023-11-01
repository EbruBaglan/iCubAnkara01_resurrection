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

| ![image.jpg](https://github.com/EbruBaglan/icub_rebranded/assets/71343894/00a7ca81-beb2-42e6-baa5-95e89d9476a9) |
|:--:|
| *The connection diagram* |

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
  - Functional Tests are
    - Power-on Check: :heavy_check_mark:
    - Voltage Mode Operation Check: :heavy_check_mark:
    - Current Mode Operation Check
    - Front Panel Function Checks

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
