---
layout: post
title: Function function Object instanceof
date: 2010-05-07
categories:
- dev
tags: []
status: publish
type: post
published: true
meta:
  _edit_last: '1'
  edg_digg_count: '0'
  _wp_old_slug: function-function-object
  dsq_thread_id: '404521134'
---
看<a href="http://www.planabc.net/" target="_blank">怿飞</a>的<a title="http://www.planabc.net/2010/05/06/interesting_code_associated_with_function_and_object/" href="http://www.planabc.net/2010/05/06/interesting_code_associated_with_function_and_object/" target="_blank">与 Function 和 Object 相关的有趣代码</a>，据说此人也叫<a href="http://www.planabc.net/" target="_blank">圆心</a>，公布下答案：
<pre lang="javascript">function Foo() {};
var foo = new Foo();
alert(foo instanceof Foo); // true
alert(foo instanceof Object); // true
alert(foo instanceof Function); // false
alert(Foo instanceof Function); // true
alert(Foo instanceof Object); // true</pre>
先上图：

<a href="http://www.yeahxj.com/wp-content/uploads/javascript_object_layout.jpg"><img class="alignnone size-full wp-image-261" title="javascript_object_layout" src="http://www.yeahxj.com/wp-content/uploads/javascript_object_layout.jpg" alt="" width="611" height="760" /></a>

以上这张图杂乱无章，其实我不太看懂，那先看下下面这些例子：

1: Function 和 function
<pre lang="javascript">    alert(Function);
    //function Function() {
    //  [native code]
    //}
    alert(typeof Function); //function
    alert(Function instanceof Object); // true

    function fun() { };
    alert(typeof fun); //function
    alert(fun.constructor == Function); //true
    alert(fun instanceof Function); //true
    alert(fun instanceof Object); //true</pre>
Function系统内置的function，用户定义的 function 都由它创建。并且他们都是"继承"于Object的.
2: function 和 Object
<pre lang="javascript"> function Class(){};

    alert(typeof Class); //function
    alert(Class.constructor == Function); //true
    alert(Class instanceof Function); //true
    alert(Class instanceof Object); //true
    alert(typeof Class.prototype); //object

    var c1 = new Class();
    alert(typeof c1);  //object
    alert(c1.constructor == Class); //true
    alert(c1 instanceof Class); //true
    alert(c1 instanceof Function); //false
    alert(c1 instanceof Object); //true
    alert(typeof c1.__proto__); //ie下为undefined firefox为object
    alert(c1.__proto__ == Class.prototype); //ie下为flase firefox为true</pre>
function 是 Function 的一个实例，是继承与Object的，在具有Object对象的特征之外，还具有
1) 可以进行 new 操作，来模拟一些面向对象的功能， new 操作返回的是一个 object 对象。它是构造函数和Object对象的实例。
2) new Class() 操作的三个步骤
a) var c1 = new Object 对象
b) 新建的 c1 复制 原来 function Class 的所有属性和方法
c) c1.__proto__ = Class.prototype
3) 在c1中，把this 指向c1
//ie 中 看不到__proto__,不过应该有相应的隐藏值

3: 关于javascript中instanceof
<pre lang="javascript">    function class1() { };
    function class2() { };
    class2.prototype = new class1();
    function class3() { };
    class3.prototype = new class2();
    function class4() { };
    class4.prototype = new class3();
    function class5() { };
    class5.prototype = new class4();

    var obj = new class4();

    //测试正常的继承关系
    alert(obj instanceof class5); //false
    alert(obj instanceof class4); //true
    alert(obj instanceof class3); //true
    alert(obj instanceof class2); //true
    alert(obj instanceof class1); //true

    class3.prototype = new class5(); //改变继承关系

    //测试改变后的继承关系
    alert(obj instanceof class5); //false
    alert(obj instanceof class4); //true
    alert(obj instanceof class3); //false
    alert(obj instanceof class2); //true  仍然是true
    alert(obj instanceof class1); //true  仍然是true</pre>
<pre lang="javascript">    var _proto = obj.__proto__;

    while (_proto) {
            if (_proto == class1.prototype) {
                alert("class1");
            }
            else if (_proto == class2.prototype) {
                alert("class2");
            }
            else if (_proto == class3.prototype) {
                alert("class3");
            }
            else if (_proto == class4.prototype) {
                alert("class4");
            }
            else if (_proto == class5.prototype) {
                alert("class5");
            }
            else if (_proto == Object.prototype) {
                alert("Object");
            } else {
                alert("unknow");
                alert(_proto.constructor);
            }
            _proto = _proto.__proto__;
     }</pre>
