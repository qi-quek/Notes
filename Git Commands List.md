## Git Commands List
###### 2022-09-06 - 11:43
---
**Always a new `branch` is needed in `remote` to have the `compare and pull` request**

Just do

	push head 

instead of

	head:tracked-remote-branch

---

#### Create local branch from a remote branch (after `pull` or `clone`)

	git checkout -b <local_branch> origin/<remote_branch>

[Click here to so more details](https://stackoverflow.com/questions/24301914/how-to-create-a-local-branch-from-an-existing-remote-branch)

---

#### Change branch name

When you are already on the branch that you intend to change the branch name:

	git branch -m <new_branch_name>

When your on the `main` branch:

	git branch -m <existing_branch_name> <new_branch_name>

---

#### Update remote connection

	git remote update


---

#### Add remote connection

	git remote add <name_you_want_the_connection_to_be_called> <url_of_the_repo>


#### Remove remote connection
Execute this command to remove connection/ bookmark to the remote repository called <name_of_the_connection>

	git remote m <name_of_the_connection>


---

#### Rename remote connection
Execute this command to rename the remote connection from <existing_name> to <new_name>

	git remote rename <existing_name> <new_name>


---

#### Undo specific commit (that has been `push`ed)

First check the status of the branch

	git status

	git log --oneline

	git revert <hash_value_of_the_commit>

	git push

Press `ctrl` + `G` to exit

---

#### Uncommit commits that has not been `push`ed to repo
Check on the status of the working tree

	git status


To check the hash value of the previous commits

	git log --oneline

	![Figure 1](/images/git-2022-0001.png)


Execute either :

	git reset <hash_value_of_intended_commit>

OR

	git reset --hard <hash_value_of_intended_commit>

---

#### Check all your remote connections
To list all connections to other repositories

	git remote


To list all th connections to other repositories, with URL included

	git remote -v

---

#### Difference between (1) git remote update (2) git fetch (3)

	git remote update

- update all the branches to track remote ones
- also updates the command prompt if there are new remote branches
- but it will not merge any changes in it

---

	git fetch

- only update the branch you are on, or branch you set to fetch to
- will not merge any changes in it

---

	git pull

- can update and merge any remote changes of the present branch you are on
- does not display the new remote branches in your terminal or command prompt

---

#### Upload folders into new repo
This is applicable to New Repo or New Remote Name

In the new project folder.  This project folder might be empty or already contain files (that are not tracked by `git`) .

	git init


Execute the following `git` command to show the status:

	git status


To create a main branch in the local `git` repository:

	git branch -M main


To include all the files (in the current project folder) into the `staging area` of the local `git` repository:

	git add .


If you intend to include only a specific file (in the current project folder) into the `staging area` of the local `git`  repository:

	git add <path_to_file_and_filename>


Next to commit the included files (in the current project folder) into the `commited area`  of the local `git` repository:

	git commit -m "message"


To add a remote repository connection into your local `git` repository, to faciliate the `push` committed codes (in local `git` repository) into the remote repository:

	git remote add origin <url_of_the_remote_repository>

*note*
`origin` is just a name you have assigned to the remote repository.  It can be any name you like, e.g. `my-github-repo`.

To push your commited code (in local `git` repository) into the `remote git` repository:

	git push origin main

*note*
- `origin` is the name you have assigned to your remote git repository;
- `main` is the name of the remote branch you wish to `push` your code into;


#### Upload folders/ files into existing repo (without pull request)

	git add .

To commit files (i.e. code) in the `staging` area into the `committed` area in the `local git` repository:

	git commit -m "message here ..."

*note:*
commit message conventions to follow:
- always in present tense
- First character of the message should be Capitalized
- think of your commit as something that will complete this sentence;  "this commit will ...."

For non-tracking scenario, to push the current `local` branch (in local `git` repository) to `remote` branch (in remote `git` repository, e.g. `origin`):

	git push origin <remote-branch-name>


For tacking scenario, where `local` and `remote` repository has different `branch name`:

	git push origin HEAD: <branch-name>


For tracking scenario, where `local` and `remote` repository has the same `branch name`:

	git push origin HEAD: <branch_name>


#### Delete local branch in `git`

Refer to prune for removing local branches not in remote

To delete `local branch` easily:

	git branch -d <local-branch-name>


To force delete `local branch` even if it contains unmarked / un`pushed` commits (to be used with care):

	git branch -D <local-branch-name>


#### Delete remote branch in remote `git` repository

	git push origin --delete <remote-branch-name>


#### Compare local working directory against remote branch (e.g. origin/ main)

Get `local git` repository to fetch the remote branch `main` from the `remote git` repository `origin` :

	git fetch origin main

- `git fetch` will not affect the files in your working directory;
- it does not attempt to merge changes (like what `git pull` does);


To tell `git` to diff the files in the working directory with those files in the `FETCH`ed branch's HEAD, and report the results in a summary format:

	git diff --summary FETCH_HEAD

*note :*
- Summary format gives an overview of the changes
- Usually a good way to start
- use `--stat` if you need more information


#### Track branches

To check which `remote branches` the `local branches` are tracking:

	git branch -vv


#### Check Upstream batch

	git status


#### Git cherry pick
Using `Goland`, you can "automatically" update all the previous commits, or the differences in commits.


#### Remote tracking branches no longer working on remote

To prune `local branches` that are **NOT** on `remote branches` anymore:

	git remote prune origin


To preview branches that will be removed:

	git remote prune origin --dry-run


#### Undo `push`ed commit to remote

The following command can be executed within `Goland`:

	git reset --hard <hash_value_of_commit>


	git push --force


Get the changes without commit:

	git cherry-pick -n <hash_number>


*note :*
- after executing the above command, re-initialize `git commit`;
- execute the usual `git push`;


#### Rename local branch

When you have navigated (in local `git` repository, using `git branch <branch_name>`) to the branch you intend to rename:

	git branch -m <new_branch_name>


If you are not in the branch that you intend to rename, use this command:

	git branch -m <existing_branch_name> <new_branch_name>


#### Change upstream

	git branch <branch_name> --set-upstream-to <remote>/<brance_name>


#### Uncommit last commit AND keep last commit changes

To discard the last commit:

	git reset --soft HEAD^

*note :*
- `HEAD` refers to the current commit - generally the TIP of the current checked-out branch.
- The `^` notation can be attached to any commit specifier and means "the commit before".  
- So `HEAD^` is the commit before the current one
- So `master^` is the commit before the tip of the `master` branch


#### Unset untracked upstream

	git branch --unset-upstream


#### Amend last commit

For files changes, not commit message change

	git add .


	git commit --amend --no-edit


To force `push` this update to the `remote git` repository:

	git push --force


#### Add only modified or deleted files

	git add -u


#### Rename files

git mv <old_filename> <new_filename>


#### Rebase

	git pull --rebase origin master






---

###### References
