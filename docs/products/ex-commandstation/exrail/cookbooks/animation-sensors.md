# Buttons and Switches

Buttons and switches are connected to an input vpin, usually on an expander such as an [MCP23017](?MCP23017) which provides a number of input or output pins.

## Detecting a button press

The ONBUTTON(x) sequence is started when the vpin x is made HIGH by a button press or other sensor being triggered.

```cpp
ONBUTTON(172)
  PRINT("Moooving on")
  SERVO(135,417) // move cow out of the way
  DELAY(4000)  // wait 
  THROW(3) // throw turnout 3 
  GREEN(130) // set a signal
  DONE
```

Repeated pressing of the button will be ignored until the DONE has completed.

## Detecting a switch change

The ONSENSOR(x) sequence is started when an input vpin changes state between HIGH and LOW. You will probabaly need to check the state inside the sequence using an IF(x) command.

```cpp
ONSENSOR(176)
  IF(176) 
    PRINT("Sensor 176 gone HIGH")
    GREEN(110) // set signal
  ELSE
    PRINT("Sensor 176 gone LOW")
    RED(110)  // set signal
  ENDIF
  DONE
```

Note: Switches are not suitable for controlling turnouts because the command station cant reach out a finger and change the switch position when the turnout is changed from a throttle or some other EXRAIL script. (Unless of course, you are into animating a servo to do just that!)

You can toggle a turnout with a single button

```cpp
ONBUTTON(172) TOGGLE_TURNOUT(7) DONE
```

Or have 2 buttons

```cpp
ONBUTTON(172) THROW(7) DONE
ONBUTTON(173) CLOSE(7) DONE
```
