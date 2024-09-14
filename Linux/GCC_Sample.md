# GCC 编译案例解析
创作者：Keruone、Github Copilot
创作时间：2024/9/14
使用设备：Ubuntu20.04.06 in VirtualBox


>本文档为编译过程的输出日志
用于学习编译过程的细节
下面将进行逐行解释
### 目录
[toc]

### 注意：
#### 关于 gcc 的输出
* 正确应该运行`gcc -o test test.c -v > output.log 2>&1`这个命令会将所有输出（包括标准输出和标准错误）重定向到 output.log 文件中。

* gcc 的大部分详细输出（由 -v 标志触发）实际上是通过标准错误（stderr）输出的。
* 这意味着 output.log 文件可能会几乎为空，或者只包含很少的信息。
* 如果你只想捕获标准错误（gcc 的详细输出主要在标准错误中）：`gcc -o test test.c -v 2> output.log`这个命令只会将标准错误输出重定向到 output.log 文件中。
* 如果你想同时在屏幕上看到输出，并且将输出保存到文件中，可以使用 tee 命令：`gcc -o test test.c -v 2>&1 | tee output.log`
#### 关于本文
本文绝大多数内容由 Github Copilot 生成，本人也处于学习阶段，如有问题，请上网搜索，勿扰谢谢！

-------------
## 完整 output.log
文件链接[在这](./output.log)
<pre style="white-space: pre-wrap;">
<code>
Using built-in specs.
COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-linux-gnu/9/lto-wrapper
OFFLOAD_TARGET_NAMES=nvptx-none:hsa
OFFLOAD_TARGET_DEFAULT=1
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 9.4.0-1ubuntu1~20.04.2' --with-bugurl=file:///usr/share/doc/gcc-9/README.Bugs --enable-languages=c,ada,c++,go,brig,d,fortran,objc,obj-c++,gm2 --prefix=/usr --with-gcc-major-version-only --program-suffix=-9 --program-prefix=x86_64-linux-gnu- --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --libdir=/usr/lib --enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --with-default-libstdcxx-abi=new --enable-gnu-unique-object --disable-vtable-verify --enable-plugin --enable-default-pie --with-system-zlib --with-target-system-zlib=auto --enable-objc-gc=auto --enable-multiarch --disable-werror --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --enable-multilib --with-tune=generic --enable-offload-targets=nvptx-none=/build/gcc-9-9QDOt0/gcc-9-9.4.0/debian/tmp-nvptx/usr,hsa --without-cuda-driver --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 9.4.0 (Ubuntu 9.4.0-1ubuntu1~20.04.2) 
COLLECT_GCC_OPTIONS='-o' 'test' '-v' '-mtune=generic' '-march=x86-64'
 /usr/lib/gcc/x86_64-linux-gnu/9/cc1 -quiet -v -imultiarch x86_64-linux-gnu test.c -quiet -dumpbase test.c -mtune=generic -march=x86-64 -auxbase test -version -fasynchronous-unwind-tables -fstack-protector-strong -Wformat -Wformat-security -fstack-clash-protection -fcf-protection -o /tmp/ccTLWMN6.s
GNU C17 (Ubuntu 9.4.0-1ubuntu1~20.04.2) version 9.4.0 (x86_64-linux-gnu)
	compiled by GNU C version 9.4.0, GMP version 6.2.0, MPFR version 4.0.2, MPC version 1.1.0, isl version isl-0.22.1-GMP

GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
ignoring nonexistent directory "/usr/local/include/x86_64-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/9/include-fixed"
ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/9/../../../../x86_64-linux-gnu/include"
#include "..." search starts here:
#include <...> search starts here:
 /usr/lib/gcc/x86_64-linux-gnu/9/include
 /usr/local/include
 /usr/include/x86_64-linux-gnu
 /usr/include
End of search list.
GNU C17 (Ubuntu 9.4.0-1ubuntu1~20.04.2) version 9.4.0 (x86_64-linux-gnu)
	compiled by GNU C version 9.4.0, GMP version 6.2.0, MPFR version 4.0.2, MPC version 1.1.0, isl version isl-0.22.1-GMP

GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
Compiler executable checksum: 01da938ff5dc2163489aa33cb3b747a7
COLLECT_GCC_OPTIONS='-o' 'test' '-v' '-mtune=generic' '-march=x86-64'
 as -v --64 -o /tmp/ccK4AjM6.o /tmp/ccTLWMN6.s
