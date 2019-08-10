### Dart简介

当前 Dart 稳定版本为： 2.4.0

------

一切且对象:  Darts所有能够使用变量引用的都是*对象*， 每个对象都是一个*类*的实例。在 Dart 中 甚至连 数字、方法和 `null` 都是对象。所有的对象都继承于 `Object` 类。

Dart中所有对象默认都是 `null`

------

#### 变量

Dart中可以使用`var`来声明变量，也可以直接指定类型来声明变量，未声明类型的变量在首次赋值时由Dart推断并确定变量的类型，类型确定后不可变更

> var age = '18'；
>
> age = 25;（错误，age首次赋值为String类型，因此age被确认为String）
>
> age = '25'; （正确）

`const`、`final`：两者声明的都是常量，已经赋值将不能改变。 `const`声明一个编译时常量，`final`只能赋值一次。

> final name = 'Bob';
>
> const number = 1000;

------

#### Dart中支持以下数据类型:

- Number (数值型)
- String 字符串)
- Boolean 布尔型)
- List 数组)
- Map 键值对)
- Runes ([String]的符文(整数Unicode代码点))
- Symbols

------

#### 数值型 num

Dart数值型分整数型`int`和浮点型`double`, 可以中 `num`、`int`、`double`声明, 默认值都是 `null`.

`num`声明的变量可以在`int`和`double`间相互转换，反正不可以。

> num a = 1;
>
> a = 1.1;
>
> int b = 1;
>
> b = 1.1;  (错误)

**数值型操作**

1、运算符：`+`、`-` 、`*`、`/`、`~/`（短除法，取结果的整数）、`%`（取余）

2、常用属性

> isNaN : num的属性,判断一个对象是否为非数字,是数字则返回false,否则返回true.
>
> isEven : int 的属性,判断一个数字是否为偶数
>
> isOdd : int 的属性,判断一个数字是否为奇数
>
> sign : 返回该整数的符号(对于0返回0，对于小于0的值返回 -1，对于大于0的值返回 1）

3、常用方法

> abs() : 返回该整数的绝对值 
>
> round() : 返回四舍五入的近似值
>
> floorl() : 向下取整
>
> ceil() : 向上取整
>
> toInt() : 转成int类型 (舍去小数)
>
> toDouble() : 转成double型

------

#### 字符串 String

**字符串声明**

> 1、使用单/双引号创建
>
> ​	String a = '字符串'
>
> 2、使用三个单/双引号创建多行字符串
>
> ​	String b = '''这是一个多行
>
> ​	的字符串''';
>
> 3、使用 r 创建原始字符串
>
> ​	String c = r'创建\n原始字符串'；
>
> ​	print(c); // 输出的是字符串：创建\n原始字符串（\n不会被转义成换行符）

**字符串操作**

1、运算符:  + 、 *、 == 、 []

> `+` : 字符串相加，print('a' + 'b');   //输出 ab
>
> `*` : 字符串成一个int数值， print('ab' * 2); // 输出 abab 
>
> `==` : 判断两个字符串是否相等

2、插值表达式：${expression}

> String a = '男生'；
>
> print('他是个$a');  // 输出：他是个男生

3、常用方法

> 1、`compareTo()` : 比较两个字符串的大小，返回一个int值(1、0、-1).  
>
> print('c'.compareTo('a'));  // 1（在ascii码中 c > a）
>
> 2、`startsWith()` : 判断字符串使用已某字符串开头，返回bool
>
> 3、`endsWith()` : 判断字符串使用已某字符串结尾，返回bool
>
> 4、`indexOf()` : 顺序查找符合的字符串，并返回索引
>
> String a = 'abcdabcd';
>
> print(a.indexOf('b')); // 1  从开头顺序查找第一个为b的字符并返回它的索引
>
> print(a.indexOf('a'), 2); // 4  从index=2的位置顺序查找第一个为a的字符并返回它的索引
>
> 5、`lastIndexOf()` :  倒序查找第一个匹配的字符串，并返回索引, 找不到返回-1
>
> 6、`substring()` :  按指定位置切割字符串，可以指定开始位置和结束位置（不指定结尾位置时截取到最后）
>
> print(a.substring(0, 2));  //ab 
>
> print(a.substring(3)); // dabcd 从指定index至末尾
>
> 7、`trim()` ： 去除字符串左右两边的空格(中间的空格不会被删除)，并返回字符串
>
> 8、`trimLeft()` ： 去除字符串右边的空格
>
> 9、`trimRight()` ： 去除字符串左边的空格
>
> 10、`padLeft()` : 长度补齐  从左边补齐长度 默认以空格补齐（也可以以指定的字符进行补齐）
>
> 11、`padRight()` : 长度补齐  从右边补齐长度 默认以空格补齐
>
> 12、`contains()` :  判断是否包含某字符串，可以指定index=N开始判断
>
> print('abcdef'.contains("ab", 3)); //false  从index=3开始判断
>
> 13、`toLowerCase()` :  全部转换写
>
> 14、`toUpperCase()` ：全部转大写
>
> 15、字符串替换：`replaceAll()`、 `replaceFirst()`、replaceRange()、`replaceAllMapped()`、`replaceFirstMapped()`

------

#### 布尔值

