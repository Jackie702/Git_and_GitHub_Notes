<!--
 * @Author: ciyuan yu
 * @Date: 2020-10-21 09:33:48
 * @LastEditTime: 2020-10-26 15:27:10
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: /undefined/Users/yuciyuan/Desktop/Self_study/Git/Git_Branches_Merges_and_Remotes-Linkedin_Learning/Git_Branches_Merges_and_Remotes-Linkedin_Learning.md
-->
#
#   Navigate the commit tree
#
Reference commits
    $ git show HEAD
    or
    $ git show <SHA-1>

Ancestry
    Each commit have its parent commit, get the parent commit:
        $ git show <SHA-1>^ / HEAD^ / HEAD~1 / master^


    Get the grandparent commit:
        $ git show <SHA-1>^^ / HEAD^^ / HEAD~2 / master^^

Tree Listings
    $ git ls-tree <tree-ish>
    
    $ git ls-tree HEAD
        we will get a list of:
            tree --> directory
            blob --> large binary file

    To check a specific tree in the list:
        $ git ls-tree <dir>
    To check the content of the object:
        $ git ls-tree <dir>/ 

Filter the commit log
    check $ git help log

    Filter the log by numbers:
        $ git log -3 

    By time:
        $ git log --since=2019-01-01    //logs after this day
        $ git log --until=2019-04-13    //logs before this day
        $ git log --until="3 days ago"
        $ git log --after=2.weeks --before=3.days

    By author:
        $ git log --author="Kevin"

    By commit message:
        $ git log --grep="Initial"  //get the commit with key word "Initial"

    By range:
        $ git log <SHA-1>..<HEAD>

    By particular file:
        $ git log file.html

Format the commit log
    Show patches(changes) of commits:
        $ git log -p

    Show number of changes of commits:
        $ git log --stat

    By different formats:
        $ git log --format=<oneline / medium(default) / short / full / fuller / email / raw>

    Show the graph:
        $ git log --graph [--all] [--oneline] [--decorate]

#
#   Branching
#
Branching overview:
    1. Try new ideas
    2. Isolate features or section of work

Create branches
    create new branch but not switch to it:
        $ git branch <new_branch>
    check branch files:
        $ ls -la .git/refs/heads/
    
    If a new branch is created from an existed branch, and no commits are submitted, they have the same SHA-1.

Switch branches
    $ git checkout <branch_name>

Create and switch branch
    $ git checkout -b <new_branch>

Switch branches with uncommitted changes
    Situations:
        1. Cannot switch if changes in working directory conflict
        2. Can switch if changes in working directory could be applied without conflict
        3. Can switch if files are not being tracked

    Solutions:
        1. Commit the changes to the current branch
        2. Remove the changes, checkout the files again
        3. Stash the changes

Compare branches
    $ git diff <branch_1>..<branch_2>

    Shorten the compare lines:
    $ git diff --color-words <branch_1>..<branch_2>

    Check the difference back to their parents / grandparents:
    $ git diff <branch_1>..<branch_2>^
    $ git diff <branch_1>..<branch_2>^^

    To see what branches have merged into the current branch:
    $ git branch --merged

    To see what branches have not merged into the current branch:
    $ git branch --no-merged

Rename branches
    $ git branch -m <new_name>

Delete branches
    $ git branch -d <branch_name>

    delete the branch that has commits that not merged into other branch, you will lose the commit forever:
    $ git branch -D <branch_name>

Configure command prompt
    

#
#   Reset Branches
#
Reset types
    - Reset changes the files in the staging index and/or working directory to the state they had when a specified commit was made
    - "Make my project look like it did back then"
    - Moves HEAD pointer to a specific commit
    - Types: soft, mixed, hard

    Soft reset:
        $ git reset --soft <tree-ish>
        · Move HEAD pointer
        · Does not change staging index
        · Does not change working directory

    Mixed reset(Default choice):
        $ git reset --mixed <tree-ish>
        · Move HEAD pointer
        · Changes staging index to match repository
        · Does not changes working repository 

    Hard reset:
        $ git reset --hard <tree-ish>
        · Move HEAD pointer
        · Changes staging index to match repository
        · Changes working directory to match repository


#
#   Merge Branches
#


#
#   Stash Changes
#


#
#   Set Up a Remote
#


#
#   Collaboration with a Remote
#