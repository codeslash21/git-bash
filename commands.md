# Important Git Commands
# Contents
- [Genral Commands](#general-commands)
- [Git Configuration](#git-configuration)
- [Alias](#alias)
- [Git Initialisation](#git-initialisation)
- [Stages of Git](#stages-of-git)
- [Moves between stages | reset | restore](#moves-between-stages--reset--restore)
- [Copy | Rename | Delete files](#copy--rename--delete-files)
- [Commit Deatails](#commit-details)
- [Create Branch](#create-branch)
- [See Differences](#see-differences)
- [Merging](#merging)
- [Tag](#tag-and-release)
- [Stashing](#stashing)
- [SSH Key](#ssh-key)
- [Connect remote GitHub Repo](#connect-remote-github-repo)
- [Push and Pull](#push-and-pull)
- [Pull Request](#pull-request)
- [Note](#note)

## Genral Commands
- `git help [command]` - to get info about the command.
- `cat ~/.gitconfig` - print the content of the file which is located in user's home directory.
- `cat file_path` - to print the content of the file.
- `ls -al` - list all file and floder in the current working directory.
- `mkdir [folder name]` - to create a folder with sepcified name.
- `clear` - to clear the bash window means delete all the previous content. But, previously used comment are still accessable using arrow keys.
- `pwd` - to print current woring directory.
- `touch file_name.extension` - to create a file with given name.
- `git ls-files` - show all the files which git is tracking. It not shows the files which is newly created and not commited.
- `cd folder_name` - to enter the directory named folder_name.
- `open [img name]` - to open img from cmd line.
## Git Configuration
- `git config --global user.[key] "value"` - to add user details in config file. And `key` can be name, email etc.
- `git config --global core.editor "[editor].exe -multiInst -nosession"` - to config default editor.
- `git config --global init.defaultBranch main` - to set default branch as main.
- `git config --global --list` - list all the configurations which are done at global/user level.
- `git config --global -e` - allow to edit .gitconfig file in the default editor.
- `git config --global alias.[aliased name] "[command to be aliased]"` - to make an alias for a long command.
- Following commands are for configuration of diff tool -
```
git config --global merge.tool p4merge
git config --global mergetool.p4merge.path "C:\Program Files\Perforce\p4merge.exe"
git config --global mergetool.promt false
```
- Following commands are for configuration of diff tool -
```
git config --global diff.tool p4merge
git config --global difftool.p4merge.path "C:\Program Files\Perforce\p4merge.exe"
git config --global difftool.promt false
```
## Alias
- Create or update `.bash_profile` to create alias. This file must be in user home directory. `notepad++ ~/.bash_profile` to open `.bash_profile` with the code editor Notepad++.
- `alias npp='notepad++ -multiInst -nosession'` - to create alias `npp` for `notepad++ -multiInst -nosession`.
- `npp file_name.extension` - to create and open file with notepad++ to edit.

## Git Initialisation
- `git init` - to initialize an empty git repository in the current working folder. But this .git folder has no prior knowledge of the present files and folders and it start fresh. So, when we type `git status` it shows every files in the current directory as untracked files and we have to make commit to create record of those files in git repository.
- `git init [project name]` - to create a working directory in the current directory with specified name and that folder contains `.git` folder(which is git repository) initially.
- `git init -b main [project name]` - do the same as `git init [project name]` but the default branch name will be `main`.

## Stages of Git
- Working directory (or files and folders), staging area and repository(or .git folder) are managed by git locally. Remote repository is also an another repository which also contains all these three stages of its own.
- Folder where `.git` folder is present is working directory of git. `.git` is actual git repository which git manages internally. If we delete `.git` folder then we will be no longer on any branch and that folder cant be recognised as git's working directory. So, if we type `git status` command in working folder we get error message "not a git repository( or any of the parent directories)"
![image](https://github.com/codeslash21/git-bash/assets/32652085/59c0e716-11a9-4a2a-ba08-b151a7f09476)

- When a new file is commited once then that file is tracked by Git and when the file is modified then git shows that file as modified and not as untracked. But a new file is shown as untracked file as its not be commited even for a single time.

## Moves between stages | reset | restore
- `git status` - to see status of working directory (like file is modified or added or nothig is done).
- `git add README.md` - move edited README file from working directory to staging area.
- `git add .` - to move all the edited files from working directory to git staging area.
- `git add -u` - move all the deleted file to staging area, but not other kind of files.
- `git add -A` - move all the deleted and added files to staging area.
- `git commit -m "README edited"` - all the files move from staging area to repository area with the given commit message.
- `git commit` - to commit all the changes and and open git core editor which is configured to write commit message.
- `git commit -am "[commit message]"` - to commit the changes without moving files to staging area seperately. This command is not applicable for untracked file.
- `git restore --staged [file name]` - to move file back from staging area to working directory. We can use `git reset` for the same purpose but it will move all the files from stagging area to working directory.
- `git restore [file name]` - to undo changes in working directory. If a file has two changes and one is staged and another one in working directory, then by this command we can undo the change which is only in working directory.
- `git checkout -- [file name]` - to undo changes in the file and back to the last commited version. This is applicable if file is in working directory not in staging area.
-  `git reset [commit id] --soft` - to move HEAD to that commit id. And, all the changes will be in staging area.
-  `git reset [commit id] --mixed` - to move HEAD to the commit and it is default mode. And, changes will be in working directory means we have to move that in staging area.
-  `git reset [commit id] --hard` - to move HEAD to the commit id and it changes all the file directly to that commit status means we dont have to move file to staging area or dont have to commit.
  
## Copy | Rename | Delete files
- `rm -rf .git` - to remove .git folder forcefully and recursively.
- `rm -r [folder name]` - to delete the folder. `r` flag stands for recursively means delete the folder and also all of its content. If the folder does not has any content they no need to use `r` flag.
- `git rm [file name]` - to delete the file. And, after this command file is in staging area and we can restore the file from there or can delete permanently by commiting that.
- `rm [file name] [file name]` - to delete multiple files together.
- `git mv [file name] [changed name]` - to rename the given file. And, after changing the name the file is in staging area and we have to commit the change.
- `mv [file name] [changed name]` - here we use bash mv command instead of git mv command. And, here status is shown as `file name` is deleted and a new `changed name` file is added and its an untracked file. And, to move all to staging area we can use `git add -A` command.
- `mv [file name] [destination folder name]` - to move the file from current directory to destination directory.
- `cp -R [source file path] [destination folder path]` - to copy the source file to destination folder.
- `cp -R ~/[source folder path from home directory]/* .` - to copy all contents from source folder to current working directory.

## Commit Details
- `git help log` - to know more about various options for `log` command.
- `git log` - to see all the commits with commit id, date, author and commit message. `git log` command show the commits from where the HEAD is pointing but not after that.
-  `git reflog` - show all log including `commit` or `reset` status.
-  `git show` - to see the details of latest commit on the current branch.
- `git show commit_id` - to see all the info which we can get using `git log` command including changes in all the edited files.
- `git log --oneline --graph --decorate --all` - show each commit message in one single line, (graph) with branch hierarchy, (decorate) and which commits belong to which branches, (all) for all the branches in the git repository.
- `git config --global alias.hist "log --oneline --graph --decorate --all"` to create an alias named `hist` for the command `log --oneline --graph --decorate --all`.
- `git hist -- LICENSE.md` - show the git log pertaining only to LICENSE.md file.

## Create Branch
- Branch is timeline of commits. Branch name is label for commits. 
- `git checkout -b [brance name]` - to create a new branch with the given name. And, we move to that branch and also if there is any uncommited change in the parent branch (even if its in staging area) then those changes will be moved on the new branch as uncommited changes.
- `git branch` - to see all the brances in git repository.
- `git branch -a` - to list all the local and remote branches.
- `git checkout [branch name]` - to change git branch. If the branch we want to switch to is not there locally then it will look for that branch in remote repository that origin refer to. If the branch is not present there also then it will show error message.
- `git branch -m main` - to change the current branch name to `main` and switch to that branch.
- `git branch -d [branch name]` - to delete the given branch. After merging if we delete the branch there is no problem as all the commits on that branch is already merged with current working branch.
- `git push origin :branch_name` to delete branch from remote git repository. `origin` is remote reference and `branch_name` is the branch we want to delete.
- If we have a branch that remote repository dont have then when we push the changes from that new branch then that new branch will be created automatically.

## See Differences
- `git diff [commit_id] [commit_id]` - to get difference between two commits. We can use HEAD as latest commit. If we dont give any commit ids then it will give difference between HEAD and latest uncommited changes. 
- `git difftool [commit_id] [commit_id]` - we see the same as `git diff` command but we see in configured difftool which is p4merge in this case.
- `git diff [branch name] [branch name]` - to see difference between two branches.
- In github iterface we can see the differences between two branches using pull request section. We go to `pull request` section and then `create pull request`, from there we choose two branches we want to compare. From where we choose the branch, there we can also put commit id that we want to compare with the latest commit on the other branch or different commit on same branch. we can compare between two tags in the same way. Here we can also compare with a particular state on a branch. Like we can compare with a state before `3 days` (like `main@{3 days}`) or on a particular date `yyyy-mm-dd` (like main@{2015-09-23}`).
- We can see difference between two commits also. If we select a particulat commit then it will show the difference between that commit and the latest commit on that branch. We can comment to a specific line and also we can comment on that particular commit.
## Merging
- Merging is three types -
  - Fast-forward merge: When there is no commit in parent branch and then feature branch commits is simply mergeed with parent branch.
  - Automatic merge: When git detects non-conflicting commit in the parent branch then git do automatic merging and parent timeline is preserveed and new commit is made on parent branch to show merging of branches.
  - Manual: Where automatic merging is not possible and conflicting merge status exists.
 - `git merge [branch name]` - to merge the given branch with the current branch. 
- `git mergetool` - to open configured mergetool to resolve merge conflict. When there is merge conflict means auto merging is not possible then we have to do manual merge. Mergetool has various options to choose to resolve conflict. After resolving conflict we have to commit. After resolving conflict a `[file name with extension].orig` file will be generated which contains original content of the file. Here file `[file name]` is the file which had conflict. We can add the `.orig` file to `.gitignore` and then we can remove that file.

## Tag and release
-  `git tag [tag name]` - to create light weight tag. If we dont specify commit id then tag will be assigned to HEAD.
-  `git tag tag_name branch_name` - to create light weight tag for the last commit on the mentioned branch.
-  `git tag --list` - to list all the tags.
-  `git tag -d [tag name]` - to delete the tag.
- `git push origin tag_name` - to push the specific tag to the remote repository.
-  `git push -u origin main --tags` - to push local branch `main` to remote repository. `-u` stands for tracking branch relationship, so after the first command we dont need `-u` any more, we can simply use `git push` and `git pull`. `--tags` means we want to push all the tags also which are in local git repository in the remote repository. And, `origin` is the remote repository reference. `main` is the branch which we want to push up. If `main` branch is not in the git repo then it also create a branch with that name and push the commit.
- `git push origin :tag_name` - to delete the tag from remote repository.
- `git tag -a [tag name like v1.0] -m "[note like release note]"` - to create annotated tag with given note. If we dont specify commit id then tag will be assigned to HEAD.
-  `git show [annotated tag name]` - to show tag message along with commit detail to which tag is associated with.
-  `git tag -f tag_name commit_id` - to make a already existed tag floating, the tag will refer to the newly assigned commit id. And to update remote repo with that if we do `git push origin tag_name` then it will show message `tag already exist` and will not update that with latest commit id. So, to update there are two ways - one we delete the tag from remote repo and then push the tag again, second we psu the tag forcefully using `git psuh --force origin tag_name`.
- When we have tags on remote repository then we have different versions of code associated with those tags, and we can and download see those different versions.
- When we create tag usinng github interface then that tag will be light-weight tag not the annotated tag.
- On github under `tag` and `release` sections we have same tags. But when we release a tag with release notes that we can see in `release` section with release note. In release note we can add the `pull request` and `issues` those are related to that release. And also we can add specific description about the release. We can edit the release note after that has been released. We can also choose that our release is production ready or not.
- If we delete a release that will not delete the associated tag and commit. That only delete the release.
- We can create a new release from `release` tab with a new or already created tag. If we want to create with a new tag then we can choose the commit id that we want to release.
## Stashing
-  `git stash` - to save the last changes and it will not be shown in `git status` command as uncommited change though the change is neither commited nor stagged. And file will be same as before making the changes. After using `git stash` command if we make changes to other(or same) file and commit those changes then the saved changes will not be reflected on that commit. This command is helpful if we want to commit a new change before a already done change.
-  `git stash list` - to show all the stash.
-  `git stash pop` - to bring the changes back and the files will be same as before `git stash` command. If there are multiple stash then this command works like `stack pop` command means pop the last stash first and others changes will not be brought back. We have to give the command as many times as the number of stash listed to bring all the changes back. Here merge conflict is possible.

## SSH Key
-  To generate ssh key follow the following steps - 
    - `cd ~` - to move to home directory.
    - `mkdir .ssh` give this command in home directory of the PC or User.
    - `cd .ssh` - to move to that folder.
    - `ssh-keygen -t rsa -C "[mail id]"` - to generate public/private key pair. ANd, there will be a promt to enter the file to which we want to save the key and just hit `enter` to choose the default.
    - Then there will be promt to give passphrase and again to re-enter it.
    - After the above steps in `.ssh` foler there will be two file - `id_rsa` and `id_rsa.pub` which holds keys for private and public rsa key pair respectively.
    - `npp id_rsa.pub` - to open this file with default code editor(Notepad++) and copy all the contents and put that in SSH key part in `GitHub settings`.
    - `ssh -T git@github.com` - to check we can connect github with ssh key. If yes then it shows successfully authenticated.

## Connect remote Github Repo
-  `git remote add origin [remote git repository url]` - To set remote repository with referenced name origin. We can use different name inplace of origin.
-  `git remote -v` - to see the connected remote repository.
- `git clone [git repo url(https/ssh)]` - to create a local copy of the git repository with git repo name by default. And, the remote repo is referenced by `origin` by default.
- `git clone [git repo url(https/ssh)] [new name]` - to create a local copy of the git repository with the given name.
- `git remote set-url origin [new url]` - to change the reference origin pointing to.
- `git remote show origin` - to details about the remote reference origin.

## Push and Pull
-  `git push -u [remote reference] [branch name]` - to push the changes in the branch. If branch is not in the remote git repository then it will ceate that branch and push the changes.
-  `git push -u origin main --tags` - to push local branch `main` to remote repository. `-u` stands for tracking branch relationship, so after the first command we dont need `-u` any more, we can simply use `git push` and `git pull`. `--tags` means we want to push all the tags also which are in local git repository in the remote repository. And, `origin` is the remote repository reference. `main` is the branch which we want to push up. If `main` branch is not in the git repo then it also create a branch with that name and push the commit.
- `git push` - it only push the changes on the current working branch to remote repo matching branch. But it will not push any tags.
- `git fetch` - to fetch all the changes made on remote repository to local repo. It will not merge the chnages. It will show the difference between commits in local and remote branches.
- `git pull` - to fetch and merge the changes made on remote repo and it also cause merge conflict depending upon the changes. Its basically combiination of fetch and merge command. It update only the active branch in local repo. If there is any extra branch in the remote repository then it will not be created automaticalyy by using `git pull`. We have to create manually or we can use `git checkout`.
- `git pull --all` - to update all the tracking branch.
- `git branch --set-upstream-to=<remote reference>/<branch> <local branch>` - to set tracking information for the local branch with desired remote branch. To use `git pull` command its needed if not done already, but if we used before `git clone` or `git push` command then its not needed as tracking is already set for the active branch. Otherwise we have to use `git pull <remote reference> <remote branch>`.
- `git fetch -p` - to remove the local stale reference of dead branch on github. After merging we still have reference to that remote branch and even after deleting that remote branch.
- `git push origin :branch_name` to delete branch from remote git repository. `origin` is remote reference and `branch_name` is the branch we want to delete.
- If there is 1 and 1 different commit on each local and remote repository and they will not create merge conflict then if we use `git pull` then both commits will be merged and create a new merge commit. but if we want whatever we are currently working on will stay ahead of github commit then we will use `git pull --rebase`. In this case another new commit will not created, rather there will be github commits first and then local commits.

## Pull Request
- We can create a new branch in github and after making a commit on the new branch we can do `pull request` to merge that branch with the default branch. And after  creating pull request there will be an open pull request we can see that in pull request tab of that repository. We can see changed files in that pull request and we can add inline comment after a particular linne in the code. If we do `close pull request` then that will close the pull request without merging the changes. To merge the commit with the default or base branch we have to do `merge pull request`. After merging we can delete that branch also.
- If we fork a repository then when we make a commit to our copy of forked repo, then there will be a option for `pull request`. If we click on `pul request` then we can see the difference between default branch of forked repo and our current branch. And, finally if we create pull request then that request will be sent to forked repo.

## NOTE:
- If we use bash command instead of git command then file will be in working directory not in staging area. Like `rm [file name]` to delete a file. And to permanently delete the file we have to add that in staging area and then commit.
- In `.gitignore` file we can write the name or the expression of files which we want to ignore. And all those file will not be in git repository but in file system. Even if the ignored file is modified it will not be shown by `git status` command, means we dont have to move that file to staging area and make commit.
- HEAD is not just pointing to last commit but pointing to the last commit of the current branch.
