# 							BOM

## BOM-window及onload

- BOM学习的对象：window上面的属性和方法；
- onload：等待静态资源加载完成后执行你的逻辑；

## window 对象 

- 特点：
  - 所有window对象的属性和方法，**都可以直接省略  `window.`，而直接使用**
  - 因为window对象在浏览器中被称为顶级对象；
  - *顶级对象**：页面中所有的东西都是依赖于这个对象存在的；
  - 变量与函数：
    - **所有的全局变量和全局函数都是window对象的属性和方法**；
    - 在js代码里面，不使用var声明的变量，都是隐式全局变量，这个方式是不推荐的，因为如果不使用var声明，是不会变量提升的；

## 方法：onload ，   定时器

### onload：等待静态资源加载完成后执行你的逻辑；

- 作用：页面加载完毕的时候执行
- 页面加载完毕：**页面所需的静态资源**全部加载完毕；
- 静态资源： **html文件、css文件、js文件、图片，
- 这个方法调用一般是用window.onload 不省略window;

```js
// 等静态资源全部加载完毕，后面的函数才会执行；
  window.onload = function() {
    // 一般情况下，看见HTML结构里引入图片，用这个方法，，
    // 把你的代码写入这个函数内部;
  }
```

### 定时器

- 语法

- setTimeout：一次性定时器；set - 设置；Timeout - 超时

  ```js
  // 作用： 延迟一定的毫秒之后，调用函数一次;
  // 返回值： 是该定时器的id，id可以用于停止这个定时器 用于清除该定时器
  // 参数：第一个参数：等待一定时间后执行的函数
  //    第二个参数：设置等待多久再执行，毫秒；
   var timer = setTimeout(function() {
  console.log(2);
   }, 3000);
  // 停止一次性的定时器：清除后，就不会执行这个定时器；
  clearTimeout(timer);
  ```

- setInterval：永久性的定时器；interval - 间隔
  ```
  // 作用：阶段的时间执行函数；
  // 返回值：就是该定时器的id
  var timer = setInterval(函数,间隔毫秒数);
  
  // 清除永久定时器
  clearInterval(timer);
  ```

## BOM-location

- 语法：负责管理浏览器地址栏相关的行为和信息的对象；

  ```
  // href 重新指定浏览器的地址，页面会转跳到新的地址；
  location.href = "http://www.baidu.com";
  ```

  

## BOM-localStorage

- 作用：实现数据本地化，刷新后还在；

  ```
  // localStorage场景：用于把一些数据真实存在本地；
  // localStorage ：属性值是个对象，有方法；
  
  setItem:设置本地数据； 
  		第一个参数：key   
  		第二个参数：值，我要存入的数据  
     localStorage.setItem("list", a);
     
  getItem: 读取本地数据：
      返回的是字符串；   传入 要查询的键的名称
  	var a = localStorage.getItem("list");
  	
  removeItem  删除本地数据
  	localStorage.removeItem("list");
  	
  全部清空；
  	localStorage.clear();
  ```

- ###### 获取不存在的键的名称，返回的是null；

## BOM-JSON

- **localStorage** **存入复杂数据类型，要先转换为 JSON格式的字符串；**

- 描述  JSON字符串是个字符串，有一定格式的字符串；

- JS BOM上的**方法：**

  ```
  // 将对象转换为json格式的字符串
   // 参数：传入JS复杂数据类型；
   // 返回值：JSON格式字符串；
  JSON.stringify(对象);   
  var str = JSON.stringify(arr);   
  
  // 将json格式的字符串转换为对象
  // 返回值：依赖于你的json格式字符串，可能返回数组，或者是对象....
  JSON.parse(json格式字符串);
  var aee = JSON.parse(str);
  
  ```

  

## BOM-getComputedStyle    获取样式对象

- 语法

  ```
   var box = document.querySelector(".box");
  
    // DOM 只能获取到行内的样式
    // console.log(box.style);
    
    // BOM：
    // 参数：DOM节点
    // 返回值：这个DOM节点所有的样式集合对象
    var res = window.getComputedStyle(box);
    console.log(res.fontSize, res.width);
  ```

  