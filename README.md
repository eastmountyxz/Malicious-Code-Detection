# Malicious-Code-Detection
该资源为恶意代码检测与识别的相关链接汇总，希望对您有所帮助！


- https://github.com/tennc/webshell

这是一个webshell收集项目

送人玫瑰，手有余香，如果各位下载了本项目，也请您能提交shell

本项目涵盖各种常用脚本

如：asp,aspx,php,jsp,pl,py


- https://github.com/ysrc/webshell-sample

收集自网络各处的 webshell 样本，用于测试 webshell 扫描器检测率。


- https://zhuanlan.zhihu.com/p/23000035
史上最全的恶意软件地址集合


- https://blog.csdn.net/mypc2010/article/details/77776870/
最新webshell大合集
收集与整理了各种webshell，以便在日后的项目中做Webshell检测训练。



- https://blog.csdn.net/answer3lin/article/details/82966360
https://xz.aliyun.com/t/1879
网络安全数据集

本文主要收录安全相关的数据集，适合初创，中小型企业用于训练和验证自己的机器学习的模型，提高准确率和准确度。
由于数据集可能比较多，一开始也不能全部列举出来，所以后续会慢慢补充，慢慢增加。


https://github.com/foospidy/payloads


- 恶意Web请求数据集
https://github.com/Echo-Ws/UrlDetect

https://github.com/exp-db/AI-Driven-WAF





- https://blog.csdn.net/u011311291/article/details/79045675

数据集：
1.KDD99 网络流量数据集，有dos,u2r,r21,probe等类行攻击
2.HTTP DATASET CSIC 2010，包含sql注入，缓冲区溢出，信息泄露，文件包含，xss等
3.SEA数据集，记录了UNIX用户的操作指令（例如cpp,sh等命令）。
4.ADFA-LD数据集，用户系统命令数据集
5.Alexa域名数据，提供了全球排名TOP一百万的网站域名。
6.MNIST数据集，入门级的计算机视觉数据集，例如手写数字图片。
7.Movie Review Data数据集，包含了1000条正面评论，1000条负面评论
8.SpamBase数据集，入门级垃圾邮件分类训练集
9.Enron数据集，垃圾邮件数据集
10.域名生成算法DGA常见的两个家族cryptolocker和post-tovargoz

K邻近算法：
1.使用SEA数据集，基于用户使用哪条命令，和最不频繁使用哪条命令的频繁度生成特征，结果准确率80%。
2.继续使用SEA数据集，但是是全量比较，基于词集，结果准确率93%。
3.从KDD99数据集中只挑选出Rootkit数据，结果准确率90%。
4.使用ADFA-LD数据集中的WEBShell数据（其实是服务器经过WEBShell攻击后出来的系统命令），基于WebShell对系统调用的行为，形成词集，结果准确率95%。

决策树
1.使用KDD99 POP3的相关数据，准确率为99%
2.使用ADFA-LD数据集中FTP暴力破解的数据（系统命令），准确率95%。

随机森林
1.使用ADFA-LD数据集中FTP暴力破解的数据（系统命令），准确率98%。

朴素贝叶斯
1.使用SEA数据集，但是是全量比较，基于词集，准确率92%。
2.在互联网上搜集到的WebShell黑样本，然后使用wordpress源码作为白样本，然后将PHP原文件作为字符串处理，基于2-gram切词生成词汇表，准确率为80%。
3.在互联网上搜集到的WebShell黑样本，然后使用wordpress源码作为白样本，然后将PHP原文件作为字符串处理，基于1-gram切词生成词汇表，准确率为96%。
4.检测DGA域名，基于2-gram切词生成词汇表，准确率93%。
5.检测DDoS攻击，基于筛选DDoS相关特征，网络连接基本特征，基于时间的网络流量统计特征，基于主机的网络流量统计特征，向量化后形成特征矩阵，准确率99%。
6.识别验证码，通过MNIST数据集进行训练，准确率在55%，因为贝叶斯算法不擅长于多分类。

逻辑回归
1.使用ADFA-LD数据集中Java溢出攻击的相关数据，然后基于词集，准确率93%。
2.识别验证码，通过MNIST数据集进行训练，准确率80%。

支持向量机SVM
1.检测XSS，基于专业的对URL进行敏感字符，关键字个数决定，准确率90%。
2.区分DGA家族，基于:
a.元音字母个数和比例
b.去重后的字母个数与原域名长度的比列
c.基于2-gram的平均jarccard系数，即两个集合交集与并集元素个数的比值
d.基于HMM模型，即以常见英文单词训练的HMM模型，这样正常域名的HMM系数会偏高。
准确率不明。

