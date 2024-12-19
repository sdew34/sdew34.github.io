- 基础知识点
  collapsed:: true
	- Java源程序可以包含多个class类
	- package语句必须出现在源文件的非空白首行
	- 在源文件中声名的public接口名称必须和源文件名一致
	- 每个Unicode码占16个比特位
	- 常量完全大写
	- jdk
		- Java ee 企业版本
		- java me 移动版本
		- Java se标准版
	-
	- Java关键字
		- private 私有
		-
	- java数据类型
		- 简单数据类型
			- 整数
			- 浮点型
			- 布尔型
		- 数组没有赋值并非是空值
	- byte
	- % 取余
		- 比较字符是否相等
			- s1 == s2 比较的是字符的地址
			- s1.equals(s2) 对的
			- s1 .length() ==s2.length() 比较的是字符的长度
	- 实参与形参
		- 在调用方法时，想通过方法改变实参的值，形参必须是对象（数组，数组本质上也是对象）
		- 实参向形参的数据传递是单向值传递
		- 局部变量的作用域为定义语句开始到包含该定义语句的最内层语句块结束
		- 属性
			- 属性可以是简单变量，也可以是一个对象
			-
	- 类成员修饰符
		- static 静态的 与访问权限无关
		- public 公开的 在包外面可以访问
		- protected 受保护的 比private范围大 比public范围小
		- private 是只能在本类访问
		-
	- 封装
		-
	- 在所有运算中赋值优先级是最低的
