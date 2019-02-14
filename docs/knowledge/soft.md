## Powerpoint音频播放限定张数停止
1.	调出动画窗格（动画-动画窗格（添加动画旁边））
2.	右键动画窗格中音频，效果选项，停止播放，在X张幻灯片后

## 刷新:F5 & Ctrl+F5
* 一下内容针对于浏览器
* 刷新快捷键：F5（普通刷新，部分数据从缓存中获取）
* Ctrl+F5：强制刷新，所有内容重新从服务器获取，一般用于解决本地缓存出错或服务器缓存更新的情况
* Eg：电视信息课那个网页，如果打开视频是黑的，用Ctrl+F5刷新即可

## 截图相关
### 视频截图
* 正式使用时拒绝QQ截图
* 以PotPlayer播放器为例
* 打开视频，找好位置暂停，按照软件进行操作，截出的图片与原视频大小（分辨率）相同
![暂停](../img/knowledge/screen1.png "暂停")
![截图](../img/knowledge/screen2.png "截图")
![结果](../img/knowledge/screen3.png "结果")

### 普通截图
* 比尔·盖茨给你的截图键：Win附件中![Win截图](../img/knowledge/cut.png "Win截图")
* 键盘上Print Screen（Prt Scr），整个屏幕内容将会进入剪辑板，使用画图变成文件，或直接粘贴皆可

### 预览截图
* 不追求画质，QQ截图即可，方便快捷
* 需启动着QQ，快捷键`Ctrl + Alt + A`

## 在此处目录打开命令窗口
### 普通操作
* `#!js Shift + 右键`窗口会出现（不能选中文件）
* 与打开cmd，`#!js cd 目录` 相同

### Win10操作
* Win10系统中由于在此处打开命令窗口被替换为了PowerShell，如果需要使用，按以下步骤操作
* 复制以下内容至文本文档，重命名另存为.reg文件，双击运行该文件以导入
```js
Windows Registry Editor Version 5.00
[HKEY_CLASSES_ROOT\Directory\shell\OpenCmdHere]
@="在此处打开命令提示符"
"Icon"="cmd.exe"
[HKEY_CLASSES_ROOT\Directory\shell\OpenCmdHere\command]
@="PowerShell -windowstyle hidden -Command \"Start-Process cmd.exe -ArgumentList '/s,/k, pushd,%V' -Verb RunAs\""
[HKEY_CLASSES_ROOT\Directory\Background\shell\OpenCmdHere]
@="在此处打开命令窗口"
"Icon"="cmd.exe"
[HKEY_CLASSES_ROOT\Directory\Background\shell\OpenCmdHere\command]
@="PowerShell -windowstyle hidden -Command \"Start-Process cmd.exe -ArgumentList '/s,/k, pushd,%V' -Verb RunAs\""
[HKEY_CLASSES_ROOT\Drive\shell\OpenCmdHere]
@="在此处打开命令窗口"
"Icon"="cmd.exe"
[HKEY_CLASSES_ROOT\Drive\shell\OpenCmdHere\command]
@="PowerShell -windowstyle hidden -Command \"Start-Process cmd.exe -ArgumentList '/s,/k, pushd,%V' -Verb RunAs\""
[HKEY_CLASSES_ROOT\LibraryFolder\background\shell\OpenCmdHere]
@="在此处打开命令窗口"
"Icon"="cmd.exe"
[HKEY_CLASSES_ROOT\LibraryFolder\background\shell\OpenCmdHere\command]
@="PowerShell -windowstyle hidden -Command \"Start-Process cmd.exe -ArgumentList '/s,/k, pushd,%V' -Verb RunAs\""
```

### 逼格操作
1. 打开命令行： `#!js Win + X` - 命令提示符  或   `#!js Win + R` - `#!js cmd`
2. 进入目录： `#!js cd 目录`  - Eg:`#!js cd C:/`
    ![CMD-CD](../img/knowledge/cmd_cd.png "CMD-CD")

!!!tip "提示"
    * 若目录中含有空格，则在目录参数两端添加引号（英文）`""`
    * Eg:`#!js cd "C:\Program Files\"`
    
