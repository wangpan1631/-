###读winter的重学前端
####建立自己的知识架构、对知识要追本溯源

#### 05节

1. **数据类型（内置类型）**
JS有7种内置类型，分为两大类型：基本类型和对象Object

* 基本类型：string  number  boolean null  undefined symbol

* 对于**undefined**, 有的编程规范要求用void 0代替undefined, 为什么呢？因为JavaScript的代码undefined是一个变量，而并非是一个关键字，这是JavaScript语言公认的设计失误之一，所以，我们为了避免无意中被篡改，建议使用viod 0来获取undefined值。
* 对于**null**, 表示的是“定义了但是为空”，它的语义表示空值，与undefined不同，null是JavaScript关键字，所以在任何代码中，我们都可以放心使用null关键字来获取null值。
* 对于**String**, 用于表示文本数据，一旦字符串构造出来，无法用任何方式改变字符串的内容。String有最大长度是2^53 - 1，但这个所谓的最大长度，并不完全是我们理解的字符数，因为String的意义并非“字符串”，而是字符串的UTF16编码，我们字符串的操作charAT、charCodeAt、length等方法针对的都是UTF16编码。所以，字符串的最大长度，实际上是受字符串的编码长度影响。
* 对于**Number**，需要注意几个特殊值，NaN、Infinity(无穷大)、-Infinity(负无穷大)，JavaScript中有+0和-0，在加法类运算中他们没有区别，但是除法的场合则需要特别留意区分，“忘记检查除以-0，而得到负无穷大”的情况经常会导致错误，而区分+0和-0的方式，正式检测1/x是Infinity还是-Infinity。
* 0.1 + 0.2 == 0.3 结果是false，这个错误的不是结论，而是比较的方法，正确的比较方法是使用JavaScript提供的最小精度值：console.log( Math.abs(0.1 + 0.2 - 0.3) <= Number.EPSILON>)，检查等式左右两边差的绝对值是否小于最小精度，才是正确的比较浮点数的方法。这段代码结果就是true了。

* Symbol， 是ES6中引入的新类型，它是一切非字符串的对象Key的集合，在ES6规范中，整个对象系统被用Symbol重塑，它的最大特点就是**独一无二**。
* Symbol 的用途就是如此：Symbol 可以创建一个独一无二的值（但并不是字符串）（Symbol 生成一个全局唯一的值。）
* Symbol迭代器: Symbol.Iterator，对象的Symbol.Iterator属性，指向这个对象的默认遍历器：
```
var myIterable = {};
myIterable[Symbol.iterator] = function* () {
    yield 1;
    yield 2;
    yield 3;
};
console.log([...myIterable]); // [1, 2, 3]
```

