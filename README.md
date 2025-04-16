# DD安全助手 V1.3

    欢迎各位大佬们使用，请点个⭐⭐支持下DD~  蟹蟹~~


**使用提醒：**
```使用前，请仔细查看第四章节-功能详情！```


# 1. ✨简介
    DD安全助手是一款集成多种安全功能的工具箱，旨在帮助用户快速进行威胁情报查询、网络排查、主机信息收集、主机日志分析、IP类处理等安全相关操作


# 2. 💡功能说明

![](_v_images/1744516843_15149.png)


1.情报查询模块：
* API配置管理：支持配置和管理每种服务的5个API密钥（微步、VirusTotal、鹰图），确保在API密钥失效或配额不足时能够自动切换到其他可用密钥。
* 单条查询：输入单个IP或域名，查询其威胁情报信息，包括是否恶意、威胁等级、可信度、标签、地理位置、whois等。
* 批量查询：支持从文件中批量读取IP或域名列表，进行威胁情报查询，并将结果保存到文本文件中。
* 高亮显示：针对不同程度的威胁，展示不同颜色的字体
* 结果复制：支持复制结果到剪贴板，方便进一步分析。

2.网络排查模块:
* 提取信息：从一键提取或主动输入的netstat -ano中提取网络连接信息。
* 提取所有IP地址：提取所有 IP 地址。
* 提取IP物理位置：查询IP地址的物理位置信息。
* 内容搜索：查询指定的IP/PID/Port等信息。

3.主机监控模块:【非管理员权限只可读取部分信息】
* 用户信息：查看系统用户列表，识别常见的异常用户。
* 计划任务：检索系统计划任务，检测其中应用程序的数字签名状态。
* 服务信息：查看系统服务详情，检测其中应用程序的数字签名状态。
* 启动项：查看启动项，检测其中应用程序的数字签名状态。
* 进程信息：查看当前进程列表，检测其中应用程序的数字签名状态。
* 重复进程检测：查看上述中重复存在的应用程序。
* 内容搜索：上述5个模块数据收集完成后，可以查询指定内容。

4.主机日志分析模块:【需要管理员权限】
* 安全日志：分析登录成功/失败以及其他登录事件。
* Windows PowerShell 日志：检测异常 PowerShell 命令。
* 自定义文件：加载第三方自定义日志文件(安全日志、PS日志)。
* RDP登录分析：列出多次尝试RDP登录的IP信息。
* SMB登录分析：列出多次尝试SMB登录的IP信息。
* SSH登录分析：列出多次尝试SSH登录的IP信息。
* 内容搜索：日志加载完成后，可以查询指定内容。

5.IP类处理模块:
* IP过滤：根据白名单过滤 IP 地址。(HW和日常研判必备，优先过滤公司IP/内网IP/公共DNS等，避免误封！)
* IP定位：查询 IP 地址的地理位置。
* IP段解析：解析 IP 段范围。
* IP提取并排序：从文本中提取并排序 IP 地址。

6.文件内容搜索模块:
* 在指定路径下搜索包含特定内容的文件，并进行时间排序 (忘了文件所在路径没关系，可以用它直接搜索)

7.免杀辅助模块:
* 哈希修改：修改文件哈希，绕过简单检测。
* 签名复制：复制文件签名，提升可信度。
* 图标提取：提取文件图标，绕过简单识别。
* 图片转 ICO：将图片转换为 ICO格式。

8.流量捕获模块: 【尝试模块待优化，可不用】
* 网络流量抓取：捕获网络流量，支持多协议过滤与实时分析
* 导出和读取：支持将捕获的数据包保存为PCAP文件，支持读取pcap包。


# 3. ✅WB云沙箱检测截图

```MD5：e5a9f6671bcd69f3669a26c168078ac1```

![](_v_images/1743322455_28310.png)




# 4. 📌功能详情


## ⌨情报查询

![](_v_images/1744553797_15139.png)


配置好对应的API key后才可使用该模块的功能！！填入key后进行保存！

![](_v_images/1744553820_27172.png)

**说明：**
```
(1).鹰图会显示剩余积分，且设置了只查询最近1个月的前3页的存活端口
(2).未显示微步数据说明API没有余额了
(3).微步API只能查询IP（这里是用的普通用户的API，每日只能查询20个IP），可以尝试多注册几个账号，使用里面的API（这里注册了6个，每日可以查询120个）
(4).API配置里，每个服务只能写5个key，但是可以在API配置里替换无额度的key，或者在api_config.json里替换
```

默认查询所有服务，也可以手动点击关闭服务只查询指定的服务

![](_v_images/1744554021_1062.png)


**单条查询：** 选择好查询源，输入IP/域名，点击单条查询，就可以看到对应的查找情报

![](_v_images/1744556727_4737.png)



![](_v_images/1744556852_7682.png)

**批量查询：** 点击"浏览"，选择对应文档(一行一个IP/域名)，点击"批量查询"等待几分钟就可以看到生成的结果文档了（API调用增加了耗时限制，批量查询的时候需要稍等一会~）

![](_v_images/1744556977_13495.png)


![](_v_images/1744557168_3529.png)

![](_v_images/1744557362_15838.png)




## ⌨网络排查:
通过点击**提取信息**或主动输入netstat -ano中提取的网络连接信息，可以从中筛选出外连IP，并针对外连IP可以定位物理地址并进行**境内/境外**的区分，并标记**境外**IP。

