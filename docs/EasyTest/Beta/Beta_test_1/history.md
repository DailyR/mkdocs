
--------------------------
版本修改
--------------------------



 - 0.5.4 Beta_2版本 (2022.05.16)
    - 当前状态：
        - 分清轻重缓急，制定优先级进行开发
        - EasyTest美化
        - 在团队中的放大化



 - 0.5.4 Beta_2版本 (2022.05.11)
    - 当前状态：
        - 推广和进一步推广，反思总结思考，李勇，汪昊推广交流使用



 - 0.5.4 Beta_2版本 (2022.05.06)
    - 当前状态：
        - 度过艰辛的半个月项目测试节点阶段，接下来重点以EasyTest的使用为推广契机
        - 信息流通知，webhook，完成文件夹监听，打包系统的通知


 - 0.5.4 Beta_2版本 (2022.04.14)
    - 当前状态：
        - EasyTest没在codeing主要是在跟进项目测试进度了，希望下个月有时间弄下，重新思考，重新清零，进行重构
        - 现在还存在使用的人不多的问题，可能没有触及到人的核心诉求，那就先不断积累自动化测试用例？


 - 0.5.4 Beta_2版本 (2022.04.08)
    - 当前版本状态：
        - 当前版本主要功能都已经实现，后续的实现需要提新的需求或者修改bug了
        - EasyTest_IDE 重新思考，重新清零，进行重构
        - 过程思路的重构也很重要
        - 使用优化，history这种
        - 已有的知识点的回顾，base，advanced_code的一些总结


 - 0.5.3 Beta_2版本 (2022.04.06)
    - 新功能：
        - try..except.. 封装web通信模块，使其不影响主流程
        - 内传外已完成


 - 0.5.2 Beta_2版本 (2022.04.03)
    - 阶段性里程碑：
        - 完成了websocket的例子和试用，主要是对websockets库的学习
        - 现有django的websocket的原生支持和websockets试验



 - 0.5.1 Beta_1版本 (2022.03.31)
    - 阶段性里程碑：
        - 完成 Beta_1 版本的内传外
        - 项目启用Beta_2 版本标识   
    - Beta_2版本：
        - sed.exe放入tools目录，直接不用改环境变量了    


 - 0.5.0 Beta_1版本 (2022.03.26)
    - 新功能：
        - 开始启用Beta_1版本
        - 开始阶段性内外同步


 - 0.4.12 Alpha_8版本 (2022.03.24)
    - 新功能：
        - 深化pytest命令行传参的example理解
        - exsample同步pytest_Allure路径
    - TODO:
        - 整理文件目录，工作目录和上传目录
        - 项目启用Beta_1 版本


 - 0.4.11 Alpha_8版本 (2022.03.23)
    - 新功能：
        - 上个版本想了几个方法，后来晚上回家的时候突然想通，这几个方法都有一定的复杂和中途易被打断的问题，而且传参可能存在困难，最后想通了一个非常巧妙的办法，在执行lua文件的是时候，return一个json的测试结果，当符合这个json测试结果的字符串出现，比如stdout里面result_str.find("EasyTest_Result")>0. 即可捕获到该段json输出

        - stdout 监听一个json格式的返回结果，然后调用jsondump，pytest去处理和生成测试报告，asset，最后用allure渲染，其中在修改插入位置的选择时候，又有了新的理解

        - 实现了pytest的传参和结果理解，详见内网的sample里的里程碑截图
    - TODO:
        - 找时间整理pytest的笔记，allure的，特别是pytest的，实在是非常好的用例组织方式


 - 0.4.10 Alpha_8版本 (2022.03.22)
    - 新功能：
        - pytest-allure的example例子结合游戏exe的实际情况运行EasyTest自动化测试例子，获取luamonCLI端的自动化验证result，将验证result, 直接luamonCLI未支持
        - luamonCLI-result方案设计
            - 1.selenium捕获结果进行判断
            - 2.服务端的数据，直接查对应的db协议数据
            - 3.用websocket和luamon的端口进行交互，执行内容获取结果
    - tips：
        - 当出现python的空格和tab混用报错，怎么改都报错时，可以用PyCharm--> Code -->Reformat Code 格式化代码，实测有效


 - 0.4.9 Alpha_8版本 (2022.03.21)
    - 新功能：
        - 独立模块文件Auto_Test.py, LuaMonCli_Thread.py,LogViewer_Control.py,Svn_Handle_Thread.py 独立文件使得目录结构更合理，单功能的文件不至于代码行数过长
        - 现在临时采取的是暴力删除exe，taskkill的方式，虽然这种方式解决了bug，但是不够优美，还是需要进行进程管理的方式来修复
        - 最后发现是 run_exe 没加self， 已修复这个bug




 - 0.4.8 Alpha_7版本 (2022.03.19)
    - 新功能：
        - 完成了增加夸夸机器人的功能
        - 试用人员：徐瑞霞，麦英杰，吴昊天，方瑞，王俊已升级继续试用
        - 试用人员达到5人
        - 增加了打包的icon，exe使用了icon，icon需要特定的软件转换png，直接改后缀名不行
        - 夸夸机器人也增加了icon
    - TODO：
        - 修复bug，进程管理，子线程的完全关闭，[] global list 记录所有的子进程id， 主要是启动游戏exe那里
        - 启用Alpha_8版本


 - 0.4.7 Alpha_7版本 (2022.03.18)
    - 新功能：
        - 完成pytest-allure的example例子
        - 增加了svn外链到ExcelTool.exe做tools里面的外部策划导表工具（需要适配相对路径和绝对路径的选择）
    - TODO:
        - 需要个夸夸机器人


 - 0.4.6 Alpha_7版本 (2022.03.17)
    - 新功能：
        - 自动化测试功能改成luamonCLI，放到独立线程去执行，信号与主线程交互
        - 解决部分试用同学遇到的兼容性问题
        - EasyTest自动化开始启用
        - 多线程执行增加线程分配
        - 增加一些tips方便使用和理解


 - 0.4.5 Alpha_7版本 (2022.03.14)
    - 功能：
        - ftp上传文件例子的写法
    - 开始内测试用：
        - 徐瑞霞，麦英杰试用，开始用户测试
        - 解决兼容性问题，国际标码gbk和utf-8的兼容问题（英杰处）try-catch
        - 解决安装问题cygwin-加路径，使用cygwin\bin加入环境变量


 - 0.4.4 Alpha_7版本 (2022.03.14)
    - 功能：
        - ftp上传文件例子的写法（内网已完成，详见sample）



 - 0.4.3 Alpha_7版本 (2022.03.11)
    - 功能：
        - 自动化测试关联EasyTest例子和规划.兼容QThread的写法
        - 基础规划完成



 - 0.4.2 Alpha_6接入LuamonCLI版本 (2022.03.09)
    - 功能：
        - 试用django websocket
        - 制定websocket 方案
        - websocket传外网
        - django websocket服务器笔记和example
    - TODO:
        - 测试例子同步sample，然后做好分类，准备新的大版本
        - PyQT_Test(Pre)、Alpha、 Beta、Gamma、 Omega、build、release可以用来命名版本
        - 启用Alpha_7版本


 - 0.4.1 Alpha_6接入LuamonCLI版本 (2022.03.08)
    - 突破性新功能：
        - 实时执行gm指令和捕获游戏客户端log —— hookLog彻底解决
        - 实现了myThread的封装了subprocess的stdout,stderr，实时捕获了输出


 - 阶段版本汇总

    - 之前版本到目前为止的TODO汇总及去重:
        - 每一个线程类，都可以抽象出一个单独的py文本模块文件（还未尝试）
        - 命名规则重新规范（还未尝试）

        - websocket连接slg服务器或者域名（连接中心服务器 11.141）（还未尝试）
        - 后台管理和上传配置同步，GM文件上传同步（还未尝试）

        - 自动化测试报告 （还未尝试）


        - 将Luamon完成掌握，包括迁移到外网（还未尝试）

        - Logging打必要的log，数据埋点，运行时间戳增加 Logging （还未尝试）
        - 加判断和各种process ID获取及win32，log获取 （还未尝试）
        - 集成自动化测试报告Allure （还未尝试）
        - 按键精灵类似的自动化回归   （还未尝试）
        - Lua Perfect debug研究，RPC方式获取数据和执行命令 （还未尝试）
        - 系统传参构建，sysArg （还未尝试）
        - 预装Luamon和客户端exe路径配置的简单化（还未尝试）
        - 研发知识点罗列，例如终端变色转义符等（还未尝试）
        - hook键盘鼠标的点击（还未尝试）
        - remind单子关联（还未尝试）
        - 账号登录（还未尝试）

        - .setToolTip() 增加悬浮使用提示 （已完成部分）
        - 考虑性能优化方案（已完成）
            - 1.初始化loading进内存，特别是读写文件的load
            - 2.减少print
            - 3.持久化对象尝试 （还未尝试）
            - 4.使用子线程
        - GM命令封装（已完成）
        - Output hook ，实时显示log（已完成）
        - 配置config.ini化（已完成）
        - 快捷键添加  （已完成部分）
        - 使用说明，buttonTips添加 （已完成部分）
        - 美观美化，添加图标  （已完成）
        - 打包exe问题解决 （已完成）
        - 启用Alpha_3版本，性能优化 （已完成）
        - 切换本地配置（ComboBox） （已完成）
        - Output（标准输入输出）进行hook，打印日志 （已完成）
        - 完成必要的模块抽象框架设计（ui与功能分离之类的）这块要新建项目，目前用的是Alpha版本 （已完成）
        - 关于进程的彻底关闭和进程pid之类的也得排期，然后自动化测试threading就放到子线程处理，防止进行自动化测试的时候出现主进程被卡住的情况。 （已完成部分）
        - 进入个人使用阶段，结合游戏的实际exe，替换成日常使用（已完成）
        - 完成必要的抽象框架设计 （已完成部分）
        - 按钮新增游戏窗口(用于tab全部关闭后，没地方可选的新增tab窗口) （已完成）  
        - AutoTest_打包luamon集成进来（已完成）
        - Output 将标准输入输出hook （已完成）



 - 0.4.0 Alpha_6接入LuamonCLI版本 (2022.03.07)
    - 突破性新功能：
        - Alpha_6接入LuamonCLI实时执行gm指令和捕获游戏客户端log
        - 改装gm命令实现方式，完成luamon的集成嵌入
        - luamon的嵌入执行完成，将threading_Luamon的启动放进初始化里
        - 实现了closeEvent的重写，退出时先强制删除node.exe
        - 后面再优化实现方式
    - 性能对比：
        - 之前用luamon-selenium的实现方式，阻塞情况下的执行是20秒左右
        - 现在优化到了Luamon-CLI 1秒之内，提升了20倍效率，已经达到可以接受的使用性能（符合2-5-8原则）
        - subprocess- stdout- stderr捕获子进程标准输出，打印到控件中
        - 实时打印，非常不易


 - 0.3.3 Alpha_5性能优化版本 (2022.03.05)
    - 研发里程碑：
        - 开始websockts例子测试
        - 开始luamon CLI 例子测试
        - websocket例子测试通过
        - websocket和http和socket的区别和联系
        - subprocess.call luamonCLI相关，指令执行与log捕获
    - 自我鼓励：
        - 吾等采石之人，当心怀大教堂之愿景
    - 版本变化：
        - 启用Alpha_6接入LuamonCLI实时执行gm指令和捕获游戏客户端log



 - 0.3.2 Alpha_5性能优化版本 (2022.03.04)
    - TODO：
        - 搞清楚HOOK Log
        - 搞清楚了，不是标准输入输出的hook error， 是打文件的log里面而实现的方法是在游戏客户端本地启动一个websocket的链接，当发生Log捕获的时候发向gamemirror
        - 一开始想的直接hook输出流是南辕北辙了，好在经过今天一天的研究，发现了正确的方向
        - 所以其实log获取和websoket链接，两个是一回事，不用分开写了
        - 研究game-mirror和luamon的CLI ，起websocket端口


 - 0.3.1 Alpha_5性能优化版本 (2022.03.02)
    - 突破性新功能：
        - 启用了Qthread线程，将svn更新等耗时工作迁移到了线程执行，完成后通过线程信号进行通知
    - 阶段性收获：
        - 1.PyQt中桌面应用的开发能力，各种控件的使用，如ComboBox这些，layout
        - 2.多线程的编程和理解能力， Qthread的实践，svn更新等耗时操作迁移线程上面执行，用信号进行通信，槽执行后续
        - 3.性能测试python产品的能力，使用cProfile和snakeviz可视化数据,对模块性能测试的数据变化非常直观
        - 4.自动化测试结合的能力，结合luamon和Selenium
        - 5.OS调用能力，web通知打开
        - 6.pyqt，pyuic5,py designer 快速设计界面的能力
        - 7.pyinstaller打包exe的能力
        - 8.Allure自动化测试报告的能力(TODO)
        - 9.日常自用和当做产品来使用很重要 *
        - 10.读取配置灵活使用的能力
        - 11.websocket获取服务端配置(TODO)
        - 12.使用history.md记录项目开发，使得开发过程更加清晰和方便回顾复盘反思
    - TODO：
        - .setToolTip() 增加悬浮使用提示


 - 0.3.0 Alpha_4性能优化版本 (2022.03.01)
    - 突破性新功能：
        - 重点优化game_start 和 run_exe 函数（game_start优化到了percall 在1秒以内，优化完成时间效率为原来的16%, 速度提升了6倍！）
        - sample测试
        - sample里增加了基础知识的温习和实践
        - 完成必要的线程分离
    - 基础知识温习：
        - 先独立线程，线程独立完成，完成备忘笔记
        - 知识储备-实践校验-形成案例-完成
        - 线程，调用，self.thread_3 = Thread_1(参数)， 在线程类的__init__里面定义，这就是带参数的线程调用
        - 带返回值的函数调用，详见 sampel里面的Qthread_test_1.py
        - python多继承，= A(B,C)  ,  A继承于B和C
        - 把读配置单独抽出来作为一个模块def get_config()
        - 基础知识continue和break
    - 版本变更：
        - 开始启动Alpha_5性能优化版本，删除冗余代码，使项目结构精简化
        - 使用cProfile和snakeviz可视化数据,对模块性能测试的数据变化非常直观


 - 0.2.2 Alpha_4性能优化版本 (2022.02.28)
    - 新功能：
        - 重点优化game_start 和 run_exe 函数
        - sample测试
        - 先独立线程


 - 0.2.1 Alpha_3性能优化版本 (2022.02.26)
    - 新功能：
        - 新增和切换项目后，自动切换到最近创建的tab页面， - tabWidget.setCurrentIndex(tabWidget.indexOf(tab))
        - 使用cProfile和snakeviz可视化数据对模块和函数性能进行测试，这样能有直观的感受
    - 项目相关：
        - 使用偶像的svn进行管理，方便查看前后prof_dump性能数据变化


 - 0.2.0 Alpha_3性能优化版本 (2022.02.25)
    - 版本TODO内容：
        - 考虑性能优化方案
        - 1.初始化loading进内存，特别是读写文件的load
        - 2.减少print
        - 3.持久化对象尝试
        - 4.使用子线程


 - 0.1.3 Alpha_2版本 (2022.02.24)
    - 新功能：
        - 增加快捷打开使用默认浏览器打开项目组工具主页，组内知乎(wecenter)
        - 增加tools工具，快速打开配置表搜素工具
        - 反馈\关于 描述的 优化
        - 控制面板 8个按钮功能开发完成
    - TODO:
        - GM命令封装
        - Output hook ，实时显示log
        - 数据埋点
        - websocket连接中心服务器 11.141
        - 后台管理和上传配置同步，GM文件上传同步，配置config.ini化
        - 集成自动化测试报告Allure
        - 按键精灵类似的自动化回归  
        - Lua Perfect debug研究，RPC方式获取数据和执行命令
        - 快捷键添加
        - 使用说明，buttonTips添加
        - 美观美化，添加图标
        - 运行时间戳增加 Logging 
        - 系统传参构建，sysArg
        - 打包exe问题解决
        - 加判断和各种process ID获取及win32，log获取
        - 启用Alpha_3版本，性能优化


 - 0.1.2 初步方案 (2022.02.23)
    - 新功能：
        - 将ui部分功能独立出一个单独模块，方便功能编写
        - 已完成部分ui及功能独立到Ui_Alpha_Test
        - 四大布局和画布交替使用完成右边控制窗口布局对齐问题（之前采用的方法总是差几个像素）
        - 控制窗口加入QToolBox实现抽屉盒工具栏效果
        - 切换本地配置（ComboBox）已完成
        - 选择一个项目后，点击切换，新开一个相关的游戏窗口表示切换成功
    - 版本变更：
        - 开始启动Alpha_2版本，删除冗余代码，使项目结构精简化



 - 0.1.1 初步方案 (2022.02.22 - 没错，同一天两个版本)
    - 新功能：
        - 项目主体完成：基础样式完成
        - 按钮新增游戏窗口（用于tab全部关闭后，没地方可以选的洗澡能tab窗口）
        - Auto_Regress 把luamon自动化测试脚本执行包含进来（已完成，点击自动化测试按钮即可）
    - TODO:
        - 切换本地配置（ComboBox）
        - Output（标准输入输出）进行hook，打印日志
        - 完成必要的模块抽象框架设计（ui与功能分离之类的）这块要新建项目，目前用的是Alpha版本
        - 关于进程的彻底关闭和进程pid之类的也得排期，然后自动化测试threading就放到子线程处理，防止进行自动化测试的时候出现主进程被卡住的情况。


 - 0.1.0 初步方案 (2022.02.22)
    - 新功能：
        - 项目主体完成：基础样式完成
        - 将Win32窗体嵌入pyqt5中，各项基础例子详见(PyQt_Test)
        - 基础版本的demo已经完成，主要是双击tab，就可以切换到有游戏运行窗口的界面
        - 基础版本的双击打开新的游戏窗口已完成，后续丰富排版和功能
        - 尝试了初版的布局layout的对应与pyqt信号与slot槽
        - 独立成子线程处理游戏窗口启动
        - 增加config\config.ini来进行不同项目的本地路径配置(configparser)模块
    - TODO：
        - 进入0.1.0个人使用阶段，结合游戏的实际exe，替换成日常使用
        - 完成必要的抽象框架设计
        - 按钮新增游戏窗口(用于tab全部关闭后，没地方可选的新增tab窗口)
        - 切换本地配置（ComboBox)
        - AutoTest_ 打包luamon集成进来
        - Output 将标准输入输出hook


 - 0.0.2 想法与方案验证 (2022.01.12)
    - 新功能：
        - 新增想法：账号化管理 (web)(对应的Luamon解析数据)
        - 基础样式设定
        - 功能初步设想
        - 基础技术方案采样验证，pywin32可行性，pyhook，PyQT5 - 验证通过
        - allure自动化报告，降低自动化的使用难度
        - 初版的pyinstaller打包验证
        - rpyc和luamon的技术结构设计
        - 解决编辑器使用airtest的问题
        - selenium远程server化
        - pysvn  —— (直接用系统就好，pysvn库已经不能用了)-subprocess.popen
    - 修复问题：
        - 降低版本确认工具的优先度，需求不明确


 - 0.0.1 初版构想-新建文件夹 (2022.01.05)
    - 新功能：
        - 设定目标：能完成一个屏幕(包含其他程序的)，集成按钮面板，然后有输出面板
        - 基础样式设定
        - 功能初步设想
        - 基础技术方案采样验证，pywin32可行性，pyhook吗，PyQT5
        - 降低自动化的使用难度
        - 初版的pyinstaller打包验证
        - rpyc和luamon的技术结构设计
        - 43996,43997端口反向捕获进程id属性数据
        - selenium远程server化
        - jenkins串联
