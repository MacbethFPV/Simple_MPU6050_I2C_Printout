# Simple_MPU6050_I2C_Printout
   
<hr> </hr>


<p align="center">   
  
   
  
  
  ## Basic MPU6050 I2C Driver used to get Accelerometer and Gyroscope data   

</p>


<hr> </hr>

Original Author: Controller's Tech  
Original Author's Website: https://controllerstech.com/how-to-interface-mpu6050-gy-521-with-stm32/  
Original Author's Youtube video used: https://youtu.be/xxphp9wDnHA  
Modified by: Mac  
Purpose: Base for future project   
<br> </br>


## Hardware used:
  - Mac / Windows Machine to run STM32CubeIDE
  - Windows Putty / Linux Terminal to get the UART Printouts (I had the 2nd computer laying around ¯\_(ツ)_/¯ but you can use the same computer)
  - STM32F411RET6U Nucleo Board
  - MPU6050 6-axis IMU
  - CP2102 USB to TTL Adapter 
  - Qty 4: 1.25mm Dupont Female to Female Connectors

## Some guidance to use the above files:
Firstly check out Controller Tech's Youtube Video to learn how the code goes together
  1) Ensure STM32CubeIDE is Installed
  2) Start an STM32 Project
  3) Select Board, (I used the STM32F411RET6U Nucleo board)
  4) Under Connectivity, choose to enable an I2C port. 
        I used I2C1 and chose pins PB6 (I2C1_SCL) and PB7 (I2C1_SDA)
        I also set my BaudRate to 115200
  5) Under Connectivity, choose to enable a USART port. 
        I used USART1 and chose pins PA9 (USART1_TX) and PA10 (USART1_RX)
  6) After saving my project and letting the code auto generate, I added the .h and .c file to my project 
        <PROJECT_FOLDER>/Core/Inc/MPU6050.h
        <PROJECT_FOLDER>/Core/Src/MPU6050.c
  7) I would advise against copying and pasting main.c into your project, I like to pick it apart and manually 
        insert the portions that were not auto-generated by STM32CubeIde into my project
  8) Connect the CP2102 USB to TTL adapter using CP2102 GND -> Nucleo GND
                                                CP2102 RXD -> Nucleo TX (PA9)
                                                CP2102 TXD -> Nucleo RX (PA10)
                                                (May differ for your setup depending on your HW and Pin configuration)  
  Linux Commands to see MCU output using the CP2102
  ```
  $ sudo apt update
  $ sudo apt install picocom
  $ ls /dev/tty*                    #To find out what the CP2102 connected as (Mine was under "/dev/ttyUSB0")
  $ picocom -b 115200 /dev/ttyUSB   #After this I had Accel and Gyro printouts
  # Quit using CTRL+A, CTRL+Q
  ```
