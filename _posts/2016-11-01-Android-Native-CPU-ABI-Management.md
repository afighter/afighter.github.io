# Android 本地 CPU ABI 管理

Android Native CPU ABI Management

Android 本地 CPU ABI 管理
Introduction:

介绍:

=============

Every piece of native code generated with the Android NDK matches a given

"Application Binary Interface" (ABI) that defines exactly how your

application's machine code is expected to interact with the system at runtime.

每一段的本地代码用 Android NDK 产生匹配一个给定的 应用程序二进制接口(ABI),

精确定义你的应用程序的机器代码是在运行时要求与系统互相作用。

A typical ABI describes things in *excruciating* details, and will typically

include the following information:

一个典型的 ABI 用极度的细节描述事情,并且将典型地包括如下信息:

- the CPU instruction set that the machine code should use.

- 机器代码将使用的 CPU 指令集。

- the endianness of memory stores and loads at runtime.

- 运行时内存存贮和加载的字节顺序。

- the format of executable binaries (shared libraries, programs, etc...)

and what type of content is allowed/supported in them.

- 可执行二进制文件(共享库、程序,等等)的格式和什么样的内容类型是在它们中允许或支持的。

- various conventions used to pass data between your code and

the system. (e.g. how registers and/or the stack are used when functions

are called, alignment constraints, etc...)

- 在你的代码和系统之间使用多方面的约定传递数据。

(例如:当函数被调用时如何注册和/或使用堆栈、对齐限制、等等)

- alignment and size constraints for enum types, structure fields and arrays.

- 字节对齐枚举类型、结构字段和数组。

- the list of function symbols available to your machine code at runtime,

generally from a very specific selected set of libraries.

- 运行时你的机器码可得到的函数符号列表,通常来自一组非常具体的精选的库。

This document lists the exact ABIs supported by the Android NDK and the

official Android platform releases.

本文档列出被 Android NDK 和官方的 Android 平台发行版所支持的确切 ABI 。

I. Supported ABIs:

I. 支持的 ABI :

==================

Each supported ABI is identified by a unique name.

每个被支持的 ABI 是通过一个独一无二的名字来标识。

I.1. 'armeabi'

I.1. armeabi

--------------

This is the name of an ABI for ARM-based CPUs that support *at* *least*

the ARMv5TE instruction set.

这是一个基于 ARM CPU 的 ABI 名字,支持至少 ARMv5TE 指令集。

Please refer to following documentation for more details:

了解更多细节请参考如下文档:

- ARM Architecture Reference manual(a.k.aARMARM)
- ARM 体

系结构参考手册
- Procedure Call Standard for the ARM Architecture (a.k.a. AAPCS)

- ARM 体系结构程序调用标准

- ELF for the ARM Architecture(a.k.a. ARMELF)

- ARM 体系结构上的可执行和可链接格式

注:可执行和可链接格式 (英语:Executable and Linkable Format,缩写为ELF),

常被称为ELF格式,在计算机科学中,是一种用于执行档、目的档、共享库和核心转储的标准文件格式。

1999年被86open项目选为x86架构上的类Unix操作系统的二进制文件格式标准,用来取代COFF。

因其可扩展性与灵活性,也可应用在其它处理器、计算机系统架构的操作系统上。

- ABI for the ARM Architecture(a.k.a. BSABI)

- ARM 体系结构 ABI

注:在计算机中,应用二进制接口描述了应用程序(或者其他类型)和操作系统之间或其他应用程序的低级接口。

ABI掩盖了各种细节,如:

1.数据类型、大小和对齐;

2.调用约定(控制着函数的参数如何传送以及如何接受返回值);

3.系统调用的编码和一个应用如何向操作系统进行系统调用;

4.以及在一个完整的操作系统 ABI 中,目标文件的二进制格式、程序库等等。

一个完整的 ABI ,像 Intel 二进制兼容标准 (iBCS),

允许支持它的操作系统上的程序不经修改在其他支持此 ABI 的操作体统上运行。

其他的 ABI 标准化细节包括:

1.C++ 名称修饰,

2.和同一个平台上的编译器之间的调用约定,但是不包括跨平台的兼容性。

ABI不同于应用程序接口(API),API定义了源代码和库之间的接口,

因此同样的代码可以在支持这个 API 的任何系统中编译,

然而 ABI 允许编译好的目标代码在使用兼容 ABI 的系统中无需改动就能运行。

在 Unix 风格的操作系统中,存在很多运行在同一硬件平台上互相相关但是不兼容的操作系统

(尤其是 Intel 80386 兼容系统)。

有一些努力尝试标准化 ABI ,以减少销售商将程序移植到其他系统时所需的工作。

