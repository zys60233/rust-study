## if Expressions

`if` 表达式允许你根据条件来分开你的代码。你提供一个条件并且规定 “如果条件符合，就执行这一块代码。如果条件不符合，就不执行这块代码。”

```Rust
fn main() {
    let number = 3;
    
    if number < 5 {
        println!("condition was true");
    } else {
        println!("condition was false");
    }
}
```

通过组合`if`和`else`成为`else if`表达式可以判断多个条件。

```Rust
fn main() {
    let number = 6;

    if number % 4 == 0 {
        println!("number is divisible by 4");
    } else if number % 3 == 0 {
        println!("number is divisible by 3");
    } else if number % 2 == 0 {
        println!("number is divisible by 2");
    } else {
        println!("number is not divisible by 4, 3, or 2");
    }
}
```

因为`if`是表达式，所以可以在`let`语句的右边使用它来给一个变量分配结果。`if`的每一个分支的返回值类型必须一致。

```Rust
fn main() {
    let condition = true;
    let number = if condition { 5 } else { 6 };

    println!("The value of number is: {number}");
}
```

## Repetition with Loops

Rust有三种类型的循环：==`loop`==，==`while`==，==`for`==。==`break`==关键字停止循环，==`continue`==关键字跳过本次循环。

`loop`关键字告诉Rust不停地执行一块代码一次又一次或者执行到你明确的告知它要停为止。

```Rust
fn main() {
    loop {
        println!("again!");
    }
}
```

为了得到循环的返回值，可以在用来停止循环的`break`表达式后边添加想要返回的值；这个值将会被从循环中返回，可以在其他地方使用。

```Rust
fn main() {
    let mut counter = 0;
    
    let result = loop {
        counter += 1;
        
        if counter == 10 {
            break counter * 2;
        }
    }
    
    println!("The result is {result}");
}
```

==当循环里面有循环时，`break`和`continue`这时对最里面的循环有效。你可以选择指定一个循环标签（loop label）给一个循环，这样就可以在`break`和`continue`加上指定的循环标签来停止对应的循环，而不是停止最内层的循环。循环标签必须以单引号开头。==

```Rust
fn main() {
    let mut count = 0;
    'counting_up: loop {
        println!("count = {count}");
        let mut remaining = 10;
        
        loop {
            println!("remaining = {remaining}");
            if remaining == 9 {
                break;
            }
            
            if count == 2 {
                break 'counting_up;
            }
            remaining -= 1;
        }
        
        count += 1;
    }
    
    println!("End count = {count}");
}
```

## Conditional Loops with while

```Rust
fn main() {
    let mut number = 3;
    
    while number != 0 {
        println1("{number}!");
        
        number -= 1;
    }
    
    println!("LIFTOFF!!!");
}
```

## Looping Through a Collection with for

```Rust
fn main() {
    let a = [10, 20, 30, 40, 50];
    
    for element in a {
        println!("the value is: {element}");
    }
}
```

指定执行次数

```Rust
fn main() {
    for number in (1..4).rev() {
        println!("{number}");
    }
    
    println!("LIFTOFF!!!");
}
```

