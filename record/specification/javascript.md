<div id="table-of-contents">
<h2>Table of Contents</h2>
<div id="text-table-of-contents">
<ul>
<li><a href="#orgheadline1">1. OOP成员的定义顺序：正常-&gt;Virtual-&gt;Abstract</a></li>
<li><a href="#orgheadline2">2. 常量</a></li>
<li><a href="#orgheadline4">3. Typescript</a>
<ul>
<li><a href="#orgheadline3">3.1. 成员的定义顺序</a></li>
</ul>
</li>
<li><a href="#orgheadline5">4. 命名原则</a></li>
<li><a href="#orgheadline6">5. 统一使用Id命名，不使用ID命名</a></li>
<li><a href="#orgheadline7">6. 注释</a></li>
<li><a href="#orgheadline8">7. 序号</a></li>
<li><a href="#orgheadline9">8. 类的方法、属性</a></li>
<li><a href="#orgheadline10">9. 类名</a></li>
<li><a href="#orgheadline11">10. 闭包（以类的概念）中共用的私有成员，加上“_”前缀；</a></li>
<li><a href="#orgheadline12">11. 参数</a></li>
<li><a href="#orgheadline15">12. 文件包名</a>
<ul>
<li><a href="#orgheadline13">12.1. 小写</a></li>
<li><a href="#orgheadline14">12.2. 用“_”隔开</a></li>
</ul>
</li>
<li><a href="#orgheadline16">13. 文件名与js一样的规则</a></li>
<li><a href="#orgheadline17">14. 在文件最开始的地方require文件</a></li>
<li><a href="#orgheadline18">15. callArgWith调用应该与验证方法放到一起</a></li>
<li><a href="#orgheadline19">16. 用function定义函数，用var定义变量，且变量在函数之前定义。如：</a></li>
<li><a href="#orgheadline20">17. 产品代码中的测试方法需要加上前缀“forTest_”。如：</a></li>
<li><a href="#orgheadline21">18. 文件包名小写，Scripts中的文件包、js文件包的名称小写。如：</a></li>
<li><a href="#orgheadline22">19. Content中的资源名小写。如：</a></li>
<li><a href="#orgheadline23">20. 项目名大写。如：</a></li>
</ul>
</div>
</div>

# OOP成员的定义顺序：正常->Virtual->Abstract<a id="orgheadline1"></a>

如下所示，先定义P\_<sub>showPercent</sub>，然后定义P\_<sub>showData</sub>，最后定义P\_<sub>getBeginDate</sub>：
Protected: {
            P\_<sub>showPercent</sub>: function () {
                &#x2026;
            },

Virtual: {
    P\_<sub>showData</sub>: function (dataArr) {
        var num = this.<sub>getNum</sub>(dataArr);  //取出数据

        this.<sub>showNum</sub>(num);
    }
},

    Abstract: {
        P\_<sub>getBeginDate</sub>: function () {
        }
    }
},

# 常量<a id="orgheadline2"></a>

用分隔符隔开。
如：
var PLUGIN<sub>NAME</sub> = "aaa";

# Typescript<a id="orgheadline4"></a>

## 成员的定义顺序<a id="orgheadline3"></a>

private static -> public static -> constructor -> (getter/setter->public->protected->private) attri -> (public->protected->private) method

abstract->virtual->common members

# 命名原则<a id="orgheadline5"></a>

使用骆驼式命名

骆驼式命名法： 
       正如它的名称所表示的那样，是指混合使用大小写字母来构成变量和函数的名字。例如，下面是分别用骆驼式命名法和下划线法命名的同一个函数：
插入代码：        printEmployeePaychecks()； 

骆驼式命名法近年来越来越流行了，在许多新的函数库和Microsoft Windows这样的环境中，它使用得当相多。 

命名原则讨论：骆驼命名法，匈牙利命名法，帕斯卡命名法与下划线命名法

枚举类型以"E"开头

接口以"I"开头

# 统一使用Id命名，不使用ID命名<a id="orgheadline6"></a>

如Layer有setCanvasId方法，该方法不命名为setCanvasID

# 注释<a id="orgheadline7"></a>

（1）“//\*”
  表示一级小标题
  "//\*\*"
  表示二级小标题

  。。。以此类推
（2）“//?”
  表示未确定的，需要修改或补充的内容

（3）方法注释中，一行代码后出现“//”表示输出结果。如：

        /\*  对每个数组元素调用iterator，返回调用iterator返回false的元素索引的数组
如 source<sub>arr</sub> = ["", "a", "b", ""];
        result = operate.Judge(arr, function (value, index) {
        if (value `=` "") {
        return false;
        }
        else {
        return true;
        }
        });
        */result = [0, 3];
        \**

表述结果为“result = [0, 3];”

# 序号<a id="orgheadline8"></a>

序号都是从0开始，0为第一个。

# 类的方法、属性<a id="orgheadline9"></a>

方法：
  构造函数首字母大写，如“Init”

非构造函数，首字母小写，如“myName”

私有方法加前缀“\_”，保护方法加前缀“P\_”。

  使用动词或动词+名词命名。
