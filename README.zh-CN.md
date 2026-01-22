# python-markdown2：快速完整的 Python Markdown 实现

## 这个代码是干什么的？

Markdown 是一种轻量级的文本标记格式，以及将其转换为 HTML 的处理器。正如其创始人所描述的：

> Markdown 是为网络写作者设计的文本到 HTML 转换工具。
> Markdown 允许你使用易读易写的纯文本格式进行写作，
> 然后将其转换为结构有效的 XHTML（或 HTML）。
>
> -- <http://daringfireball.net/projects/markdown/>

**python-markdown2** 是 Markdown 的一个快速且完整的 Python 实现。它的编写目标是尽可能匹配原始 Perl 实现的 Markdown.pl 的行为。markdown2 还附带了许多扩展功能（称为"extras"），例如语法着色、表格、标题 ID 等。详见下面的"扩展语法"部分。"markdown2"支持 Python 2.4 到 3.3 的所有版本（以及 pypy 和 jython，虽然我不经常测试这些）。

还有另一个 [Python markdown.py](http://www.freewisdom.org/projects/python-markdown/) 实现。但是，至少在这个项目启动时，markdown2.py 更快（参见[性能说明](https://github.com/trentm/python-markdown2/wiki/Performance-Notes)），据我所知也更准确（参见[测试说明](https://github.com/trentm/python-markdown2/wiki/Testing-Notes)）。不过那是很久以前的事了，所以你不应该因此而排除 Python-markdown。

关注 <a href="https://twitter.com/intent/user?screen_name=trentmick" target="_blank">@trentmick</a> 获取 python-markdown2 的更新。

Travis-ci.org 测试状态: [![Build Status](https://secure.travis-ci.org/trentm/python-markdown2.png)](http://travis-ci.org/trentm/python-markdown2)


## 安装

在你的 Python 环境中运行以下**任一**命令来安装：

    pip install markdown2
    pypm install markdown2      # 如果你使用 ActivePython (activestate.com/activepython)
    easy_install markdown2      # 如果这是你最好的选择
    python setup.py install

不过，运行此程序所需的所有内容都在 "lib/markdown2.py" 文件中。如果对你来说更方便，你可以直接将该文件复制到你的 PythonPath 中的某个位置（作为模块使用）或可执行路径（作为脚本使用）。


## 快速使用

作为模块使用：

    >>> import markdown2
    >>> markdown2.markdown("*boo!*")  # 或使用 `html = markdown_path(PATH)`
    u'<p><em>boo!</em></p>\n'

    >>> markdowner = markdown2.Markdown()
    >>> markdowner.convert("*boo!*")
    u'<p><em>boo!</em></p>\n'
    >>> markdowner.convert("**boom!**")
    u'<p><strong>boom!</strong></p>\n'

作为脚本（命令行）使用：

    $ python markdown2.py foo.md > foo.html

我认为基于 pip 的安装也会启用以下方式：

    $ markdown2 foo.md > foo.html

有关更多详细信息，请参见[项目 wiki](https://github.com/trentm/python-markdown2/wiki)、[lib/markdown2.py](https://github.com/trentm/python-markdown2/blob/master/lib/markdown2.py) 的文档字符串和/或 `python markdown2.py --help`。


## 扩展语法（即扩展功能）

许多 Markdown 处理器都支持额外的可选语法（通常称为"扩展"），markdown2 也不例外。在 markdown2 中，这些被称为"extras"。以 "footnotes" extra 为例，以下是如何使用 extra ... 作为脚本：

    $ python markdown2.py --extras footnotes foo.md > foo.html

作为模块：

    >>> import markdown2
    >>> markdown2.markdown("*boo!*", extras=["footnotes"])
    u'<p><em>boo!</em></p>\n'

目前实现了许多 extras，包括表格、脚注、`<pre>` 块的语法着色、自动链接模式、目录、Smarty Pants（用于花式引号、破折号等）等等。有关完整详细信息，请参见 [Extras wiki 页面](https://github.com/trentm/python-markdown2/wiki/Extras)。


## 项目

python-markdown2 项目位于 <https://github.com/trentm/python-markdown2/>。（注意：2011 年 3 月 6 日，该项目从 [Google Code](http://code.google.com/p/python-markdown2) 迁移到了 Github。）另请参见 [PyPI 上的 markdown2](http://pypi.python.org/pypi/markdown2)。

变更日志：<https://github.com/trentm/python-markdown2/blob/master/CHANGES.md>

报告错误：<https://github.com/trentm/python-markdown2/issues>


## 测试套件

这个 markdown 实现通过了一个相当广泛的测试套件。要运行它：

    make test

测试套件的核心是许多"cases"目录——每个目录都包含一组匹配的 .text（输入）和 .html（预期输出）文件。这些是：

    tm-cases/                   为 python-markdown2 编写的测试（tm=="Trent Mick"）
    markdowntest-cases/         来自第三方 MarkdownTest 包的测试
    php-markdown-cases/         来自第三方 MDTest 包的测试
    php-markdown-extra-cases/   也来自 MDTest 包的测试

有关完整详细信息，请参见[测试说明 wiki 页面](https://github.com/trentm/python-markdown2/wiki/Testing-Notes)。


## 主要功能

python-markdown2 将 Markdown 格式的文本转换为 HTML，支持以下核心功能：

- **标题**：使用 # 符号创建标题（# 一级标题，## 二级标题，等等）
- **强调**：使用 *斜体* 或 _斜体_ 表示斜体，使用 **粗体** 或 __粗体__ 表示粗体
- **列表**：支持有序列表和无序列表
- **链接**：支持内联链接和引用式链接
- **图片**：嵌入图片的语法
- **代码块**：内联代码和缩进代码块
- **引用**：使用 > 符号创建引用块
- **水平线**：使用 --- 或 *** 创建水平分隔线

以及许多扩展功能（extras），使其成为一个功能强大且灵活的 Markdown 处理工具。


## 许可证

MIT 许可证。详见 LICENSE.txt 文件。
