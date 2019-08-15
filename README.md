### Dart简介

当前 Dart 稳定版本为： 2.4.0

------

一切且对象:  Darts所有能够使用变量引用的都是*对象*， 每个对象都是一个*类*的实例。在 Dart 中 甚至连 数字、方法和 `null` 都是对象。所有的对象都继承于 `Object` 类。

Dart中所有对象默认都是 `null`

Dart没有声明公开、私有和保护的关键字，使用`_`来标识类或变量为私有的。

------

### 变量

Dart中可以使用`var`来声明变量，也可以直接指定类型来声明变量。

未声明类型的变量在创建时赋值由Dart推断并确定变量的类型，类型确定后不可变更。

如果变量在创建时没有赋值，则变量的类型为dynamic类型

如果可以建议在声明时明确变量的类型。

> var age = '18'；// age被推导为String类型
>
> age = 25;（错误，age首次赋值为String类型，因此age被确认为String）
>
> age = '25'; （正确）
>
> var a;	// a变量类型为dynamic动态类型，可动态变更变量的类型
>
> a = 10;
>
> a = 'bbbbb';

`const`、`final`：两者声明的都是常量，已经赋值将不能改变。 `const`声明一个编译时常量，`final`只能赋值一次。

> final name = 'Bob';
>
> const number = 1000;

------

### Dart中的内置类型:

- Number (数值型)
- String 字符串)
- Boolean 布尔型)
- List 数组)
- Map 键值对)
- Runes ([String]的符文(整数Unicode代码点))
- dynamic
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
> ```
> list.forEach( (element) {
> 	// do smoething
> 	// 不能对list进行add或remove操作，但是可以修改元素值
> });	
> ```
>
> ```
> for( var lalue in list ){
> 	print(lalue);
> }
> ```

------

### 枚举

使用`enum`来定义枚举

枚举常用语控制语句，尤其在switch…case中.

枚举中不能指定原始值，枚举的值(index)由0开始，依次累加1

可以通过枚举的values获取所有的枚举元素

> ```
> var i = XXXX.x1;
> var list = XXXX.values;
>
> enum Person {
>   Boy,
>   Girl
> }
> ```

### 运算符

##### 算术运算符：

> 加减乘除：`+`、`-` 、`*`、`/`、`~/`（短除法，取结果的整数）、`%`（取余）
>
> 递增递减：`++var`、`var--`、`--var`、`var--`
>
> 针对数值类型运算

##### 关系运算符

> **针对内容判断**
>
> `==`、`!=`、`>`、`<`、`>=`、`<=`、`==`(判断内容是否相同，而非判断对象类型是否相同)
>
> **as  is   is! 判断对象类型**
>
> as : 类型转换
>
> is : 如果对象具有指定的类型，则为true
>
> is! : 如果对象具有指定的类型，则为fasle

##### 逻辑运算符

> `!`、`&&`、`||`   针对布尔类型运算

##### 条件运算符

> **三目运算符**   `condition ? expr1 : expr2` 
>
> int a  = 10;  int b = a > 10 ?  'A' : 'B';
>
> **??运算符** `expr1 ?? expr2` 表示如果expr1为空则使用expr2
>
> String a;  String b = 'Dart';  String c = a ?? b;    // c = 'Dart'

##### 赋值运算符

> **基础运算符**：`=`、`??=`
>
> `??=` 表示如果变量为空则进行赋值，如果变量不为空则不赋值
>
> int a;    a ??= 10;            // 此时 a = 10
>
> int a = 5;   a ??= 10; 	// 此时 a = 5;
>
> **复合运算符** ：先运算再赋值 `+=`、`-=`、`*=`、`/=`、`%=`、`~/=`

##### 级联操作符

> ```
> String s = (new StringBuffer()
> 	 ..write('a')
> 	..write('b')
> 	..write('c')
> ).toString();
> print(s);	// abc
> ```

### 控制语句 ######

##### if语句

> ```
> var a = 100;
> if (a < 50) {
> 	print('大')；
> } else if (a == 50) {
> 	print('中')；
> } else {
> 	print('小')；
> }
> ```

##### for语句

> ```
> var list = [0, 1, 2, 3, 4,];
> for(int index = 0; index < list.lenght; index++) {
> 	print(list[index]);
> }
>
> for(var i in list) {
> 	print(i);
> }
> ```

##### while语句

