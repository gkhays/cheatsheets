# Subversion Cheat Sheet

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

[What do the result codes in SVN mean?](https://stackoverflow.com/a/40470073/6146580)
