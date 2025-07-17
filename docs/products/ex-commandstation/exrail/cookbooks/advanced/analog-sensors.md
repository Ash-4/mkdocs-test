# Analog sensors  

Sensors that read analog values are comparatively rare for model railway use but are sometimes used to detect a binary state depending on the current detected by a sensor.

[ADS1113](https://www.ti.com/product/ADS1113) and [ADS1114](https://www.ti.com/product/ADS1113) are restricted to 1 input.  [ADS1115](https://www.ti.com/product/ADS1115) has 4 way multiplexer which allows any of four input pins to be read by its ADC.

The ADS111x is set up so that the maximum input voltage of 5V (when Vss=5V) gives a reading of 32767*(5.0/6.144) = 26666.

A device like the above is defined in EXRAIL by

```cpp
HAL(ADS1113,300, 1, 0x48);  // single-input ADS1113 on vpin 300
// or
HAL(ADS1115,300, 4, 0x48);  // four-input ADS1115 on pins 300..303
```

To monitor a vpin like this for a binary decision

```cpp
AUTOSTART SEQUENCE(99)
ATGTE(300,1000) // wait intil vpin 300 reaches 1000 or greater
... do something
ATGTE(300,950) // wait until it drops back below 950
.. do something else
FOLLOW(99) // continue monitoring
```
