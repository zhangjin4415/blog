title: jQuery教程
date: 2016-03-30 09:30:00
categories: "jQuery"
tags: "jQuery"
---
主要内容：
说明：本教程使用webstorm和jquery-1.9.1
<!--more-->

第一章 环境搭建
======================
1.jQuery介绍
-------------------
jQuery是一套跨浏览器的JavaScript库，简化HTML与JavaScript之间的操作。它是轻量级的js库 ，兼容CSS3，还兼容各种浏览器。jQuery使用户能更方便地处理HTML documents、events、实现动画效果，并且方便地为网站提供AJAX交互。jQuery还有一个比较大的优势是，它的文档说明很全，而且各种应用也说得很详细，同时还有许多成熟的插件可供选择。jQuery能够使用户的html页面保持代码和html内容分离，也就是说，不用再在html里面插入一堆js来调用命令了，只需定义id即可。

2.环境搭建
--------------------
下载jQuery文件库：
http://jquery.com
或者
http://www.jq22.com/jquery-info122
下载完jQuery框架文件后，不需要安装，使用script文件导入标记，将jQuery框架文件导入页面中即可，在页面的head中加入如下代码：
```
<script language="javascript" type="text/javascript" src="文件目录/jquery.js"></script>
```
加入上述代码后，便完成了jQuery框架开发环境的搭建。

3.JavaScript与jQuery关系
----------------------
jQuery本身就是JavaScript，只不过是把JavaScript代码包装成拿过来就能实现特定功能的代码库！我们想改变页面中所有段落标签<p>中的文本内容：
javaScript代码：
```
var page_p = document.getElementsByTagName("p");
for(var i=0;i<page_p.length;i++){
	page_p[i].innerHTML="改变后的内容";
}
```
jQuery代码：
```
$("p").html("改变后的内容");
```
以上两段代码完成的功能是一样的。jQuery更加的简洁方便，我们在处理DOM时不必关心功能的实现细节。    
$()就是jQuery中的函数，它的功能是获得（）中指定的标签元素。如示例中$(“p”)会得到一组P标签元素,其中“p”表示CSS中的标签选择器。$()中的()不一定是指定元素，也可能是函数。
在jQuery中 $()方法等价于jQuery()方法,前者比较常用，是后者的简写。一般只有在$()与其它语言冲突时才会使用jQuery()方法。

4.应用实例
----------------
用webstorm新建一个项目Test,新建index.html、style.css,导入jquery.js
![image](img/jquery/1.png)
index.html
```
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <title>初识jQuery</title>
    <script src="jquery.js" type="text/javascript"></script>
    <link href="style.css" rel="stylesheet" type="text/css" />
</head>

<body>
<div id="test">初识jQuery</div><!-- test标签在css中设置属性 -->
<button onclick="sayHello()">点我</button><!-- 方法调用 -->

<script type="text/javascript">
    function sayHello(){//方法定义
        $("#test").show();
    }
</script>
</body>
</html>
```
style.css
```
#test{
    display:none;
    width:100px;
    height:40px;
    border:2px solid red;<!-- 边框 -->
}
```
运行结果:
![image](img/jquery/2.png)
点击按钮如下：
![image](img/jquery/3.png)


第二章 jQuery选择器
======================
1.基础选择器
----------------------
(1)#id
通过一个id号去查找一个元素，使用格式： $("#选择的id")。
```
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <title>#id选择器</title>
    <script src="jquery.js" type="text/javascript"></script>
</head>

<body>
<div id="my_id1">div内容1</div>
<div id="my_id2">div内容2</div>
<script type="text/javascript">
    $("#my_id2").html($("#my_id1").html());//将my_id2处内容设置成与my_id1相同 $("#my_id1").html()获得my_id1处内容
</script>
</body>
</html>
```
运行:
![image](img/jquery/4.png)

(2)element选择器
jQuery中可以根据元素名/element（<div>、<span>等）查找元素，格式如下：
$("element")
```
<body>
<button id="btn">点我</button>
<div id="my_id">div显示</div>
<script type="text/javascript">
	$("div").css("font-weight","bold");//将div中内容字体加粗
    $("button").attr("disabled","true");//将按钮设置为灰色(不可以点击)
</script>
</body>
```

(3).class 选择器
可以通过类别（class）属性查找元素。调用格式如下：
$(".class")
style.css
```
.red{ color:red;}
.green{ color:green;}
```
index.html
```
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <title>.class选择器</title>
    <script src="jquery.js" type="text/javascript"></script>
    <link href="style.css" rel="stylesheet" type="text/css" />
</head>

<body>
<div class="red" id="div_id">我是红色</div>
<div class="green">我是绿色</div>
<p></p>

<script type="text/javascript">
    var $className=$("#div_id").attr("class");//调用元素的attr()方法获取元素的类别名-----attr()函数
    $("p").html($className);//标签p位置显示.red类的类名
    var $redHTML = $(".red").html();
    $(".green").html($redHTML);
</script>
</body>
</html>
```
运行结果:
![image](img/jquery/5.png)

(4)* 选择器
“*”号选择器，它的功能是获取页面中的全部元素，包括head、body、script这些元素,格式为：
```
$("*")
```
由于该选择器的特殊性，它常与其他元素组合使用，表示获取其他元素中的全部子元素。
```
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <title>*选择器</title>
    <script src="http://libs.baidu.com/jquery/1.9.0/jquery.js" type="text/javascript"></script>
</head>
<body>
<form action="#">
    <input id="Button1" type="button" value="button" />
    <input id="Text1" type="text" />
    <input id="Radio1" type="radio" />
    <input id="Checkbox1" type="checkbox" />
</form>

<div>
    <span></span>
    <p></p>
    <label></label>
</div>


<script type="text/javascript">
    $("form *").attr("disabled", "true");//设置form下所有子标签为灰色 不可以
    $("div *").html("div *选择器");//设置div下所有子标签显示内容"div *选择器"
</script>
</body>
</html>
```
运行结果:
![image](img/jquery/6.png)

(5)sele1,sele2,seleN选择器
精确的选择任意多个指定的元素,调用格式如下：
```
$("sele1,sele2,seleN")
```
每个选择器之间用“，”号隔开，它们可以是之前提及的各种类型选择器，如$("#id")、$(".class")、$("selector")选择器等。
```
<div class="red">red</div>
<div class="green">green</div>
<div id="blue">blue</div>

<script type="text/javascript">
    $(".red,.green,#blue").html("我们是红绿蓝");//全部标签内容设置成指定值
</script>
```

