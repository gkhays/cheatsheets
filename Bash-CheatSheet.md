# Bash Cheat Sheet

### Move to Start of the Line
```bash
Ctrl + a
```

### Move to End of the Line
```bash
Ctrl + e
```

### Return to Previous Directory
```bash
cd -
```

### Find Previous Command
Also known as `reverse-i-search`
```bash
Ctrl + R <match>
```

### Show How Command Will Be Interpreted
```bash
type -a <command>
```
E.g.
```bash
type -a bash
bash is /opt/homebrew/bin/bash
bash is /bin/bash
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
