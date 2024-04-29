## RC hobby servo controller using STM32L053 on Nucleo-64 board.

Project Home: https://github.com/markr1961/Nucleo-L053-RC

compiles with IAR 7.80.4  
need to edit mpu_armv7.h/ARM_MPU_SetRegionEx() to remove __RESTRICT attribute from 3rd param  

## TIM2
