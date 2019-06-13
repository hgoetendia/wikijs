<!-- TITLE: Pics -->
<!-- SUBTITLE: A quick summary of Pics -->

# Header
Positive voltages:
Vcc- Positive supply voltage of a Bipolar Junction Transistor.
Vdd- Positive supply voltage of A Field Effect Transistor

Negative voltages/ground:
Vee- Negative supply voltage of a Bipolar Junction Transistor.
Vss- Negative supply voltage of A Field Effect Transistor.

# Basic circuit:

![Pic 18 F 4550 Usb Communication](/uploads/electronics/pic-18-f-4550-usb-communication.jpg "Pic 18 F 4550 Usb Communication")


#Data sheets, common PICS (PIC18F2550, PIC18F4550)

![Pic 18 F 2550](/uploads/electronics/pic-18-f-2550.jpg "Pic 18 F 2550")


![Pic 18 F 4550](/uploads/electronics/pic-18-f-4550.jpg "Pic 18 F 4550")



# Hello world program using CCS.


```c_cpp
#include <main.h>

void main()
{
   while(TRUE)
   {
       output_low(PIN_B7);
       delay_ms(1000);
       output_high(PIN_B7);
       delay_ms(1000);
   }
}
```
