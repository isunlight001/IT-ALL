1.JSON.stringify()用于从一个对象解析出==字符串==，eg：
```
var obj = {"name":"奔跑的蜗牛","age":"200"};
console.log(JSON.stringify(obj));
// 结果：{"name":"奔跑的蜗牛","age":"200"};
console.log(typeof JSON.stringify(obj));
// 结果：string
```
2.JSON.parse()用于从一个字符串中解析出==json对象==，eg：
```
var str = '{"name":"奔跑的蜗牛","age":"200"}';
console.log(JSON.parse(str));
// 结果：Object {name: "奔跑的蜗牛", age: "200"};
console.log(typeof JSON.parse(str));
// 结果：object
```
【注】==单引号在外，里面应该用双引号，否则报错（3.html:16 Uncaught SyntaxError: Unexpected identifier）;双引号在外，里面应该用单引号==

3.eval(string)

语法说明：

```
eval()函数可计算某个字符串，并执行其中的的JavaScript代码。
如果参数是一个表达式，eval() 函数将执行表达式。如果参数是Javascript语句，eval()将执行 Javascript 语句。
string：必需。要计算的字符串，其中含有要计算的 JavaScript 表达式或要执行的语句
```

```
var obj = '{"name":"奔跑的蜗牛","age":200}';
var evalobj=eval('('+obj+')');
console.log(evalobj);
// 结果：Object {name: "奔跑的蜗牛", age: 200}
console.log(typeof evalobj);
// 结果：object
```
解释：

```
加上圆括号的目的：是迫使eval函数，在处理JavaScript代码的时候，强制将括号内的表达式（expression）转化为对象，而不是作为语句（statement）来执行
```
 4.JSON.parse()和eval(string)，两者的区别


```
var value = 1;
var jsonstr = '{"data1":"hello","data2":++value}';
var data1 = eval('('+jsonstr+')');console.log(data1);//这时value值为2
var data2=JSON.parse(jsonstr);console.log(data2);//报错

```
结果：


```
eval在解析字符串时，会执行该字符串中的代码（这样的后果是相当恶劣的），
如上例中，由于用eval解析一个json字符串而造成原先的value的值改变这是极其不安全的，
很容易被恶意的用户在json字符串注入木马链接。
所以推荐使用JSON.parse()来解析字符串。
该方法不仅可以捕捉JSON中的语法错误，并且允许你传入一个函数，用来过滤或转换解析结果
```




。

