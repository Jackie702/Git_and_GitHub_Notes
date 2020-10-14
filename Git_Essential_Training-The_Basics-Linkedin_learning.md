<!--
 * @Author: your name
 * @Date: 2020-10-09 09:47:01
 * @LastEditTime: 2020-10-14 10:14:19
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: /Git/Git_Essential_Training-The_Basics-Linkedin_learning.md
-->
#
#   Intro and installation of Git
#
Distributed version control:
    1. Different user maintain their own repositories
    2. No central repository, just many working copies
    3. Changes are stored as change sets
        Track changes, not versions
        Changes sets can be exchanged between repositories
        "Merge in change sets" or "apply patches"

    All repositories are equal for the Git, the master repo is assigned by convential, you can have as many master repos as you want.

Git configuration
    System level:
        Linux: /etc/gitconfig
        Windows: Program Files\Git\etc\gitconfig
        $ git config --system

    User level:
        Linux: ~/.gitconfig
        Windows: $HOME\.gitconfig
        $ git config --global

    Project level:
        my_project/.git/config
        $ git config

    $ git config --global user.name "user's name"     //set user's name
    $ git config user.name                            //get user's name
    $ git config --global user.email "user's email"   //set email
    $ git config --list                               //list all configurations
    $ git config --global core.editor "atom --wait"   //set editor
    $ git config --global color.ui=true               //color text in git

Git auto-completion
    go to the contrib/completion in github.com/git/git, download and set the shell script to let git has the functionality to do auto-completion.

Git help
    $ git help          //general info about git
    $ git help log      //info about git log command


#
#   Getting started
#
Init a repo
    under the project directory:
        $ git init
    Then you will have a .git directory generated. To see what inside:
        $ ls -la .git

Where Git files are stored
    inside .git directory

Your first commit
    - Make changes
    - Add the changes:
        $ git add <fileaname>
    - Commit changes to the repo with a message:
        $ git commit -m <"Message you what to add">

Write a commit message
    - less than 50 characters
    - optionally followed by a blank line and a more complete description
    - Keep each line to less than 72 characters
    - Write commit messages in present tense, not past tense

View the commit log
    $ git log
    Every commit is given an unique ID

    $ git log -n 5  //show 5 most recent commits 
    $ git log --since=2020-01-01    //show commits since 2020-01-01
    $ git log --until=2020-01-01
    $ git log --author="Kevin"      //find commits done by specific author
    $ git log --grep="Init"         //find commits with specific strings

#
#   Git concepts and architecture
#
The three trees
    workspace =git add=> staging index =git commit=> repo

Git workflows

Hash values (SHA-1)
    - Git generates a checksum for each change set
    - Changing data would change checksum
    - Git use SHA-1 hash algorithm to create checksums:
        40-character hexadecimal string(0-9, a-f)

The HEAD pointer
    - Pointer to tip of current branch in repo
    - Last state of repo, what was last checked out
    - Points to parent of next commit where writing commits takes place

#
#   Make changes to files
#
Add files
    $ git status    //check git status
    $ git add <new files>   or  $ git add .
    $ git commit -m "add new files"

Edit files
    After modified the current tracked file, 
    run $ git status
    it will show in red text:
        modified: <modified file>

    Add the modified file to the stage tree again:
        $ git add <modified file>
    Then it will show in greed text:
        modified: <modified file>

    Then commit the changed files

View changes with diff
    show what changes have been made in our working directory:
        $ git diff
    It will only show the changed set, not the whole file

    Show changes in one file:
        $ git diff <filename>
    

View only staged changes
    $ git diff --staged     or
    $ git diff --cached

Delete files
    Track files when deleted
        $ git rm <file to delete>       //it also remove the file from the system permenately
        $ git commit -m "delete first file" 

