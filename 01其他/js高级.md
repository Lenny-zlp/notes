#                   ES6  类   

##  编程两大思想 

- 面向过程  POP(Process-oriented programming)
  - 面向过程就是分析出解决问题所需要的步骤，然后用函数把这些步骤一步一步实现，使用的时候再一个一个的依次调用就可以了

- 面向对象  OOP (Object Oriented Programming)
  - 面向对象是把事务分解成为一个个对象，然后由对象之间分工与合作。

- 区别 
  - 面向过程：小项目
  - 面向对象：多人合作大项目

## 面向对象三大特性

- 封装性        【已经把扫把功能准备好，负责开即可】
- 继承性        【继承与拖拉机，会开拖拉机就会弄这个，继承自拖拉机】
- 多态性        【可以放到一起，也可以单独拿下来，而且那个扫把坏了换哪个不影响其他的】push()

## 面向对象和过程优缺点

- 面向过程
  - 优点  性能比面向对象高，步骤练习紧密
  - 缺点  不好维护，不易多次使用及扩展

- 面向对象
  - 优点：易维护，可复用，可扩展，灵活性高	
  - 缺点     性能没有面向过程高

## 类   对象

- 类： 抽象   泛指一类
- 对象：具体    类中的具体的某个实例【属性和方法的集合】

##### 对象是由属性和方法组成的：

- 属性：对象有什么【访问】【语法：对象.属性】  ===》事物的特征，在对象中用属性来表示（常用名词）

- 方法：对象做什么【执行】【语法：对象.方法()】 ===》事物的行为，在对象中用方法来表示（常用动词）

## 类 class

- 类抽象了对象的公共部分，它泛指某一大类（class）

## 创建类

```
class Star {
};

var ldh = new Star();
```

## 类constructor构造函数

```
class Star {
	constructor (uname,age){
		this.uname = uname;
		this.age = age;
	}
}

属性：放到constructor，构造函数里面
注意：类里面的方法不带function，直接写既可

类里面要有属性方法，属性方法要是想放到类里面，我们用constructor构造器

构造函数作用：接收参数，返回实例对象，new的时候主动执行，主要放一些公共的属性
```

constructor() 方法是类的构造函数(默认方法)，用于传递参数,返回实例对象，通过new命令生成对象实例时，自动调用该方法。

注意：每个类里面一定有构造函数，如果没有显示定义, 类内部会自动给我们创建一个constructor() ，

注意：this代表当前实力化对象，谁new就代表谁

## 类添加方法

- 语法：注意方法和方法之间不能加逗号

  ```
  class Star {
  
  	constructor () {}
  
  	sing () {}
  
  	tiao () {}
  
  }
  
  
  class 类名 { constructor(){}   方法名(){} }
  
  注意：类中定义属性，调用方法都得用this
  注意：方法之间不能加逗号分隔，同时方法不需要添加function 关键字
  ```

- ##### 总结：类有对象的公共属性和方法，用class创建，class里面包含constructor和方法，我们把公共属性放到constructor里面，把公共方法直接往后写既可，但是注意不要加逗号

## 类的继承

- #### extends

  ```
  语法：
  
  ​	class Father {}
  
  ​	class Son extends Father{}
  
  注意：是子类继承父类
  ```

  

## super关键字

- 我们应用的过程中会遇到父类子类都有的属性，此时，没必要再写一次，可以直接调用父类的方法就可以了
- super关键字用于访问和调用对象父类上的函数。可以调用父类的构造函数，也可以调用父类的普通函数

- 当子类没有constructor的时候可以随意用父类的，但是如果子类也含有的话，constructor会返回实例，this的指向不同，不可以再直接使用父类的东西

  ### 调用父类构造函数

  ```
  class F { 
  constructor(name, age){}
  }
  
  class S extends F { 
  constructor (name, age) { 
  super(name,age);
    }
  }
  
  注意: 子类在构造函数中使用super, 必须放到this 前面(必须先调用父类的构造方法,在使用子类构造方法
  ```

  ### 调用父类普通函数*

  ```
  class F { 
  constructor(name, age){} 
  say () {} 
  }
  
  class S extends F { 
   constructor (name, age) {
   super(name,age);
    }
   say () { super.say() }
  }
  
  注意：如果子类也有相同的方法，优先指向子类，就近原则
  
  如果子类不写东西，那么直接继承父类就可以用 
  但是如果子类有自己的构造函数和父类同名的方法，此时不可以直接用父类的东西，需要用super调用父类的方法和构造函数
  ```

  ##### 总结：super调用父类的属性和方法，那么查找属性和方法的原则就近原则

## 三个注意点

- 在ES6中类没有变量提升，所以必须先定义类，才能通过类实例化对象.
- 类里面的共有属性和方法一定要加this使用.【this，对象调用属性和方法】按钮练习
- 类里面的this指向问题
  - constructor 里面的this指向实例对象, 方法里面的this 指向这个方法的调用者

### 类里面的this指向

- 构造函数的this指向实例对象

- 普通函数的this是调用者，谁调用this是谁

  ```
   var li = '<li> 我是li标签</li>';
   that.ul.insertAdjacentHTML('beforeend', li);
   
   该方法地址:  https://developer.mozilla.org/zh-CN/docs/Web/API/Element/insertAdjacentHTML
  ```

  

### 添加元素

```

```



## 创建对象

- 通过字面量

  ```
  var obj={
   name:"小王",
   age:22,
   chang:function() {
      console.log("123")
   }
  }
  ```

- 通过构造函数创建对象【object】

  ```
  var obj=new Object();
  obj.name="小王"；
  obj.chang=function() {
  alert("123")
  }
  ```

  

- 自定义构造函数

  ```
  function Star (name,age) {
  	this.name=name;
  	this.age=age
  }
  
  
  var obj=new Star('小王'，22)；
  ```

  #### 区分普通函数和构造函数

  ```
  function fn() {}
  
  fn()  //调用   普通函数
  var obj=new fn()  //new   构造函数
  
  ```

  

##### 静态成员和实例成员

- 静态成员：在构造函数身上的成员叫静态成员，静态成员只能由构造函数访问
- 实例成员：在构造函数内部的成员叫实例成员，实例成员只有由实例对象访问

### 原型对象  

- 原型对象：prototype，构造函数的一个属性，
- 每一个构造函数都有一个原型
- 总结：属性放到构造函数，方法放到原型对象

```
function Star (name,age) {
	this.name=name;
	this.age=age;
	// 浪费空间
	// this.chang = function () {}
}

Star : 构造函数
prototype: 原型对象
Star.prototype.chang = function () {
			console.log('嫦娥');
		}
var obj = new Star('张三丰', 22);		
```

### 对象原型 ：__proto__

- 主要作用：指向prototype

- 注意：____proto____是一个非标准属性，不可以拿来赋值或者设置【只读属性】

- 总结：每一个对象都有一个原型，作用是指向原型对象prototype

  ```
   function Star(name, age) {
          this.name = name;
          this.age = age;
      }
      Star.prototype.chang = function() {
          console.log("唱歌")
      }
      var obj = new Star("小王", 22);
      // obj.chang();
      console.log(obj);
      console.log(obj.__proto__);
      console.log(Star.prototype == obj.__proto__); //true
  ```

  

### 构造函数  constructor

- 作用：指回构造函数本身  记录是那个构造函数创建出来的

- 原型对象：prototype   保存方法

- 对象原型：____proto____    指向原型对象

- 构造函数： constructor：指回构造函数

instanceof: 查看是否是对象类型   console.log(arr instanceof  Object)