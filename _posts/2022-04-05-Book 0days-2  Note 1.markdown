---
layout:     post
title:      "Book 0days-2  Note 1"
subtitle:   " \"Information Security\""
date:       2020-09-20 14:47:00
author:     "Nastul"
header-img: "img/data-featured-image-1.jpg"
tags:
    - InformationSecurity  
---

### **Basic knowledge**

由于最近研究方向需要，找了些安全相关的书看，网上好像推荐0day这本书比较多，就写个笔记记录下。

ollydbg et al. 动态调试工具， IDA 静态反汇编工具



bug：功能性逻辑缺陷

漏洞：安全性逻辑权限

对于非可执行文件， 如果文件在解析时存在某些漏洞，比如说缓冲区溢出，就有可能导致该文件的恶意代码被执行。

- 漏洞挖掘- 安全性漏洞通常不会对软件功能本身造成很大影响，所以很难被QA工程师的功能性测试发现。需要进行Penetration test（攻击测试）， by Tiger team 或者 Ethic hacker。学术界主要是静态分析寻找源代码中的漏洞， 工业界普遍的采用Fuzzing。 灰盒测试

- 分析漏洞 搜索到 POC（proof of concept）重现漏洞被触发的场景。使用调试器观察漏洞细节，或者利用工具 Paimei 等。如果没有POC 通用的方法是使用补丁比较器，  然后利用反汇编工具IDA Pro 重点逆向分析该位置。

- 漏洞利用

未被修复未被公布的常常叫做 0day 漏洞。



### 二进制文件

PE（Portable Exec utable）是 Win32 平台下可执行文件. （如“*.exe”文件和“*.dll”文件）都是典型的 PE 文件。

.text 由编译器产生，存放着二进制的机器代码，也是我们反汇编和调试的对象。 

.data 初始化的数据块，如宏定义、全局变量、静态变量等。

.idata 可执行文件所使用的动态链接库等外来函数与文件的信息。

.rsrc 存放程序的资源，如图标、菜单等。 

除此以外，还可能出现的节包括“.reloc”、“.edata”、“.tls”、“.rdata”等。

但是这知识为了方便记忆的名字，实际上可以任意定义， 加壳后的信息也会不同。



虚拟内存的映射





静态反汇编工具看到的PE文件中某条指令的位置是相对于磁盘文件而言的，即所谓的文件偏移，我们还需要知道这条指令在内存中的位置， 虚拟内存地址 VA

在调试时看到指令的VA，需要回到PE中找到指令对应的机器码



#### PE 文件地址和虚拟内存地址之间的映射关系

（1）文件偏移地址（File Offset）：文件在 磁盘上存放时相对于文件开头的偏移

（2）装载基址（Image Base）：PE 装入内存时的基地址。默认情况下，EXE 文件在内存中的基地址是 0x00400000，DLL 文件是 0x10000000。这些位置可以通过修改编译选项更改。

（3）虚拟内存地址（Virtual Address，VA）： PE 文件中的指令被装入内存后的地址。

（4）相对虚拟地址（Relative Virtual Address，RVA） 相对虚拟地址是内存地址相对于映射基址的偏移量。

VA= Image Base+ RVA

文件偏移地址 = 虚拟内存地址（VA）−装载基址（Image Base）−节偏移 = RVA -节偏移





Ollydbg 无法调试内核。

SoftICE 工作在 ring0 级   In Circuit Emulator  （SoftICE 被呼出时会独占 CPU，中断一切进程和消息）

WinDbg

IDA Pro



74/75  JE    JNE 