Move and rename files
    Let's say we have a file <first_file.txt> now, 
    then we change its name to <primary_file.txt>.
    Enter: 
        $ git status 
        we can see two changes--one file deleted and one file untracked.
    Then we do:
        $ git add primary_file.txt
        $ git rm first_file.txt
        $ git status
        The staging tree will recognize these two files are similar and show text in green: "renamed: <file1 -> file2>"
    
    Use git mv command:
        $ git mv second_file.txt secondary_file.txt
        The actual name of the file will be changed, too.
        $ git status
        The renamed file will be recognized.

    Change the position of file is also like renaming:
        $ git mv third_file.txt first_folder/thrid_file.txt

#
#   Use Git with a real project
#
The Explore California website

Initialize Git
    After $ git init, if no commit yet, HEAD pointer points to nothing and $ git log will raise error.

View file edits
    After editing files, run $ git diff, and you will enter the paginator of the diff info.
    f: going forwards
    b: going backwards
    -S: to wrap or not wrap the lines
    q: exit the paginator

    $ git diff --color-words
    This will only highlight changed words.

Stage and commit shortcut
    Commit file and skip the staging index:
        $ git commit -a
        $ git commit --all
    - This stages and commits all changes to tracked files, be careful
    - Does not include untracked file

View a previous commit
    $ git show <ID of commit>
        or
    $ git show <ID of commit> --color-words

Compare commits
    $ git diff <older commit ID>..<newer commit ID>
        or
    $ git diff <older commit ID>..<newer commit ID> --color-words

Multiline commit messages
    $ git log               //will give multiple lines of info
    $ git log --oneline     //give one line of info for each commit
        
Make atomic commits(small commits)
    - Affect only a single aspect
    - Easier to understand, to work with, and to find bugs
    - Improve collaboration
    Commit files by small steps, each commit contains limited message

Client edit
    Open the commit file to write complicated message:
        $ git commit
        Put '*' before each line to make a bullet list.
 

#
#   Undo changes
#
Undo working directory changes
    $ git checkout -- index.html    
    checkout the index.html under current branch(what "--" means). It replaces whatever we had in our directory with it, and it discards the changes that are there.
    In another word, it restores back the version the repository has.

    $ git checkout -- .
    Undo all changes

Unstage files
    $ git reset HEAD <staged filename>

Amend commits(only most recent commit)
    We can only chaneg the lastest commit.
    Any tiny change to commit will lead to the change of the SHA.
    
    After changing some of the file and staging them:
        $ git commit --amaned -m "Sum up several changes"
    Use "--amend" to combine current changes with lastest commit

Retrieve old versions
    Different from ammending and undo above.
    To retrieve old versions of specific file under current branch:
        $ git checkout <ID of previous commit> -- <file to retrieve old versions>

    Check the differences of changes before and after staging:
        $ git diff --staged

Revert a commit
    $ git revert <ID of previous commit>
    After this step, the reversion will be automatically committed

Remove untracked files(remove multiuple files at one time)
    $ git clean -n  //get ready to remove everything untracked from the staging tree(not actually rm them)
    $ git clean -f  //actually remove untracked files


#
#   Ignore files
#
Use .gitignore files
    Git will read this file to ignore some files:   
    - Exact: file1.txt                                    //ignore file1.txt
    - Use exact name or regular expression:   *.txt       //ignore all .txt files
    - Or use negative expression:     !index.php          //do not ignore index.php

Ideas on what to ignore
    - Compiled source code
    - Packages and compressed files
    - Logs and databases
    - OS generated files
    - User-uploaded assets(images, PDFs, videos)

    A collection of useful .gitignore templates: github.com/github/gitignore

Globally ignore files
    Ignore files in all repositories
        $ git config --global core.excludesfile ~/.gitignore_global

Ignore tracked files
    Track a file at beginning and then ignore the changes of the file.
    The git will always commit the first version of this file.
    $ git rm --cached file1.txt

Track empty directories
    Note: Git will igonre directories with no files.
    Check the files in the staging tree:
        $ git ls-tree HEAD
    If you want to track empty directories:
        create a ".gitkeep" file in the dir you want to track
    

