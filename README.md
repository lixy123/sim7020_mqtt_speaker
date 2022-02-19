# sim7020_mqtt_speaker

<b>一.功能：</b> <br>
    1.通过手机或网上自动化服务平台将文字信息用MQTT协议发送到本机器，并播放.<br>
    2.考虑到电池供电场景。设计了sleep指令，收到指令后定时休眠N分钟。唤醒状态后再重新返回工作状态.<br>
    3.安卓手机mqtt客户端可以用 iot controler<br>
      注：iot controler 可以方便定制按钮触发mqtt信息发送和接收<br>
    4.网上触发mqtt平台可以用, https://ifttt.com/ <br>
      通过触发器 https://ifttt.com/ 能指定触发条件满足后发送MQTT,例如每日定时时间到，出现异常天气，收到邮件等<br>

 <b>二.硬件：</b><br>
  1.LILYGO T-PCIE ESP32 NB-IOT<br>
  2.亚博智能 语音合成播报模块XFS5152芯片TTS开发板<br>

ESP32 语音合成播报模块<br>
5V/3.3V  --  VIN<br>
GND      --  GND<br>
13       --  SDA<br>
12       --  SCL  <br>
<br>
 <img src= 'https://github.com/lixy123/sim7020_mqtt_speaker/blob/main/mqtt_speaker1.jpg?raw=true' /><br>
 <img src= 'https://github.com/lixy123/sim7020_mqtt_speaker/blob/main/mqtt_speaker2.jpg?raw=true' /><br>
 
演示视频地址<br>
   https://github.com/lixy123/sim7020_mqtt_speaker/blob/main/mqtt_speaker.mp4?raw=true <br>
   
   
 <b>三.软件功能列表:</b><br>
  1.开机,自动连接MQTT<br>
  2.当收到MQTT，对播放，休眠指令进行对应的处理<br>
  3.程序功能检查:<br>
    A.如果检测到MQTT服务器中断时，60秒后自动重新连接MQTT<br>
    B.自检功能:每n小时检查mqtt网络连接，如中断，重建MQTT<br>
    C.自检功能:每天强制重启1次，防止程序意外死掉<br>

 <b>四.性能</b><br>
  1.整体电流:<br>
    带电运行:70-85ma<br>
    休眠状态: 2-3ma,待测试？ <br>

  2.程序大小：<br>
    0.4MB<br>

 <b>五.其它</b><br>
  1.MQTT服务器需要找一个稳定可靠的，网上免费的虽然不花钱，但没准哪一天就停了。<br>
  2.mqtt_clientid,mqtt_topic,mqtt_topic_resp 三个值需要调整，否则多个硬件都用同一个信息会互相串.<br>
  3.语音模块非工作状态偶尔会有杂音，可能是NBIOT电流噪音影响？<br>
  
