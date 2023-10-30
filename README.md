# icub_rebranded
The diary to register all my steps to revive the icub residing in ROMER @ METU.

## Day4 (10.30.23):
- IIT replied my email. It is as follows.


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