![](_v_images/1743085801_11573.png)

![](_v_images/1743085691_7260.png)

通过**内容搜索**可以查询指定的内容，如外连IP的PID，或PID对应的外连IP等。点击**下一个**可以查看多项匹配内容，并进行标记。

![](_v_images/1743085755_28307.png)



## 🖥主机信息收集:

**`现在正在加载中~`就不要点击工具的界面了，等待加载完成后会显示`已加载XXX`这时候可以查看收集的数据，也可以搜索指定的内容了**
* **用户信息查看:** 可以查看系统中的用户、隐藏用户、异常用户等

![](_v_images/1743085213_27803.png)

* **计划任务查看:**

![](_v_images/1743085183_11391.png)

* **启动项信息查看:**

![](_v_images/1743085254_7196.png)


* **服务信息查看:**

![](_v_images/1743084502_7470.png)

* **进程信息查看:**

![](_v_images/1743084441_2308.png)

* **重复程序查看:**

![](_v_images/1743091143_16626.png)



## 📋主机日志分析:

    日志类型里选择的安全日志与PowerShell日志是本机系统的，浏览里选择的安全日志和PowerShell日志是加载第三方的，如服务器的

**`点击加载日志后，请等待日志加载完成，加载过程中不要点击GUI界面！！`**

* **加载安全日志:** 这里日志类型里的是本地系统的安全日志，选择加载日志后可以在常用事件里选择对应的安全事件，这里主推登录成功/登录失败，其他安全事件里的内容可能解析不全

![](_v_images/1743085924_8595.png)


![](_v_images/1743086049_29050.png)


* **SSH登录分析结果:**
加载Linux主机上的secure文件，可以点击"SSH登录分析"会提醒到对应目录提取日志文件，点击确定后，会弹出选择目录，找到对应文件，点击选择后，再点击确定，就可以看到结果了：

![](_v_images/1744557514_26691.png)

![](_v_images/1744557603_16726.png)

这里以Linux主机被弱口令暴破成功感染挖矿病毒的日志为例，标黄的说明是可疑IP，尝试多次登录后才登录成功的，关注对应时间和登录总次数

![](_v_images/1744557703_21702.png)


* **RDP登录分析结果:**
加载本地和第三方安全日志后，可以点击"RDP登录分析"来查看有哪些IP进行了rdp的登录尝试和爆破，以及登录成功

![](_v_images/20250407102525.png)


* **SMB登录分析结果:**
加载本地和第三方安全日志后，可以点击"SMB登录分析"来查看有哪些IP进行了smb的登录尝试和爆破，以及登录

![](_v_images/20250407102413.png)

* **加载PowerShell日志:**
**`点击加载日志后，请等待日志加载完成，加载过程中不要点击GUI界面！！
`**
PS日志加载完成后，可以右键选择复制指定内容：

这里参考驱动人生病毒的计划任务，产生的PS日志内容：

![](_v_images/1744711453_17019.png)


* **指定内容搜索:**

![](_v_images/1743087746_3960.png)


* **加载第三方日志:**
点击"浏览"，选择其他路径下的日志内容，通常是从其他终端/服务器中复制过来的安全日志或PowerShell日志，选择日志后，点击"加载日志"，操作同上：

![](_v_images/1743088040_25366.png)


## ⚙IP类处理
* **IP过滤:** 首先在'白名单IP列表'里填入我们的白名单，比如公司IP/公共DNS/内网IP等，点击'白名单读取'，就会在本地会生成白名单文件 `whitelist.txt`；白名单读取成功后就可以在'待筛选IP列表'里输入我们的IP，比如攻击IP，点击'开始处理'后，就可以在'筛选后的IP列表'中看到过滤后的IP地址了。这时候可以查询IP的威胁情报下一步进行上报或者封禁。

![](_v_images/1743089569_17243.png)

![](_v_images/1743090301_3154.png)


* **IP定位**：查询 IP 地址的地理位置。

![](_v_images/1743090415_14511.png)


* **IP段解析**：解析 IP 段范围。

![](_v_images/1743090739_14178.png)


* **IP提取并排序**：从文本中提取IP地址并进行排序。

![](_v_images/1743090832_27865.png)




## 🧲文件内容搜索:
    在指定路径下搜索包含特定内容的文件，并进行时间排序，在文件路径下选择一条路径右键可以选择`打开所在目录`

![](_v_images/1743065496_4473.png)


## 🎯免杀辅助:
* **哈希修改：** 修改文件哈希，绕过简单检测。

![](_v_images/1743091728_15429.png)

* **签名复制：** 复制文件签名，提升可信度。

![](_v_images/1743091832_29674.png)

* **杀软识别：**

![](_v_images/1743091234_2971.png)

* **图标提取：** 提取exe文件图标，绕过简单识别。

![](_v_images/1743091296_10611.png)

* **图片转ICO：** 将图片转换为 ICO格式。

![](_v_images/1743091362_7783.png)



## 🎯流量捕获: （测试阶段）

选择好网络接口、协议等条件后，点击"开始捕获"就可以看到数据包了，点击"停止捕获"后可以导出，而且可以加载其他pcap

![](_v_images/1744558034_2098.png)



# 5. 免责声明

`该工具仅供安全研究与学习之用，如用于其他用途，由使用者承担全部法律及连带责任，作者不承担任何法律责任。`

# 👍大佬项目 
* https://github.com/secretsquirrel/SigThief