(6)ance desc选择器
层次性选择器可以快速定位某一层次的一个或多个元素，ance desc选择器就是其中之一，格式如下：
```
$("ance desc")
```
ance desc是使用空格隔开的两个参数。ance参数（ancestor祖先的简写）表示父元素；desc参数（descendant后代的简写）表示后代元素，即包括子元素、孙元素等等。两个参数都可以通过选择器来获取。
index.html
```
 <!DOCTYPE html>
 <html>
 <head>
     <meta charset="utf-8"/>
     <title>ance desc选择器</title>
     <script src="jquery.js" type="text/javascript"></script>
     <link href="style.css" rel="stylesheet" type="text/css" />
 </head>

<body>
<div>宽度随着文字增加而增加
    <p>
        <label></label>
    </p>
    <label></label>
</div>
<script type="text/javascript">
    $("div label").css("background-color","red");//将div下所有label标签背景色改为red
</script>
</body>
</html>
```
style.css
```
div, p, label
{
    float: left;
    border: solid 1px #666;
    margin: 5px;
    padding: 5px;
}
label
{
    width: 20px;
    height:20px
}
```
运行:
![image](img/jquery/7.png)

(7)parent > child选择器
与ance desc选择器相比，parent > child选择器的范围要小些，child参数获取的元素都是parent选择器的子元素,它所选择的目标是子集元素，相当于一个家庭中的子辈们，但不包括孙辈，格式如下：
$("parent > child")

(8)prev + next选择器
通过prev + next选择器就可以查找与“prev”元素紧邻的下一个“next”元素，格式如下：
```
$("prev + next")
```
其中参数prev为任何有效的选择器，参数“next”为另外一个有效选择器
```
$("p+span")//选择p后面的第一个span
```

(9)prev ~ siblings选择器
与prev + next层次选择器相同，prev ~ siblings选择器也是查找prev 元素之后的相邻元素，但前者只获取第一个相邻的元素，而后者则获取prev 元素后面全部相邻的元素，格式如下：
```
$("prev ~ siblings")
```
siblings选择器获取的元素都是prev元素之后的同辈元素。
```
<body>
    <div>
        <label></label>
        <p></p>
        <label></label>
        <label></label>
    </div>
    <label></label>
    <script type="text/javascript">
        $("p ~ label").css("border", "solid 1px red");//选中p后面的两个label
   </script>
</body>
```

2.过滤选择器
-------------------
(1):first :last过滤选择器
过滤选择器是根据某过滤规则进行元素的匹配，书写时以“：”号开头,通常用于查找集合元素中的某一位置的单个元素。
:first :last得到一组相同标签元素中的第1个和最后一个元素
```
<body>
    <div>:first，:last过滤器</div>
    <ol>
        <li>葡萄</li>
        <li>香蕉</li>
        <li>橘子</li>
        <li>西瓜</li>
        <li>苹果</li>
    </ol>
    
    <script type="text/javascript">
        $("li:first").css("background-color", "green");//葡萄背景绿色
        $("li:last").css("background-color","red")//苹果背景红色
    </script>
</body>
```

(2):eq(index)过滤选择器
从一组标签元素数组中，灵活选择任意的一个标签元素，使用格式
:eq(index)
其中参数index表示索引号（即：一个整数），它从0开始，如果index的值为3，表示选择的是第4个元素。
```
<body>
    <div>:eq(index)过滤选择器</div>
    <ol>
    <li>橘子</li>
    <li>香蕉</li>
    <li>葡萄</li>
    <li>苹果</li>
    <li>西瓜</li>
    </ol>  
    <script type="text/javascript">
        $("li:eq(3)").css("background-color", "#60F");//改变苹果背景颜色
    </script>
</body>
```

(3):contains(text)过滤选择器
:contains(text)选择器按照文本内容来查找一个或多个元素，它的功能是选择包含指定字符串的全部元素，它通常与其他元素结合使用，获取包含“text”字符串内容的全部元素对象。其中参数text表示页面中的文字。
```
<body>
    <div>:contains(text)过滤选择器</div>
    <ol>
        <li>强大的"jQuery"</li>
        <li>"javascript"也很实用</li>
        <li>"jQuery"前端必学</li>
        <li>"java"是一种开发语言</li>
        <li>前端利器——"jQuery"</li>
    </ol>
    
    <script type="text/javascript">
        $("li:contains('jQuery')").css("background", "green");//改变包含"jQuery"字符内容的背景色
    </script>
</body>
```

(4):has(selector)过滤选择器
:has(selector)获取选择器中包含指定元素名称的全部元素，其中selector参数就是包含的元素名称，是被包含元素。
```
<body>
    <div>:has(selector)过滤选择器</div>
    <ol>
        <li><p>aa</p></li>
        <li><label>bb</label></li>
        <li><p>cc</p></li>
        <li><label>dd</label></li>
        <li><p>ee</p></li>
    </ol>
    
     <script type="text/javascript">
        $("li:has('p')").css("background-color", "blue");//带有p标签的aa,cc,ee背景色改变
    </script>
</body>
```

(5):hidden过滤选择器
:hidden过滤选择器的功能是获取全部不可见的元素，这些不可见的元素中包括type属性值为hidden的元素。
```
<body>
    <h3>显示隐藏元素的内容</h3>
    <input id="hidstr" type="hidden" value="我已隐藏起来"/>
    <div></div> 
    <script type="text/javascript">
    var $strHTML = $("input:hidden").val();
    $("div").html($strHTML);//显示“我已隐藏起来”
</script>
</body>
```

(6):visible过滤选择器
:visible过滤选择器获取的是全部可见的元素，也就是说，只要不将元素的display属性值设置为“none”，那么，都可以通过该选择器获取。
```
<body>
    <h3>:visible过滤选择器</h3>
    <ul>
        <li style="display:none">橘子</li><!-- 不显示 -->
        <li style="display:block">香蕉</li>
        <li style="display:">葡萄</li>
        <li>苹果</li>
        <li style="display:none">西瓜</li>
    </ul>
    
    <script type="text/javascript">
        $("li:visible").css("background-color","blue");//显示的香蕉，葡萄，苹果背景色都blue
    </script>
</body>
```

