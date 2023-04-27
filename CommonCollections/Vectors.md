> Vectors允许存储多个值在单一的数据结构中，在内存中一个接一个的放置数据。
>
> Vectors只能存储相同类型的数据。

## Creating a New Vector

```rust
//创建一个新的空Vector

let v: Vec<i32> = Vec::new();
```

> 当想创建一个保存特定类型数据的vector时，可以在尖括号里指定类型。

```rust
// 带初始值的vector
let v = vec![1, 2, 3];
```

> Rust会推断你想存储的值的类型，所以不再需要做类型声明。

## Updating a Vector

> Vector用==`push`==在结尾追加元素。

```rust
let mut v = Vec::new();

v.push(5);
v.push(6);
v.push(7);
v.push(8);
```

> Vector用==`pop`==将末尾元素删除并返回他的值。

## Reading Elements of Vectors

> 引用存储在Vector中的值的方法有两种：通过索引或者用==`get`==方法。

```rust
let v = vec![1, 2, 3, 4, 5];

let third: &i32 = &v[2];
println!("The third element is {third}");

let third: Option<&i32> = v.get(2);
match third {
    Some(third) => println!("The third element is {third}"),
    None => println!("There is no third element."),
}
```

> Vector是由数字索引的，从0开始。
>
> Rust提供两种引用元素的方法的原因是这样你可以选择程序当你使用的索引值超出了存储的元素数量时如何处理。==`[]`==会引起程序panic，而==`get`==会让程序停止。

## Iterating over the Values in a Vector

> 为了轮流访问Vector中的每一个元素，我们应该迭代通过所有元素而不是每次用索引方位一个元素。

```rust
let v = vec![100, 32, 57];
for i in &v {
    println!("{i}");
}
```

```rust
let mut v = vec![100, 32, 57];
for i in &mut v {
    *i += 50;
}
```

## Using an Enum to Store Multiple Types

> 用枚举类型保存不同的类型值，然后将这些枚举类型保存到Vector中，达到Vector保存不同类型值的目的。

```rust
enum SpreadsheetCell {
    Int(i32),
    Float(f64),
    Text(String),
}

let row = vec![
    SpreadsheetCell::Int(3),
    SpreadsheetCell::Text(String::from("blue")),
    SpreadsheetCell::Float(10.12),
];
```

## Dropping a Vector Drops Its Elements

> Vector当超出作用域后将会被释放。