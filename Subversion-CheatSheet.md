# Subversion Cheat Sheet

### Revert the change to a single file
```bash
$ svn merge -r HEAD:PREV <file>
```
Related: [How do I return to an older version of our code in Subversion?](https://stackoverflow.com/a/814436/6146580)

### Commit with a changelist
```bash
$ svn changelist my-changelist mydir/dir1/file1.c mydir/dir2/myfile1.h
$ svn changelist my-changelist mydir/dir3/myfile3.c etc.
... (add all the files you want to commit together at your own rate)
$ svn commit -m"log msg" --changelist my-changelist
```

### Review changelist
```bash
$ svn status

--- Changelist 'math-fixes':
        button.c
M       integer.c
M       mathops.c
```

Source: [SVN - How to commit multiple files in a single shot](https://stackoverflow.com/a/4335763/6146580)<br/>
Reference: [svn changelist (cl)](http://svnbook.red-bean.com/en/1.6/svn.ref.svn.c.changelist.html)

### Simulate Git Stash
```bash
svn diff > patch_name.patch; svn revert -R .    # git stash
patch -p0 < patch_name.patch                    # git stash apply
```

Source: [Temporarily put away uncommitted changes in Subversion (a la “git-stash”)](https://stackoverflow.com/a/3391053)
See also: [Using patch as a subversion stash](http://blog.jayfields.com/2008/02/using-patch-as-subversion-stash.html) by Jay Fields

### Update Repo URL
```
$ svn relocate https://sub.someaddress.com.tr/project
```

[Change SVN repository URL](https://stackoverflow.com/a/13944343/6146580)

### SVN Result Codes
```bash
$ svn help status
```

```
  The first seven columns in the output are each one character wide:
    First column: Says if item was added, deleted, or otherwise changed
      ' ' no modifications
      'A' Added
      'C' Conflicted
      'D' Deleted
      'I' Ignored
      'M' Modified
      'R' Replaced
      'X' an unversioned directory created by an externals definition
      '?' item is not under version control
      '!' item is missing (removed by non-svn command) or incomplete
      '~' versioned item obstructed by some item of a different kind
```
The StackOverflow article also has an helpful one-liner.
```bash
svn help status | grep \'\?\'
svn help status | grep \'\!\'
svn help status | grep \'\YOUR_SYMBOL_HERE\'
```

[What do the result codes in SVN mean?](https://stackoverflow.com/a/2036/6146580)
