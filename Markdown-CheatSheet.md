# Markdown Cheat Sheet

![logo](images/64px-Markdown-mark.svg.png)

### Open link in new window
`<a href="http://example.com/" target="_blank">example</a>`

Runner up: works for Jekyll, but not Markdown

`[link](url){:target="_blank"}`

[Markdown open a new window link](http://stackoverflow.com/a/5803384/6146580)

### Hide Details

This is more of an HTML "cheat" but comes in handy in pull requests and other Markdown documents where you may wish to save on screen "real estate."

```html
<details>
  <summary>Details Example</summary>
  <p>Here are the details!</p>
</details>
```

E.g.

<details>
  <summary>Details Example</summary>
  
```html
<details>
  <summary>Details Example</summary>
  <p>Here are the details!</p>
</details>
```
</details>

See the [jsfiddle](https://jsfiddle.net/gkhays/3gaev1k8/).

### Resize an Image
```html
<img src="images/img.png" width="100">
```
For Jekyll
```
![](images/img.png | width=100)
![](images/img.png =250x250
```
More... https://gist.github.com/uupaa/f77d2bcf4dc7a294d109  
- https://gist.github.com/stevecondylios/dcadb4fc73e63f27a3bbcf17e52058bf  
- https://stackoverflow.com/a/14747656  
- https://stackoverflow.com/a/26138535

### Illustrate command line or shell commands
Use `console` as the language
<pre>
```console
$ ls
```
</pre>
E.g.
```console
$ ls
```
`bash` or `bat` work as well

* [Defines all Languages known to GitHub](https://github.com/github/linguist/blob/master/lib/linguist/languages.yml)
* [Syntax highlighting in markdown](https://support.codebasehq.com/articles/tips-tricks/syntax-highlighting-in-markdown)

### Check Box

```
- [ ] One
- [x] Two
```

- [ ] One
- [x] Two

### Callouts

```
> [!NOTE]
> Pay extra attention! 😎
```

> [!NOTE]
> Pay extra attention! 😎

### Strike-Through

```
~~strike-through~~
```

- [x] ~~*Show how to do strike-through*~~

### Internal Link
Useful in a table of contents.
Represent spaces with a `-`.
```
[Go to this href](#heading)
```

I didn't know you could do this! Numbered sections.
```
#1. Go
#2. Python
#3. Java
#4. JavaScript
```

Then add a reference:
```
[1. Go](#1-go)
[2. Python](#2-python)
[3. Java](#3-java)
[4. JavaScript](#4-javascript)
```

[Footnotes](#footnotes)

* [How to link to part of the same document in Markdown?](https://stackoverflow.com/a/16426829/6146580)
* [Numbered sections in Markdown?](https://stackoverflow.com/a/72756103/6146580)

### Footnotes

```
To quote myself. [^1]

[^1]: I said this would be the first footnote.
```

To quote myself. [^1]

[^1]: I said this would be the first footnote.

### Math Symbols

A little flex with LaTeX! 😇

```
- Inline: $E = mc^2$
- Block:

$$
\int_{-\infty}^\infty e^{-x^2} dx = \sqrt{\pi}
$$
```

Inline: $E = mc^2$

Block:

$$
\int_{-\infty}^\infty e^{-x^2} dx = \sqrt{\pi}
$$

### Line Breaks

I didn't know this one! I always used `<br/>`.

To create a line break, add 2 or more spaces to the end.

```
Line one.  
Line two.^^
```

Line one.  
Line two.

## References

1. [Daring Fireball - Markdown](https://daringfireball.net/projects/markdown/)
1. [Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) by [adam-p](https://github.com/adam-p)
1. [Markdown Syntax Guide](https://sourceforge.net/p/checkbox/wiki/markdown_syntax/) by mjaniczkova
1. [Markdown Cheat Sheet](https://www.markdownguide.org/cheat-sheet/)
1. [Markdown Guide](https://www.markdownguide.org/basic-syntax)
1. [GitHub Markdown Alerts](https://github.com/orgs/community/discussions/16925)
1. [Your life need to be MARKDOWNED: Essential Tips for Exceptional GitHub Writing](https://medium.com/@1chooo/vyour-life-need-to-be-markdowned-essential-tips-for-exceptional-github-writing-08c23ddc3464)
