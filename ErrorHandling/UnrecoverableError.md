## Unrecoverable Errors with panic!

> Rust有 ==*panic!*== 宏。在实践中，有两种方式会触发panic，一种是执行一个导致panic的动作（比如越界访问一个数组），一种是显式的调用 ==panic!== 宏命令。
>
> 通常情况下，这些paincs将会打印一个失败信息，展开，清理堆栈，然后退出。

显式调用 ==panic!== 宏：

```rust
fn main() {
    panic!("crush and burn");
}
```



## Using a panic! Backtrace

```rust
fn main() {
    let v = vec![1, 2, 3];
    
    v[99];
}
```

> 通过设置 ==RUST_BACKTRACE=1== 环境变量来获得到底发生了什么导致出现错误的调用栈信息。使用方法为：
>
> ```shell
> $ RUST_BACKTRACE=1 cargo run
> ```
>
> 