[Symbol使用场景举例](https://zhuanlan.zhihu.com/p/22652486 "Symbol使用场景举例")

* Object, 对象的定义是“属性的集合”。属性分为数据属性和访问器属性，二者都是key-value结构，key可以是字符串或者Symbol类型。JavaScript中的“类”， 仅仅是运行时对象的一个私有属性，而JavaScript中是无法自定义类型的。
* JavaScript中的几个基本类型，都在对象类型中有一个“亲戚”，它们是：Number String Boolean Symbol, 所以，我们必须认识到3与new Number(3)是完全不同的值，前者是Number类型，后者是Object类型，Number String Boolean，三个构造器是两用的，当跟new搭配时，它们产生对象，当直接调用时，它们表示强制类型转换。Symbol函数比较特殊，直接用new调用它会抛出错误，但它们仍然是Symbol对象的构造器。
* 为什么给对象添加的方法能用在基本类型上？答案：.运算符提供了装箱操作，它会根据基础类型构造一个临时对象，使得我们能在基础类型上调用对应对象的方法。

**对象这块需要着重多学习，这几篇文章看的有些晕乎**
#### 06节 JavaScript面向对象，面向对象还是基于对象？ 看的优点晦涩，没有学习到非同寻常的知识点，也可能是没理解

#### 07节 JavaScript面向对象，我们真的需要模拟类吗？
* 结论，当我们使用类的思想来设计代码时，应该尽量使用class来声明类，而不是用旧语法，拿函数来模拟对象。

#### 09节 值得关注的前端技术，图形学、包管理、智能开发AI

#### CSS语法
* CSS支持一批特定的计算型函数：calc() max() min() clamp() toggle() attr()

**calc()**函数是基本的表达式计算，它支持加减乘除四则运算，在针对维度进行计算时，calc()函数允许不同单位混合运算，这非常的有用。

```
section {
    float: left;
    margin: 1em;
    border: 1px solid green;
    width: calc(100%/3 - 2*1em - 2*1px);
}
```

#### 10节，浏览器

此处省略。。。。

####一些重学前端的学员分享的：
* 分享一：
对于程序员来说，最重要的是迅速获取某项知识的能力以及动手解决问题的能力，**前者需要我们建立自己的知识体系，也就是winter老师在第一讲中提到的，我们需要完善的知识架构**

* 分享二：
先提升知识的广度，再去拓展知识的深度；
养成随时记录的习惯，可以是笔记，可以是代码（一定要写上注释）；
多逛逛技术论坛，有条件的情况下多去实验一下论坛中自己感兴趣的代码；
最后一条也是最重要的一条，坚持每天八小时之外的学习和锻炼；

* 木易杨的分享：
对于框架的使用没必要花费太多时间，应该多研究一下三大框架背后的设计思想。；
对于前段进阶这个问题，其实看书的作用和意义已经不太明显，需要寻找好的平台和合适的项目，在项目中不断克服难题并挑战自己，遇到问题再去查阅资料总结，如果只是闭门看书那很难成为高手，书只是基础而已，真正的应用还是在项目中；
**寒冬中能做的只有提升自己，但是光靠技术提升是不行的。还需要靠 表达能力！表达能力！表达能力，表达能力就是形成自己的框架系统，有理有据并且逻辑清晰，而且能让外人听懂，**大部分优秀的人都具备这样的能力，那提升表达能力的最重要的方法就是**写作训练**；
我最近在执行的方法是专注 + 锻炼 + 利用周末（专注即工作时专注于工作，努力做好每次迭代，遇到难题迎难而上，工作时不开微信，勤用笔记安排日常工作并整理文档，锻炼即一周抽出三天时间每次去健身房锻炼1小时，强壮的体魄才能撑住高强度的学习和工作）

**书写简历的技巧：**
hr先看学历，在根据技术负责人要求的技术点搜索关键字，如react、vue等
全栈不易，不如把自己最擅长的那个语言或技术高亮加粗出来，
一定要多刷题

#### 36节为什么会有捕获过程和冒泡过程？
* 我们先来了解一下事件，事件来自输入设备，我们平时的个人设备上，输入设备有三种：键盘、鼠标、触摸屏（**这其中，触摸屏和鼠标又有一定的共性，它们被称作pointer设备，所谓pointer设备，是指它的输入最终会被抽象成屏幕上面的一个点。**）    鼠标点击并没有位置信息，但是一般操作系统会根据位移的累积计算出来，跟触摸屏一样，提供一个坐标给浏览器。那么，把这个坐标转换为具体的元素上事件的过程，就是捕获过程了，而冒泡过程，则是符合人类理解逻辑的：当你按电视机开关时，你也按了电视机。所以我们可以认为，捕获是计算机处理事件的逻辑，而冒泡是人类处理事件的逻辑，捕获总是在冒泡之前发生。

#### 43节前端的性能到底对业务数据有多大的影响？
* 性能优化不能只着眼于局部的代码，**一切没有profiling的性能都是耍流氓。**凡是真正有价值的性能优化，必定是从端到端的业务场景建立体系来考虑的。winter提供的性能体系的建立要分成以下几部分：
1. 现状评估和建立指标（正确地评估现状和建立指标是关键的一步，性能问题可以分成很多方面，**最重要的几个点是页面加载性能、动画与操作性能、内存和电量消耗，其实这三部分中，“页面加载性能”跟用户的流失率有非常强的关联性，而用户流失率，正是公司业务非常看重的指标**），设计的一个新指标——**秒开率**，即一秒之内打开的用户占用户总量的百分比。
2. 技术方案
3. 执行
4. 结果评估和监控

#### 44节 什么样的工具链才能提升团队效率？
* Yeoman这个工具我从来没有使用过
[Yeoman](https://www.jianshu.com/p/f6b8ace5c287 "Yeoman")
[Yeoman的使用](https://www.cnblogs.com/nzbin/p/5751323.html "Yeoman的使用")
[Yeoman官网](https://yeoman.io/ "Yeoman官网")
* 前端开发大概要做的事情，有：初始化项目、运行和测试、测试（单元测试）、发布
* 关系到开发体现的指标一般有：调试/构建次数、构建平均时长、使用的工具版本、发布次数，（winter：我司工具团队曾经从构建平均时长数据中发现构建效率问题，对webpack做了大量深度优化来改善开发体验）