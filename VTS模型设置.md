## 基础设置

<p float="left">
  <img src="https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/model_settings_main.jpg" width="290" /> 
  <img src="https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/model_settings_physics.jpg" width="290" /> 
  <img src="https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/model_settings_autosetup.jpg" width="290" /> 
</p>

在载入模型之后，你可以在VTube Studio模型设置栏中查看模型设置。

在最上方，你可以给模型命名，该名称会显示在模型选择栏。
在下方，你可以看到Live2D模型的文件名与自动生成的VTube Studio模型文件（VTS模型）。

你可以选择一个图标（.jpg或.png文件，点击右上角的图标打开文件选择）与模型的默认待机动画（.model3.json）。你可以在模型文件夹中选择任意文件。

你也可以为你的VTube Studio模型进行自动设置。这将根据标准的Live2D参数名称与数值来设置模型。关于这些参数的更多信息，请参见： https://docs.live2d.com/cubism-editor-manual/standard-parametor-list/# 

如果你修改了参数ID或范围，则无法自动设置模型，需要手动设置。即使使用自动设置，你也可能需要对VTS模型进行微调，以适配Live2D模型。

## 模型移动

通过“模型移动”设置，您可以根据头部位置将模型向左/向右移动或靠近/远离屏幕。通过滑块，您可以设置模型的移动程度。

## 物理设置

在这里，你可以提高或降低你的Live2D物理设置的效果。你也可以开启“风”，这将随机对物理系统添加一个近似于风的力。该功能目前处于试验阶段，效果可能不会很好，取决于模型的设置方式。

VTube Studio曾忽略了Live2D物理设置的“有效性”，这在近期更新中已被修复。 要启用“有效性”设置，请确认未启用“旧版物理”选项。

## VTS参数设置

<p float="left">
  <img src="https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/model_settings_params.jpg" width="290" /> 
  <img src="https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/model_settings_param_in.jpg" width="290" /> 
  <img src="https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/model_settings_param_out.jpg" width="290" /> 
</p>

这是你模型设置中最重要的一部分。在这里，你将会设置面部追踪参数对应控制的Live2D参数。

总而言之：

* 你可以自由地将任何输入参数（面部追踪，鼠标等）映射到任何输出参数（Live2D参数）。 
* 数值的映射方式可以自由配置。例如，输入参数MouthOpen的范围是[0, 1]，0表示关闭，1表示完全张开。如果你的Live2D参数（例如名为ParamMouthOpen）的范围是[-10, 10]，你就可以映射该范围，让(IN, 0)对应(OUT, -10)，(IN, 1)对应(OUT, 10)。或你也可以以其他方式映射它，没有任何限制。
* 红点将显示值在当前输入和输出范围内的位置。
* 通过激活“范围限制”，你可以确保输入或输出值不会超过你为之设置的范围。这也会让数值在接近极限使更为平滑地停止。
* 一般来说，建议只修改输出范围，输入范围保持不变。
* 更高的平滑度会使动作更少颤抖，但会导致动作滞后。多试验一下平滑度，直到找到适合每个参数的数值。在iOS系统上，你应该几乎不需要调整平滑度。
* 自动呼吸将使输出参数以类似呼吸的方式浮动。使用该选项时不需要输入参数，任何已输入参数都会被忽略。
* 自动眨眼将随机把参数减小到零。这可以与任何一个参数相结合，但并非必须。
* 对于输入参数，你能从可用的参数列表中选择。相较于Android，iOS支持更多的面部追踪参数（见下表）。
* 至于输出参数，你可以选择任何Live2D参数。每个输出参数只能选择一次，否则将会有多个输入参数写入同一个输出参数。


[[https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/hint_top.png]]
[[https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/bunny_point.png|alt="Important Point!!"|height=59px|width=189px]]<br/>
如果你模型的Live2D参数在VTS模型设置中有明显浮动，模型本身却没有移动的话，最有可能的原因是一个表情、动画或物理系统覆盖了面部追踪值。这将在以下章节中详细解释： 

