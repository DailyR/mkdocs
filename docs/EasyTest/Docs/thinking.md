


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


