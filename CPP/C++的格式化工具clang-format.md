# C++的格式化工具clang-format

## 主要用法

```sh
# OS X 需要先安装
brew install clang-format
# 以LLVM代码风格格式化main.cpp, 结果输出到stdout
clang-format main.cpp -style=LLVM
# 以LLVM代码风格格式化main.cpp, 结果直接写到main.cpp
clang-format -i main.cpp -style=LLVM
# 当然也支持对指定行格式化，格式化main.cpp的第1，2行
clang-format -lines=1:2 main.cpp
```