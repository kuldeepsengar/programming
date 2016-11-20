---
layout : post
title : 'Markdown and Pandoc'
subtitle : 'for all types of writings'
date : 2016-11-17 00:00:00
categories : [tool]
---

**Abstract**. Markdown has been widely used documentation format. It is simpler than *LateX*, enabling easy to read as-is, without much knowing about the format semantics. Mostly used for writing readme files for the projects, it can be efficiently used to write an article or a document very easily. Whereas Markdown can be converted to many format, Pandoc is seen as a universal document converter from one format to other. This article explores various ways you can use to create articles, paper, journals and almost every type of documentation using Markdown and Pandoc.

# Pandoc
- Pandoc is a universal format converter.
- Written in haskell
- Released as *Markdown of Haskell* under *[RFC-7764](https://tools.ietf.org/html/rfc7764)*
    - an extension of markdown format that can be converted to html and many more...
    - Has grown to become a univeral converter having supporting many libraries.
- Comes as a standalone program as well as a haskell package.

## Command line tool

### Installation
For Installing standalone tool, you can download appropriate version from [here](http://pandoc.org/installing.html).


### Converting between formats

By default pandoc works as a pipeline, running ```pandoc``` would just take stdin as an input and when you press **ctrl+d** it will convert the text to html.

Or you can provide files using:

``` pandoc <input-file> -o <output-file>   ```

Some Examples are:

- *stdin* to *latex* ::
``` pandoc -to latex ```
- *latex* to *markdown* ::
``` pandoc example.tex -o example.markdown ```
- Create a standalone result to html::
``` pandoc -s example.tex -o example.html ```

> ```-s``` or ```--standalone``` is needed if you want to generate a whole ```.html``` file. Without the flag you'll be getting a fragmented file.

> For converting to pdf you can install PdfLateX, similarly for LateX you can either use MacLateX or BasicLateX.

Pandoc provides different ways to structure your document like *table of content*, *bibiliography*, *citations*, etc, which we will use to create in this article.


# Markdown
Markdown began as a plain text and a perl html processor.It targeted the non technical users to use unspecialized tools such as plain text email client.

Markdown initially didn't have a notion of validity, There are many implementations of markdown format. [rfc7763](https://tools.ietf.org/html/rfc7763) incorporated the *text/markdown* media type as well introduced the various implementation of markdown like - multi markdown, pandoc, etc.

## Styling

Markdown provides basic styling functionalities like:

# Heading1 - ``` #h1 ```
## Heading2 - ``` ##h2 ```
.
.
.

**bold** - ``` **bold** ```

*italic* - ``` *italic* ```

and so on...


----
This is Work in progress, there will be more updates for this article.
