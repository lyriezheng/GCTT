\[翻译中\] by lyriezheng

# 选择一个Go语言框架

每天，最多每几天天，就会有一些人跑到[/r/golang](https://www.reddit.com/r/golang/)问“哪个框架最好”，在我看来，至少应该尝试着用一个容易让人理解的方式来提出这个问题吧。我的答案是，尽量不要使用框架。
这或许是对于这个复杂问题的一个非常简洁的答案，但是这也不是说你不要使用框架。我们都知道，当我们开发软件的时候，框架可以帮助我们不断适应常见的使用模式并越来越快速的进行重复开发。框架也在尽可能的消除重复。

### 标准库或者stdlib
Go语言的标准库的质量还是很高的，你应该尽量的使用它。如果你正在写一些API服务，你就需要让自己熟练```net/http```包，而且无论你使用什么框架，它们都是基于这个包构建起来的。当标准库不能够恰当的解决你正在关注的重点问题时，引入第三方包是一个合理的做法，例如那些生成UUIDS和Json web token (JWT)处理器。有一些包（包括web框架）构建在标准库的上层，一个著名的例子就是在建立在sql/database之上的[jmoiron/sqlx ](https://jmoiron.github.io/sqlx/)。

### 包管理
Go和包含一个软件包市场的语言有很大的不同，Node有[npm](https://www.npmjs.com/)，PHP有[packagist (composer)](https://packagist.org/)，Ruby有它的[gems](https://rubygems.org/)。Go语言没有一个官方包管理器的现状极大的影响了包的可发现能力。[gvt](https://github.com/FiloSottile/gvt)、[glid](https://github.com/Masterminds/glide)是Go语言的两个包管理器的例子，还有一个是官方实验品[dep](https://github.com/golang/dep)，未来的某一天有可能会和Go工具链绑定到一起。

>     dev目前只是官方的试验品，并不是官方工具。查阅[Roadmap](https://github.com/golang/dep/wiki/Roadmap)去获取更多的相关信息。

实际上，Glide在官方README里面正在建议迁移至dep上，当你开始工作时，请使用dep。
Go语言包代码存在于Github,Bitbucket以及其他仓库内，甚至可以自己进行托管。最完整的Go语言包列表可以通过检索[godoc](https://godoc.org/)得到，对从这些包生成的文档进行集中托管。Go语言并不提供类似于其他语言的某些项目的包市场，不过有一个值得注意的项目[gopkg.in](http://labix.org/gopkg.in),类似于其他包管理器那样进行包索引。
不管你创建了什么样的包，都有可能因为代码质量等等因素而不被接受。某些软件包作者比其他人更为人所知，如果你正在寻找一些像配置标志软件包那样微不足道的东西，那么你只剩下少量但是高质量的选择。 这在相关的包装系统中是不可能的。
相比较而言，Node软件包的质量发生了快速下降，由于把焦点放到了前后端之间，Node里面有了大量的怪异代码，而这种情况在Go语言中是不存在的。Go是一个纯正的服务端语言，而Node则往往服务于前后端的js代码。有一些违反了逻辑解释的模式存在于Node的开发过程中
，这也是开发和采纳[left-pad](https://www.npmjs.com/package/left-pad)和[is-array](https://www.npmjs.com/package/is-array)的背后深层原因。
---

via: [https://scene-si.org/2017/10/18/choosing-a-go-framework/](https://scene-si.org/2017/10/18/choosing-a-go-framework/)

作者：[Tit Petric](https://scene-si.org/about/)  
译者：[译者ID](https://github.com/译者ID)  
校对：[校对者ID](https://github.com/校对者ID)

本文由 [GCTT](https://github.com/studygolang/GCTT) 原创编译，[Go 中文网](https://studygolang.com/) 荣誉推出

