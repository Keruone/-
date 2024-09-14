# 一篇 makefile 的个人学习经历
> 参考:[Makefile教程](https://blog.csdn.net/weixin_38391755/article/details/80380786)

------------------
[toc]

------------------
## 1. makefile 的接收
### 1.1 makefile 的规则

```
<target> : <prerequisites> 
[tab]  <commands>
...
...
```

**target**也就是一个目标文件，可以是**Object File**，也可以是执行文件。还可以是一个标签（Label），对于标签这种特性，在后续的“伪目标”章节中会有叙述。
**prerequisites**就是，要生成那个**target**所需要的文件或是目标。
**command**也就是**make**需要执行的命令。（任意的Shell命令）


这是一个文件的依赖关系，也就是说，target这一个或多个的目标文件依赖于prerequisites中的文件，其生成规则定义在command中。说白一点就是说，prerequisites中如果有一个以上的文件比target文件要新的话，command所定义的命令就会被执行。这就是Makefile的规则。也就是Makefile中最核心的内容。


*注：在看别人写的Makefile文件时，你可能会碰到以下三个变量：`$@`，`$^`，`$<`代表的意义分别是： 
* `$@`--目标文件
* `$^`--所有的依赖文件
* `$<`--第一个依赖文件。

---

### 1.2 makefile 的一个案例
这个示例来源于GNU的make使用手册，在这个示例中，我们的工程有8个C文件，和3个头文件，我们要写一个Makefile来告诉make命令如何编译和链接这几个文件。
```
   edit : main.o kbd.o command.o display.o \
          insert.o search.o files.o utils.o
           cc -o edit main.o kbd.o command.o display.o \
                      insert.o search.o files.o utils.o 

   main.o : main.c defs.h
           cc -c main.c

   kbd.o : kbd.c defs.h command.h
           cc -c kbd.c

   command.o : command.c defs.h command.h
           cc -c command.c

   display.o : display.c defs.h buffer.h
           cc -c display.c

   insert.o : insert.c defs.h buffer.h
           cc -c insert.c

   search.o : search.c defs.h buffer.h
           cc -c search.c

   files.o : files.c defs.h buffer.h command.h
           cc -c files.c

   utils.o : utils.c defs.h
           cc -c utils.c

   clean :
           rm edit main.o kbd.o command.o display.o \
              insert.o search.o files.o utils.o
```

**反斜杠（\）** 是换行符的意思。这样比较便于Makefile的易读。我们可以把这个内容保存在文件为“Makefile”或“makefile”的文件中，然后在该目录下直接输入命令“make”就可以生成执行文件edit。如果要删除执行文件和所有的中间目标文件，那么，只要简单地执行一下“make clean”就可以了。

在这个makefile中，目标文件（target）包含：执行文件edit和中间目标文件（*.o），依赖文件（prerequisites）就是冒号后面的那些 .c 文件和 .h文件。每一个 .o 文件都有一组依赖文件，而这些 .o 文件又是执行文件 edit 的依赖文件。依赖关系的实质上就是说明了目标文件是由哪些文件生成的，换言之，目标文件是哪些文件更新的。

在定义好依赖关系后，后续的那一行定义了如何生成目标文件的操作系统命令，一定要以一个Tab键作为开头。记住，make并不管命令是怎么工作的，他只管执行所定义的命令。make会比较targets文件和prerequisites文件的修改日期，如果prerequisites文件的日期要比targets文件的日期要新，或者target不存在的话，那么，make就会执行后续定义的命令。

 这里要说明一点的是，clean不是一个文件，它只不过是一个动作名字，有点像C语言中的lable一样，其冒号后什么也没有，那么，make就不会自动去找文件的依赖性，也就不会自动执行其后所定义的命令。要执行其后的命令，就要在make命令后明显得指出这个lable的名字。这样的方法非常有用，我们可以在一个makefile中定义不用的编译或是和编译无关的命令，比如程序的打包，程序的备份，等等。