# GPG Cheat Sheet

### List Private Keys
(uppercase `K`) or just use long form: `--list-secret-keys`
```
gpg -K
```

### List Public Keys
(lowercase `k`) or just use long form: `--list-keys`
```
gpg -k
```

### Edit Key
Typically to extend expiration.
```
gpg --edit-key <key_id>
```

Remember to save afterwards from the `gpg>` prompt.
```
gpg> save
```

### Trust Imported Key
**Note**: must be in edit mode. Remember to save afterwards.
```
gpg --edit-key <key_id>
gpg> trust
```

E.g.
```
Please decide how far you trust this user to correctly verify other users' keys
(by looking at passports, checking fingerprints from different sources, etc.)
  1 = I don't know or won't say
  2 = I do NOT trust
  3 = I trust marginally
  4 = I trust fully
  5 = I trust ultimately
  m = back to the main menu
```

### Change Expiration
```
gpg --edit-key <key_id>
gpg> expire
```

### Export Public Key
```
gpg --output public.pgp --armor --export username@email
```

### Export Secret Key
```
gpg --output private.pgp --armor --export-secret-key username@email
```

### Import Pulic Key
```
gpg --import public.txt
```

### Import Private Key
```
gpg --import private.txt
```

### Stop the GPG Agent
```
gpgconf --kill gpg-agent
```

### Restart the GPG Agent
```
gpg-connect-agent reloadagent /bye
```

### Change PIN Entry Method
I am getting a command line prompt for the GPG passphrase.
```
┌────────────────────────────────────────────────────────────────┐
│ Please enter the passphrase to unlock the OpenPGP secret key:  │
│ "My Name <my.email@example.com>"                               │
│ 4096-bit RSA key, ID A1B2C3D4E5F67890,                         │
│ created 2020-08-10.                                            │
│                                                                │
│                                                                │
│ Passphrase: __________________________________________________ │
│                                                                │
│         <OK>                                    <Cancel>       │
└────────────────────────────────────────────────────────────────┘
```
But I want a Windows UI prompt.

![image](https://github.com/user-attachments/assets/f374b2c1-18db-44f1-b243-f6ade869789a)


Edit `~/.gnupg/gpg-agent.conf` and add the following.
```
pinentry-program "/mnt/c/Program Files/Git/usr/bin/pinentry-w32.exe"
```

### Test Key
```bash
echo "test" | gpg --clearsign
```

## GPG Tools
A collection of GPG tools for Windows and Linux.

- [GPG Suite](https://gpgtools.org/)
- [Gpg4win](https://www.gpg4win.org/)
- [Kleopatra](https://www.openpgp.org/software/kleopatra/)
- [Pinentry](https://www.gnupg.org/related_software/pinentry/index.html)

## Other Cheat Sheets

https://gock.net/blog/2020/gpg-cheat-sheet
