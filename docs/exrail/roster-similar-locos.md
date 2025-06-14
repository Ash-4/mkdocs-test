# Roster for Similar Sound Locos

The ROSTER command in EXRAIL can be tedious if you have several sound locos with the same function settings. Using a preprocessor definition saves typing.

```cpp
ROSTER(1201,"Red class 99","light/*horn/flash/bang/wallop/squeal/honk") 
ROSTER(1202,"Green class 99","light/*horn/flash/bang/wallop/squeal/honk") 
```
  
Can be simplified by pre-defining the functions:

```cpp
#define CLASS99F "light/*horn/flash/bang/wallop/squeal/honk" 
ROSTER(1201,"Red class 99",CLASS99F) 
ROSTER(1202,"Green class 99",CLASS99F) 
```
  
This technique is particularly useful for rostering DC tracks where the function keys are related to PWM frequency:

```cpp
#define DCFuncs"/////////////////////////////FQ490 Hz/FQ3400 Hz/FQ62500 Hz"
ROSTER(1225,"DC TRACK B 1225",DCFuncs)
ROSTER(1226,"DC TRACK C 1226",DCFuncs)
```

It is also possible to utilise the compiler rule that "Hello" "Sailor" is treated as "HelloSailor". This means that common functions can be used with loco specific additions.

```cpp
#define CommonFuncs "light/*horn" 
ROSTER(1201,"Noisy class 99",CommonFuncs "/flash/bang/wallop/squeal/honk") 
ROSTER(1202,"Quieter class 99",CommonFuncs) 
```
