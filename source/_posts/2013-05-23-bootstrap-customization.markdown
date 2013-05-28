---
layout: post
title: "Bootstrap定制-工具与目录"
date: 2012-07-23 14:54
comments: true
categories: 
- programming
- css
- bootstrap
---

Twitter的Bootstrap简洁好用，但内置的配色和样式用多了难免会审美疲劳。如果直接修改或覆盖生成的css会失去灵活性，而且以后升级维护也会非常麻烦。我使用的方式是下载bootstrap的less文件，添加自己的less文件重新编译来定制样式。

#自定义less
以下是Bootstrap的less文件引用关系

- bootstrap.less (编译后生成bootstrap.css)
  - variables.less
  - mixins.less
  - buttons.less
  - … (widgets)
- responsive.less (编译后生成bootsrap-responsive.css)
  - variables.less
  - mixins.less
  
bootstrap.less 是主文件，定义需要引用的文件。variables.less和mixins.less定义各种变量和函数。而Widget(如button, navbar)的具体样式则由对应的文件分别定义。修改这两个文件基本上可以满足大部分自定义的需求。responsive.less定义的是响应式布局相关的样式，一般不需要改动。

##具体步骤
1) 以bootstrap.less为蓝本定义项目的less文件style.less。import 的路径作相应修改

2) variable的改动较多，所以单独定义style_variables.less文件用于覆盖默认变量定义。如果必要，其他less文件也可以作类似处理

3) 编译style.less文件，生成style.css。html中的引用由bootstrap.css改为style.css。

4) 如果以后需要升级bootstrap，检查一下新的bootstrap.css和variables.css有没有变化，一般直接替换bootstrap下的less文件就可以了。

##文件示例
目录结构

```
/Web_dir
     /bootstrap
          /less
          /js
     /css
          style.css
     /less
          style.less
          variables_override.less
          buttons_override.less
          my_component.less
```

style.less
``` css
/*!
 * style.css based on bootstrap.less (v2.0.2)
 */

// CSS Reset
@import "../bootstrap/less/reset.less";

// Core variables and mixins
@import "../bootstrap/less/variables.less"; // Modify this for custom colors, font-sizes, etc
@import "variables_override.less"//project overriding variables 
@import "../bootstrap/less/mixins.less";

// Grid system and page structure
@import "../bootstrap/less/scaffolding.less";
@import "../bootstrap/less/grid.less";
@import "../bootstrap/less/layouts.less";
```

variables_override.less
``` css
//override the bootstrap/less/variabiles

@linkColor:             #f89632; //Green #7CA60A  //Orange #f89632

@bodyBackground:        #f7f7f7;
```
          
#编译less文件
编译less文件可以使用client-side或server-side方式，client-side由浏览器完成less文件的编译，一般在开发阶段使用；而production一般使用server-side方式，事先编译好css文件。现在有很多编译工具可以监测文件变化，瞬间完成编译，所以即使在开发阶段也可以使用server-side方式。

[less tools](http://less.cnodejs.net/tools) 有很多less编译工具，Mac，Windows和Linux上的都有。如果你在用Sublime Text2， 使用插件会更方便些。我使用的是[less2css](https://github.com/timdouglas/sublime-less2css)，用package control可以直接下载。使用千需要简单配置一下。配置可以放在全局或者项目级别。如果选择项目级别，点击Project->Edit project菜单项修改配置，在setttings项中增加less2css节点就可以实现自动编译了。

``` json
	"settings":
	{
		...

		"less2css":
			{
				"autoCompile": true,
				"main_file": "style.less",
				"minify": true,
				"outputDir": "./css"
			}
	}
```
