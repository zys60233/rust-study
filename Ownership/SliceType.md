## The Slice Type

> 切片使你引用一个集合中相邻连续的元素，而不是整个集合。切片是一种引用，所以它没有所有权。

## String Slices

> 字符串切片指向了一个字符串的一部分。

```Rust
let s = String::from("hello world");

let hello = &s[0..5];
let world = &s[6..11];
```

> 如果你想从索引0开始，你可以丢掉那两个句号之前的的值。

```Rust
let s = String::from("hell0");

let slice = &s[0..2];
let slice = &s[..2];
```

> 如果你的切片包括了字符串的最后一个字节，你可以丢掉结尾的数字。

```Rust
let s = String::from("hello");

let len = s.len();

let slice = &s[3..len];
let slice = &[3..];
```

> 你也可以丢掉一个切片的两个值来取整个字符串。

```Rust
let s = String::from("hello");

let len = s.len();

let slice = &s[0..len];
let slice = &s[..];
```

## String Literals as Slices

> 字符串常量保存在二进制。

## String Slices as Parameters

> 如果我们有一个切片，我们可以直接把它传递给函数。如果我们有一个==`String`==,我们可以传递==`String`==的切片或者引用。