# selenium  web自动化
## 

 

### 需要匹配对应chrome的 driver，去网上查对应版本的驱动

'''
- 内网运行过  但是直接手打copy的思路，pytho3.4云桌面环境不支持环境配置，思路是这个思路
- 但是由于比较简单，运行起来调错应该也很快，就直接传了，实际要用到的时候再调试
- web自动化 selenium 的运行成功实例
'''


- 可以作为一些工具的衔接和组件，比如luamon这种

- 办法都是靠人想出来的


- 这里的xpath获取是直接chrome打开对应网页，然后F12，选择左上角的鼠标，选中后copy的xpath，这个是比较快捷和简便的
'''


### 启动命令：

>> java -jar selenium-server-4.1.1.jar standalone --host 0.0.0.0 [--port 9999]    参数其实都可选

>> 然后用webdrive.Remote 模式的话，  driver.implicitly_wait()  这个写法就不能用了

>> server端的话，把驱动放到chrome.exe同路径下，然后把chrome路径加入环境变量

>> linux的话最好用docker来装
