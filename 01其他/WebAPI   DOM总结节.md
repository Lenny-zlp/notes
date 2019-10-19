#        					DOM



# 获取元素对象的方法

```js
document.getElementById(id名)  
```

* 获取单个元素对象

* 传入元素 必须是 字符串

```js
document.getElementsByClassName(类名)
```

* 获取元素 组成伪数组， 可以遍历
* 传入元素 必须是 字符串

```
document.getElementsByTagName(标签名);
```

* 获取元素 组成伪数组， 可以遍历
* 传入元素 必须是 字符串

``` javascript
document.body
```

* 获取body，因为body比较特别；永远只有一个；

```javascript
document.querySelector(css选择器);
```

- 作用： 根据指定的选择器获取从上到下的第一个元素，获取不到返回个null对象；
- 该选择器输入的值，主要为CSS选择器的写法，获取元素
- 传入元素 必须是 字符串


```javascript
document.querySelectorAll(css选择器1,css选择器2...);
```

- 作用：根据选择器获取所有满足条件的元素，这个使用的比较多；
- 参数：多个css选择器，以逗号隔开，都是字符串
- 返回值：伪数组；for，但是有forEach方法

# 注册事件的方法

#### 1. onclick  注册点击事件

```js
btn.onclick = function(){
  console.log('被点击了');
}
```

#### 2. onfocus   注册获取光标

```js
search.onfocus = function(){
  // 把搜索历史显示 - 通过修改display属性 - 元素.style.display = 'block';
  list.style.display = 'block';
}
注册给谁？有光标的标签input textarea;
```

#### 3. onblur   注册失去光标

```js

search.onblur = function(){
  // 把搜索历史隐藏 - 修改display为none
  list.style.display = 'none';
}
```

#### oncontextmenu  注册 页面右键

```javascript
document.oncontextmenu = function(e){
    阻止右键弹窗
  e.preventDefault();
}
```

#### 4. onmousedown：按键被点下  当鼠标的按键点下的时候触发

```j
 var p_dom = document.querySelector('.p');
  
  var x_start = 0;
  var y_start = 0;

  var move_key = false;
  p_dom.onmousedown = function (e) {
    // 
    move_key = true;
    
    x_start = e.pageX - p_dom.offsetLeft;
    y_start = e.pageY - p_dom.offsetTop;
  }

  var x_yidong = 0;
  var y_yidong = 0;
  document.onmousemove = function (e) { 
    // console.log(1);
    
    if (move_key) {
      x_yidong = e.pageX - x_start;
      y_yidong = e.pageY - y_start;

      p_dom.style.top = y_yidong  + 'px';
      p_dom.style.left = x_yidong  + 'px';
    }
    
  }

  p_dom.onmouseup = function (e) {
    // 
    move_key = false;
  }
```



#### 5. onmousemove：鼠标移动  鼠标在某个元素身上移动的时候触发

#### 6. onmouseup ：按键被松开   当鼠标的按键被松开的时候触发

#### 7. onmouseover  :   鼠标移入时触发 

#### 8.onmouseout  :     鼠标移出时触发

```
// 鼠标移入时触发 
  // onmouseover：box元素对象 属性名 内置好的；后面要一个函数；方法名；
  box.onmouseover = function(e) {
    // console.log(1);
    // var index = box.getAttribute("index");
    // console.log(index);


    // this：事件注册给谁，this指哪个DOM节点；
    // var index = this.getAttribute("index");
    // console.log(index);


    // 事件对象
    // e.target：触发在谁上面，就是哪个DOM节点；
    // e.currentTarget 事件注册给谁，this指哪个DOM节点；
    // console.log(e.target, e.currentTarget);
  };

  // 鼠标移出时触发
  box.onmouseout = function() {
    // console.log(2);
  };
```



#### 9. onkeydown : 按键按下

#### 10. onkeyup :      按键弹起

