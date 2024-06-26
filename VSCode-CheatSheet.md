# VS Code Cheat Sheet

### Go to File

```
Ctrl + P
```

My replacement for `Ctrl + Shift + R` in Eclipse.

### Go to Symbol

```
Ctrl + Shift + O
```

My replacement for `Ctrl + O` in Eclipse.

[Code Navigation](https://code.visualstudio.com/docs/editor/editingevolved)

## Vertical Editing

### Change Repeating Multi-line String

```
Ctrl + F
Alt + Enter
```

[Multiline editing in Visual Studio Code](https://stackoverflow.com/a/45277437/6146580)

### Edit Settings.json

```
Ctrl + Shift + P
```

Then type "open settings."

### Code Formatting

- On Windows `Shift + Alt + F`
- On Mac `Shift + Option + F`
- On Ubuntu `Ctrl + Shift + I`

https://stackoverflow.com/a/29973358/6146580

See also the `Prettier` VSCode Extension.

### Delete Line

```
Shift + Del
```

[Delete a line in Visual Studio without copying it?](https://superuser.com/questions/194004/delete-a-line-in-visual-studio-without-copying-it)

### Toggle Comment

```
Ctrl + K + C
Ctrl + /
```

### Column Select

```
Shift + Alt then drag mouse
Ctrl + Shift + Alt then arrow keys
```

[Selecting columns in Visual Studio Code](https://superuser.com/a/1087720)

### Open Terminal

```
Ctrl + `
```

### Markdown Preview

`Ctrl + Shift + V` To switch between views

`Ctrl + K V` Side-by-side

https://code.visualstudio.com/docs/languages/markdown

## Open with VS Code

I wasn't paying attention to the installer and missed this feature. 😦

![Open with Code](images/open-with-code.png)

`Computer\HKEY_CLASSES_ROOT\Directory\shell\vscode`

![Win Reg](images/vscode-reg.png)

[Open with VS Code from right click in Windows Explorer](https://github.com/Microsoft/vscode/issues/12147)

## Java

### JVM Arguments

In `launch.json`

```json
"vmArgs": [
    "-Xms256m",
    "-Xmx256m",
    "-XX:+HeapDumpOnOutOfMemoryError",
    "-XX:HeapDumpPath=${workspaceFolder}/gc.hprof"
]
```

[Launch Options](https://code.visualstudio.com/docs/java/java-debugging#_launch)

### Organize imports

```
Alt + Shift + O (Windows)
Option + Shift + O (Mac)
```

[Is there a way to remove unused imports and declarations from Angular 2+?](https://stackoverflow.com/a/46722805/6146580)

## HTML

[HTML in Visual Studio Code](https://code.visualstudio.com/Docs/languages/html)

### Emmet

#### New HTML Template

Emmet abbreviation for new HTML document.

```
! + Tab
```

Output:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Document</title>
  </head>
  <body></body>
</html>
```

## Extensions

### GitLens

#### Accept All Incoming Changes

```console
Ctrl+Shift+P merge
Merge Conflict: Accept All Incoming
```

![Merge](images/vscode-merge.png)

[How can I accept all current changes in VSCode at once?](https://stackoverflow.com/a/59574283)

### Docker

### REST Client

### Prettier

```
Settings >> Editor: Format On Save
```

[Prettier - Code formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) ([On GitHub](https://github.com/prettier/prettier-vscode))

See also [js-beautify for VS Code](https://marketplace.visualstudio.com/items?itemName=HookyQR.beautify).

### CSS Peek

`Go To Definition` and `Go To Symbol in Workspace` support for `CSS`.

[CSS Peek](https://marketplace.visualstudio.com/items?itemName=pranaygp.vscode-css-peek)

### Material Icon Theme

[Material Icon Theme](https://marketplace.visualstudio.com/items?itemName=PKief.material-icon-theme)

### Visual Studio IntelliCode

### Remote-WSL

### Live Server

- [Live Server | VSCode Extension](https://ritwickdey.github.io/vscode-live-server/)
- [VSCode Live Server](https://github.com/ritwickdey/vscode-live-server) (GitHub)

### Python

### Auto Rename Tag

[Auto Rename Tag](https://marketplace.visualstudio.com/items?itemName=formulahendry.auto-rename-tag)

### Shades of Purple

### Peacock
