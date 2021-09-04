VTube Studio的主要用途是使用你的手机进行面部追踪，在Mac/PC应用中渲染你的模型，然后使用OBS（或类似的录制软件）向YouTube或Twitch推流。任何Windows/Mac录制软件都应与VTube Studio兼容。 

如果你使用iPhone/iPad进行追踪，你可以使用WiFi或USB向电脑端传输面部追踪数据，Android端则仅能使用WiFi传输。

[[https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/hint_top.png]]
[[https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/bunny_point.png|alt="Important Point!!"|height=59px|width=189px]]<br/>
VTube Studio使用你的本地网络（TCP/UDP）从手机向PC或Mac发送面部追踪数据。取决于你的家庭网络设置，可能会出现连接问题，原因多为防火墙设置。更多信息参见以下章节： 

[连接问题 & 解决方案](https://github.com/Elegetic/VTubeStudio/wiki/%E8%BF%9E%E6%8E%A5%E9%97%AE%E9%A2%98&%E8%A7%A3%E5%86%B3%E6%96%B9%E6%A1%88)
[[https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/hint_bottom.png]]


## 通过WiFi推流 - PC/Mac上的准备

将面部追踪数据从手机向PC/Mac推流十分方便。首先，确认你的手机与PC/Mac都在同一个本地网络下，否则它们将无法识别对方。

然后，启动桌面应用。在设置中，你可以在选择端口后启动服务器（优先尝试默认端口，25565）。

[[https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/connection_server.png]]

这将在每个可用的网络设备上启动你电脑端的VTube Studio服务器。由于同一电脑可能有多个网络设备，你也许会在按下 **“显示IP列表”** 时看到多个IP。

[[https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/ip_vx.png]]

[[https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/hint_top.png]]
[[https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/bunny_point.png|alt="Important Point!!"|height=59px|width=189px]]<br/>
虽然此处显示的IPv4地址通常是无法在互联网上公开访问的本地、内部地址，但你的IPv6地址很有可能是公共地址！若想公开截图，别忘了挡住它们，注意安全！
[[https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/hint_bottom.png]]
<br/>

首次启动服务器时，你可能会看到Windows Defender防火墙的弹窗。请确保勾上“允许访问专用网络”。否则，你的手机将因被防火墙阻止而无法连接到电脑端应用。

服务器现在已被启动，并正在检测手机应用连接。让它保持该状态。

## 通过WiFi推流 - 连接手机应用

下一步，在手机上启动应用。在设置中，你可以手动输入桌面应用的IP与端口，也可以使用 **“查找服务器”** 按钮自动搜寻服务器并使用它的IP与端口。扫描过程应该不会超过五秒。

<p float="left">
  <img src="https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/server_scan.png" width="290" /> 
  <img src="https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/settings_main_2.jpg" width="290" /> 
  <img src="https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/smartphone_connected_real.png" width="290" /> 
</p>

现在，点击“连接到电脑”，应用现在会连接到服务器端。如果连接因某些原因丢失，应用会自动尝试重新建立连接。

**恭喜！** 你现在正在将你的面部追踪数据推流到电脑。你可以在桌面应用中打开一个VTS模型，它会使用手机上的面部追踪数据。只要你想，也可以同时在手机应用上打开任意一个模型。

[[https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/hint_top.png]]
[[https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/bunny_point.png|alt="Important Point!!"|height=59px|width=189px]]<br/>
向电脑推流时，你不必在手机上也打开模型。事实上，出于性能方面的考虑，更建议不启用模型。在使用“推流模式”时，连接电脑后，手机上加载的所有模型都会被自动移除。
[[https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/hint_bottom.png]]

## WiFi替代: 通过USB从iOS向PC/Mac推流

若您使用iPhone/iPad进行追踪，你也可以使用USB有线连接来实时传输面部追踪数据。这比WiFi传输更为稳定，但也是一个经过测试的新功能。目前，这是更为推荐的传输面部追踪数据的方式。

要开始连接，首先启用手机上“连接USB”选项。若电脑上WiFi连接面部追踪属于启用状态，因二者不兼容，该选项也会将它停用。随后，在PC/Mac端的应用上启用“连接USB”选项。

[[https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/usb_con_pc_1.png]]

如果设备没有显示或连接失败，请确保下述情况无误：
* iOS设备通过USB线与电脑连接。
* iOS设备已解锁并正在运行VTube Studio应用。
* iOS端应用显示“USB已启用。等待电脑应用连接。”
* iPhone已与电脑“配对”（手机必须“信任”该电脑）。可以通过检查iTunes上是否可以查看该iPhone文件目录来确认这点。
* **重要：请确保你安装了iTunes！！** iTunes在Windows/MacOS上会启动一些与iPhone通信所需的后台服务。iTunes本身无需启动，但请务必确认已安装并至少运行过一次。如果USB连接依旧失败，请尝试在打开VTube Studio前先启动iTunes。

## 使用OBS录制 （窗口透明）

在电脑端的VTube Studio中，选择 **取色背景**。在Windows版中，你可以使用“在捕捉时透明”选项，这将使窗口背景在OBS捕捉时保持透明， **这样就无需使用绿幕/色度键了**。

[[https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/obs_2.png|width=526px]]

**在macOS上，OBS不支持该功能**，所以请选择任意你想要的颜色，然后在OBS的视频捕捉中使用 **“色度键”**滤镜来进行颜色移除。需要记住的是，你不能在你的Live2D模型中使用该颜色，否则模型的某些部分也将会变得透明。

在OBS中添加一个背景，然后增加一个VTube Studio的画面捕获。要做到这一点，请选择 **“游戏源”**。该捕捉支持透明背景，但仅适用于Windows。
在macOS，该选项被称为 **“Syphon客户端”**，但在macOS 10.14 Mojave后就无法使用了（参见https://github.com/zakk4223/SyphonInject），所以你需要使用普通的窗口捕获与色度键滤镜。

<p float="left">
  <img src="https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/obs_4.png" width="394" /> 
  <img src="https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/obs_5.png" width="394" /> 
</p>

捕获现在已经启用。在macOS上，你需要 **右键选择你的来源 → 滤镜 → 添加滤镜 → 色度键** 来增加滤镜移除绿幕（或你选择的任何颜色）。

你现在可以通过直接在VTube Studio或OBS中移动/缩放/旋转你的角色，以将它放置在屏幕的任何地方。

或者，你可以使用VTube Studio中的 **虚拟摄像头功能** 或 **NDI** 来创建一个网络摄像头推流，然后将它直接用在Zoom，Discord等应用中（参见常见问题）。 

## 使用NDI向OBS推流且隐藏UI（窗口透明）

建议使用OBS的“游戏源”录制VTS窗口。或者，你可以使用虚拟摄像头或者NewTek NDI（网络设备接口） 来创建视频流，以作为OBS等软件的输入源。

NDI推流的质量与延迟都十分优秀，它同时也支持窗口透明（不需要色度键），并且完全不会录下VTube Studio的UI。使用NDI可能会使VTS的CPU占用增加。OBS插件可用于macOS与Windows。

**OBS 插件界面:** https://obsproject.com/forum/resources/obs-ndi-newtek-ndi%E2%84%A2-integration-into-obs-studio.528/

**OBS 插件下载（Win/Mac）:** https://github.com/Palakis/obs-ndi/releases/tag/4.9.1 

要使用NDI，请从上方的GitHub网页中下载该插件（Windows为.exe，macOS为.pkg）并安装。在VTube Studio中，于 **“摄像机设置”** 栏内 **启用NDI选项**。NDI与虚拟摄像头可以同时开启，但不建议。

在OBS中，建议使用以下设置。有时NDI推流会在OBS界面中扭曲，若发生该情况，请调整（拖动）VTube Studio窗口的大小，直到推流“闪回(snaps back)”原样。

[[https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/obs_ndi.png]]

