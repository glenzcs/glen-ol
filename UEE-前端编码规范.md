# 前端编码规范
##1 通用准则
###1.1	缩进
对于所有编程语言，包括html/css/javascript，我们要求使用软tab（用空格字符），在你的编辑器中敲Tab，应该是由4个空格代替。

###1.2	注释
我们提倡尽可能多的写有效的注释，不必考虑注释可能会带来的文件体积变大。在运行态我们有多种手段消除由注释/空格/换行带来的文件体积变大的问题，
如js/css文件压缩，静态资源服务端通过gzip压缩等。

需要注意的是，html/css/js的注释方式是不同的，在合适的地方使用合适的注释方式，如：
```html
<!—这是一段合法的html注释-->
<div class=”test-header”>
    ......
</div>
/**
 * 这是一段合法的js注释
 */
  function test(a,b){
    ......
}
```

###1.3	文件编码
我们要求所有的文件以UTF-8无BOM的方式进行编码。

###1.4	文件命名
无论文件还是文件夹的命名，都需要遵循：
* 以英文命名，且命名全小写。
* 多个英文单词之间使用”-”连接，只能出现英文字母、数字和连接符，严禁出现中文。

##2 HTML编码准侧
###2.1	显式申明doctype
在HTML的顶部显式申明doctype，指示浏览器触发标准模式，避免触发浏览器的Quirks模式。HTML5对doctype的申明更加友好，
建议在所有的HTML头部都显式申明该文档的doctype为HTML5，如：
```html
   <!DOCTYPE html>
```

###2.2	显式申明字符编码
通过meta标签显式申明当前文档的编码格式。
```html
   <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
```
如果是html5，则只需要写：
```html
   <meta charset="utf-8">
```

###2.3	阻止IE的兼容模式
有时IE会在用户不知道的情况下，自作主张切换到兼容模式进行显示。我们要求通过meta标签显式申明不使用兼容模式：
```html
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
```

###2.4	HTML的属性值
HTML的属性使用全小写，属性值使用双引号包裹，如:
```html
	<!-- Not recommended -->
	<div paramIndex='maia-button maia-button-secondary'>Sign in</a>
	<!-- Recommended -->
	<a param-index ="maia-button maia-button-secondary">Sign in</a>
```

###2.5	type属性
避免在script、link标签中使用type属性，如:
```html
	<!-- Not recommended -->
	<link rel="stylesheet" href="//www.google.com/css/maia.css"
	  type="text/css">
	<!-- Recommended -->
	<link rel="stylesheet" href="//www.google.com/css/maia.css">
	<!-- Not recommended -->
	<script src="//www.google.com/js/gweb/analytics/autotrack.js"
	  type="text/javascript"></script>
	<!-- Recommended -->
	<script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>
```

###2.6	多媒体标签的alt属性
当我们使用img等多媒体标签时，我们无法确定现网中会不会出现指定资源无法加载的问题。为了使我们的站点更加友好，可以通过alt属性指定备份文字：
```html
<!-- Not recommended -->
<img src="spreadsheet.png">
<!-- Recommended -->
<img src="spreadsheet.png" alt="Spreadsheet screenshot.">
```

