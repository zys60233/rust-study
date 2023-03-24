## Functions

Rust代码常用用*snake case*风格来命名函数和变量名，所有字符小写并且以下划线分割单词。

我们在Rust中定义一个函数，通过输入`fn`关键字，加上函数名和一组小括号。大括号会高数编译器函数体的开始和结束位置。

```Rust
fn hello_world (x: i32, y: i32) {
    //函数体
    println!("{x}");
    println!("{y}");
}
```

通过输入函数名带一组小括号来调用定义的函数。

```Rust
fn main() {
	hello_world(1, 2);
}
```

你可以在作用域内的任何地方定义函数，只要是函数调用者能够发现就可以。



## Parameters

必须声明每个参数的数据类型。要求在函数定义中声明类型，这是一个审慎的决定，这意味着编译器几乎不需要你在代码的任何地方使用他们时需要指出他是什么数据类型。

多个参数之间用逗号分割。

```Rust
fn main() {
    print_labeled_measurement(5, 'h');
}

fn print_labeled_measurement(value: i32, unit_label: char) {
    println!("The measurement is: {value}{unit_label}");
}
```



## Statements and Expressions

**Statements**是完成一些操作和不返回值的指令。

```Rust
let y = 6;
```

**Expressions**是计算一个结果值。其不包含结尾的分号，如果给一个表达式添加结尾分号，就变成了语句，并且不会返回值。

```Rust
let y = {
    let x = 3;
    x + 1
};
```



## Functions with Return Values

函数给调用他们的代码返回值。我们不命名返回值，但是必须声明他们的类型在箭头符号后面（`->`）。在Rust中，函数的返回值是等同于函数体代码块最后的表达式的值。也可以在函数体中通过使用`return`关键字来更早的返回值，但是大多函数隐式的返回最后表达式的值。

```Rust
fn five() -> i32 {
    5
}

fn main() {
    let x = five();
    
    println!("The value of x is: {x}");
}
```