- 9.10.的语法

  ```js
   // 键的按下；
    ipt.onkeydown = function(e) {
      // console.log(1);
      // 如何知道你按下的是哪个键？
      console.log(e.keyCode==13, e.ctrlKey);
  
      // e.ctrlKey 只是针对于 ctrl键的 返回是true
    }
  
    // 弹起
    ipt.onkeyup = function() {
      console.log(1);
    }
  注意：enter :13 
  	 ctrl: 17  
  ```

#### addEventListener

```javascript
btn.addEventListener('click', function() {
    console.log(123);
})
```



# 操作标准属性

* 标准属性：html标准中出现的，有特殊功能的属性 id,class,href,src,title....

###### style属性

```js
// 获取：只能获取行内样式；
div.style.backgroundColor
// 设置
div.style.backgroundColor = ’#fff‘;
```

* 获取：只需要  `元素对象.style.样式属性名` ；
* 如果样式属性名是多个单词的，需要把样式属性的`-` 去掉，修改为驼峰命名；

###### checked属性

* 开关属性： checked/selected/disabled ，这种只有两种状态的属性；
* 赋值：两个状态的值，布尔类型
* 什么DOM节点时有这样的属性：<input type="checkbox" name="check" id="ck"  />

```javascript
var ck = document.getElementById('ck');

ck.checked = true;
ck.checked = false;
```

###### nodeName

-  DOM节点属性：e.target.nodeName 返回 DOM节点的标签名；返回值是大写！！！

###### .innerHTML

  innerHTML，可以获取标签内的HTML结构，也也可以设置HTML结构；返回值 是字符串

```javascript
btn.onclick = function () {
    // 给ul添加新的元素
     ul.innerHTML= ul.innerHTML+'<li>新的li</li>';
  }
```



# 操作类样式属性 

* 类样式是 节点上的class属性

###### className 

* 操作类样式的效果：可以添加或修改我们已经写好的类名；快熟的更换样式；

```js
// 如果要修改类样式，只需要把className修改一下就行了；
// 但是会直接覆盖
box.className = '新的类名';

// 解决：在原来的基础上进行添加类名
box.className += '新的类名';
```

###### classList

* add：给元素对象添加一个或者多个类名，不会影响原来的类名；

``` javascript
// 参数：多个类名，之间用逗号隔开
box.classList.add(类名1,类名2...)；
```

* remove： 给元素删除一个或者多个类名，

```javascript
// 参数：多个类名，可以是多个，多个之间用逗号隔开
box.classList.remove(类名1,类名2...)
```

* toggle：切换类名

``` javascript
// 参数： 要切换的类名
box.classList.toggle(类名)
```



# 操作自定义属性

自定义属性：往DOM节点标签内设置自己需要的属性

自定义属性：开发者依据自己的需要，把数据存储到对应元素身上时使用的属性，可以自己胡乱命名的，没啥功能，就是自己需要

标准属性**：html标准中出现的，有**特殊功能的属性** id,class,href,src,title....

###### data-属性

* 自定义属性需要加上data-属性名

```javascript
<input type="button" value="图片1" id="btn_1" data-src="./images/01.jpg">
<input type="button" value="图片2" id="btn_2" data-src="./images/02.jpg">
<input type="button" value="图片3" id="btn_3" data-src="./images/03.jpg">

```



* 事件执行函数：内部如何获取到DOM节点的自定义属性；可以通过标签，也可以通过this;

``` javascript
btn_2.onclick = function(){
  // 修改图片的src属性
  img.src= btn_2.dataset.src;
  
  
  // this，只当前事件执行的事件源本身；点击的是哪个DOM节点，就是谁；
  img.src= this.dataset.src;
}
```

###### getAttribute(属性名)

```js
元素.getAttribute(属性名)
// 作用： 根据属性名获取属性值
// 参数： 要获取的属性名,标准属性和自定义属性都可以。而且自定义属性不再限制于 data-属性 的格式要求
// 返回值：返回获取属性的值；
```

- 获取属性值

###### setAttribute(属性名,属性值)

```javascript
元素.setAttribute(属性名,属性值)
作用：添加或者修改属性的值
// 参数：都是字符串；
```

- 添加或者修改属性值

###### removeAttribute(属性名)

```javascript
元素.removeAttribute(属性名)
```

