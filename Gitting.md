## GIT

is a version control system. GitHub offers a lot of additional functionality on top of what basic git does. 

#### Recommended config (need to be done one time)
```git config --global push.default simple```


#### When working directly on master, what is the workflow?
```
git status
git add <files/directories>
git commit -m "<message>"
git pull
git push 
```

#### When working with multiple branches?

```
# From the branch of interest, create a new branch first time you need it with
git checkout -b <branch name>
git push -u origin <branch name>

# Once you are on the branch
git add <files/directories>
git commit -m "<message>"
git pull
git push
```

#### How do you switch branches?

```
git checkout <branch name>
```

#### How to merge branch?

```
# Make sure the branches are updated.
# Switch to the branch into which you want to merge changes.
git checkout master
git pull
git merge my_branch
git push
```

#### What is origin and master?
When you run `git pull origin master`, you are explicitly defining to use origin (which is github) and master (which is the branch you want).

