# java8

构造方法/构造器
看一个需求
我们来看一个需求：前面我们在穿件人类的对象时，是先把一个对象创建好后，再给他的年两和姓名属性赋值，如果现在我要求，在创建人类的对象时，就直接指定这个对象的年龄和姓名，该怎么做？这时就可以使用构造器。
基本语法
【修饰符】方法名（形参列表）{
方法体；}
1.构造器的修饰符可以默认，也可以是public protected private
2.构造器没有返回值
3.方法名和类名字必须一样
4.参数列表 和成员方法一样的规则
5.构造器的调用，由系统完成

constructor构造器 建造
基本：
构造方法又叫构造器，是类的一种特殊的方法，它的主要作用是完成对新对象的初始化，它有几个特点：
1.方法名和类名相同
2.没有返回值
3.在创建对象时，系统会自动的掉该类的构造器完成对对象的初始化。


构造方法
快速入门
现在我们就用构造方法来完成刚才提出的问题：在创建人类的对象时，就直接指定这个对象的年龄和姓名

class constructor{
	public static void main(String[] args) {
	//当我们new一个对象时，直接通过构造器指定名字和年龄
	Person p1 = new Person("smith",80);
	System.out.println("p1的信息如下");
	System.out.println("p1对象name=" + p1.name);
	System.out.println("p1对象age=" + p1.age);
	}
}
class Person{
	String name;
	int age;
	//构造器
	//没有返回值不能写void
	//构造器的名称和类Person一样
	//（String pName, int pAge）是构造器形参列表，规则和成员方法一致
	public Person(String pName,int pAge){
		System.out.println("构造器被调用");//输出
		name = pName;
		age = pAge;
	}
}

构造器的注意事项和使用细节
1.一个类可以定义多个不同的构造器，即构造器重载，比如：我们可以再给Person类定义一个构造器，用来创建对象的时候，只指定人命，不需要指定年龄
2.构造器名和类名要相同
3.构造器没有返回值
4.构造器是完成对象的初始化，并不是创建对象
5.在创建对象时，系统自动的调用该类的构造方法


class Person{
	String name;
	int age;
	//构造器
	//没有返回值不能写void
	//构造器的名称和类Person一样
	//（String pName, int pAge）是构造器形参列表，规则和成员方法一致
	public Person(String pName,int pAge){
		System.out.println("构造器被调用");//输出
		name = pName;
		age = pAge;
	}	public Person(String pName){
		System.out.println("构造器被调用");//输出
		name = pName;
		age = pAge;
	}
}构造器名与类名要相同

6.如果程序员没有定义构造器，系统会自动给类生成一个默认无参构造器（也叫默认构造器），比如Person{}{}，使用javap指令反编译看看
Dog dog1 = new Dog();//()带动默认构造器
	}
}
class Dog{
	//如果程序员没有定义构造器，系统会自动给类生成一个默认无参构造器（也叫默认构造器）
	/*
	   默认构造器
	   Dog(){
	
	   }
	   */
}

javap能对给定的class文件提供的字节代码进行反编译，通过它，可以对照源代码。
-v 输出附加信息
-p显示所有类和成员 javap Dog   
-c 对代码进行反汇编


7.一旦定义了自己的构造器，默认的构造器就覆盖了，就不能再使用默认的无参构造器，除非显式的定义一下，即Person{}{}，Dog{}这点很重要
	Dog dog1 = new Dog();//()带动默认构造器
	}
}
class Dog{
	//如果程序员没有定义构造器，系统会自动给类生成一个默认无参构造器（也叫默认构造器）
	/*
	   默认构造器
	   Dog(){还想用默认必须显示默认
                                    无参构造器
	
	   }
	   */public Dog(String dName){//没有了默认无参构造器
	   //...
	}
}

构造方法：



//前面定义的Person类中添加两个构造器：
 //第一个无参构造器：利用构造器设置所有人的age属性初始值为18
 //第二个带pName和pAge两个参数的构造器：使得每次创建Person对象的同时初始化对象的age属性值和name属性值
//分别使用不同的构造器，创建对象。
class constructor2{

	public static void main(String[] args) {
		Person p1 = new Person();//默认无参构造器
			Person p2 = new Person("scott",90);//默认无参构造器
		System.out.println(p1.name + p1.age+"\n"+ p2.name + p2.age);


//对象Person有了p2 和 p1 两个名字

	}
}
class Person{
	int age;
	String name;
	public Person(){
		age = 18;
	}
	public Person(String pName,int pAge){
          age = pAge;
          name = pName;
	}
}

对象创建的流程分析
看一个案例
class Person{//类Person
    int age = 90;
String name;
Person(String n, int a){//构造器
         name = n;//给属性赋值
       age= a;
}}
Person p = new Person("小钱“，20）p就是对象的引用
)
流程分析（面试题）
1.加载Person类信息（Person.class），只会加载一次
2.在堆中分配空间（地址）
3.完成对象初始化【3.1默认初始化 age=0 name=null 3.2 显式初始化 age = 90， name = null， 3.3构造器的初始化 age = 20，name = 小倩】
4.在对象在堆中的地址，返回给p（p是对象名，也可以理解成是对象的引用）


类定义的完善
学习完构造器后，我们类的定义就应该更加完善了
class 类名{
成员变量；}         ====>      class   类名{
                                          成员变量；
                                         成员方法；
                                          }
class   类名{
成员变量；                               <====
构造器；
成员方法}
                            =====》待定