- 删除某个属性

# 获取元素对象的位置

元素对象的位置：获取到的是数值；

上面学习的鼠标的位置，通过事件对象；

style.left

###### 元素.offsetLeft

###### 元素.offsetTop

###### 元素的offsetParent

```javascript
// 得到的是某个元素距离他的offsetParent元素的水平距离
// 元素.offsetLeft = marginLeft + left
元素.offsetLeft 

// 得到的是某个元素距离他的offsetParent元素的垂直距离
// 元素.offsetTop = marginTop + top
元素.offsetTop 

// 找到一个有定位的父亲元素，如果亲生父亲没有定位，会一直往上找，直到找打有定位的父亲，或者body；
元素的offsetParent
```

- 元素对象的位置：获取到的是数值

# 属性：获取元素的实际宽度和高度

- 实际宽高：border+padding+content(设置的width/height)

  ```
  // 返回盒子实际的宽度(高度)：width（height）+ padding + border
  // 返回是数字；
    console.log(box.offsetWidth, box.offsetHeight);
    
  // 只能进行获取；
  // 元素的实际宽度    元素.offsetWidth 
  // 元素的实际高度    元素.offsetHeight
  ```

  

# 获取事件对象

```javascript
// 获取事件对象
事件源.on+事件类型 = function(事件对象){   }

事件源.addEventListener(事件类型,function(事件对象){});
```

# 事件对象的属性

###### e.clientX e.clientY

```javascript
// 鼠标位置

// 可视区域坐标系 - 以浏览器的可视区域的左上角为原点的
// 可视区域：就是元素用来显示内容的区域
事件对象.clientX
事件对象.clientY
```



###### .pageX .pageY

```javascript

// 页面坐标系  -  以body的左上角作为原点
事件对象.pageX
事件对象.pageY
```



###### e.target

```javascript
// 事件的目标对象，用户点击到谁上面了；
事件对象.target

// 事件的绑定对象，就是是绑定在哪个DOM节点上 和 this一样
// 前面说的事件源
 // 在事件对象中，还有一个属性target，这个属性指向事件目标
e.currentTarget
    // 注意，this目前拥有指向 注册事件的元素；e.currentTarget指向绑定事件的元素的对象，事件源；
    console.log(e.target,e.currentTarget==this);
    
  });
e.currentTarget==this -----> true
```

# 事件对象的方法

###### e.stopPropagation(); 阻止冒泡

```
// 要阻止冒泡，需要先得到事件对象，给处理程序添加一个形参就行
erzi.addEventListener('click',function(e){
  // 调用阻止事件冒泡的方法进行阻止
  // 事件对象 e 把该次点击这个过程看成一个对象
  e.stopPropagation();
  console.log('我是你儿子');
});
```



###### e.preventDefault(); 阻止默认行为

```
// 页面右键事件 查看右键菜单
document.oncontextmenu = function(e){
  e.preventDefault();
}
```



###### 阻止a标签跳转

```
// 阻止a标签转跳
// 1 把a标签的href属性设置为 javascript:void(0);
// 2 在a标签的点击事件里面，return false;
// 3 使用事件对象.preventDefault();
dom_a.addEventListener('click', function(e) {
    e.preventDefault();
});
```



# 事件委托

- 事件默认在冒泡阶段执行：子元素注册了一个事件，父级如果也注册了同样的事件，那么在触发子元素的事件的时候，父级的事件也会跟着触发；

- 事件委托：不是给子元素注册事件，给父亲注册事件；那么点击子元素，根据冒泡执行。父亲也会触发；

  - 把事件注册在父级的元素身上，

  - 利用事件冒泡执行，当事件传播到已经注册了事件的父级元素身上，

  - 判断  触发事件的DOM  （e.target）节点是否是指定的元素，e.target.nodeName=="LI"

  1. 如果是，就执行逻辑，
  2. 否则什么都不管

- 场景：给新增的标签，注册一样的事件，用到事件委托；

# 事件的解绑  

