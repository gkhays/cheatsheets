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

### Change Expiration
**Note**: must be in edit mode. Remember to save afterwards.
```
gpg> expire
```

## Other Cheat Sheets

https://gock.net/blog/2020/gpg-cheat-sheet
