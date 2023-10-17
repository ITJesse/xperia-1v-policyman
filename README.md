# Xperia 1 V 解锁 5G 完整体验

本教程适用于：Xperia 1 V 日版无锁（XQ-DQ44)

适用系统版本：67.0.A.4.79B

其他版本请务必不要直接覆盖文件。特别是运营商定制版，请仔细核对后自行修改。

## 基本步骤

### 解锁 Bootloader 并获得 root 权限
据说从 Xperia 1 开始，解锁 BL 就不会丢失任何功能。这里我只测试了两款手机：
* Xperia 10 IV
* Xperia 1 V

解锁后 10 IV 的 DRM 等级降为 L3，再重新上锁后恢复为 L1

而 1 V 的 DRM 则在解锁后保持 L1 的状态

具体过程这里不再赘述。去索尼官网获取解锁码：

https://developer.sony.com/open-source/aosp-on-xperia-open-devices/get-started/unlock-bootloader

然后使用 Magisk 进行 root 操作。

需要提一下的是，在 patch 内核时，要选择 init_boot 而不是 boot

刷写 init_boot 需要进入 fastbootd 界面，可以通过 `adb reboot fastboot` 进入。黑屏状态的 bootloader 模式无法刷写 init_boot

### 打开高通的调试模式

```shell
su
setprop persist.usb.eng 1
```

这时手机会重连，重连后继续执行：


```
su
setprop sys.usb.config rndis,diag,adb
```

手机会再次重连，这时在 QPST 里即可看到手机了。

### 替换 policyman 里的配置文件

在 QPST 里：

Start Client -> EFS Explorer

等待加载文件列表。完成后进入 `policyman` 文件夹。

全选文件夹中所有 xml 文件，拖动到本地进行备份。

请务必再三确认备份的完整性。

下载本项目中的 xml 文件，拖动到文件夹内覆盖。

重启手机，你就能连接到 5G 网络，任务栏会同时出现 VoNR 的标志。
