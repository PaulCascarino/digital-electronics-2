# digital-electronics-2
## works by Paul Cascarino

### Read me


*student in ESIEE Paris and VUT Brno*
**until the 22 December**

- Work begin in october
- Continue in november
- Finish in december

1. Work begin in october
2. Continue in november
3. Finish in december

my school :
[esiee](https://www.esiee.fr/)

Table of dates :
|     Date	|      Work     |
| ------------- | ------------- |
|    October    |     begin     |
|    November   |    continue   |
|    December   |      end      |

List of C source code :
```
```c
int main(void)
{
    // Set pin where on-board LED is connected as output
    pinMode(LED_GREEN, OUTPUT);

    // Infinite loop
    while (1)
    {
        // Generate a lettre `A` Morse code

        digitalWrite(LED_GREEN, HIGH);
        delay(1000);
        digitalWrite(LED_GREEN, LOW);
        delay(2000);
        digitalWrite(LED_GREEN, HIGH);
        delay(3000);
        digitalWrite(LED_GREEN, LOW);
        delay(5000);

    }

    // Will never reach this
    return 0;
}
```

```
