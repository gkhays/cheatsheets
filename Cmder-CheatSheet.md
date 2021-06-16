# Cmder Cheat Sheet

### Grep History

Cmder has an alias for history.

```console
history=cat "%CMDER_ROOT%\config\.history"
```

But you can't `grep` against the alias, e.g.

```console
history | grep "docker run"
```

Instead you must use the content of the `doskey` macro.

> In Cmder::Cmder sessions history is a doskey macro. The output of a macro cannot be passed using the pipe | but you could use the command that is the content of the doskey macro as shown below:

```console
C:\Users\user\cmder
λ cat %CMDER_ROOT%\config\.history | grep cmder
```

## References

1. [Can't Pipe history to grep #1770](https://github.com/cmderdev/cmder/issues/1770)
1. [Is there a way to filter the command history in Windows using cmder?](https://superuser.com/a/1619906/1100004)
