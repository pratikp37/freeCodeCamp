---
title: Garbage Collection
localeTitle: 垃圾收集
---
## 垃圾收集

#### 什么是垃圾收集？

在一般情况下，垃圾收集（GC）只是收集或获取已分配给对象的内存，这在目前我们程序的任何部分都没有使用。简要说明如下。

垃圾收集是程序试图释放对象不再使用的内存空间的过程，等等。垃圾收集对每种语言的实现都不同。大多数高级编程语言都有某种垃圾收集。低级编程语言可以通过库添加垃圾收集。

如上所述，每种编程语言都有自己的GC方式。在C编程中，开发人员需要使用malloc（）和dealloc（）函数来处理内存分配和释放。但是，如果C＃开发人员不需要处理GC，也不建议使用它。

####内存分配如何发生？ 在C＃中，对象的内存分配发生在托管堆中。由CLR（公共语言运行时）负责。堆中的内存分配是通过操作系统中的win32 dll完成的，就像在C中一样。但是，In C对象被放置在内存中，其中自由空间适合对象的大小。而且，内存映射是基于Linkedlist概念的。在C＃中，堆的内存分配以线性方式发生。像一个接一个。

每当创建一个新对象时。在堆中分配内存，并将指针移动到下一个内存地址。 C＃中的内存分配比C快。因为，在C中，内存需要为对象进行搜索和分配。所以它需要比C＃更高的时间。

\#### C＃GC中的生成？ 在.net编程中，堆有三代，分别叫做第0代，第1代，第2代。每当创建新对象时，第0代就会被填充。当第0代被填满时，垃圾收集器运行。新创建的对象放在第0代中。执行垃圾收集时，所有不需要的对象都被销毁，内存被释放并压缩。一旦GC发生，GC就会指向释放内存的指针。

世代1和2具有寿命更长的对象。第1代和第2代的GC将不会发生，直到第0代有足够的内存来分配。

不建议以编程方式调用GC。让它自己发生是件好事。每当第0代被填充时，GC就会调用。 GC不会影响程序的性能。

垃圾收集是程序试图释放变量，对象等不再使用的内存空间的过程。垃圾收集对每种语言的实现都不同。大多数高级编程语言都内置了某种垃圾收集。低级编程语言可能会通过库添加垃圾收集。

垃圾收集是一种为程序员节省时间的工具，例如它取代了对C语言中的malloc（）和free（）等函数的需求。它还可以帮助防止内存泄漏。

垃圾收集的缺点是它对性能有负面影响。程序必须定期运行程序，检查对象引用和清理内存 - 这会占用资源并且通常需要程序暂停。

如果对象没有引用（不再可访问），则它有资格进行垃圾回收。例如，在下面的Java代码中，最初由'thing1'引用的Thing对象将其唯一的引用重定向到堆上的另一个对象 - 然后它将无法访问，并且其内存将由垃圾收集器取消分配。

```java
class Useless { 
  public static void main (String[] args) { 
  Thing thing1 = new Thing(); 
  Thing thing2 = new Thing(); 
  thing2 = thing1; // direct thing2's reference towards thing1 
                   // no references access thing2 
 } } 
```

垃圾收集的一个例子是ARC，它是自动引用计数的缩写。例如，这在Swift中使用。 ARC归结为跟踪对所有创建对象的引用。如果引用量降至0，则将标记该对象以进行重新分配。

#### 更多信息：

*   https://docs.microsoft.com/en-us/dotnet/standard/garbage-collection/fundamentals - 了解有关垃圾收集的更多信息