- java程序基础
  collapsed:: true
	- Java程序基本结构
	  collapsed:: true
		- 返回值
			- void 表示没有返回值
		- 关键字
			- static 静态 Java入口程序规定的方法必须是静态方法，方法名称必须是main，括号内的参数必须是String数组
		- 方法内部，语句才是真正的执行代码
		- 注释
			- ```
			  // 单行注释
			  
			  /*多行注释1
			  多行
			  */
			  /**多行注释2
			  *每行以*开头
			  *
			  */
			  ```
	- 变量与数据类型
	  collapsed:: true
		- 变量必须先定义再使用
		- 基本数据类型
			- 整数类型
				- byte：1字节 -128~127
				- short：2字节 -32768~32767
				- int：4字节 -2147483648~21474483647
				- long：8字节 -9223372036854775808~9223372036854775807
					- ```
					  // 定义整型
					  public class Main {
					      public static void main(String[] args) {
					          int i3 = 2_000_000_000; // 加下划线更容易识别
					          int i4 = 0xff0000; // 十六进制表示的16711680
					          int i5 = 0b1000000000; // 二进制表示的512
					  
					          long n1 = 9000000000000000000L; // long型的结尾需要加L
					          long n2 = 900; // 没有加L，此处900为int，但int类型可以赋值给long
					          int i6 = 900L; // 错误：不能把long型赋值给int
					      }
					  }
					  ```
			- 浮点数类型
				- float 最大表示$$3.4*10**38$$
					- ```
					  float f1 = 3.14f;
					  float f2 = 3.14e38f; // 科学计数法表示的3.14x10^38
					  float f3 = 1.0; // 错误：不带f结尾的是double类型，不能赋值给float
					  
					  double d = 1.79e308;
					  double d2 = -1.79e308;
					  double d3 = 4.9e-324; // 科学计数法表示的4.9x10^-324
					  ```
				- double 最大表示$$1.79*10**308$$
			- 字符类型
				- cha 使用单引号`'`，且仅有一个字符 2字节
					- ```
					  // 字符类型
					  public class Main {
					      public static void main(String[] args) {
					          char a = 'A';
					          char zh = '中';
					          System.out.println(a);
					          System.out.println(zh);
					      }
					  }
					  ```
			- 布尔类型
				- boolean Java语言对布尔类型的存储并没有做规定，因为理论上存储布尔类型只需要1 bit，但是通常JVM内部会把`boolean`表示为4字节整数。
					- ```
					  boolean b1 = true;
					  boolean b2 = false;
					  boolean isGreater = 5 > 3; // 计算结果为true
					  int age = 12;
					  boolean isAdult = age >= 18; // 计算结果为false
					  ```
		- 引用类型
			- 引用类型的变量类似于C语言的指针，它内部存储一个“地址”，指向某个对象在内存的位置
			- String
				- ```
				  String s = "hello";
				  ```
		- 常量
			- 定义变量时加上final修饰符
				- 常量在定义时进行初始化后就不可再次赋值，再次赋值会导致编译错误。
				- 常量名通常**全部大写**
				- ```
				  final double PI = 3.14; // PI是一个常量
				  double r = 5.0;
				  double area = PI * r * r;
				  PI = 300; // compile error!
				  ```
		- var关键字
			- 使用`var`定义变量，仅仅是少写了变量类型而已
			- ```
			  StringBuilder sb = new StringBuilder();
			  var sb = new StringBuilder();
			  ```
	- 整数运算
	  collapsed:: true
		- 整数的数值表示不但是精确的，而且整数运算永远是精确的
		- 求余运算使用`%`
		- 溢出
			- 整数由于存在范围限制，如果计算结果超出了范围，就会产生溢出，而溢出**不会出错**，却会得到一个奇怪的结果：
				- ```
				  // 运算溢出
				  public class Main {
				      public static void main(String[] args) {
				          int x = 2147483640;
				          int y = 15;
				          int sum = x + y;
				          System.out.println(sum); // -2147483641
				      }
				  }	
				  ```
		- 运算符简写
			- +=，-=，*=，/=
			- ```
			  n += 100; // 相当于 n = n + 100;
			  n -= 100; // 相当于 n = n - 100;
			  ```
		- 自减/自加
			- 可以对一个整数进行加1和减1的操作：
				- `++n`表示先加1再引用n，`n++`表示先引用n再加1
				- ```
				  // 自增/自减运算
				  public class Main {
				      public static void main(String[] args) {
				          int n = 3300;
				          n++; // 3301, 相当于 n = n + 1;
				          n--; // 3300, 相当于 n = n - 1;
				          int y = 100 + (++n); // 不要这么写
				          System.out.println(y);
				      }
				  }
				  ```
		- 移位运算
			- 左移实际上就是不断地×2，右移实际上就是不断地÷2
			- 对`byte`和`short`类型进行移位时，会首先转换为`int`再进行位移
		- 位运算
			- 位运算是按位进行与、或、非和异或的运算
			  id:: 6756b08f-d581-41c0-9738-f4a16e0c66fe
			- 与运算的规则是，必须两个数同时为`1`，结果才为`1`：
			- ```
			  n = 0 & 0; // 0
			  n = 0 & 1; // 0
			  n = 1 & 0; // 0
			  n = 1 & 1; // 1
			  ```
			- 或运算的规则是，只要任意一个为`1`，结果就为`1`：
			- ```
			  n = 0 | 0; // 0
			  n = 0 | 1; // 1
			  n = 1 | 0; // 1
			  n = 1 | 1; // 1
			  ```
			- 非运算的规则是，`0`和`1`互换：
			- ```
			  n = ~0; // 1
			  n = ~1; // 0
			  ```
			- 异或运算的规则是，如果两个数不同，结果为`1`，否则为`0`：
			- ```
			  n = 0 ^ 0; // 0
			  n = 0 ^ 1; // 1
			  n = 1 ^ 0; // 1
			  n = 1 ^ 1; // 0
			  ```
		- 类型自动提升与强制转型
			- 在运算过程中，如果参与运算的两个数类型不一致，那么计算结果为较大类型的整型。例如，`short`和`int`计算，结果总是`int`，原因是`short`首先自动被转型为`int`：
				- ```
				  // 类型自动提升与强制转型
				  public class Main {
				      public static void main(String[] args) {
				          short s = 1234;
				          int i = 123456;
				          int x = s + i; // s自动转型为int
				          short y = s + i; // 编译错误!
				      }
				  }
				  ```
			- 也可以将结果强制转型，即将大范围的整数转型为小范围的整数。强制转型使用`(类型)`，例如，将`int`强制转型为`short`：
				- ```
				  int i = 12345;
				  short s = (short) i; // 12345
				  ```
	- 浮点运算
	  collapsed:: true
		- 浮点数存在运算误差
		- 判断浮点数是否相等
			- 两数相减的绝对值是否小于一个给定的较小的数
			- ```
			  // 比较x和y是否相等，先计算其差的绝对值:
			  double r = Math.abs(x - y);
			  // 再判断绝对值是否足够小:
			  if (r < 0.00001) {
			      // 可以认为相等
			  } else {
			      // 不相等
			  }
			  ```
		- 溢出
			- 整数运算在除数为`0`时会报错，而浮点数运算在除数为`0`时，不会报错，但会返回几个特殊值：
				- `NaN`表示Not a Number
				- `Infinity`表示无穷大
				- `-Infinity`表示负无穷大
				- ```
				  double d1 = 0.0 / 0; // NaN
				  double d2 = 1.0 / 0; // Infinity
				  double d3 = -1.0 / 0; // -Infinity
				  ```
		- 强制转型
			- 进行四舍五入，可以对浮点数加上`0.5`再强制转型：
				- ```
				  // 四舍五入
				  public class Main {
				      public static void main(String[] args) {
				          double d = 2.6;
				          int n = (int) (d + 0.5);
				          System.out.println(n);
				      }
				  }
				  ```
	- 布尔运算
	  collapsed:: true
		- 布尔运算是一种关系运算，包括以下几类：
			- 比较运算符：`>`，`>=`，`<`，`<=`，`==`，`!=`
			- 与运算 `&&`
			- 或运算 `||`
			- 非运算 `!`
			- ```
			  boolean isGreater = 5 > 3; // true
			  int age = 12;
			  boolean isZero = age == 0; // false
			  boolean isNonZero = !isZero; // true
			  boolean isAdult = age >= 18; // false
			  boolean isTeenager = age >6 && age <18; // true
			  ```
			- 关系运算符的优先级从高到低依次是：
				- `!`
				- `>`，`>=`，`<`，`<=`
				- `==`，`!=`
				- `&&`
				- `||`
			- 短路运算
				- && 出现假就结束
				- || 出现真就结束
	- 字符串与字符
	  collapsed:: true
		- 字符和字符串是两个不同的类型
		- \
			- `\n` 表示换行符
			- `\r` 表示回车符
			- `\t` 表示Tab
			- `\u####` 表示一个Unicode编码的字符
		- 不可变性
			- 指的是字符串内容不可变，变量只是指向字符串
				- ```
				  // 字符串不可变
				  public class Main {
				      public static void main(String[] args) {
				          String s = "hello";
				          System.out.println(s); // 显示 hello
				          s = "world";
				          System.out.println(s); // 显示 world
				      }
				  }
				  ```
		- 空值null
			- 空字符串是一个有效的字符串对象，不等同于null
				- ```
				  String s1 = null; // s1是null
				  String s2 = s1; // s2也是null
				  String s3 = ""; // s3指向空字符串，不是null
				  ```
	- 数组类型
		- 数组所有元素初始化为默认值，整型都是`0`，浮点型是`0.0`，布尔型是`false`；
		- 数组一旦创建后，大小就不可改变
		- 用`数组变量.length`获取数组大小
			- ```
			  // 数组
			  public class Main {
			      public static void main(String[] args) {
			          // 5位同学的成绩:
			          int[] ns = new int[5];
			          System.out.println(ns.length); // 5
			      }
			  }
			  ```
		- 未知数组大小：
			- ```
			  // 数组
			  public class Main {
			      public static void main(String[] args) {
			          // 5位同学的成绩:
			          int[] ns = new int[] { 68, 79, 91, 85, 62 };
			          System.out.println(ns.length); // 编译器自动推算数组大小为5
			      }
			  }
			  //int[] ns = { 68, 79, 91, 85, 62 }; 简化
			  ```
		- 数组本身不变，变的是变量指向的数组位置