GNU assembler version 2.34 (x86_64-linux-gnu) using BFD version (GNU Binutils for Ubuntu) 2.34
COMPILER_PATH=/usr/lib/gcc/x86_64-linux-gnu/9/:/usr/lib/gcc/x86_64-linux-gnu/9/:/usr/lib/gcc/x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/9/:/usr/lib/gcc/x86_64-linux-gnu/
LIBRARY_PATH=/usr/lib/gcc/x86_64-linux-gnu/9/:/usr/lib/gcc/x86_64-linux-gnu/9/../../../x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/9/../../../../lib/:/lib/x86_64-linux-gnu/:/lib/../lib/:/usr/lib/x86_64-linux-gnu/:/usr/lib/../lib/:/usr/lib/gcc/x86_64-linux-gnu/9/../../../:/lib/:/usr/lib/
COLLECT_GCC_OPTIONS='-o' 'test' '-v' '-mtune=generic' '-march=x86-64'
 /usr/lib/gcc/x86_64-linux-gnu/9/collect2 -plugin /usr/lib/gcc/x86_64-linux-gnu/9/liblto_plugin.so -plugin-opt=/usr/lib/gcc/x86_64-linux-gnu/9/lto-wrapper -plugin-opt=-fresolution=/tmp/cc2C58D6.res -plugin-opt=-pass-through=-lgcc -plugin-opt=-pass-through=-lgcc_s -plugin-opt=-pass-through=-lc -plugin-opt=-pass-through=-lgcc -plugin-opt=-pass-through=-lgcc_s --build-id --eh-frame-hdr -m elf_x86_64 --hash-style=gnu --as-needed -dynamic-linker /lib64/ld-linux-x86-64.so.2 -pie -z now -z relro -o test /usr/lib/gcc/x86_64-linux-gnu/9/../../../x86_64-linux-gnu/Scrt1.o /usr/lib/gcc/x86_64-linux-gnu/9/../../../x86_64-linux-gnu/crti.o /usr/lib/gcc/x86_64-linux-gnu/9/crtbeginS.o -L/usr/lib/gcc/x86_64-linux-gnu/9 -L/usr/lib/gcc/x86_64-linux-gnu/9/../../../x86_64-linux-gnu -L/usr/lib/gcc/x86_64-linux-gnu/9/../../../../lib -L/lib/x86_64-linux-gnu -L/lib/../lib -L/usr/lib/x86_64-linux-gnu -L/usr/lib/../lib -L/usr/lib/gcc/x86_64-linux-gnu/9/../../.. /tmp/ccK4AjM6.o -lgcc --push-state --as-needed -lgcc_s --pop-state -lc -lgcc --push-state --as-needed -lgcc_s --pop-state /usr/lib/gcc/x86_64-linux-gnu/9/crtendS.o /usr/lib/gcc/x86_64-linux-gnu/9/../../../x86_64-linux-gnu/crtn.o
COLLECT_GCC_OPTIONS='-o' 'test' '-v' '-mtune=generic' '-march=x86-64'

</code>
</pre>
-------------
## 详细解析

**Using built-in specs.**
> 使用内置规范

**COLLECT_GCC=gcc**    
> 收集gcc编译器 后接的是gcc的路径

**COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-linux-gnu/9/lto-wrapper**
> 收集LTO（link-time optimization）包装器 后接的是lto-wrapper的路径

**OFFLOAD_TARGET_NAMES=nvptx-none:hsa**
>OFFLOAD_TARGET_NAMES是一个环境变量，用于指定目标设备，这里指定了两个目标设备，分别是nvptx-none和hsa
offload是一个编译器的功能，用于将代码分发到不同的设备上执行
nvptx-none是一个CUDA的目标设备，hsa是一个Heterogeneous System Architecture的目标设备
Heterogeneous System Architecture是一个异构计算的标准，用于将CPU和GPU等不同的计算设备整合在一起
OFFLOAD_TARGET_DEFAULT=1
OFFLOAD_TARGET_DEFAULT是一个环境变量，用于指定默认的目标设备，这里指定了1，表示默认目标设备是nvptx-none
这里的默认目标设备是nvptx-none，表示默认情况下，编译器会将代码分发到CUDA设备上执行
**Target: x86_64-linux-gnu**
>目标设备是x86_64-linux-gnu，表示编译器的目标设备是x86_64架构的Linux系统

