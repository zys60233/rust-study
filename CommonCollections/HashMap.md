> 用键值对的方式存储数据。

## Creating a New Hash Map

> 一种创建空的hash map的方式是用==`new`==函数，并且用==`insert`==函数添加元素。

```rust
use std::collections::HashMap;

let mut scores = HashMap::new();

scores.insert(String::from("Blue"), 10);
scores.insert(String::from("Yellow"), 50);
```

## Accessing Values in a Hash Map

> 通过给==`get`==方法提供对应的key，我们可以从hash map中获取到相应的值。

```rust
use std::collections::HashMap;

let mut scores = HashMap::new();

scores.insert(String::from("Blue"), 10);
scores.insert(String::from("Yellow"), 50);

let team_name = String::from("Blue");
let score = scores.get(&team_name).copied().unwrap_or(0);
```

```rust
//用for循环迭代获取hash map的值
use std::collections::HashMap;

let mut scores = HashMap::new();

scores.insert(String::from("Blue"), 10);
scores.insert(String::from("Yellow"), 50);

for (key, value) in &scores {
    println!("{key}: {value}");
}
```

## Hash Maps and Ownership

```rust
use std::collections::HashMap;

let field_name = String::from("Favorite color");
let field_value = String::from("Blue");

let mut map = HashMap::new();
map.insert(field_name, field_value);
```

> 在被插入hasp map后，变量field_name和field_value便不可再用。

## Updating a Hash Map

```rust
//覆盖旧值
use std::collections::HashMap;

let mut scores = HashMap::new();

scores.insert(String::from("Blue"), 10);
scores.insert(String::from("Blue"), 25);

println!("{:?}", scores);	//{"Blue": 35}
```

```rust
//当key不存在时，添加一个key和value
use std::collections::HashMap;

let mut scores = HashMap::new();
scores.insert(String::from("Blue"), 10);

scores.entry(String::from("Yellow")).or_insert(50);
scroes.entry(String::from("Blue")).or_insert(50);

println!("{:?}", scores);	//{"Yellow": 50, "Blue": 10}
```

```rust
//基于旧值更新
use std::collections::HashMap;

let text = "hello world wonderful world";

let mut map = HashMap::new();

for word in text.split_whitespace() {
    let count = map.entry(word).or_insert(0);
    *count += 1;
}
println!("{:?}", map); //{"world": 2, "hello", 1, "wonderful": 1}
```

## Hashing Functions

> ==`HashMap`==默认使用了一个叫*SipHash*的哈希函数。