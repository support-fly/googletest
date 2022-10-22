## 使用指导

### 编写测试用例
举例
```c++
#include "gtest/gtest.h"
int foo(int a, int b)
{
    return a + b;
}

TEST_F(Test_foo, test_normal)
{
    EXPECT_EQ(2, foo(1, 1));
}

int main(int argc, char const *argv[])
{
    testing::AddGlobalTestEnvironment(new TestSysdbg);
    testing::InitGoogleTest(&argc, argv);
    return RUN_ALL_TESTS();
    return 0;
}
```
### 编译测试用例二进制
```makefile
# 添加 gtest 库
C_FLAGS: -lgtest -lgtest_main
```
### 编译 gtest 库
编译 gtest 库可以使用 Makefile，也可以使用 cmake。默认使用 cmake
```cmakelist
#可通过修改 cmakelist 文件指定编译工具链和配置项进行自定义配置。
```
## 运行解析
### 预处理
所有的宏、包含的头文件、inline函数都是在预处理阶段被预处理器展开的，然后才是经过编译器编译成汇编代码，接着汇编器把汇编代码生成可重定位的目标文件，然后链接器再把可重定位的目标文件链接成可执行文件的目标文件。

可使用下面指令单独调用预处理器对源文件进行预处理：
```makefile
cpp main.cpp main.i –Igoogletest/include/
```


## 问题

## reference
[解析gtest框架运行机制](http://originlee.com/2014/12/01/analys-implementation-of-gtest/)