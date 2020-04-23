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

#### Discard changes in working directory

```bash
git checkout -- <file>
```

#### Undo git revert HEAD

```bash
git reset --hard HEAD^
```

See [Is there any way to undo the effects of “git revert head”?](https://stackoverflow.com/a/3662556/6146580).

#### Remove a file from a Git repository without deleting it from the local

For single file:

```bash
git rm --cached mylogfile.log
```

For single directory:

```bash
git rm --cached -r mydirectory
```

[--bdonlan](https://stackoverflow.com/a/1143800/6146580)

#### Move uncommitted work to a new branch

```bash
git checkout -b development
git add .
git commit -m "First commit in the new branch"
```

[Move existing, uncommitted work to a new branch in Git](https://stackoverflow.com/a/1394804)

#### Push branch to remote repo

```bash
git push -u origin feature_branch_name
```

#### Show changes to branch

```
git log master..
git log master..<branchname>
```

[How do I run git log to see changes only for a specific branch?](https://stackoverflow.com/a/4649377/6146580)  
[git - changes to branch since created?](https://stackoverflow.com/questions/15954631/git-changes-to-branch-since-created)

#### Sync local repo with remote one

```bash
git fetch --prune
```

Also removes completed branch.
[Sync local repo with remote one](https://stackoverflow.com/a/15124916/6146580)

#### Syncing a fork

```bash
git fetch upstream
git checkout master
git merge upstream/master
```

[Working with forks / Syncing a fork](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/syncing-a-fork)  
[Sync your Git Fork to the Original Repo](https://digitaldrummerj.me/git-sync-fork-to-master/)  
[How do I update a GitHub forked repository?](https://stackoverflow.com/a/7244456/6146580)

Or

```bash
git pull upstream develop
```

#### Switch to a branch and sync

```bash
git pull origin other-branch
```

Which is equivalent to

```bash
git fetch origin other-branch && git merge other-branch
```

See [Git pull a certain branch from GitHub](https://stackoverflow.com/a/1710474).

#### Check out fresh local branch

If the branch exists on origin but not yet locally, do the following.

```bash
git fetch
git checkout test
```

1. [How do I check out a remote Git branch?](https://stackoverflow.com/a/1783426/6146580)
2. [How can I switch to another branch in git?](https://stackoverflow.com/a/47631215/6146580)

#### Fetch remote branch

```bash
git checkout --track origin/daves_branch
```

[Git fetch remote branch](https://stackoverflow.com/a/9537923/6146580)

#### Track an Empty Directory

You cannot commit a completely empty directory in Git. The convention is to add a placeholder file named `.gitkeep` to the target directory.

1. [How can I add an empty directory to a Git repository?](https://stackoverflow.com/a/932982/6146580)
1. [What are the differences between .gitignore and .gitkeep?](https://stackoverflow.com/a/7229996/6146580)

#### Resolve your branch is ahead of 'origin/master' by x commits

```bash
git rebase -i origin/master
```

Typically, you would use `git reset --hard origin/master` but in this case I wanted to see how the local master differed from the remote one. See [Your branch is ahead of 'origin/master' by 3 commits](https://stackoverflow.com/a/16288283/6146580).

#### Rename a local and remote branch

```bash
git checkout <old_name>
git branch -m <new_name>
git push origin -u <new_name>
push origin --delete <old_name>
```

Or

```bash
git branch -m new-name
git push origin :old-name new-name
git push origin -u new-name
```

See [Rename a local and remote branch in git](https://multiplestates.wordpress.com/2015/02/05/rename-a-local-and-remote-branch-in-git/)  
[How To Rename a Local and Remote Git Branch](https://linuxize.com/post/how-to-rename-local-and-remote-git-branch/)

#### Remove and then ignore IDE settings

```bash
git rm --cached .project
git rm --cached .classpath
git rm --cached -r .settings
```

Then add to .gitignore

```
.project
.classpath
.settings/
```

Example .gitignore

```bash
# Eclipse
.classpath
.project
.settings/

# Maven
log/
target/
```

[How to ignore IDE settings on Git?](https://stackoverflow.com/a/24583296/6146580)<br/>
[A .gitignore file for Intellij and Eclipse with Maven](http://gary-rowe.com/agilestack/2012/10/12/a-gitignore-file-for-intellij-and-eclipse-with-maven/)

#### Determine from where a local repository was cloned

```bash
git remote show origin
```

Or if referential integrity has been broken:

```bash
git config --get remote.origin.url
```

Or simply

```bash
git remote -v
```

[How can I determine the URL that a local Git repository was originally cloned from?](https://stackoverflow.com/questions/4089430/how-can-i-determine-the-url-that-a-local-git-repository-was-originally-cloned-fr)

#### Change remote URL

Origin

```bash
git remote set-url origin https://github.com/USERNAME/REPOSITORY.git
git remote set-url origin git@github.com:USERNAME/REPOSITORY.git
```

Upstream

```bash
git remote set-url upstream https://github.com/[Original Owner Username]/[Original Repository].git
git remote set-url upstream git@github.com:[Original Owner Username]/[Original Repository].git
```

#### SSH URLs

```
git@github.com:<repo>/<project>.git
```

#### Push an existing repository from the command line

```bash
git remote add origin https://github.com/gkhays/orientdb-testdrive.git
git push -u origin master
```

#### Push the curent branch and set the remote as upstream

```bash
git push --set-upstream origin developer
```

### Import repository to Bitbucket

Create a new repo in bitbucket.

```bash
git clone <gitlabRepoUrl>
cd <repoName>
git remote add bitbucket <bitbucketRepoUrl>
git push bitbucket master
```

[How to import gitlab repository to bitbucket Repository](https://stackoverflow.com/a/44106169/6146580)

#### Show your configuration

```bash
git config --list
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

### Git Hashes

```bash
$ git describe --tags
v1.0.1-2-g39918b9
```

```bash
$ git rev-parse --short HEAD
39918b9
```

[Get the short Git version hash](https://stackoverflow.com/a/5694416/6146580)  
[git-rev-parse - Pick out and massage parameters](https://git-scm.com/docs/git-rev-parse)

### Diff and Merge

#### Compare Two Git Branches

```bash
gti diff patch/feat36..develop
git log patch/feat36..develop
git log --oneline --graph --decorate --abbrev-commit patch/ig36..develop
```

#### Compare a file between two Git branches

```bash
git diff patch/feat35...patch/feat36 Jenkinsfile
```

[How To Compare Two Git Branches](https://devconnected.com/how-to-compare-two-git-branches/)  
[Comparing two branches in Git?](https://stackoverflow.com/a/9834872/6146580)  
[Showing which files have changed between two revisions](https://stackoverflow.com/a/822859/6146580)  
[git-diff - Show changes between commits, commit and working tree, etc](https://git-scm.com/docs/git-diff)

### Diff Tools

Add the following to `~/.gitconfig`.

```ini
[merge]
	tool = bc3
[diff]
	tool = bc3
[difftool "bc3"]
	cmd = "\"C:/Program Files (x86)/Beyond Compare 3/bcomp.exe\" \"$LOCAL\" \"$REMOTE\""
[mergetool "bc3"]
	cmd = "\"c:/program files (x86)/beyond compare 3/bcomp.exe\" \"$LOCAL\" \"$REMOTE\" \"$BASE\" \"$MERGED\""
```

Invoke the diff tool.

```bash
D:\src\test-remote (master -> origin)
λ git difftool -t bc3 src/main/org/gkh/test/remote/JarCommand.java

Viewing (1/1): 'src/main/java/org/gkh/test/remote/JarCommand.java'
Launch 'bc3' [Y/n]? y
```

### [Flight rules for git](https://github.com/k88hudson/git-flight-rules)

### Git and Passwords

```bash
git config --global --unset user.password
```

Caching your Git Password On Windows

```bash
$ git config --global credential.helper wincred
```

- [How do I update the password for Git?](https://stackoverflow.com/a/20195558/6146580)
- https://git-scm.com/book/gr/v2/Git-Tools-Credential-Storage
- [git credential helper - update password](https://stackoverflow.com/a/25846817/6146580)
- [Caching Your Password](https://help.github.com/articles/caching-your-github-password-in-git/)

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

Alternatively, using the `-c` switch

```bash
$ git -c http.sslVerify=false clone https://github.com/gkhays/cheatsheets.git
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

#### Expected Committer Email

```bash
git commit --amend --allow-empty --author="FirstName LastName <name@email.com>"
git commit --amend --reset-author
```

- https://stackoverflow.com/a/28425852/6146580
- https://stackoverflow.com/a/33009142/6146580

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

## References

[Git vs SVN commands](https://backlog.com/git-tutorial/reference/commands/)  
[How can I make git accept a self signed certificate?](http://stackoverflow.com/a/11622001/6146580)  
[How do I set GIT_SSL_NO_VERIFY for specific repos only?](http://stackoverflow.com/a/9008394/6146580)  
[server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none](http://stackoverflow.com/a/21181447/6146580)  
[configure Git to accept a particular self-signed server certificate for a particular https remote](http://stackoverflow.com/a/16543283/6146580)  
[Https certificate errors for GitHub using git on Windows 7](http://stackoverflow.com/a/32318742/6146580)  
[Unable to clone Git repository due to self signed certificate](https://confluence.atlassian.com/fishkb/unable-to-clone-git-repository-due-to-self-signed-certificate-376838977.html)  
https://github.com/iwonbigbro/tools/blob/master/bin/git-remote-install-cert.sh  
[Setting up a repository](https://www.atlassian.com/git/tutorials/setting-up-a-repository)
