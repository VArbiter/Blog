---
title: 什么是 Mixins ?
categories: Geek
---

# 在 Dart ( Also Flutter ) 中 , 什么是 Mixins

### 作者 [Romain Rastel](https://medium.com/@lets4r?source=post_page-----3a72344011f3----------------------)
### [原文地址(科学上网)](https://medium.com/flutter-community/dart-what-are-mixins-3a72344011f3)

### 译者 : [ElwinFrederick](https://github.com/VArbiter)

> 
> 译者注 :
> 在学习 flutter 的时候 , 对于 诸如 **SingleTickerProviderStateMixin** , **ProviderStateMixin** 很不理解 , 
> 而在网上的书籍教程之类的对于 mixin 几乎都是一句话带过 , 并不多讲 . 
> 现今又被人问起 , 讲了很久才明白 = = ... 
> 科学上网找了很久 , 发现了这篇文章 . 
> 讲的很好 , 然而并没有中文 , 所以我就翻译下 
>

---

## 译文

>
> 当我 开始学习 [Dart](https://dart.dev) , mixins 的概念对于我来说是全新的 . 我从 C# 这个没有 mixins 的地方转到 Dart (据我所知至少 C# 8.0 之前) .
> 最开始 , 我发现这个概念不知怎么的很难懂 , 直到我认识到了它是多么的强大 .
>
> 声明 : [Mixins 在 Dart2 被引入](https://github.com/dart-lang/language/blob/master/working/0006.%20Super-invocations%20in%20mixins/0007.%20Mixin%20declarations/lrhn-strawman.md) , 以下的一些内容可能在你读到的时候已经不太适用了 .
> (译者注: 概念还是相通的)
>

### 🤔 为什么需要 mixins ?

> 
> 例如 C# 之类的语言压根没有 mixins , 可能是没那么有用 ... 吗?
> 让我们来看看下面的继承树 :
>

![示例图表 1](https://raw.githubusercontent.com/VArbiter/Blog/develop/source/_posts/images/WhatAreMixins/1.png "继承树")

> 
> 这里有一个拥有三个子类 **(Mammal (哺乳动物) , Bird (鸟类) 和 Fish (鱼类))** 的祖类称之为 **Animal(动物)**  .
> 在底部 , 我们构造了一些类 . 那些小方块代表了行为 .
> 例如 , 蓝色的方块代表了这个类拥有这个行为的实例可以 swim (游泳)
>
> 一些动物有一些共同的行为 : Cat (猫) 和 dove (鸽子) 都可以步行 , 但是猫不可以飞 ([Nyan Cat(彩虹猫)](https://www.youtube.com/watch?v=QH2-TGUlwu4)除外) (译者注 , 链接是油管视频 , 需科学上网)
>
> 这些行为在这个类中是相互交错的 , 所以我们不能再这些类的父类中实现这些行为 .
>
> 如果一个类可以有超过一个父类 , 这就很容易了 . 我们可以创建三个其它的类 **Walker (步行) , Swimmer (游泳), Flyer (飞行)**
> 之后 , 我们可以将 **Dove (鸽子)** 和 **Cat (猫)** 继承自 **Walker (步行)** 类 . 
> 但是 在 Dart 中 , 每个类 (除了 `Object`) 只有一个父类 . (译者注 , 单继承)
>
> 除了继承自  **Walker (步行)** 类 , 我们可以实现一个类似接口 , 但是我们要实现在很多类中实现很多次 . 所以这不是个好的解决办法 .
> 
> 我们需要一种可以在多个类别中 , 多次复用一个类中代码的方法 .
> 猜猜看? Mixins 就是为此而生的 .
>
>>  Mixins are a way of reusing a class’s code in multiple class hierarchies. (译者注 , 这里不翻译了 , 原汁原味)
>> [**—dartlang.org**](https://dart.dev/guides/language/language-tour#adding-features-to-a-class-mixins)
>
> 这么形容 , 是否就感觉容易了呢 😁? 

### 🔒 限制

> mixins 有一些限制 (源自: [**dartlang.org**](https://dart.dev/guides/language/language-tour#adding-features-to-a-class-mixins))
>
>> · Dart 1.12 或更低版本的 , 支持 mixins 必须扩展自(extend) `Object` , 而且不能 调用 `super()`.
>> · Dart 1.13 或更高 , mixins 可以在 `Object` 之外扩展 , 也可以调用 `super.method()`. 这个仅仅在 默认的 Dart VM 和 带参的 Analyzer (译者注 , 是 Dart 的静态代码分析器) . 更确切的说 , 是在命令行工具调用 `analyzer` 加上  `--supermixin` .  这个也同样在服务器中有效 , 在客户端配置的选项中 . Dart2js 和 dartdevc 不支持 此类调用 .
>> · 在 Dart 2.1 中 , mixins 限制减少 . 例如 , **Flutter** 支持 mixins 调用 `super()` , 也同样支持扩展自除了 `Object` 类之外的其他类. (译者注 , 划重点 , 敲黑板!) . 但语法似乎在所有 Dart SDK 支持之前就有所改变 . 更多细节 , 参考 [mixin](https://github.com/dart-lang/sdk/blob/master/docs/language/informal/mixin-declaration.md)

### 📝 语法

> 我们见识到了 mixins 的有用之处 , 现在看一下如何创建和使用他们 .
> 
> Mixins 隐式的声明在了 平常的类 中
>

``` dart
    class Walker {
      void walk() {
        print("I'm walking");
      }
    }
```

>
> 如果我们想避免 mixin 被实例化或被扩展 , 我们可以这样定义
>

``` dart
    abstract class Walker {
      // 这个类已经被当做 mixin 来使用 , 所以它不应当被直接扩展
      factory Walker._() => null;

      void walk() {
        print("I'm walking");
      }
    }
```

>
> 若想使用 mixin , 使用 `with` 关键字 , 用来跟随一个或者多个 mixin 声明
> 

``` dart
    class Cat extends Mammal with Walker {}

    class Dove extends Bird with Walker, Flyer {}
```

>
> 在 `Cat` 类中 定义 `Walker` mixin , 这样允许我们直接调用 `walk` 方法 而不是 `fly` 方法 (在 `Flyer` 中定义) 
> 

``` dart
    main(List<String> arguments) {
      Cat cat = Cat();
      Dove dove = Dove();

      // 猫可以走路
      cat.walk();

      // 鸽子可以走和飞
      dove.walk();
      dove.fly();

      // 一只普通的猫不会飞
      // cat.fly(); // 取消注释 , 编译不通过
    }
```

### 🔎  细节

> 
> 我告诉你这个概念有些难以理解 , 但是到现在为止也不是那么难 , 不是嘛 ?
>
> 唔 ... 那么你能告诉我下列程序的输出结果是什么么 😵 ?
>

```dart
    class A {
      String getMessage() => 'A';
    }

    class B {
      String getMessage() => 'B';
    }

    class P {
      String getMessage() => 'P';
    }

    class AB extends P with A, B {}

    class BA extends P with B, A {}

    void main() {
      String result = '';

      AB ab = AB();
      result += ab.getMessage();

      BA ba = BA();
      result += ba.getMessage();

      print(result);
    }
```

>
> 其中 , **AB** 和 **BA** 扩展自 **P** 类 , `with` 上了 **A** 和 **B** mixins , 但是是不同顺序的 .
> 这三个类 **A , B** 和 **P** 都有一个叫做 **getMessage** 的方法 .
>
> 首先 , 我们在  **AB** 类中调用  **getMessage** , 然后调用 **BA** 的 **getMessage** .
>
> **那么 , 输出结果是什么呢 ?**
> 我提供了五个建议选项
>
> **A.** 无法编译
> **B.** BA
> **C.** AB
> **D.** BAAB
> **E.** ABBA
>

---

>
> 🥁🥁🥁 答案是 **B** ! 程序输出 **BA**.
>
> 我想你猜到了 , mixins 的声明顺序是非常重要的 .
>
> 为什么呢 ? 

### ✨ 线性

> 
> 当你在类中遵循了 一个 mixin , 这样想
>
>> 在 Dart 中 , Mixins 是通过在父类的实现之上创建一个新的类
>> 并不是在 "旁边" , 而是在父类 "之上"  , 所以在路由 (译者注 , 继承链) 上就没有歧义
>> (译者注 , 实际上就是在 **父类** 和 **子类** 之间创建了桥接类 , **iOS** 中的 `NSProxy` 也是类似的模拟实现多继承)
>> **— [Lasse R. H. Nielsen](https://stackoverflow.com/users/2156621/lrn) on [StackOverflow](https://stackoverflow.com/questions/45901297/when-to-use-mixins-and-when-to-use-interfaces-in-dart/45903671#45903671).**
> 

>
> 实际上 , 代码
>

```dart
    class AB extends P with A, B {}

    class BA extends P with B, A {}
```

>
>   在语义上相等于
>

```dart
    class PA = P with A;
    class PAB = PA with B;

    class AB extends PAB {}

    class PB = P with B;
    class PBA = PB with A;

    class BA extends PBA {}
```

>
> 最终的继承树可以被这样表示 :
> 

![示例图表 2](https://raw.githubusercontent.com/VArbiter/Blog/develop/source/_posts/images/WhatAreMixins/2.png "继承树2")

>
> 新类在 **AB** 和 **P** 之间被创建. 这些新类是 `mix-in (混合)` 在父类 **P** 和 **A** , **B** 类之间
>
> 所以 , 这里并没有多继承 .
>

>
>> Mixins 并不是一种实现多继承的方式 , 
>> Mixins 是一种可以抽象出且复用的一种 "操作" 或者 "状态" 的集合
>> 它和扩展复用的类很像 , 但它可以适配单继承 , 因为它是线性的
>> **— [Lasse R. H. Nielsen](https://stackoverflow.com/users/2156621/lrn) on [StackOverflow](https://stackoverflow.com/questions/45901297/when-to-use-mixins-and-when-to-use-interfaces-in-dart/45903671#45903671).**
>

> 
> 重要的一点是 , 记住 mixins 被声明的顺序代表了继承链 , 从最顶端的祖类到最底部 .
> 

### 📄 类型 

>
>> mixin 的实例类型是什么 ? 
>> 简单来说 , 它是其父类的子类型 , 同时也是 mixin 名称所指示的类型 ,
>> 即为 , 原来的类型 .
>> (译者注 , 遵循 mixin 的实例的类型是 , 它的父类类型 与 它所遵循的 mixin 类型  , 因为有中间层 , 所以均为其子类)
>> [**—dartlang.org**](https://dart.dev/guides/language/language-tour#adding-features-to-a-class-mixins)
> 

>
> 这就意味着这个程序
> 

```dart
    class A {
      String getMessage() => 'A';
    }

    class B {
      String getMessage() => 'B';
    }

    class P {
      String getMessage() => 'P';
    }

    class AB extends P with A, B {}

    class BA extends P with B, A {}

    void main() {
      AB ab = AB();
      print(ab is P);
      print(ab is A);
      print(ab is B);

      BA ba = BA();
      print(ba is P);
      print(ba is A);
      print(ba is B);
    }
```

>
> 将会在控制台输出六行 `true`
> 

### 细节解释

>
> Lasse R. H. Nielsen 给了我一个非常棒的解释
>
>> 因为每个 mixin 都创建一个新类 , 它也创建了新的 接口 (因为所有 Dart 类都定义接口)
>> 就像形容的那样 , 新类扩展自 父类 , 也包括 (copy) 了 mixin 类的 副本 . 
>> 但是它同时也实现了 mixin 类的接口
>>
>> 在大多数的情况下 , 没有方法可以查到 mixin 的类 或者 其接口
>> `Super with Mixin` 类只是一个匿名父类 (声明类似  `class C extends Super with Mixin {}`)  ,
>> 如果你像是用 `class CSuper = Super with Mixin {}` 命名了一个 mixin ,
>> 那么你可以查到这个 mixin 的类或者其接口 , 同时 , 它也是 父类 和 Mixin 类的子类 .
>>
>> **— [Lasse R. H. Nielsen](https://stackoverflow.com/users/2156621/lrn)**
>

### 🙄 什么时候使用 mixins ?

> 
> 在我们想在多个类之间去共享一个行为 , 且不具备相同的继承时 , 
> 或者在父类中实现这个行为很另类时 , 会非常有用 .
> 
> 在解析(例如 [ jaguar_serializer](https://github.com/Jaguar-dart/jaguar_serializer) ) 或储存中很常见 , 
> 但你也可以使用 mixins 去提供一些 工具方法 (例如 **Flutter** 中的 [RenderSliverHelpers](https://github.com/flutter/flutter/blob/master/packages/flutter/lib/src/rendering/sliver.dart)) .
>

### 📈  Mixins 在进步 (规范)

>
> 如果你对 Dart 语言的发展感兴趣 , 你应该知道它的规范将在 Dart 2.1 中改进 .
> 他们也很欢迎你反馈[使用建议](https://github.com/dart-lang/language/issues/7).
> 详细的信息, 请移步[这里](https://github.com/dart-lang/language/blob/master/working/0006.%20Super-invocations%20in%20mixins/0007.%20Mixin%20declarations/lrhn-strawman.md).
> 

>
> 给你一个瞥见未来的机会 , 思考一下这个源代码
>

```dart
    abstract class Super {
      void method() {
        print("Super");
      }
    }

    class MySuper implements Super {
      void method() {
        print("MySuper");
      }
    }

    mixin Mixin on Super {
      void method() {
        super.method();
        print("Sub");
      }
    }

    class Client extends MySuper with Mixin {}

    void main() {
      Client().method();
    }
```

>
> 第 **13 到 18** 行的 mixin 声明 , 指出了一个父类的限制 .
> 这就意味着 , 如果一个类要遵循这个 mixin , 这个类必须扩展 或者 实现自 `Super`  ,
> 因为这个 mixin 使用的是 `Super` 提供的 特征 . 
> 
> 这个程序的输出是 :
>

```bash
    MySuper
    Sub
```

>
> 如果你想知道为什么 , 请记住 mixins 是线性的 .
>

![示例图表 3](https://raw.githubusercontent.com/VArbiter/Blog/develop/source/_posts/images/WhatAreMixins/3.png "继承树 3")

>
> 实际上 , 在 **15 行** 调用 `super.method()` 是调用 **第 8 行** 的方法 .
>

### 🐬 完善 最开始的 动物 例子

> 
> 你可以在下方代码中找到 我用来解释 mixins 的 **Animal** 的完整例子 .
> 

```dart
    abstract class Animal {}

    abstract class Mammal extends Animal {}

    abstract class Bird extends Animal {}

    abstract class Fish extends Animal {}

    abstract class Walker {
      // 这个类作为 mixin , 不应该被直接扩展
      factory Walker._() => null;

      void walk() {
        print("I'm walking");
      }
    }

    abstract class Swimmer {
      // 这个类作为 mixin , 不应该被直接扩展
      factory Swimmer._() => null;

      void swim() {
        print("I'm swimming");
      }
    }

    abstract class Flyer {
      // 这个类作为 mixin , 不应该被直接扩展
      factory Flyer._() => null;

      void fly() {
        print("I'm flying");
      }
    }

    class Dolphin extends Mammal with Swimmer {}

    class Bat extends Mammal with Walker, Flyer {}

    class Cat extends Mammal with Walker {}

    class Dove extends Bird with Walker, Flyer {}

    class Duck extends Bird with Walker, Swimmer, Flyer {}

    class Shark extends Fish with Swimmer {}

    class FlyingFish extends Fish with Swimmer, Flyer {}
```

>
> 这里我们可以看到这些 mixins 的线性过程 :
> 

![示例图表 4](https://raw.githubusercontent.com/VArbiter/Blog/develop/source/_posts/images/WhatAreMixins/4.png "继承树 4")

### 📗 结论

>
> 至此我们知道了 mixins 是一个很强大的概念 , 它可以让你 在多类多层级中 复用代码 .
>
> **Flutter** 在很多地方使用了这个特性 . 我发现 , 理解 mixins 很重要 , 
> 这也是为什么我在这里和你分享我的理解 .
> 
> 如果你有什么疑问 , 请不要吝惜 👇.
>
> 欢迎任何反馈 . 
>
> 如果你觉得不错 , 可以点击下方 的  👏 . 
> (译者注 , 这是 flutter 社区的 , 可以点击上方原文链接中的 👏 来支持作者)
> 

---

>
> 原作者 : [Romain Rastel](https://medium.com/@lets4r?source=post_page-----3a72344011f3----------------------)
> 原发布时间 : 2018 . 09 . 16 
> 阅读时长 : 7 分钟
>
> 任何交流欢迎邮件至 elwinfrederick@163.com
>