(7)[attribute=value]与[attribute!=value]属性选择器
[attribute=value]属性选择器的功能是获取与属性名和属性值完全相同的全部元素，其中[]是专用于属性选择器的括号符，参数attribute表示属性名称，value参数表示属性值。[attribute!=value]与[attribute=value]正好相反！
```
<body>
    <h3>[attribute=value]属性选择器</h3>
    <ul>
        <li title="蔬菜">茄子</li>
        <li title="水果">香蕉</li>
        <li title="蔬菜">芹菜</li>
        <li title="水果">苹果</li>
        <li title="水果">西瓜</li>
    </ul>
    
    <script type="text/javascript">
        $("li[title='蔬菜']").css("background-color", "green");//改变"title"属性值为"蔬菜"的背景颜色
    </script>
</body>
```

(8)[attribute*=value]属性选择器
获取属性值中包含指定内容的全部元素，其中[]是专用于属性选择器的括号符，参数attribute表示属性名称，value参数表示对应的属性值。
```
<body>
    <h3>attribute*=value]属性选择器</h3>
    <ul>
        <li title="蔬菜">茄子</li>
        <li title="水果">香蕉</li>
        <li title="蔬菜">芹菜</li>
        <li title="人参果">小西红柿</li>
        <li title="水果">西瓜</li>
    </ul>
    
    <script type="text/javascript">
        $("li[title*='果']").css("background-color", "green");//改变"title"属性值包含"果"的背景色
    </script>
</body>
```

(9):first-child与:last-child子元素过滤选择器
:first过滤选择器可以获取指定父元素中的首个子元素，但该选择器返回的只有一个元素，并不是一个集合，而使用:first-child子元素过滤选择器则可以获取每个父元素中返回的首个子元素，它是一个集合，常用多个集合数据的选择处理。
:last-child获取每个父元素中返回的最后一个子元素，它也是一个集合，常用多个集合数据的选择处理。
```
<body>
    <h3>改变每个"蔬菜水果"中第一行的背景色</h3>
    <ol>
        <li>芹菜</li>
        <li>茄子</li>
        <li>萝卜</li>
        <li>大白菜</li>
        <li>西红柿</li>
    </ol>
    <ol>
        <li>橘子</li>
        <li>香蕉</li>
        <li>葡萄</li>
        <li>苹果</li>
        <li>西瓜</li>
    </ol>
    
    <script type="text/javascript">
        $("li:first-child").css("background-color", "green");//改变每个"蔬菜水果"中第一行的背景色--芹菜，橘子
    </script>
</body>
```

(10)练习
开始显示1,2,3,4,5和更多
点击更多显示到8，点击简化恢复显示1,2,3,4,5.
```
<!DOCTYPE html>
<html>
    <head>
        <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
        <title>挑战题</title>
    </head>  
    <body>
    <ul>
    <li>1</li><li>2</li><li>3</li><li>4</li><li>5</li>
    <li class="no" style="display:none">6</li><li class="no" style="display:none">7</li><li class="no" style="display:none">8</li><a href="#">更多</a>
       <script src="http://libs.baidu.com/jquery/1.9.0/jquery.js" type="text/javascript"></script>
    <script>
        $(function(){
            $("a").click(function(){
                var text = $("a").text();
                if(text == "更多"){
                    $("a").html("简化");
                    $("li[class=no]").show();
                }else{
                    $("a").html("更多");
                    $("li[class=no]").hide();
                }
            });
        });
    </script>
    </ul>
        
    </body>
</html>
```

3.表单选择器
-------------
(1):input表单选择器
:input表单选择器返回全部的表单元素，不仅包括所有input标记的表单元素，而且还包括textarea、select 和 button标记的表单元素，因此，它选择的表单元素是最广的。
style.css
```
.bg_blue
{
    background-color: blue;
}
```
html
```
<body>
    <h3>修改全部表单元素的背景色</h3>
    <form id="frmTest" action="#">
    <input type="button" value="Input Button" /><br />
    <select>
        <option>Option</option>
    </select><br />
    <textarea rows="3" cols="8"></textarea><br />
    <button>
        Button</button><br />
    </form>
    
    <script type="text/javascript">
        $("#frmTest :input").addClass("bg_blue");
    </script>
</body>
```
![image](img/jquery/8.png)

(2):text表单文本选择器
获取表单中全部单行的文本输入框元素，单行的文本输入框就像一个不换行的字条工具
```
<body>
    <h3>修改多个单行输入框元素的背景色</h3>
    <form id="frmTest" action="#">
    <input type="text" id="Text1" value="我是小纸条"/><br />
    <textarea rows="3" cols="8"></textarea><br />
    <input id="Text2" value="我也是小纸条"/><br />
    <button>
        Button</button><br />
    </form>
    
    <script type="text/javascript">
        $("#frmTest :text").addClass("bg_blue");//两个input标签的背景色改变 对于<textarea>区域文本、按钮元素无效
    </script>
</body>
```
备注:
```
:text对<input type="password" id="Text2" value="我也是小纸条"/><br />无效
```

(3):password表单密码选择器
:password选择器，它的功能是获取表单中全部的密码输入文本框元素。
```
<body>
    <h3>修改多个密码输入框元素的背景色</h3>
    <form id="frmTest" action="#">
    <input type="text" id="Text1" value="单行文本输入框"/><br />
    <input type="password" id="Text2" value="密码文本输入框"/><br />
    <textarea rows="3" cols="8">区域文本输入框</textarea><br />
    <input type="password" id="Text3" value=""/><br />
    <button>
        Button</button><br />
    </form>
    
    <script type="text/javascript">
        $("#frmTest :password").addClass("bg_red");//type="password"的两个input框背景色改变
    </script>
</body>
```

(4):radio单选按钮选择器
使用:radio选择器可轻松获取表单中的全部单选按钮元素。
```
<body>
    <h3>将表单中单选按钮设为不可用</h3>
    <form id="frmTest" action="#">
    <input type="button" value="Input Button" /><br />
    <input id="Radio1" type="radio" />
    <label for="Radio1">
        男</label>
    <input id="Radio2" type="radio" />
    <label for="Radio2">
        女</label><br />
    <button>
        Button</button><br />
    </form>
    
    <script type="text/javascript">
        $("#frmTest :radio").attr("disabled","true");//type="radio"的两个input不可以，变成灰色
    </script>
</body>
```