> while循环 (先判断条件，满足条件再执行循环)
>
> ```
> int i =10;
> while (i < 10) {
> 	print(i++);
> }
> ```
>
> do…while循环 (先执行一次，在判断条件，满足条件再执行循环)
>
> ```
> do {
> 	print(i—);
> } while (i > 0 && i <= 10);
> ```

##### switch…case语句

> 比较类型：num, String, 枚举, 对象, 编辑期常量
>
> 使用default关键字处理默认情况
>
> 每一个非空的case语句必须有一个break
>
> 可以使用continue跳转到另一个标签
>
> ```
> var animal = 'dog';
> switch(animal){
> 	case 'cat':
> 		print('this is cat');
> 		continue TestTag;	// 跳转到其他标签继续执行对应的case
> 		// break;
>     case 'dog':
>     	print('this is dog');
>     	break;
>     TestTag:	// 这就是定义的标签
>     case 'tiger':
>     	print('this is tiger');
>     	break;
>     default:
>     	print('this is other animal');
> }
> ```



------



### 异常捕获 

Dart的异常捕获可以抛出任意类型的对象。

> 1、抛出异常
>
> throw Exception('任意类型的异常');  
>
> 2、捕获异常
>
> ```
> try {
> 	// to do something
> } on CustomException catch (e) {
> 	// 捕获自定义类型异常
> } on Exception catch (e) {
> 	// 捕获特定类型异常
> } catch (e, s) {
> 	// 捕获所有类型异常
> } finally {
> 	// ...
> }
> ```

------

### 函数 #####

Dart是一门面向对象的语言，在Dart中函数是Function类型的对象，函数可以分配给变量，也可以当成参数传递给其他函数。

`=>`可以简化函数，适用于实现简单逻辑的函数

> ```
> // 定义一个有返回值的函数
> String run() {
>   return 'a string';
> }
> // 使用 => 声明以上函数
> String run() => 'a string';
> ```

##### 1、函数定义

函数定义有函数名称、函数入参、函数返回参数和函数执行体。

> ```
> int addition(int a, int b) {
>     return a + b;
> }
> int i = addition(100, 2);	// i=102
> ```

##### 2、可选参数

函数的参数可以声明为可选类型，即调用函数时可不传参数，在函数定义时使用{param1, param2, ...}指定命名参数。

> ```
> void userSettings({int age, String name}) {
>   // ....
> }
> userSettings();
> userSettings(age: 18);
> userSettings(name: 'tom');
> userSettings(age: 18, name: 'tom');
> // 以上方式调用函数都是正确的
> ```

##### 3、必传参数

如果函数的参数在调用时必须传入，那个在声明函数时可以使用@required修饰参数。

> ```
> void userSettings({@required int age, String name}) {
>   // ....
> }
> // 以上函数将age参数声明为了必须传入的参数，函数调用时不传入必须参数则会报错。
> ```

##### 4、可选的位置参数

在函数声明时，可以使用[]将参数标记为可选的位置参数

> ```
> void userSettings(int age, String name, [String sex]) {
>   print('性别：$sex');
> }
> userSettings(18, 'tom');
> userSettings(18, 'tom', '男');
> ```

##### 5、默认参数

默认参数基于可选参数，使用`=`为可选参数指定默认值

默认值只能是编译时常量

> ```
> void userSettings(String name, {int age = 18, String sex = '女'}) {
>     print('name: $name  age: $age  sex: $sex');
>   }
> userSettings('tom');
> userSettings('tom', sex: '男');
> ```

##### 6、函数作为变量

> ```
> Function say = (some) {
> 	print(some);
> };
> say('新年好！')
>
> 或者
> var say = say('新年好！');
> say();
>
> void sayHappyNewYear() {
>   print('新年好');
> }
> ```

##### 7、函数作为参数

> ```
> List list = [1, 2, 3, 4];
> print(listAdd(list, addNum));	// 输出 [3, 4, 5, 6]
>
> List listAdd(List list, int addNumber(number)) {
>   for(var index = 0; index < list.length; index++) {
>     list[index] = addNumber(list[index]);
>   }
>   return list;
> }
>
> int addNum(number) {
>   return number + 2;
> }
> ```

##### 8、匿名方法

格式  `（expr1, expr2, … ）{ … }`

> ```
> 匿名函数赋值给变量
> var say = (some) {
> 	print(some);
> };
> say('新年好！')
>
> 匿名函数当做参数
> // 使用匿名方法修改上面提到的listAdd的调用
> List newList = listAdd(list, (number){ return number + 2;});
> ```

