> `if let`语法让你联合`if`和`let`来用一个简洁的方式处理匹配一个模式的值，而忽略其他的。

```rust
let config_max = Some(3u8);
if let Some(max) = config_max {
    println!("The maximum is configured to be {}", max);
}
```

```rust
//match版
let mut count = 0;
match coin {
    Coin::Quarter(state) => println!("State quarter from {:?}!", state),
    _ => count += 1,
}

//if let ... else ...版
let mut count = 0;
if let Coin::Quarter(State) = coin {
    println!("State quarter from {:?}！", state);
} else {
    count += 1;
}
```

