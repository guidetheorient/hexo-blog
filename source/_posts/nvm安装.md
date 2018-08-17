---
title: nvm安装
date: 2018-08-17 09:23:40
tags:
---

nvm-windows管理node版本
===

> 参考
[1.nvm-windows/gitub](https://github.com/coreybutler/nvm-windows)
[2.Accessing Long File Names Under MS-DOS](https://technet.microsoft.com/en-us/library/cc722482.aspx)

1. 卸载已安装的node，删除node安装目录(e.g. "C:\Program Files\nodejs")
2. 删除npm文件夹 (e.g. "C:\Users\\\<user>\AppData\Roaming\npm")
3. 安装nvm(安装完成后以管理员身份重启命令行，输入nvm检查是否安装成功)
4. 安装后可以使用`nvm install <version>`安装node，但无法使用`nvm use [version]`，查看[issues](https://github.com/coreybutler/nvm-windows/issues/41)，两个问题：
	1. 查看nvm安装目录下的`settings.txt`中`root`是否指向`nvm`所在目录(因为此处是安装了nvm之后重新安装node，root没有设置的情况下，默认安装`nvm`目录下)
*注：`nvm root [path]`:  指定nvm存放node的路径*

	2. 报错如下，即文件夹名带有空格，参照windows文件名简写规则，我是安装在`Program Files`中的，所以`nvm root c:\progra~1\nvm`，此时应该可以使用命令`nvm use [version]`

`'c:\program' 不是内部或外部命令，也不是可运行的程序或批处理文件。`

补充说明：
filename前六位+~+n，其中n是数字，代表第几个，n最多为4(应该是按名称顺序)
* 如前六位就可以区分，比如*Documents and Settings => Docume~1*;
* 如前六位不能区分，比如:
*Program Files => Progra~1*
*Program Files(x86) => Progra~2*

3. npm例行换源
	```
	npm set registry https://registry.npm.taobao.org
	// 当然改完之后检测一下，有返回数据就行
	npm info vue
	```