K-means
1.用于DGA cryptolocker和post-tovargoz和正常样本聚类，虽然没有给出准确率，但使用TSNE降维看图，效果还不错

DBSCAN（Density-Based Spatial Clustering of Applications with Noise），基于密度的聚类算法
1.用于DGA cryptolocker和post-tovargoz和正常样本聚类，虽然没有给出准确率，但使用TSNE降维看图，效果好像比K-means好

Apriori
1.使用在WAF的accesslog与后端数据库的sqllog，识别SSH操作日志中异常操作，发现关联关系，然后用作SVM的特征提取依据

FP-growth
1.分析防火墙的拦截日志，使用攻击源ip,浏览器user-agent字段和被攻击的目标URL之间，挖掘出浏览器的user-agent字段和被攻击的目标URL之间的关联关系。使用

隐马尔可夫算法（HMM）
1.通过学习正常XSS来识别异常，以白找黑例如：
a.[a-zA-Z]可范化为A
b.[0-9]范化为N
c.[-_]范化为C
d.其它字符都范化为T
这样userid=%3Cscript%3Ealert(1)%3C/script%3E为例，可得TAAAAAATAAAAATNTTTAAAAAAT,score=-13945识别为异常
2.通过学习异常XSS来识别异常，以黑找黑
3.通过计算DGA cryptolocker和post-tovargoz的score值()可以为使用SVM对DGA算法分类提供特征

图算法概述:
1.使用有向图识别WebShell
2.使用有向图识别僵尸网络，通过一段时间的观察，统计攻击源IP和被攻击者域名之间的关联关系，可以确定哪些IP是被同
一个黑产团体控制。

知识图谱在风控领域的应用
1..检测疑似账号被盗，将uid,ip,tel,activesyncid(客户端与硬件绑定的id)连成一张图，但其实主要看的是activesyncid连了多少uid(同一台设备尝试登录不同的账号)。
2.检测疑似刷单，hid(硬件指纹,唯一标识一台设备),uid,app，action（买，卖行为），如果发现买，卖在同一台设备，则有可能刷单。
3.应用于威胁情报领域

神经网络(只使用隐藏层为一层的神经网络)
1.使用神经网络对MNIST验证进行分类，准确率97%。
2.使用神经网络检测Java溢出攻击，准确率87%。

深度神经网络(DNN，Deep Neural Network)就是一种全连接的错层感知机。
卷积神经网络(CNN,Convolutional Neural Network)
循环神经网络(RNN,Recurrent Neural Network)
多层感知机与DNN算法（待看）
1.使用TensorFlow中的softmax回归算法识别MNIST验证码，将验证码通过one-hot编码，准确率90%
2.使用TensorFlow中的多层感知机算法识别MNIST验证码，将验证码通过one-hot编码，准确率96%
3.使用TensorFlow中的DNN算法识别MNIST验证码，将验证码通过one-hot编码，准确率93%
4.使用高斯朴素贝叶斯GaussianNB识别SpamBase垃圾邮件，该SpamBase数据集已经向量化好了，准确率82%
5.使用TensorFlow中的DNN算法识别SpamBase垃圾邮件，该SpamBase数据集已经向量化好了，准确率87%

循环神经网络(RNN)
特点:会回忆以前类似的场景是如何解决的，温故而知新，即隐藏层之间的节点不再无连接，而是有连接的
有时候需要追溯到以前更长的记忆，提出LSTM（Long short term memory）
1.使用构造RNN神经网络，LSTM算法识别MNIST数据集，准确率95%
2.使用高斯朴素贝叶斯GaussianNB辨别Movie Review Data影评数据集正负面，准确率51%
3.使用构造RNN神经网络，LSTM算法辨别Movie Review Data影评数据集正负面，准确率61%
4.使用Us.Cities.txt数据集使用RNN,LSTM算法随机生成城市名
5.使用RNN,LSTM算法识别ADFA-LD数据集，基于系统命令调用时序，准确率93%
6.使用RNN,LSTM算法基于WVS自带的密码字典作为训练集自动生成常用密码
7.使用RNN,LSTM算法基于SEA数据集识别UNIX系统异常操作，准确率94%

卷积神经网络(CNN)
1.使用CNN识别MNIST验证码，准确率99%
2.使用CNN辨别Movie Review Data影评数据集正负面，准确率66%
3.使用CNN辨别垃圾邮件，其中对文本的处理为使用一维卷积函数，并且基于词袋模型的改进，使用生成的词汇表对原有句子
按照单词逐个进行编码，准确率98%



