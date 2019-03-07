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
> 如果你想安装全部 , 安装 `"MQExtensionKit/MQFull"` . (`MQFull` 包含了 `MQCore` , `MQRouter` , `MQOrigin`)
>

**说明**
>
> > MQCore : 核心拓展 . 一个抽象集合.
>
> > MQFull : 完整的 扩展 (包含 MQCore , MQRouter , MQOrigin) . 一个抽象集合 .
>
> > MQCommon : 宏 和 公共的工具类 .
>
> > MQProtocol : MQProtocol . 为了 MQ . 让所有 NSObject 的子类都遵循它 .
>
> > MQData : NS 族群类库 .
>
> > MQView : UI 族群类库 .
>
> > MQOrigin : 一个由自己开发的自定义视图 / 媒体 / 数据 库.
>
> > MQRouter : 组件化路由 , 其中 wrapper 依赖了 [`MGJRouter`](https://github.com/meili/MGJRouter) ('~> 0.9.3')  .
>
> > MQMedia : 多媒体操作 . 视频 , 音频 , 图像 , 等等 ...
>
> > MQDataBase :  [`Realm`](https://github.com/realm/realm-cocoa) ('~> 2.10.2')  && && [`FCModel`](https://github.com/marcoarment/FCModel) 的包裹 .
>
> > MQCustom :  一些自定义的类和功能 , 依赖或者基于一些其它的第三方 .

### 设计思路

最核心的设计思路是 **`无侵入性`** , 即为 , **不通过任何动态方式 , 更改与原生有关的 API . (没有方法替换 , 没有路径更改等 ... )** , 旨在以原生为基础 , 在其之上通过各种 **`非侵入`** 方式实现便利操作 .

### 上新 ?

请移步 [`ChangeLog`](https://varbiter.github.io/2019/02/22/MQExtensionKit_ChangeLog_CN/) .

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