##### 9、闭包

闭包也是一个函数，定义在其他函数内部，闭包能访问外部函数内定义的局部变量，并持有其状态。

> ```
> var func = closure();
> func();
> func();
>
> Function closure() {
>   int count = 0;
>   return () {
>     count++;
>     print(count);
>   };
> }
>
> // 多次调用func()函数，发现输出的值会依次累加，说明func函数变量持有了closure()函数内的局部变量的状态
> ```

------



### 面向对象编程  ####

#### 对象和类

使用`class`关键字来声明一个类，使用`new`关键字(也可以省略`new`)创建一个对象，Dart中一切都是对象，所有对象都继承与`Object`类

> ```
> // 创建一个对象
> Person person = new Person(); 或者 var person = Person();
>
> // 创建一个类
> class Person {
> }
> ```

##### 类的属性和方法

属性默认生产setter和getter方法，但是使用final声明的属性只有getter方法。

类的属性和方法都可以通过点语法`.`来访问，访问属性时实际也是访问它的setter和getter方法。

使用`_`声明属性、方法或者类为私有。

使用`import`导入类。

Dart中方法不可以被重载(方法参数支持可选参数)

> ```
> // 创建一个对象
> var person = Person();
> person.name = 'Tom';
> person.age = 18;
> person.run();
>
> person._wight = 180.0;	// 这里会报错，类外部不能访问私有属性
>
> // 创建一个类
> class Person {
> 	String name;
> 	int age;
> 	double _wight;	// _开头的属性都是私有属性
> 	void run() {
>       print('runner is $name, age: $age');
> 	}
> 	// 函数不支持重载(下面run函数声明是错误的)
> 	void run(String name) {}  
> }
> ```

##### 计算属性

Dart中属性有存储属性、计算属性。

计算属性的值通过计算而来本身并不存储值。

计算属性的赋值，实际上是通过计算将结果赋值给其他的实例变量。

> ```
> var wall = Wall();
> wall.width = 100;
> wall.height = 10;
> //  print(wall.area());
> print(wall.area);
> wall.area = 500;
>   
> class Wall {
>   num width, height;
> //  num area() {
> //    return width * height;
> //  }
>   num get area => width * height;	// 计算墙的面积
>       set area(num value) {
>         height = value / 100;		// 通过设置面积来给墙的高度赋值
>       }
> }
>
> // 函数主要表达对象的行为动作，而计算属性主要用来表达对象自身的属性
> ```

##### 类的构造方法

如果类没有自定义的构成方法，则类自己会有一个默认的构成方法。

如果有自定义的构造方法，默认方法会自动无效。

构造方法不能够重载。

可以使用命名构造方法（`类名.函数名(){}`），给类构造多个构造方法

> ```
> class Wall {
> 	num width, height;
> 	final Color color;
>
> 	// 默认的构造方法
> 	Wall() {
>   	}
>   	
>   	// 自定义构造方法
>   	Wall(num width, num height) {
>     	this.width = width;
>     	this.height = height;
>   	}
>   	// 自定义构造方法(这种构造方法可以用来解决类中有final属性，但是希望外部传值的情况)
>   	Wall(this.width, this.height, this.clolr){
>     	print('$width   $height');
>   	}
>   	
>   	// 命名构成方法(可实现多个构造方法)
>     Wall.withWidth(this.width) {
>     	print('$width');
> 	}
> 	Wall.withHeight(this.height) {
>     	print('$height');
> 	}
>   	
> }
> ```

##### 类的常量构造方法

如果类是不可变状态，可以把对象定义为编译时常量

使用`const`声明构造方法，且所有属性都是`final`声明

使用`const`声明对象，可省略

> ```
> const wall = Wall(20, 20);
> class Wall {
> 	final num width, height;
>   	const Wall(this.width, this.height, this.clolr);
> }
> ```

##### 工厂构造方法

工厂构造方法可以理解为设计模式中的工厂模式

工厂构造方法中可以返回对象

使用`factory`声明工厂构造方法

> ```
> var wall = Wall(20);
> print(wall.color);
>
> class Wall {
>   num width, height;
>   Color color;
>   // 工厂构造函数 通过宽度返回不同颜色墙对象
>   factory Wall(num width) {
>     if (width > 10) {
>       return Wall._init(width, Colors.yellow);
>     }
>     return Wall._init(width, Colors.red);
>   }
>
>   Wall._init(this.width, this.color){
>     print('$width   $height');
>   }
> }
> ```

