# Xperia 1 V 解锁 5G 完整体验

## 基本步骤

### 解锁 Bootloader 并获得 root 权限
这里不再赘述。去索尼官网获取解锁码：

https://developer.sony.com/open-source/aosp-on-xperia-open-devices/get-started/unlock-bootloader

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
