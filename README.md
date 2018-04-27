# 菜鸟教程 Git 测试
第一次内容修改

<p>10 Segment LED Bar Graph (SKU:FIT0188)</p>
<p>10 Segment LED Bar Graph Contents [hide] 1 Introduction 1.1 Applications 1.2 Specification 1.3 Shipping List 2 Connection Diagram 3 Sample Code Introduction These 10 segment bar graph LEDs have many uses. With a compact footprint, and a simple hookup, they are easy for prototyping or finished products. Essentially, they are 10 individual red LEDs housed together.</p>
<p>Applications Audio equipment Instrument panels Digital readout display Signal strength display Power status display Art display Specification Forward Current (Per Segment): 25mA Max Reverse Voltage: 5v 10 segment bar Color: Super Bright Red Industrial standard size Low power consumption Categorized for luminous intensity Shipping List 10 segment led bar graph - Red (1 unit) Connection Diagram</p>
<p>10 Segment LED Bar Graph Connection Please note that the connection diagram shows the pins connected in reverse order for the sake of clarity. When you run the sample code included here you might notice a reverse order sequence. If you wish to wire the LEDs in the correct order you should wire: Arduino D2 to PIN1 Arduino D3 to PIN2 Arduino D4 to PIN3 Arduino D5 to PIN4 and so on…</p>
<p>Alternatively you could modify the sample code to operate in the expected order.</p>
<p>Sample Code // # // # Editor : Lauren from DFRobot // # Date : 19.03.2012</p>
<p>// # Product name: 10 Segment LED Bar Graph // # Product SKU : FIT0188 // # Version : 1.0</p>
<p>// # Description: // # The sketch for using the 10 Segment LED Bar Graph with prototype shield</p>
<p>// # Connection: // # LED Bar positive pins – Arduino digital pins through a 1K resistor // # LED Bar negative pins – GND</p>
<p>const int ledPin[10] = { 2,3,4,5,6,9,10,11,12,13}; // the number of the LED pins int ledState = 0;</p>
<p>void setup() { Serial.begin(9600); // set the digital pin as output: for(int i = 0; i &lt; 10 ;i ++){ pinMode(ledPin[i], OUTPUT); digitalWrite(ledPin[i], LOW);<br />
} ledState = 1; display(ledState); delay(100); }</p>
<p>void loop() { for(int i = 0; i &lt; 9; i++){ ledState = ledState &lt;&lt; 1; display(ledState); delay(50); Serial.println(ledState,BIN); } for(int i = 9; i &gt; 0; i–){ ledState = ledState &gt;&gt; 1; display(ledState); delay(50); Serial.println(ledState,BIN); } }</p>
<p>void display(int sat){ for(int i = 0; i &lt; 10 ;i ++){ digitalWrite(ledPin[i],bitRead(ledState,i)); } }</p>