##### 对象的call()方法

当类实现了call()方法时，该类的对象可以作为方法使用

> ```
> var wall = Wall();
> wall();	// 对象当成了方法使用
>
> class Wall {
>   num width, height;
>   // 也可以不传参数 void call() {}
>   void call(this.width, this.color){
>     print('$width   $height');
>   }
> }
> ```

##### 对象操作符 ###  ######

> 

##### 静态成员  ########

使用`static`关键字来修饰类级别的静态变量和静态函数，使用 `static const`修饰静态常量

静态成员不能访问非静态成员，非静态成员可以访问静态成员

直接使用类名访问静态函数和静态变量

> ```
> void main() {
>   // 类的静态成员和函数可以通过类名直接访问
>   print(AB.i);
>   print(AB.add(10, 20));
> }
> class AB {
>   static int i = 1; // 如果不是static声明，则该变量将不能在static声明的静态函数中访问
>   static int  add(int a, int b) {
>     return a + b + i;
>   }
> }
> ```

#### 继承 ######

使用`extends`让一个类继承另一类

子类可以继续父类的可见方法和属性，但不会继承父类的构造方法

子类可以复写父类的可见方法、setter和getter方法

Dart是单继承，通过继承实现多态性

> ```
> void main() {
>   var man = Man();
>   man.name = 'Tom';
>   man.say();
>
>   Person person = Man();
>   // 判断person是否是Man类的对象
>   if (person is Man) {
>     person.manSay();
>   }
> }
>
> class Man extends Person {
>   void manSay() {
>     print('$name man say');
>   } 
>
>   // 复写父类的函数
>   @override
>   void say() {
>     // TODO: implement say
>     super.say();
>   }
> }
>
> class Person {
>   String name;
>   int _age;
>
>   void say() {
>     print('$name say xxxx');
>   }
> }
> ```

#### 接口

Dart中类就是接口,好奇怪唉

纯接口类使用`abstract`关键字修饰, abstract

每个类都隐式的定义了一个包含所有实例成员的接口

如果需要使用类的方法名，但是希望能够自定义方法的实现，那么使用接口 `implements`

如果需要复用类已有功能，那么建议使用继续`extends`

> ```
> void main() {
>   var man = Man();
>   man.say();
> }
>
> // 使用 implements 声明对接口的
> class Man implements Person {
>   @override
>   void say() {
>     print('a man say');
>   }
> }
>
> // 接口使用 abstract 修饰
> abstract class Person {
>   void say();
> }
> ```

#### Mixins ######

使用Mixins实现类似多继承的功能

作为Mixin的类不能显示的声明构造函数，并且只能继续自Object

使用`with`连接一个或多个Mixin

> ```
> void main() {
>   var d = D();	// 创建一个D类的对象，但是可以调A/B/C中的函数
>   d.b();
> }
>
> // 使用Mixins实现多继承，如果多个Mixin类中都实现了同一个函数f()，那对象d在调用f()函数时，调用的是D类声明时写在最后一位的Mixin类
> // 比如 class D extends A with B, C {}   d.f()调的是C类的f()函数
> // 比如 class D extends A with C, B {}   d.f()调的是B类的f()函数
> class D extends A with B, C {
>   void d(){
>     print('调用的是 D.d() ');
>   }
> }
>
> class A {
>   void a(){
>     print('调用的是 A.a() ');
>   }
> }
>
> class B {
>   void b(){
>     print('调用的是 B.b() ');
>   }
> }
>
> class C {
>   void c(){
>     print('调用的是 C.c() ');
>   }
> }
> ```

### 泛型  #####

使用泛型可以有效的避免重复代码。

Dart中类型是可选的，可以使用泛型指定类型，更加安全和易读

> ```
> // 官网代码
> abstract class ObjectCache {
>   Object getByKey(String key);
>   void setByKey(String key, Object value);
> }
>  
> abstract class StringCache {
>   String getByKey(String key);
>   void setByKey(String key, String value);
> }
>
> //上面两个类，使用泛型可以精简为一个类
> abstract class Cache<T> {
>   T getByKey(String key);
>   void setByKey(String key, T value);
> }
>  
> main(List<String> args) {
>   // 指定String类型，只能添加String到list, 添加其他类型会报错
>   List<String> strList = List<String>();
>   strList.add("a");
>   strList.add(1); // 类型错误
> }
> ```

### 异步编程 ###### #######





