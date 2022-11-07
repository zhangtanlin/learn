# FLUTTER
FLUTTER

## 文档
- [常用插件](https://juejin.im/post/5de9bbb0f265da33d361f5d0)
- [《Flutter实战》电子书](https://github.com/flutterchina/flutter-in-action/blob/master/docs/SUMMARY.md)
- [数据类型转换](https://app.quicktype.io/)
- [吸顶效果](https://www.jianshu.com/p/b5292ef7c38c)
- [AppBar滚动渐变(notification.metrics用法)](https://www.programmersought.com/article/88294292702/)
- [flutter部件插件](https://asmcn.icopy.site/awesome/awesome-flutter/)
- [flutter预加载资源学习文档](https://stackoverflow.com/questions/61353764/preload-all-image-assets-in-a-flutter-app)

## 插件
+ flutter下拉/下拉加载插件：pull_to_refresh
+ flutter数据库存储：drift 1.5.0(安装方法：flutter pub add drift)

## flutter混淆说明
一、混淆前需要做的<br/>
1.字符串拼接尽量使用 + 进行拼接，<br/>
2.用$拼接也可以，但是不可以存在表达式和中括号引用的变量,可以使用方法，但是方法中不要直接传入字符串
如: ${a > b ? '1' : '2'}或者${a['b'] }和${ function('字符串')}以及${a ?? '123'} 都是错误写法，
${a}  ${a.b} 这都是可以的<br/>
3.使用三元表达式时 把表达式中的字符串写成变量
如: a=‘a.png’ b='b.png' 
bool ? a : b;<br/>
注意: 正则中的字符串也会被混淆<br/>
二、混淆后的修改<br/>
1.在 switch/case 条件语句中需要使用 const 声明的值 ，如果过是变量需要使用const声明，
所以在混淆之后需要把const 声明的值改回 未混淆之前的值，如果不想麻烦可以使用 if/else代替
（我是使用的前者，因为这种变量不多）<br/>
2.混淆后的字符串后面有一部分会带有一个空白字符，但不是空格，打印出它的unicode 是[0]
 所以需要替换掉它，还有‘\n’也是无效的，也需要替换,
全局替换就OK<br/>
源代码: utf8.decode(newList)
修改后的代码:  utf8decode(newList).replaceAll(utf8.decode([0]), '') .replaceAll(r'\n', '\n')

