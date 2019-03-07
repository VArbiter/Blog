---
title: MQExtensionKit Docs (English)
categories: Geek
---

# MQExtensionKit

##### Some custom categories for iOS with Objective-C.

[![Version](https://img.shields.io/cocoapods/v/MQExtensionKit.svg?style=flat)](http://cocoapods.org/pods/MQExtensionKit)

[![License](https://img.shields.io/cocoapods/l/MQExtensionKit.svg?style=flat)](http://cocoapods.org/pods/MQExtensionKit)

[![Platform](https://img.shields.io/cocoapods/p/MQExtensionKit.svg?style=flat)](http://cocoapods.org/pods/MQExtensionKit)

### Current Version 4.0.0

> pod 'MQExtensionKit' , '~> 4.0.0' // default is MQCore
>
> > pod 'MQExtensionKit/MQFull' , '~> 4.0.0' . if you wanna install the whole Kit .

### Warning
>
> CCExtensionKit has no longer effect after version `3.7.0`
>
> cause after `3.7.0` , CCExtensionKit was renamed to `'MQExtensionKit'` .
>
> CCLocalLib has no longer effect after version `2.2.3`
>
> cause after `3.0.0` , CCLocalLib was renamed to `'CCExtensionKit'` .
>
> MQExtensionKit had import the `AdSupport.framework`.
>
> therefore , be ware when submit your app to App Store .

### Note
> when install , default is `MQCore` , `MQCore` contains
>
> > `MQCommon` (Macros) , `MQProtocol` (Protocol) , `MQData` (NS Family), `MQView` (UI Family) .
>
> when you wanna get to Full , install with `"MQExtensionKit/MQFull"` . (MQFull contains `MQCore` , `MQRouter` , `MQOrigin`)

**Instructions**
>
> > MQCore : Core extensions . a abstract collection .
>
> > MQFull : Full extensions (contains MQCore , MQRouter , MQOrigin) . an abstract collection .
>
> > MQCommon : Macros && Common tools .
>
> > MQProtocol : MQProtocol . for MQ . make all the sub-class of NSObject conforms to it .
>
> > MQData :  a extension actions for NS family .
>
> > MQView :  a extension actions for UI family .
>
> > MQOrigin : a kit that for develop for custom views / medias / datas .
>
> > MQRouter : a router for module developing . and "wrapper" was depended on [`MGJRouter`](https://github.com/meili/MGJRouter) ('~> 0.9.3')  .
>
> > MQMedia : Media operate . video , audio , images , etc ...
>
> > MQDataBase : Wrappers for [`Realm`](https://github.com/realm/realm-cocoa) ('~> 2.10.2') && [`FCModel`](https://github.com/marcoarment/FCModel)
>
> > MQCustom :  Custom classes or functions , dependend or based on other vendors .

### Design instruction

The most important was **`non-invade`** , which is , **`Can't change any original API through any DYNAMIC operates . (no method swizz (implement swap) , no search-path changed)`** , Make it based on the original APIs , and through **`non-invade`** ways to achieved convenient functions .

### What's new ?

See [`ChangeLog`](https://varbiter.github.io/2019/02/22/MQExtensionKit_ChangeLog_EN/) .

### Example

To run the example project, clone the repo, and run `pod install` from the Example directory first.

### Requirements

Already done in pod spec.

### Installation

MQExtensionKit is available through [CocoaPods](http://cocoapods.org). To install
it, simply add the following line to your Podfile:

```ruby
pod "MQExtensionKit"
```

### Author

**ElwinFrederick, elwinfrederick@163.com**

### License

MQExtensionKit is available under the MIT license. See the LICENSE file for more info.
