# Hello World Blink
A simple program to test Raspberry Pi Pico W.  Hello World, I am blinking!!!

May be a bit blinking mad at times... :smiley:

# Instructions
## VS Code
When opening this project via Visual Studio Code, make sure you scan for a kit when prompted by VS Code, and select the appropriate kit from the dropdown list.

### Debugging in VS Code
When debugging make sure you select the Cortex Debug option.


# Raspberry Pi Pico Wi-Fi LED Hello World Blink

This is a simple C code for the Raspberry Pi Pico that initializes Wi-Fi using the CYW4343 Wi-Fi/BT chipset and blinks an LED on the board.

```c
#include <stdio.h>
#include "pico/stdlib.h"
#include "pico/cyw43_arch.h"

int main() {
    stdio_init_all();
    if (cyw43_arch_init()) {
        printf("Wi-Fi init failed");
        return -1;
    }

    const uint LED_PIN = CYW43_WL_GPIO_LED_PIN;
    gpio_init(LED_PIN);
    gpio_set_dir(LED_PIN, GPIO_OUT);

    while (true) {
        cyw43_arch_gpio_put(LED_PIN, 1);
        sleep_ms(250);
        cyw43_arch_gpio_put(LED_PIN, 0);
        sleep_ms(250);
        printf("Hello, world!\nI am blinking!\n");
        sleep_ms(500);
    }
}
```

## How to Use

To use this code, follow these steps:

1. Set up your Raspberry Pi Pico development environment.
2. Create a new C project and copy the provided code into your project file.
3. Make sure you have the necessary header files (`stdio.h`, `pico/stdlib.h`, and `pico/cyw43_arch.h`) included in your project.
4. Build and flash the code onto your Raspberry Pi Pico board.
5. When the code runs, it will initialize Wi-Fi and start blinking the LED on the board while printing a message.

Make sure you have the necessary Wi-Fi and LED connections configured properly.

That's it! You now have a basic program that initializes Wi-Fi and blinks an LED on the Raspberry Pi Pico board.


