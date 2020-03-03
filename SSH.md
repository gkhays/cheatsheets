# SSH Settings

### Bash (or other) Profile

Add the following to `.profile` (preferred) or `.bash_profile`
```
# SSH
eval $(ssh-agent -s)
ssh-add ~/.ssh/ghe_rsa
trap $(kill $SSH_AGENT_PID) EXIT
```

>`.bash_profile` is specific to bash, `.profile` is generic to all POSIX shells. `bash` will look first for .bash_profile, then default to `.profile`. – Barmar Sep 18 '13 at 20:54

>The correct way to spawn ssh-agent for a "standard" (POSIX-compatible) shell is eval `$(ssh-agent -s)`. Note also that you have to make sure you properly get rid of the agent when you log out, so it's also advisable to put `trap 'kill $SSH_AGENT_PID' EXIT` in your `.profile` after the line which starts the agent. – kostix Sep 19 '13 at 10:16 

## References

1. [Using ssh-agent with ssh](http://mah.everybody.org/docs/ssh)
1. [Start ssh-agent on login](https://stackoverflow.com/a/18915067/6146580)
