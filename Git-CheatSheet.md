Undo a git add

```bash
git reset
```

[Undo a git add - remove files staged for a git commit](http://data.agaric.com/undo-git-add-remove-files-staged-git-commit)

Create a new repository on the command line

```bash
touch README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/gkhays/orientdb-testdrive.git
git push -u origin master
```

Push an existing repository from the command line

```bash
git remote add origin https://github.com/gkhays/orientdb-testdrive.git
git push -u origin master
```

```bash
git fetch --prune
-p, --prune
```
After fetching, remove any remote-tracking branches which no longer exist on the remote -- http://stackoverflow.com/a/15124916/6146580
