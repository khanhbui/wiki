## Delete multiple branches

### Local branches

```sh
git branch | grep 'xxx' | while read line ; do git branch -D $line; done; 
```

### Remote branches

```sh
git branch | grep 'xxx' | while read line ; do git push origin :$line; done; 
```
