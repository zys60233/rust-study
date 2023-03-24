## Variables

默认变量的值是不可变的，以一种方式编写代码是Rust提供给助力之一，这样带来了安全优势；Rust也能容易的处理并发请求。

```Rust
//不可变变量声明
let x = 5;

//可变变量声明
let mut x = 5;
```

## Constants

常量不允许使用**mut**修饰，默认是不可变的。常量值的类型必须标明。

```Rust
//常量声明
const CHAR_A: char = A;

//常量表达式声明
const THREE_HOURS_IN_SECONDS: u32 = 60 * 60 * 3;
```

## Shadowing

通过对同一个变量名进行声明，第二次声明可以覆盖掉第一次声明。覆盖和可变变量不同点在于，覆盖可以改变变量类型，可变变量只能改变值，不能改变类型。

```Rust
//变量声明覆盖
let x = 5;

let x = 5 + 1;
```