###2.7	正确使用标签闭合
* 自定义标签一定要使用全闭合。
如：
```html
<!-- Not recommended -->
<uee:fire script=”test”/>
<!-- Recommended -->
<uee:fire script=”test”></uee:fire>
```
* void element标签不要闭合。
```html
<!-- Not recommended -->
<br></br>
<br/>
<!-- Recommended -->
<br>
```
根据[w3的规范](http://www.w3.org/TR/html5/syntax.html#void-elements)，void元素有area，base，br，col，command，embed，hr，img，input，keygen，link，meta，param，source，track，wbr。

###2.8 合适的使用缩进
html作为XML衍生的标记语言，只有恰当的使用换行和缩进，才能保证html代码的可读性。
```html
<!-- Not recommended -->
<div>
<span>
Not recommended
</span>
</div>
<!-- Recommended -->
<div>
	<span>
	Not recommended
	</span>
</div>
```

###2.9 元素id与class的命名
* id必须保证全局唯一性，在一个页面中，id不允许重复。
* 命名一律小写，多个英文单词之间使用”-”连接。
```html
/* Not recommended: does not separate the words “demo” and “image” */
.demoimage {}
/* Not recommended: uses underscore instead of hyphen */
.error_status {}
/* Recommended */
#video-id {}
.ads-sample {}
```
* 命名遵循“内容优先”的原则，命名跟其包含的内容相关，如”choose-number”。
* 命名尽可能的短的情况下保持语义化。
```html
/* Not recommended */
#navigation {}
.atr {}
/* Recommended */
#nav {}
.author {}
```
* 大型项目组中，命名建议加上前缀，避免使用css选择器时发生命名冲突的情况。
```html
/* Recommended */
.adw-help {} /* for AdWords */
#maia-note {} /*  for Maia */
```

## 3 CSS编码准则
###3.1 css文件的引用总是放在head区
###3.2 尽量少使用内联样式
###3.3 定义css选择器时，优先使用id，其次使用class
使用高效的css选择器，详见 http://rnd-soa.huawei.com/uee/doc/guide/#/item/best-practice#2-css 。
###3.4 css选择器单独占一行，每个属性单独占一行，以分号结尾
```html
/* Not recommended */
.test {display: block;height: 100px}
/* Recommended */
.test {
    display: block;
    height: 100px;
}
```

###3.5 属性值前用空格分开，选择器后用空格分开
```html
/* Not recommended */
h3{
    font-weight:bold;
}
/* Recommended */
h3 {
    font-weight: bold;
}
```

###3.6 不同css规则之间用空行隔开
```html
/* Recommended */
html {
    background: #fff;
}

body {
    margin: auto;
    width: 50%;
}
```

###3.7 属性值中使用单引号代替双引号
```html
/* Not recommended */
html {
    font-family: "open sans", arial, sans-serif;
}
/* Recommended */
html {
    font-family: 'open sans', arial, sans-serif;
}
```

##4 Javascript编码准则
###4.1	使用var申明变量
在申明一个局部变量时，显示使用var来申明，如果不使用的话，相当于申明了个全局的变量，可能跟现有的变量名冲突。

如确实要申明全局变量，必须显式申明：
```html
window.globalVar = { ... }
```

###4.2 语句显式以分号结尾

###4.3 避免使用eval
当前我们支持的浏览器是IE8以上，chrome，firefox，从JSON转换的角度来看，已经原生支持JSON.parse()和JSON. Stringify()进行JSON的序列化与反序列化，无需通过eval完成。

###4.4 不要修改一个基本对象的原型
如不要擅自给String、Array这样的基本对象增加方法，你加的这一个方法可能对整个系统使用基本类型时产生影响。

###4.5 不要使用浏览器检测和版本检测
如需要，使用特性检测，更多信息参见 [深入 HTML5： 检测](http://diveintohtml5.info/detect.html) 和[jQuery support文档](http://api.jquery.com/jQuery.support/)。

###4.6	缩进与换行
* 左括号不另起一行。
```html
/* Not recommended */
if (something) {       //if后的左括号不另起一行
    // ...
} else {
    // ...
}
```
* array，object的初始化。
```html
var arr = [1, 2, 3];  // No space after [ or before ].
var obj = {a: 1, b: 2, c: 3};  // No space after { or before }.
// Object initializer.
var inset = {
    top: 10,
    right: 20,
    bottom: 15,
    left: 12
};
```
* 数值操作符(如, +/-/*/% 等)两边留空格，赋值操作符/等价判断符两边留空格。
```html
var value = 1 + 2;
```
* 每个冒号，逗号后添加空格。
```html
for (var i = 0, j = arr.length; i < j; i++) {
// Do something.
}
```
* 每行代码字符数建议不超过120个字符。
* 逻辑上独立的代码块之间用空行隔开。

###4.7	命名
* 普通变量统一以驼峰命名法命名，如myContent。
* 常量、枚举值全部大写，以_为连接符，如MAX_POP_SIZE。
* boolean变量的命名以is开头，如isValid。

###4.8	字符串避免一行过长
字符串过长时以”+”或者”array.join()”进行拼接，书写时换行书写，避免一行过长。

###4.9	函数带有有效注释
函数需要带有有效的注释，在注释中对函数的功能及参数进行说明。
```html
/**
     * Context constructor
     * @param $scope, the scope context attach to
     * @param jqBusiness, the <business> define DOM object (TODO refactor later)
     * Usage: new Context($scope, jqBusiness)
     */
function Context($scope, jqBusiness){
......
}
```

##附： 参考文献
* Google html/css编码规范：  
http://google-styleguide.googlecode.com/svn/trunk/htmlcssguide.xml#General_Formatting_Rules
* Google js编码规范：  
http://google-styleguide.googlecode.com/svn/trunk/javascriptguide.xml
* taobao kissy前端编码规范：  
http://docs.kissyui.com/1.4/docs/html/tutorials/style-guide/common-conventions.html

