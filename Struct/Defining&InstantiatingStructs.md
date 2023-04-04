## Struct Declare
> 一个结构体，或者数据组合，是一个自定义的数据类型，它可以使你把多个相关的值打包到一起并且命名，组成一个有意义的组。

> 结构体和元组相似，两者都拥有多个相关联的值。结构体和元组相同的是，结构体的每一部分都可以是不同类型；与元组不同的是，在结构体中，你将给每一部分数据命名，所以每部分数据意味着什么很清楚。加上这些名字代表着结构体比元组更加灵活：你不需要依赖数据的顺序来指定或者访问一个实例的值。

> 为了命名结构体，我们输入关键字==`struct`==并且命名整个结构体。结构体的名字应该描述这块被组合到一起的数据的意义。然后在花括号内，定义每一部分数据的名字和类型，我们称他们为字段。

```Rust
struct User {
    active: bool,
    username: String,
    email: String,
    sign_in_count: u64,
}
```

> 在定义结构体后使用它，我们通过给每一个字段指定明确的值来创建一个实例。通过指定结构体名称，加上带有键是字段名，值是用字段保存的数据的键值对的花括号内容来创建实例。我们不需要以在结构体中定义的顺序一样来指定字段值。换句话说，结构体的定义就像一个通用的类型模板，实例是用特定的数据填充模板来创建这个类型的值。

```Rust
fn main() {
    let user1 = User {
        active: true,
        username: String::from("someusername123"),
        email: String::from("someone@example.com"),
        sign_in_count: 1,
    };
}
```

> 从结构体中获取数据，使用点符号(.)。

```Rust
fn main() {
    let mut user1 = User {
        active: true,
        username: String::from("someusername123"),
        email: String::from("someone@example.com"),
        sign_in_count: 1,
    };
    
    user1.email = String::fron("anothereamil@example.com");
}
```

> 和其他的表达式一样，我们可以构建一个新的结构体实例作为函数体的最后一个表达式来隐式的返回一个新的实例。

```Rust
fn build_user(email: String, username: String) -> User {
    User {
        active: true,
        username: username,
        email: email,
        sign_in _count: 1
    }
}
```

## Using the Field Init Shorthand

```Rust
fn build_user(email: String, username: String) -> User {
    User {
        active: true,
        username,
        email,
        sign_in_count: 1,
    }
}
```

## Creating Instances from Other Instances with Struct Update Syntax

> 创建一个包含另一个结构体实例大多数的值的新的结构体实例，但是改变一些字段值，你可以用结构体更新语法来做。

```Rust
//普通方式
fn main() {
    let user2 = User {
        active: user1.active,
        username: user1.username,
        email: String::from("another@example.com"),
        sign_in_count: user1.sign_in_count,
    };
}

//结构体更新语法
fn main() {
    let user2 = User {
        email: String::from("another@example.com"),
        ..user1
    };
}
```

## Using Tuple Structs Without Named Fields to Create Different Types

> Rust也支持看起来像元组的结构体，叫做元组结构体。元组结构体有结构体名称提供的额外意义，但是它相关联的字段没有名字。而且，他们仅有字段类型。当你想要给整个元组一个名字来使这个元组与其他元组不同时，元组结构体是有用的。当像在于给常规的结构体中命名每一个字段时，将会时多余的。
>
>  
>
> 定义一个元组结构体，以==`struct`==关键字开始，后边跟着结构体名称伴随着在元组中的类型。

```Rust
struct Color(i32, i32, i32);
struct Point(i32, i32, i32);

fn main() {
    let back = Color(0, 0, 0);
    let origin = Point(0, 0, 0);
}
```

> 你定义的每一个结构体都是自己的类型，尽管在结构体中的字段可能有同样的类型。
>
> 元组结构体实例和元组相似，你可以解构他们到独立的块，并且你可以用`.`加索引来访问单个值。

## Unit-Like Structs Without Any Fields

> Rust中可以定义没有任何字段的结构体，叫做==*Unit-Like*==结构体，因为表现像`()`。当需要实现一个基于一些类型的特性，但是没有任何数据想要保存在类型里面时，Unit-Like结构体是非常有用的。

```Rust
struct AlwaysEqual;
fn main() {
    let subject = AlwaysEqual;
}
```

