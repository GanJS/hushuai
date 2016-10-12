title: OmniMarkupPreviewer
date: 2016-04-02 14:11:20
description: 
categories:
- sublime
tags:
- sublime
toc: true
author:
comments:
original:
permalink: 
---

　　**OmniMarkupPreviewer：**作为 Sublime Text 的一款强大插件，支持将标记语言渲染为 HTML 并在浏览器上实时预览，同时支持导出 HTML 源码文件。

<!-- more -->

## Markdown

>Markdown 是一种轻量级标记语言，创始人为约翰·格鲁伯（John Gruber）。它允许人们“使用易读易写的纯文本格式编写文档，然后转换成有效的XHTML(或者HTML)文档”。 —— 来自维基百科

## Sublime Text 3

>Sublime Text 作为近些年迅速崛起的后起之秀，凭借其精美的 UI 交互、完备的特色功能俘虏了一大批忠实用户。其风靡之势刺激了一些新老文本编辑器的重新思考和开发，开源实现 Lime Text Editor 无需多说，Github 主导的 Atom 以及号称下一代 Vim 编辑器的 neovim 都明确受到 Sublime Text 的影响。

## OmniMarkupPreviewer

>作为 Sublime Text 的一款强大插件，支持将标记语言渲染为 HTML 并在浏览器上实时预览，同时支持导出 HTML 源码文件。

### 详细设置

```
${packages} 路径为 /Users/ashfinal/Library/Application Support/Sublime Text 3/Packages/

{
	"server_host": "192.168.1.100",
	<!-- 开启预览服务的 IP 地址, 默认为 localhost. -->

	"browser_command": ["open", "-a", "Google Chrome", "{url}"],
	<!-- 你完全可以在 Mac 上编辑 Markdown 文档，而把 iPad 当作外接显示器来实时预览 -->
	// User public static files should be placed into
	// ${packages}/User/OmniMarkupPreviewer/public/
	// User templates should be placed into:
	// ${packages}/User/OmniMarkupPreviewer/templates/
	// Requires browser reload

	"html_template_name": "Evolution Yellow",
	// list of renderers to be ignored, case sensitive.
	// Valid renderers are: "CreoleRenderer", "MarkdownRenderer", "PodRenderer",
	// "RDocRenderer", "RstRenderer", "TextitleRenderer"
	// for example, to disable Textile and Pod renderer:
	// "ignored_renderers": ["TextitleRenderer", "PodRenderer"]

	"ignored_renderers": ["CreoleRenderer", "PodRenderer", "RDocRenderer", "TextitleRenderer", "LiterateHaskellRenderer"],

	"mathjax_enabled": false,
	// MarkdownRenderer options

	"renderer_options-MarkdownRenderer": {
	// Valid extensions:
	// - OFFICIAL (Python Markdown) -
	// "extra": Combines ["abbr", "attr_list", "def_list", "fenced_code", "footnotes", "tables", "smart_strong"]
	// For PHP Markdown Extra(http://michelf.ca/projects/php-markdown/extra/)
	// "abbr": http://packages.python.org/Markdown/extensions/abbreviations.html
	// "attr_list": http://packages.python.org/Markdown/extensions/attr_list.html
	// "def_list": http://packages.python.org/Markdown/extensions/definition_lists.html
	// "fenced_code": http://packages.python.org/Markdown/extensions/fenced_code_blocks.html
	// "footnotes": http://packages.python.org/Markdown/extensions/footnotes.html
	// "tables": http://packages.python.org/Markdown/extensions/tables.html
	// "smart_strong": http://packages.python.org/Markdown/extensions/smart_strong.html
	// "codehilite": http://packages.python.org/Markdown/extensions/code_hilite.html
	// "meta": http://packages.python.org/Markdown/extensions/meta_data.html
	// "toc": http://packages.python.org/Markdown/extensions/toc.html
	// "nl2br": http://packages.python.org/Markdown/extensions/nl2br.html
	// - 3RD PARTY -
	// "strikeout": Strikeout extension syntax - `This ~~is deleted text.~~`
	// "subscript": Subscript extension syntax - `This is water: H~2~O`
	// "superscript": Superscript extension syntax 0 `2^10^ = 1024`
	// "smarty" or "smartypants": Python-Markdown extension using smartypants to emit
	// typographically nicer ("curly") quotes, proper
	// ("em" and "en") dashes, etc.
	// See: http://daringfireball.net/projects/smartypants/
	// And: https://github.com/waylan/Python-Markdown/blob/master/docs/extensions/smarty.txt

	"extensions": ["extra", "codehilite", "toc", "strikeout", "smarty", "subscript", "superscript"]
}
```

### 配色美化

[github.css](https://github.com/luuman/sublime-config/blob/master/OmniMarkupPreviewer/public/github.css "github.css")
