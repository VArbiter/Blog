---
title: MQExtensionKit 中文文档
categories: Geek
---

# MQExtensionKit

##### 一些以 Objective-C 书写的为 iOS 添加的自定义类库. 

[![Version](https://img.shields.io/cocoapods/v/MQExtensionKit.svg?style=flat)](http://cocoapods.org/pods/MQExtensionKit)

[![License](https://img.shields.io/cocoapods/l/MQExtensionKit.svg?style=flat)](http://cocoapods.org/pods/MQExtensionKit)

[![Platform](https://img.shields.io/cocoapods/p/MQExtensionKit.svg?style=flat)](http://cocoapods.org/pods/MQExtensionKit)

### 当前版本 4.0.0

> pod 'MQExtensionKit' , '~> 4.0.0' // 默认是 MQCore
> 
> > pod 'MQExtensionKit/MQFull' , '~> 4.0.0' . 如果你想安装整个框架.

### Warning
>
> CCExtensionKit 在版本 `3.7.0` 后就失效了
>
> 因为版本`3.7.0`之后 , CCExtensionKit 被重命名为 `'MQExtensionKit'` .
>
> CCLocalLib 在版本 `2.2.3` 后就失效了
> 
> 因为版本`3.0.0`之后 , CCLocalLib 被重命名为 `'CCExtensionKit'` .
> 
> MQExtensionKit 引入了 `AdSupport.framework`
> 
> 所以 , 当你提交应用到 App Store 的时候要注意 .

### Note
> 安装的时候 , 默认是 `MQCore` , `MQCore` 包含了 
> 
> > `MQCommon` (宏) , `MQProtocol` (协议) , `MQData` (NS族群), `MQView` (UI 族群), `MQRuntime` (objc/ runtime 相关)
> 
> 如果你想安装全部 , 安装 `"MQExtensionKit/MQFull"` 
> 

**说明**
> 
> > MQCore : 核心拓展 . 一个抽象集合.
> 
> > MQFull : 全部 (不包括 MQDataBase && MQCustom) . 一个抽象集合 .
> 
> > MQExtensionAssets : 资源集合 , 为未来的使用做准备 . (当前还未启用).
> 
> > MQCommon : 宏 和 公共的工具类 .
> 
> > MQProtocol : MQProtocol . 为了 MQ . 让所有 NSObject 的子类都遵循它 .
> 
> > MQRuntime : 一些 runtime 的封装合集 .
> 
> > MQDataBase :  [`Realm`](https://github.com/realm/realm-cocoa) ('~> 2.10.2')  && && [`FCModel`](https://github.com/marcoarment/FCModel) 的包裹 . 
> 
> > MQRouter : 一个路由的拓展, 依赖了 [`MGJRouter`](https://github.com/meili/MGJRouter) ('~> 0.9.3') && perform actions .
> 
> > MQData : NS 族群类库 .
> 
> > MQView : UI 族群类库 .
> 
> > MQOrigin : 一个由自己开发的自定义视图 / 媒体 / 数据 库.
> 
> > MQCustom :  一些自定义的类和功能 , 依赖或者基于一些其它的第三方 .

### 上新 ?
---
---
**2018-08-13 16:22:06**

> 添加 `NSError+MQExtension` .

**2018-08-02 14:04:53**

> 增加 `MQMultiArgumentPerformer` 用来 perform 并携带多个参数 .

**2018-08-02 11:03:05**

> 增加 `SVProgressHUD+MQExtension` 的通知处理 .

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

### 示例

若想运行示例, 克隆 repo,  在工程文件夹内先运行 `pod install` .

### 要求

已经在 pod spec 中完成了.

### 安装

MQExtensionKit 已经上传到了 [CocoaPods](http://cocoapods.org). 若安装,只需要在你的 Podfile 添加下列代码:

```ruby
pod "MQExtensionKit"
```

### 作者

**ElwinFrederick, elwinfrederick@163.com**

### 许可协议

MQExtensionKit 收到 MIT 协议保护. 详细请查看工程中的 LICENSE 文件.
