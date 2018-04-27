---
title: Digital Servo Shield for Arduino SKU:DRI0027
permalink: /Digital_Servo_Shield_for_Arduino_SKU:DRI0027/
---

[thumb|300px|link=<https://www.dfrobot.com/product-958.html>|[Digital Servo Shield for Ardhuino_DRI0027](https://www.dfrobot.com/product-958.html)](/image:DRI0027.jpg "wikilink")

Introduction
------------

This board Integrates a half duplex circuit inside. That means the transmit wire from your UART is connected to all of the AX-12 servos. Hence: when you send a command over the wire then all of the servos will hear it - but because the message contains the destination servo ID then only one servo, matching that ID number, will process it.

Because of the servo can be linked by serial bus, which can connect up to 200+ servos. Each unit can feedback its position, rotation velocity, torque, current, motor temperature and so on.It can do rotating all round, and the velocity can be controlled, just act as a gear motor. This feature enables it to work as a motor of [wheeled robots](https://www.dfrobot.com/category-111.html), or tracked robots.

**Application**

* * * * *

-   Education
-   Robot Arm
-   Humanoid Robot
-   Hexapod Robot
-   Any other servo driven application

==Specification==

-   MCU:Atmega8
-   Power Supply:6.5-12V
-   Compatible with Arduino R3
-   SPI interface with Arduino(Digital 10,11,12,13)
-   Friendly using for the primary user
-   UART interface for deeper development
-   7 channels for servo connecting
-   A half duplex circuit inside
-   Board surface:Immersion Gold
-   Size:59x53mm

==Pin Out== [550px|center|Digital Servo Shield for Ardhuino_PinOut](/image:DRI0027_Pinout_update2.png "wikilink")

===More Details===

-   **POWER SUPPLY:** 6.5\~12V power supply for servos & the whole system.
-   **UART SELECT:** UART is already shorted by solder. When you use the UART FOR ATmega8 please remove solder off. [Visit Forum for more details](http://www.dfrobot.com/forum/viewtopic.php?f=8&t=1781&p=8424#p8445).
-   **UART FOR ATmega8:**This UART interface is for deeper development of the shield.You can program the atmega8 on the board with [<http://www.dfrobot.com/index.php?route=product/product&filter_name=ftdi&product_id=147>\#.UaLcBLUwfN4 FTDI].Board choose "Arduino Optiboot8 "
-   **SS SELECT FOR SPI:**Digital pin 10 in default.If you want to use other digital pins,please remove the jumper cap and connect the ss header to other Arduino digital pin.

==Connection Diagram== [550px|center|Digital Servo Shield for Ardhuino_Diagram](/image:DRI0027_Diagram.png "wikilink")

Sample Code
-----------

:{|style="width:50%; " |- |

~~~~ {.cpp}
/*
 # This Sample code is to test the Digital Servo Shield.
 # Editor : Leff
 # Date   : 2016-1-19
 # Ver    : 1.1
 # Product: Digital Servo Shield for Arduino

 # Hardwares:
 1. Arduino UNO
 2. Digital Servo Shield for Arduino
 3. Digital Servos( Compatible with AX-12,CDS55xx...etc)
 4. Power supply:6.5 - 12V

 # How to use:
 If you don't know your Servo ID number, please
 1. Open the serial monitor, and choose NewLine,115200
 2. Send command:'d',when it's finished, please close the monitor and re-open it
 3. Send the command according to the function //controlServo()//
*/

#include <SPI.h>
#include <ServoCds55.h>
ServoCds55 myservo;

int servoNum = 1;
char inputCommand ;         // a string to hold incoming data
boolean inputComplete = false;

void setup () {
  Serial.begin (115200);
  myservo.begin ();
}

void loop () {
  serialEvent();
  if (inputComplete) {
    Serial.print("Your command is: "); Serial.println(inputCommand); Serial.println("");
    controlServo(inputCommand);
    // clear the command:
    inputCommand = 0;
    inputComplete = false;
  }
}

void serialEvent() {
  while (Serial.available()) {
    char inChar = (char)Serial.read();
    if (inChar == '\n') {
      inputComplete = true;
      break;
    }
    inputCommand += inChar;
  }
}

void controlServo(char val) {
  switch (val) {
    case 'p':
      myservo.write(servoNum, 300); //ID:1  Pos:300  velocity:150
      delay(3000);
      myservo.write(servoNum, 0); //ID:1  Pos:0  velocity:150
      break;
    case 'v':
      myservo.setVelocity(200);// set velocity to 100(range:0-300) in Servo mode
      break;
    case 'm':
      myservo.rotate(servoNum, 150); //   Anti CW    ID:1  Velocity: 150_middle velocity  300_max
      delay(2000);
      myservo.rotate(servoNum, -150); //  CW     ID:1  Velocity: -150_middle velocity  -300_max
      delay(2000);
      myservo.rotate(servoNum, 0); //Stop
      myservo.Reset(servoNum);    //Only Dynamixel AX need this instruction while changing working mode
      //CDS55xx don't need this, it can switch freely between its working mode
      break;
    case 'r':
      myservo.Reset(servoNum);//Restore ID2 servo to factory Settings ( ID:1  Baud rate:1000000)
      break;
    //        case 'i':
    //        myservo.SetID(2,1);//ID:1   newID:2
    //        break;
    case 'd':  //Reset servo to ID>>servoNum. If you don't know your Servo ID, please send "d".
      Serial.print("Please wait..");
      for (int buf = 0; buf < 255; buf++) {
        myservo.SetID(buf, servoNum);
        if (buf % 50 == 0) Serial.print(".");
      }
      delay(2000);
      Serial.println("");   Serial.println("Please close the monitor and re-open it to play your servo! ");
      break;
    default:
      Serial.println("Please give me an available instruction:");
      Serial.println("  Servo mode: p_Set position; v_Set velocity.");
      Serial.println("  Motor mode: m_Rotate; v_Set velocity.");
      Serial.println("  Others: r_Reset servo to factory settings; i_Change servo ID."); Serial.println("");
  }
}
~~~~

|}

[thumb|450px|center|Send command after uploading.](/image:DRI0027_Serial_monitor_command.png "wikilink")
 [link=<http://www.dfrobot.com/>](/image:DFshopping_car1.png "wikilink") Shop from [**Smart Arduino Digital Servo Shield for Dynamixel AX**](https://www.dfrobot.com/product-958.html) or [**DFRobot Distributor**.](http://www.dfrobot.com/index.php?route=information/distributorslogo)

Category: [DFRobot](https://www.dfrobot.com/) \> [**Arduino**](https://www.dfrobot.com/category-35.html) \> [Arduino Shields](https://www.dfrobot.com/category-124.html) [category: Product Manual](/category:_Product_Manual "wikilink") [category: DRI Series](/category:_DRI_Series "wikilink") [category: Shield](/category:_Shield "wikilink")