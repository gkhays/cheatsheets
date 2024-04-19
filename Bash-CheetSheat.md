# Bash Cheat Sheet

### Return to Previous Directory
```bash
cd -
```

### Find Previous Command
Also known as `reverse-i-search`
```bash
Ctrl + R <match>
```

### Here-Document
```bash
$ wc << EOF
> one two three
> four five
> EOF
2 5 24

See also "here-string
```bash
command <<<$word
```