- 事件解绑：事件注销；
  - 希望曾经注册了的事件，在触发之后，无法执行对应的事件处理程序了；
  - 事件触发的时候，把事件解绑。那么下次你再次点击的时候，就无效了。



######  btn.onclick = null;

```javascript
var btn = document.getElementById('btn');
btn.onclick = function(){
  btn.onclick = null;
  console.log('谢谢惠顾');
}

```



###### btn.removeEventListener('click',fn);

```javascript
var btn = document.getElementById('btn');
btn.addEventListener('click',function fn(){
  // 解绑 当前的函数
  btn.removeEventListener('click',fn);
  console.log('抽奖了');
})
```

# 事件三阶段        捕获、到达目标、冒泡

事件发生的时候，必然存在这三个传播的阶段：**捕获、到达目标、冒泡；

- **客观存在事情：**需要记住

  ***

  - 捕获：从根部节点往目标DOM节点上，一层一层的找，捕获到用户点击了那个DOM节点；

  - 冒泡：从目标节点到根节点

  - 冒泡阶段执行：**事件默认是在冒泡阶段执行；**当我们目标DOM节点注册了事件，冒泡往上的DOM节点也注册了同样的事件话，也会执行；

    

###### 冒泡

- 为什么默认是冒泡阶段执行？
  - 用户点击一个孙子元素，站在用户的角度想，
  - 更为人性化的角度是用户看见的第一个弹窗或者反应是用户点击了当前的那个元素，
  - 至少用户知道自己点击对了；
  - 再出现其他反应，也没有关系，但至少用户知道自己第一次点击对了；
  - **上面这个事件执行在冒泡阶段执行；**
  - **但如果是默认是捕获阶段执行，**
  - 从根部到目标元素，一个一个元素执行注册的事件，
  - 若是从根部到目标元素有1万个节点，每个都注册事件，
  - 那用户得等很久，才能看到用户点击的那个元素，**体验不好**。
  - 所有这就是为为什么**默认是冒泡阶段执行？还是归结于用户的体验上；**

### 阻止冒泡

- 为什么要阻止继续冒泡？
  - 当父亲们辈的同样注册了相同的事件，事件默认是在冒泡阶段执行；
  - 所有注册的相同的事件都会执行；
  - 但是，**用户只想点击当前的有反应就行，上面的不需要再执行了。



# DOM-节点-修改、创建、添加

- 创建：
  - innerHTML属性：可以识别HTML结构；
  - document.write();  可以识别HTML结构；
  - document.createElement('li') ：创建出DOM节点，不显示在页面

- 添加：参考

  - 父节节点.appendChild(新DOM节点)：从后添加新的DOM节点；
  - 父节节点.insertBefore(新DOM节点，插入谁之前的DOM节点)：在某个元素之前，添加新的DOM节点

- 修改：

  - innerHTML：结构；
    - console.log(ul.innerHTML);       作用：获取或修改DOM节点里面结构，返回的是字符串    
    - ul.innerHTML = "<li>--------</li>";   设置DOM节点内部的HTML结构，可以识别HTML结构的字符串；
  - innerText：文本内容；
    - innerText 获取DOM节点内部的文本信息；
    - 不识别HTML结构，把你的设置完全当做 文本信息；   li.innerText = "这是一个新的LI标签";

  ###### 例

  ```
  	//获取父元素 
  var ul = document.querySelector("ul");
  	//创建DOM节点:只是在JS里创建出来，在页面还没有显示；
  var li = document.createElement("li");
  	//给li添加内容
   li.innerText = "这是一个新的LI标签";
  	//指定一个父级DOM,从后面添加一个DOM节点：参数：传入DOM节点
  ul.appendChild(li);
  ```

  

# 属性：根据DOM节点 获取 DOM节点

- 获取子元素：可以得到某个元素之下的所有的子元素的集合，一个**伪数组

  ```js
  父元素.children
  ```

- 获取父元素：返回一个；

  ```
  元素.parentNode
  ```

- 获取兄弟元素

  ```
  元素.nextElementSibling  -  得到下一个兄弟元素
  元素.previousElementSibling - 得到上一个兄弟元素
  ```

  







