Git-SVN | Description
---|---
git-svn clone -s http://example.com/my_subversion_repo local_dir|Checking out a Subversion repository -s means standard layout (trunk,tags,branches)
git-svn show-ignore > .gitignore                                |Files you were ignoring via svn:ignore are not ignored in this git repository. To ignore them again, run in the root of your repository
git-svn rebase                                                  |Update local repository
git-svn dcommit                                                 |Commit on remote repository 

Essential commands | Description
---|---
git config                                           |set your user name and email in the main configuration file.
git config --global user.name                        |check your name
git config --global user.name = "Dhruv Nenwani"      |set your name
git config --global user.email	                     |email
git config --global user.email = "nendhruv@gmail.com"|
git init	                                         |initialise a git repository for a new or existing project in the current directory
git clone <:clone git url:>	                         |copy a git repository from remote source, also sets the remote to original source so that you can pull again.
git status                                           |check the status of files you’ve changed in your working directory, i.e, what all has changed since your last commit.
git add .                                            |adds changes to stage/index in your working directory.
git add filename                                     |
git commit                                           |commits your changes and sets it to new commit object for your remote.
git commit -m"weet little commit message"            |
git commit --amend                                   |
git push                                             |if you have added and committed your changes and you want to push them
git pull <:remote:> <:branch:>                       |
git pull                                             |if your remote has updated and you want those latest changes
git push <:remote:> <:branch:>                       |
git branch                                           |Lists out all the branches
git branch -a                                        |list all the remote branches as well
git branch <:new_branch_name:> [source_branch]       |If you want to fork from the current branch, you don’t have to say so.
git branch new_branch_name master                    |You’ll probably want to create a branch every time you work on a new feature “master” is the branch you are forking off a new branch from.
git checkout <:branch:>                              |Switch to different branches
git checkout -b <:branch:>                           |if you want to create and switch to a new branch.
git checkout filename                                |Revert unstaged changes
git checkout -b new_branch_name [old_branch_name]    |To make things easier, all of these steps can be combined
git stash                                            |Save changes that you don’t want to commit immediately.
git stash pop                                        |bring your saved changes back https://stackoverflow.com/questions/15286075/difference-between-git-stash-pop-and-git-stash-apply
git merge <:branch_you_want_to_merge:>               |Merge two branches you were working on.(first, Switch to branch you want to merge everything in)
git reset                                            |You know when you commit changes that are not complete, this sets your index to the latest commit that you want to work on with.
git reset <:mode:> <:COMMIT:>                        |
git reset HEAD filename                              |Revert staged changes
git remote                                           |check what remote/source you have or add a new remote
git remote add <:remote_url:>                        |
git rm filename                                      |To stop tracking -r make it recursive, but pay attention!
git cherry                                           |

Other commands | Description
---|---
git grep "foo()"                                              |Search the working directory for foo():
git rebase                                                    |
git blame -L337,+5 -- src/myproject/services.py               |history of changes at specific line
git log --pretty=short -u -L 337,337:src/myproject/services.py|evolution at line 337
git log -S puppy                                              |Search the commit history for the word puppy and display matching commits

## Reference: 
- https://www.viget.com/articles/effectively-using-git-with-subversion/
- https://stackoverflow.com/questions/3491270/git-merge-apply-changes-to-code-that-moved-to-a-different-file