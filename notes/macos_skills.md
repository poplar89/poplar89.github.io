## Mac 使用习惯/技巧
###  触摸板
1. 系统偏好设置 —> 触摸板 —> 轻点来点
2. 系统偏好设置 —> 辅助功能 —> 鼠标与触摸板：有鼠标或无线触控板时忽略内建触摸板
   
### 键盘
1. 系统偏好设置 —> 键盘 —> 将F1、F2等键用作标准功能键
2. 系统偏好设置 —> 键盘 —> 快捷键 —> 全键盘控制：选择“所有控制”
3. 系统偏好设置 —> 键盘 —> 快捷键 —> 应用快捷键：去掉“显示帮助菜单”
4. 系统偏好设置 —> 键盘 —> 快捷键 —> 屏幕快照
5. 系统偏好设置 —> 键盘 —> 文本：修改自动纠正
   
### 界面
1. 系统偏好设置 —> 程序坞 —> 将窗口最小化为程序窗口
2. 系统偏好设置 —> 日期与时间：使用24小时格式时钟
3. 系统偏好设置 —> 语言与地区：24小时制
4. 系统偏好设置 -> 键盘 -> 快捷键 -> 新建位于文件夹位置的终端窗口
   
### 聚焦搜索
1. 系统偏好设置 —> 聚焦 —> 去掉不需要的类别
    1. 去掉搜索结果中的代码文件：安装Xcode后，上述设置中去掉"开发者"类别
    2. 上文中对于Xcode的安装可以可以使用`touch /Applications/Xcode.app`来代替
    
### 启动台 LaunchPad
1. 删除从AppStore安装的引用
    1. 长按图标
    2. ⌥
    
### 安全
1. 系统偏好设置 —> 安全性与隐私 —> 进入睡眠或开始屏幕保护程序“立即”要求输入密码
2. 系统偏好设置 —> 用户与群组 —> 客人用户：不允许客人用户登录到这台电脑
3. 任何来源
    1. ```sudo spctl --master-disable```
    2. ```sudo xattr -r -d com.apple.quarantine 应用路径```
   
### 网络
1. 系统代理忽略某些主机与域的代理设置：使用英文逗号分隔才生效     
### [快捷键](../imgs/mac_skills_accelerator_key.png)：
1. 窗口全屏 ⌘ ^ F
2. 全屏窗口之间切换 ^ ←/→
3. Finder中显示隐藏文件：⌘ ⇪ .
4. 锁定屏幕：⌘ ^ Q
5. 同一软件不同窗口之间切换：⌘ \`
6. 输入全角空格 拼音输入法状态下 ⌥ Space
7. Finder中文件剪切
    1. ⌘ C
    2. ⌘ ⌥ V

### [小技巧/Scripts](macos_skills_other.md)

### 常见问题
1. 不能完成此操作，因为找不到一个或多个需要的项目。（错误代码 -43）重启Finder `killall Finder`
2. [Mac不能按预期睡眠或唤醒](https://support.apple.com/zh-cn/HT204760)
3. Xcode Server Builder无法关闭
    1. Xcode -> Preferences -> Server & Bots -> OFF
    2. Finder进入/Applications/Xcode.app/Contents/Developer/Applications
    3. 将Xcode Server Builder.app 拖入“系统偏好设置 -> 聚焦 -> 隐私”的列表中

备注: 
     ⌘ Command
     ^ Ctrl
     ⇧ Shift
     ⌥ Option
     ⇪ Caps Lock
    
