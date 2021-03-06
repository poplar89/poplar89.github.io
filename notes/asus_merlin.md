## Asus Merlin

### 1. 华硕梅林固件自定义设备图标(Asus Merlin Custom Device Icons)
#### 1. 思路

Merlin 在 DHCP 服务器页面中可以自定义设备的图标，但默认提供的图标显然不足以支撑我们日常使用的，因此 Merlin 提供了上传的功能。

但在 MacOS 上上传了图像之后，会发现图像是模糊的。我尝试通过上传 svg 图像来进行展示，遗憾的是系统只支持jpg、jpeg、gif、png、bmp、ico后缀格式。

上传后的文件存储在 /jffs/usericon 文件夹，查看文件内容发现是 data:image/png;base64 开头的文件，显然这是一个 Data URI scheme。

通过转换文件内容发现，我们上传的图像被转换为了 85*85 的图像用于减少空间占用，这也就解释了为什么我们上传了图像之后是模糊的。

于是我又尝试了修改文件的内容为 svg 格式的矢量图像，系统能够展示，但展示的内容没有了系统默认图标的深蓝色边框。

因此，我们可以通过 SFTP 自行上传更高分辨率的图像来解决显示模糊的问题。文件名为设备的 MAC 地址去掉“:”。（文件头尾不要有多余字符否则不展示）

#### 2. 目前遗留的问题
1. 对于页面放大显示，会出现模糊的情况，
2. 无法实现官方 SVG 图标鼠标 over 事件的变白效果

上述问题，无法使用非矢量图进行实现，我们期待华硕官方或 Merlin 进行改进支持 SVG 的上传，这样不仅文件会小，更加美观。

#### 3. 具体操作步骤
1.  通过提供的 [psd 文件](../imgs/merlin/device_icons.psd)，进行导出，PS 导出选项：
	+ 建议分辨率 100+（建议不要太大，以我手中的RT-AC86U 为例，jffs 容量为48M）
	+ 重新取样 两次平方
	+ 选择较小文件以减小文件占用空间
2.  使用 scp 上传文件到 /jffs/usericon/下，文件名是设备 MAC 地址去掉冒号(:).log

### 2. 调用阿里云 Python SDK 实现 DDNS
#### 1. 安装 Entware
1. U盘格式化成 ext2/ext3/ext4 格式, 插入路由器
2. 按照[教程](https://hqt.ro/how-to-install-new-generation-entware/)安装Entware
3. opkg install python gcc
4. 按照[教程](https://pip.pypa.io/en/stable/installing/)安装 pip
5. pip install aliyun-python-sdk-core aliyun-python-sdk-alidns aliyun-python-sdk-ecs
6. 参考[教程](https://github.com/poplar89/poplar89-scripts/blob/master/README.md)设置脚本

### 2. 关于自定义配置
1. 自定义dns解析
/jffs/configs/dnsmasq.conf.add文件中, 格式如:
```
address=/a.com/b.com/2.2.2.2
address=/c.com/1.1.1.1
```