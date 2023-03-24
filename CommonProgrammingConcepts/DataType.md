在Rust中每一个值都有一个确定的数据类型，这告诉Rust数据将被指定为哪种类型以便于Rust知道改怎么处理这个数据。



## Scalar Types

一个标量类型代表了单一的值。Rust有四个主要的标量类型：整型（`integers`），浮点型（`floating-point numbers`），布尔类型（`booleans`），字符型（`characters`)。

- **Integer Types**

  整型是一个不带小数部分的数字。

  | 长度    | 有符号 | 无符号 |
  | ------- | ------ | ------ |
  | 8-bit   | i8     | u8     |
  | 16-bit  | i16    | u16    |
  | 32-bit  | i32    | u32    |
  | 64-bit  | i64    | u64    |
  | 128-bit | i128   | u128   |
  | arch    | isize  | usize  |

  有符号类型存储的数字范围：-2^n-1^ ---- (2 ^n-1^) - 1，n是bit位数

  无符号类型存储的数字范围：0 ---- 2^n^ - 1，n是bit位数

  ==`isize`==和==`usize`==类型取决于电脑的架构

  | 整型常量      | 例子        |
  | ------------- | ----------- |
  | Decimal       | 98_222      |
  | Hex           | 0xff        |
  | Octal         | 0o77        |
  | Binary        | 0b1111_0000 |
  | Byte(u8 only) | b'A'        |

  > To explicitly handle the possibility of overflow, you can use these families of methods provided by the standard library for primitive numeric types:
  >
  > - Wrap in all modes with the `wrapping_*` methods, such as `wrapping_add`.
  > - Return the `None` value if there is overflow with the `checked_*` methods.
  > - Return the value and a boolean indicating whether there was overflow with the `overflowing_*` methods.
  > - Saturate at the value’s minimum or maximum values with the `saturating_*` methods.

  

- **Floating-point Numbers**

  Rust的浮点类型是==`f32`==和==`f64`==，分别是32位和64位大小。默认是==`f64`==。

  ```Rust
  let f = 88.2344;
  
  let f: f32 = 56.89;
  
  let d: f64 = 999.3232;
  ```

  

- **Number Operations**

  ```Rust
  //addition
  let sum = 5 + 10;
  
  //subtraction
  let difference = 95.5 - 4.3;
  
  //multiplication
  let product = 4 * 30;
  
  //division
  let quotient = 56.7 / 32.2;
  let truncated = -5 / 3; //Results in -1
  
  //remainder
  let remainder = 43 %5;
  ```

  

- **Boolean**

  ```Rust
  let t = true;
  
  let f: bool = false;
  ```

  

- **Characters**

  char类型用单引号，字符串类型用双引号。Rust的==`char`==类型占用4个字节，保存Unicode标量值，可以存比ACSII码多的字符。包括重音符号，中文，日文，韩文，emoji，零长度的空格。

  ```Rust
  let c = 'z';
  
  let z: char = 'Z';
  
  let heart_eyed_cat = '😻';
  ```

## Compound Types

复合类型可以组合多个值到一个类型。Rust有两种原有复合类型：==`tuples`== 和 ==`arrays`==;

- **Tuple Type**

  元组是把若干各种类型的值组合到一个复合类型中的常用方式。它有固定的长度：一旦声明，不能增加或减少。

  ```Rust
  let tup: (i32, f64, u8) = (500, 6.4, 1);
  ```

  为了取出一个元组的中单个的值，我们可以用模式匹配来拆解它的值。

  ```Rust
  let (x, y, z) = tup;
  ```

  也可以通过用一个句点（`.`）跟着想要访问的值得索引来直接访问元组的元素。

  ```Rust
  let five_hundred = tup.0;
  
  let six_point_four = tup.1;
  
  let one = tup.2;
  ```

  没有任何值的元组有一个特殊的名字==`Unit`==。值和对应类型都写作==`()`==，代表空的值或空的类型。如果不返回任何值，表达式隐式的返回了一个Unit。

- **Array Type**

  集合多个值的另一种方式是用数组。与元组不同，数组的每一个元素类型必须一致。Rust的数组有一个固定的长度。

  ```Rust
  let a = [1, 2, 3, 4, 5];
  
  let a: [i32; 5] = [1, 2, 3, 4, 5];   //[i32 类型；5 元素数量]
  
  let a = [3; 5];  //等同于 let a = [3, 3, 3, 3, 3];
  
  
  ```

  可以用索引访问数组元素。

  ```Rust
  let first = a[0];
  
  let second = a[1];
  ```

  
