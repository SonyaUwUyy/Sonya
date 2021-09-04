## 设置文件

点击主菜单中的设置图标后，会显示设置界面。它有几个选项卡，一个帮助图标（链接到本文档）和语言选择按钮，可以通过它切换界面语言（需要重启应用）。

全局（与模型无关联）设置被保存在该文件内：<br/>

`<VTS-App-Path>/VTube Studio_Data/StreamingAssets/Config/vts_config.json`<br/>

## 基础设置（杂项）

<p float="left">
  <img src="https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/settings_main_1.jpg" width="290" /> 
  <img src="https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/settings_main_2.jpg" width="290" /> 
  <img src="https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/settings_mouse.jpg" width="290" /> 
</p>

在这里，你可以购买 **VTube Studio专业版（仅限iOS/Android）**。在iOS端，该界面上也有恢复已购项目的按钮。

此外，还有隐藏VTS标志、记住场景（重启时保存打开的背景和模型）等常规设置。

接下来是 “向电脑端推流”的设置。该设置将你的手机连接至电脑，以便将面部追踪数据推流至电脑应用。这将在 **“连接你的手机到PC/Mac”** 一章中讲述。在iOS设备上，你也可以在此处用启用USB连接来代替WiFi传输。因其似乎比WiFi更加稳定，所以更为推荐使用USB连接。在Android端，该选项暂时不适用。

最后，还有 "鼠标输入配置"。它允许你使用鼠标/触控位置作为输入参数，在面部追踪的基础上为模型增加动画。你可以以像素为单位选择 **X区间** 与 **Y区间** ，该区间将在X与Y上被映射为[-1, 1]。通过该设置，你可以让模型双眼随着手指或鼠标指针移动。这里也会显示鼠标点击（右键、左键、中键），可用以触发热键。在手机应用中，这些鼠标按键可以通过用一根手指（左键）、两根手指（右键）和三根手指（中键）触屏来触发。

## 基础设置 (基于音频的唇音同步) 

[[https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/voice_lipsync.jpg]]

基于音频的唇音同步仅支持Windows与MacOS系统（不包括基于M1/Silicon芯片的Mac），手机上无法使用该功能。

基于语音的唇音同步有以下两种功能：

* 基于当前麦克风音量 **张开/合上嘴部** （或其他任何Live2D参数）。
* 基于监测到的声音频率 **改变口型** （或其他任何Live2D参数）。

若麦克风音频与界面上显示数值有延迟，请使用“重新加载”按键重载指定麦克风。或者，你也可以使用热键来重载麦克风。

当启用时（开启“使用麦克风”开关），你可以在VTube Studio模型中使用三个额外参数： 

[[https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/new_params_voice.png]]

* **VoiceVolume:** 基于麦克风音量的、范围在0与1之间的参数。
  * **音量增益滑块** 控制音量对该参数的影响程度。
  * **音量削减滑块** 控制麦克风可收录的最小音量。你可以通过它来过滤背景噪音。
* **VoiceVolumePlusMouthOpen:** 将 **VoiceVolume** 参数与 **追踪所得参数值** 合并。举个例子，通过它，你可以在面部追踪到嘴部张开、且捕捉到声音时张开模型嘴部。该参数范围也介于0与1之间。
* **VoiceFrequency:** 该参数范围介于0与1之间，以0.5为基准。它会基于捕捉到的声音频率而上升/下降，你可以通过它控制口型。
  * **频率增益滑块** 控制频率对该参数的影响程度。

### VoiceFrequency参数的计算方式:

当你说话时，VTube Studio会分析你的语音并从中检索音素（**A, I, U, E, O, 其他**）。当特定音素被检索到时，你会看见底部对应方块（如上图）变暗。

你可以点击音素以让它变为 **红色 (-)**, **绿色 (+)** 或 **中性** 。根据这点，当检索到该特定音素时，它会向上/向下推动 **VoiceFrequency** 参数（若使用该参数，它也会改变你的口型。）

<br/>
<p align="center">
  <img src="https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/karaoke_saiten.png" width="412"/>
</p>
<br/>

[[https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/hint_top.png]]
[[https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/bunny_point.png|alt="Important Point!!"|height=59px|width=189px]]<br/>
关于音素设置，其实并没有特别的建议。你可以多多尝试，直到找到最适合自己的配置。这可能需要一些试错，但设置完成后的效果会很棒，尤其是在唱歌的时候。♪ ♫ ♬

[[https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/hint_bottom.png]]

## 摄像机设置(iPhone/Android)

<p float="left">
  <img src="https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/ar_cam_config.jpg" width="290" /> 
  <img src="https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/sensitivity_settings.jpg" width="290" /> 
  <img src="https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/blink_fix.jpg" width="290" /> 
</p>

该配置栏可以修改关于渲染和相机的设置：

