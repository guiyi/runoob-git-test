<h2 id="overview">Overview</h2>
<p>DFRobot sensors are designed<a href="image:sensors_for_arduino1.png" title="wikilink">thumb</a><a href="image:sensors_for_arduino2.png" title="wikilink">thumb</a>==DFRobot Ambient Light Sensor==<a href="image:sensors_for_arduino3.png" title="wikilink">thumb</a>====Introduction====The <em>DFRobot Ambient Light Sensor</em> works with Cds Photoresistor and allows you to have a DC Voltage output depending on the brightness of lights. Dark has a low value. The sensor can be used to detect the intensity of ambient light.<br />Ambient light sensor pin definitions are#output#complex#power====Specification====*Detects ambient light density*Works with Cds Photoresistor*Analog voltage output: 0 to 5 Vdc *Suitable supply voltage: +3 to 5Vdc*Interface with microcontrollers and logic circuits*Standard 3-pin PCB connector==DFRobot Capacitive Touch Sensor==<a href="image:sensors_for_arduino4.png" title="wikilink">thumb</a>====Introduction====This is the <em>DFRobot Capacitive Touch Sensor</em>. This sensor can sense the human body and metal, when they touch the sensor. In addition to this, the detection works even when separated by plastic, glass and other materials. In combination with arduino boards, the sensors can be used to create very interesting and an interactive projects.<br />Touch switch pin definitions are#output#power supply#ground====Specification====*Plug &amp; Play*Can sense the human body and metal*Works well with arduino boards*Weight: 0.030 grams==DFRobot Digital Vibration Sensor==<a href="image:sensors_for_arduino5.png" title="wikilink">thumb</a>====Introduction====The <em>DFRobot Digital Vibration Sensor</em> is a digital Plug and Play sensor blocks. It has vibration switch digital input module and dedicated sensor expansion boards with the Arduino in combination. It can sense the weak vibration signals, which can be realized with the shock interaction with relevant works.<br /><strong>Product Performance:</strong>*The conductive pin will make an instant turn-on (ON) state when touched by the outside force to achieve the proper vibration force, or an appropriate speed from the (partial) energy.* No direction, any angle may burst.* The switch is suitable for small-current circuit (secondary circuit) or (IC) of the trigger.* At room temperature and normal use the next switch service life is up to 10 million times (times/1sec).====Specification====*On-Time: 0.1ms*Open circuit resistance: 10Mohm==DFRobot Grayscale Sensor==<a href="image:sensors_for_arduino6.png" title="wikilink">thumb</a>====Introduction====The <em>DFRobot Grayscale Sensor</em> is an analog sensor. It is a special sensor with arduino expansion boards. The Gray-scale sensor interface uses PH 2.0 socket. The power supply needs the same controller, typically for 3.3V or 5V. The definition of gray-scale sensor pin is#output#complex#power====Specification====*Analog sensors*Uses PH 2.0 socket*Special sensor with Arduino expansion boards==DFRobot LM35 Linear Temperature Sensor==<a href="image:sensors_for_arduino7.png" title="wikilink">thumb</a>====Introduction====The <em>DFRobot LM35 Linear Temperature Sensor</em> is based on the semiconductor LM35 temperature sensor. The DFRobot LM35 Linear Temperature Sensor can be used to detect ambient air temperature. This sensor is produced by National Semiconductor Corporation and offers a functional range between -40 degree Celsius to 150 degree Celsius. Sensitivity is 10mV per degree Celsius. The output voltage is proportional to the temperature.<br />It is commonly used as a temperature measurement sensors. It includes thermocouples, platinum resistance, thermal resistance and temperature semiconductor chips, which commonly used in high temperature measurement thermocouples. Platinum resistance temperature used in the measurement of 800 degrees Celsius, while the thermal resistance and semiconductor temperature sensor suitable for measuring the temperature of 100-200 degrees or below, in which the application of a simple semiconductor temperature sensor has good linearity and high sensitivity. The LM35 linear temperature sensor and sensor-specific expansion of Arduino board, in combination, can be very easy to achieve.The LM35 linear temperature sensor pin definitions:#output#complex#power====Specification====*Based on the semiconductor LM35 temperature sensor*Can be used to detect ambient air temperature*Sensitivity: 10mV per degree Celcius* Functional range: -40 degree Celsius to 150 degree Celsius==DFRobot Magnetic Induction Sensor==<a href="image:sensors_for_arduino8.png" title="wikilink">thumb</a>====Introduction====This is the <em>DFRobot Magnetic Induction Sensor</em>. It senses the magnetic materials within a detection range up to about 3cm. The detection range and the strength of the magnetic field are proportional. The output is digital on/off. The definition of magnetic induction sensor pin is#output#power supply#ground.This sensor uses the SFE Reed Switch - Magnetic Field Sensor.====Specification====*Senses magnetic materials*Detection range: up to 3cm*Output: digital on/off*Detection range and magnetic field strength are proportional==DFRobot Digital Push Button==<a href="image:sensors_for_arduino9.png" title="wikilink">thumb</a>====Introduction====This is a big button which gives the first touch of the physical world. Simply plug to IO expansion board to finish your first taste of Arduino.====Specification====*Digital push button sensor*Easy to 'plug and play'* Large button keypad and high-quality first-class hat*Able to achieve very interesting and an interactive work*Big button module pin definition:#output#power supply#way==DFRobot Tilt Sensor==<a href="image:sensors_for_arduino10.png" title="wikilink">thumb</a>====Introduction====The <em>DFRobot Tilt Sensor</em> is a digital mercury-based tilt switch that is either closed, disconnected or open. The module is based on the number of mercury switches. The mercury flows to the low-lying and could therefore be used as a simple tilt sensor. The dedicated sensor expansion boards with the Arduino, in combination, can achieve very interesting and an interactive work.The Mercury switch module pin definitions are:#output#power supply#ground.<em>Note: Mercury is a toxic substance, please be careful to avoid breaking the glass case.</em>====Specification====*Digital mercury-based tilt switch*Can be used as a simple tilt sensor*Interesting and interactive work*Pin definitions:*Able to achieve very interesting and an interactive work*Big button module pin definition:#output#power supply#ground==DFRobot Gas Sensor======Introduction========Specification====</p>
<pre class="sourceCode cpp"><code class="sourceCode cpp">Arduino Sample Codevoid setup(){  Serial.begin(<span class="dv">9600</span>); <span class="co">//}void loop(){int val;val=analogRead(0);传感器接于模拟口0Serial.println(val,DEC);//从串口发送声音强度并换行delay(100);}</span></code></pre>
<p><a href="image:nextredirectltr.png" title="wikilink">image:nextredirectltr.pngGo</a> Shopping <a href="https://www.dfrobot.com/product-110.html"><strong><u>Sensor Set For Arduino (SKU: DFR0018)</u></strong></a>Category: <strong><u><a href="https://www.dfrobot.com/">DFRobot</a></u></strong> &gt; <strong><u><a href="https://www.dfrobot.com/category-156.html">Sensors &amp; Modules</a></u></strong>  &gt;  <strong><u><a href="https://www.dfrobot.com/category-36.html">Sensors</a></u></strong> &gt; <strong><a href="https://www.dfrobot.com/category-227.html"><u>Sensor Kit</u></a></strong><a href="category:_Product_Manual" title="wikilink">category: Product Manual</a><a href="category:_DFR_Series" title="wikilink">category: DFR Series</a><a href="category:_Robots-kits" title="wikilink">category: Robots-kits</a><a href="category:_source" title="wikilink">category: source</a><a href="category:_Diagram" title="wikilink">category: Diagram</a></p>---
title: Sensor Set For Arduino (SKU: DFR0018)
permalink: /Sensor_Set_For_Arduino_(SKU:_DFR0018)/
---
