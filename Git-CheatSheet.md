# Git Cheat Sheet

#### Undo a delete

```bash
git checkout -f
```
CAUTION: commit uncommitted files before executing this command, otherwise you're going to lose them all.

[Undo delete in Git](http://stackoverflow.com/a/9478062/6146580)

#### Undo a git add

```bash
git reset
```

[Undo a git add - remove files staged for a git commit](http://data.agaric.com/undo-git-add-remove-files-staged-git-commit)

#### Undo the last commit

```bash
git reset HEAD~
```
[A more detailed example](https://stackoverflow.com/a/927386/6146580)

#### Undo git revert HEAD

```bash
git reset --hard HEAD^
```
[Discussion](https://stackoverflow.com/a/3662556/6146580)

#### Resolve your branch is ahead of 'origin/master' by x commits

```bash
git rebase -i origin/master
```
Typically, you would use `git reset --hard origin/master` but in this case I wanted to see how the local master differed from the remote one. See [Your branch is ahead of 'origin/master' by 3 commits](https://stackoverflow.com/a/16288283/6146580).

#### Determine from where a local repository was cloned

```bash
git remote show origin
```
Or if referential integrity has been broken:
```bash
git config --get remote.origin.url
```
[How can I determine the URL that a local Git repository was originally cloned from?](https://stackoverflow.com/questions/4089430/how-can-i-determine-the-url-that-a-local-git-repository-was-originally-cloned-fr)

#### Push an existing repository from the command line

```bash
git remote add origin https://github.com/gkhays/orientdb-testdrive.git
git push -u origin master
```

#### Push the curent branch and set the remote as upstream

```bash
git push --set-upstream origin developer
```

#### Create a new repository on the command line

```bash
touch README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/gkhays/orientdb-testdrive.git
git push -u origin master
```

```bash
git fetch --prune
-p, --prune
```
After fetching, remove any remote-tracking branches which no longer exist on the remote -- http://stackoverflow.com/a/15124916/6146580

### Possible Aliases

```bash
alias ga='git add'
alias gaa='git add .'
alias gaaa='git add --all'
alias gau='git add --update'
alias gb='git branch'
alias gbd='git branch --delete '
alias gc='git commit'
alias gcm='git commit --message'
alias gcf='git commit --fixup'
alias gco='git checkout'
alias gcob='git checkout -b'
alias gcom='git checkout master'
alias gcos='git checkout staging'
alias gcod='git checkout develop'
alias gd='git diff'
alias gda='git diff HEAD'
alias gi='git init'
alias glg='git log --graph --oneline --decorate --all'
alias gld='git log --pretty=format:"%h %ad %s" --date=short --all'
alias gm='git merge --no-ff'
alias gma='git merge --abort'
alias gmc='git merge --continue'
alias gp='git pull'
alias gpr='git pull --rebase'
alias gr='git rebase'
alias gs='git status'
alias gss='git status --short'
alias gst='git stash'
alias gsta='git stash apply'
alias gstd='git stash drop'
alias gstl='git stash list'
alias gstp='git stash pop'
alias gsts='git stash save'
```
From [Git Command-Line Shortcuts](https://jonsuh.com/blog/git-command-line-shortcuts/).

### Self-Signed Certificates

To initially clone the repository, set an environment variable.

```bash
$ export GIT_SSL_NO_VERIFY=1
```

Then clone:

```bash
$ git clone https://<repo>.git
```

It is possible to globally disable certificate verification, `--global`, but the best practice is to only do it on repos you trust.

```bash
$ git config http.sslVerify false
```
or
```bash
$ git -c http.sslVerify=false
```

It would be insecure to disable certificate validation on a global basis, so as a rule don't do it, e.g. avoid `$ git config --global http.sslVerify false`.

```bash
$ git config --system http.sslCAPath /path/to/cacerts
```

#### From WikiLeaks [Vault 7](https://wikileaks.org/ciav7p1/cms/page_1179773.html)
```bash
# Issue: When attempting to clone (or any other command that interacts with the 
# remote server) git by default validates the presented SSL certificate by the 
# server.  Our server's certificate is not valid and therefore git exits out with 
# an error. Resolution(Linux): For a one time fix, you can use the env command 
# to create an environment variable of GIT_SSL_NO_VERIFY=TRUE. 
$ env GIT_SSL_NO_VERIFY=TRUE git <command> <arguments>


# If you don't want to do this all the time, you can change your git configuration:
$ git config --global http.sslVerify false
```

#### References
[How can I make git accept a self signed certificate?](http://stackoverflow.com/a/11622001/6146580)<br/>
[How do I set GIT_SSL_NO_VERIFY for specific repos only?](http://stackoverflow.com/a/9008394/6146580)<br/>
[server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none](http://stackoverflow.com/a/21181447/6146580)<br/>
[configure Git to accept a particular self-signed server certificate for a particular https remote](http://stackoverflow.com/a/16543283/6146580)<br/>
[Https certificate errors for GitHub using git on Windows 7](http://stackoverflow.com/a/32318742/6146580)<br/>
[Unable to clone Git repository due to self signed certificate](https://confluence.atlassian.com/fishkb/unable-to-clone-git-repository-due-to-self-signed-certificate-376838977.html)<br/>
https://github.com/iwonbigbro/tools/blob/master/bin/git-remote-install-cert.sh<br/>
[Setting up a repository](https://www.atlassian.com/git/tutorials/setting-up-a-repository)
