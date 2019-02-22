# Quantized Transaction 量化交易  quantitative trading 量化投资

量化投资的主要内容包括：量化选股、量化择时、股指期货套利、商品期货套利、统计套利、期权套利、算法交易、ETF/LOF套利、高频交易等

[入门教程：教你写量化策略，Ricequant量化大课堂](https://www.ricequant.com/community/topic/761/)

[七月算法在线 量化投资 视频教程](https://www.bilibili.com/video/av22022468)

[《量化投资：策略与技术（修订版）》（丁鹏）.pdf](http://vdisk.weibo.com/s/ttHPatjvLk2z)

> 打开量化投资的黑箱

[《打开量化投资的黑箱》读书笔记](https://github.com/fujohnwang/fujohnwang.github.com/blob/b56e2e2f0e68e937aae3d5c798ec4cf4b5e57610/posts/2013-04-06-reading-note-of-inside-the-black-box.markdown)


* 黑箱:量化交易如何运作
* 量化交易：人类经过研究后得到的交易策略，然后交付给系统去实施
* 宽客:赋予量化交易生命的人
* 研究调整模式适应市场的变化
* 算法实施是量化交易的基础之一
* 确定风险的准确度量和正确度量
* 历史数据反映了哪些情景是可能的，哪些是不可能的，哪些又是从未发生过的
* 交易者应该学习宽客在合理设置和实施其交易策略时表现出来的全面性和严格性
* 宽客以人工干预模型的运行，防止模型基于错误信息做出错误决策
* 非量化交易的投资者以宽客身上学到的第一点就是，强制自己对所采用的投资策略的各个方面做出更深入的思考。 我们的策略到底是什么?如何贯彻它? 宽客希望对所有事物都进行度量，包括风险在内。 宽客对纪律的严格遵守。 宽客始终保持一致性。


> 核心思想：没有永远好的金融产品，也没有永远坏的金融产品

* 理论驱动：观察市场后，提出一般性模型的理论，并通过严谨的证明和验证，判断这个理论解释是否有效并符合市场情况的理论
* 数据驱动（经验驱动）：根据市场的历史数据，发掘出有用的关系和模式，建立关联性映射关系，不注重理论解释。

## 理论驱动型大致分为5类（和主观判断型交易几乎一样）
### 价格相关数据策略
#### 1。趋势型（trend）
市场参与者需要慢慢地形成对金融产品价值的共识，从一个均衡向新的均衡慢慢运动的过程就形成了趋势，而这个过程需要一定的时间。 还有一种解释就是“博傻理论”。

#### 2.回复型（reversion）
流动性需求可能导致买者和卖者之间的力量在短期内出现失衡，于是金融产品被超买或超卖。 比较典型的就是统计套利（标的为相似公司的股票价差）

### 基本面相关数据策略
#### 3.价值型/收益型（value/yield）：
基于市场的风险高估和低估，市场经常会对风险资产的风险作出过高的估计，而低估风险相对低的资产的风险。（高风险资产价格较低，...）。 参考市盈率（P/E,price-to-earnings），但一般宽客都是用它的倒数E/P——盈利收益率（earnings yield，原因见下图），金融产品的收益率越高，价格越便宜。也可以参考股利收益率（dividend yield）。 当基于一个相对价差来操作时，即同时买入价值相对低估的股票而卖出相对高估的股票，这种策略被称为携带交易（carre trade） 

#### 4.成长型（growth）
基于关于资产的某些变量的增长水平，比如PEG比率，这个指标是指价格除以盈利增长，或者是市盈率除以每股盈利增长率。 但市场上常见的成长型策略确实简单的买入高增长资产，卖出低增长甚至负增长股票，不考虑当前的价格因素，因为成长型股票的价值是无法确定的。强势增长的公司未来可以夺得更多的市场占有率，可以说是一种着眼于远期的携带交易

#### 5.品质型（quality）
根据一些品质信号，比如资产负债率，自由现金流，具体业务指标等。


## 数据驱动型
优势：门槛高，竞争力小；捕获各种市场行为，虽然理论上无法解释。 劣势：可能伪显著；可能计算量巨大；需要不断调整而带来风险；输入数据噪声多，导致一些错误信号。

### 策略的实施（大概归纳为6点）
#### 1. 预测目标
可以是预测方向、幅度、运动的持续时间、以及预测的置信度和概率。 信号强度指更大的期望回报或更高的可能性。在给定的置信水平下，期望回报越大则信号强度越大；在给定的预期回报下，置信度越大则信号强度越大。对应的，可能意味着头寸投注可以越大。

#### 2. 投资期限
不同投资期限（长期、短期、超短期）的实施方案可能完全不一样，甚至导致相反头寸。

    高频交易（high-frequency）：不超过当日收盘
    短线策略（short-term）：持仓一天到两周
    中线策略（medium-term）：数周到数月
    长线策略（long-term）：持仓数月或更长
    
#### 3. 投注结构
    预测单个金融产品的绝对回报
    预测多个金融产品的相对回报
    
较小范围内选取一对金融产品进行配对交易，很少能精确匹配。

较大范围内选一个门类，消除同组证券间的共同因素。甚至采用多种分组方式共同决定分组，以达到比绝对回报更平稳的回报。

#### 4. 投资范围
同一个策略可以用在多个金融产品上，一般需要考虑很多因素。比如，地域，资产类别，金融产品种类。

    需要流动性好的交易标的，交易成本可控；
    需要大量高质量的数据，它们在富有流动性和发达的市场更容易获得；
    需要比较容易用系统化模型来预测的金融产品。
#### 5. 模型设置
机器学习技术主要是用于寻找量化模型的最优参数设置，其算法主要是用更智能且更科学的方法检验多种潜在可能的参数，同时又不会出现过拟合。

#### 6. 运行频率
太多的运行导致模型根据毫无用处的噪声而建仓平仓的概率加大，交易成本升高，同时也容易出现过拟合。 太少的运行会导致很少的交易，如果订单规模同时很大的话，对市场有较大冲击，进而改变市场，使模型失效。


# 量化交易 详细知识

## 一、量化投资介绍

### 有效市场假说

EMH的三种形式：

- 弱式有效市场假说（Weak-Form Market Efficiency）
- 半强式有效市场假说（Semi-Strong-Form Market Efficiency）
- 强式有效市场假说（Strong-Form Market Efficiency）

推论：

- 如果弱式有效市场假说成立，则股票价格的技术分析失去作用，基本分析还可能帮助投资者获得超额利润。
- 如果半强式有效假说成立，在市场中利用基本面分析则失去作用，内幕消息可能获得超额利润。
- 在强式有效市场中，没有任何方法能帮助投资者获得超额利润，即使基金和有内幕消息者也一样。

<!--more-->

### 主动投资的不足

人性中对于获利的贪婪和对于损失的恐惧是亘古不变的

### 理查德·塞勒（Richard Thaler）理论

- 禀赋效应：人们在决策过程中对利和害的权衡是不均衡的，对“避害”的考虑远大于对“趋利”的考虑
- 跨期选择：人类恰恰是不擅长做跨期决策的，大多数时候会做出短视冲动的选择
- 心理账户 & 储蓄理论：人在思考问题时，会在心里构建出分门别类的心理账户，分别进行计算

### 行为经济学

- 赚谁的钱：市场在某一特定时间内的无效性，或者说是别人犯的错误
- 赚什么钱：主动承担某种特定风险，继而获得承担该风险的风险溢价

### 主观投资与量化投资的区别 

只在于策略如何被制定以及如何被执行

### 收益率(return) 公式

$$ r_P = \beta_P  * r_B +\alpha_P $$

- P：投资组合portfolio
- B：业绩基准组合B
- $\beta_P$：P相对于B的beta系数，又称P的系统风险
- $\alpha_P$：反映了P对于B的超额收益能力，这部分收益与大盘的波动无关，这就是alpha的魅力

#### Alpha 的非常规定义：

在交易中关于持有头寸选择和买卖时机把握的技巧 

### 宽客(Quant)

![](http://os21ow86u.bkt.clouddn.com/quant1.png)

### 一个完整的量化交易系统

- 市场：买卖什么
- 逻辑：买卖思路
- 头寸规模：买卖多少
- 入市：何时买进
- 止损：何时退出亏损的头寸
- 离市：何时退出盈利的头寸



## 二、量化必备股票基础知识

### 交易决策过程

1. 数据
2. 价量时空仓
3. 指标
4. 信号
5. 买卖

### 分时图与K线图的数据处理

- 分时图上共有251个数据点

- K线图（蜡烛图）反应的是开高低收(Open/High/Low/Close)

- K线图数据（bars）是由Level1行情数据（ticks）经过格式解析、聚合处理成的。

- 正确地接收行情数据，并根据量化模型的需要累计出不同级别的分时和K线数据，是量化 

  一项基本功。

### 技术指标

基于行情数据，通过特定数学公式或模型计算得出的、用于辅助交易决策的数值序列。

分类：

1. 均线型：反映一段时间内的平均成本；具有一定的压力或支撑作用；MA、EXPMA、BBI...
2. 趋势型：适用于趋势类的行情；检测趋势的启动、延续，还有可能的转折；MACD、SAR、ASI、DMI...
3. 摆动型：适用于震荡类的行情；检测超买超卖、波动走势的可能转折点；KDJ、RSI、CCI、WR、BOLL...
4. 能量型：度量涨跌的力度，预示价格位移的可持续性；依据是“量在价先，量价配合”；OBV、VOL、VR...

#### MA-移动均线(Moving Average)

$$ MA10_k = \cfrac{1}{10} \sum_{i = k-9}^k {Price_i} (k=10\cdots n) $$

用Python计算MACD：

```python
import pandas as pd

# the data type of "close" is pd.Series
def calc_macd(close, long, short, mid):
    diff = close.ewm(span=short).mean()-close.ewm(span=long).mean()
    dea= diff.ewm(span=mid).mean()
    macd= (diff - dea) * 2
    return (diff, dea, macd)
```

#### KD-随机指数

$$ \%K = 100\times \cfrac{Close-min_n Low}{max_nHigh-min_nLow}  $$

$$\%D = MA(\%K,N)$$

#### RSI-相对强弱指数

$$RS = \cfrac{\sum_1^nMAX(Close-LC, 0)}{\sum_1^n|Close-LC|}$$

$$RSI = 100 - \cfrac{100}{1+RS}$$

#### 技术指标的应用技巧

1. 信号：价格突破/指标突破、均线交叉/指标交叉、顶背离/底背离
2. 用途：预警、确认、预测
3. 决策：趋势跟踪、高抛低吸
4. 动作：买入、卖出、观望

#### 技术指标的应用原则

客观看待，理性应用

- 扬长避短
  - 间接性、滞后性、钝化
  - 连续背离现象
  - 时间周期相关
- 综合判断
  - 靠单一指标解决问题不现实
  - 交叉验证，辅助决策
- 概率思维
  - 行情多变，市场不可预测
  - 量化即概率，大数定律

### 更多的交易决策依据

- 基本面：业绩表现、潜力大小、是否抗跌
- 资金面：大盘/板块资金流向、个股资金流向、主力大单的表现
- 技术面：趋势方向如何、涨跌空间大小、有无买卖信号
- 其他：市场情绪、利空/利多的消息、公告事件

### 集合竞价

#### 撮合交易原理

- 撮合交易是指交易所的计算机交易系统对买卖双方的交易指令进行配对的过程
- 撮合成交的前提是买入价大于或者等于卖出价：
  - 相等：“买入价/卖出价”作为成交价
  - 不等：“买入价、卖出价、前一成交价，取三者居中的那个价格”作为成交价
- 基本原则： 按价格优先、时间优先的原则进行

#### 集合竞价时间线

09:15~09:20：接受买卖申报，也可撤单申报

09:20~09:25：开盘集合竞价阶段，不接受撤单申报

09:25：产生（当日该股的）开盘价：按价格优先和时间优先的原则计算各价位的成交量，最后以最大成交量的价格作为成交价

09:25~09:30：只接受买卖申报，但不可撤单，也不做处理

09:30：进入正常交易（连续竞价）阶段

### 除权、复权

#### 除权/除息原因

1. 因为以下事件，每股对应的权益发生了变化
   - 分红：派息、送股、转股（转增）
   - 融资：配股
2. 为公平起见，需要对股价进行修正。该过程就是“除权/除息”

#### 复权原因

除权/除息使得股价（每股代表的权益）发生了跳变。为便于观察股价的正常波动，将扣除的权息再回补过去（修复股价的跳变），该过程就是“复权”。

#### 复权方式

- 前复权
- 后复权
- 定点复权
- 不复权

### 打新、配股

#### 打新股

- 所谓“打新”，是指个人或机构投资者用资金参与新股的申购，如果（配号）中签且预存资金充足的话，就买到了即将上市的股票
- 因为IPO通常折价发行，所以新上市的股票往往短期上涨的概率较大，所以如果打新成功，收益稳风险低，因此“打新申购”非常受投资者的青睐
- 温馨提示：两个交易所均配置有底仓；维持一定的底仓市值额度；风险意识

#### 配股

- 上市公司向原股东按其持股比例，以低于市价的某一特定价格配售一定数量新发行股票的融资行为
- 在股权登记日收市清算后仍持有该股，则自动享有配股权利；需在缴款期内参加配股，逾期不操作，即为放弃配股权利
- 一般配股价越低（也就是对老股东折让的幅度越大），参与配股越合算。但受除权和配股募资投向等影响，并不意味着稳赚不赔

### 公告研报社交媒体

是面向量化的非结构化数据处理基础。

#### 处理非结构化数据的相关技术：

- 渠道和获取：接口、抓取、购买
- 数据清洗、格式转换：网页、PDF、图片
- 分析、处理和存储：非结构化到半结构化/结构化：NLP、统计语言模型、规则
- 应用方式：独到视角、演进分析、建模

### 趋势分析和量价分析

趋势分析和量价分析是技术派量化的逻辑基础 。

#### 趋势分析

趋势即牛熊，需关注三个关系：

- 供需关系：趋势的动力来自于供需关系的不平衡
- 因果关系：趋势形成之前需要准备过程
- 努力和结果关系：成交量的增长没有使价格大幅增长，这是走势停止行为

#### 对支撑和压力的理解：

支撑：

- 在某个价位购买力超过了抛售压力，需求吸收了全部供应
- 当价格再次回到支撑位，反弹力度表明需求质量

压力：

- 某个价位抛售力量超过了购买力，供应超过了需求
- 当价格再次回到压力位，价格回落力度表明供应是否扩大

#### 量价时空

- 量：供应和需求投入的兵力
- 价：供应和需求当前的强弱
- 时：供应和需求拉锯的过程长度
- 空：供应和需求战场的广阔程度

#### 量价分析的核心问题

还是三个关系： 

- 供需关系：
  - 质量
  - 力量
- 因果关系：
  - 过程
  - 时空
- 努力和结果关系：
  - 显性
  - 隐性



### 参考书籍

- 《打开量化投资的黑箱》 

  Inside the Black'Box:A Simple Guide to Quantitative and High-Frequency Trading 

  里什•纳兰(Rishi K.Narang)  

- 《主动投资组合管理:创造高收益并控制风险的量化投资方法》 

  Active Portfolio Management: A Quantitative Approach for Providing Superior Returns and Controlling Risk (2th Edition) 

  理查德C.格林诺德(Richard C.Grinol) , 雷诺德N.卡恩(Ronald N.Kahn) , 李腾 (译者)

- 《威科夫操盘法》

  Wychkoff Trading Tools and Techniques 

  孟洪涛 （Edward Meng） 

- 《证券分析》 

  Security Analysis: Sixth Edition 

  本杰明•格雷厄姆 (Benjamin Graham) , 戴维•多德 (David L. Dodd)  
  
  
## 三、量化交易策略实战技巧 

### 1. 股票池择时策略基础

#### 1.1 交易系统中与盈利相关的要素

- 策略的胜率（系统的期望收益 ）
- 每次交易的盈亏比（系统的期望收益 ）
- 头寸规模的确定
- 资金量的大小
- 交易机会的多少
- 交易成本

<!--more-->

#### 1.2 Alpha 的非常规定义

Alpha 的非常规定义：在交易中关于持有头寸选择和买卖时机把握的技巧，即股票池+择时。

#### 1.3 股票池

构建股票池：多因子分析

典型的对冲策略：股票alpha策略

$$
(Alpha+Beta) -Beta = Alpha
$$

- alpha+beta：做多股票组合
- -beta：做空股指期货
- alpha：组合超额收益

Alpha策略不需要依靠对证券组合或大盘的趋势判断，而是追求对冲系统风险后的绝对收益，即做到无论大盘涨跌都能赚钱。

常见因子：PE、PB、ROE、ROA

#### 1.4 择时

随机入市策略：

- 每次凭掷硬币随机进入市场，或者做多头，或者做空头 
- 一旦得到一个退出市场的信号，就基于随机信号再次入市 
- 用EMA(ATR,10)指标来确定市场的波动性
- 用这一波动性得数的3倍作为初始止损
- 跟踪止损，只按照对盈利有利的方式移动（多头向上，空头向下） 

结论：入市时间不是最重要的

其他因素策略：

- 头寸：根据波动率分配头寸 
- 止损：波动率倍数设置初始止损
- 退出：回撤止盈
- 风控：策略内外的风控

### 2. 主流投资流派的量化策略

#### 2.1 五大门派

| 投资模式 |    代表人物     |    价格-价值关系     |    时间尺度    |                          方法                          |
| :------: | :-------------: | :------------------: | :------------: | :----------------------------------------------------: |
| 价值投资 | 格雷厄姆/巴菲特 |  不定，而且可以确定  |    从月到年    |    关注于价值，寻找那些定价低 于内在价值的投资对象     |
| 成长投资 |    费雪/林奇    |  不定，而且可以确定  |    从月到年    | 关注于增长，寻找价值增长速度快于价格增长速度的投资对象 |
| 指数投资 |      伯格       |       不能确定       |    从月到年    |       忽略价格-价值关系，而购买整个市场的一部分        |
| 技术投资 |     奥尼尔      | 可能有关系，但不相关 | 秒、分钟到数周 |                     关注于价格趋势                     |
| 组合投资 |     麦基尔      |       相互独立       |  数日到月、年  |          将风险偏好与价格-价值风险水平相匹配           |

#### 2.2 五大门派的量化要素

- 价值投资：关注于对估值因素的量化，更多从基本面分析的角度，考察一个公司的商业逻辑所对应的数据指标，并建立相应的财务分析、行业分析量化模型，最终形成对公司价值的估算
- 成长投资：关注于对公司成长能力的量化，与价值投资类似，只不过量化模型偏重于价值的增长速度而不仅仅是价值本身
- 指数投资：关注于对某一基准指数的跟踪模型，即试图尽量准确地跟踪基准指数的变化；一些指数型投资策略，还侧重于指数增强，即通过对基准进行择时或者对成份股进行筛选来实现相对于指数的一定超额回报
- 技术投资：关注于量、价、时、空的各种统计规律的分析和建模，也通过很多技术指标来反映对价格趋势的预测；随着大数据与人工智能技术的发展，也有很多技术投资者通过市场情绪的监测、对市场外部数据的分析来寻找价格趋势与各种数据的相关性，采用数据驱动模型作为量化交易系统的判断依据
- 组合投资：关注于对投资组合风险水平的估算以及获得最佳的风险-收益机会集

### 3. 多因子模型和因子检验 

#### 3.1 因子投资的发展 

- 单因子：市场对风险和回报的认识是单一的
- 多因子：市场对风险和回报有多维度的认识
- 市场异常回报：无法被其他因子所解释
- 因子投资：为投资人提供因子回报和敞口；有单因子基金，也有多因子组合

#### 3.2 美股因子检验–定义

- 大市值：市场上市值最大的前10%的股票
- 小市值：市场上市值最小的前10%的股票
- 高价值：市场上账面市值比（Book-to-MarketRatio）最高的前10%的股票
- 高动量：市场上过去12个月总回报最高的前10%的股票
- 低波动：市场上相对于大盘的beta最低的前10%的股票
- 高质量：市场上利润率最高的前10%的股票

#### 3.3 美股因子检验–回报

| 1970-2017 | 年化回报 | 夏普比率 | 最大回撤 | 总回报     |
| --------- | -------- | -------- | -------- | ---------- |
| 大市值    | 10.15%   | 0.39     | -52.81%  | 9464.59%   |
| 小市值    | 13.11%   | 0.45     | -63.10%  | 33227.16%  |
| 高价值    | 20.06%   | 0.72     | -70.75%  | 554107.81% |
| 高动量    | 18.71%   | 0.66     | -59.38%  | 325281.13% |
| 低波动    | 13.10%   | 0.62     | -56.95%  | 33140.59%  |
| 高质量    | 12.70%   | 0.45     | -62.21%  | 27980.31%  |
| 标普500   | 10.51%   | 0.42     | -50.21%  | 11020.50%  |

每种因子都有其周期性，都不可能在短时间内跑赢大盘，选择哪个因子要与投资人的风险承受能力匹配。只有在可靠的投资框架内坚持自己的投资理念，与自己的认知缺陷抗衡，投资人才有可能在较长的投资期限上战胜大盘。



### 参考书籍

- 《打开量化投资的黑箱》 

  Inside the Black'Box:A Simple Guide to Quantitative and High-Frequency Trading 

  里什•纳兰(Rishi K.Narang)  

- 《主动投资组合管理:创造高收益并控制风险的量化投资方法》 

  Active Portfolio Management: A Quantitative Approach for Providing Superior Returns and Controlling Risk (2th Edition) 

  理查德C.格林诺德(Richard C.Grinol) , 雷诺德N.卡恩(Ronald N.Kahn) , 李腾 (译者)

- 《威科夫操盘法》

  Wychkoff Trading Tools and Techniques 

  孟洪涛 （Edward Meng） 

- 《证券分析》 

  Security Analysis: Sixth Edition 

  本杰明•格雷厄姆 (Benjamin Graham) , 戴维•多德 (David L. Dodd)  


## 国内外 在线量化平台

[BigQuant](https://bigquant.com/) - 你的人工智能量化平台可以无门槛地使用机器学习、人工智能开发量化策略，基于python，提供策略自动生成器     
[镭矿](http://www.raquant.com/) - 基于量化回测平台  
[果仁网](http://guorn.com/) - 回测量化平台  
[京东量化](http://quant.jd.com/) - 算法交易和量化回测平台  
[优矿](http://uqer.io/home/) - 通联量化实验室  
[Ricequant](http://www.ricequant.com/) - 量化交易平台  
[况客](http://qutke.com/) - 基于R语言量化回测平台   
聚宽 - 量化回测平台   
Factors - 数库多因子量化平台    
诸葛量化 - 量化交易平台    
宽狗量化 - 回测量化平台    

python派量化金融社区   http://www.pythonpai.com 

国外量化平台：

     Quantopian 研究、回测、算法众包平台 
     QuantConnect 研究、回测和投资交易 
     Quantstart 研究、回测和投资交易、数据科学网站 
     ASC 研究、交易平台 
     zulutrade 自动交易平台 
     quantpedia 研究、策略平台 
     algotrading101 策略研究平台 
     investopedia 可以股票、外汇模拟交易的财经网站 
     Amibroker 提供系统交易工具的一家公司 
     AlgoTrades 股票、ETF、期货自动交易系统 
     Numerai 数据工程师众包的一家对冲基金 
     WealthFront 财富管理平台 
     Betterment 个人投资平台 
     TradeLink 量化交易平台 
     ActiveQuant 基于JavaScript开源交易开发框架 
 
 
## 相关平台
[掘金量化](http://www.myquant.cn/) - 支持C/C++、C#、MATLAB、Python和R的量化交易平台  
[DigQuant](http://www.digquant.com.cn/) - 提供基于matlab量化工具  
[SmartQuant](http://www.smartquant.cn/) - 策略交易平台  
[OpenQuant](http://github.com/QuantBox/OpenQuant-Esunny) - 基于C#的开源量化回测平台  

## 基于图表的量化交易平台
 文华赢智 、TB、金字塔、MultiCharts 中国版 - 程序化交易软件、MT4、TradeStation 
 Auto-Trader - 基于MATLAB的量化交易平台 
 BotVS - 首家支持传统期货与股票证券与数字货币的量化平台 
 
## 开源框架

[Pandas](http://github.com/pandas-dev/pandas) - 数据分析包  
[Zipline](http://github.com/quantopian/zipline) - 一个Python的回测框架  
[vnpy](http://github.com/vnpy/vnpy) - 基于python的开源交易平台开发框架  
[tushare](http://pypi.python.org/pypi/tushare/) - 财经数据接口包  
[easytrader](http://github.com/shidenggui/easytrader) - 进行自动的程序化股票交易  
[pyalgotrade](http://github.com/gbeced/pyalgotrade) - 一个Python的事件驱动回测框架  
[pyalgotrade-cn](http://github.com/Yam-cn/pyalgotrade-cn) - Pyalgotrade-cn在原版pyalgotrade的基础上加入了A股历史行情回测，并整合了tushare提供实时行情。   
[zwPython](http://github.com/ziwang-com/) - 基于winpython的集成式python开发平台     
[quantmod](http://github.com/joshuaulrich/quantmod) - 量化金融建模   
[rqalpha](http://github.com/ricequant/rqalpha/) - 基于Python的回测引擎   
[quantdigger](http://github.com/QuantFans/quantdigger) - 基于python的量化回测框架   
[pyktrader](http://github.com/harveywwu/pyktrader) - 基于pyctp接口，并采用vnpy的eventEngine，使用tkinter作为GUI的python交易平台   
[QuantConnect/Lean](http://github.com/QuantConnect/Lean) - Lean Algorithmic Trading Engine by QuantConnect (C#, Python, F#, VB, Java)   
[QUANTAXIS](http://github.com/yutiansut/QUANTAXIS) - 量化金融策略框架   

## 库
[pandas](http://pandas.pydata.org/) - Python做数据分析的基础   
[pyql](http://github.com/enthought/pyql) - Cython QuantLib wrappers   
[ffn](http://pmorissette.github.io/ffn/quick.html) - 绩效评估   
[ta-lib](http://github.com/mrjbq7/ta-lib): Python wrapper for TA-Lib (http://ta-lib.org/). - 技术指标   
[StatsModels](http://statsmodels.sourceforge.net/): Statistics in Python — statsmodels documentation - 常用统计模型   
[arch](http://github.com/bashtage/arch): ARCH models in Python - 时间序列   
[pyfolio](http://github.com/quantopian/pyfolio): Portfolio and risk analytics in Python - 组合风险评估   
[twosigma/flint](http://github.com/twosigma/flint): A Time Series Library for Apache Spark - Apache Spark上的时间序列库  

## 数据源
[TuShare](http://tushare.org/) - 中文财经数据接口包      
[Quandl](http://www.quandl.com/) - 国际金融和经济数据   
[Wind资讯-经济数据库](http://www.wind.com.cn/NewSite/edb.html) - 收费   
[东方财富 Choice金融数据研究终端](http://choice.eastmoney.com/Product/index.html) - 收费   
[iFinD 同花顺金融数据终端](http://www.51ifind.com/) - 收费   
[朝阳永续 Go-Goal数据终端](http://www.go-goal.cn/) - 收费   
[天软数据](http://www.tinysoft.com.cn/TSDN/HomePage.tsl) - 收费   
[国泰安数据服务中心](http://www.gtarsc.com/) - 收费   
[锐思数据](http://www.resset.cn/) - 收费   
[恒生API](http://open.hscloud.cn/) - 收费   
[Bloomberg API](http://www.bloomberglabs.com/api/libraries/) - 收费   
[数库金融数据和深度分析API服务](http://developer.chinascope.com/) - 收费   
[Historical Data Sources](http://quantpedia.com/Links/HistoricalData) - 一个数据源索引   
[预测者网](http://www.yucezhe.com/) - 收费   
[巨潮资讯](http://www.cninfo.com.cn/cninfo-new/index) - 收费   
[通联数据商城](http://www.datayes.com/) - 收费   
[通达信](http://www.tdx.com.cn/) - 免费   

## 数据库
manahl/arctic: High performance datastore for time series and tick data - 基于mongodb和python的高性能时间序列和tick数据存储   
kdb | The Leader in High-Performance Tick Database Technology | Kx Systems - 收费的高性能金融序列数据库解决方案   
MongoDB Blog - 用mongodb存储时间序列数据   
InfluxDB – Time-Series Data Storage | InfluxData - Go写的分布式时间序列数据库   
OpenTSDB/opentsdb: A scalable, distributed Time Series Database. - 基于HBase的时间序列数据库  
kairosdb/kairosdb: Fast scalable time series database - 基于Cassandra的时间序列数据库  
SQLite Home Page   

## 网站、论坛、社区、博客
[BigQuant量化社区](http://community.bigquant.com/)    
[算法组_新浪微博](http://weibo.com/u/3183064657%3Ftopnav%3D1%26wvr%3D6%26topsug%3D1)   
[海洋部落](http://www.oceantribe.org/xf/index.php)   
[水木社区](http://www.newsmth.net/)   
[（经管之家）人大经济论坛](http://bbs.pinggu.org/forum-2166-1.html)  
[清华大学学生经济金融论坛](http://forum.thuquant.com/)   
[Code4Quant](http://code.tradeclassroom.com/)   
[量化交易 - 热门问答 - 知乎](https://www.zhihu.com/topic/19815465/hot)   
[集思录 - 低风险投资 - 集思录](http://www.jisilu.cn/)   
[雪球 - 聪明的投资者都在这里](http://xueqiu.com/%23/)   
[myquant/strategy: 掘金策略集锦](http://github.com/myquant/strategy/)   
[芝诺量化交易,程序化交易](http://www.zenotrade.com/)   
[统计之都 (Capital of Statistics)](http://cos.name/)   
[中国量化投资学会](http://www.chinaqi.org/default.php)   
[宽客 (Quant) - 索引 - 知乎](https://www.zhihu.com/topic/19557481)   
[faruto的博客](http://blog.sina.com.cn/s/blog_4cf8aad30102e5dh.html)   
[david自由之路](http://blog.sina.com.cn/financialindependence)   
[债券的大拿没钱又丑](http://wangzhai2008.blog.hexun.com/)   
[期货用来复盘的blog](http://huzi2010.blog.hexun.com/)   
[股海泛舟 - 股海范舟](http://xman707.blog.163.com/)   
[带头大哥777的博客](http://dtdg777.blog.163.com/)   

## 交易API
[上海期货信息技术有限公司CTP API](http://www.sfit.com.cn/5_2_DocumentDown.htm) - 期货交易所提供的API   
[飞马快速交易平台](http://www.cffexit.com.cn/static/3000201.html) - 上海金融期货信息技术有限公司 - 飞马   
[大连飞创信息技术有限公司](http://www.dfitc.com.cn/portal/cate%3Fcid%3D1364967839100%231) - 飞创  
[vnpy](http://github.com/vnpy/vnpy) - 基于python的开源交易平台开发框架   
[QuantBox/XAPI2](http://github.com/QuantBox/XAPI2) - 统一行情交易接口第2版   
[easytrader](http://github.com/shidenggui/easytrader) - 提供券商华泰/佣金宝/银河/广发/雪球的基金、股票自动程序化交易，量化交易组件   
[IB API | Interactive Brokers](http://www.interactivebrokers.com.hk/cn/index.php%3Ff%3D5234%26ns%3DT) - 盈透证券的交易API   

## 书籍
```
《投资学》第6版[美]兹维·博迪.文字版 
《打开量化投资的黑箱》 里什·纳兰
《宽客》[美] 斯科特·帕特森（Scott Patterson） 著；译科，卢开济 译
《解读量化投资：西蒙斯用公式打败市场的故事》 忻海 
《Trends in Quantitative Finance》 Frank J. Fabozzi, Sergio M. Focardi, Petter N. Kolm
《漫步华尔街》麦基尔
《海龟交易法则》柯蒂斯·费思
《交易策略评估与最佳化》罗伯特·帕多
《统计套利》 安德鲁·波尔《信号与噪声》纳特•西尔弗
《期货截拳道》朱淋靖
《量化投资—策略与技术》 丁鹏
《量化投资—以matlab为工具》 李洋faruto
《量化投资策略:如何实现超额收益Alpha》 吴冲锋
《中低频量化交易策略研发（上）》 杨博理
《走出幻觉走向成熟》 金融帝国
《通往财务自由之路》范K撒普
《以交易为生》 埃尔德
《超越技术分析》图莎尔·钱德
《高级技术分析》布鲁斯·巴布科克
《积极型投资组合管理》格里纳德，卡恩
《金融计量学:从初级到高级建模技术》 斯维特洛扎
《投资革命》Bernstein
《富可敌国》Sebastian Mallaby
《量化交易——如何建立自己的算法交易事业》欧内斯特·陈
《聪明的投资者》 巴菲特
《黑天鹅·如何应对不可知的未来》 纳西姆·塔勒布
《期权、期货和其他衍生品》 约翰·赫尔
《Building Reliable Trading Systems: Tradable Strategies That Perform As They Backtest and Meet Your Risk-Reward Goals》 Keith Fitschen
《Quantitative Equity Investing》by Frank J. Fabozzi, Sergio M. Focardi, Petter N. Kolm
Barra USE3 handbook
《Quantitative Equity Portfolio Management》 Ludwig Chincarini
《Quantitative Equity Portfolio Management》 Qian & Hua & Sorensen
```
----
[1]银行管存：银行存管是由银行管理资金，平台管理交易，做到资金与交易的分离，使得平台无法直接接触资金，避免客户资金被直接挪用。[查询地址](http://www.p2peye.com/platform/bank/)
[2]Quant：宽客，设计并实现金融的数学模型（主要采用计算机编程），包括衍生品定价，风险估价或预测市场行为等。



编程

Python

    安装
     Anaconda - 推荐通过清华大学镜像 下载安装 
     Pycharm download 
     Python Extension Packages for Windows - Christoph Gohlke - Windows用户从这里可以下载许多python库的预编译包 
 
教程

     Python | Codecademy 
     用 Python 玩转数据 - 南京大学 | Coursera 
     Google 开源项目风格指南 (中文版) 
     廖雪峰python教程 
     Introduction to Data Science in Python - University of Michigan | Coursera 
     The Python Tutorial 
     Python for Finance 
     Algorithmic Thinking - Python 算法思维训练 
     Python Cookbook 3rd Edition Documentation  
 
库

     Python Extension Packages for Windows 
     awesome-python: A curated list of awesome Python frameworks, libraries, software and resources 
     pandas - Python做数据分析的基础 
     pyql: Cython QuantLib wrappers 
     ffn - 绩效评估 
     ta-lib: Python wrapper for TA-Lib (http://ta-lib.org/). - 技术指标 
     StatsModels: Statistics in Python — statsmodels documentation - 常用统计模型 
     arch: ARCH models in Python - 时间序列 
     pyfolio: Portfolio and risk analytics in Python - 组合风险评估 
     twosigma/flint: A Time Series Library for Apache Spark - Apache Spark上的时间序列库 
 
R 安装

     The Comprehensive R Archive Network - 从国内清华镜像下载安装 
     RStudio - R的常用开发平台下载 
 
教程

     Free Introduction to R Programming Online Course - datacamp的在线学习 
     R Programming - 约翰霍普金斯大学 | Coursera 
     Intro to Computational Finance with R - 用R进行计算金融分析 
 
库

     CRAN Task View: Empirical Finance - CRAN官方的R金融相关包整理 
     qinwf/awesome-R: A curated list of awesome R packages, frameworks and software. - R包的awesome 
 
C++ 教程

     C++程序设计 - 北京大学 郭炜 
     基于Linux的C++ - 清华大学 乔林 
     面向对象程序设计（C++） - 清华大学 徐明星 
     C++ Design Patterns and Derivatives Pricing - C++设计模式 
     C++ reference - cppreference.com - 在线文档 

库

     fffaraz/awesome-cpp: A curated list of awesome C/C++ frameworks, libraries, resources, and shiny things. - C++库整理 
     rigtorp/awesome-modern-cpp: A collection of resources on modern C++ - 现代C++库整理 
     QuantLib: a free/open-source library for quantitative finance 
     libtrading/libtrading: Libtrading, an ultra low-latency trading connectivity library for C and C++. 
    Julia 教程
     Learning Julia - 官方整理 
     QUANTITATIVE ECONOMICS with Julia - 经济学诺奖获得者Thomas Sargent教你Julia在量化经济的应用。 
    库
     Quantitative Finance in Julia - 多数为正在实现中，感兴趣的可以参与 
 
编程论坛

     Stack Overflow 
     SegmentFault 
     Quora 
     Github 
     知乎 - 与世界分享你的知识、经验和见解  
 
编程能力在线训练

     Solve Programming Questions | HackerRank - 包含常用语言(C++, Java, Python, Ruby, SQL)和相关计算机应用技术(算法、数据结构、数学、AI、Linux Shell、分布式系统、正则表达式、安全)的教程和挑战。 
     LeetCode Online Judge - C, C++, Java, Python, C#, JavaScript, Ruby, Bash, MySQL在线编程训练 
     


     
