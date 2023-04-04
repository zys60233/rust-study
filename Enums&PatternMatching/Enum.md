## Defining an Enum

> 枚举类型提供了一种方法描述一个值是一系列可能值中的一个。

```rust
enum IpAddrKind {
    V4,
    V6,
}
```

## Enum Values

```rust
let four = IpAddrKind::V4;
let six = IpAddrKind::V6;
```

## The Option Enum and Its Advantanges Over Null Values

> ==`Option`==另外一种定义在标准库中的枚举类型。它编码非常常见的一个值可以是某些或者什么也不是的场景。
>
> Rust没有==`NULL`==的特性，Null是一个值代表这里没有值。

```rust
enum Option<T> {
    None,
    Some(T),
}
```

