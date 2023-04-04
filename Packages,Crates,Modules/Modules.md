## Modules Cheat Sheet

> - 从单元包的根开始：当编译单元包时，编译器首先在单元包根文件中寻找代码来编译。
> - 声明模块：在单元包的根文件中，你可以声明新的模块；比如说，你声明了一个“garden”模块==`mod garden;`==，编译器将在这些地方寻找模块代码：
>   * 行内，代替了跟随在`mod garden`后边分号的花括号内；
>   * 在*src/garden.rs*文件内；
>   * 在*src/garden/mod.rs*文件内；
> - 声明子模块：在除单元包根文件外的任何文件里，你可以声明子模块。例如，你可能声明==`mod vegetables`==在*src/garden.rs*中。编译器将在被指定作父模块的文件目录中的这些位置寻找子模块的代码：
>   * 行内，直接跟随在`mod vegetabels`后边，花括号里面代替分号；
>   * 在*src/garden/vegetables.rs*文件中；
>   * 在*src/garden/vegetables/mod.rs*文件中
> - 模块中代码路径：一旦模块成为单元包的一部分，只要隐私规则允许，你可以在同单元包中任何其他地方引用这个模块中的代码，用路径访问代码。例如，一个在garden vegetables模块中==`Asparagus`==类型，将会被发现通过==`crate::garden::vegetables::Asparagus`==。
> - 私有与公有：在模块中的代码是私有的，从父模块中默认继承来的。使一个模块公有，声明模块用==`pub mod`==代替==`mod`==。使在一个公有模块中的元素公有也是一样，用==`use`==关键字在元素的声明前面。
> - ==`use`==关键字：在一个作用域内，==`use`==关键字为元素创建快捷方式来减少长路径的重复。在任何作用域内都可以引用==`crate::garden::vegetables::Asparagus`==，你可以在作用域内用==`use crate::garden::vegetables::Asparagus;`==创建一个快捷方式，然后你只需要写==`Asparagus`==来使用这个类型。

## Grouping Related Code in Modules

> 模块允许我们控制元素的隐私性，因为在一个模块内的代码默认是私有的。私有元素的内部实现细节不能被外部使用。我们可以选择使模块或者内部元素公有来暴露它们允许外部代码使用和依赖。