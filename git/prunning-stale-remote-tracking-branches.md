
## Pruning Stale Remote Tracking Branches

- to see the branches that are present localy but don't exist anymore on remote 
```shell
    git remote prune origin --dry-run
```
and to remove them :
```shell
git remote prune origin
```