**Configured with: ../src/configure -v --with-pkgversion='Ubuntu 9.4.0-1ubuntu1~20.04.2' --with-bugurl=file:///usr/share/doc/gcc-9/README.Bugs --enable-languages=c,ada,c++,go,brig,d,fortran,objc,obj-c++,gm2 --prefix=/usr --with-gcc-major-version-only --program-suffix=-9 --program-prefix=x86_64-linux-gnu- --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --libdir=/usr/lib --enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --with-default-libstdcxx-abi=new --enable-gnu-unique-object --disable-vtable-verify --enable-plugin --enable-default-pie --with-system-zlib --with-target-system-zlib=auto --enable-objc-gc=auto --enable-multiarch --disable-werror --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --enable-multilib --with-tune=generic --enable-offload-targets=nvptx-none=/build/gcc-9-9QDOt0/gcc-9-9.4.0/debian/tmp-nvptx/usr,hsa --without-cuda-driver --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu**
>配置信息，表示编译器的配置信息

编译器配置选项
| 选项 | 含义 |
|------|------|
| `../src/configure -v --with-pkgversion='Ubuntu 9.4.0-1ubuntu1~20.04.2' --with-bugurl=file:///usr/share/doc/gcc-9/README.Bugs` | 表示编译器的配置文件是 `../src/configure`，`-v` 表示显示详细信息，`--with-pkgversion` 表示包的版本信息，`--with-bugurl` 表示 bug 的 URL |
| `--enable-languages=c,ada,c++,go,brig,d,fortran,objc,obj-c++,gm2` | 表示编译器支持的语言，包括 `c,ada,c++,go,brig,d,fortran,objc,obj-c++,gm2` |
| `--prefix=/usr` | 表示编译器的安装路径是 `/usr` |
| `--with-gcc-major-version-only` | 表示只显示 gcc 的主版本号 |
| `--program-suffix=-9` | 表示编译器的程序后缀是 `-9` |
| `--program-prefix=x86_64-linux-gnu-` | 表示编译器的程序前缀是 `x86_64-linux-gnu-` |
| `--enable-shared` | 表示编译器支持共享库 |
| `--enable-linker-build-id` | 表示编译器支持链接器的构建 ID |
| `--libexecdir=/usr/lib` | 表示编译器的执行库路径是 `/usr/lib` |
| `--without-included-gettext` | 表示编译器不包含 gettext |
| `--enable-threads=posix` | 表示编译器支持 POSIX 线程 |
| `--libdir=/usr/lib` | 表示编译器的库路径是 `/usr/lib` |
| `--enable-nls` | 表示编译器支持国际化 |
| `--enable-clocale=gnu` | 表示编译器支持 GNU 的 C 语言环境 |
| `--enable-libstdcxx-debug` | 表示编译器支持 `libstdc++` 的调试 |
| `--enable-libstdcxx-time=yes` | 表示编译器支持 `libstdc++` 的时间 |
| `--with-default-libstdcxx-abi=new` | 表示编译器的默认 `libstdc++` 的 ABI 是 `new` |
| `--enable-gnu-unique-object` | 表示编译器支持 GNU 的唯一对象 |
| `--disable-vtable-verify` | 表示编译器不支持 vtable 的验证 |
| `--enable-plugin` | 表示编译器支持插件 |
| `--enable-default-pie` | 表示编译器默认支持 PIE |
| `--with-system-zlib` | 表示编译器使用系统的 zlib |
| `--with-target-system-zlib=auto` | 表示编译器的目标系统的 zlib 是自动的 |
| `--enable-objc-gc=auto` | 表示编译器的 Objective-C 的 GC 是自动的 |
| `--enable-multiarch` | 表示编译器支持多架构 |
| `--disable-werror` | 表示编译器不支持错误警告 |
| `--with-arch-32=i686` | 表示编译器的 32 位架构是 `i686` |
| `--with-abi=m64` | 表示编译器的 ABI 是 `m64` |
| `--with-multilib-list=m32,m64,mx32` | 表示编译器的多架构列表是 `m32,m64,mx32` |
| `--enable-multilib` | 表示编译器支持多架构 |
| `--with-tune=generic` | 表示编译器的调优是通用的 |
| `--enable-offload-targets=nvptx-none=/build/gcc-9-9QDOt0/gcc-9-9.4.0/debian/tmp-nvptx/usr,hsa` | 表示编译器的 offload 目标是 `nvptx-none` 和 `hsa` |
| `--without-cuda-driver` | 表示编译器不包含 CUDA 驱动 |
| `--enable-checking=release` | 表示编译器的检查是发布的 |
| `--build=x86_64-linux-gnu` | 表示编译器的构建是 `x86_64-linux-gnu` |
| `--host=x86_64-linux-gnu` | 表示编译器的主机是 `x86_64-linux-gnu` |
| `--target=x86_64-linux-gnu` | 表示编译器的目标是 `x86_64-linux-gnu` |


