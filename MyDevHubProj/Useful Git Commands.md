# Useful Git commands

Create branch
```
git branch myFeatureBranch
```

checkout branch
```
git checkout myFeatureBranch
```

add file from working tree to staging area
```
git add ReadMe.me
```

take snapshot
```
git commit -m "Adding readme"
```

send upstream
```
git push -u origin myFeatureBranch
```

create PR
```
create pull request in Github web
```

review | automated tests | approvals
```
Github web: depending on complexity, have anothr person review PR, merge code, run automated build tests, etc.
```

delete branch
```
Github web: once safely merged the PR, it's best practice to delete branch to keep everyone on right branch
```

switch to default branch
```
git checkout main
```

retrieve all changes from repo
```
git pull

this is combo of : 
git fetch
git pmerge
```



