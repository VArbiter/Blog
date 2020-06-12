---
title: MQExtensionKit ChangeLog (中文)
categories: Geek
---

## MQExtensionKit ChangeLog

---
---

**2020-06-12 10:50:00**

> <big>重要</big> 因为 `Realm` 的激进式更新 , MQDataBase 将从 4.1.9 版本开始暂时停止更新 , 并被移除出了 MQExtensionKit

**2019-08-24 15:32:00**

> 更新 `NSString+MQExtension` 中一些本地化方法 , 废弃了 `NSPredicate+MQExtension` 中一些方法 .

**2019-06-14 12:22:00**

> 更新 `NSString+MQExtension` 修复了汉字 "一" 过滤失效的问题

**2019-05-22 11:51:00**

> 添加 `CLLocation+MQExtension` && `CLGeocoder+MQExtension` (MQData) 来做地理相关操作

**2019-02-22 14:01:38**

> 添加  `MQVideo_H264_HEVC_Encoder` && `MQVideo_H264_HEVC_Decoder` (MQMedia) 用来 硬编码 / 硬解码 视频 .

**2018-12-26 14:44:04**

> 添加  `MQRouter` (MQRouter) .

**2018-08-13 16:22:06**

> 添加 `NSError+MQExtension` (MQData) .

**2018-08-02 14:04:53**

> 增加 `MQMultiArgumentPerformer` (MQOrigin) 用来 perform 并携带多个参数 .

**2018-08-02 11:03:05**

> 增加 `SVProgressHUD+MQExtension` (MQCustom) 的通知处理 .

**2018-07-30 12:52:51**

> 使用新的前缀 `MQ` .

**2018-07-09 17:37:21**

> 增加  `NSLock+MQExtension` (MQData) 针对锁相关.
>
> 增加 `MQNull` (MQOrigin) 用来替换 NSNull 空值占位  相关 .

**2018-06-27 20:03:04**

> 增加 `MQPointMarker ` (MQOrigin) 来让自己收集信息 ,
>
> 增加 `MQCrashCatcher` (MQOrigin) 以捕获崩溃 ,
>
> 增加 `MQPhotoManager` (MQOrigin) 用来从相册选择 图片 / 视频 ,
>
> 增加 `MQAudioRecorder` (MQOrigin) 用来录音 .

**2018-06-25 19:22:00**

> 增加 `MQTaskManager` (MQOrigin) 简易队列任务.

**2018-05-04 21:55:33**

> 增加 `MQAuthentication` (MQCommon) 用来做指纹 / 面部验证 , `MQIAPManager`(MQOrigin) 用来做内购相关 .

**2018-04-23 18:53:35**

> 更换所有的前缀为 `mq_` , 将 MQDataBase 和 MQCustom 从 MQFull 中移除

**2017-12-22 15:59:44**

> 将头文件中所有的注释都翻译成汉语 .

**2017-11-28 12:39:59**

> 重构 `MQRouter` 中的 `MQBridgeWrapper` .

**2017-11-01 19:24:27**

> 修复 Xcode 9 下烦人的警告.

**2017-09-15 17:56:19**

> 将 'CCLocalLib' 重命名为 'CCExtensionKit' .
> 更新到 '3.0.0'
>

**2017-08-10 14:50:52**

> 在差不多写了一个月的 `CCChainOperate` 之后 , 我发现 , 它 , **可以成为一个开发库 !**
>
> 所以 , `CCChainKit` 就诞生了 . 👏👏👏 .
>
> ~~👉👉👉 **[CCChainKit](https://github.com/VArbiter/CCChainKit)**~~
> CCChainKit 可能会很长一段时间不再更新了. 维护两个库确实没精力 .

**2017-08-06 15:38:09**

> 呃 ... 我发现 , 本地库在依赖一些其它的第三方库上有一些问题 , 所以 , CCLocalLib 不再是一个本地库了 .
👏👏👏 -> 现在 , 仅仅是 `pod 'LocalLib' ` , cocoapods 就会帮你完成剩下的工作.

**2017-07-01 19:49:01**
> 我创建了一个叫做 `CCChainOperate` 的新库 , 我为啥写他?
>
> 嗯 , 在写了 OC 几年之后 , 我发现它还是有许多不足的地方的 . 比如你必须在几乎所有地方使用 `[]` . 我不喜欢 .
>
> 但是 , 我们都知道 , 相对的 , `swift` 就做的比它好 , 简单使用 , 容易理解 (现在还不太稳定就是了).
>
>  某天 , 我发现 , 经常使用的 block ,  实际上是可以用来模仿 swift 的风格的 , 所以 `CCChainOperate ` 就诞生了 (目前还没完成 , 可能 , 永远也不会 , 但是我会努力尝试的.).
>  
>  当然 , 受到了 React-Objc 的很大启发.
