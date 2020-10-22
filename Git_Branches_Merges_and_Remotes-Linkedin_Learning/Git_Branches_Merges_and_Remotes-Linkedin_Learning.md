<!--
 * @Author: ciyuan yu
 * @Date: 2020-10-21 09:33:48
 * @LastEditTime: 2020-10-21 10:31:37
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


#
#   Reset Branches
#


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