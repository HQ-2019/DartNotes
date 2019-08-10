### Dart简介

当前 Dart 稳定版本为： 2.4.0

------

一切且对象:  Darts所有能够使用变量引用的都是*对象*， 每个对象都是一个*类*的实例。在 Dart 中 甚至连 数字、方法和 `null` 都是对象。所有的对象都继承于 `Object` 类。

Dart中所有对象默认都是 `null`

------

#### 变量

Dart中可以使用`var`来声明变量，也可以直接指定类型来声明变量，未声明类型的变量在首次赋值时由Dart推断并确定变量的类型，类型确定后不可变更。如果可以建议在声明时明确变量的类型。

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

#### Dart中的内置类型:

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

**1、运算符**：`+`、`-` 、`*`、`/`、`~/`（短除法，取结果的整数）、`%`（取余）

**2、常用属性**

> isNaN : num的属性,判断一个对象是否为非数字,是数字则返回false,否则返回true.
>
> isEven : int 的属性,判断一个数字是否为偶数
>
> isOdd : int 的属性,判断一个数字是否为奇数
>
> sign : 返回该整数的符号(对于0返回0，对于小于0的值返回 -1，对于大于0的值返回 1）

**3、常用方法**

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

> **1、使用单/双引号创建**
>
> ​	String a = '字符串'
>
> **2、使用三个单/双引号创建多行字符串**
>
> ​	String b = '''这是一个多行
>
> ​	的字符串''';
>
> **3、使用 r 创建原始字符串**
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

> 3.1、`compareTo()` : 比较两个字符串的大小，返回一个int值(1、0、-1).  
>
> ​	print('c'.compareTo('a'));  // 1（在ascii码中 c > a）
>
> 3.2、`startsWith()` : 判断字符串使用已某字符串开头，返回bool
>
> 3.3、`endsWith()` : 判断字符串使用已某字符串结尾，返回bool
>
> 4.4、`indexOf()` : 顺序查找符合的字符串，并返回索引
>
> ​	String a = 'abcdabcd';
>
> ​	print(a.indexOf('b')); // 1  从开头顺序查找第一个为b的字符并返回它的索引
>
> ​	print(a.indexOf('a'), 2); // 4  从index=2的位置顺序查找第一个为a的字符并返回它的索引
>
> 4.5、`lastIndexOf()` :  倒序查找第一个匹配的字符串，并返回索引, 找不到返回-1
>
> 4.6、`substring()` :  按指定位置切割字符串，可以指定开始位置和结束位置（不指定结尾位置时截取到最后）
>
> ​	print(a.substring(0, 2));  //ab 
>
> ​	print(a.substring(3)); // dabcd 从指定index至末尾
>
> 4.7、`trim()` ： 去除字符串左右两边的空格(中间的空格不会被删除)，并返回字符串
>
> 4.8、`trimLeft()` ： 去除字符串右边的空格
>
> 4.9、`trimRight()` ： 去除字符串左边的空格
>
> 4.10、`padLeft()` : 长度补齐  从左边补齐长度 默认以空格补齐（也可以以指定的字符进行补齐）
>
> 4.11、`padRight()` : 长度补齐  从右边补齐长度 默认以空格补齐
>
> 4.12、`contains()` :  判断是否包含某字符串，可以指定index=N开始判断
>
> ​	print('abcdef'.contains("ab", 3)); //false  从index=3开始判断
>
> 4.13、`toLowerCase()` :  全部转换写
>
> 4.14、`toUpperCase()` ：全部转大写
>
> 4.15、字符串替换
>
> ​	`replaceAll()`、 `replaceFirst()`、replaceRange()、`replaceAllMapped()`、`replaceFirstMapped()`
>
> 4.16、`split()` : 以指定分隔符拆分字符串并返回一个字符串列表
>
> ​	var vb = 'a.b.c.d'.split('.');
>
> ​	print('拆分字符串：$vb');	// 输出    拆分字符串：[a, b, c, d]
>
> ​		

------

#### 布尔值 bool

布尔值是编译时常量，

使用bool表示布尔类型，

布尔值只有true和false。(当然Dart对象默认值都是null)

------

#### 字典 Map

Map是以key-value(键值对)形式存储数据的无序集合，key和value支持任意类型，在一个map中key唯一。

**1、Map的初始化**

> **1.1 通过字面量创建不可变字典** `const {}`
>
> ​	Map person = const {'name': 'Tom', 'age': 18}; 
>
> ​	person['sex'] = 'boy';    //  报错 Cannot set value in unmodifiable Map
>
> **1.2 通过字面量创建可变字典** `{}`
>
> ​	Map person = {'name': 'Tom', 'age': 18}; 
>
> ​	person['sex'] = 'boy';  
>
> ​	print('可变字典  $person');    // 输出  可变字典  {name: Tom, age: 18, sex: boy}
>
> **1.3 通过构造函数声明，在赋值** `new Map()`
>
> ​	Map person = new Map();
>
> ​	person['name'] = 'tom'; 
>
> ​	也可以通过其他map来创建一个新的map  如：Map person1 = new Map.from(person);

**2、map的修改**

> **2.1 赋值** 通过"变量名[key] = value"进行赋值
>
> ​	person['name'] = 'tom'; 
>
> **2.2 删除某个key**   `remove()`
>
> ​	person.remove('name'); 	// 把person字典中key为name的键值对删除
>
> **2.3 清空map**  `clear()`
>
> ​	person.clear();	// 清空整个map集合

------

#### 数组 List

list表示一个有序集合，与数组其实是同一个概念。list可以储存任意类型的数据，数组内的元素可以重复。

**1、list初始化**

> **1.1 可变数组**
>
> ​	List list = ['s', 2, null, person];
>
> ​	List list1 = new List();
>
> ​	list1[0] = 2; // 给数组中第1位元素赋值
>
> **1.2 不可变数组**
>
> ​	List list = const ['s', 2, null, person];

**2、常用函数**

> **2.1 获取长度**
>
> ​	list.lenght
>
> **2.2修改元素**
>
> ​	list[1] = 'xxxxx';	// 替换指定位置的元素
>
> ​	list.replaceRange(1, 3, [5,6,7,8]); //替换范围内的元素  含头不含尾
>
> ​	list.fillRange(1, 4, 'ABC'); // 用相同的值替换指定索引范围内的值
>
> **2.3 添加元素**
>
> ​	list.add('someValue');	// 向数组末尾添加新元素
>
> ​	list.addAll(otherList);	// 合并数组
>
> ​	list.insert(1, 'someValue'); // 向数组的第2个位置插入新元素，原来索引为1的元素及1后面的元素的所有位向后移动一位 （注意数组越界问题）
>
> **2.4 移除元素**
>
> ​	list.remove('s');	// 移除数组中匹配的元素
>
> ​	list.removeAt(1);	// 移除数组中指定位置的元素
>
> ​	list.removeLast();	// 移除数组中最后一个元素
>
> ​	list.removeRange(0, 2); //移除数组中指定范围内的元素
>
> ​	list.removeWhere((item) => item.length == 3); // 移除数组中符合条件的元素
>
> ​	list.clear();	// 移除所有元素
>
> **2.5 排序** 
>
> ​	list.shuffle();	// 数组中元素重新随机排序
>
> ​	list.sort((a, b) => a.length.compareTo(b.length));	// 数组内根据条件排序
>
> **2.6 判断包含**
>
> ​	list.contains('abc'); //判断数组中是否包含指定元素
>
> **2.7 查找**
>
> ​	list[0];	// 查找指定位置的元素值
>
> ​	list.indexOf('abc', 1); // 从指定的位置开始`顺序`查找第一个符合指定元素的索引 
>
> ​	list.lastIndexOf('abc', 4); // 从指定的位置开始`倒序`查找第一个符合指定元素的索引
>
> ​	list.firstWhere((element)=>(bool));  // 返回第一个满足条件的元素
>
> ​	list.indexWhere((e)=>(bool);  // 返回第一个满足条件的元素的索引
>
> ​	list.lastWhere((element)=>(bool));  // 从后往前找，返回第一个满足条件的元素
>
> ​	list.lastIndexWhere((e)=>(bool);  // 从后向前找 返回第一个满足条件的元素的索引
>
> **2.8 截取**
>
> ​	List list = [0, 1, 2, 3, 4, 5];
>
> ​	list.sublist(1, 3); // 从指定的开始位置和结束位置截取数组 [1, 2]
>
> **2.9 遍历**
>
> ​	list.forEach( (element) {
>
> ​		// do smoething
>
> ​		// 不能对list进行add或remove操作，但是可以修改元素值
>
> ​	});
>
> ​	for( var lalue in list ){
>
> ​		print(lalue);
>
> ​	}