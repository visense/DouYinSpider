DouYinSpider
===============
此Github包含两个抖音爬虫：  
第一个为github用户[loadchange](https://github.com/LoadChange/amemv-crawler)的代码，位于amemv-crawler目录下：
```
“ 可以下载指定抖音用户的全部视频(含收藏)，也可以下载指定主题(挑战)或音乐下的全部视频。”
```  
其优势为爬取速度快，系统资源占用少，但是不能够筛选特定的视频，如此项目的仅下载 **竖屏广告** 

indepent目录下的本人的代码，通过安卓模拟器，抓取抖音对应视频及视频数据，此项目抓取的目标视频为抖音随机出现的 **竖屏广告** 
实际使用时可以根据自身 **测试学习** 需求修改FlowCatch.py逻辑
## 开发环境
>
>* Python3
>* Android environment
>* Appium
>* Mitmproxy


## 注意

这个项目是一个**练手项目**，源码仅作为和大家一起**学习Python**使用，你可以免费: 拷贝、分发和派生当前源码。你不可以用于*商业目的*及其他*恶意用途*。

## 环境安装
1. Android environment
    >   * 建议通过[Android Studio](https://developer.android.google.cn/studio/)安装JDK，配置[环境变量](https://blog.csdn.net/zeternityyt/article/details/79655150)
    >   * 安装JAVA [SDK](https://blog.csdn.net/u012382791/article/details/50891044)
    >   * 安卓模拟器: 常用的模拟器有
    >       * genymotion（收费）
    >       * 天天模拟器
    >       * 夜神模拟器
    >       * 领航模拟器
    >       * 这里使用[天天模拟器](http://www.kpzs.com/topic/ttmnqsgou/)作为测试
2. Appium
    >    * [Appium](https://github.com/appium/appium-desktop/releases)，为类似于Selenium的移动端测试工具，建议安装桌面版
    >       <img src="https://github.com/panoslin/DouYinSpider/blob/master/pic/AppiumDownload.png" width="600">
3. Python 依赖库：
    >```bash
    >pip install -r requirement.txt
    >```
## 配置和运行

1. 首先运行天天模拟器，通过adb连接模拟器(天天默认端口*6555*)：在命令行输入
    >```bash
    >adb connect 127.0.0.1:6555
    >adb devices -l
    >```
    >第一步连接模拟器端口，如果端口连接不成功，可到ttmnq\deployed\TianTian.vbox中查看host端口（hostport）  
    >第二步显示是否连接成功，成功则会显示已连接设备信息  
    >返回结果应该如下图表示连接成功：
    ![adb](https://github.com/panoslin/DouYinSpider/blob/master/pic/adb.jpg)  
2. 通过模拟器内的“靠谱游戏”安装抖音App  
3. 安装Mitmproxy证书  
    > * 将C:\Users\UserName\\.mitmproxy 目录下面的mitmproxy-ca-cert.cer拖动到模拟器界面上安装证书  
    > * 双击运行安装mitmproxy-ca-cert.p12，选择证书存储位置为“受信任的根证书颁发机构”
4. 运行Appium服务器(默认端口*4723*)
5. 分别开启两个命令行窗口，激活虚拟环境，进入indepent目录，命令行输入
    >```bash
    >python AppiumControl.py
    >mitmdump -s .\FlowCatcher.py
    >```
    >此时模拟器便被Appium控制，自行打开抖音并且开始没日没夜的刷抖音。  
    >   <img src="https://github.com/panoslin/DouYinSpider/blob/master/pic/douyin.jpg" width="300">
