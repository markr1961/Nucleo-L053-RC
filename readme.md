## RC hobby servo controller using STM32L053 on Nucleo-64 board.

Project Home: https://github.com/markr1961/Nucleo-L053-RC

compiles with IAR 7.80.4  
need to edit mpu_armv7.h/ARM_MPU_SetRegionEx() to remove __RESTRICT attribute from 3rd param  

## CPU
32 MHz
using HSI

### LED
PA5     LD2     green LED  

### Button
PC12    B1      user button (blue)  

## TIM2
generates PWM on compare 1-4.  
- pre-scaler: 128 -> 250 KHz = 4.0 uS tick.  
- period: 5000 -> 20mS cycle  
- auto-reload
- CH1: 250  +90 degrees  
- CH2: 375    0 degrees  
- CH3: 500  -90 degrees  
- CH4: 1 -  sync pulse  

## USART1
100,000 baud, 9-bit Even, 2 stop.  
used for S.Bus input.  

## USART2
115,200  
connected through debugger.

## RTC
external LSE 32,768  