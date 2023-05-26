# Auto_Simulated_Universe
星穹铁道-模拟宇宙全自动化

有一定的断点回复功能，你可以切出去做其他事，切回来会继续自动化。

目前只支持模拟宇宙6，地图数据基本录完了

----------------------------------------------------------------------------------------------

## 免责声明
本软件是一个外部工具旨在自动化崩坏星轨的游戏玩法。它被设计成仅通过现有用户界面与游戏交互,并遵守相关法律法规。该软件包旨在提供简化和用户通过功能与游戏交互,并且它不打算以任何方式破坏游戏平衡或提供任何不公平的优势。该软件包不会以任何方式修改任何游戏文件或游戏代码。

This software is open source, free of charge and for learning and exchange purposes only. The developer team has the final right to interpret this project. All problems arising from the use of this software are not related to this project and the developer team. If you encounter a merchant using this software to practice on your behalf and charging for it, it may be the cost of equipment and time, etc. The problems and consequences arising from this software have nothing to do with it.

本软件开源、免费，仅供学习交流使用。开发者团队拥有本项目的最终解释权。使用本软件产生的所有问题与本项目与开发者团队无关。若您遇到商家使用本软件进行代练并收费，可能是设备与时间等费用，产生的问题及后果与本软件无关。


请注意，根据MiHoYo的 [崩坏:星穹铁道的公平游戏宣言]([https://hsr.hoyoverse.com/en-us/news/111244](https://sr.mihoyo.com/news/111246?nav=news&type=notice)):

    "严禁使用外挂、加速器、脚本或其他破坏游戏公平性的第三方工具。"
    "一经发现，米哈游（下亦称“我们”）将视违规严重程度及违规次数，采取扣除违规收益、冻结游戏账号、永久封禁游戏账号等措施。"

### 用法

**第一次运行**

双击install_requirements.bat安装依赖库

进入游戏，将人物传送到黑塔的办公室，然后双击 **校准.bat** ，切回游戏界面，等待视角转换/原地转圈结束

如果**校准.bat**闪退，可以尝试管理员运行<pre><code>python align_angle.py
</code></pre>

如果改变了鼠标dpi或游戏分辨率/屏幕分辨率/窗口缩放倍率，需要重新校准！

**运行脚本**

人物靠近模拟宇宙（出现f键交互条）

双击run.bat 或者 管理员权限运行 <pre><code>python states.py --find=1
</code></pre>

只支持1920\*1080(窗口化或全屏幕)，必须开启沿用自动战斗，关闭HDR。

info.txt中第一行保存了模拟宇宙开局选的角色，建议改成自己的配队，1表示第一个角色。最好在一号位选远程角色（艾丝妲、三月七）方便开怪。第二行是校准数据，不要改第二行！

第三行是宇宙的难度，如果你要打难度1就改成1保存。第四行是命途选择，默认巡猎，可以直接修改为其它命途，对巡猎做了专门优化，因此除非万不得已不要改命途。

第五行是地图数据的版本，不建议更改。

默认是哪个宇宙就会进哪个！如果你默认不是第6世界，记得先手动切到第6世界！

**更新文件**

双击update.bat

----------------------------------------------------------------------------------------------

### 部分逻辑

选祝福的逻辑是硬选巡猎，事件基本都会跳过，最后一层不会强化祝福，奇物随机选。

寻路模块基于小地图，所以跑图的时候会低头保持小地图不受高亮的天空干扰

小地图中只会识别白色边缘线和黄色交互点。

----------------------------------------------------------------------------------------------

支持增加地图，具体方法为

运行 python states.py --debug=1 --find=1

如果遇到新图会角色停住，这时候结束自动化并且游戏中暂离模拟宇宙

然后运行 python states.py --debug=1 --find=0

注意，一开始的状态必须是刚进图、视角也没有改变的状态

几秒后角色会后退，然后前进。在角色前进时，你可以移动鼠标改变视角。

在地图中绕一圈，感觉差不多就ctrl+c结束进程能得到地图数据了。保存在imgs/maps/xxxxx目录下（可以按修改时间排序）

最好保持低头状态，减少高亮天空的干扰。

有怪的图最好用希儿战技，被锁定会影响小地图识别。

小地图上表示人物视角的淡蓝色扇形（探照灯）也会影响小地图白色边缘线的识别。因此尽量让探照灯少照射到白色边缘。

imgs/maps/xxxxx目录下会存在target.jpg，你可以用windows自带的画图打开它，然后在上面标记点（可以参考其它地图文件中的target.jpg）

靛蓝色：路径点 黄色：终点 绿色：交互点（问号点） 红色：怪点

----------------------------------------------------------------------------------------------

欢迎加入，欢迎反馈bug，QQ群：831830526
