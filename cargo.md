# cargo

### 什么是cargo?

​	Rust的编译系统和包管理器，cargo可以帮助开发人员处理一系列的任务，例如编译代码，下载依赖库和编译这些库。

### cargo的使用

创建项目：

```shell
//创建项目
$ cargo new <project_name> [options]

//编译项目
//编译生成的文件路径：<project_root>/target/debug/<execate_file>
$ cargo build [options]

//编译并运行
//使用上比cargo build编译并手动执行可执行文件要便利，推荐使用
$ cargo run [options] [-- args]

//编译检查
//确保代码没有错误可以编译，不会产生编译结果
$ cargo check [options]
```
