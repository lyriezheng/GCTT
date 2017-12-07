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
，这也是开发和采纳[left-pad](https://www.npmjs.com/package/left-pad)和[is-array](https://www.npmjs.com/package/is-array)的背后深层原因。我迷失在每周解释成千上万的下载中了。

### Go语言生态系统
Go的生态系统比较小，但是有很多基于Go的了不起的项目，目前[go-chi/chi](https://github.com/go-chi/chi)在github上已经收获了超过2500个星和大量的积极反馈(像sqlx，chi项目建立在底层的net/http包上)。我们使用它做了[ErrorHub](https://errorhub.io/)，我强烈推荐这个项目。
也有一些web框架可以使用，但是就像我前面所讲的，你应该首先使用标准库，然后你能够发现当你前进的时候真正需要的是什么。使用一个web框架本身不是必须的，但是当你要拓展需求的时候，你也许可以更明智的把项目迁移到框架中。
### 迁移自其他语言
Go语言和其他原因的区别来自于语言的细节上。我们可以发现，从Python和Ruby迁移，或者从PHP迁移到JavaScripe有着相同的差异。Go语言也没有特别之处，你可能一开始觉得[slice工作原理](https://scene-si.org/2017/08/06/the-thing-about-slices/)有一点点困惑，但是从任何语言迁移到其他语言时都会遇到这样的问题，作为另一个样例，请看[Ruby谓词](http://ruby-for-beginners.rubymonstas.org/objects/predicates.html)。
Go语言入门门槛不是很高，我曾经写了差不多15年的PHP，然后相对轻松的就转到Go语言上了。让你的脑袋理解Node的异步操作，包括Promises和Yields，那就困难很多了。如果要我建议两篇相关的文章的话，你可以阅读一下[对话Node之父Ryan Dahl](https://www.mappingthejourney.com/single-post/2017/08/31/episode-8-interview-with-ryan-dahl-creator-of-nodejs/)，[Bob Nystroms点评异步函数](http://journal.stuffwithstuff.com/2015/02/01/what-color-is-your-function/)也是一篇必读文章。
>    我认为Node并不是一个构建大型web服务的最佳系统，我会使用Go来做这个事情。而且说实话，这也是我抛弃Node的原因，事实就是，Node不是最好的服务端系统。 --by Ryan Dahl
    
### Go的强大
不管你选择什么项目来作为你的前后端框架，Go总是能够非常好的提供终端API。WebSocket？没问题！互联互通的Go语言集群？难道你没听说过Docker或者Kubernetes吗？那些可都是拥有者难以置信的扩展性的系统啊，而且，是用Go写的。
Go是一个非常出色的语言，它提供了与数据库接口这样的后端逻辑，并通过HTTP终端API暴露此逻辑。前端堆栈的选择将确保你可以为浏览器使用和呈现此数据。
如果你厌倦了React,那么将其替换为VueJs而并不减少任何Go语言代码。在其他语言中你可能会不得不像这样分隔应用，因为很多时候，你并不是写了一个server，而是一个产生输出并运行在浏览器中的脚本。当然，使用Go你需要使用相同的方式使用```http/template```，但是通过一个前端的框架来实现你的前端，将会给你带来只需要寻找那个框架的专业人才的好处。并不是每个人都会觉得Go舒服。
你应该不会希望用bash来实现一个web server吧？

### 为什么你应该选择Go
Go语言对我的主要卖点在于高质量的标准库、语言和类库。Node、PHP、Ruby以及其他专注于web开发的语言通常是单线程，就算可以实现多线程，也是作为一个附加功能而不是第一公民。他们的内存管理很烂(尽管PHP在这15年里得到了很大的提高)，而且或许是最重要的一点，所有的他们似乎都落入了脚本语言的范畴。编译后的代码永远比任何一个通过解释器运行的代码要更快。
人们总是重复造轮子，不仅仅是因为他们可以，而且还因为他们可以以某种方式改善它。也许只有一点点的改进，类似于优化了一个产生特殊输出的函数，或者产生了巨大的进步，就像创造了一个把并发作为第一公民的语言。
总有些地方处理的没有这么好（在Go中有这么多关于泛型的讨论），但是总会有进步的空间。我没有排除一种可能性，那就是某人在Go里建了个分支并提供了在他看来对泛型最好的解决办法。人们根据他们的经验会做出应对，如果你的经验告诉你并发对于某个语言是个大问题，你也正在寻找处理它的办法，移植到Go语言是个很好的方式。



---

via: [https://scene-si.org/2017/10/18/choosing-a-go-framework/](https://scene-si.org/2017/10/18/choosing-a-go-framework/)

作者：[Tit Petric](https://scene-si.org/about/)  
译者：[lyriezheng](https://github.com/lyriezheng)  
校对：[校对者ID](https://github.com/校对者ID)

本文由 [GCTT](https://github.com/studygolang/GCTT) 原创编译，[Go 中文网](https://studygolang.com/) 荣誉推出

