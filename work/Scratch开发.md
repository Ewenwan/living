# Scratch
    软件下载 https://scratch.mit.edu/download
    
    网页在线版 https://scratch.mit.edu/projects/editor/?tutorial=getStarted
    
             Scratch3 Lab, https://scratch3.codelab.club/
             万物积木化scratch3_adapter https://scratch3-adapter-docs.just4fun.site/user_guide/install/
             
    github源码仓库 https://github.com/LLK/scratch-blocks
    
    
## 与 python语言的交互
    scratch是一款又麻省理工开发的图形化编程软件，
    这款软件提供了可以使用javascript与scratch交互的接口，
    同时提供了一个socket端口和一系列的命令与应用程序交互，
    这里我们通过python与scratch交互。
    
    之所以选择python是主要基于以下几个原因： 
        1.python是非编译性语言，所以除非库的提供者将不想开源的代码写在C/C++,
          或者java等编译性语言的代码中，然后通过python调用，
          一般情况下我们是可以看到源代码的.
        2.scratch 对于使用python与它交互，有现成的python库可以调用，
          这样我们就不需要详细了解scratch对外定义的繁琐的命令结构，这样没有意义.
    
    原理:
        1.当scratch启动的时候会默认打开本机的42001端口
          作为服务器端的socket接收应用程序请求（这个port只是默认的，可以修改） 
        2.我们通过本地socket连接到scratch，然后可以发送一系列的命令与scratch交互，
          这样我们就能通过scratch图形化编程操作我们希望操作的任何东西，比如硬件.
    
    linux下配置 
        安装scratch 
              sudo apt-get install scratch   差不多是 1.4版本
        安装scratch 的python库
              sudo apt-get install python-pip scratchpy
              
        在安装目录有一个scratch.py的python脚本，可以查看scratch.py的代码，
        这个里面提供的通过python操作scratch的所有接口以及命令。
        
> scratch.py

```python
import array
import errno
import itertools
import socket
import struct

class ScratchError(Exception): pass
class ScratchConnectionError(ScratchError): pass        

class Scratch(object):
    prefix_len = 4
    broadcast_prefix_len = prefix_len + len('broadcast ')
    sensorupdate_prefix_len = prefix_len + len('sensor-update ')

    msg_types = set(['broadcast', 'sensor-update'])
    
    # 使用的port端口是42001,host是“localhost”(说明不支持远端连接)
    # 当然我们可以用我们的应用程序做一个跳板，然后远程操作scratch
    def __init__(self, host='localhost', port=42001):
        self.host = host
        self.port = port
        self.socket = None
        self.connected = False
        self.connect()
        
    # 连接到 Scratch
    def connect(self):
        """
        Connects to Scratch. 
        """
        self.socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        try:
            self.socket.connect((self.host, self.port))
        except socket.error as (err, msg):
            self.connected = False
            raise ScratchError("[Errno %d] %s" % (err, msg))
        self.connected = True
    
    # 广播，发送消息
    def broadcast(self, msg):
        if getattr(msg, '__iter__', False): # iterable
            for m in msg:
                self._send('broadcast "%s"' % self._escape(str(m)))
                print "hjptestfor:",self._escape(str(m))
        else: # probably a string or number
            self._send('broadcast "%s"' % self._escape(str(msg)))
            print "hjptestfor:",self._escape(str(msg))
            
    # 接收消息
    def receive(self):
        return self._parse(self._recv())

```