!!!note "提示"
    命令行目录数据不区分`\`和`/`

## 扩展名/后缀名相关
### 显示
* 较高版本的系统是默认不显示后缀名的
* 需要显示，按以下方法操作
* 资源管理器 - 查看（上方菜单） - 勾选文件扩展名（显示/隐藏）
    ![扩展名显示](../img/knowledge/ext.png "扩展名显示")

### 修改
1.	显示扩展名后使用重命名直接更改，会提示确认，点是即可
    ![扩展名更改](../img/knowledge/ext_change.png "扩展名更改")

!!!Warning "警告"
    虽然有时更改扩展名之后仍然可以读出源文件（正常文件），如音频文件、图片文件，但是仍然推荐根据文件格式命名
2.	Reg，Bat等本身就是文本的可以使用文本文档进行编辑，使用另存为-所有格式*.*，手动输入扩展名
    ![扩展名保存](../img/knowledge/ext_save.png "扩展名保存")

## 32位系统剪辑音(视)频（Expired Adobe/PPT/ffmpeg）

!!!success "Excellent"
    非常好，现在团委有一台64位电脑了，可以使用Au 2018剪辑音频
### Expired Adobe
* 使用Adobe CS 可以在32位系统中运行

### PPT
* 原理：2012+的PowerPoint提供了音、视频的保存功能，利用该功能进行操作
* 操作步骤：插入音频，选择裁减范围、淡化，然后进行保存
![PPT剪辑](../img/knowledge/ppt1.png "PPT剪辑")
![PPT剪辑](../img/knowledge/ppt2.png "PPT剪辑")

### ffmpeg
* 关于ffmpeg的详细内容：见ffmpeg相关
* 剪辑操作
```js
ffmpeg -ss 00:10:00 -t 00:15:00 -accurate_seek -i input.mp4 -codec copy cut.mp4
```
```js
ffmpeg -ss 开始时间（时:分:秒） -t 结束时间 -accurate_seek -i 输入文件(可以mp3) -codec copy 输出文件(与输入文件格式相同)
```

## 录屏
* 使用：[BiliBili直播姬](https://live.bilibili.com/liveHime)
* 方案仅供参考
* 录屏直播-选择显示器-不用啦-抓屏-显示器/窗口，也可以加入文本图片等
    ![录屏](../img/knowledge/live1.png "录屏")
    ![录屏](../img/knowledge/live2.png "录屏")
    ![录屏](../img/knowledge/live3.png "录屏")
* 点击确定后加入的场景会在右边显示，可以直接点左边屏幕上的选中，也可以点右边列表选中，选中后可以上下移动（按钮），删除（delete）或是切换显示（场景列表前面的眼睛）
    ![录屏](../img/knowledge/live4.png "录屏")
* 设置界面（头像右边）可以调整分辨率等信息
    ![录屏](../img/knowledge/live5.png "录屏")
* 准备就绪后单击开始录制，录制完成后会生成flv文件，生成在上方录像保存路径位置
    ![录屏](../img/knowledge/live6.png "录屏")
* Flv文件后续转码，剪辑等操作，见ffmpeg篇

## B站视频下载相关
* 使用[jjDown](https://www.jijidown.com/)

### 网页版（不推荐）
* <http://www.jijidown.com/> 或 <http://www.bilibilijj.com/>
* 如何打开：在b站.com前面加个jj
* 如：<https://www.bilibili.com/video/av26829036> 变成 <https://www.bilibilijj.com/video/av26829036> ，回车打开即可
    ![JJDown网页版](../img/knowledge/jj_web.png "JJDown网页版")
* Flv文件是有直接下载的（使用B站源），Mp3和Mp4么….看脸（原理：JJ服务器转码），如果要下一个很新/很少人看的视频
    ![JJDown等待](../img/knowledge/jj_fuck.png "JJDown等待")
* 这还是在大半夜，曾经有过几W名的，所以推荐客户端

### 客户端（推荐）
* [JJDownForWPF](http://client.jijidown.com/)
* 高版本系统不需要去关注神奇的运行环境，不过如果你XP的话还是要装.net的
* 正常使用：![JJDownWPF](../img/knowledge/jj_wpf.png "JJDownWPF")
* 打不开请安装：![Microsoft.NET](../img/knowledge/jj_net.png "Microsoft.NET")
* 还是打不开使用：![JJDownCOM](../img/knowledge/jj_com.png "JJDownCOM")
* 还是打不开进[官方BUG群](点击链接加入群聊【唧唧PC客户端BUG中心 - 3】：https://jq.qq.com/?_wv=1027&k=53AQgkG)反馈
* 你可以复制B站视频链接或是Av号（Ep等也可）至主页面输入框，在JJDown启动情况下，会自动检测剪辑板并在任务栏提示

!!!example "URL自动加载"
    ![JJDownURL](../img/knowledge/jj_url1.png "JJDownURL")
    ![JJDownURL](../img/knowledge/jj_url2.png "JJDownURL")
    ![JJDownURL](../img/knowledge/jj_url3.png "JJDownURL") 
    ![JJDownURL](../img/knowledge/jj_url4.png "JJDownURL")
* 点击URL自动加载气泡，或手动输入URL
![JJDownURLFill](../img/knowledge/jj_url_fill.png "JJDownURLFill")
* 回车即可跳转到相应页面，页面中下载：超清：720p，标清：480p
![JJDownGUI](../img/knowledge/jj_gui.png "JJDownGUI")
* 1080p：使用批量下载（左边）

![JJDown](../img/knowledge/jj_down.png "JJDown")

* FLV在设置中调整，即可自动转码MP4
![JJDownCFG](../img/knowledge/jj_cfg.png "JJDownCFG")

* 弹幕下载：XML弹幕下载后会自动变成Ass字幕文件，和同名视频放在同一文件夹，播放视频即可同步播放
* 若Ass播放很卡，请使用BiliLocal 或 [弹弹Play](http://www.dandanplay.com/)等专业XML弹幕播放软件
* 若XML弹幕播放软件有双倍弹幕，请删除Ass文件

!!!info "提示"
    * MP3文件下载原理：下载FLV视频文件，转码成为MP3
    * 所以下载MP3速度与下载MP4速度差不多
* 搜索：在首页编辑框中直接进行搜索，会跳出B站搜索界面，点击标题获取视频信息，点击后看到右下角创建完毕后即可关闭搜索界面（不会自动关闭，可以一次创建多个）
![JJDownSearch](../img/knowledge/jj_search.png "JJDownSearch")

!!!tip "提示"
    部分番剧/视频/高清版需要登陆/大会员权限才可下载（观看），点击右上角即可登录

### 你可能需要的UP
* 哔哩小红旗：<https://space.bilibili.com/86335477/#/>
* 共青团中央：<https://space.bilibili.com/20165629/#/>

### 你可能会需要的几个视频
* SSDFZ优酷账号（润梦）：<http://i.youku.com/u/UMTc0ODkwMzI4OA==>
* 邂逅（航拍2016）（朱序）（有高清不用去下）：<https://www.bilibili.com/video/av6073206> 
* 邂逅（延时2018）（李加西）（有高清不用去下）：<https://www.bilibili.com/video/av25369386> 
* 团歌（PV）（前半合唱，后半伴奏，可以剪辑操作一下）<https://www.bilibili.com/video/av25332398> 

## 一些图片格式
### TIF(F)
* 无损压缩，可以保存需要图层的图片，但是不推荐
* 可以保存透明度

!!!tip "提示"
    * 在Ps中保存TIF时会显示确认框，如需保存透明度需手动勾选
    * 推荐选择：LZW、存储透明度、扔掉图层并存储拷贝（其余保持默认）
    * ![TIFPSSave](../img/knowledge/tif_ps.png "TIFPSSave")
!!!quote "LZW"
    * 蓝波-立夫-卫曲编码法（Lempel-Ziv-Welch，缩写LZW），是亚伯拉罕·蓝波（英语：Abraham Lempel）、杰可布·立夫（英语：Jacob Ziv）与泰瑞·卫曲（英语：Terry Welch）共同提出的一种无损数据压缩算法。
    * 别名串表压缩算法
    * 通过建立一个字符串表，用较短的代码来表示较长的字符串来实现压缩。
    * 无损压缩

### PNG
* 无损压缩，保存透明度图片推荐

### JP(E)G
* 有损压缩，可以设置图片质量，根据需求进行设置

### PSD
* PS工程文件，大小根据嵌入内容而定
  
### PSB
* PS大型工程文件，用于存PSD存不下的文件（但是只有PS可以读取）
* 支持宽度或高度最大为 300,000 像素

## 压缩相关内容
* 压缩：一种通过特定的算法来减小计算机文件大小的机制
* 分：
    * 可直接读（html文件、js文件）（本质：文本文件）【删除空格、回车等不必要的标记符】
    * 不可直接读（ZIP、RAR）【使用压缩算法，必须要相应的压缩软件】

### 分卷压缩
* 将一个压缩文件进行拆分成几份，压缩卷缺一不可
* 后缀名根据压缩软件不同而不同，目前发现有.01.zip和zip.01这种格式
* 现在压缩软件很通用，无需担心

!!!note "运用：简单的文件加密"
    1. 将源文件进行分卷压缩
    2. 删除源文件，带走一份或多份压缩卷（即：移动硬盘保存一个分卷，本地磁盘保存其余分卷）
    3. 需要文件时，将移动硬盘中分卷复制至本地，解压即可
    4. 原理：分卷压缩缺卷无法解压

### 压缩文件损坏
* 在各种神奇的下载过程之中（如百度云多线程下载、IDM拼接文件出错），压缩文件可能会损坏
* 可能有两种情况：
    1. 文件写入顺序错误（正常错误，有救的）   
    2. 文件下载出错（某一分块下载了两份，某一分块没有下载，没救了，重新下）
* 我们针对1进行处理（方法二选一）【当然你在处理之前不能判定是哪种情况】
    1.	WINRAR处理
        * 下载[WinRAR压缩](http://www.winrar.com.cn/)
        * 打开压缩包，点击工具-修复压缩文件（`#!js Alt + R`）
        * 软件会进行处理，并且生成rebuilt文件，进行解压即可
    2.	Proxyee Down自带
        * 如果你装了，可以直接用
        * 如果没装，请看方法a，毕竟Winrar小得多

