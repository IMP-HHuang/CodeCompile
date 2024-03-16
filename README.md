# [MakeFile](https://www.cs.colby.edu/maxwell/courses/tutorials/maketutor/)

```
#注释
CC:=gcc #变量声明，赋值(后续操作保持该值不变)
CFLAGS=-I. #变量声明，赋值（如果右侧的表达式包含了其他变量引用或者命令执行，那么这些操作将会延迟到变量被引用时才进行）
DEPS = hellomake.h #多个字符组成变量引用时要用括号，否则只认第一个字符
OBJ = hellomake.o hellofunc.o 

#左边为目标（$@调用），右边为依赖($^(规则中的所有依赖项列表,即所有的源文件; $<(规则中的第一个,也就是规则的第一个源文件)调用)
#-c 指示编译器只进行编译，而不进行链接。这个选项通常用于将源文件编译成目标文件（通常是 .o 文件），而不生成最终的可执行文件或共享库
%.o: %.c $(DEPS)
	$(CC) -c -o $@ $< $(CFLAGS) #-o指定编译器生成的目标文件

hellomake: $(OBJ)
	$(CC) -o $@ $^ $(CFLAGS)
```
