
Create:
-------
Create new repo (Online)
Navigate to local project
git init
git add .
git commit -m "Initial Commit"
git remote add origin <url>
git remote -v
git push origin master


Update:
-------
git status
git add <file-names>
git commit -m "descriptive message"
git push origin master



Create a new branch to contribute:
-----------------------------------
git checkout -b my-new-branch
git commit -am "some helpful comment"
git push origin my-new-branch



GROUP CHANGES:
---------------
git branch  (Lists all local branches in the current repository)
git branch [branch-name] (Creates a new branch)
git checkout [branch-name] (Switches to the specified branch and updates the working directory)
git merge [branch] (Combines the specified branch’s history into the current branch)
git branch -d [branch-name] (Deletes the specified branch)



SYNCHRONIZE CHANGES    (Register a repository bookmark and exchange version history)
--------------------------------------------------------------------------------------
$ git fetch [bookmark] (Downloads all history from the repository bookmark)
$ git merge [bookmark]/[branch] (Combines bookmark’s branch into current local branch)
$ git push [alias] [branch] (Uploads all local branch commits to GitHub)
$ git pull  (Downloads bookmark history and incorporates changes)



REDO COMMITS     (Erase mistakes and craft replacement history)
---------------------------------------------------------------
$ git reset [commit]   (Undoes all commits after [commit], preserving changes locally)
$ git reset --hard [commit]  (Discards all history and changes back to the specified commit)


REVIEW HISTORY  (Browse and inspect the evolution of project files)
-------------------------------------------------------------------
$ git log                   (Lists version history for the current branch)
$ git log --follow [file]   (Lists version history for a file, including renames)
$ git diff [first-branch]...[second-branch] (Shows content differences between two branches)
$ git show [commit] (Outputs metadata and content changes of the specified commit)

CONFIGURE TOOLING:
------------------
git config --global user.name "[name]"
git config --global user.email "[email address]"
git config --global color.ui auto(Enables helpful colorization of command line output)


Extra:
-------
git status (Lists all new or modified files to be commited)
git diff   (Shows file differences not yet staged)
git reset [file] (Un stages the file, but preserve its contents)