* **AR相机设置**
  * 修改追踪摄像头每秒帧率。这不会改变应用帧率。
  * 切换摄像头预览显示。若你想确保自己的脸永远不会出现在手机屏幕上，你可以在这里设置（参见图三）。
  * 切换面部遮罩显示。 

* **追踪设置**
  * 选择面部追踪丢失时的模型行为。你可以让模型在原地固定不动，也可以让它恢复为默认姿势。
  * 改变眨眼关联行为
    * 若选择“总是”，则左眼与右眼的EyeOpen值将一直被设为二者的平均值。
    * 若选择“当面部旋转时”，双眼的EyeOpen值会在头部转动幅度较大时被关联。此时将使用头部转向一侧时可见侧的眼睛数值。
  * iOS/Android端面部追踪的各项灵敏度。举例而言，如果模型嘴部无法张开，可以通过在此处增加灵敏度来快速解决该问题。

* **iOS眨眼修复**
  * 由于近期iOS面部追踪出现的问题，HeadY参数会在眨眼时非常轻微地向上抽动。在苹果公司正式修复该问题前（希望尽快），可以使用此滑块来解决问题。建议将Y值设置在30-45间，但请选择最适合你的数值。X值通常可以保持在0。由于其影响十分微弱，你的模型可能根本无需对此进行设置。

* **质量与效果**
  * 开启抗锯齿（使模型边缘更平滑，但会消耗性能，不建议在手机上使用）。
  * 修改应用每秒帧率。VSync意味着每秒帧率将与你的显示器刷新率同步，推荐在电脑端使用以防止屏幕撕裂。
  * **追踪V2:** 增加了各种试验性的iOS追踪改进，请谨慎使用！
    * **更好的单眼眨动** 当一只眼睛完全闭上而另一只没有时，该功能会迫使眼睛的睁开幅度更大，这将使单眼眨动更容易/效果更好。
    * **更好的蹙额：** 在低眉时自动增加蹙额幅度。该功能通过在检测到眉毛下垂时减少MouthSmile的数值实现。

* **屏幕录制**
  * 仅限手机。可以直接录制屏幕与麦克风声音。在录制时，右下方会显示一个小红点。可以随时点击它以停止录制。

## 摄像机设置 (MacOS/Steam平台的网络摄像头)

先从VTube Studio的Steam版本讲起，你可以使用你的网络摄像头进行面部追踪。请注意，和iPhone/Android版类似，你的网络摄像头画面永远都不会在VTube Studio中显示。

**VTube Studio中无法显示网络摄像头视频，也没有任何代码可以实现该功能。**

[[https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/face_track_win.png]]

这里的大部分设置应该都不言自明。通常而言，为实现较好的追踪效果，推荐1280x720的分辨率，且每秒帧率应至少为10。这对眼部与眨眼追踪尤为重要。

当勾选“VTS自启摄像机”时，在启动VTube Studio后，摄像头将在场景加载完毕几秒钟后启动。

在第一次启动网络摄像头后，请在面无表情、平视相机时按下“校准”键。你的校准数据会被保存，所以即使重启VTube Studio，你也无需再次进行校准。不过，如果觉得模型的角度与面部有所差距，你可以随时重新校准。网络摄像头的校准数据会被保存在以下文件中：

`<VTS-App-Path>/VTube Studio_Data/StreamingAssets/Config/webcam_calibration.json`

关于不同追踪质量水平的细节，请参考VTube Studio中选择它们时所显示的信息。**注意：只有五级支持单眼眨动。**

相机会在开启后立即进行校准，你也可以通过按钮或热键进行手动校准。该功能会使面部位置重置为向前。**校准十分重要，所以在运行时，请务必保持面无表情平视相机。**

[[https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/face_track_win_2.png]]

网络摄像头追踪设置可用于自定义面部追踪值的计算方式。同样，大多数功能都不言自明。在找到合适你的数值之前，可以先尝试不同的数值。接下来将对 **“眨眼关联”** 与 **“网络摄像头参数计算模式”** 进行更详细的解释。


### 眨眼关联：
 
通过该选项，你可以将双眼关联，以防有奇怪的眨眼行为。建议将其设置为“当面部旋转时”，这样做的目的是，当面部向左/右旋转到一定程度时，其中一只眼睛对追踪器而言是不可见的，在这种情况下，另一只可见的眼睛将会被用来控制眨眼。

### 网络摄像头参数计算模式:
 
**“自动”** 是先前的方法，如果这适用于你，请继续使用。初始化需要十秒左右（参见VTube Studio中的说明）。新的 **“手动”** （现为默认）模式则无需等待，且在多数情况下更准确。

在 **“手动”** 模式中，最重要的是将灵敏度滑块调整到合适位置， **并且总是能在保持面无表情、平视摄像头时对其进行校准**。这些模块只会影响网络摄像头追踪，若想为手机追踪设置灵敏度，请使用Android/iOS版本中的对应滑块。
