# α-Remote 简体中文版

基于 [Sebastian Staacks 的 α-Remote](https://github.com/Staacks/alpharemote) 1.4，补齐简体中文界面、帮助、权限提示、通知和常见连接错误。原项目版权和 GPL-3.0 许可证继续保留。

## 安装与语言

- 支持 Android 12（API 31）及以上。
- 中文系统自动使用简体中文；其他系统语言保留上游英文或德文。
- 本 fork 的包名为 `org.aqchsh.alpharemote`，版本为 `1.4-zh.1`，可与原版共存；原版设置不会自动迁移。
- 安装 APK 后授予“附近的设备”权限。如需通知栏遥控，再允许通知权限。

## A6400 + E 18–135mm 的首次设置

1. A6400 固件应为 2.00 或以上。
2. 相机：菜单 → 网络 → 蓝牙设置 → 蓝牙功能 → 开。
3. 相机：菜单 → 网络 → 蓝牙遥控 → 开，再进入蓝牙设置 → 配对。
4. 应用：“设置”→“添加相机”→“搜索相机”，并在相机上确认配对。
5. 镜头 AF/MF 开关保持在 **AF**，相机菜单的对焦模式设为 **MF**。这样镜头仍接受遥控调焦命令。
6. 先测试快门及“向远处调焦”按钮，再开始自动拍摄。

## 焦点包围

固定相机和被摄物，设为单张拍摄，从主体最近的清晰位置开始。向上展开相机界面底部的高级控制，开启“间隔拍摄”和“焦点包围”。

可以先用 **5 张、3 秒间隔、0.1 秒单次调焦时长**测试。调焦由近向远进行。此参数表示驱动镜头的时间，不是毫米距离，也不是精确的固定步数。不同镜头、焦距、距离所需时长不同，请逐组检查清晰区域是否连续覆盖主体。

本应用负责拍摄不同焦点的素材，不负责将照片合成为一张景深合成图。没有在实体 A6400 和镜头上完成本 fork 的配对或拍摄验证，实际兼容性仍需在你的设备上确认。

## 从源码构建

安装 JDK 17、Android SDK Platform 37.0，以及相应 Android Build Tools。设置 `ANDROID_HOME` 后运行：

```sh
./gradlew :app:assembleRelease :app:lintRelease :app:testReleaseUnitTest
```

输出为 `app/build/outputs/apk/release/app-release-unsigned.apk`。安装前需使用自己的签名密钥通过 `zipalign`、`apksigner` 对齐并签名。后续更新必须使用相同的包名和签名证书。

GitHub Actions 会对汉化分支执行上述构建检查，并将未签名 APK 和检查报告上传为 workflow artifact。签名私钥不存放在此仓库。

## 上游与授权

- 上游源码：https://github.com/Staacks/alpharemote
- 本 fork：https://github.com/aqchsh/alpharemote
- 许可证：[GPL-3.0](LICENSE)

汉化修改覆盖所有应用字符串；英文的系统异常、相机报告的型号、实体键盘通用键名和外部网页内容仍可能由系统或外部服务决定。
