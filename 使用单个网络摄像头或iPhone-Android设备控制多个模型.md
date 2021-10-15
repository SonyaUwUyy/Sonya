## 准备工作

你可以使用单个网络摄像头或iPhone/Android设备控制多个VTube Studio进程。

要达到该效果，首先你需要启动多个VTube Studio，可以用该按钮实现：
![](https://github.com/Elegetic/Photos/blob/main/VTS/start_new_vts_instance_button.png)
或者，你也可以使用与VTube Studio`.exe`同目录的`start_without_steam.bat`文件，参见[“不通过Steam启动应用”](https://github.com/Elegetic/VTubeStudio/wiki/%E4%B8%8D%E9%80%9A%E8%BF%87Steam%E5%90%AF%E5%8A%A8%E5%BA%94%E7%94%A8)。这样就有多个VTube Studio同时运行了。

## 使用单个网络摄像头控制多个VTube Studio进程

在VTube Studio中多次选择同一个网络摄像头即可。在这种情况下，摄像头只会执行一次面部追踪，所以不会有额外的CPU负荷。

## 使用单个iPhone或Android设别控制多个VTube Studio进程

### 使用iPhone/Android网络追踪

**注意**：若使用USB而不是网络追踪，请下拉至“**使用iPhone USB连接**”。
假设你启动了五个VTS进程。当在同一个端口上启动两次网络服务器时，VTube Studio会自动选择下一个可用端口启动连接，原端口号则会被划以删除线。
![](https://github.com/Elegetic/Photos/blob/main/VTS/network_server_auto_ip.png)
这五个进程分别在以下端口运行：

* (A) "VTube Studio" - 端口25565
* (B) "VTube Studio 窗口 2" - 端口25566
* (C) "VTube Studio 窗口 3" - 端口25567
* (D) "VTube Studio 窗口 4" - 端口25568
* (E) "VTube Studio 窗口 5" - 端口25569

需要注意的是，该功能只有在所有进程启动网络服务器时才会运行。现在你可以通过在iOS应用中输入**任意进程的端口号**来进行连接。假设你连接了端口25566的进程（**B**）。该进程会传输追踪数据到`<own_port> - 1`与`<own_port> + 1`的进程，即为向上方与下方传输。收到该数据的进程会继续进行传递，在双方向上建立链。若链因其中有端口没有运行VTube Studio进程而断裂，数据则不会进行进一步传递。

这也意味着如果你**在同一台电脑上**想要使用**两部手机**控制**两个不同的VTube Studio进程**，这两个进程必须相隔至少两个端口号，否则它们将会试图互相传递数据。
![](https://github.com/Elegetic/Photos/blob/main/VTS/vtube_studio_multi_instance_1_CHN.png)

### 使用iPhone USB连接

它的运作方式有些许不同。一个进程通过USB接收数据并将其传递给另一个进程。假设有以下五个进程在运行：

* (A) "VTube Studio" - USB服务器运行中，网络服务器关闭但选择了25565端口。
* (B) "VTube Studio 窗口 2" - 端口25565
* (C) "VTube Studio 窗口 3" - 端口25566
* (D) "VTube Studio 窗口 4" - 端口25567
* (E) "VTube Studio 窗口 5" - 端口25568

需要注意的是进程（**A**）与（**B**）都选择同一个网络服务器端口。它之所以可以正常运作，是因为进程（**A**）使用了USB连接，这意味着它不能同时使用网络服务器。进程（**A**）通过USB接收数据并将它传输给了（未运作的）网络服务器端口。在该端口运行的进程（**B**）会接收数据并再次将它向上方与下方传输，由此传输到端口25564（未运行任何进程）与端口25566（进程（C））。这样一来，该链就会正常运作了。
![](https://github.com/Elegetic/Photos/blob/main/VTS/vtube_studio_multi_instance_2_CHN.png)