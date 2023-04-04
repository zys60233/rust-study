## Paths for Referring to an Item in the Module Tree
> 路径的两种形式：
>
> - 绝对路径是一个全路径，从单元包根目录开始；对于来自外部单元包的代码，绝对路径以单元包名开始，但是对于当前单元包的代码，路径是以==`crate`==常量开始。
> - 相对路径以当前模块开始，并且使用==`self`==、==`super`==或者模块里面的标识符。
>
> 无论是绝对路径还是相对路径，后边都有一个或多个由双冒号（==`::`==）分割的标识符。

```rust
mod front_of_house {
    mod hosting {
        fn add_to_waitlist() {}
    }
}

pub fn eat_at_restaurant() {
    //绝对路径
    crate::front_of_house::hosting::add_to_waitlist();
    
    //相对路径
    front_of_house::hosting::add_to_waitlist();
}
```

> 在父模块中的元素不能使用在子模块中私有的元素，但是在子模块中的元素可以使用在“祖宗”模块中的私有元素。

## Exposing Paths with the pub Keyword

> 使模块公有不会让内部的内容公有。在模块前面的==`pub`==关键字仅仅使“祖宗”模块中代码可以引用该模块，但是没有权限访问该模块内部的代码。因为模块是容器，仅仅使模块公有我们没有什么可做的；我们需要继续选择使模块中的一个或多个元素公有了。

## Starting Relative Paths with super

> 我们可以构造以父模块名称开始的相对路径，而不是当前模块或者单元包根目录，通过用==`super`==作为路径的开始。
>
> 使用==`super`==允许我们来引用一个在父模块中一致的元素，这样可以使我们更容易地重新安排模块树，当模块与父模块紧密关联时，但是某天父模块可能移动到模块树中的任何其他地方。

## Making Structs and Enums Public

> 我们可以用==`pub`==来指明结构体和枚举公有，但是关于结构体和枚举的==`pub==用法没有更多的详细信息。
>
> 如果我们在结构体定义前面使用`pub`，我们使结构体公有，但是结构体内字段仍然是私有的。可以逐个地确定每一个字段是否公有。

```rust
mod back_of_house {
    pub struct Breakfast {
        pub toast: String,
        seasonal_fruit: String,
    }
    
    impl Breakfast {
        pub fn summer(toast: &str) -> Breakfast {
            Breakfast {
                toast: String::from(toast),
                seasonal_fruit: String::from("peaches"),
            }
        }
    }
}

pub fn eat_at_restaurant() {
    let mut meal = back_of_house::Breakfast::summer("Rye");
    
    meal.toast = String::from("Wheat");
    println!("I'd like {} toast please", meal.toast);
}
```

>相反，如果我们使一个枚举类型公有，那么它所有的变量都会公有。我们只需要在==`enum`==关键字前加上==`pub==。

```rust
mod back_of_house {
    pub enum Appetizer {
        Soup,
        Salad,
    }
}

pub fn eat_at_restaurant() {
    let order1 = back_of_house::Appetizer::Soup;
    let order2 = back_of_house::Appetizer::Salad;
}
```

> 枚举类型没什么用除非他的变量是公有的；必须逐个声明枚举的所有变量都是公有的是很令人烦恼的，所以枚举类型的所有变量默认是公有的。没有字段是公有的结构体通常是实用的，所以结构体字段默认遵循所有私有的规则，除非声明它是公有的。