然而,直到现在还没有很成功的例子,虽然 Linux 标准化工作组正在为 Linux 做这方面的努力。

- Base Platform ABI for the ARM Architecture(a.k.a. BPABI)

- ARM 体系结构基础平台 ABI

- C Library ABI for the ARM Architecture(a.k.a. CLIABI)

- ARM 体系结构 C 库 ABI

- C++ ABI for the ARM Architecture(a.k.a. CPPABI)

- ARM 体系结构 C++ ABI

- Runtime ABI for the ARM Architecture(a.k.a. RTABI)

- ARM 体系结构 运行时 ABI

- ELF System V Application Binary Interface (DRAFT - 24 April 2001)

- ELF System V 应用程序二进制接口 (草稿 - 2001-04-24)

注:System V, 曾经也被称为 AT&T System V ,是 Unix 操作系统众多版本中的一支。

- Generic C++ ABI (http://www.codesourcery.com/public/cxx-abi/abi.ht ml)

- 一般的 C++ ABI

Note that the AAPCS standard defines 'EABI' as a moniker used to specify

a _family_ of similar but distinct ABIs.

注意 AAPCS 标准定义 EABI 作为一个标记用来明确说明一个 _family_ 的相似但又不种类不同的 ABI。

Android follows the little-endian ARM GNU/Linux ABI as documented in the following document:

Android 遵照小头字节序 ARM GNU Linux ABI 像如下文档记载:

注:BIG-ENDIAN 就是低位字节排放在内存的高端,高位字节排放在内存的低端。而 LITTLE-ENDIAN 正好相反。

如果我们将 0x1234abcd 写入到以 0x0000 开

 
始的内存中,则结果为
big-endianlittle-endian
0x00000x120xcd
0x00010x340xab
0x00020xab0x34
0x00030xcd0x12
http://www.codesourcery.com/gnu_toolchains/arm/arm _gnu_linux_abi.pdf
With the exception that wchar_t is only one byte.
具有 wchar_t 仅一个字节的例外。
This should not matter in practice since wchar_t is simply *not* really supported
by the Android platform anyway.
在实际中这应该是无关紧要的,因为不管怎么说 wchar_t 简直是不十分被 Android 平台支持。
This ABI does *not* support hardware-assisted floating point computations.
该 ABI 不支持硬件辅助浮点计算。
Instead, all FP operations are performed through software helper functions
that come from the compiler's libgcc.a static library.
作为替代,全部的浮点操作是通过来自编译器的 libgcc.a 静态库中的软件帮助程序函数完成。
Thumb (a.k.a. Thumb-1) instructions are supported.
Thumb(又叫做:Thumb-1)指令是支持的。
Note that the NDK will generate thumb code by default,
unless you define LOCAL_ARM_MODE in your Android.mk
(see docs/ANDROID-MK.html for all details).
注意 NDK 默认将产生 thumb 代码,除非你在你的 Android.mk 文件中定义 LOCAL_ARM_MODE 变量值。
( 参见 docs/ANDROID-MK.html 了解更多细节 )
I.2. 'armeabi-v7a'
I.2. armeabi-v7a
------------------
This is the name of another ARM-based CPU ABI that *extends* 'armeabi' to
include a few CPU instruction set extensions as described in the following
document:
这是其它基于 ARM CPU ABI 名字,扩展 armeabi 包含几个 CPU 指令集增设部分,正如以下文档描述:
- ARM Architecture v7-a Reference Manual
- ARM 体系结构 v7-a 参考手册
The instruction extensions supported by this Android-specific ABI are:
指令增设部分被 Android 特定 ABI 支持的是:
- The Thumb-2 instruction set extension.
- Thumb-2 指令集增设部分。
- The VFP hardware FPU instructions.
- 矢量浮点硬件浮点单元指令。
注:VFP(Vector Float Point 矢量浮点)是在协同处理器针对ARM架构的派生技术。
它提供低成本的单精度和倍精度浮点运算能力,并完全兼容于ANSI/IEEE Std 754-1985 二进制浮点算数标准。
VFP 提供大多数适用于浮点运算的应用,
例如PDA、智慧手机、语音压缩与解压、3D图像以及数字音效、打印机、机上盒,和汽车应用等。
VFP 架构也支持 SIMD(单指令多重数据)平行化的短矢量指令运行。
这在图像和信号处理等应用上,非常有助于降低编码大小并增加输出效率。
VFU(Float Point Unit 浮点单元)
More specifically, VFPv3-D16 is being used,
which corresponds to 16 dedicated 64-bit floating point registers provided by the CPU.
更

 
具体地说,由 CPU 提供的 16 个专用的 64 位浮点寄存器 VFPv3-D16 是在使用了。
Other extensions described by the v7-a ARM like Advanced SIMD (a.k.a. NEON),
VFPv3-D32 or ThumbEE are optional to this ABI,
which means that developers should check *at* *runtime*
whether the extensions are available and provide alternative code paths
if this is not the case.
v7-a ARM 其余的增设部分像高级的 SIMD (又称 NEON)、VFPv3-D32 或 ThumbEE 对 Android 特定 ABI 来说是可选的,
意味着开发者将在运行时将检查增设部分是否可得到,如果不能是否提供了替代代码路径。
注:SIMD(Single Instruction Multiple Data 单指令多重数据)。
(Just like one typically does on x86 systems to check/use MMX/SSE2/etc...
specialized instructions).
(正像在 x86 系统上典型地检查使用 MMX/SSE2/等等 专门的指令)
You can check docs/CPU-FEATURES.html to see how to perform these runtime checks,
and docs/CPU-ARM-NEON.html to learn about the NDK's support for building NEON-capable machine code too.
你可以核对 docs/CPU-FEATURES.html 参见如何完成这些运行时检查,
参见 docs/CPU-ARM-NEON.html 来学习关于 NDK 也支持生成 NEON 能力的机器代码。
IMPORTANT NOTE:
重要提示:
This ABI enforces that all double values are passed during function calls in 'core' register pairs,
instead of dedicated FP ones.
Android 特定 ABI 迫使全部 double 值在函数调用期间传递用一对核心寄存器,代替一个专用的 FP 。
However, all internal computations can be performed with the FP registers and will be greatly sped up.
然而,全部的内部计算可以用 FP 寄存器完成且将大大地加速。
This little constraint, while resulting in a slight decrease of performance,
ensures binary compatibility with all existing 'armeabi' binaries.
这个小限制,虽然导致工作性能的轻微的减少,确保了全部存在的 armeabi 二进制程序的二进制兼容性。
IMPORTANT NOTE:
重要提示:
The 'armeabi-v7a' machine code will *not* run on ARMv5 or ARMv6 based devices.
armeabi-v7a 机器码将不能运行在基于 ARMv5 或 ARMv6 设备上。
I.3. 'x86'
I.3. x86
----------
This is the name of an ABI for CPUs supporting the instruction set commonly named 'x86' or 'IA-32'.
这是一个支持通常命名为 x86 或 IA-32 指令集 CPU 的 ABI 名字。
More specifically,
this targets the instruction set commonly referenced as 'i686' or 'Pentium Pro' in documents such as:
更具体地说,
这个目标板指令集通常参考如 i686 或 Pentium Pro文档,例

 
如:
Intel IA-32 Intel Architecture Software Developer's Manual volume 2: Instruction Set Reference
英特尔 IA-32 英特尔体系结构软件开发者手册卷 2:指令集参考
IMPORTANT IMPORTANT IMPORTANT IMPORTANT IMPORTANT IMPORTANT:
重要的六次幂之重点:
THE 'x86' ABI IS AN EXPERIMENTAL FEATURE
THAT IS NOT FULLY SUPPORTED YET BY THIS NDK RELEASE.
x86 ABI 是一个试验性的功能,尚不被 NDK 发行版完全支持。
TRYING TO USE IT WILL RESULT IN AN ERROR DURING THE BUILD PROCESS.
尝试使用它将导致在生成过程中出现错误。
Note that optional features like MMX/SSE2/SSE3/3DNow!/KVM must be
explicitly tested at runtime by the generated machine code and
cannot be assumed to be everywhere.
注意可选的功能像 MMX/SSE2/SSE3/3DNow!/KVM 必须用产生的机器码在运行时明确地测试过且不能有任何假定。
II. Generating code for a specific ABI:
II. 为特定的 ABI 产生代码:
=======================================
By default, the NDK will generate machine code for the 'armeabi' ABI.
默认情况下,NDK 将产生 armeabi ABI 机器代码。
You can however add the following line to your Application.mk to generate
ARMv7-a compatible machine code instead:
不过你可以添加如下行到你的 Application.mk 来产生 ARMv7-a 兼容机器代码:
APP_ABI := armeabi-v7a
It is also possible to build machine code for *two* distinct ABIs by using:
它同样可做到生成两种明确的 ABI 机器代码通过以下方式:
APP_ABI := armeabi armeabi-v7a
This will instruct the NDK to build two versions of your machine code:
这将指示 NDK 去生成你的两个版本的机器代码:
one for each ABI listed on this line.
在这行上列出的每一个 ABI 。
Both libraries will be copied to your application
project path and will be ultimately packaged into your .apk.
两个库将都拷贝到你的应用程序工程路径并且最终打包进你的 .apk 中。
Such a package is called a "fat binary" in Android-speak since it contains
machine code for more than one CPU architecture.
这样的一个包用 Android 行话被叫作 “胖二进制”,因为它包含多于一个 CPU 体系结构的机器代码。
At installation time,
the package manager will only unpack the most appropriate machine code for the target device.
在安装时,包管理器将仅仅为目标设备解压最适当的机器代码。
See below for details.
更多细节参见下面。
III. ABI Management on the Android platform:
III. 在 Andorid 平台上的 ABI 管理:
============================================
This section provides specific details about
how the Android platform manages native code in application packages.
这

 
节提供关于 Android 平台如何用应用程序包管理本地代码的具体细节。
III.1. Native code in Application Packages:
III.1. 在应用程序包中的本地代码:
-------------------------------------------
It is expected that shared libraries generated with the NDK are stored in
the final application package (.apk) at locations of the form:
要求用 NDK 产生的共享库将存贮在最终的应用程序包如下形式的位置:
lib//lib.so
Whereis one of the ABI names listed in section II above,
andis a name that can be used
when loading the shared library from the VM as in:
是上面节 II 中已列出的 ABI 名字中的一个,
是用如下代码让虚拟机加载共享库时用到的共享库名:
System.loadLibrary("");
Since .apk files are just zip files,
you can trivially list their content with a command like:
因为 .apk 文件只是 zip 文件,你可以轻易地用如下命令列出它们的内容:
unzip -l
to verify that the native shared libraries you want are indeed at the proper location.
去核实你想要的本地共享库确实在适当的位置。
You can also place native shared libraries at other locations within the .apk,
but they will be ignored by the system,
or more precisely by the steps described below;
you will need to extract/install them manually in your application.
你同样可以放置本地共享库在 .apk 中的其它位置,但是它们将被系统忽略,或由下面步骤更精确地描述:
In the case of a "fat" binary, two distinct libraries are thus placed in the .apk,
for example at:
在 “胖二进制” 的情况中,两个明确的库是如此放置在 .apk 文件中的,例如:
lib/armeabi/libfoo.so
lib/armeabi-v7a/libfoo.so
III.2. Android Platform ABI support:
III.2. Android 平台 ABI 支持:
------------------------------------
The Android system knows at runtime which ABI(s) it supports.
Android 系统在运行时知道它支持哪个 ABI 。
More precisely,
up to two build-specific system properties are used to indicate:
更确切地说,取决于两个特定的生成系统属性用来指出:
- the 'primary' ABI for the device,
corresponding to the machine code used in the system image itself.
- 设备首要的 ABI ,相应的机器代码应用于系统镜像自身。
- an optional 'secondary' ABI,
corresponding to another ABI that is also supported by the system image.
- 一个可选的次要的 ABI ,相应的另一个ABI 同样

 
被系统镜像所支持。
For example, a typical ARMv5TE-based device would only define
the primary ABI as 'armeabi' and not define a secondary one.
例如,一个典型的基于 ARMv5TE 的设备将仅定义首要 ABI 为 armeabi 且不定义一个次要 ABI 。
On the other hand,
a typical ARMv7-based device would define the
primary ABI to 'armeabi-v7a' and the secondary one to 'armeabi'
since it can run application native binaries generated for both of them.
另一方面,一个典型的基于 ARMv7 设备将定义首要 ABI 为 armeabi-v7a 且次要 ABI 为 armeabi ,
因为它可以运行它们两个产生的应用程序本地二进制代码。
III.3. Automatic extraction of native code at install time:
III.3. 在安装时自动选取本地代码:
-------------------------------------------------- ---------
When installing an application,
the package manager service will scan the .apk
and look for any shared library of the form:
当安装一个应用程序时,包管理器服务将扫描 .apk 文件并寻找每一个如下格式的共享库:
lib/
/lib.so
If one is found,
then it is copied under $APPDIR/lib/lib.so,
where $APPDIR corresponds to the application's specific data directory.
如果找到一个,那么它是被拷贝到 $APPDIR/lib/lib.so ,$APPDIR 对应应用程序的特定数据目录。
If none is found,
and a secondary ABI is defined,
the service will then scan for shared libraries of the form:
如果没有一个被找到,且次要 ABI 是已定义,服务将于是扫描如下格式的共享库:
lib//lib.so
If anything is found, then it is copied under $APPDIR/lib/lib.so
如果有共享库是找到了,那么它是被拷贝到 $APPDIR/lib/lib.so
This mechanism ensures that the best machine code for the target
device is automatically extracted from the package at installation time.
这个机制确保在安装时自动从包中抽出最好的机器代码提供给目标设备。

