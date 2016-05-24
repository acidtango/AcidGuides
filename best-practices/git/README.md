Git
===

Things to consider
------------------

* Don't push local files to the repository.
* Delete local and remote feature branches after merging.
* Perform work in a feature branch.
* Rebase frequently to incorporate upstream changes.
* Use a pull request for code reviews.

How to write a new feature
--------------------------

* Create a local feature branch based off development branch.
  - `git checkout development`
  - `git pull`
  - `git checkout -b <branch-name>`
* Prefix the branch name with your initials.
* Rebase frequently to incorporate upstream changes.
  - `git fetch origin`
  - `git rebase origin/master`
* Resolve conflicts. When feature is complete and tests pass, stage the changes.
  - `git add --all`
* When you've staged the changes, commit them.
  - `git status`
  - `git commit --verbose`
* If you've created more than one commit, use a rebase to squash them into
  cohesive commits with good messages:
  - `git rebase -i origin/master`
* Share your branch.
  - `git push origin <branch-name>`
* Submit a GitHub pull request.

Review Code
-----------

* A team member other than the author reviews the pull request. They follow Code
  Review guidelines to avoid miscommunication.
* They make comments and ask questions directly on lines of code in the GitHub
  web interface or in the project's chat room.
* For changes which they can make themselves, they check out the branch.
  - `git checkout <branch-name>`
  - `./bin/setup`
  - `git diff staging/master..HEAD`
* They make small changes right in the branch, test the feature on their
  machine, run tests, commit, and push.
* When satisfied, they comment on the pull request Ready to merge.

Merge
-----

* Rebase interactively. Squash commits like `'`Fix whitespace`'` into one or a
  small number of valuable commit(s). Edit commit messages to reveal intent.
  Run tests.
  - `git fetch origin`
  - `git rebase -i origin/master`
* Force push your branch. This allows GitHub to automatically close your pull
  request and mark it as merged when your commit(s) are pushed to master. It
  also makes it possible to find the pull request that brought in your changes.
  - `git push --force origin <branch-name>`
* View a list of new commits. View changed files. Merge branch into master.
  - `git log origin/master..<branch-name>`
  - `git diff --stat origin/master`
  - `git checkout master`
  - `git merge <branch-name> --ff-only`
  - `git push`
* Delete your remote feature branch.
  - `git push origin --delete <branch-name>`
* Delete your local feature branch.
  - `git branch --delete <branch-name>`
