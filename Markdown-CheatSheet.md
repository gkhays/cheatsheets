# Markdown Cheat Sheet

### Open link in new window
`<a href="http://example.com/" target="_blank">example</a>`

Runner up: works for Jekyll, but not Markdown

`[link](url){:target="_blank"}`

[Markdown open a new window link](http://stackoverflow.com/a/5803384/6146580)

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
