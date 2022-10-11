# Lab 2: PAUL CASCARINO

### GPIO control registers

1. Complete the table for DDRB and PORTB control register values.

   | **DDRB** | **PORTB** | **Direction** | **Internal pull-up resistor** | **Description** |
   | :-: | :-: | :-: | :-: | :-- |
   | 0 | 0 | input | no | Tri-state, high-impedance |
   | 0 | 1 | input | no/yes | Tri-state, high-impedance |
   | 1 | 0 | output | no | Push-pull Zero Output|
   | 1 | 1 | output | no | Push-pull Zero Output|
   
```
#define LED_GREEN PB5   // PB5 is AVR pin where green on-board LED
                        // is connected
#define LED_RED PB0     // External active-low LED
#define SHORT_DELAY 250 // Delay in milliseconds
#ifndef F_CPU
# define F_CPU 16000000 // CPU frequency in Hz required for delay funcs
#endif

/* Includes ----------------------------------------------------------*/
#include <avr/io.h>     // AVR device-specific IO definitions
#include <util/delay.h> // Functions for busy-wait delay loops


// -----
// This part is needed to use Arduino functions but also physical pin
// names. We are using Arduino-style just to simplify the first lab.
//#include "Arduino.h"
//#define PB5 13          // In Arduino world, PB5 is called "13"
//#define PB0 8
// -----


/* Function definitions ----------------------------------------------*/
/**********************************************************************
 * Function: Main function where the program execution begins
 * Purpose:  Toggle LEDs and use delay library.
 * Returns:  none
 **********************************************************************/

#include <gpio.h>
int main(void)
{
    uint8_t led_value = 0;  // Local variable to keep LED status

    // Set pin where on-board LED is connected as output
    //pinMode(LED_GREEN, OUTPUT);
    // Set second pin as output
    //pinMode(LED_RED, OUTPUT);


    //DDRB = DDRB | (1<<LED_GREEN);/////////////////////

    //DDRB = DDRB | (1<<LED_RED);

    GPIO_mode_output(&DDRB,LED_GREEN);
    GPIO_mode_output(&DDRB,LED_RED);

    // Infinite loop
    while (1)
    {
        // Turn ON/OFF on-board LED ...
        //digitalWrite(LED_GREEN, led_value);
        // ... and external LED as well
        //digitalWrite(LED_RED, led_value);

       // PORTB = PORTB | (1<<LED_GREEN);

        //PORTB = PORTB | (1<<LED_RED);

        // Pause several milliseconds
        _delay_ms(SHORT_DELAY);

        // Change LED value
        if (led_value == 0){
            led_value = 1;
            GPIO_write_high(&PORTB,LED_GREEN);
            GPIO_write_high(&PORTB,LED_RED);}


        else{
            led_value = 0;
            //PORTB = PORTB & ~(1<<LED_GREEN);
            //PORTB = PORTB & ~(1<<LED_RED);

            GPIO_write_low(&PORTB,LED_GREEN);
            GPIO_write_low(&PORTB,LED_RED);}
    }

    // Will never reach this
    return 0;
}
```

### GPIO library

2. Complete the table with code sizes from three versions of the blink application.

   | **Version** | **Size [B]** |
   | :-- | :-: |
   | Arduino-style     | 2.81 kb |
   | Registers         | 3.37 kb  |
   | Library functions | 2.4 kb |

### Traffic light

3. Scheme of traffic light application with one red/yellow/green light for cars, one red/green light for pedestrians, and one push button. Connect AVR device, LEDs, resistors, push button (for pedestrians), and supply voltage. The image can be drawn on a computer or by hand. Always name all components and their values!

[schemaPaul](schemaPaul.jpg)
doesn't work
here a link : 
https://photos.app.goo.gl/sRcjfbftJoDFZwrG7
