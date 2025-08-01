# TCA8418 keyboard scanner

The TCA8418 IC from Texas Instruments is a low cost and very capable GPIO and keyboard scanner. Used as a keyboard scanner, it has 8 rows of 10 columns of IO pins which allow encoding of up to 80 buttons. The IC is available on an Adafruit board with Qwiic I2C interconnect called the [Adafruit TCA8418 Keypad Matrix and GPIO Expander Breakout](https://www.adafruit.com/product/4918).

The great advantage of this IC is that the keyboard scanning is done continuously, and it has a 10-element event queue, so even if you don't get to the interrupt immediately, keypress and release events will be held for you. Since it's I2C its very easy to use with any DCC-EX command station.

The TCA8418 driver presently configures the IC in the full 8x10 keyboard scanning mode, and then maps each key down/key up event to the state of a single vpin for extremely easy use from within EX-RAIL and JMRI as each key looks like an individual sensor.

This is ideal for mimic panels where you may need a lot of buttons, but with this board you can use just 18 wires to handle as many as 80 buttons.

By adding a simple HAL statement to myAutomation.h it creates between 1 and 80 buttons it will report back.

```cpp
HAL(TCA8418, firstVpin, numPins, I2CAddress, interruptPin)
```

For example:

```cpp
HAL(TCA8418, 300, 80, 0x34)
```

Creates VPINs 300-379 which you can monitor with EX-RAIL, JMRI sensors etc.

With an 8x10 key event matrix, the events are numbered using the Rn row pins and Cn column pins as such:

```console
     C0  C1  C2  C3  C4  C5  C6  C7  C8  C9
    ========================================
 R0|  0   1   2   3   4   5   6   7   8   9
 R1| 10  11  12  13  14  15  16  17  18  19
 R2| 20  21  22  23  24  25  26  27  28  29
 R3| 30  31  32  33  34  35  36  37  38  39
 R4| 40  41  42  43  44  45  46  47  48  49
 R5| 50  51  52  53  54  55  56  57  58  59
 R6| 60  61  62  63  64  65  66  67  68  69
 R7| 70  71  72  73  74  75  76  77  78  79
```

So if you start with the first pin definition being VPIN 300, R0/C0 will be 300 + 0, and R7/C9 will be 300+79 or 379.

And if needing an Interrupt pin to speed up operations:

```cpp
HAL(TCA8418, 300, 80, 0x34, 21)
```

*This is not for CSB1 which has no spare pins for interrupts.*

Note that using an interrupt pin speeds up button press acquisition considerably (less than a millisecond vs 10-100), but even with interrupts enabled the code presently checks every 100ms in case the interrupt pin becomes disconnected. Use any available Arduino pin for interrupt monitoring.
