


# EasyTest

# Easy_Test_IDE_Beta_Test_V1

## TODO



- 用来记录一些想法和变化 -


	- 战斗测试用例
		- 1.出城战斗
		- 2.

	- 增加调试用的按钮
	- 战斗出城分解，先出城一只队伍


- 使用问题随时联系 Daily李岱

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

