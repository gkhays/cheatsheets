# GitHub Cheat Sheet

### Set up remote repository from the command line

```
git remote add origin https://github.com/VijayNew/NewExample.git
```

See [Why does Git tell me “No such remote 'origin'” when I try to push to origin?](http://stackoverflow.com/a/25504199/6146580)

### Rename a repository

Click on Settings.

![Settings](images/settings.png)

Type in the new name and click on Rename.

![Rename](images/rename.png)

See http://stackoverflow.com/a/2042020/6146580.

### Close issues using keywords in commit message

```
fix #n
close #n
resolve #n
```

- [Link to the issue number on GitHub within a commit message](https://stackoverflow.com/a/6742691/6146580)
- [Closing issues using keywords](https://help.github.com/en/github/managing-your-work-on-github/closing-issues-using-keywords)
- [Mastering Issues](https://guides.github.com/features/issues/)

### Link to an issue or PR in a different repo

```md
jlord/sheetsee.js#26
```

- [Issues and pull requests](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/autolinked-references-and-urls#issues-and-pull-requests)

### GitHub Wiki Sidebar

```
npm install github-wiki-sidebar -g
github-wiki-sidebar --git-push
```

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=gkhays/til,gkhays/cheatsheets&type=Date)](https://star-history.com/#gkhays/til&gkhays/cheatsheets&Date)

## GitHub Desktop

### Launch GitHub Desktop from the Command Line

```
github
```

[Ssh-agent is running. Authentication failed. I cannot push on repos I cloned using git bash. #7360](https://github.com/desktop/desktop/issues/7360#issuecomment-578807630)

## References

1. [GitHub Secrets](https://github.blog/2011-10-21-github-secrets/)
1. [How to rename a directory/folder on GitHub website?](https://stackoverflow.com/a/32620165/6146580)
1. [GitHub Wiki Sidebar](https://www.npmjs.com/package/github-wiki-sidebar)
