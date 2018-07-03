<p>[category:_Source|category: Source]] [[category:_DFRobot|category: DFRobot]]-- { style=width:65%;</p>

<p><embed src="DFR0202.jpg300pxthumblink=https:_www.dfrobot.com_product-780.html[https:_www.dfrobot.com_product-780.html_8x8_LED_RGB_Matrix_(SKU:DFR0202)" title="fig:File:DFR0202.jpg300pxthumblink=https://www.dfrobot.com/product-780.html[https://www.dfrobot.com/product-780.html 8x8 LED RGB Matrix (SKU:DFR0202)" />]</p>

<h2 id="introduction">Introduction</h2>

<p>A dot matrix display is a display device used to display information on machines, clocks, railway departure indicators and many other devices requiring a simple display device of limited resolution.Even if the 8x8 RGB led dot matrix is commonly used in lots of applications, but it require too much digital pins to drive it. And the software is too complex also.<br /><br />The 8x8 LED RGB matrix module aimed to solve these problems.Directly drive the 8x8 RGB matrix module via the SPI serial interface. It works with 3-wire digital pins and the hardware SPI interface.The RGB matrix module from DFRobot is Daisy-chainable connection design - vertically and horizontally at the same time.And the high speed data transmission design improves its' display refresh rate.So it's possible to assemble a big RGB Matrix screen.<br /><br />Unit comes with a Red/Green/Blue full color LED Matrix assembled with a RGB Matrix Backpack Controller.Certainly,it directly support Arduino. And the library supplied is helpful to drive it much easier.<br /><br /><strong>Attention:Due to the restrictions, currently only supports 7 colors display, maximum 3x3 cascade!</strong><br /><br /></p>

<h2 id="specification">Specification</h2>

<div class="figure">

<p class="caption">DFR0202_Front_Back.png</p>

</div>

<ul>

<li>Power supply: 5v</li>

<li>Max current comsuption: 300mA</li>

<li>Communications interface: SPI(3 digital pins or hardware SPI interface)</li>

<li>LED color: RGB tri-color LEDs</li>

<li>8x8 dot matrix display assembled</li>

<li>Useful both for industrial and commercial information displays as well as for hobbyist human–machine interfaces</li>

<li>Directly support Arduino</li>

<li>Simplify the driving way</li>

<li>Daisy-chainable connection design - vertically and horizontally at the same time</li>

<li>High speed data transmission design to improve the display refresh rate</li>

<li>Size: 60x60mm</li>

</ul>

<h2 id="connection">Connection</h2>

<h3 id="connection-with-arduino-uno">Connection with Arduino UNO</h3>

<div class="figure">

<p class="caption">DFR0202_Connection.jpg</p>

</div>

<h2 id="connection-with-interface-shield">Connection with interface shield</h2>

<div class="figure">

<p class="caption">678px.LED_rgb.jpg</p>

</div>

<h3 id="multiple-modules-connected">Multiple modules connected</h3>

<p><br /><br /><br /></p>

<h2 id="at-command">AT Command</h2>

<p>When you have uploaded the sketch, you can control the module by AT command via serial port.<br />Baudrate: 115200</p>

<pre><code>AT+clear()                     Clear screenbr

AT+set_cur(0)                  Initialize the cursor positionbr

AT+print(123,0)                Display 123 on top layer, and it doesn&#39;t support letter br

AT+add_layer()                 Add a new layerbr

AT+set_cur(0,8)                Reset the the cursor position.br

AT+put_char(0,8,65,1,0,3,1)    Rotate display A at (0,8) color: red+greenbr

AT+put_char(8,8,66,1,0,5,1)    Rotate display B at (8,8) color: red+bluebr

AT+move(4,1,0)                 Move layer 0 rightbr

AT+move(3,1,0)                 Move layer 0 leftbr

AT+move(1,1,1)                 Move layer 1 upbr

AT+move(2,1,1)                 Move layer 1 downbr

AT+remove_layer(1)             Remove layer 1br</code></pre>

<h2 id="sample-code-ide-v1.0">Sample Code (IDE V1.0)</h2>

<h3 id="sample-code-1x1">Sample Code 1x1</h3>

<pre class="sourceCode cpp"><code class="sourceCode cpp"><span class="co">/************************* </span>

<span class="co">* Copyright:    ChengDu Geeker Tech. Co., Ltd. (DFRobot)</span>

<span class="co">* File name:      hello_matrix.pde </span>

<span class="co">* Description:    test the function of rgb matrix</span>

<span class="co">* Author:       wanghui_CD</span>

<span class="co">* Version:      V1.0</span>

<span class="co">* Date:         2012.06.21 </span>

<span class="co">* History:      none</span>

<span class="co">*************************/</span>

<span class="ot">#include rgb_matrix.h</span>