**Thread model: posix**
> 线程模型是posix，表示编译器的线程模型是POSIX线程

**gcc version 9.4.0 (Ubuntu 9.4.0-1ubuntu1~20.04.2)**
>gcc的版本是9.4.0，Ubuntu的版本是9.4.0-1ubuntu1~20.04.2

**COLLECT_GCC_OPTIONS='-o' 'test' '-v' '-mtune=generic' '-march=x86-64'**
>收集gcc的选项，-o表示输出文件是test，-v表示显示详细信息，-mtune=generic表示调优是通用的，-march=x86-64表示架构是x86-64

**/usr/lib/gcc/x86_64-linux-gnu/9/cc1 -quiet -v -imultiarch x86_64-linux-gnu test.c -quiet -dumpbase test.c -mtune=generic -march=x86-64 -auxbase test -version -fasynchronous-unwind-tables -fstack-protector-strong -Wformat -Wformat-security -fstack-clash-protection -fcf-protection -o /tmp/ccTLWMN6.s**
编译选项解释
| 选项 | 含义 |
|------|------|
| `/usr/lib/gcc/x86_64-linux-gnu/9/cc1` | gcc 的前端编译器 |
| `-quiet` | 安静模式 |
| `-v` | 显示详细信息 |
| `-imultiarch x86_64-linux-gnu` | 多架构是 x86_64-linux-gnu |
| `test.c` | 源文件是 test.c |
| `-dumpbase test.c` | 输出文件是 test.c |
| `-mtune=generic` | 调优是通用的 |
| `-march=x86-64` | 架构是 x86-64 |
| `-auxbase test` | 辅助文件是 test |
| `-version` | 版本信息 |
| `-fasynchronous-unwind-tables` | 异步解开表 |
| `-fstack-protector-strong` | 堆栈保护强 |
| `-Wformat` | 格式警告 |
| `-Wformat-security` | 格式安全 |
| `-fstack-clash-protection` | 堆栈冲突保护 |
| `-fcf-protection` | CF 保护 |
| `-o /tmp/ccTLWMN6.s` | 输出文件是 /tmp/ccTLWMN6.s |

**GNU C17 (Ubuntu 9.4.0-1ubuntu1~20.04.2) version 9.4.0 (x86_64-linux-gnu)**
>GNU C17是gcc的版本，Ubuntu 9.4.0-1ubuntu1~20.04.2是Ubuntu的版本
x86_64-linux-gnu是目标设备
compiled by GNU C version 9.4.0, GMP version 6.2.0, MPFR version 4.0.2, MPC version 1.1.0, isl version isl-0.22.1-GMP

**compiled by GNU C version 9.4.0, GMP version 6.2.0, MPFR version 4.0.2, MPC version 1.1.0, isl version isl-0.22.1-GMP**
>编译器的版本是9.4.0，GMP的版本是6.2.0，MPFR的版本是4.0.2，MPC的版本是1.1.0，isl的版本是isl-0.22.1-GMP
GMP是GNU的多精度算术库，MPFR是多精度浮点运算库，MPC是多精度复数运算库，isl是整数集合库

**GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072**
>GGC是gcc的垃圾收集器，heuristics是启发式算法，--param ggc-min-expand=100表示最小扩展是100，--param ggc-min-heapsize=131072表示最小堆大小是131072

**ignoring nonexistent directory "/usr/local/include/x86_64-linux-gnu"**
>忽略不存在的目录"/usr/local/include/x86_64-linux-gnu"

**ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/9/include-fixed"**
>忽略不存在的目录"/usr/lib/gcc/x86_64-linux-gnu/9/include-fixed"

**ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/9/../../../../x86_64-linux-gnu/include"**
>忽略不存在的目录"/usr/lib/gcc/x86_64-linux-gnu/9/../../../../x86_64-linux-gnu/include"

