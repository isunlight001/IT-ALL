# eval函数的作用

总结：
- 如果是字符串就返回字符串
- 如果是JSON对象的拼接的话，需要"("+str+")"
- [原文参见](https://blog.csdn.net/xm393392625/article/details/80359473 )
- 


几个demo：
- 第一个例子： 

```
console.log(eval("1212")); //输出结果为1212；
```


第二个例子： 

```
var msg="hello worle";
 eval("alert(msg)");//  输出：hello world 传入参数当做实际的ECMAScript语句来执行；
 相当于：alert(msg);
```


第三个例子：eval定义一个函数；

```
eval("function sayHi(){alert('hello wold')}");

sayHi();//输出的结果是helloworld  （运行机制：在解析代码的时候，它们包含在一个字符串中，它们只在eval()执行的时候的创建）
```
第四个例子：

```
var obj = eval(“({name:’cat’,color:’black’})”);等效于 var obj = {name:’cat’,color:’black’};
```

==这个主要在处理后台穿过来的json在前台无法转换成json对象的时候，使用eval进行解析==