<span class="ot">#include SPI.h</span>

<span class="dt">unsigned</span> <span class="dt">long</span> time=<span class="dv">0</span>;

<span class="dt">unsigned</span> <span class="dt">int</span> tick_100ms = <span class="dv">0</span>;

<span class="dt">unsigned</span> <span class="dt">char</span> counter=<span class="dv">0</span>;

<span class="ot">#define N_X 1</span>

<span class="ot">#define N_Y 1</span>

<span class="co">/*</span>

<span class="co">//Interface shield ShiftOut connector </span>

<span class="co">#define DATA_PIN  9</span>

<span class="co">#define CLK_PIN   3</span>

<span class="co">*/</span>

<span class="co">//Hardware SPI</span>

<span class="ot">#define DATA_PIN  11</span>

<span class="ot">#define CLK_PIN   13</span>

<span class="ot">#define LATCH_PIN 8</span>

rgb_matrix M = rgb_matrix(N_X, N_Y, DATA_PIN, CLK_PIN, LATCH_PIN);

<span class="dt">unsigned</span> <span class="dt">char</span> cmd[<span class="dv">50</span>]={<span class="dv">0</span>},cmd_num=<span class="dv">0</span>;

<span class="dt">unsigned</span> <span class="dt">char</span> tmp =  &#39;A&#39;;

<span class="dt">unsigned</span> <span class="dt">char</span> st=<span class="dv">0</span>;

<span class="dt">void</span> setup()

{

       Serial.begin(<span class="dv">115200</span>);

       delay(<span class="dv">200</span>);

}

<span class="co">/*************************                    </span>

<span class="co">*  Description:</span>

<span class="co">*                         display callback function</span>

<span class="co">*        Receive AT comand via serial,and then run the right comand.</span>

<span class="co">*        This function can be run in sweep interval.</span>

<span class="co">*        Reduce delay time at function tail if screen blink.</span>

<span class="co">*        Increase delay time at function tail if screen shows a double image.</span>

<span class="co">* Param:   none</span>

<span class="co">* Retval:  none </span>

<span class="co">**************************/</span>

<span class="dt">void</span> hook(<span class="dt">void</span>)

{

    <span class="dt">int</span> i = <span class="dv">0</span>;

    <span class="dt">unsigned</span> <span class="dt">long</span> enter_time,exit_time;

    enter_time = micros();

    <span class="kw">if</span>((++counter)%<span class="dv">10</span> == <span class="dv">0</span>)

    {

        <span class="kw">if</span>(millis() - time = <span class="dv">100</span>)

        {

            time = millis();

            tick_100ms ++;

            M.move(UP,<span class="dv">1</span>,<span class="dv">0</span>);

            <span class="kw">if</span>(tick_100ms%<span class="dv">2</span> == <span class="dv">0</span>)

            {

            }

            <span class="kw">if</span>(tick_100ms%<span class="dv">5</span> == <span class="dv">0</span>)

            {

                M.clear();

                M.put_char(<span class="dv">0</span>,<span class="dv">0</span>,tmp+(st++)%<span class="dv">26</span>,<span class="dv">1</span>,MULTIPLY,RED  (st%<span class="dv">3</span>),TOP_LAYER);

            }

            <span class="kw">if</span>(tick_100ms%<span class="dv">10</span> == <span class="dv">0</span>)

            {

            }

            <span class="kw">if</span>(tick_100ms%<span class="dv">20</span> == <span class="dv">0</span>)

            {

            }

            <span class="kw">if</span>(tick_100ms%<span class="dv">50</span> == <span class="dv">0</span>)

            {

            }

        }

    }

    <span class="kw">if</span>(Serial.available())

    {

        cmd[cmd_num++] = Serial.read();

        <span class="kw">if</span>((cmd_num=<span class="dv">2</span>)  (cmd[cmd_num<span class="dv">-1</span>] == <span class="bn">0x0a</span>)  (cmd[cmd_num<span class="dv">-2</span>] == <span class="bn">0x0d</span>))

        {

            M.at_cmd(cmd);

            cmd_num = <span class="dv">0</span>;

        }

     }

     exit_time = micros();

     <span class="kw">if</span>(enter_time  exit_time)

     {

       <span class="kw">if</span>(exit_time - enter_time  <span class="dv">500</span>)

       {

         delayMicroseconds(<span class="dv">500</span> - (exit_time-enter_time));

       }

     }

}

<span class="co">/*****************************                    </span>

<span class="co">*  Description:</span>

<span class="co">*                         loop function</span>

<span class="co">*        Display function must be called.</span>

<span class="co">*        If you wanna do something after display be called,</span>

<span class="co">*    you should give display function a parameter which is a pointer to a function.</span>

<span class="co">* Param:   none</span>

<span class="co">* Retval:  none </span>

<span class="co">******************************/</span>

