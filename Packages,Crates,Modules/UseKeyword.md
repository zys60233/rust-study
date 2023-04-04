## Bringing Paths into Scope with the use Keyword

> 不得不写出全部路径来调用函数是不方便的和重复乏味的。
>
> 一旦我们用==`use`==关键字为路径创建了快捷方式，那么在作用域内任何地方都可以使用这个更短的名字。

```rust
mod front_of_house {
    pub mod hosting {
        pub fn add_to_waitlist() {}
    }
}

use crate::front_of_house::hosting;

pub fn eat_at_restaurant() {
    hosting::add_to_waitlist();
}
```

> `use`关键字仅仅在`use`引入的特定作用域内创建快捷方式。

## Creating Idiomatic use Paths

> 使用==`use`==将函数引入到作用域内，通常引入函数的父模块到作用域，所以我们在调用函数时需要指定父模块名。
>
> 使用==`use==将结构体、枚举和其他元素引入到作用域内，通常引入全路径。

```rust
use std::collections::HashMap;

fn main() {
    let mut map = HashMap::new();
    map.insert(1, 2);
}
```

> 在这种习惯背后没有特别的理由，仅仅是因为习惯已经形成了，各位开发者已经习惯于用这种方式读和写Rust代码。
>
> 这个习惯的一个例外是我们用==`use`==语句将两个有相同名称的元素引入到作用域内，这是Rust不允许的。

```rust
use std::fmt;
use std::io;

fn function1() -> fmt::Result {
    
}

fn function2() -> io::Result<()> {
    
}
```

> 使用父模块名来区分两个类型。

## Providing New Names with the as Keyword

> 同一个作用域内引入两个名字相同的的类型的问题的另一个解决方案是：在路径后边，我们用==`as`==关键字来为类型指定一个新的本地名或者叫做别名。

```rust
use std::fmt::Result;
use std::io::Result as IoResult;

fn function1() -> Result {
    
}

fn function2() -> IoResult<()> {
    
}
```

## Re-exporting Names with pub use

> 当我们用`use`关键字把一个名称引入到作用域内时，在新的作用域内可用的名称是私有的。为了使调用我们功能的代码使用这个名称就像它被定义在代码中一样，我们可以联合`pub`和`use`。这个方法被称为*re-exporting*，因为我们将会将一个元素引入到作用域，但是也将这个元素提供给其他引入到作用域的代码用。

```rust
mod front_of_house {
    pub mod hosting {
        pub fn add_to_waitlist() {}
    }
}

pub use crate::front_of_house::hosting;

pub fn eat_at_restaurant() {
    hosting::add_to_waitlist();
}
```

## Using External Packages

> 在Cargo.toml文件中添加依赖，Cargo将会下载对应的包和其他依赖的包来确保这个包在我们的项目中可用。
>
> 然后在单元包中通过`use`关键字引入到我们的项目中。

## Using Nested Paths to Clean Up Large use Lists

> 如果我们用了定义在同一个单元包内或者模块内的多个元素，可以使用嵌套路径在一行内将这些元素引入到作用域。

```rust
//不嵌套
use std::cmp::Ordering;
use std::io;

//嵌套
use std::{cmp::Ordering, io};
```

```rust
//不嵌套
use std::io;
use std::io::Write;

//嵌套
use std::io::{self, Write}
```

## The Glob Operator

> 如果我们想将定义在一个路径内的全部公共元素引入到作用域，可以指定后边带`*`通配符的路径。

```rust
use std::collections::*;
```

> 使用通配符时要小心，通配符使辨别哪些名称引入的作用域和一个名字在程序中哪里定义了变得更加难。