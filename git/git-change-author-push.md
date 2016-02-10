# Change Author Of Old Commits And Push It

I often switch to another user or computer and forget to set git user
(specialy with github) only to remember it after pushing, to fix it :

```bash
$ git config user.name "My Name"
$ git config user.email "my_email"
$ git commit --amend --author "My Name <my_email>"
$ git push origin my_branch --force
```
