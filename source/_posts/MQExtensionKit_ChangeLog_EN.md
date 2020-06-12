---
title: MQExtensionKit ChangeLog (English)
categories: Geek
---

## MQExtensionKit ChangeLog

---
---

**2020-06-12 10:50:00**

> <big>IMPORTANT</big> for the `Realm` database's aggressive update , MQDataBase's development will be temporarily pasued since `4.1.9` , and removed from MQExtensionKit.

**2019-08-24 15:32:00**

> updated `NSString+MQExtension` for some localized methods , deprecated some methods in `NSPredicate+MQExtension`.

**2019-06-14 12:22:00**

> updated `NSString+MQExtension` to fix a bug that cause filter ineffective for Chinese Character "一" .

**2019-05-22 11:51:00**

> added `CLLocation+MQExtension` && `CLGeocoder+MQExtension` (MQData) for location-related operations.

**2019-02-22 14:01:38**

> added  `MQVideo_H264_HEVC_Encoder` && `MQVideo_H264_HEVC_Decoder` (MQMedia) for video hardware encode && hardware decode  .

**2018-12-26 14:44:04**

> added  `MQRouter` (MQRouter) .

**2018-08-13 16:22:06**

> added  `NSError+MQExtension` (MQData) .

**2018-08-02 14:04:53**

> added `MQMultiArgumentPerformer` (MQOrigin) for perfoming a selector with multi arguments .

**2018-08-02 11:03:05**

> added  `SVProgressHUD+MQExtension` (MQCustom) for notification issues.

**2018-07-30 12:52:51**

> using new prefix  `MQ` .

**2018-07-09 17:37:21**

> added `NSLock+MQExtension` (MQData) for lock issues .
>
> added `MQNull` (MQOrigin) for replace NSNull holding issues .

**2018-06-27 20:03:04**

> added `MQPointMarker` (MQOrigin) for collect infos on our own ,
>
> added `MQCrashCatcher` (MQOrigin) for catch crashes ,
>
> added `MQPhotoManager` (MQOrigin) for pick photos / videos in album ,
>
> added `MQAudioRecorder` (MQOrigin) for recording audios .

**2018-06-25 19:22:00**

> added `MQTaskManager` (MQOrigin) for easy queue tasks .

**2018-05-04 21:55:33**

> added `MQAuthentication` (MQCommon) for touch id && face id verify , `MQIAPManager`(MQOrigin) for in app purchase  .

**2018-04-23 18:53:35**

> make prefix all `mq_` . remove MQDataBase && MQCustom from MQFull .

**2017-12-22 15:59:44**

> translate all comment in header file into chinese .

**2017-11-28 12:39:59**

> rebuilt `MQBridgeWrapper` in `MQRouter` .

**2017-11-01 19:24:27**

> fix annoying warnings under Xcode 9.

**2017-09-15 17:56:19**

> rename 'CCLocalLib' to 'CCExtensionKit' .
> updated to '3.0.0'
>

**2017-08-10 14:50:52**

> After writing `CCChainOperate` for almost a month , I figured , that , **THIS CAN BE A KIT !**
>
> Therefore , `CCChainKit` was created . 👏👏👏 .
>
> ~~👉👉👉 **[CCChainKit](https://github.com/VArbiter/CCChainKit)**~~
> probably I won't update CCChainKit for a long time , I don't have that time or energy to continue contribute on two repos .

**2017-08-06 15:38:09**

> Well ... I found that local libraries have some issues on spec dependency . Therefore , CCLocalLib was no longer a local lib.
👏👏👏 -> now , jusy run `pod 'LocalLib' ` and cocoapods will do the rest .

**2017-07-01 19:49:01**
> I wrote a new library called `CCChainOperate` .
Why I wrote it ?
>
> well , after years of writing objective-c , i figured some dis-advantage of it . such as you have to use `[]`  everywhere . i just hate that .
>
> but , as we all know , on the opposite side , `swift` was much better , easily to use , simple to unsderstand (though its haven't stable yet).
>
>  Someday , i find , that block , can actually can perform a style like swift , therefore `CCChainOperate ` was born (not complete yet , maybe , forever , but I'll try.).
>  
>  Also , heavily inspired by react-Objc .
