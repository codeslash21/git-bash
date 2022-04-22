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
- 
