## Asus Merlin

1. Asus Merlin Device Icons
Merlin 在 DHCP 服务器页面中可以自定义设备的图标，但默认提供的图标显然不足以支撑我们日常使用的，因此 Merlin 提供了上传的功能。
但在 MacOS 上上传了图像之后，会发现图像是模糊的。我尝试通过上传 svg 图像来进行展示，遗憾的是系统只支持jpg、jpeg、gif、png、bmp、ico后缀格式。
上传后的文件存储在 /jffs/usericon 文件夹，查看文件内容发现是 data:image/png;base64 开头的文件，显然这是一个 Data URI scheme。
通过转换文件内容发现，我们上传的图像被转换为了 85*85 的图像用于减少空间占用，这也就解释了为什么我们上传了图像之后是模糊的。
于是我又尝试了修改文件的内容为 svg 格式的矢量图像，系统能够展示，但展示的内容没有了系统默认图标的深蓝色边框。
因此，我们可以通过 SFTP 自行上传更高分辨率的图像来解决显示模糊的问题。文件名为设备的 MAC 地址去掉“:”。（文件头尾不要有多余字符否则不展示）
目前遗留的问题有：
	1. 对于页面放大显示，会出现模糊的情况，
	2. 官方的 SVG 图标，在鼠标 over 的时候会有变白的效果
	3. 上述问题，无法使用非矢量图进行实现，我们期待华硕官方或 Merlin 进行改进支持 SVG 的上传，这样不仅文件会小，更加美观。

具体操作步骤：
	1. 通过提供的 [psd 文件](../imgs/merlin/device_icons.psd)，进行导出，PS 导出选项：
		1. 建议分辨率 100+（建议不要太大，以我手中的RT-AC86U 为例，jffs 容量为48M）
		2. 重新取样 两次平方
		3. 较小文件
	2. 使用 scp 上传文件到 /jffs/usericon/下