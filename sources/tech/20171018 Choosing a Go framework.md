\[翻译中\] by lyriezheng

# 选择一个Go语言框架

每天，最多每几天天，就会有一些人跑到[/r/golang](https://www.reddit.com/r/golang/)问“哪个框架最好”，在我看来，至少应该尝试着用一个容易让人理解的方式来提出这个问题吧。我的答案是，尽量不要使用框架。
这或许是对于这个复杂问题的一个非常简洁的答案，但是这也不是说你不要使用框架。我们都知道，当我们开发软件的时候，框架可以帮助我们不断适应常见的使用模式并越来越快速的进行重复开发。框架也在尽可能的消除重复。

### 标准库或者stdlib
Go语言的标准库的质量还是很高的，你应该尽量的使用它。如果你正在写一些API服务，你就需要让自己熟练```net/http```包，而且无论你使用什么框架，它们都是基于这个包构建起来的。当标准库不能够恰当的解决你正在关注的重点问题时，引入第三方包是一个合理的做法，例如那些生成UUIDS和Json web token (JWT)处理器。有一些包（包括web框架）构建在标准库的上层，一个著名的例子就是在建立在sql/database之上的[jmoiron/sqlx ](https://jmoiron.github.io/sqlx/)。

### 包管理
Go和包含一个软件包市场的语言有很大的不同，Node有[npm](https://www.npmjs.com/)，PHP有[packagist (composer)](https://packagist.org/)，Ruby有它的[gems](https://rubygems.org/)


---

via: [https://scene-si.org/2017/10/18/choosing-a-go-framework/](https://scene-si.org/2017/10/18/choosing-a-go-framework/)

作者：[Tit Petric](https://scene-si.org/about/)  
译者：[译者ID](https://github.com/译者ID)  
校对：[校对者ID](https://github.com/校对者ID)

本文由 [GCTT](https://github.com/studygolang/GCTT) 原创编译，[Go 中文网](https://studygolang.com/) 荣誉推出