- 流程控制
  collapsed:: true
	- 输入与输出
		- 输出
			- `println`是print line的缩写，表示输出并换行。因此，如果输出后不想换行，可以用`print()`：
			- 格式化输出
				- 格式化输出使用`System.out.printf()`，通过使用占位符`%?`，`printf()`可以把后面的参数格式化成指定格式：
					- ```
					  // 格式化输出
					  public class Main {
					      public static void main(String[] args) {
					          double d = 3.1415926;
					          System.out.printf("%.2f\n", d); // 显示两位小数3.14
					          System.out.printf("%.4f\n", d); // 显示4位小数3.1416
					      }
					  }
					  ```
				- 占位符
					- 由于`%`表示占位符，因此，连续两个`%%`表示一个`%`字符本身
					- | 占位符 | 说明 |
					  | ---- | ---- | ---- |
					  | %d | 格式化输出整数 |
					  | %x | 格式化输出十六进制整数 |
					  | %f | 格式化输出浮点数 |
					  | %e | 格式化输出科学计数法表示的浮点数 |
					  | %s | 格式化字符串 |
		- 输入
			- `import`语句导入`java.util.Scanner`
			- 创建`Scanner`对象并传入`System.in` `System.in`代表标准输入流
			- 要读取用户输入的字符串，使用`scanner.nextLine()`，要读取用户输入的整数，使用`scanner.nextInt()`
			- ```
			  import java.util.Scanner;
			  
			  public class Main {
			      public static void main(String[] args) {
			          Scanner scanner = new Scanner(System.in); // 创建Scanner对象
			          System.out.print("Input your name: "); // 打印提示
			          String name = scanner.nextLine(); // 读取一行输入并获取字符串
			          System.out.print("Input your age: "); // 打印提示
			          int age = scanner.nextInt(); // 读取一行输入并获取整数
			          System.out.printf("Hi, %s, you are %d\n", name, age); // 格式化输出
			      }
			  }
			  ```
	- if条件判断
		- 判断引用类型相等
			- equals方法
				- ```
				  // 条件判断
				  public class Main {
				      public static void main(String[] args) {
				          String s1 = "hello";
				          String s2 = "HELLO".toLowerCase();
				          System.out.println(s1);
				          System.out.println(s2);
				          if (s1.equals(s2)) {
				              System.out.println("s1 equals s2");
				          } else {
				              System.out.println("s1 not equals s2");
				          }
				      }
				  }
				  ```
	- switch多重开发
		-
- 练习
	- in.hasNextInt(): 这个方法会检查输入流中是否还有下一个 int 类型的输入。如果有，它返回 true；否则返回 false。
	- in.nextInt(): 这个方法会读取下一个整数值。
	- sc.hasNext() 检查输入流中是否还有下一个 token (默认以空格分隔)
- cd Blog/
  git init
  git clone https://github.com/xianmin/hugo-theme-jane.git --depth=1 themes/jane
- |
- |
- ```
  [1](https://ludard.com/post/tech/create-blog-step-by-step-1/#hl-3-1)
  [2](https://ludard.com/post/tech/create-blog-step-by-step-1/#hl-3-2)
  [3](https://ludard.com/post/tech/create-blog-step-by-step-1/#hl-3-3)
  ```
- |
- ```
  git status
  git add .
  git commit -m 'init blog'
  ```
- ```
  [1](https://ludard.com/post/tech/create-blog-step-by-step-1/#hl-3-1)
  [2](https://ludard.com/post/tech/create-blog-step-by-step-1/#hl-3-2)
  [3](https://ludard.com/post/tech/create-blog-step-by-step-1/#hl-3-3)
  ```
- |
- ```
  git status
  git add .
  git commit -m 'init myBlog'
  ```
- |