> helloscratch.py
```python
#-*- coding:utf-8 -*-
'''
主要功能是将scratch发送过来的字符串打印出来，
为了操作硬件，我们可以自定义一套命令，比如i2c，address等，
当收到这些字符串的时候我们可以在我们的客户端里面操作硬件（当然这个例子里面只是打印） 
比如要操作i2c，只需要执行sudo apt-get install python-smbus就可以了
'''
import scratch
try:
    # 使用上述 类对象 连接
    s = scratch.Scratch()
    if s.connected:
        print "Connected to Scratch successfully"
    else:
        print "Connected to Scratch error"
except scratch.ScratchError:
    print "Scratch is  not opened or remote sensor connections aren't enabled"


try:
    print "broadcast begin"
    # 广播 发送 消息
    s.broadcast('hello scratch')
except NameError:
    print "Scratch: Unable to Broadcast"

while True:
    try:
        msg = s.receive()
        print "Scratch: receive:",msg
    except KeyboardInterrupt:
        print "GrovePi Scratch: Disconnected from Scratch"
        break

```
    
    运行
    执行1：首先手动启动scratch，否则我们的客户端 会由于 服务器端不在线连接失败 
          在shell下直接输入：scratch 回车就启动了scratch
    执行2：在shell下运行我们的客户端,就连接到了 scratch：
          suso python helloscratch.py 
          
    比如我们在 scratch服务器 中 加入下面这个模块   
          when 旗帜 clicked    <===>  当 旗帜 被点击
          broadcast join 112   <===>  广播 112 并等待
    
    当我们点击旗帜的时候scratch图形代码运行，
    在我们的客户端收到112这个字符串，效果如下： 
       Connected to Scratch successfully
       broadcast begin
       Scrach:  receive: ('broadcast', '112')
    
    如果需要操作硬件，可以把在join里面定义自己的命令：
    在接收到这些命令字符串之后，紧接着操作硬件，这样就起到了操作硬件的效果.
    
    
    
## 使用Scratch2和ROS进行机器人图形化编程学习
    https://blog.csdn.net/ZhangRelay/article/details/78857311
    http://jderobot.org/Raulperula-colab
    https://github.com/JdeRobot/Scratch4Robots
    
    Scratch是一款由麻省理工学院(MIT)设计开发的少儿编程工具，
    Python是近年来非常流行的机器人和人工智能编程语言，
    ROS是机器人操作系统。
    需要安装Scratch2、ROS Kinetic、Gazebo 7、JdeRobot、Python2.7等。
    
    !!!!!思想!!!!!!!!!!!!!!!!!!!!
    通过将Scratch2图形化编程语言转为 Python，然后通过ROS消息机制控制 Gazebo 或实际机器人。
    或者参考上述 Scratch socket 到 Python 再通过 ros话题发送 机器人运动的消息。
    在 Gazebo 仿真环境中 控制仿真机器人。
    或者 控制一个机器人移动底盘
    
    是不是比较有趣，在不需购买任何设备的情况下，就可以用Scratch2进行ROS机器人编程。
    小学用Scratch2学习简单编程，中学用Python学习简单编程，大学用Python和C++学习复杂机器人编程，无缝衔接。
    
    
##  万物积木化scratch3_adapter 插件系统
![](http://wwj-tmp-video2.just4fun.site/%E6%8F%92%E4%BB%B6%E7%B3%BB%E7%BB%9F.png)
    
[scratch 连接 Cozmo ](https://scratch3-adapter-docs.just4fun.site/extension_guide/cozmo/)

[cozmo系列之入门 - 有性格且可编程的机器人](https://blog.just4fun.site/cozmo-hello-world.html)

[]()

[]()

[]()

[]()

[]()

BB8可爱且呆，cozmo可爱又任性

![](http://wwj-fig-bed.just4fun.site/cozmo1a05d914.png)

    Scratch3 Lab, https://scratch3.codelab.club/
    万物积木化scratch3_adapter, https://scratch3-adapter-docs.just4fun.site/user_guide/install/
    
    步骤1: 打开Scratch3 Lab
    步骤2: 打开scratch3_adapter
           双击打开scratch3-adapter
           scratch3-adapter启动之后，
           可以看到Scratch3 Lab指示灯显示绿色,代表连接成功
    步骤3: 连接micro:bit，加载插件
          使用数据线将micro:bit接入电脑，下载usbMicrobit_0_2.hex并拖入micro:bit中
          ps: Windows7用户注意(Mac和Windows10用户可以跳过),为了能发现并连接micro:bit，
               需要安装驱动(和使用mu-editor操作相同)
               
    完成后在scratch3_adapter中点击加载micro:bit插件
    
    步骤4: 打印hello world
        现在让我们利用Scratch3 Lab控制micro:bit，让它在点阵屏上打印hello world
        选择对应的scratch3插件:Microbit_cx(我们同时制作了若干中micro:bit，包括使用web蓝牙的)



           
           
    
    
