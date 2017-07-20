## eslint

`ESLint`就是一个Lint工具，它是由js红宝书的作者创立的一个开源项目.旨在为大家提供一个可扩展、每条规则独立、不内置编码风格的语法检测工具，`ESLint`相比`JSLint`它被设计成完全可配置的.每一条规则都是一个插件，用户完全可以根据自己的需求来选择使用哪些规则.比如报错就分为`警告`和`错误`两个等级，或者禁用

<img src="http://up.2cto.com/2012/0525/20120525032153802.png" width="300" />

### 安装`ESLint`

在安装`vue-cli`提示是否安装`ESLint`的时候选择y,然后选择标准(standard)安装。

<img src="http://i4.buimg.com/519918/c73d86e23559eaba.png" width="400"/>

然后创建的项目中就会出现:`.eslintignore`和`.eslintrc.js`两个文件。 

`.eslintignore`类似Git的`.gitignore`用来忽略一些文件不使用ESLint检查。 
`.eslintrc.js`是ESLint配置文件，用来设置插件、自定义规则、解析器等配置

[官方文档地址](http://eslint.org/docs/user-guide/configuring)

[github地址](https://github.com/eslint/eslint)

### 关键属性解释：

**解析器(parser)：**使用了babel-eslint，这个可以在package.json中找到，说明我们已经安装过该解析器了。 
**环境配置(env)：**在浏览器中使用eslint。 
**继承(extends)：**该配置文件继承了[standard](https://github.com/feross/standard/blob/master/RULES.md#javascript-standard-style)规则，具体规则自己看文档，看不懂有[中文版](https://github.com/feross/standard/blob/master/docs/RULES-zhcn.md)的。**！重要** 
**规则(rules)：**三个自定义规则。完整的[文档](http://eslint.org/docs/rules/)

> - arrow-parems 允许箭头函数参数使用括号,具体操作请看[文档](http://eslint.org/docs/rules/arrow-parens)
> - generator-star-spacing 允许方法之间加星号，如`function * generator() {}`。[文档](http://eslint.org/docs/rules/generator-star-spacing)在此。这是ES6提供的[生成器函数](https://imququ.com/post/generator-function-in-es6.html)。
> - no-debugger’ 允许在开发环境下使用debugger。这个比较简单，不过还是贴下[文档](http://eslint.org/docs/rules/no-debugger)便于查看。

在`rules`中每个配置项后面第一个值是eslint规则的**错误等级**。 

* “off” 或 0 - 关闭这条规则 
* “warn” 或 1 - 违反规则会警告（不会影响项目运行） 
* “error” 或 2 - 违反规则会报错（屏幕上一堆错误代码~）

在`main.js`中有一行`/* eslint-disable no-new */`这行代码的意思不执行`ESLint`检查,因为`standard`规则中实例化的构造函数必须用一个变量保存