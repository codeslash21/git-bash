# Important Git Commands
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
## Git configuration
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

## Initialisation
- `git init` - to initialize an empty git repository in the current working folder. But this .git folder has no prior knowledge of the present files and folders and it start fresh. So, when we type `git status` it shows every files in the current directory as untracked files and we have to make commit to create record of those files in git repository.
- `git init [project name]` - to create a working directory in the current directory with specified name and that folder contains `.git` folder(which is git repository) initially.
- `git init -b main [project name]` - do the same as `git init [project name]` but the default branch name will be `main`.

## Stages of Git
- Working directory (or files and folders), staging area and repository(or .git folder) are managed by git locally. Remote repository is also an another repository which also contains all these three stages of its own.
- Folder where `.git` folder is present is working directory of git. `.git` is actual git repository which git manages internally. If we delete `.git` folder then we will be no longer on any branch and that folder cant be recognised as git's working directory. So, if we type `git status` command in working folder we get error message "not a git repository( or any of the parent directories)"
![image](https://github.com/codeslash21/git-bash/assets/32652085/59c0e716-11a9-4a2a-ba08-b151a7f09476)

- When a new file is commited once then that file is tracked by Git and when the file is modified then git shows that file as modified and not as untracked. But a new file is shown as untracked file as its not be commited even for a single time.

## Moves between stages
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
## Copy, Rename and Delete
- `rm -rf .git` - to remove .git folder forcefully and recursively.
- `rm -r [folder name]` - to delete the folder. `r` flag stands for recursively means delete the folder and also all of its content. If the folder does not has any content they no need to use `r` flag.
- `git rm [file name]` - to delete the file. And, after this command file is in staging area and we can restore the file from there or can delete permanently by commiting that.
- `rm [file name] [file name]` - to delete multiple files together.
- `git mv [file name] [changed name]` - to rename the given file. And, after changing the name the file is in staging area and we have to commit the change.
- `mv [file name] [changed name]` - here we use bash mv command instead of git mv command. And, here status is shown as `file name` is deleted and a new `changed name` file is added and its an untracked file. And, to move all to staging area we can use `git add -A` command.
- `mv [file name] [destination folder name]` - to move the file from current directory to destination directory.

## Commit details
- `git help log` - to know more about various options for `log` command.
- `git log` - to see all the commits with commit id, date, author and commit message.
- `git show commit_id` - to see all the info which we can get using `git log` command including changes in all the edited files.
- `git log --oneline --graph --decorate --all` - show each commit message in one single line, (graph) with branch hierarchy, (decorate) and which commits belong to which branches, (all) for all the branches in the git repository.
- `git config --global alias.hist "log --oneline --graph --decorate --all"` to create an alias named `hist` for the command `log --oneline --graph --decorate --all`.
- `git hist -- LICENSE.md` - show the git log pertaining only to LICENSE.md file.













## NOTE:
- If we use bash command instead of git command then file will be in working directory not in staging area. Like `rm [file name]` to delete a file. And to permanently delete the file we have to add that in staging area and then commit.
- In `.gitignore` file we can write the name or the expression of files which we want to ignore. And all those file will not be in git repository but in file system. Even if the ignored file is modified it will not be shown by `git status` command, means we dont have to move that file to staging area and make commit.
