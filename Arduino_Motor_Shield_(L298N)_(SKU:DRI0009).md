---
title: Arduino Motor Shield (L298N) (SKU:DRI0009)
permalink: /Arduino_Motor_Shield_(L298N)_(SKU:DRI0009)/
---

Introduction
------------

This [**2x2A DC Motor Shield for Arduino**](https://www.dfrobot.com/product-69.html) allows Arduino to drive two channel [DC motors](https://www.dfrobot.com/category-110.html). It uses a L298N chip which deliveries output current up to 2A each channel. The speed control is achieved through conventional PWM which can be obtained from Arduino’s PWM output Pin 5 and 6. The enable/disable function of the motor control is signalled by [Arduino](https://www.dfrobot.com/category-35.html) Digital Pin 4 and 7.

The Motor shield can be powered directly from [Arduino](https://www.dfrobot.com/category-35.html) or from external power source. It is strongly encouraged to use external power supply to power the motor shield.

-   Logic Control Voltage：5V (From Arduino)
-   Motor Driven Voltage：4.8～35V (From Arduino or External Power Source)
-   Logic supply current Iss：≤36mA
-   Motor Driven current Io：≤2A
-   Maximum power consumption：25W（T=75℃）
-   PWM、PLL Speed control mode
-   Control signal level:



High：2.3V≤Vin≤5V

Low：-0.3V≤Vin≤1.5V

Diagram
-------

[thumb|600px|center|Motor Shield](/image:Arduino_Shield3.png "wikilink")

**Control Mode Selection Jumpers:** The shield supports PWM and PLL(Phased Locked Loop) control Modes. The PWM mode uses E1 and E2 to generate PWM signal. The PLL mode uses M1 and M2 to generate phase control signal. [thumb|600px|center|Control Mode Selection Jumpers](/image:Arduino_Shield4.png "wikilink")

'''Motor Terminal: ''' Two DC motors are connected to blue motor terminals. The male header behide the terminals are the same as the motor terminals. [thumb|300px|center|Motor terminal](/image:Arduino_Shield5.png "wikilink") **PWRIN：** The motors can be powered by external power supply when the motor current exceeds the limits provided from the Arduino. The swith between external and Arduino power is implemented by two jumpers.

-   PWRIN: External Power
-   VIN: Arduino Power



[thumb|300px|left|The motors are powered by external power supply](/image:Arduino_Shield6.png "wikilink") [thumb|300px|right|The motors are powered by Arduino power supply](/image:Arduino_Shield7.png "wikilink")

''NOTE: When the motor shield is powered by external power source, make sure the external power source and Arduino have the same GND. ''

**Control Signal Truth Table：**

|E1|M1||E2|M2||
|---|---|---|---|---|---|
|L|X|Motor 1 Disabled|L|X|Motor 2 Disabled|
|H|H|Motor 1 Backward|H|H|Motor 2 Backward|
|PWM|X|PWM Speed control|PWM|X|PWM Speed control|

*Note：H is High level ;L is Low level ;PWM is Pulse Width Modulation signal; X is any voltage level*

Pin Allocation
--------------

|Pin|Function|
|---|--------|
|Digital 4|Motor 2 Direction control|
|Digital 5|Motor 2 PWM control|
|Digital 6|Motor 1 PWM control|
|Digital 7|Motor 1 Direction control|

{|border="1" cellspacing="0" align="center" cellpadding="5" width="400px" |+ "PLL Mode" !style="background:\#7dc2f5"|Pin !style="background:\#7dc2f5"|Function |- |align="center"|Digital 4 |align="center"|Motor 2 Enable control |- |align="center"|Digital 5 |align="center"|Motor 2 Direction control |- |align="center"|Digital 6 |align="center"|Motor 1 Direction control |- |align="center"|Digital 7 |align="center"|Motor 1 Enable control |}

[Shield diagram](http://www.shieldlist.org/dfrobot/2a-motor)

Sample Code
-----------

### PWM Speed Control

~~~~ {.cpp}
//Arduino PWM Speed Control：
int E1 = 5;
int M1 = 4;
int E2 = 6;
int M2 = 7;

void setup()
{
    pinMode(M1, OUTPUT);
    pinMode(M2, OUTPUT);
}

void loop()
{
  int value;
  for(value = 0 ; value <= 255; value+=5)
  {
    digitalWrite(M1,HIGH);
    digitalWrite(M2, HIGH);
    analogWrite(E1, value);   //PWM Speed Control
    analogWrite(E2, value);   //PWM Speed Control
    delay(30);
  }
}
~~~~

### PLL Speed Control

~~~~ {.cpp}
//Arduino PLL Speed Control：
int E1 = 4;
int M1 = 5;
int E2 = 7;
int M2 = 6;

void setup()
{
    pinMode(M1, OUTPUT);
    pinMode(M2, OUTPUT);
}

void loop()
{
  int value;
  for(value = 0 ; value <= 255; value+=5)
  {
    digitalWrite(M1,HIGH);
    digitalWrite(M2, HIGH);
    analogWrite(E1, value);   //PLL Speed Control
    analogWrite(E2, value);   //PLL Speed Control
    delay(30);
  }
}
~~~~

[image:nextredirectltr.pngGo](/image:nextredirectltr.png "wikilink") Shopping [Arduino Motor Shield (L298N) (SKU:DRI0009)](https://www.dfrobot.com/product-69.html)

Category: [DFRobot](https://www.dfrobot.com/) \> [Motors & Actuators & Drivers](https://www.dfrobot.com/category-51.html) \> [DC Motor Drivers](https://www.dfrobot.com/category-105.html) [category: Product Manual](/category:_Product_Manual "wikilink") [category: DRI Series](/category:_DRI_Series "wikilink") [category: Motor Controllers](/category:_Motor_Controllers "wikilink") [category: Shields](/category:_Shields "wikilink")