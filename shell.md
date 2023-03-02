## Delete multiple branches

### Local branches

```sh
git branch | grep 'xxx' | while read line ; do git branch -D $line; done;
```

### Remote branches

```sh
git branch | grep 'xxx' | while read line ; do git push origin :$line; done;
```

## Deletes all stale tracking branches under \<name\>

  >These stale branches have already been removed from the remote repository referenced by \<name\>, but are still locally available in "remotes/\<name\>".
  >With --dry-run option, report what branches will be pruned, but do no actually prune them.

```sh
git remote prune origin
```

## Pull all repositories in a folder

```sh
for f in *; do echo "=== $f ==="; cd "$f"; git pull && git remote prune origin && git submodule update --init --recursive; cd -; done
```
