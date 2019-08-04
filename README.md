FFXIV-Zoom-Hack
允许调整游戏摄像机距离超过游戏内允许的最大距离。

国服仅在DX11上4.56版本可正常工作。


在版本更新后提交新的偏移地址
CE 软件在此处下载: http://www.cheatengine.org/downloads.php 本指南使用的版本为 6.5: http://www.cheatengine.org/download/CheatEngine65NoSetup.rar 该指南适用于任何软件版本，但设置上可能有不同的命名

图片指南: https://jayotterbein.com/2016/03/13/hacking-ffxiv-zoom/
如果你熟悉CE软件的话，可以使用以下简洁指南
在 CE: File - Open process. 打开 ffxiv_dx11.exe（最终幻想XIV）
在游戏: 拉到最远视角，确保没有碰上障碍物
在 CE: 在软件右侧，更改 Value Type 为 Float，查找 Value 值 20.0
在游戏: 不使用第一人称模式，拉到最近视角
在 CE: 更改 Value 值为 1.5, 按下键盘上的"enter" 或点击软件上的 "Next Scan"
重复步骤 2-5 直到左边的窗口出现了有意义的值，你能过看到这个值随着游戏视角距离的变化而变化。
在 CE: 右键列表中小数位只有一位的选项，点击"find what writes to this address"
在游戏: 拉进拉远视角一会, 在CE的新窗口中能看到一条指令代码的出现
在 CE:  1. 选择该条指令  2. 在下方的文本框中查找以'<<' 结尾的指令  3. 查找寄存器与偏移量, 你可以看到一些如mov [r9+00000128] 的代码(r9:寄存器 00000128：偏移量)  4. 在寄存器中查找地址 在下方可以发现如 R9=0000019E9BC70AC0 的地址. 把这个地址保存到剪贴板或记事本  5. 返回CE的主窗口
在 CE: 点击 "New Scan", Value Type 设置为 DX11: 8 Bytes, 勾选 "Hex"，开始查找
在 CE: 顶部的列表可能会出现多个值, 点击表里绿色的值:  1. 双击顶部的地址  2. 双击在出现在底部列表里项目的"Address"值  3. 复制新窗口中"Address"框里的内容,内容为 DX9: ffxiv.exe+offset, DX11: ffxiv_dx11.exe+offset  4. ffxiv_dx11.exe+offset中的offset地址即为所寻找的地址
你已经找到了偏移地址，可以着手修改Offset.xml文件, 偏移地址为mxl文件里的DX11或DX9标签内的StructureAddress值

###################### RAW ######################

FFXIV-Zoom-Hack
Allow adjustment of camera zoom and field of vision beyond what the game normally allows.

Works for DX9 and DX11.

You can use the source or download the latest release from here: https://github.com/jayotterbein/FFXIV-Zoom-Hack/releases/latest

Submitting updates to offsets after patch
CE can be downloaded here: http://www.cheatengine.org/downloads.php This guide assumes 6.5: http://www.cheatengine.org/download/CheatEngine65NoSetup.rar It should work with any version, but options may be named differently

Guide with pictures: https://jayotterbein.com/2016/03/13/hacking-ffxiv-zoom/
Quick guide if you're more familiar with CE
In CE: File - Open process. for DX9: ffxiv.exe, DX11: ffxiv_dx11.exe
In game: Zoom all the way out, make sure there are no obstructions
In CE: On the right side, change Value Type to Float. Look for Value 20.0
In game: Zoom all the way in without going to first person
In CE: Change Value to 1.5, hit enter or click "Next Scan"
Repeat steps 2-5 until you see the value of interest in the window on the left. You should see the value changing as you change zoom in game.
In CE: Double click the value in the top, this adds it to the list on the bottom.
In CE: Right-click on the address on the bottom, click "find what writes to this address"
In game: Zoom in and out a few times, CE should update with an instruction in the new new window.
In CE:
Select the instruction
Look for the line which does the writing, it will have '<<' at the end
Look for the register and offset, you should see something like DX9: [ecx+000000F8], DX11: [r9+00000000000000F8] (note: it's been RCX before)
Find the address in the register, at the bottom look for ECX=0125BB80. Save this address, clipboard or notepad.
Get back to the main CE window
In CE: Click "New Scan", Value Type DX9: 4 Bytes, DX11: 8 Bytes, check Hex. Search
In CE: Top list should show multiple results, for all green ones do this until something makes sense:
Double-click the address in the top
Double-click the address in the bottom that appears, make sure to click on the 'Address' value
Copy the address, DX9: ffxiv.exe+offset, DX11: ffxiv_dx11.exe+offset
Check Pointer, change Type to Float
Paste the address in the box above "Add Offset", click OK
If the Value is displayed as a hex: Right-click the row in the bottom, click "show as decimal"
Ensure that value updates as you zoom
You have now found the offset. Modify the Offset.xml, the offset from above (after ffxiv.exe or ffxiv_dx11.exe) is the StructureAddress in the xml.
