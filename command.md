# Important git commands
- `git help [command]` - to get info about the command.
- `git config --global user.[key] "value"` - to add user details in config file. And `key` can be name, email etc.
- `git config --global core.editor "[editor].exe -multiInst -nosession"` - to config default editor.
- `git config --global --list` - list all the configurations which are done at global/user level.
- `git config --global -e` - allow to edit .gitconfig file ith default editor.
- `cat ~/.gitconfig` - print the content of the file which is located in user directory.
- `git config --global merge.tool p4merge` - to set merge tool to resolve conflict while merging.
- `git config --global mergetool.p4merge.path "C:\Program Files\Perforce/p4merge.exe"` - to give path to merge tool.
- `git config --global mergetool.promt false` - to tell git not to promt whether or not to launch p4merge.
- Following commands are for configuration of diff tool -
```
git config --global diff.tool p4merge
git config --global difftool.p4merge.path "C:\Program Files\Perforce/p4merge.exe"
git config --global difftool.promt false
```
- `ls -al` - list all file and floder in the current working directory.
- `mkdir [folder name]` - to create a folder with sepcified name.
- `clear` - to clear the bash window means delete all the previous content. But, previously used comment are still accessable using arrow keys.
- `git init [project name]` - to create a git repository with specified name and that folder contains `.git` folder initially.
- Working directory (or files and folders), staging area and repository(or .git folder) are managed by git locally. Remote repository is also an another repository which also contains all these three stages of its own.
- `git status` - to see status of working directory (like file is modified or added or nothig is done).
- `npp [file name with extension]` - to create a file with given name and open Notepad++ editor(as alias npp stands for Notepad++) to write content of the file.
- `git add README.md` - move edited README file from working directory to staging area.
- `git commit -m "README edited"` - all the files move from staging area to repository area with the given commit message.
- Folder where `.git` folder is present is working directory of git. `.git` is actual git repository which git manages internally. If we delete `.git` folder then we will be no longer on any branch and that folder cant be recognised as git repository. So, if we type `git status` command in working folder we get error message "not a git repository( or any of the parent directories)"
- `cd .git` - to move to .git folder.
- `rm -rf .git` - to remove .git folder forcefully and recursively.
- `git init` - to initialize an empty git repository in the current working folder. But this .git folder has no prior knowledge of the present files and folders and it start fresh. So, when we type `git status` it shows every files in the current directory as untracked files and we have to make commit to create record of those files in git repository.
- `git add .` - to move all the edited files from working directory to git staging area.
- `git commit` - to commit all the changes and and open git core editor which is configured to write commit message.
- `git log` - to see all the commits with commit id, date, author and commit message.
- `git show` - to see all the info wwhich we can get using `git log` command including changes in all the edited files.
- When a new file is commited once then that file is tracked by Git and when the file is modified then git shows that file as modified and not as untracked. But a new file is shown as untracked file as its not be commited even for a single time.
- `git ls-files` - show all the files which git is tracking. It not shows the files which is newly created and not commited.
- `touch [file name with extension]` - to create a file with the given name.
- `git commit -am "[commit message]"` - to commit the changes without moving files to staging area seperately.
- `git restore --staged [file name]` - to move file back from staging area to wworking directory.
- `git checkout -- [file name]` - to undo changes in the file and back to the last commited version.
- 
