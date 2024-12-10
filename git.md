## Helper sheet

### auth
curl -sS https://webi.sh/gh | sh
gh auth login

### Config
```#bash
git config --get user.name
git config --add  --global user.email meshi@gmail.com  
git config --global init.DefaultBranch main
git config --unset <key>
  git config --unset-all <key>
  git config --remove-section <section>  
git config --list  
git config pull.rebase false   #sets to merge on pull
git config --local rerere.enabled false/true   #disables/enables rerere
~/.gitconfig     #location of global gitconfig
```

### Working with Git
```#bash
git init         #create hidden dir .git locally  
  .git/objects   #location of all git objects  
git status  
git add . (or <smth>)  
git commit -m <message_here>  
  git commit --amend  # rename commit message
git log --oneline  
  git log --oneline --graph --all --parents
  git --no-pager log -n 10  
  git log -p    # see changes, diffs
git cat-file -p <hash>  # see content of commits, objects
  # tree of commit is kind of dir
  # blob is kind of file from tree

git reflog

git switch -c <new_branch>
  git switch <branch>
  git switch -c <new_branch> <commit's hash that to branch of>
git branch # see what branch are in
  git branch -m <oldname> <newname>
  git branch -d <branch>

git merge temp_branch (being on branch to merge with)
  git merge HEAD@{1}   #recover last commit
  git commit # after conflict
git rebase main (branch what changes we want to take to ours)
  git rebase --continue # after conflict
  git rebase -t HEAD~n  # squash

git reset --soft HEAD~1
  git reset --hard <commithash> (to commit to be one after running command)

git remote add <name> <uri>
git fetch                     # only get metadata in .git/objects
  git log origin/temp_branch  (origin is common name for remote repo)
git merge origin/temp_branch  # actually merge some branch to new repo
git ls-remote
curl -sS https://webi.sh/gh | sh
gh auth login
git remote add origin https://github.com/your-username/webflyx.git
git push origin main
  git push origin main --force    # don't care about out of sync situation, just do branch like mine
git pull [remote/branch] (if not specified pulls current branch)

git stash
  git stash list -p  # see changes that stash have
  git stash list  
  git stash pop
  git stash apply   # take changes without poping from stack
  git stash drop
  git stash apply stash@{1} # take specific stash

git diff <commitish_hash>
  git diff HEAD~1  # diff current state with previous commit
  git diff commit1 commit2

git cherry-pich commit_hash

git bisect start
  git bisect bad (commit_hash) (HEAD for example)
  git bisect good commit_hash
  git bisect reset
  git bisect run <script>
```