(5):checkbox复选框选择器
:checkbox选择器可以快速定位并获取表单中的复选框元素。
```
<body>
    <h3>将表单的全部复选框设为不可用</h3>
    <form id="frmTest" action="#">
    <input type="button" value="Input Button" /><br />
    <input id="Checkbox1" type="checkbox" />
    <label for="Checkbox1">
        西红柿</label><br />
    <input id="Checkbox2" type="checkbox" />
    <label for="Checkbox2">
        茄子</label><br />
    <input id="Checkbox3" type="checkbox" />
    <label for="Checkbox3">
        黄瓜</label><br />
    <button>
        Button</button><br />
    </form>
    
    <script type="text/javascript">
        $("#frmTest :checkbox").attr("disabled","true");//type="checkbox"的复选框不可用
    </script>
</body>
```

(6):submit提交按钮选择器
通常情况下，一个表单中只允许有一个“type”属性值为“submit”的提交按钮，使用:submit选择器可获取表单中的这个提交按钮元素。
style.css
```
.bg_red
{
    background-color: blue;
    color:Orange;
}
```
html
```
<body>
    <h3>修改表单中提交按钮的背景色</h3>
    <form id="frmTest" action="#">
    <input type="button" value="Input Button" /><br />
    <input type="submit" value="点我就提交了" /><br />
    <button>
        Button</button><br />
    </form>
    
    <script type="text/javascript">
        //$("#frmTest submit").addClass("bg_red");无效
        $("#frmTest input:submit").addClass("bg_red");//设置type="submit"的input标签(按钮)背景色
        $("#frmTest input:submit").attr("value","提交");//更改显示内容
    </script>
</body>
```

(7):image图像域选择器
当一个input元素的“type”属性值设为“image”时，该元素就是一个图像域，使用:image选择器可以快速获取该类全部元素。
使用:image选择器只能获取input图像域，而不能获取img格式的图像元素。
style.css
```
.bg_green
{
    background-color: green;
    width:159px;
    height:42px;
    padding:20px;
}
```
html
```
<body>
    <h3>修改表单中图像元素的背景色</h3>
    <form id="frmTest" action="#">
    <input type="image" src="http://img.mukewang.com/52b284ea00016b2902590070.jpg" /><br />
    <br />
    <img alt="" src="http://img.mukewang.com/52b284ea00016b2902590070.jpg" /><br />
    </form>
    
    <script type="text/javascript">
        $("#frmTest :image").addClass("bg_green");
    </script>
</body>
```
![image](img/jquery/9.png)

(8):button表单按钮选择器
表单中包含许多类型的按钮，而使用:button选择器能获取且只能获取“type”属性值为“button”的input和button这两类普通按钮元素。
```
<body>
    <h3>修改表单中按钮元素的背景色</h3>
    <form id="frmTest" action="#">
        <input id="Button1" type="button" value="我是普通按钮" /><br />
        <input id="Submit1" type="submit" value="点我就提交" /><br />
        <button> 我也是普通按钮 </button><br />
    </form>

    <script type="text/javascript">
        $("#frmTest :button").addClass("bg_blue");
    </script>
</body>
```
![image](img/jquery/10.png)

(9):checked选中状态选择器
有一些元素存在选中状态，如复选框、单选按钮元素，选中时“checked”属性值为“checked”，调用:checked可以获取处于选中状态的全部元素。
```
<body>
    <h3>将处于选中状态的元素设为不可用</h3>
    <form id="frmTest" action="#">
    <input id="Radio1" type="radio" checked="checked" />
    <label id="Label1" for="Radio1">
        苹果</label><br />
    <input id="Radio2" type="radio" />
    <label id="Label2" for="Radio2">
        桔子</label><br />
    <input id="Checkbox1" type="checkbox" checked="checked" />
    <label id="Label3" for="Checkbox1">
        荔枝</label><br />
    <input id="Checkbox2" type="checkbox" />
    <label id="Label4" for="Checkbox2">
        葡萄</label><br />
    <input id="Checkbox3" type="checkbox" checked="checked" />
    <label id="Label5" for="Checkbox3">
        香蕉</label><br />
    </form>
    
    <script type="text/javascript">
        $("#frmTest :checked").attr("disabled", true);
    </script>
</body>
```
![image](img/jquery/11.png)

(10):selected选中状态选择器
与:checked选择器相比，:selected选择器只能获取select下拉列表框中全部处于选中状态的option选项元素。
```
<body>
    <h3>获取处于选中状态元素的内容</h3>
    <form id="frmTest" action="#">
    <select id="Select1" multiple="multiple">
        <option value="0">苹果</option>
        <option value="1" selected="selected">桔子</option>
        <option value="2">荔枝</option>
        <option value="3" selected="selected">葡萄</option>
        <option value="4">香蕉</option>
    </select><br /><br />
    <div id="tip"></div>
    </form>
    
    <script type="text/javascript">
        var $txtOpt = $("#frmTest :selected").text();
        $("#tip").html("选中内容为:" + $txtOpt);
    </script>
</body>
```
![image](img/jquery/12.png)

第三章 操作DOM元素
========================
1.使用attr()方法控制元素的属性
-----------------------
attr()方法的作用是设置或者返回元素的属性，其中attr(属性名)格式是获取元素属性名的值，attr(属性名，属性值)格式则是设置元素属性名的值。
```
<body>
    <h3>attr()方法设置元素属性</h3>
    <a href="http://127.0.0.1" id="a1">点我就变</a>
    <div>我改变后的地址是：<span id="tip"></span></div>   
    <script type="text/javascript">
        $("#a1").attr("href" , "best.com");//将href设置成best.com
        var $url = $("#a1").attr("href");//获取id=a1的href属性的值
        $("#tip").html($url);//id=tip设置值为$url
    </script>
</body>
```

2.操作元素的内容
-------------------
使用html()和text()方法操作元素的内容，当两个方法的参数为空时，表示获取该元素的内容，而如果方法中包含参数，则表示将参数值设置为元素内容。
html()方法可以获取元素的HTML内容，因此，原文中的格式代码也被一起获取，而text()方法只是获取元素中的文本内容，并不包含HTML格式代码
```
    <body>
        <h3>html()和text()方法设置元素内容</h3>
        <div id="html"></div>
        <div id="text"></div>
        <div id="html_2"></div>
        <div id="text_2"></div>
        
        <script type="text/javascript">
            var $content = "<b>唉，我又变胖了！</b>";
            $("#html").html($content);
            $("#text").text($content);
            $("#html_2").html($("h3").html());
            $("#text_2").text($("h3").text());
        </script>
    </body>
```
![image](img/jquery/13.png)