<span class="dt">void</span> loop()

{

    M.set_cur(<span class="dv">0</span>,<span class="dv">0</span>);

    M.display(hook);

}</code></pre>

<h3 id="sample-code-4x2">Sample Code 4x2</h3>

<pre class="sourceCode cpp"><code class="sourceCode cpp"><span class="co">/************************* </span>

<span class="co">*                Copyright:  ChengDu Geeker Tech. Co., Ltd. </span>

<span class="co">* File name:      hello_matrix.pde </span>

<span class="co">* Description:    test the function of rgb matrix</span>

<span class="co">* Author:       wanghui_CD</span>

<span class="co">* Version:      V1.0</span>

<span class="co">* Date:         2012.06.21 </span>

<span class="co">* History:      none</span>

<span class="co">*************************/</span>

<span class="ot">#include rgb_matrix.h</span>

<span class="ot">#include SPI.h</span>

<span class="dt">unsigned</span> <span class="dt">long</span> time=<span class="dv">0</span>;

<span class="dt">unsigned</span> <span class="dt">int</span> tick_100ms = <span class="dv">0</span>;

<span class="dt">unsigned</span> <span class="dt">char</span> counter=<span class="dv">0</span>;

<span class="ot">#define N_X 4</span>

<span class="ot">#define N_Y 2</span>

<span class="co">/*</span>

<span class="co">//Interface shield ShiftOut connector </span>

<span class="co">#define DATA_PIN  9</span>

<span class="co">#define CLK_PIN   3</span>

<span class="co">*/</span>

<span class="co">//Hardware SPI</span>

<span class="ot">#define DATA_PIN  11</span>

<span class="ot">#define CLK_PIN   13</span>

<span class="ot">#define LATCH_PIN 8</span>

rgb_matrix M = rgb_matrix(N_X, N_Y, DATA_PIN, CLK_PIN, LATCH_PIN);

<span class="dt">unsigned</span> <span class="dt">char</span> data_buf[N_XN_Y<span class="dv">8</span>*<span class="dv">3</span>]={<span class="dv">0</span>};

<span class="co">/*</span>

<span class="co">×ÝÏòÈ¡Ä££¬¸ßÎ»ÔÚÉÏ¡£</span>

<span class="co">ÏÈ×óºóÓÒ£¬ÏÈÉÏºóÏÂ¡£</span>

<span class="co">*/</span>

<span class="dt">const</span> <span class="dt">char</span> ni[] =

{

      <span class="bn">0x02</span>,<span class="bn">0x04</span>,<span class="bn">0x1F</span>,<span class="bn">0xE0</span>,<span class="bn">0x02</span>,<span class="bn">0x04</span>,<span class="bn">0x18</span>,<span class="bn">0xF0</span>,

      <span class="bn">0x10</span>,<span class="bn">0x13</span>,<span class="bn">0x10</span>,<span class="bn">0x10</span>,<span class="bn">0x14</span>,<span class="bn">0x18</span>,<span class="bn">0x00</span>,<span class="bn">0x00</span>,

      <span class="bn">0x00</span>,<span class="bn">0x00</span>,<span class="bn">0xFF</span>,<span class="bn">0x00</span>,<span class="bn">0x00</span>,<span class="bn">0x10</span>,<span class="bn">0x20</span>,<span class="bn">0xC2</span>,

      <span class="bn">0x01</span>,<span class="bn">0xFE</span>,<span class="bn">0x00</span>,<span class="bn">0x80</span>,<span class="bn">0x60</span>,<span class="bn">0x30</span>,<span class="bn">0x00</span>,<span class="bn">0x00</span>

};

<span class="dt">const</span> <span class="dt">char</span> hao[] =

{

      <span class="bn">0x08</span>,<span class="bn">0x08</span>,<span class="bn">0x0F</span>,<span class="bn">0xF8</span>,<span class="bn">0x08</span>,<span class="bn">0x0F</span>,<span class="bn">0x01</span>,<span class="bn">0x41</span>,

      <span class="bn">0x41</span>,<span class="bn">0x41</span>,<span class="bn">0x47</span>,<span class="bn">0x49</span>,<span class="bn">0x51</span>,<span class="bn">0x63</span>,<span class="bn">0x01</span>,<span class="bn">0x00</span>,

      <span class="bn">0x02</span>,<span class="bn">0x44</span>,<span class="bn">0xA8</span>,<span class="bn">0x10</span>,<span class="bn">0x28</span>,<span class="bn">0xC6</span>,<span class="bn">0x00</span>,<span class="bn">0x00</span>,

      <span class="bn">0x02</span>,<span class="bn">0x01</span>,<span class="bn">0xFE</span>,<span class="bn">0x00</span>,<span class="bn">0x00</span>,<span class="bn">0x00</span>,<span class="bn">0x00</span>,<span class="bn">0x00</span>

};

