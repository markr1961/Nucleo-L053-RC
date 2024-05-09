## RC hobby servo controller using STM32L053 on Nucleo-64 board.

Project Home: https://github.com/markr1961/Nucleo-L053-RC

#### back ground
- [Control Servos With Arduino and RC Receiver/Transmiter](https://www.instructables.com/Control-Servos-with-Arduino-and-RC-receiver/)
just single channel in to drive 3 channels out. meh.
- [Building a Hobby Servo Controller – Part 1](https://community.element14.com/products/raspberry-pi/raspberrypi_projects/b/blog/posts/building-a-hobby-servo-controller-part-1) 
uses MSP430 as controller. Never got to code....
- [gihub: IntelliServo](https://github.com/alvaroferran/IntelliServo) Project aiming to transform regular hobby servos into smart ones by replacing their original boards.  

## project
compiles with IAR 7.80.4  
need to edit mpu_armv7.h/ARM_MPU_SetRegionEx() to remove __RESTRICT attribute from 3rd param  

### CPU
32 MHz
using HSI

### LED
PA5     LD2     green LED  

### Button
PC12    B1      user button (blue)  

### TIM2
generates PWM on compare 1-4.  
- pre-scaler: 128 -> 250 KHz = 4.0 uS tick.  
- period: 5000 -> 20mS cycle  
- auto-reload
- CH1: 250  +90 degrees  
- CH2: 375    0 degrees  
- CH3: 500  -90 degrees  
- CH4: 1 -  sync pulse  

### USART1
100,000 baud, 9-bit Even, 2 stop.  
used for S.Bus input.  

### USART2
115,200  
connected through debugger.

### RTC
external LSE 32,768  

