## What Is Ownership?

*Ownership*（所有权）是一系列决定Rust程序如何管理内存的规则。Rust通过编译器检查一系列所有权系统规则来管理内存。如何规则被违反，程序将不被编译。

## Ownership Rules

- 在Rust中每个值都有拥有者。
- 一次只能有一个拥有者。
- 当拥有者超出了作用域，值将会被删除。