## SysWOW64
* 在Windows64位系统上有，C:\Windows\SysWOW64
* 目的：为了在64位系统上运行32位的软件

## API
* API（Application Programming Interface,应用程序编程接口）是一些预先定义的函数，目的是提供应用程序与开发人员基于某软件或硬件得以访问一组例程的能力，而又无需访问源码，或理解内部工作机制的细节。
* 可以是：网页，DLL，模块，文件包，exe等形式

### RESTful API
* [Origin(REST-WikiPedia)](https://zh.wikipedia.org/wiki/%E8%A1%A8%E7%8E%B0%E5%B1%82%E7%8A%B6%E6%80%81%E8%BD%AC%E6%8D%A2)

!!!quote "REST"
	* 表现层状态转换（英语：Representational State Transfer，缩写：REST）
        1. 以资源为基础
            * 每个资源都可以通过URI访问到。
            * 也就是一个个可以认知的资源，比如文档，音乐，视频等信息，都可以通过唯一的URI确定
        2. 通过重表达的客户端可以管理原资源
            * 就是我们通过客户端可以修改原资源的状态
        3. 返回信息足够描述自己
            * 这样重表达的客户端可以知道如何处理

!!!quote "RESTful API"
    * 匹配REST设计风格的Web API称为RESTful API。
    * 它从以下三个方面资源进行定义：
      	* 直观简短的资源地址：URI，比如：`#!js https://example.com/resources/`
        * 传输的资源：Web服务接受与返回的互联网媒体类型，比如：JSON，XML，YAML等。
        * 对资源的操作：Web服务在该资源上所支持的一系列请求方法（比如：POST，GET，PUT或DELETE）。
    * 下表列出了在实现RESTful API时HTTP请求方法的典型用途。
    
        | 资源 | GET | PUT | POST | DELETE |
        | ---- | --- | --- | ---- | ------ |
        | 一组资源的URI，比如`#!js https://example.com/resources/`    | **列出**URI，以及该资源组中每个资源的详细信息（后者可选）。  | 使用给定的一组资源**替换**当前整组资源。              | 在本组资源中**创建/追加**一个新的资源。该操作往往返回新资源的URL。 | **删除**整组资源。   |
        | 单个资源的URI，比如`#!js https://example.com/resources/142` | **获取**指定的资源的详细信息，格式可以自选一个合适的网络媒体类型（比如：XML、JSON等） | **替换/创建**指定的资源。并将其追加到相应的资源组中。 | 把指定的资源当做一个资源组，并在其下**创建/追加**一个新的元素，使其隶属于当前资源。 | **删除**指定的元素。 |

!!!example "示例"
    * 例如，一个简单的网络商店应用，列举所有商品
    
        `#!http GET http://www.store.com/products`
        
    * 呈现某一件商品
    
        `#!http GET http://www.store.com/products/12345`
        
    * 下单购买
    
         `#!http POST http://www.store.com/orders`
         
         `#!html <order>...</order>`

## DLL
* DLL(Dynamic Link Library)文件为动态链接库文件，又称“应用程序拓展”
* Windows系统中就有很多DLL文件，位于：C:\Windows\System32  和  C:\Windows\SysWOW64（64位限定）
* 在应用程序当前目录下也可以放所需的dll文件，系统会自动进行调用（放到system也可以调用）
* 在使用应用程序的时候，如果提示缺少DLL，可以获取放入系统中或是软件运行目录下

## 图片处理相关
### 抗锯齿(伪高清)
* 使用软件 PhotoZoom ，详见 PhotoZoom 篇
!!!warning "提示"
    * 本方法无法将图片清晰度调高，只是去除颗粒，所以最好还是拍摄时候取出高清图片

### 细节化处理
* 使用Waifu2X