属性：
  首字母小写，如“myName”

私有属性加前缀“\_”，保护属性加前缀“P\_”。  

# 类名<a id="orgheadline10"></a>

以function定义的类，首字母大写。如：

function Asyn(){}

对象直接量首字母小写。如：

asyn = {
  set: function(){}
}

# 闭包（以类的概念）中共用的私有成员，加上“\_”前缀；<a id="orgheadline11"></a>

枚举变量不加“\_”前缀；function中的私有成员不加“\_”前缀；内部类加上“\_”前缀；测试describe中的私有成员不加前缀
如
var t = (function(){
  function \_a(){}
  return {
…
}
}());

function A(){
  function \_get(){}
  this.b = function(){}
}

测试describe中的私有成员不加前缀
如：
Describe(“”,function(){
  function a(){}
…
});

# 参数<a id="orgheadline12"></a>

（1）函数中定义与形参同名的变量，前面加“\_”。如：

function A(args){
var \_args = null;

  &#x2026;
}
1\*   文件

js文件名：

如果该.js文件中定义了一个类，则以大写开头。如：

Index.js

Operate<sub>Boss.js</sub>

如果该.js文件中不是定义了一个类（如var t = {}；或者定义了一个实例等），则以小写开头。如：

index.js

operate<sub>boss.js</sub>

js文件包名：

以小写开头。如：

index

    operate<sub>boss</sub>
1\*   接口以I开头。
1\*   接口、抽象类首字母大写。如：

IIterator（接口）
Layer（抽象类）
1\*   命名空间首字母大写。如：

YYC.Tool

1\*   全局变量全部大写。如：

  SIZE
1\*   常量全部大写，私有常量不加“\_”前缀。如：

  FPS
1\*   事件句柄小写。如：

  onload
  onclick
1\*   引号
  首先使用双引号""，然后嵌套时再使用单引号''
1\*   变量申明与初始化放在函数开头。如：

\_loadImg: function () {
          var img = null,
              i = 0,
              len = this.<sub>images.length</sub>,
              self = this,
              image = null;

  函数体&#x2026;
  }
1\*   for循环，在括号里定义i的初始值（即时已经在变量i申明时已经初始化了！）（因为我不习惯看到：for(;i < len;i ++)）的形式！）。如：
  var i = 0,
            len = this.<sub>images.length</sub>;

            for (i = 0;i < len; i++) {
    &#x2026;
      }        
2\*   枚举变量首字母大写，key全部大写，value从0开始。如：
var State = {
  OPEN: 0,
  CLOSE: 1
}
2\*   配置信息属性最后一部分大写。如：
WIDTH: 50,
speed: {
            SLOW: 1,
            NORMAL: 2,
            FAST: 5
        }
2\*   一行代码太长时，需要换成多行显示，此时应将操作符换行。
如下所示：
var str = “a”

-   “b”
-   ”c”;

var result = true
&& true;

var t = a.push()
.concat()
.when()

逗号不需要换行。
如：
a.when(function(){
},
function(){
});

Webstorm
文件包名小写
Node.js

# 文件包名<a id="orgheadline15"></a>

## 小写<a id="orgheadline13"></a>

## 用“\_”隔开<a id="orgheadline14"></a>

如：gulp<sub>plugin</sub>

# 文件名与js一样的规则<a id="orgheadline16"></a>

如 驼峰命名

# 在文件最开始的地方require文件<a id="orgheadline17"></a>

Javascript 测试

# callArgWith调用应该与验证方法放到一起<a id="orgheadline18"></a>

错误：
            it("测试", function () {
                sandbox.stub(tab, "name", "tab");

tab.getAndShowFirstLevelChart("20140720");
fakeChart.draw.callArgWith(1, "tabB");

                expect(fakeChart.draw.callCount).toEqual(1);
            });
正确：
            it("测试", function () {
                sandbox.stub(tab, "name", "tab");

tab.getAndShowFirstLevelChart("20140720");

    fakeChart.draw.callArgWith(1, "tabB");
    expect(fakeChart.draw.callCount).toEqual(1);
});

# 用function定义函数，用var定义变量，且变量在函数之前定义。如：<a id="orgheadline19"></a>

var t = 1;

function a(){
  xxx
}

# 产品代码中的测试方法需要加上前缀“forTest\_”。如：<a id="orgheadline20"></a>

namespace("YE").Director = YYC.Class({
        &#x2026;
        Static: {
           &#x2026;
            //\*供测试使用

            forTest<sub>clearInstance</sub>: function () {
                \_instance = null;
            },
            forTest<sub>getGameStatus</sub>: function () {
                return GameStatue;
            }
        }
});
Asp.net MVC

# 文件包名小写，Scripts中的文件包、js文件包的名称小写。如：<a id="orgheadline21"></a>

content -> css

scripts -> bomber

jquery-\* \* js

# Content中的资源名小写。如：<a id="orgheadline22"></a>

content -> css -> index.css
content -> image ->　index.jpg

# 项目名大写。如：<a id="orgheadline23"></a>

Help
JavascriptTest