3.操作元素的样式
----------------
通过addClass()和css()方法可以方便地操作元素中的样式，前者括号中的参数为增加元素的样式名称，后者直接将样式的属性内容写在括号中。
```
<html>
    <head>
        <title>操作元素样式</title>
        <script src="jquery.js" type="text/javascript"></script>
        <link href="style.css" rel="stylesheet" type="text/css" />
        <style type="text/css"><!-- blue -->
            .blue
            {
             background-color:Blue;
             color:White;
            }
        </style>
    </head>
    
    <body>
        <h3>css()方法设置元素样式</h3>
        <div id="content">我穿了一件红色外衣</div>
        <p>addClass方法</p>
        
        <script type="text/javascript">
            $("#content").css({"background-color":"#ff0000","color":"White"});
            $("p").addClass("blue");
        </script>
    </body>
</html>
```
![image](img/jquery/14.png)

4.移除属性和样式
------------------
使用removeAttr(name)和removeClass(class)分别可以实现移除元素的属性和样式的功能，前者方法中参数表示移除属性名，后者方法中参数则表示移除的样式名。
style.css
```
div
{
    padding: 8px;
    width: 180px;
}
.blue
{
    background-color: Blue;
}
.white
{
    color: White;
}
```
html
```
<body>
    <h3>removeClass()方法移除元素样式</h3>
    <div id="content"class="blue white">我脱下了一件蓝色外衣</div>
    <a href="localhost"></a>
    <div id="div_1"></div>
    <div id="div_2"></div>
    
    <script type="text/javascript">
        $("#content").removeClass("blue white");
        var $var1=$("a").attr("href");
        $("#div_1").html($var1);
        $("a").removeAttr("href");
        $var1=$("a").attr("href");
        $("#div_2").html($var1);
    </script>
</body>
```
![image](img/jquery/15.png)

5.使用append()方法向元素内追加内容
--------------------
append(content)方法的功能是向指定的元素中追加内容，被追加的content参数，可以是字符、HTML元素标记，还可以是一个返回字符串内容的函数。
```
<body>
    <h3>append()方法追加内容</h3>
    <p>hello </p>
    
    <script type="text/javascript">
        function rethtml() {
            var $html = "<div id='test' title='hi'>我是调用函数创建的</div>"
            return $html;
        }
        $("body").append(rethtml());//向页面追加div（我是调用函数创建的）
        $("p").append("你好");//向p标签追加内容
    </script>
</body>
```

6.使用appendTo()方法向被选元素内插入内容
---------------------
appendTo()方法也可以向指定的元素内插入内容，它的使用格式是：
```
$(content).appendTo(selector)
```
参数content表示需要插入的内容，参数selector表示被选的元素，即把content内容插入selector元素内，默认是在尾部。
```
<body>
    <h3>appendTo()方法插入内容</h3>
    <div>
        <span class="green">小乌龟</span>
    </div>
    <span class="blue">小兔子</span>
    
    <script type="text/javascript">
    //注意：class用''
        var $html = "<span class='red'>小青蛙</span>"
        $($html).appendTo("div");//$html追加到div
        var $hh="<span class='blue'>小小</span>";//这是值；添加下面代码只会追加小兔子一行,不会追加这行
       // $(".blue").appendTo("div");
    </script>
</body>
```
![image](img/jquery/16.png)
去掉如下行的注释后
```
// $(".blue").appendTo("div");
```
![image](img/jquery/17.png)

7.使用before()和after()在元素前后插入内容
---------------------
使用before()和after()方法可以在元素的前后插入内容，它们分别表示在整个元素的前面和后面插入指定的元素或内容，调用格式分别为：
$(selector).before(content)和$(selector).after(content)
```
<body>
    <h3>after()方法在元素之后插入内容</h3>
    <span class="green">我们交个朋友吧！</span>
    <p>追加后.green的全部内容:</p>
    <div></div>
    <script type="text/javascript">
        var $html = "<span class='red'>兄弟。</span>"
        $(".green").before("你好啊！");//前面加
        $(".green").after($html);//后面加
        $("div").html($(".green").html());//.green内容没变
    </script>
</body>
```
![image](img/jquery/18.png)

8.使用clone()方法复制元素
---------------------
调用clone()方法可以生成一个被选元素的副本，即复制了一个被选元素，包含它的节点、文本和属性，它的调用格式为：
```
$(selector).clone()
```
其中参数selector可以是一个元素或HTML内容。
```
<body>
    <h3>使用clone()方法复制元素</h3>
    <span class="red" title="hi">我是美猴王</span>
    
    <script type="text/javascript">
        $("body").append($(".red").clone());
    </script>
</body>
```
![image](img/jquery/19.png)

9.替换内容
---------------
replaceWith()和replaceAll()方法都可以用于替换元素或元素中的内容。
********************************
调用时，内容和被替换元素所在的位置不同：
```
$(selector).replaceWith(content)$(content).replaceAll(selector)
```
参数selector为被替换的元素，content为替换的内容。
使用replaceWith()方法替换之后，旧元素完全由新替换的元素所取代。
```
<body>
    <h3>使用replaceAll()方法替换元素内容</h3>
    <span class="green" title="hi">原内容1</span>
    <span class="red" title="hi">原内容2</span>
    <p>原内容3</p>
    <script type="text/javascript">
        var $html = "<span class='red' title='hi'>替换内容</span>"; 
        $(".green").replaceWith($html);
        $($html).replaceAll(".red");
        //$("nihao").replaceAll($("p"));//不能替换内容
        $("p").html("替换标签p的内容");
    </script>
</body>
```
![image](img/jquery/20.png)

