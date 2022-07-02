


## Easy_Test_IDE_Beta_Test_V1 lua&Luamon practices & study notes



- 用来记录一些想法和变化 -


	- 战斗测试用例
		- 1.出城战斗
		- 2.

	- 增加调试用的按钮
	- 战斗出城分解，先出城一只队伍



### [EasyTest 总纲ReadMe](../README.md)

### [LuaMon 总纲ReadMe](../../lua_luamon/README.md)

####  lua&Luamon practices & study notes

- 代码路径

	- 第一步：代码制作:所有界面代码文件放置于x\Assets\ulua\Lua\GameScript\Module按功能以文件夹划分，也有些原项目残留的界面代码存放于x\Assets\ulua\Lua\GameScript\View。确定需要完成的目标，比如完成跳过创建完新号后进入的视频跳过，那实例操作步骤如下:收集资料第一步:打开svn 客户端x目录下的log提交记录，找到大概的关键字， 剧情动画 plot cartoon， 看到svn 提交目录大概是这个样子，

		- 提交内容:【前端】剧情动画接入客径	操作 从路径复制版本	/trunk/dient/lowpoly-dev-2019/x/Assets/ulua/Lua/GameScrpt/Module/CgCartoon/CgCartoonController.lua已修改。获取关键字，plot ， cartoon.

	- 第二步:打开 perfect lua ide里对应的module，大概查看一下相关的代码接口找到对应路径下的有个Player  PlayerTalent Plot view GuideDialogView.lua PlotView.lua GuideDialogController.lua PlotDefine.lua PlotEvent.lua PlotModel.Jua ScenePlot文件夹，在五.Ul框架重构 里说了大概这些文件的作用，现在开始详细去看各自实现的功能和作用。一开始可能也有找错的，再细看其实应该是CgCartoon的相关文件夹，CampCgCartoon，CgCartoonController.lua CgTouchBlockView.lua CityBuild，好，定位到这个文件夹和里面的文件。

	- 第三步:打开exe和luamon，调用里面的参数进行调试， 从文件里获取的 CgCartoonController对象和播放模块控制器，很明显local	test = function	endIlocal main =function()CgCartoonController=CgCartoonController or Maker() Play_state =CgCartoonController.IsPlaying return "Hello",Play state endreturn main()然后再在luamon里面运行这个，和exe不同阶段对应，从中运行可知道[LuaRun] 成功 2022-01-1714:25:13

		- 运行有False有True，那就是开始是False就是一开始的视频不属于动画播放控制范畴，仔细一看，确实是一个mp4格式的cg文件，开场动画视频，地址是/trunk/client/lowpoly-dev-2019/x/Assets/Resources/FMOD/DemoMapOceanmp4是个mp4视频。找到之后全局搜索调用，发现是登录流程后自动UIMgr.OperView(“VideoPlayView”)来播放的，Mp4播放完才是 剧情 plot 相关的东西。

	- 第四步:UIMgr.ViewlsOpen(view_name)这个之前就知道了(不知道可以再看下UIMgr)从调试结果看，符合预期，开场视频动画和打开的view 视图的状态相一致，对应代码如上所述。

	- 第五步:上述的播放视频和开场cgCartoon的状态都已经获取成功，就剩下剧情的解析， BaseData Plot opera 从代码里，知道这个plot剧情的播放时机，(有spine的)
	```lua
	local main =function()
		-- log({1,2,3})
		GuideDialogController = GuideDialogController or Maker() 
		if UIMgr.ViewIsOpen("PlotView") then
			return "view is opend" 
		else
			return "view is not opened" 
		end
		return "Hello" 
	end
	return main()
	```

	经过多次摸索，其实最好用的判断是PlotView对话窗口是否打开，有的话就跳过

	- 第六步:上述的过程里还存在一个GameLoading界面的问题，这个是用C#写的 gameLoadingview(有些基础概念放在第七点[不是第七步])
	经过多次摸索，
	```lua
	local main =function()
		if	GameLoadingView.Instance.isActive==true	then	
			return "Game Loading " 
		else
			return "Game is not Loading " 
		end
		return "Hello" 
	end
	return main()
	```
	完成

	- 第七步:上述的经过多次摸索,Ps:一些有用的代码片段看到也可以截取，比如说下面这段，就可以用来判断是否在塔防中或者是否在剧情中
	```lua
	function ApiGuide.ShowGuideMask(show)
	show =show or false if show == false then
	UICameraMgr.guideMask:SetActive(false) else
	--判断是否在塔防中
	local flag=SLGMapMgrGetARPGMapFlag() if flag then
	return end
	--判断一下是否在剧情中
	if not UlMgr.ViewlsOpen("PlotView")then
	UICameraMgr.guideMaskSetActive(show) 
	end
	end
	```
	直接 copy 拿来用，真香!
	ss:如果凭借经验需要找到某个View，又不太确定这个View 的名字，那么打开unity，在 scene模式下面的，选中对应的资源，比如如下图所示的 view 对话框，右边的 Inspector 窗口就会显示出具体的 View 名字，这样就可以很方便地进行 viewname 相关的操作了， open,close，isOpened 这些函数.

	- Psss:
	D:\slg\client\lowpoly-online-2019\x\Assets\ulua\Lua\GameScript\Module\Player\View\PlayerSe ttingView.Lua调用的帐号切换 self:AddClick(selfbtnSwitchfunction()SDKEventHandle.Switch() end)

