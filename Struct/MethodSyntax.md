> 方法(methods)和函数很想，用==`fn`==关键字和名字来定义方法，有参数和返回值，当在其他地方调用它时会运行内部包含的代码。不像函数的点是，方法被定义在一个结构体（或者枚举、特质对象）的上下文中，并且他们的第一个参数总是自己（self），代表了结构体实例的方法被调用了。

## Defining Methods

```Rust
#[derive(Debug)]
struct Rectangle {
    width: u32,
    height: u32,
}

impl Rectangle {
    fn area(&self) -> u32 {
        self.width * self.height
    }
}

fn main() {
    let rect1 = Rectangle {
        width: 30,
        height: 50,
    };
    
    println!("The area of the rectangle is {} square pixels.", rect1.area());
}
```

> 方法语法是在一个实例后边，添加一个点(.)加上方法名，小括号和其他的任何的参数。

## Methods with More Parameters

```rust
#[derive(Debug)]
struct Rectangle {
    width: u32,
    height: u32,
}

impl Rectangle {
    fn area(&self) -> u32 {
        self.width * self.height
    }
    
    fn can_hold(&self, other: &Rectangle) -> bool {
        self.width > other.width && self.height > other.height
    }
}

fn main() {
    let rect1 = Rectangle {
        width: 30,
        height: 50,
    };
    
    let rect2 = Rectangle {
        width: 10,
        height: 40,
    };
    
    let rect3 = Rectangle {
        width: 60,
        height: 45,
    };
    
    println!("Can rect1 hold rect2? {}", rect1.can_hold(&rect2));
    println!("Can rect1 hold rect3? {}", rect1.can_hold(&rect3));
    println!("The area of the rectangle is {} square pixels.", rect1.area());
}
```

## Associated Functions

> 所有定义在一个`impl`块中的函数被叫做关联函数，因为它们跟`impl`后面的类型名相关联。可以定义不带`self`作为第一个参数的关联函数（这个不是方法），因为不需要一个类型实例来运行。
>
> 关联函数不是方法，被经常用于将会返回一个新的结构体实例的构造函数。

```rust
impl Rectangle {
    fn square(size: u32) -> Slef {
        Self {
            width: size,
            height: size,
        }
    }
}

//调用
let sq = Rectangle::square(3);
```

## Multiple impl Blocks

> 结构体允许有多个`impl`块。

```rust
impl Rectangle {
    fn area(&self) -> u32 {
        self.width * self.height
    }
}

impl Rectangle {
    fn can_hold(&self, other: &Rectangle) -> bool {
        self.width > other.width && self.height > other.height
    }
}
```

