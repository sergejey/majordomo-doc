---
title: Documentation
linkTitle: Docs
menu: {main: {weight: 20}}
weight: 20
---
 
- [Google Docsy](https://www.docsy.dev/)
- [Markdown Basics](https://www.markdownguide.org/cheat-sheet/)  
- [Hugo Markdown](https://www.markdownguide.org/tools/hugo/)  
- [Emojis](https://gohugo.io/quick-reference/emojis/)  

{{% pageinfo %}}
This is a placeholder page that shows you how to use this template site.
{{% /pageinfo %}}

# Header 1
## Header 2
### Header 3
#### Header 4

> Callout title
> 
> Text

**Bold text**

*Italic Text*

~~Strike through~~

Un-ordered list:
- Item 1
- Item 2
- Item 3

Ordered list:
1. Item 1
2. Item 2
3. Item 3

```php
echo "Some code goes here";
```

{{% alert title="Alert title" %}}
Alert content
{{% /alert %}}

{{% alert title="Warning title" color=warning %}}
Alert content
{{% /alert %}}

| Param        | Description  |
| ---------------- | ------------|
| `height` | See above.
| `color` | See above.
| `type`  | Specify "container" (the default) if you want a general container, or "row" if the section will contain columns -- which must be immediate children.


{{< tabpane >}}
{{< tab header="Tabpane title:" disabled=true />}}
{{< tab header="JavaScript" lang="javascript" >}}
alert('zz');
{{< /tab >}}
{{< tab header="PHP" lang="php" >}}
echo('zz');
{{< /tab >}}
{{< tab header="JSON" lang="json" >}}
data: "Value"
{{< /tab >}}
{{< /tabpane >}}

### PlantUML
[PlantUML web-site](https://plantuml.com/)
```plantuml
participant participant as Foo
actor       actor       as Foo1
boundary    boundary    as Foo2
control     control     as Foo3
entity      entity      as Foo4
database    database    as Foo5
collections collections as Foo6
queue       queue       as Foo7
Foo -> Foo1 : To actor
Foo -> Foo2 : To boundary
Foo -> Foo3 : To control
Foo -> Foo4 : To entity
Foo -> Foo5 : To database
Foo -> Foo6 : To collections
Foo -> Foo7: To queue
```

### Markmap
```markmap
# markmap

## Links

- <https://markmap.js.org/>
- [GitHub](https://github.com/gera2ld/markmap)

## Related

- [coc-markmap](https://github.com/gera2ld/coc-markmap)
- [gatsby-remark-markmap](https://github.com/gera2ld/gatsby-remark-markmap)

## Features

- links
- **inline** ~~text~~ *styles*
- multiline
  text
- `inline code`
-
    ```js
    console.log('code block');
    ```
- Katex - $x = {-b \pm \sqrt{b^2-4ac} \over 2a}$
```