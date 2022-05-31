# Git power tools

https://nvie.com/posts/git-power-tools/

```
$ git commit -m 'Bugfix for login screen'

# Oops, I should've split this one up. Let's start over!
$ git delouse
$ git add -p     # Just pick the bugfix bits
$ git fixup
$ git add -p     # Now pick the var rename bits
$ git commit -m 'Rename variable name to be clearer'
```

This