**#include "..." search starts here:**
**#include <...> search starts here:**
 **/usr/lib/gcc/x86_64-linux-gnu/9/include**
 **/usr/local/include**
 **/usr/include/x86_64-linux-gnu**
 **/usr/include**
**End of search list.**
>`#include "..." search starts here:`表示包含文件的搜索路径，here后面没有路径，表示当前目录
`#include <...> search starts here:`表示包含文件的搜索路径，here后面没有路径，表示当前目录
`/usr/lib/gcc/x86_64-linux-gnu/9/include`表示gcc的头文件路径
`/usr/local/include`表示本地的头文件路径
`/usr/include/x86_64-linux-gnu`表示x86_64-linux-gnu的头文件路径
`/usr/include`表示系统的头文件路径
从上到下是包含文件的搜索路径，从上到下的顺序是优先级，优先级高的先搜索
`End*`搜索列表的结束

**GNU C17 (Ubuntu 9.4.0-1ubuntu1~20.04.2) version 9.4.0 (x86_64-linux-gnu)**
>GNU C17是gcc的版本，Ubuntu 9.4.0-1ubuntu1~20.04.2是Ubuntu的版本
x86_64-linux-gnu是目标设备

**compiled by GNU C version 9.4.0, GMP version 6.2.0, MPFR version 4.0.2, MPC version 1.1.0, isl version isl-0.22.1-GMP**
>编译器的版本是9.4.0，GMP的版本是6.2.0，MPFR的版本是4.0.2，MPC的版本是1.1.0，isl的版本是isl-0.22.1-GMP
GMP是GNU的多精度算术库，MPFR是多精度浮点运算库，MPC是多精度复数运算库，isl是整数集合库

**GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072**
>GGC是gcc的垃圾收集器，heuristics是启发式算法，--param ggc-min-expand=100表示最小扩展是100，--param ggc-min-heapsize=131072表示最小堆大小是131072

**Compiler executable checksum: 01da938ff5dc2163489aa33cb3b747a7**
> 编译器可执行文件的校验和是01da938ff5dc2163489aa33cb3b747a7

**COLLECT_GCC_OPTIONS='-o' 'test' '-v' '-mtune=generic' '-march=x86-64'**
>收集gcc的选项，-o表示输出文件是test，-v表示显示详细信息，-mtune=generic表示调优是通用的，-march=x86-64表示架构是x86-64

 **as -v --64 -o /tmp/ccK4AjM6.o /tmp/ccTLWMN6.s**
>as是汇编器，-v表示显示详细信息，--64表示64位，-o /tmp/ccK4AjM6.o表示输出文件是/tmp/ccK4AjM6.o，/tmp/ccTLWMN6.s表示输入文件是/tmp/ccTLWMN6.s

**GNU assembler version 2.34 (x86_64-linux-gnu) using BFD version (GNU Binutils for Ubuntu) 2.34**
>GNU assembler是2.34，x86_64-linux-gnu是目标设备，BFD是GNU Binutils for Ubuntu，版本是2.34

