梳理:


需求讲解(产品经理)
设计评审
案例评审
代码评审
冒烟
UAT用户满意度测试
回归测试
预发布验证
版本评审ITC

格式化  ctr + i
搜索替换  option+cmd+f

架构模式 MVVM 

Runtime 方法替换   
	YLSafeObject

DSBridge 

swift 
	Swift 是一个类型安全（type safe）的语言

	类型安全
		Swift 是类型安全的，所以它会在编译你的代码时进行类型检查（type checks），并把不匹配的类型标记为错误,  当你要处理不同类型的值时，类型		检查可以帮你避免错误

	类型推断
		编译器在编译代码的时候自动推断出表达式的类型。不需要每次声明常量和变量的时候都需要显式指定类型,  原理是检查你赋的值
	
	可选类型
		可选类型（optionals）来处理值可能缺失的情况
		表示两种可能： 或者有值, 你可以解析可选类型访问这个值;    或者根本没有值
		nil 不能用于非可选的常量和变量。如果你的代码中有常量或者变量需要处理值缺失的情况，请把它们声明成对应的可选类型。
		Swift 的 nil 和 Objective-C 中的 nil 并不一样。在 Objective-C 中，nil 是一个指向不存在对象的指针。在 Swift 中，nil 不是指针——它是一个确定			的值，用来表示值缺失。任何类型的可选状态都可以被设置为 nil，不只是对象类型。

	可选值的强制解析（forced unwrapping）：
		当确定可选类型确实包含值之后，在可选的名字后面加一个感叹号（!）来获取值,  使用 ! 来获取一个不存在的可选值会导致运行时错误。使用 ! 来强		制解析值之前，一定要确定可选包含一个非 nil 的值

	guard 
		guard的执行取决于一个表达式的布尔值,  要求条件必须为真时，以执行 guard 语句后的代码.  不同于 if 语句，一个 guard 语句总是有一个 else 从句

	函数的定义与调用
		
	实参
		函数的实参必须与函数参数表里参数的顺序一致

	输入输出参数（In-Out Parameters）
		在参数定义前加 inout,  当传入的参数作为输入输出参数时，需要在参数名前加 & 符，表示这个值可以被函数修改
		输入输出参数不能有默认值，而且可变参数不能用 inout 标记
	
	闭包
		函数和闭包都是引用类型
		闭包可以捕获和存储其所在上下文中任意常量和变量的引用。被称为包裹常量和变量。 Swift 会为你管理在捕获过程中涉及到的所有内存操作
		闭包的函数体部分由关键字 in 引入。该关键字表示闭包的参数和返回值类型定义已经完成，闭包函数体即将开始。

		值捕获
			包可以在其被定义的上下文中捕获常量或变量。即使定义这些常量和变量的原作用域已经不存在，闭包仍然可以在闭包函数体内引用和修改这些值
			
			如果你将闭包赋值给一个类实例的属性，并且该闭包通过访问该实例或其成员而捕获了该实例，你将在闭包和该实例间创建一个循环强引用。Swift 使用捕获			列表来打破这种循环强引用。


	结构体和类对比
		Swift 中结构体和类有很多共同点。两者都可以：
		 	* 定义属性用于存储值   
		 	* 定义方法用于提供功能   
			* 定义下标操作用于通过下标语法访问它们的值   
			* 定义构造器用于设置初始值   
			* 通过扩展以增加默认实现之外的功能   
			* 遵循协议以提供某种标准功能  
		与结构体相比，类还有如下的附加功能：
			继承允许一个类继承另一个类的特征 
			类型转换允许在运行时检查和解释一个类实例的类型 
			析构器允许一个类实例释放任何其所被分配的资源 
			引用计数允许对一个类的多次引用
			所有结构体都有一个自动生成的成员逐一构造器，用于初始化新结构体实例中成员的属性。类实例没有默认的成员逐一构造器

	值类型
		是这样一种类型，当它被赋值给一个变量、常量或者被传递给一个函数的时候，其值会被拷贝。
		Swift 中所有的基本类型：整数（integer）、浮点数（floating-point number）、布尔值（boolean）、字符串（string)、数组（array）和字典（dictionary），		都是值类型，其底层也是使用结构体实现的。

		Swift 中所有的结构体和枚举类型都是值类型。  
		
	引用类型
		类是引用类型	

	属性
		当值类型的实例被声明为常量的时候，它的所有属性也就成了常量,  引用类型的类则不一样。把一个引用类型的实例赋给一个常量后，
		依然可以修改该实例的可变属性。
		
		延时加载存储属性
			延时加载存储属性是指当第一次被调用的时候才会计算其初始值的属性。在属性声明前使用 lazy 来标示一个延时加载存储属性		
			必须将延时加载属性声明成变量（使用 var 关键字），因为属性的初始值可能在实例构造完成之后才会得到。而常量属性在构造过程完成之前必须要有初始值，因此无法声明成延时加载

			如果一个被标记为 lazy 的属性在没有初始化时就同时被多个线程访问，则无法保证该属性只会被初始化一次。

	疑问点
        1. var let 使用时机
        2. ? 含义,用法
            -  定义属性
            -  定义函数
            -  访问属性和调用函数, 可空链式调用
            -  类型转换 
        3. guard let _ = (scene as? UIWindowScene) 
        4. tabbar 	
        5. Any?
		
	 数组
		swift 数组只能存储一种数据类型