10.使用wrap()和wrapInner()方法包裹元素和内容
--------------------
wrap()和wrapInner()方法都可以进行元素的包裹，但前者用于包裹元素本身，后者则用于包裹元素中的内容，它们的调用格式分别为：
```
$(selector).wrap(wrapper)
$(selector).wrapInner(wrapper)
```
参数selector为被包裹的元素，wrapper参数为包裹元素的格式。
style.css
```
span
{color: White;padding: 8px;}
.red
{background-color: Red;}
div
{border:2px solid #00ff00}
```
html
```
<body>
    <h3>使用wrapInner()方法包裹元素</h3>
    <span class="red" title='hi'>我的身体有点歪</span>
    <p>我被div包围了</p>
    <script type="text/javascript">
        $(".red").wrapInner("<i></i>");
        $("p").wrap("<div></div>");
    </script>
</body>
```
![image](img/jquery/21.png)

11.使用each()方法遍历元素
-------------------
each()方法可以遍历指定的元素集合，在遍历时，通过回调函数返回遍历元素的序列号，调用格式为：
```
$(selector).each(function(index))
```
参数function为遍历时的回调函数，index为遍历元素的序列号，它从0开始。
```
<body>
    <h3>使用each()方法遍历元素</h3>
    <span class="green">香蕉</span>
    <span class="green">桃子</span>
    <span class="green">葡萄</span>
    <span class="green">荔枝</span>
    
    <script type="text/javascript">
        $("span").each(function (index) {
            if (index == 1) {
                $(this).attr("class", "red");
            }
        });
    </script>
</body>
```
![image](img/jquery/22.png)

12.使用remove()和empty()方法删除元素
-----------------------
remove()方法删除所选元素本身和子元素，该方法可以通过添加过滤参数指定需要删除的某些元素，而empty()方法则只删除所选元素的子元素。
```
<body>
    <h3>使用empty()方法删除元素</h3>
    <span class="green">香蕉</span>
    <span class="red">桃子</span>
    <span class="green">葡萄</span>
    <span class="red">荔枝</span>
    <div>p1</div>
    <div>p2</div>        
    <script type="text/javascript">
    $("span").remove(".red");
    $("div").empty();
    </script>
</body>
```
移除前：
![image](img/jquery/23.png)
移除后：
![image](img/jquery/24.png)

第四章 jQuery事件
=======================
1.页面加载时触发ready()事件
----------------
ready()事件类似于onLoad()事件，但前者只要页面的DOM结构加载后便触发，而后者必须在页面全部元素加载成功才触发，ready()可以写多个，按顺序执行。此外，下列写法是相等的：
```
$(document).ready(function(){})等价于$(function(){});
```
```
<body>
    <h3>页面载入时触发ready()事件</h3>
    <div id="tip"></div>
    <input id="btntest" type="button" value="点下我" />
    <div id="div2"></div>     
    <script type="text/javascript">
        $(function(){
            $("#btntest").bind("click", function () {
                $("#tip").html("我被点击了！");
            });
        });
        $(document).ready(function(){
            $("#div2").html("我被加载了");
        });
    </script>
</body>
```
运行：
![image](img/jquery/25.png)
点击按钮后：
![image](img/jquery/26.png)

2.使用bind()方法绑定元素的事件
-----------------
bind()方法绑定元素的事件非常方便，绑定前，需要知道被绑定的元素名，绑定的事件名称，事件中执行的函数内容就可以，它的绑定格式如下：
```
$(selector).bind(event,[data] function)
```
参数event为事件名称，多个事件名称用空格隔开，function为事件执行的函数。
```
<body>
    <h3>bind()方法绑多个事件</h3>
    <input id="btntest" type="button" value="点击或移出就不可用了" />
    
    <script type="text/javascript">
        $(function () {
            $("#btntest").bind("click mouseout", function () {//点击或者鼠标移出按钮就不可用
                $(this).attr("disabled", "true");
            })
        });
    </script>
</body>
```

3.使用hover()方法切换事件
-------------------
hover()方法的功能是当鼠标移到所选元素上时，执行方法中的第一个函数，鼠标移出时，执行方法中的第二个函数，实现事件的切实效果，调用格式如下：
```
$(selector).hover(over，out);
```
over参数为移到所选元素上触发的函数，out参数为移出元素时触发的函数。
```
<body>
    <h3>hover()方法切换事件</h3>
    <div>鼠标移入时为橘红色，否则没有颜色</div>
    
    <script type="text/javascript">
        $(function () {
            $("div").hover(
            function () {
                $(this).addClass("orange");
            },
            function () {
                $(this).removeClass("orange")
            })
        });
    </script>
</body>
```

4.使用toggle()方法绑定多个函数
--------------------
toggle()方法可以在元素的click事件中绑定两个或两个以上的函数，同时，它还可以实现元素的隐藏与显示的切换，绑定多个函数的调用格式如下：
```
$(selector).toggle(fun1(),fun2(),funN(),...)
```
其中，fun1，fun2就是多个函数的名称
```
<body>
    <h3>toggle()方法绑定多个函数</h3>
    <input id="btntest" type="button" value="点一下我" />
    <div id="div1">我是动态显示的</div>
    <div id="div2">苹果</div>
    
    <script type="text/javascript">
        $(function () {//点击按钮id=div1显示或者隐藏
            $("#btntest").bind("click", function () {
                $("#div1").toggle();//等价show() hide()
            })
        });
        $(function () {//点击id=div2时顺序切换苹果，香蕉，葡萄
           $("#div2").toggle(
               function(){
                 $(this).html("香蕉");
                 },
               function(){
                 $(this).html("葡萄");
                 })
        });
    </script>
</body>
```
运行
![image](img/jquery/27.png)
点击按钮“我是动态显示的”隐藏或者显示切换，点击div2苹果，香蕉，葡萄循环切换
![image](img/jquery/28.png)

5.使用unbind()方法移除元素绑定的事件
----------------
unbind()方法可以移除元素已绑定的事件，它的调用格式如下：
```
$(selector).unbind(event,fun)
```
其中参数event表示需要移除的事件名称，多个事件名用空格隔开，fun参数为事件执行时调用的函数名称。
style.css
```
div
{
    width: 160px;
    border: solid 1px #ccc;
    padding: 8px;
    text-align: center;
}
.color
{
    color: Orange;
}
.backcolor
{
    background-color: Orange;
    color: White;
}
```
html
```
<body>
    <h3>unbind()移除绑定的事件</h3>
    <input id="btntest" type="button" value="移除事件" />
    <div>点击和双击效果不同哦</div>
    
    <script type="text/javascript">
        $(function () {
            ////单击div时文字变橘色
            $("div").bind("click",
            function () {
                $(this).removeClass("backcolor").addClass("color");
                //双击div时背景变橘色
            }).bind("dblclick", function () {
                $(this).removeClass("color").addClass("backcolor");
            })
            //点击按钮移除div使用事件
            $("#btntest").bind("click", function () {
                $("div").unbind();//使用unbind()方法移除已绑定的全部事件。
                $(this).attr("disabled", "true");//按钮（点击后）设置为不可用 此时div保持最近设置的状态
            });
        });
    </script>
</body>
```
备注:$("div").unbind("click");//只是移除点击事件

