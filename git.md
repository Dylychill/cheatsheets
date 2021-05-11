# Git
### Creating a git repository
`git init`: inside the directory to create a respository

`git remote add origin git@github.com:DirectoryChain`: adds initial local repository to online repository - copy paste from github after making a new repository there

`git clone [link to repositoryy]`: getting an online repository onto local device
- Fork is like clone, except it pushes onto online git repos from someoe elses.

### Save your code
`git add .`: adds indicate files to the staging area: dot is all files in directory

`git commit -m "my message"`: commits staged changes with a message

`git push origin master`: pushes committed changes up to selected branch

`git status`: lists what commits and changes have been made

`git diff`: lists all the differences

### Notes

The `.gitignore` files speciffies what files you don't want saved on github. The `node_modules` folder should always be ignored.

# Git Branches
`git branch` in command shows what branch you are currently on. Default is master, all projects start with a Master branch


### Create a Branch

`git checkout -b BRANCH_NAME`
- this will switch to the branch specified. `-b` creates a new branch
- then when pushing to github, can specify the branch you are pushing to.
- `git add .` + `git commit -m "for new-feature"` + `git push origin [BRANCH_NAME]`

### Merging

If branch has been changed, need to pull before you can push your changes.

- You are in your own branch
- `git pull origin master` - pulls any updated since last pull
- `git merge master` - when in your side-branch will put master changes into local branch to resolve any conflicts. If there are conflicts, need to add and commit again.
- `git push origin BRANCH_NAME`