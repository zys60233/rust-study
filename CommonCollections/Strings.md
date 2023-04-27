> 在Rust的核心语言中仅有一种字符串类型，那就是常以借用形式==`&str`==出现的字符串切片==`str`==。
>
> 由Rust的标准库提供的`String`类型是可变长的，值可变，拥有所有权的，UTF-8编码的字符串类型。

## Creating a New String

```rust
//第一种方式
let mut s = String::new();

//第二种方式
let data = "initial contents";
let s = data.to_string();
let s = "initial contents".to_string();

//第三种方式
let s = String::from("initial contents");
```

## Updating a String

```rust
//Appending to a String with push_str and push
//push_str 追加一个字符串
let mut s = String::from("foo");
s.push_str("bar");

//push 追加一个字符
let mut s = String::from("lo");
s.push('l');
```

```rust
//Concatenation with the + Operator or the format! Macro
//+ 连接两个字符串
let s1 = String::from("Hello, ");
let s2 = String::from("world!");
let s3 = s1 + &s2; //s1所有权转移，不可再使用；s2所有权保留，可再次使用

//format! 连接字符串
let s1 = String::from("tic");
let s2 = String::from("tac");
let s3 = String::from("toe");

let s = format!("{s1}-{s2}-{s3}");
```

## Indexing into Strings

> Rust不允许用索引来访问字符串中的单个字符。

## Slicing Strings

> 用==*[]*==加上一个范围值来创建一个包含特定字符的切片。

```rust
let hello = "Здравствуйте";
let s = &hello[0..4];
```

## Methods for Iterating Over Strings

> 分割字符串为单个字符的最好方式是明确你要的是字符还是字节值。

```rust
//需要字符
for c in "Зд".chars() {
    pirntln!("{C}");   //输出З 、 д
}

//需要字节码
for b in "Зд".bytes() {
    println!("{b}");  //输出208、151、208、180
}
```

