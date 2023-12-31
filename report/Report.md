# Embedded Systems Lab Report

*  Nirmal Kumar bBarik [ee23mt014@iitdh.ac.in] 
* Shiv Sharan Gauda [ee23mt025@iitdh.ac.in]
* Group: 05 
* [03/10/2023]

### Problem Statement:

Generate a 50% duty cycle waveform on TM4c123GH6PM, change the duty cycle of the signal on the press of on board user switches

procedure:
Task 1:
Create a PWM waveform with frequency = 100KHz and variable duty cycle.

The program should begin with d = 50%.
On pressing one switch the duty should be increased by 5% and on pressing other switch it should be decreased by 5%.

1. We enabled the  System Clock as source to PWM Modules using RCC and RCGC registers.
2.  Then we enabled the clock and initialize GPIO Port F accordingly.
3. After that we enabled the Interrupts on both the on-board switches.
4.  Then we  enabled the Alternate function on the desired pin, where the PWM signal were generated, using AFSEL and PCTL registers.
5. Then we disable/Turn off the PWM generator, Loaded the 'load' and 'compare' values in their respective registers,then we config the PWM genrator using the PWM_GENA(B) register, enabled the the PWM generator and gave the pwm signal to the desired pin.
6.   On the press of user switch 1(2) increase(decrease) the duty cycle, by modifying the compare value.



### Task 2:
##### Implement the same but using only 1 switch (SW1 OR SW2) – short press for d increase and long press for decrease.

1. We enabled the  System Clock as source to PWM Modules using RCC and RCGC registers.
2. Then we enabled the clock and initialized the  GPIO Port F accordingly.
3. Then we enabled the Interrupts on both the on-board switches.
4. Then we enabled the Alternate function on the desired pin, where the PWM signal were generated, using AFSEL and PCTL registers.
5. Then disable/Turn off the PWM generator, Load the 'load' and 'compare' values in their respective registers, config the PWM genrator using the PWM_GENA(B) register, enable the the PWM generator and give the pwm signal to the desired pin.
6. On the falling edge, when the user switch is pressed, turn on the systick timer and load a reload value in 'STRELOAD' register corresponding to 0.5 sec of delay.
7. On the rising edge, when the button is released, we checkd the 'COUNT_FLAG' of the systick timer, if set then we decrease the duty cycle, if not set then we increase the duty cycle of the pwm signal and turn of the systick timer.


### Measurements:
With 16MHz clock given to PWM module, to generate a 100kHz signal, we need to wait for 16MHz/100kHz clock cycles. Therefore, the load value for the PWM module is set to be 160.
To generate a PWM signal of 50 percent duty cycle, the compare value must be 160/2 = 80.
When increasing(decreasing) the duty cycle by 5% we must decrement(increment) the compare value by 8 units.

       

### Results

![Fig 1 40% duty cycle](40dut.jpg)
* 40% duty cycle

![Fig 2 45% duty cycle](45dut.jpg)
* 45% duty cycle

![Fig 3 50% duty cycle](50dut.jpg)
* 50% duty cycle

![Fig 4 55% duty cycle](55dut.jpg)
* 55% duty cycle

![Fig 5 60% duty cycle](60dut.jpg)
* 60% duty cycle

PWM signals of different duty cycle are generated.