<span class="dt">unsigned</span> <span class="dt">char</span> cmd[<span class="dv">50</span>]={<span class="dv">0</span>},cmd_num=<span class="dv">0</span>;

<span class="dt">void</span> setup()

{

       Serial.begin(<span class="dv">115200</span>);

       delay(<span class="dv">200</span>);

}

<span class="co">/*************************                    </span>

<span class="co">*  Description:</span>

<span class="co">*                         display callback function</span>

<span class="co">*        Receive AT comand via serial,and then run the right comand.</span>

<span class="co">*        This function can be run in sweep interval.</span>

<span class="co">*        Reduce delay time at function tail if screen blink.</span>

<span class="co">*        Increase delay time at function tail if screen shows a double image.</span>

<span class="co">* Param:   none</span>

<span class="co">* Retval:  none </span>

<span class="co">**************************/</span>

<span class="dt">void</span> hook(<span class="dt">void</span>)

{

    <span class="dt">int</span> i = <span class="dv">0</span>;

    <span class="dt">unsigned</span> <span class="dt">long</span> enter_time,exit_time;

    enter_time = micros();

    <span class="co">//delayMicroseconds(300);</span>

    <span class="kw">if</span>((++counter)%<span class="dv">10</span> == <span class="dv">0</span>)

    {

        <span class="kw">if</span>(millis() - time = <span class="dv">100</span>)

        {

            time = millis();

            tick_100ms ++;

            <span class="kw">if</span>(tick_100ms%<span class="dv">2</span> == <span class="dv">0</span>)

            {

            }

            <span class="kw">if</span>(tick_100ms%<span class="dv">5</span> == <span class="dv">0</span>)

            {

            }

            <span class="kw">if</span>(tick_100ms%<span class="dv">10</span> == <span class="dv">0</span>)

            {

                M.move(LEFT,<span class="dv">1</span>,<span class="dv">0</span>);

            }

            <span class="kw">if</span>(tick_100ms%<span class="dv">20</span> == <span class="dv">0</span>)

            {

                M.move(RIGHT,<span class="dv">1</span>,<span class="dv">1</span>);

            }

            <span class="kw">if</span>(tick_100ms%<span class="dv">50</span> == <span class="dv">0</span>)

            {

            }

        }

    }

    <span class="kw">if</span>(Serial.available())

    {

        cmd[cmd_num++] = Serial.read();

        <span class="kw">if</span>((cmd_num=<span class="dv">2</span>)  (cmd[cmd_num<span class="dv">-1</span>] == <span class="bn">0x0a</span>)  (cmd[cmd_num<span class="dv">-2</span>] == <span class="bn">0x0d</span>))

        {

            M.at_cmd(cmd);

            cmd_num = <span class="dv">0</span>;

        }

     }

     exit_time = micros();

     <span class="kw">if</span>(enter_time  exit_time)

     {

       <span class="kw">if</span>(exit_time - enter_time  <span class="dv">300</span>)

       {

         delayMicroseconds(<span class="dv">300</span> - (exit_time-enter_time));

       }

     }

}

<span class="co">/*****************************                    </span>

<span class="co">*  Description:</span>

<span class="co">*                         loop function</span>

<span class="co">*        Display function must be called.</span>

<span class="co">*        If you wanna do something after display be called,</span>

<span class="co">*    you should give display function a parameter which is a pointer to a function.</span>

<span class="co">* Param:   none</span>

<span class="co">* Retval:  none </span>

<span class="co">******************************/</span>

<span class="dt">void</span> loop()

{

    M.add_layer(data_buf);

    M.put_HZ(<span class="dv">0</span>,<span class="dv">0</span>,ni,MULTIPLY,RED+GREEN,TOP_LAYER);

    M.put_HZ(<span class="dv">16</span>,<span class="dv">0</span>,hao,MULTIPLY,GREEN,TOP_LAYER<span class="dv">+1</span>);

    M.display(hook);

}

 </code></pre>

<h2 id="documents">Documents</h2>

<ul>

<li>Arduino library (for IDE 1.0 or latest version)</li>

<li>Arduino library (for IDE 0023)</li>

<li>Schematic</li>

<li>Manual</li>

<li>8x8 RGB Matrix LED datasheet</li>

<li>Zip file with all of the above</li>

<li>Simple spectrum display sample</li>

</ul>

<p><br /><br /><br />image:nextredirectltr.pngGo Shopping 8x8 LED RGB Matrix (SKU:DFR0202)<br /><br />category: Product Manual category: DFR Series |}</p>---

title: 8x8 LED RGB Matrix (SKU:DFR0202)

permalink: /8x8_LED_RGB_Matrix_(SKU:DFR0202)/


