引用就像一个指针，指针指向一个地址，通过这个地址我们可以访问到保存的数据；这个数据被一些其他的变量拥有。与指针不同的是，在引用的生命周期内，它保证指向一个特定类型的合法值。

```Rust
fn main() {
    let s1 = String::from("hello");
    
    let len = calculate_length(&s1);
    
    println!("The length of '{}' is {}.", s1, len);
}

fn calculate_length(s: &String) -> usize {
    s.len()
}
```

==**&**==代表了引用，它允许指向一些值而不带走他的所有权。

当函数用引用作为参数，而不是实际的值，我们不需要返回值来返还所有权，因为我们从没有拥有过所有权。

==**我们把创建引用的行为叫做租借（borrowing).**==

引用的变量默认不可变，就像变量默认不可变一样。

## Mutable References

```rust
fn main() {
    let mut s = String::from("hello");
    
    change(&mut s);
}

fn change(some_string: &mut String) {
    some_string.push_str(", world");
}
```

首先，变量是可变的；其次，创建一个可变引用当调用函数时；最后更新函数声明，使其可以接受一个可变引用。

可变引用一个很大的约束：如果你对一个值有了可变引用，对于这个值将不再能有其他的引用。

数据竞争与竞争条件的类似，当以下三种行为发生时出现：

- 两个或多个指针同时访问相同的数据。
- 至少一个指针正在改写数据。
- 没有机制将用于同步访问数据。

一个引用的作用域开始于它被引入的地方，一直到它再次使用。

## Dangling References

> 如果你有一个指向一些数据的指针，在对数据引用之前，编译器会确认数据不会超出作用域。

## The Rules of References

> - 在任何给定的时间，你可以有一个可变引用或者任何数量的不可变引用。
> - 引用必须总是合法。