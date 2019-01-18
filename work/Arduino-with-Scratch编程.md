# Arduino与Scratch结合编程

    scratch是一款比较容易学习的小学生编程图形化操作软件，
    arduino是一款比较适合小学生学习的单片机，
    这样两者结合学习，培养孩子的单片机应用能力，以及逻辑思维能力。

    arduino下载安装 
    链接：https://pan.baidu.com/s/1voK925xQ7PoFFLER4gJWrQ 
    提取码：5sjs 
    
    KittenBlock：教你快速从Scratch进阶到 Arduino
    从图形化编程进阶到Arduino的软件-KittenBlock
    下载 https://www.kittenbot.cn/software/
    
    
## KittenBlock 图形化 Arduino 编程
[参考](https://www.arduino.cn/thread-42752-1-1.html)

    Kittenblock是基于MIT和Google团队共同开发的 Scratch3.0代码进行二次开发的图形化编程软件，
    帮助Scratch用户以更简单的方式学习Arduino电子平台的电子以及机器人知识。
     
在线模式和离线模式

    在线模式是通过Kittenblock直接发送指令给主控板，以达到控制外围硬件的目的。
    在线模式下必须保证Kittenblock和主控板的串口或者Wifi连接
    
    顾名思义，在线模式就是需要kittenblock或者kblock app需要保持和机器人之间的实时通讯。
    通信方式包括串口、wifi或者蓝牙。
    机器人上需要预先烧录在线模式的固件。
    kittenblock通过发送指令给机器人，机器人执行对应指令。


    离线模式是将图形化代码直接转换为Arduino C++代码并且编译固化到主控板上，
    离线模式目前暂时无法和舞台内的精灵进行交互。
    离线模式不需要保持和kittenblock或者app之间的通信。
    离线模式只能执行固化烧录的程序，更换程序需要重新执行烧录。
    一般情况下将图形化代码专为C++或者python固化到目标主板上。

    Kittenblock 教程 http://learn.kittenbot.cn/zh_CN/latest/kittenblock/index.html

![](http://learn.kittenbot.cn/zh_CN/latest/_images/J.bmp)
    
    标签1：顶部菜单栏
        选择硬件
           Arduino UNO
           Arduino 2560
           ...
        选择通信方式
           如果你用数据线连接串口后，点击"没有连接"，
           选择对应的COM连接（前提您已成功安装好驱动）             
        进行网路配置
        各种快捷按钮
        设置和更新入口
        
    标签2：编程控制区(Flyout)
        图形化代码源
        用于切换工作区栏目

            
    标签3：工作区
        可以将图形化方块拖拽到此处
        切换精灵的时候会自动切换对应的代码
        工作区的代码可以生成对应的c++，python或js代码
        
    标签4：舞台
        可以通过工作区的代码控制舞台中的精灵元素
        可以通过右下角的两个按钮添加精灵或者背景
        通过菜单栏的代码切换开关可以将舞台变成代码模式
        
        切换到舞台Python模式
            python按钮是用来将图形块工作区切换到python编程工作区。
            python的编程对象就是舞台的小喵。
            小喵独创的拖拽积木块转换python代码
            通过拖拽可以快速提醒对应操作的python控制指令。
            当然我们后面也会把python控制的API更新出来，方便大家查看
            
    标签5：舞台元素配置       
        造型和精灵绘制 用于修改舞台的角色或者舞台背景 声音标签用于修改声音的效果，或者录制。
        各种舞台中元素的配置
        给每个精灵配置独立的通信端口
        
            角色与舞台参数编辑区
            精灵（舞台的角色）名称
            当前精灵x轴坐标
            当前精灵y轴坐标
            显示或者隐藏按钮
            精灵大小（默认100%）
            当前精灵的方向
            精灵与wifi或者串口对接
            精灵集合区（加入的精灵全部会显示在此）
            舞台集合区（加入的全部舞台背景会显示在此）
            添加精灵按钮
            添加舞台背景按钮
            
    标签6：帮助和辅助控制
        后退和重做操作
        快速帮助按钮
        舞台python入口
        

    连线引擎基本使用介绍
        Kittenblock是一个专注于硬件编程的平台，但是硬件编程少不了连线的步骤，
        Kittenblock内的连线引擎设计的初衷就是多少简化这个步骤，给用户更加直观的电路连接的概念。
        如果只是为了做个可沟通交流容易修改的连线图，那么喵家的这个连线引擎就非常合适。
        它没有Fritzing一定是svg图条条框框定义引脚，它没有PS那种门槛专业要求。

      特色：
        使用简单，容易上手，导入图片后，进行连线即可，无需设置
        包容开放，除了内置喵家常用电子模块，还支持用户导入其他家模块图片
        可编辑性，连线是根据软件坐标点计算的，所以其他用户打开后，这个连线图依然是可编辑的。
        可保存PNG，为了方便各位老师写书，右上角的截图图标可以将连线区域截图下来存成png用作其他用途。
        
### 物联网专题:什么是Thingspeak 

    Thingspeak是Mathworks在物联网(Internet of Things)大潮下的一个产品线，
    它是物联网的数据收集和数据分析的云平台。
    大多数使用Thingspeak的用户都是Maker,也叫做创客，
    他们有工程和硬件方面的经验，开发和使用可联网的硬件收集数据，并把数据传向云端，
    Thingspeak扮演的角色是物联网的后端，即 免费 存储硬件所收集的数据，
    以及提供 免费的在线使用MATLAB 分析这些数据的功能。
    
    目前支持直接在 Kittenblock 内的 IOT模块 上报 和 读取数据。

    Thingspeak账号的注册激活大家请执行前往他们的网站完成

    https://thingspeak.com

    注册完成后可以新建一个channel，
    channel用来收集数据并提供接口做进一步的处理，不同的channel之间相互之间独立。
    每个channel可以设置不同的field，相当于不同的参数。
    注册完成后，可以打开Kittenblock，在左下角的插件面板中导入IOT插件

    Thing Speak 配置
    打开channel的控制面板，将读/写api key填入kittenblock对应的方块之中。    
    
    Kittenblock中使用ThingSpeak模块
    这里以最基本的读写操作为例子，
    写模块需要我们首先设置API key，
    写模块的field中的序号对应我们channel中设置的参数序号，
    大家可以在channel setting中查看.
    
    我们随机发送一些数字到thing speak的服务器，注意发送频率有限制，默认是60s。
    回到thing speak的控制台我们就可以看到刚刚上发的数据了：
    
![](http://learn.kittenbot.cn/zh_CN/latest/_images/thingspeak_write.png)
    
    读取操作类似，唯一区别是如果你将你的chennel设置为公开模式，
    可以不用设置读取api key，还需要设置正确的channel ID。
    这里我们的channel id是546917，大家可以在浏览器地址中找到，
    或者前往channel view查看id号码。
    读取框的最后一个参数是目标field数据的序号，具体取决于你有多少数据。

![](http://learn.kittenbot.cn/zh_CN/latest/_images/thingspeak_read.png)
    
    
### Kittenblock插件开发指南
    具体的插件定义大家可以前往MIT团队的官方github仓库查看：
    https://github.com/LLK/scratch-vm/wiki/Scratch-3.0-Extensions-Specification
    
[开发一个跟硬件设备通信的插件](http://learn.kittenbot.cn/zh_CN/latest/kittenblock/%E6%8F%92%E4%BB%B6%E5%BC%80%E5%8F%91%E6%8C%87%E5%8D%9702.html)
    
    
    scratch3的插件形式
    跟scratch2类似，scratch3的插件也是一大块JavaScript的代码，
    不同的是更加开放、更加灵活、允许用户定义的功能也更加多，
    但是随之的开发难度也提高了不少。
    所有的插件都是一个类Class，当然也同时支持es6的各种语法。
    对js class或es6不熟悉的同学可以看看这篇 ECMAScript 6 入门 作者：阮一峰 ：
    http://es6.ruanyifeng.com/#docs/class

    构件我们的第一个插件
    首先我们先在电脑上新建一个文件，名字就叫testext.js吧，用您喜欢的文本或者代码编辑器打开它并添加以下代码。
```js
const ArgumentType = Scratch.ArgumentType;
const BlockType = Scratch.BlockType;
const formatMessage = Scratch.formatMessage;
const log = Scratch.log;
// 其中前四行是scratch3的运行环境=======

// 定义了一个名字叫TestExt的Class，这个类就是插件的主体，
// scratch的vm（虚拟机）会自动生成一个这个类的实例并挂载到运行环境中
class TestExt {
    // es6  类构造函数
    constructor (runtime){
        this.runtime = runtime;
        this.runtime.registerExtensionDevice('TestExt', this);
    }
    
    // 信息函数
    getInfo (){
        return {
            id: 'TestExt',
            name: 'TestExt'
        };
    }
    
    
}

module.exports = TestExt;


```

    接着我们打开Kittenblock，在左上角的硬件下拉菜单最后一栏导入外部插件testext.js
![](http://learn.kittenbot.cn/zh_CN/latest/_images/extload.png)
    
    加载后可以看到在最左下角有一个新的插件
![](http://learn.kittenbot.cn/zh_CN/latest/_images/extload02.png)    
    
    
    但是这个完全是空的，接下来我们来讲解如何定制化插件的各种属性。
    PS: 如果重复加载插件发现插件没有更新，这是因为更新的内容太少，
    这时候可用切换到造型面板再切换回代码面板让程序强制刷新图形化方块。
    
    
更改图标的颜色只需要在genInfo加入对应的颜色定义
```js
getInfo (){
    return {
        id: 'TestExt',
        name: 'TestExt',
        color1: '#DE5277',
        color2: '#AA3F5B',
        color3: '#AA3F5B',
    };
}
```

    如果需要图标则可以加入对应的图标定义，
    有菜单栏图标menuIconURI和方块前缀图标blockIconURI两种：
![](http://learn.kittenbot.cn/zh_CN/latest/_images/extload04.png)

    图标支持base64格式和你的插件图标路径的require方法，
    大家可以找一下在线的图片转base64工具，注意控制图片大小。
    
    这里我们添加我们第一个自定义的图形化方块，先贴完整的代码：
```js
    getInfo ()
       {
        return {
            id: 'TestExt',
            name: 'TestExt',
            color1: '#DE5277',
            color2: '#AA3F5B',
            color3: '#AA3F5B',
            
            // 加入了一个blocks数组定义，数组中每个元素对应一个方块===
            blocks: [
                     {
                    opcode: 'test1', // 对应方块的id,必须唯一
                    blockType: BlockType.COMMAND,// 方块类型
                    text: 'Test [VALUE]',        // 方块内容定义
                    arguments: { // 参数的结构定
                        VALUE: {
                            type: ArgumentType.NUMBER, // 参数的类型,有STRING,NUMBER,BOOLEAN,COLOR等
                            defaultValue: 123          // 默认值
                               }
                               }
                     },
                     
                     {
                        opcode: 'test2', // 需要添加 实现函数 test2()
                        blockType: BlockType.REPORTER,

                        text: 'Random Value [MAX]',
                        arguments: {
                               MAX: {
                                type: ArgumentType.NUMBER,
                                defaultValue: 100
                                    }
                                   }
                     }
                     
                     ]
             };
         }
         
    // 并且还要对应一个对应的实现函数 test1 名字为   opcode: 'test1'
    test1 (args){
        console.log('test1', args.VALUE); // 主要功能就是在终端打印出参数的值
    }
    
    // 实现函数
    test2 (args){
    return Math.random()*args.MAX
    }
    
```

完整代码

```js
const ArgumentType = Scratch.ArgumentType;
const BlockType = Scratch.BlockType;
const formatMessage = Scratch.formatMessage;
const log = Scratch.log;

class TestExt {
    constructor (runtime){
        this.runtime = runtime;
        this.runtime.registerExtensionDevice('TestExt', this);
    }
    
    getInfo (){
        return {
            id: 'TestExt',
            name: 'TestExt',
            color1: '#DE5277',
            color2: '#AA3F5B',
            color3: '#AA3F5B',
            
            blocks: [
                {
                    opcode: 'test1',
                    blockType: BlockType.COMMAND,
                    text: 'Test [VALUE]',
                    arguments: {
                        VALUE: {
                            type: ArgumentType.NUMBER,
                            defaultValue: 123
                        }
                    }
                },
                {
                    opcode: 'test2',
                    blockType: BlockType.REPORTER,

                    text: 'Random Value [MAX]',
                    arguments: {
                        MAX: {
                            type: ArgumentType.NUMBER,
                            defaultValue: 100
                        }
                    }
                },
            ]
        };
    }
    
    test1 (args){
        console.log('test1', args.VALUE);
    }
    
    test2 (args){
        return Math.random()*args.MAX
    }
    
    
}

module.exports = TestExt;

```


### Kittenblock 使用 TensorFlow的机器学习插件
    [鸢尾花(Iris)分类](http://learn.kittenbot.cn/zh_CN/latest/Tensorflow/03IrisTrainig.html)
    [MNIST 手写数字识别](http://learn.kittenbot.cn/zh_CN/latest/Tensorflow/04MnistTraining.html)
    [MNIST 模型的保存和加载](http://learn.kittenbot.cn/zh_CN/latest/Tensorflow/05MnistLoad.html)
    [使用MobileNet模型进行物体识别](http://learn.kittenbot.cn/zh_CN/latest/Tensorflow/06MobileNetModel.html)
    [使用MobileNet模型进行任意物体识别——剪刀石头布为例](http://learn.kittenbot.cn/zh_CN/latest/Tensorflow/07TransferLearning.html)
[永远猜不赢 剪刀石头布猜拳机器人](http://learn.kittenbot.cn/zh_CN/latest/Tensorflow/08%E6%B0%B8%E8%BF%9C%E7%8C%9C%E4%B8%8D%E8%B5%A2%E6%9C%BA%E5%99%A8%E4%BA%BA.html)
    
    
    请先下载Kittenblock1.79或以上版本，点击左下角的扩展插件之后可以在列表中找到TensorFlow的插件。
    
Kittenblock的TensorFlow引擎

![](http://learn.kittenbot.cn/zh_CN/latest/_images/c01_09.png)
    
    Google在2018上半年发布了使用js实现轻量版本的TensorFlow，
    经过半年的迭代优化而且生态圈的案例和资料越来越丰富。 
    Kittenblock在1.79版本更新也集成了TensorFlowjs引擎，
    并且将其重新进行整合使她更加适合图形化编程和入门。 
    即使完全没有编程基础，也能够让你在最短的时间内构造自己的机器学习模型，并且能够解决一些实际问题。
    无论看多少相关的理论和书籍都没有自己真真切切地动手实践一下理解的深刻。
    
    实现了察异辨花、手写数字识别和识图认物等几个例子
    
    由于TensorFlow使用了GPU进行计算，请确保你的电脑配置还过的去，
    部分太老的电脑或者集成显卡的电脑可能因为资源限制会有部分例子无法正常完成。

![](http://learn.kittenbot.cn/zh_CN/latest/_images/c02_27.png)

数据的导入

    说到机器学习，我们第一步就是要给机器准备好标定过的数据。
    实际上大部分大数据的工作也是抓取和标定数据， 
    当然实际工作中的数据是海量的也不可能在个人电脑中完成所有计算。
    Kittenblock将数据导入流程做了大大的简化，可以直接导入csv文件和图片文件夹。
    当然这些简化带来的缺点就是效率的降低，但是可以让每一个人都看到数据长的是什么样子。
    
    Kittenblock内的数据保存使用了Scratch的列表变量（list）完成，
    因此在导入任何数据之前请先建立对应的列表变量。

![](http://learn.kittenbot.cn/zh_CN/latest/_images/c02_04.png)
    
    其中前两个是导入CSV数据，第三个方块是导入图片文件夹，第四个是数据混淆（或者简称洗牌）。
    目前就4个导入数据的方块，后面会加入更加丰富的数据导入方法。
    这里做测试我们在D盘根目录下建立data.csv文件，里面的内容如下（注意要用英文的逗号）
```js
1,2
2,4
3,6
4,8
5,10
```
    我这里使用excel建立的，填写好内容后，另存为data.csv的文件,并且记住这个文件的位置。

    作为我们普通人，一眼就可以看出，第二列的数字都是第一列的两倍。

    那我们如何让机器也能看出这个规律呢？跟着我们一步步操作

    新建两个列表变量，分别叫in和out（如下图操作），
    准备用来分别储存刚才那两列的数据（通过这种方法，
    以表格的形式快速把数据导入到Kittenblock中，方便快捷，
    而且后续数据比较好维护，专业工具做专业的事情）
![](http://learn.kittenbot.cn/zh_CN/latest/_images/c02_20.png)

    这样就建里了两个空的列表变量，下一步我们往列表中导入数据
![](http://learn.kittenbot.cn/zh_CN/latest/_images/c02_21.png)

    拖入如下方块，积木块的意思是将“D:/data.csv”
    这个文件的第0列（col0）导入到列表in中（就是这么特别从0列开始算起）...
    
![](http://learn.kittenbot.cn/zh_CN/latest/_images/c02_05.png)
    
    点击方块，相当于把这两个方块的命令执行一次，然后就看到两个列表已经导入了data.csv的数据了
![](http://learn.kittenbot.cn/zh_CN/latest/_images/c02_22.png)
    
    但是我们看到，实际我们想导入5行数据，这里居然有6行（应该是excel的一个bug，默认自己去补一个空行），
    这里我们手动删除下。
    鼠标指针移动到6行那里（如图所示），
    点击下出现一个叉，再点击一下叉，就可以删除这个数据了。
    
建立学习模型
    
    数据有了，接下来建立学习模型。
    因为Kittenblock的TensorFlow引擎支持多个模型同时存在，
    我们需要先定义一个变量指向这个模型。
    注意这个变量只保存模型的名字，模型实体储存在TensorFlow的引擎中。
    保存sb3的时候也仅仅只是保存这个模型的名字，下次打开程序的时候还是需要重新初始化这个模型
    这里直接新建一个叫model的变量。 

![](http://learn.kittenbot.cn/zh_CN/latest/_images/c02_23.png)
    
    之后新建一个模型并赋给这个变量，后续我们所有对应的模型操作均需要指定模型名字
![](http://learn.kittenbot.cn/zh_CN/latest/_images/c02_08.png)
    
    其中input shape是模型的输入矩阵尺寸，我们的数据每次只输入一个数据，
    并且每次只输出一个数据，因此这里直接填1就行了。
    大家常常听说神经网络，这里我们就要给我们的模型添加神经网络了。
    作为入门我们只用一层的神经网络，并且这一层中只有一个神经元。

![](http://learn.kittenbot.cn/zh_CN/latest/_images/c02_09.png)
    
    注意这是一个Denselayer类型的层，也叫全连接层。
    因为这个模型太简单了，我们会在下一章更加直观的看到它的形式。
    其中unit参数就是它的神经元数目，act是激活函数类型。
    我们模型建立就到这里完成了，但是记住建立完模型后一定要编译模型，
    就跟我们写完代码要编译程序一样的道理。
    只有编译后的模型才生效并且可以用于训练，
    并且TensorFlow引擎会自动检察模型有没有错误。

![](http://learn.kittenbot.cn/zh_CN/latest/_images/c02_10.png)
    
    
    其中opt是Optimizer的简称，指的是模型训练中使用的优化器，
    loss是损失函数类型，最后一个参数是学习速率。
    这三个参数（特别是最后一个）设置的好坏将取决于你的模型是否能够收敛。

完整的模型建立方块如下

![](http://learn.kittenbot.cn/zh_CN/latest/_images/c02_11.png)

    将数据交给模型并且开始训练
        注意我们将数据保存为scratch3的list变量中，
        但是TensorFlow引擎并不知道也不能直接访问这些变量，
        我们需要手动将数据指定给模型。
        在训练模型之前我们还需要将数据交给TensorFlow引擎。
        
        大家看其他资料或代码的时候也经常会发现将输入命名为xs输出命名为ys，
        大家只要记住xs表示输入数据，ys表示对应的输出数据或者标签就行了。
        