6.使用one()方法绑定元素的一次性事件
-----------------------
one()方法可以绑定元素任何有效的事件，但这种方法绑定的事件只会触发一次，它的调用格式如下：
```
$(selector).one(event,[data],fun)
```
参数event为事件名称，data为触发事件时携带的数据，fun为触发该事件时执行的函数。
```
<body>
    <h3>one()方法执行一次绑定事件</h3>
    <div>请点击我一下</div>
    <p>div被点击了0次</p>
    
    <script type="text/javascript">
        $(function () {
            var intI = 0;
            $("div").one("click", function () {
                intI++;
                $(this).css("font-size", intI + "px");//div中字体调整
                $("p").html("div被点击了"+intI+"次");//点击一次后显示1次，之后点击再也没有反应
            })
        });
    </script>
</body>
```

7.调用trigger()方法手动触发指定的事件
---------------------
trigger()方法可以直接手动触发元素指定的事件，这些事件可以是元素自带事件，也可以是自定义的事件，该事件必须能执行，调用格式为：
```
$(selector).trigger(event)
```
其中event参数为需要手动触发的事件名称。
style.css
```
div
{
    width: 160px;
    border: solid 1px #ccc;
    padding: 8px;
    text-align: center;
}
.color
{
    color: Orange;
}
```
html
```
<body>
    <h3>trigger()手动触发事件</h3>
    <input type="text" value="请输入姓名"/>
    <div>我一开始就是橘色</div>
    
    <script type="text/javascript">
    //指定输入框默认为选中状态(select事件)
        $(function(){
           $("input").trigger("select");
            });
            
    //自定义事件
        $(function () {
            //指定change-color事件与其函数
            $("div").bind("change-color", function () {
                $(this).addClass("color");
            });
            //调用自定义的change-color函数
            $("div").trigger("change-color");
        });
    </script>
</body>
```
![image](img/jquery/29.png)

8.文本框的focus和blur事件
--------------------
focus事件在元素获取焦点时触发，如点击文本框时，触发该事件；而blur事件则在元素丢失焦点时触发，如点击除文本框的任何元素，都会触发该事件。
```
<body>
    <h3>表单中文本框的focus和blur事件</h3>
    <input id="txtest" type="text" value="" />
    <div></div>
    
    <script type="text/javascript">
        $(function () {
            $("input")
            .bind("focus", function () {//点击框时
                $("div").html("请输入您的姓名！");
            })
            .bind("blur", function () {//移出框点击其他地方
                if ($(this).val().length == 0)
                    $("div").html("你的名称不能为空！");
            })
        });
    </script>
</body>
```
![image](img/jquery/30.png)

9.下拉列表框的change事件
---------------------
当一个元素的值发生变化时，将会触发change事件，例如在选择下拉列表框中的选项时，就会触change事件。
```
<body>
    <h3>下拉列表的change事件</h3>
    <select id="seltest">
        <option value="葡萄">葡萄</option>
        <option value="苹果">苹果</option>
        <option value="荔枝">荔枝</option>
        <option value="香焦">香焦</option>
    </select>
    
    <script type="text/javascript">
        $(function () {
            $("#seltest").bind("change",function () {
                //选中苹果时背景色红色，否则绿色
                if ($(this).val() == "苹果")
                    $(this).css("background-color", "red");
                else
                    $(this).css("background-color", "green");
            })
        });
    </script>
</body>
```
![image](img/jquery/31.png)