- 二.有些基本概念可以从客户端程序文档处获取
	- 如代码存放路径，UI架构重构的函数理解这些，还有活动框架的分解这些

- 三.有些基本的 unity概念
	- Assetsbundle可以包含prefab，详细的美术概念笔记可以看《UnitySLG一些疑问笔记》




- 四.测试环境的问题
	- 一般客户端的luamon调试需要打开5个东西:
		- 1个是unity，方便查找资源和预设，
		- 1个是exe(有时候可以直接用unity的客户端进行替代)，
		- 1个是开着浏览器的luamon进行调试和看效果，
		- 1个是开着perfectlua的环境去查看客户端代码，
		- 1个是开着sublimetext3进行lua代码的备份和output调试记录。

		- 有时候很unity运行慢就用exe，需要再打开就好
		- 然后svnlog是帮助理解代码的辅助工具，详见一、代码路径

- 五.UI框架重构里面说了对应代码模块分类
	- 新加卷(D:)>sig>lowpoly>x>Assets>ulua> Lua > GameScriptModule >ModuleName 
	- 共享·	新建文件夹 修改日期	类型	大小	
		- View-界面类集合	2021/3/16 17:23	文件夹	
		- TestContro-控制器Lua	2021/3/16 17:23	LUA文件	0 KB	
		- TestDefine-常量枚举.ua	2021/3/1617:23	LUA 文件	OKB	
		- TestEvent-事件类iua	2021/3/16 17:23	LUA文件	O KB	
		- TestModel-数据处理,lua	2021/3/16 17:23	LWA 文件	O KB	
	- 方便后期维护，提高可读性，规范目录结构，如图所示

	- 所有View对应的lua文件路径都需要手动添加到ModuleInclude.lua中，必须用ViewName作为key
	- 通过UIMgr创建的时候才会去require对应的lua文件


- 六.在unity里面找预设的方法
	- 在unity里面找预设的方法，如图所示，搜索预设名
	- 记得如果是找界面，view 的这种，就-要从 Game 模式切换到 Scene 模式

- 七. 有些基本的 unity 概念
	- 构建智能table，本身就做了单例化了，c#写的gameLoadingview
	- 有下面这种的基本都要这个构建这个的时候，把单例外露出来了而已 
	```lua
	function New()
		local obj = {}
		setmetatable(obj,{index=SceneObjMgr}) 
		obj:init() 
		return obj 
	end
	```


