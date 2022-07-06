# Table of Contents

1.  [Commandline](#orgd66688b)
    1.  [File system navigation](#orgff2b603)
    2.  [File system manipulation](#orgd015f24)
        1.  [touch - Creating Files, and modifying access times](#orgc9b36ca)
        2.  [cp - Copying](#orgbd84782)
        3.  [mv - Moving and Renaming](#org2e0cd95)
        4.  [mkdir - Create Directories](#orgdb84040)
        5.  [rm - Delete files and directories](#org24fc326)
    3.  [Commandline help](#orgd071f4b)
2.  [Version Control](#orgab47708)
    1.  [Why do we need it?](#orgec3e259)
    2.  [Git](#org6bfcd0d)
        1.  [Git configuration](#org21cc338)
        2.  [Creating repositories](#orgf63bd88)
        3.  [Branches](#org062783a)
        4.  [Changes](#org738bc97)
        5.  [GitHub](#orga790685)
        6.  [Reverting commits](#org56067f5)
        7.  [Pull-requests and forks](#org60b1110)

<a id="orgd66688b"></a>

# Commandline

- **Shell** - a program which faciliates the communication to the system
- Terminal:Shell `::` Phone:Language
- Bash - Bourne Again SHell - most common (and) default.
- General structure of a command:
  `command -options arguments`

<a id="orgff2b603"></a>

## File system navigation

- Example file system structure:

```
  .
  ├── images
  │   ├── dec-vt100.jpg
  │   ├── fsf.png
  │   ├── git-flow.png
  │   ├── gnome-terminal.png
  │   ├── gnu.png
  │   ├── linus.jpg
  │   ├── open-source-iniative.png
  │   └── stallman.png
  ├── linux-01.md
  ├── linux-01.org
  ├── linux.md
  ├── linux.org
  ├── linux.txt
  └── virtualbox-and-ubuntu.org
```

- `pwd` - print current working directory
- `ls` - list files and subdirectories
- `cd` - change directory
  - `cd /path/to/target`
- Paths are two types:
  1.  Absolute - referred from the `root` (`/`)
  2.  Relative - referred from the current directory.
- Relative pathname notation:
  1.  `.` - _current_ directory
  2.  `..` - _parent_ directory
- `file` - prints information about file
- `less` - terminal pager for viewing text files

<a id="orgd015f24"></a>

## File system manipulation

<a id="orgc9b36ca"></a>

### touch - Creating Files, and modifying access times

- `touch file` - If file exists, changes access and modification time, if not
  creates empty file &ldquo;file&rdquo;
- `touch -c file` - Previous one, but don&rsquo;t create file if it doesn&rsquo;t exist.
- `touch -a file` - Change only access time
- `touch -m file` - Change only modification time
- `touch -t STAMP file` - Sets the time to STAMP instead of current time (UTC

- `touch -d DATE file` - Sets the time to DATE string, multiple formats possible.

<a id="orgbd84782"></a>

### cp - Copying

- `cp source desination`
- `cp -r source destination` - for recursively copying directories
- `cp -i source destination` - for prompting overwrite confirmations
- `cp -u source destination` - for copying only new files
- `cp source1 source2 destination` - for copying multiple files

<a id="org2e0cd95"></a>

### mv - Moving and Renaming

- `mv source destination` - for both moving and renaming files
- `mv source1 source2 destination` - for moving multiple files

<a id="orgdb84040"></a>

### mkdir - Create Directories

- `mkdir dir1`
- `mkdir dir1 dir2 dir3` - for creating multiple directories

<a id="org24fc326"></a>

### rm - Delete files and directories

- `rm file` - removes file. If it is folder, it throws up error
- `rm -r folder` - removes folder by recursively deleting all contents

<a id="orgd071f4b"></a>

## Commandline help

- Four different (standard) command types:
  1.  Executable
  2.  Shell Built-in
  3.  Shell Function
  4.  Alias
- The types can be checked using `type`
- Executable location can be printed using `which`
- Manual pages can be read using `man`
- Relevant commands can be found with keywords using `apropos`

<a id="org396007f"></a>


<a id="orgab47708"></a>

# Version Control

<a id="orgec3e259"></a>

## Why do we need it?

- Software development gets complicated with increase in size of project.
- Concept of &ldquo;undo&rdquo; exists only within the context of a editor.
- Needs may arise to try two different design choices simultaneously.
- Making a lot of changes at one time, if the code breaks, difficult to debug.

<a id="org6bfcd0d"></a>

## Git

- One such version control system.
- Created by _Linus Torvalds_ for devloping Linux kernel.
- Development process can be explained by graphs:

![img](./images/git-flow.png)

<a id="org21cc338"></a>

### Git configuration

- The first time git is used to commit, it asks for credentials.
- Setting-up config:
  `git config --global user.name "your-name"` - Setting user name
  `git config --global user.email "mail@address.com"` - Setting email address

<a id="orgf63bd88"></a>

### Creating repositories

- You can initialise a local repository in a folder:
  `git init`
- Or you can clone an existing repository from any VCS:
  `git clone url`

<a id="org062783a"></a>

### Branches

- Default branch name in git used to be **master**, but it may have been / can be
  changed to other things like **main**, **trunk** or **development**.
- Check branch with `git status`
- Branches can be created using:
  `git branch branch-name`
- Branches are activated by &ldquo;checking-out&rdquo;:
  `git checkout branch-name`
- Any branch can be merged with the current branch using:
  `git merge branch-name`, where &ldquo;branch-name&rdquo; is the branch to merge with current
  one
- Current branch can be renamed using:
  `git branch -m new-name`
- Specified branch can be deleted using:
  `git branch -d branch-name`

<a id="org738bc97"></a>

### Changes

- Untracked files can be added to track in the version control using
  `git add file`
- All changed files can be added using
  `git add -u`
- All files in a directory can be added using
  `git add .`
- Changes can be committed to the branch using
  `git commit` - this prompts with an editor to specify the commit message
  `git commit -m "message"` - this takes the &ldquo;message&rdquo; as the short commit
  message

<a id="orga790685"></a>

### GitHub

- Provides internet hosting for version control using git.
- Local repository can be linked to a &ldquo;remote&rdquo; repository from GitHub:
  `git remote add remote-name remote-repo-url`, remote-name is usually kept as
  &ldquo;origin&rdquo;
- There can be more than one remote, but the working directory can have files
  only from one remote at a time. Changing remotes changes file to that remote
  files.
- All change histories from the remote branches can be downloaded using:
  `git fetch`
- First time pushing to remote repository will prompt for credentials. Important
  points:
  1.  Depending upon the default configuration of git, your passwords may/may not
      be cached locally. This means future pushing may not/may ask for
      credentials again.
  2.  If you have 2FA set-up in your GitHub account, you cannot push using
      password. You need to obtain PAT from GitHub, and use that as password
      instead. PAT (Personal Access Token) is a usage-specific password sort-of,
      so do not share it with anyone.
- Local branch commits can be pushed to the remote repo using:
  `git push` - this pushes to the default branch of the default remote
  `git push remote-name branch-name` - pushes to the &ldquo;branch-name&rdquo; branch of
  &ldquo;remote-name&rdquo; remote repository.
- New changes/commits in the remote repository can be downloaded and applied
  to your local working tree using:
  `git pull` - this pulls from default branch of default remote
  `git pull remote-name branch-name` - self-explanatory.
- `git pull` is a combination of `git fetch` and `git merge`.

<a id="org56067f5"></a>

### Reverting commits

- Reset commit while leaving the local changes unaffected:
  `git reset commit-name`
- Reset commit while also reverting local changesaa:
  `git reset --hard commit-name`

<a id="org60b1110"></a>

### Pull-requests and forks

- Forking - making a copy of repository in own account.
- Changes made in a forked repository can be requested to be taken into
  the original repository by using **pull requests**
- Changes in the original repository can be synced to the forked repository
  by setting an **upstream**:
  1.  Switch to master branch in your local cloned forked repository.
      `git checkout master`
  2.  Add the remote of the original repository (commonly named as &ldquo;upstream&rdquo;)
      `git remote add upstream url`
  3.  Fetch the changes/history from the original repository
      `git fetch upstream`
  4.  Merge the fetched changes into our local master branch
      `git merge upstream/master`