10.调用live()方法绑定元素的事件
-----------------
与bind()方法相同，live()方法与可以绑定元素的可执行事件，除此相同功能外，live()方法还可以绑定动态元素，即使用代码添加的元素事件，格式如下：
```
$(selector).live(event,[data],fun)
```
参数event为事件名称，data为触发事件时携带的数据，fun为触发该事件时执行的函数。
```
<body>
    <h3>live()方法绑多个事件</h3>
    
    <script type="text/javascript">
   // 使用live()方法绑定，页面中按钮元素的单击事件，而这个按钮是通过追加的方式添加至页面的。
   //点击或移出按钮，按钮就变灰色不可用
        $(function () {
            $("#btntest").live("click", function () {//点击事件
                $(this).attr("disabled", "true");
            })
            $("#btntest").live("mouseout", function () {//移出事件
                $(this).attr("disabled", "true");
            })
            $("body").append("<input id='btntest' type='button' value='点击或移出就不可用了' />");
        });
    </script>
</body>
```
备注:以上代码可以简化为$("#btntest").live("click mouseout", function () {}...

第五章  jQuery 动画特效
==============
1.调用show()和hide()方法显示和隐藏元素
---------------
show()和hide()方法用于显示或隐藏页面中的元素，调用格式分别为：
```
$(selector).hide(speed,[callback])
$(selector).show(speed,[callback])
```
参数speed设置隐藏或显示时的速度值，可为“slow”、“fast”或毫秒数值，可选项参数callback为隐藏或显示动作执行完成后调用的函数名。
```
<body>
    <h3>使用show()和hide()方法显示和隐藏元素</h3>
    <div>
        <h4>我喜欢吃的水果</h4>
        <ul>
            <li>苹果</li>
            <li>甘桔</li>
            <li>梨</li>
        </ul>
        <input id="hidval" type="hidden" value="0"/>
    </div>
    
    <script type="text/javascript">
        $(function () {
            //通过点击h4实现ul表的隐藏与显示
            $("h4").bind("click", function () {
                if ($("#hidval").val() == 0) {
                    $("ul").show();
                    $("#hidval").val(1);
                } else {
                    $("ul").hide();
                    $("#hidval").val(0);
                }
            });
        });
    </script>
</body>
```

2.show()和hide()方法的动画效果
---------------
show()和hide()增加“speed”参数可以实现动画效果的显示与隐藏，同时，如果添加了方法的回调函数，它将在显示或隐藏执行成功后被调用。
```
<body>
    <h3>show()和hide()方法动画方式显示和隐藏元素</h3>
    <div>
        <h4>我喜欢吃的水果</h4>
        <ul>
            <li>苹果</li>
            <li>甘桔</li>
            <li>梨</li>
        </ul>
        <input id="hidval" type="hidden" value="0"/>
    </div>
    
    <script type="text/javascript">
        $(function () {
            $("h4").bind("click", function () {
                if ($("#hidval").val() == 0) {
                    //缓慢的展开ul列表
                    $("ul").show(1500,function(){//1500（ms）也可以用"slow"
                        $("#hidval").val(1);
                    })
                } else {
                    //快速地收起ul表
                    $("ul").hide("fast",function(){
                        $("#hidval").val(0);
                    })
                }
            })
        });
    </script>
</body>
```

3.调用toggle()方法实现动画切换效果
---------------------
实现元素的显示与隐藏需要使用hide()与show()，那么有没有更简便的方法来实现同样的动画效果呢？
调用toggle()方法就可以很容易做到，即如果元素处于显示状态，调用该方法则隐藏该元素，反之，则显示该元素，它的调用格式是：
```
$(selector).toggle(speed,[callback])
```
其中speed参数为动画效果时的速度值，可以为数字，单位为毫秒，也可是“fast”、“slow”字符，可选项参数callback为方法执行成功后回调的函数名称。
```
<body>
    <h3>toggle()方法的动画切换效果</h3>
    <div>
        <h4>
           <span class="fl">我喜欢吃的水果</span>
           <span class="fr" id="spnTip">显示</span>
        </h4>
        <ul>
            <li>苹果</li>
            <li>甘桔</li>
            <li>梨</li>
        </ul>
    </div>
    
    <script type="text/javascript">
        $(function () {
            var $spn = $("#spnTip");
            $("h4").bind("click", function () {
                $("ul").toggle(3000,function(){//展开到完全显示时间3s
                 $spn.html() == "隐藏" ? $spn.html("显示") : $spn.html("隐藏");
                })
            });
        });
    </script>
</body>
```
效果：
![image](img/jquery/32.png)
当点击显示时显示列表，文字提示变成隐藏，点击隐藏列表收回。

4.使用slideUp()和slideDown()方法的滑动效果
------------------------
可以使用slideUp()和slideDown()方法在页面中滑动元素，前者用于向上滑动元素，后者用于向下滑动元素，它们的调用方法分别为：
```
$(selector).slideUp(speed,[callback])和$(selector).slideDown(speed,[callback])
```
其中speed参数为滑动时的速度，单位是毫秒，可选项参数callback为滑动成功后执行的回调函数名。
要注意的是：slideDown()仅适用于被隐藏的元素；slideup()则相反。
```
<body>
    <h3>使用slideUp()和slideDown()方法的滑动效果</h3>
    <div>
        <h4>我喜欢吃的水果</h4>
        <ul>
            <li>苹果</li>
            <li>甘桔</li>
            <li>梨</li>
        </ul>
        <input id="hidval" type="hidden" value="0"/>
    </div>
    
    <script type="text/javascript">
        $(function () {
            $("h4").bind("click", function () {
                if ($("#hidval").val() == 0) {
                    $("ul").slideUp(3000,function(){
                        $("#hidval").val(1);
                    })
                } else {
                    $("ul").slideDown(3000,function(){
                        $("#hidval").val(0);
                    })
                }
            })
        });
    </script>
</body>
```
![image](img/jquery/33.png)
点击“我喜欢吃的水果”缓缓下拉显示列表，再点时缓缓上升收起列表。

5.使用slideToggle()方法实现图片“变脸”效果
-------------------------------
使用slideToggle()方法可以切换slideUp()和slideDown()，即调用该方法时，如果元素已向上滑动，则元素自动向下滑动，反之，则元素自动向上滑动，格式为：
```
$(selector).slideToggle(speed,[callback])
```
其中speed参数为动画效果时的速度值，可以为数字，单位为毫秒，也可是“fast”、“slow”字符，可选项参数callback为方法执行成功后回调的函数名称。
```
<body>
    <h3>使用slideToggle()方法切换滑动效果</h3>
    <div>
        <h4>
           <span class="fl">我喜欢吃的水果</span>
           <span class="fr" id="spnTip">向下滑</span></h4>
        <ul>
            <li>苹果</li>
            <li>甘桔</li>
            <li>梨</li>
        </ul>
        <input id="hidval" type="hidden" value="0"/>
    </div>
    
    <script type="text/javascript">
        $(function () {
            var $spn = $("#spnTip");
            $("h4").bind("click", function () {
            $("ul").slideToggle(3000,function(){
           $spn.html() == "向下滑" ? $spn.html("向上滑") : $spn.html("向下滑");
                })
            })
        });
    </script>
</body>
```
运行效果与4中相似，点击h4中内容时显示“向下滑”显示下拉菜单，名称改为“向上滑”，再次点击向上收起。

6.使用fadeIn()与fadeOut()方法实现淡入淡出效果
--------------------------------
fadeIn()和fadeOut()方法可以实现元素的淡入淡出效果，前者淡入隐藏的元素，后者可以淡出可见的元素，它们的调用格式分别为：
```
$(selector).fadeIn(speed,[callback])和$(selector).fadeOut(speed,[callback])
```
其中参数speed为淡入淡出的速度，callback参数为完成后执行的回调函数名。
```
<body>
    <h3>使用fadeIn()与fadeOut()方法实现元素淡入淡出的效果</h3>
    <div>
        <h4>我喜欢吃的水果</h4>
        <ul>
            <li>苹果</li>
            <li>甘桔</li>
            <li>梨</li>
        </ul>
        <input id="hidval" type="hidden" value="0"/>
    </div>
    
    <script type="text/javascript">
        $(function () {
            $("h4").bind("click", function () {
                if ($("#hidval").val() == 0) {
                    $("ul").fadeOut(3000,function(){
                        $("#hidval").val(1);
                    })
                } else {
                    $("ul").fadeIn(3000,function(){
                        $("#hidval").val(0);
                    })
                }
            })
        });
    </script>
</body>
```
![image](img/jquery/34.png)
点击h4时淡入淡出。









注意事项：
============
1.平台上输入$($)代码时，一些用户的浏览器会造成崩溃，所以您做这个练习时可使用粘贴的方式，不要直接输入。

