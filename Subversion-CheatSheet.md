# Subversion Cheat Sheet

### Commit with a changelist
```bash
$ svn changelist my-changelist mydir/dir1/file1.c mydir/dir2/myfile1.h
$ svn changelist my-changelist mydir/dir3/myfile3.c etc.
... (add all the files you want to commit together at your own rate)
$ svn commit -m"log msg" --changelist my-changelist
```
Source: [SVN - How to commit multiple files in a single shot](https://stackoverflow.com/a/4335763/6146580)<br/>
Reference: [svn changelist (cl)](http://svnbook.red-bean.com/en/1.6/svn.ref.svn.c.changelist.html)
