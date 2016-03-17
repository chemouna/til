
## Create changelog from git log

A simple command to generate a clean changelog for a project (provided that the
  commits are clean) :

  ```bash
     git log --pretty=format:"- %s%n%b" --since="$(git show -s --format=%ad `git rev-list --tags --max-count=1`)"
  ```
