# Lab 3: Paul CASCARINO
### Overflow times

1. Complete table with overflow times.

   | **Module** | **Number of bits** | **1** | **8** | **32** | **64** | **128** | **256** | **1024** |
   | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
   | Timer/Counter0 | 8  | 16u | 128u | 512u | 1024u | 2048u | 4096u | 16384u|
   | Timer/Counter1 | 16 |  32u|  256u| 1024u | 2048u| 4096 |10192u   |32768u|
   | Timer/Counter2 | 8  | 16u | 128u | 512u | 1024u | 2048u | 4096u | 16384u|

### Interrupts

2. In `timer.h` header file, define macros also for Timer/Counter2. Listing of part of the header file with settings for Timer/Counter2. Always use syntax highlighting, meaningful comments, and follow C guidelines:

   ```c
   #ifndef TIMER_H
    # define TIMER_H

    /* Includes ----------------------------------------------------------*/
    #include <avr/io.h>


    /* Defines -----------------------------------------------------------*/
    /**
     * @name  Definitions for 16-bit Timer/Counter1
     * @note  t_OVF = 1/F_CPU * prescaler * 2^n where n = 16, F_CPU = 16 MHz
     */
    /** @brief Stop timer, prescaler 000 --> STOP */
    #define TIM1_stop()           TCCR1B &= ~((1<<CS12) | (1<<CS11) | (1<<CS10));
    /** @brief Set overflow 4ms, prescaler 001 --> 1 */
    #define TIM1_overflow_4ms()   TCCR1B &= ~((1<<CS12) | (1<<CS11)); TCCR1B |= (1<<CS10);
    /** @brief Set overflow 33ms, prescaler 010 --> 8 */
    #define TIM1_overflow_33ms()  TCCR1B &= ~((1<<CS12) | (1<<CS10)); TCCR1B |= (1<<CS11);
    /** @brief Set overflow 262ms, prescaler 011 --> 64 */
    #define TIM1_overflow_262ms() TCCR1B &= ~(1<<CS12); TCCR1B |= (1<<CS11) | (1<<CS10);
    /** @brief Set overflow 1s, prescaler 100 --> 256 */
    #define TIM1_overflow_1s()    TCCR1B &= ~((1<<CS11) | (1<<CS10)); TCCR1B |= (1<<CS12);
    /** @brief Set overflow 4s, prescaler // 101 --> 1024 */
    #define TIM1_overflow_4s()    TCCR1B &= ~(1<<CS11); TCCR1B |= (1<<CS12) | (1<<CS10);

    /** @brief Enable overflow interrupt, 1 --> enable */
    #define TIM1_overflow_interrupt_enable()  TIMSK1 |= (1<<TOIE1);
    /** @brief Disable overflow interrupt, 0 --> disable */
    #define TIM1_overflow_interrupt_disable() TIMSK1 &= ~(1<<TOIE1);


    /**
     * @name  Definitions for 8-bit Timer/Counter0
     * @note  t_OVF = 1/F_CPU * prescaler * 2^n where n = 8, F_CPU = 16 MHz
     */
    /** @brief Stop timer, prescaler 000 --> STOP */
    #define TIM0_stop()           TCCR0B &= ~((1<<CS02) | (1<<CS01) | (1<<CS00));
    /** @brief Set overflow 4ms, prescaler 001 --> 1 */
    #define TIM0_overflow_4ms()   TCCR0B &= ~((1<<CS02) | (1<<CS01)); TCCR10B |= (1<<CS00);
    /** @brief Set overflow 33ms, prescaler 010 --> 8 */
    #define TIM0_overflow_33ms()  TCCR0B &= ~((1<<CS02) | (1<<CS00)); TCCR0B |= (1<<CS01);
    /** @brief Set overflow 262ms, prescaler 011 --> 64 */
    #define TIM0_overflow_262ms() TCCR0B &= ~(1<<CS02); TCCR0B |= (1<<CS01) | (1<<CS00);
    /** @brief Set overflow 1s, prescaler 100 --> 256 */
    #define TIM0_overflow_1s()    TCCR0B &= ~((1<<CS01) | (1<<CS00)); TCCR0B |= (1<<CS02);
    /** @brief Set overflow 4s, prescaler // 101 --> 1024 */
    #define TIM0_overflow_4s()    TCCR0B &= ~(1<<CS01); TCCR0B |= (1<<CS02) | (1<<CS00);

    /** @brief Enable overflow interrupt, 1 --> enable */
    #define TIM0_overflow_interrupt_enable()  TIMSK0 |= (1<<TOIE0);
    /** @brief Disable overflow interrupt, 0 --> disable */
    #define TIM0_overflow_interrupt_disable() TIMSK0 &= ~(1<<TOIE0);



    /**
     * @name  Definitions for 8-bit Timer/Counter2
     * @note  t_OVF = 1/F_CPU * prescaler * 2^n where n = 8, F_CPU = 16 MHz
     */
    /** @brief Stop timer, prescaler 000 --> STOP */
    #define TIM2_stop()           TCCR2B &= ~((1<<CS22) | (1<<CS21) | (1<<CS20));
    /** @brief Set overflow 4ms, prescaler 001 --> 1 */
    #define TIM2_overflow_4ms()   TCCR2B &= ~((1<<CS22) | (1<<CS21)); TCCR22B |= (1<<CS20);
    /** @brief Set overflow 33ms, prescaler 010 --> 8 */
    #define TIM2_overflow_33ms()  TCCR2B &= ~((1<<CS22) | (1<<CS20)); TCCR2B |= (1<<CS21);
    /** @brief Set overflow 262ms, prescaler 011 --> 64 */
    #define TIM2_overflow_262ms() TCCR2B &= ~(1<<CS22); TCCR0B |= (1<<CS21) | (1<<CS20);
    /** @brief Set overflow 1s, prescaler 100 --> 256 */
    #define TIM2_overflow_1s()    TCCR2B &= ~((1<<CS21) | (1<<CS20)); TCCR2B |= (1<<CS22);
    /** @brief Set overflow 4s, prescaler // 101 --> 1024 */
    #define TIM2_overflow_4s()    TCCR2B &= ~(1<<CS21); TCCR2B |= (1<<CS22) | (1<<CS20);

    /** @brief Enable overflow interrupt, 1 --> enable */
    #define TIM0_overflow_interrupt_enable()  TIMSK2 |= (1<<TOIE2);
    /** @brief Disable overflow interrupt, 0 --> disable */
    #define TIM0_overflow_interrupt_disable() TIMSK2 &= ~(1<<TOIE2);


    /** @} */

    #endif
   ```
   
   code : 
   
   ```c
      #define LED_GREEN PB5  // Arduino Uno on-board LED
    #define LED_RED PB0    // External active-low LED


    /* Includes ----------------------------------------------------------*/
    #include <avr/io.h>         // AVR device-specific IO definitions
    #include <avr/interrupt.h>  // Interrupts standard C library for AVR-GCC
    #include <gpio.h>           // GPIO library for AVR-GCC
    #include "timer.h"          // Timer library for AVR-GCC


    /* Function definitions ----------------------------------------------*/
    /**********************************************************************
     * Function: Main function where the program execution begins
     * Purpose:  Toggle two LEDs using the internal 8- and 16-bit 
     *           Timer/Counter.
     * Returns:  none
     **********************************************************************/
    int main(void)
    {
        // Set pins where LEDs are connected as output
        GPIO_mode_output(&DDRB, LED_GREEN);
        GPIO_mode_output(&DDRB, LED_RED);

        // Configuration of 16-bit Timer/Counter1 for LED blinking
        // Set the overflow prescaler to 262 ms and enable interrupt
        TIM1_overflow_1s();
        TIM1_overflow_interrupt_enable();

        TIM0_overflow_33ms();
        TIM0_overflow_interrupt_enable();

        // Enables interrupts by setting the global interrupt mask
        sei();

        // Infinite loop
        while (1)
        {
            /* Empty loop. All subsequent operations are performed exclusively 
             * inside interrupt service routines, ISRs */
        }

        // Will never reach this
        return 0;
    }


    /* Interrupt service routines ----------------------------------------*/
    /**********************************************************************
     * Function: Timer/Counter1 overflow interrupt
     * Purpose:  Toggle on-board LED.
     **********************************************************************/
    ISR(TIMER1_OVF_vect)
    {
        PORTB = PORTB ^ (1<<LED_GREEN);
    }
    ISR(TIMER0_OVF_vect)
    {

        uint8_t no_of_overflow = 0;

        no_of_overflow++;

        if(no_of_overflow >=60)
          PORTB = PORTB ^ (1<<LED_RED);
          no_of_overflow =0;
    }
    ISR(TIMER2_OVF_vect)
    {

        uint8_t no_of_overflow = 0;

        no_of_overflow++;

        if(no_of_overflow >=60)
          PORTB = PORTB ^ (1<<LED_RED);
          no_of_overflow =0;
    }
  
   ```
   