- 八.一些基本的 View 和代码所在的地方
	- (其实就是时隔一段时间后，对于一代码路径的再次实践与复习)
	- SlgLoginView界面-登录界面
	- self.GuideToggle.isOn=false--ApiGuideisGuideOpen() 
	- GuideModel.getInstance():set_guide_open(false)
	- 是否打开新手

	- 先确定这个东西它的类型，例如它是场景，那在 Project 里面就是这个样子，【记住这个图标】
	- ●Inspector	Project	Hierarchy
		- hierarchy里面查找对应的ABassetsbundle
		- 然后如果是一个MessageView就简单了
		- 去perfectlua 里面用ctrl+shift+f来寻找对应的文字，一般都是能直接找到的

		- 在1，2，3，4，5里面找到对应的UI然后选中后点击勾选，如果对应的UI对话框消失，表示选中了对应的对话框了【记得 Game 模式切换成 Scene模式，然后点击一下 2D模式这样更方便查找对应的组件】
	- BoxTips/Dialog/Content/Buttons/ensureBtn 通过这个找层级，就会有对应的Btn路径
		- 可以通过左边的hierarchy(层级，等级)
		- 可以获取到对应的资源路径。
		- 然后通过perefect lua可知，对应的这个是个MessageView，通过MessageViewlua和 SDKEventHandle.lua可以获取到对应的函数，
		- selfboxtips ensureBtn=self:FindChild("BoxTips/Dialog/Content/Buttons/ensureBtn","Button")获取到对应的控件之后，

		- 就变成了类似这种的普通界面，--UI层级的都可以用 onClick tile_info.onClick:Invoke(),用.onClick:Invoke()就可以了


- 九.已经进入到场景里的第一个画面
	- Twd_Main_condition_check.lua 一直执行的结果就是进到这个界面为止，接下来继续调试新起一个文件chapter__regress.lua

	关键接口备忘:

-队伍出城/移动到某个目标
BattleMgr.GetInstance():CityTeamOutOrMove(1,nil,nilVector2(1440,764)

--内城移动可以使用这个接口函数
具体在 BattleMgr.lua文件中，查看cityTeamOutOrMove函数

Editor里的表是直接引用的，跟Excel进行的导表不太一样，没有Excel 文件有些定义可以从注释中获取，然后用return来试验新手编辑器和对应表
指引指南说明http://sy4.4399svn.com/svn/slg/trunk/client/Doc/引导相关/lowpoly引导 Utilfunc:feiPrint 文件:函数名 调用的函数 -- 这个是飞云的打印函数， Twd feiPrint.lua实例里面可以查看问题:数据结构在哪里?
ProtoApi 里面有些字段的定义，拼凑一下
protocol.xml#p_concise_scene_object 里面的协议文件获取对应的 table 结构，
I
答案:
对应的客户端直接接收服务端发送回来的协议，装配工作是在服务端完成的，只是根据协议来进行显示。(当然之前是获得各种 obj)

D:\slg\server\game_twd\proto\protocol.xml

客户端战斗基础流程
1.选择行军部队
2.
3.播放移动动作，根据服务端给过来的位置列表和行军速度移动到指定点
4. 播击动作，被攻击对象接收到事件也播放攻击动作
5. 动作播放完，判断是否攻击时间是否结束，没结束继续播放攻击动作，否则播放待机动
作
发起攻击指令
请求寻路数据
接收广播开始移动
发送移动后位置给后端
判断部队点和攻击点距离
处于战斗状态且在范围内，播放战斗动作
接收战报广播，实时显示扣血和士兵元素数量减少

接收战报广播，实时显示扣血和士兵元素数量减少

判断如果位置已经到达攻击范围，动作状态改变，变成战斗状态

后端推送 on_synsc_report_s2c 协议，实时改变血条和士兵血量
战斗结束，判断是否待命，否则移动回城

虽然说明比较精简，但是已经把战斗流程都说清楚了，客户端承担的战斗相关的部分，然后on_synsc_report_s2c 处理后端推送的协议，dispatch分发一些动作给对应的队列进行处理。