**COMPILER_PATH=/usr/lib/gcc/x86_64-linux-gnu/9/:/usr/lib/gcc/x86_64-linux-gnu/9/:/usr/lib/gcc/x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/9/:/usr/lib/gcc/x86_64-linux-gnu/**
>COMPILER_PATH是编译器的路径，包括/usr/lib/gcc/x86_64-linux-gnu/9/等

**LIBRARY_PATH=/usr/lib/gcc/x86_64-linux-gnu/9/:/usr/lib/gcc/x86_64-linux-gnu/9/../../../x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/9/../../../../lib/:/lib/x86_64-linux-gnu/:/lib/../lib/:/usr/lib/x86_64-linux-gnu/:/usr/lib/../lib/:/usr/lib/gcc/x86_64-linux-gnu/9/../../../:/lib/:/usr/lib/**
>LIBRARY_PATH是库的路径，包括/usr/lib/gcc/x86_64-linux-gnu/9/等

**COLLECT_GCC_OPTIONS='-o' 'test' '-v' '-mtune=generic' '-march=x86-64'**
>收集gcc的选项，-o表示输出文件是test，-v表示显示详细信息，-mtune=generic表示调优是通用的，-march=x86-64表示架构是x86-64

 **/usr/lib/gcc/x86_64-linux-gnu/9/collect2 -plugin /usr/lib/gcc/x86_64-linux-gnu/9/liblto_plugin.so -plugin-opt=/usr/lib/gcc/x86_64-linux-gnu/9/lto-wrapper -plugin-opt=-fresolution=/tmp/cc2C58D6.res -plugin-opt=-pass-through=-lgcc -plugin-opt=-pass-through=-lgcc_s -plugin-opt=-pass-through=-lc -plugin-opt=-pass-through=-lgcc -plugin-opt=-pass-through=-lgcc_s --build-id --eh-frame-hdr -m elf_x86_64 --hash-style=gnu --as-needed -dynamic-linker /lib64/ld-linux-x86-64.so.2 -pie -z now -z relro -o test /usr/lib/gcc/x86_64-linux-gnu/9/../../../x86_64-linux-gnu/Scrt1.o /usr/lib/gcc/x86_64-linux-gnu/9/../../../x86_64-linux-gnu/crti.o /usr/lib/gcc/x86_64-linux-gnu/9/crtbeginS.o -L/usr/lib/gcc/x86_64-linux-gnu/9 -L/usr/lib/gcc/x86_64-linux-gnu/9/../../../x86_64-linux-gnu -L/usr/lib/gcc/x86_64-linux-gnu/9/../../../../lib -L/lib/x86_64-linux-gnu -L/lib/../lib -L/usr/lib/x86_64-linux-gnu -L/usr/lib/../lib -L/usr/lib/gcc/x86_64-linux-gnu/9/../../.. /tmp/ccK4AjM6.o -lgcc --push-state --as-needed -lgcc_s --pop-state -lc -lgcc --push-state --as-needed -lgcc_s --pop-state /usr/lib/gcc/x86_64-linux-gnu/9/crtendS.o /usr/lib/gcc/x86_64-linux-gnu/9/../../../x86_64-linux-gnu/crtn.o**
链接选项解释
| 选项 | 含义 |
|------|------|
| `/usr/lib/gcc/x86_64-linux-gnu/9/collect2` | 链接器 |
| `-plugin /usr/lib/gcc/x86_64-linux-gnu/9/liblto_plugin.so` | 插件 |
| `-plugin-opt=/usr/lib/gcc/x86_64-linux-gnu/9/lto-wrapper` | 插件选项 |
| `-plugin-opt=-fresolution=/tmp/cc2C58D6.res` | 插件选项 |
| `-plugin-opt=-pass-through=-lgcc` | 插件选项 |
| `-plugin-opt=-pass-through=-lgcc_s` | 插件选项 |
| `-plugin-opt=-pass-through=-lc` | 插件选项 |
| `--build-id` | 构建 ID |
| `--eh-frame-hdr` | eh 帧头 |
| `-m elf_x86_64` | 目标是 elf_x86_64 |
| `--hash-style=gnu` | 哈希风格是 gnu |
| `--as-needed` | 需要汇编 |
| `-dynamic-linker /lib64/ld-linux-x86-64.so.2` | 动态链接器是 /lib64/ld-linux-x86-64.so.2 |
| `-pie` | PIE |
| `-z now` | 立即 |
| `-z relro` | RELRO |
| `-o test` | 输出文件是 test |
| `/usr/lib/gcc/x86_64-linux-gnu/9/../../../x86_64-linux-gnu/Scrt1.o` | Scrt1.o |
| `/usr/lib/gcc/x86_64-linux-gnu/9/../../../x86_64-linux-gnu/crti.o` | crti.o |
| `/usr/lib/gcc/x86_64-linux-gnu/9/crtbeginS.o` | crtbeginS.o |
| `-L/usr/lib/gcc/x86_64-linux-gnu/9` | 库路径 |
| `-L/usr/lib/gcc/x86_64-linux-gnu/9/../../../x86_64-linux-gnu` | 库路径 |
| `-L/usr/lib/gcc/x86_64-linux-gnu/9/../../../../lib` | 库路径 |
| `-L/lib/x86_64-linux-gnu` | 库路径 |
| `-L/lib/../lib` | 库路径 |
| `-L/usr/lib/x86_64-linux-gnu` | 库路径 |

**COLLECT_GCC_OPTIONS='-o' 'test' '-v' '-mtune=generic' '-march=x86-64'**
>收集gcc的选项，-o表示输出文件是test，-v表示显示详细信息，-mtune=generic表示调优是通用的，-march=x86-64表示架构是x86-64

-----------------
<p align="right">
2024/9/14
<br>
Keruone
</p>