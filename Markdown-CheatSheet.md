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
```
![](images/img.png | width=100)
![](images/img.png =250x250
```
More... https://gist.github.com/uupaa/f77d2bcf4dc7a294d109

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

### Strike-Through

```
~~strike-through~~
```

- [x] ~~*Show how to do strike-through*~~

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

