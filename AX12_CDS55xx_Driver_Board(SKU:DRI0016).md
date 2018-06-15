---
title: AX12 CDS55xx Driver Board(SKU:DRI0016)
permalink: /AX12_CDS55xx_Driver_Board(SKU:DRI0016)/
---

Introduction
------------

AX-12 CDS55xx Driver Board makes it possible for you to directly connect AX-12/CDS55xx Servos to your arduino controllers. The interface of this driver board is just using a UART port. The CDS series robot servo and the AX-12 servos can be linked by serial bus, this means you can connect 200+ servos.

The CDS55xx Driver Board Integrates a half duplex and a voltage regulator circuit inside. The voltage regulator is used to manage the power supply for your servos, and the half duplex mode means that the transmit wire from your UART is connected to all of the AX-12 servos. Hence: when you send a command over the wire then all of the servos will hear it - but because the message contains the destination servo ID then only one servo, matching that ID number, will process it. If the message requires a response then it is sent back down the same wire from the servo back to your AX-12/CDS55xx Driver Board.

### Applications

[Robot Arm](https://www.dfrobot.com/category-163.html)
Humanoid Robot
[hexapod Robot](https://www.dfrobot.com/product-515.html)
Any other servo driven application

### Specification

Power supply: 7-16v
Interface for Arduino: UART
Size:50x25x12mm

### Shipping List

AX-12 CDS55xx Driver Board(1 unit)

Connection Diagrams
-------------------

[400px|thumb|center|Arduino connection diagram](/File:Connect_DRI0016-CDS-Arduino.png "wikilink") Connect: GND-GND, Tx-Tx, Rx-Rx
It is recommended that you use a 7.4V LiPo battery with this servo driver board. But you may also use a power adapter for stationary applications
[400px|thumb|center|FTDI Board connection to PC](/File:Connect_DRI0016-CDS-PC.png "wikilink") Using an FTDI board it is possible to use the servo controller directly from your PC.
Connect: GND-GND, Tx-TxO, Rx-RxI
It is recommended that you use a 7.4V LiPo battery with this servo driver board. But you may also use a power adapter for stationary applications

Documents
---------

[CDS55xx Arduino Library](http://www.dfrobot.com/image/data/DRI0016/Arduino%20CDS55xx%20library.rar)
[Software(Windows)](http://www.dfrobot.com/image/data/DRI0016/RobotServoTerminal2.1.10.402_Setup.exe)
[CDS Servo product page](http://www.dfrobot.com/index.php?route=product/product&filter_name=cds&product_id=373)
[image:nextredirectltr.pngGo](/image:nextredirectltr.png "wikilink") Shopping [AX12 CDS55xx Driver Board(SKU:DRI0016)](https://www.dfrobot.com/product-579.html)
[category: Product Manual](/category:_Product_Manual "wikilink") [category: DRI Series](/category:_DRI_Series "wikilink")


![123](http://www.lattepanda.com/wp-content/uploads/2016/05/plug-USB.jpg)