[动画、表情、面部追踪、物理等之间的交互](https://github.com/Elegetic/VTubeStudio/wiki/%E5%8A%A8%E7%94%BB%E3%80%81%E8%A1%A8%E6%83%85%E3%80%81%E9%9D%A2%E9%83%A8%E8%BF%BD%E8%B8%AA%E3%80%81%E7%89%A9%E7%90%86%E7%AD%89%E4%B9%8B%E9%97%B4%E7%9A%84%E4%BA%A4%E4%BA%92)
[[https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/hint_bottom.png]]

## 支持的输入参数（面部追踪等）

VTube Studio目前支持以下输入参数，可以将它们映射到输出的Live2D参数上。仅iOS支持的参数在应用中也有相应标记。


| 参数名 | 释义                 | iOS  | Android | 网络摄像头 |
| --------------- | -------------------------- | ---- | ------- | ------- |
| **FacePositionX**  | 面部水平位置 | ✔️  | ✔️      |    ✔️ |
| **FacePositionY** | 面部垂直位置 | ✔️ | ✔️ | ✔️ |
| **FacePositionZ** | 面部离摄像头距离 | ✔️ | ✔️ | ✔️ |
| **FaceAngleX** | 面部右/左回转 | ✔️ | ✔️ | ✔️ |
| **FaceAngleY** | 面部上/下回转 | ✔️ | ✔️ | ✔️ |
| **FaceAngleZ** | 面部倾斜回转 | ✔️ | ✔️ | ✔️ |
| **MouthSmile** | 面部笑容幅度 | ✔️ | ✔️ | ✔️ |
| **MouthOpen** | 嘴部张开程度 | ✔️ | ✔️ | ✔️ |
| **Brows** | 双眉共同上/下移动 | ✔️ | ✔️ | ✔️ |
| **MousePositionX** | 鼠标或手指在设定范围内的X轴位置 | ✔️ | ✔️ | ✔️ |
| **MousePositionY** | 鼠标或手指在设定范围内的Y轴位置 | ✔️ | ✔️ | ✔️ |
| **TongueOut** | 伸出舌头 | ✔️ | ❌ | ❌ |
| **EyeOpenLeft** | 左眼睁开程度 | ✔️ | ❌ | ✔️ |
| **EyeOpenRight** | 右眼睁开程度 | ✔️ | ❌ | ✔️ |
| **EyeLeftX** | 眼部追踪 | ✔️ | ❌ | ✔️ |
| **EyeLeftY** | 眼部追踪 | ✔️ | ❌ | ✔️ |
| **EyeRightX** | 眼部追踪 | ✔️ | ❌ | ✔️ |
| **EyeRightY** | 眼部追踪 | ✔️ | ❌ | ✔️ |
| **CheekPuff** | 检测脸颊鼓起 | ✔️ | ❌ | ❌ |
| **BrowLeftY** | 左眉上/下移动 | ✔️ | ❌ | ✔️ |
| **BrowRightY** | 右眉上/下移动 | ✔️ | ❌ | ✔️ |
| **VoiceFrequency*** | 基于检测到的音素 | ❌ | ❌ | ✔️ |
| **VoiceVolume*** | 麦克风音量响度 | ❌ | ❌ | ✔️ |
| **VoiceVolume<br/>PlusMouthOpen*** | MouthOpen + VoiceVolume | ❌ | ❌ | ✔️ |
| **VoiceFrequency<br/>PlusMouthSmile*** | MouthSmile + VoiceFrequency | ❌ | ❌ | ✔️ |
| **MouthX** | 嘴部X轴位置（嘴巴左/右移动） | ✔️ | ❌ | ❌ |
| **FaceAngry** | 检测怒颜<br/>（试验性功能，不推荐） | ✔️ | ❌ | ❌  |

_\* 这些参数不能在iOS/Android上直接使用，但可以在使用手机进行追踪时于PC/Mac上使用。在手机上加载模型时，VoiceVolumePlusMouthOpen等参数会默认使用MouthOpen的参数值。_


## 热键设置与类型

<p float="left">
  <img src="https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/hotkey_settings_1.jpg" width="290" /> 
  <img src="https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/hotkey_settings_2.jpg" width="290" /> 
  <img src="https://raw.githubusercontent.com/wiki/DenchiSoft/VTubeStudio/img/hiyori_1.jpg" width="290" /> 
</p>


在VTube Studio中，你可以使用热键来触发各种动作。创建好的热键会被保存在VTube Studio模型配置文件中。你可以给热键命名，当热键被激活时，其名称也会显示在日志中。

热键有两种触发方式：


* **键盘热键（仅可用于PC/Mac）**
  * 正如其名，你可以通过键盘按键来触发热键。
  * 你可以设置最多两个键的按键组合。 
  * 即使当VTube Studio窗口不在最前端，比如你在玩游戏时，按键也会被读取。然而，这在macOS上并不适用。
  * 同时包含：鼠标热键（右键/左键/中键）。
 
* **屏幕按钮热键（PC/Mac和手机端）**
  * 最多有八个热键可以设置为屏幕按钮热键。它们将在主界面的右侧以半透明形式呈现。（见图三）
  * 可以调整热键透明度，也能够将其设置为隐形。
  * 你可以自定义每个屏幕按钮的颜色。

  * 如果你启用了 **“将热键发送到电脑”**，在手机上按下按键将给（已连接的）电脑发送信号，表明该ID所对应的按键已被按下。当电脑上加载的模型也设置了屏幕按钮热键时，对应表情就会被触发。
  * 发送热键到电脑的手机上并不需要加载模型。若未加载模型，八个屏幕按钮将会全部显示。

## 热键动作

各种动作都可以通过热键触发：

* **播放动画 (.motion3.json)**
  * 会播放一次指定动画（覆盖面部追踪数据）。
* **切换待机动画 (.motion3.json)**
  * 将切换当前正在循环的待机动画。不会被保存到VTS模型默认设置中。
* **设置/移除表情 (.exp3.json)**
  * 切换模型中的指定表情（覆盖面部追踪数据与动画）。
  * 如果多个表情将同一个Live2D参数设置为不同值，最后一个表情将会决定最终值。
  * 更多参见“表情”章节。
* **移除所有表情**
  * 移除所有当前设置的表情。
* **重新载入模型纹理**
  * 重新载入模型纹理。这意味着你可以在应用外修改模型的.PNG纹理并进行实时重载，可以借此在直播中实现各种炫酷效果。
* **移动模型**
  * 移动模型到指定位置/角度/尺寸。
  * 你可以设置每次运动所使用的时长。 
  * 该热键的位置可以通过“记录位置”按钮来设置，它将保存当前模型的位置、角度和尺寸。数字所对应的是：
    * X方向位置/Y方向位置/尺寸   旋转角度
* **切换背景**
  * 将当前背景改为你在热键中选择的背景。
* **重新载入麦克风**
  * 重新加载当前用于唇音同步的麦克风。
* **校准摄像头**
  * 启动摄像头校准。
* **切换VTS模型**
  * 将当前的VTube Studio模型改为在热键中选择的模型。
* **截图**
  * 用先前的截图设置进行截图。

对于动画和表情，你可以用额外设置来自定义淡出时间和播放形式。例如，你可以在固定秒数或松开按键后停止动画/表情。

特别是对于动画，你可以将它们设置为 **在最后一帧停止**。这将使动画在最后一帧停下并保持所有参数，直至再次按下热键。**所有被用于面部追踪的Live2D参数则不会受此影响** 并会在动画播放结束后自动恢复。