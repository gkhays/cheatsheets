# SSH Settings

### SSH Version

```
ssh -V
```

### Verify Connection

```
ssh -T git@github.com
```

---
- [ ] Is this really a cheat sheet? Or perhaps a longer form Gist article?

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

>This solution from [Joseph M. Reagle](https://www.cygwin.com/ml/cygwin/2001-06/msg00537.html) by way of Daniel Starin:

```
SSH_ENV="$HOME/.ssh/environment"

function start_agent {
     echo "Initialising new SSH agent..."
     /usr/bin/ssh-agent | sed 's/^echo/#echo/' > "${SSH_ENV}"
     echo succeeded
     chmod 600 "${SSH_ENV}"
     . "${SSH_ENV}" > /dev/null
     /usr/bin/ssh-add;
}

# Source SSH settings, if applicable

if [ -f "${SSH_ENV}" ]; then
     . "${SSH_ENV}" > /dev/null
     #ps ${SSH_AGENT_PID} doesn't work under cywgin
     ps -ef | grep ${SSH_AGENT_PID} | grep ssh-agent$ > /dev/null || {
         start_agent;
     }
else
     start_agent;
fi
```

## References

1. [Using ssh-agent with ssh](http://mah.everybody.org/docs/ssh)
1. [Start ssh-agent on login](https://stackoverflow.com/a/18915067/6146580)
1. [How can I run ssh-add automatically, without a password prompt?](https://unix.stackexchange.com/a/90869)
