# This is our Git cheat sheet ☆*:.｡.o(≧▽≦)o.｡.:*☆

Git cheat sheet is a collaborative document created by Aline (Lyly) and Gustavo Krajuska as a way to help each other (and why not you too?) on getting better and more proficient using Git - a system that looks scary, but is not (trust us, we were afraid too!).

The main goal with this sheet is to make it as simple and straightforward as possible, so you can quickly run your eyes through it and get the information you're looking for. We are also going to work on a more detailed version of it, to be read when you're just starting with Git and want further explanations, not a refreshment for our weak memories.

Please, have in mind that this is a work-in-progress document and consider collaborating with it if you have a secret handy command you think someone could benefit from.

___

# Git basic commands (∩ᄑ_ᄑ)⊃━☆ﾟ*･｡*･:

Looking for the essentials only? Say no more.

```
git add \<filename>
```
* adds the file named \<filename> into the staging area

```
git commit -m "message"
```
* commits the staged files with the message between the double quotes

```
git push origin \<branchname>
```
* pushes your commits into the branch named \<branchname>
___

# Lyly's favorite Git commands (∩ᄑ_ᄑ)⊃━☆ﾟ*･｡*･:

```
git add .
```
* adds ALL of the changed files into the staging area
```
git commit -am "message"
```
* adds all of the changed files into the staging area, then commits them with the message between the double quotes
```
git log
```
* shows the history of commits (it's important to get the hash of your commits (the first seven chars of your commits hash are enough to identify them (´｡• ᵕ •｡`))
```
git reset --soft HEAD~n 
```
* goes back to the state of **n** commits behind.

* substitute **n** for the number of non-pushed commits you want to go back to
```
git reset --soft \<commithash>
```
* goes back to the state of the commit identified as \<commithash> 

* also: using _'git reset --soft ...'_ goes back to a specific commit and puts the changes commited after that into the code again. If you want to go back to a specific commit and **discard** the changes done, use 'git reset --hard ...'
```
git checkout -b \<branchname>
```
* creates a branch called \<branchname> and then sets it as the current branch
```
git checkout -m \<newbranchname>
```
* resets the name of the current branch to \<newbranchname>
```
git checkout --orphan \<branchname>
```
* creates a new **empty** branch called \<branchname>
```
git branch -D \<branchname>
```
* deletes the branch called \<branchname>
```
git stash 
```
* saves all of the unstaged changes into a stash
```
git stash list
```
* lists all of your stashed changes 
* note that the important thing to get from here is the identification of each stash (usually identified as **"stash@{N}"**
```
git stash apply
```
* applies the latest created stash into the current branch
```
git stash drop \<stashID>
```
* deletes the stash identified as \<stashID> 
```
git stash pop
```
* removes the latest created stash and applies it on the current branch

___

# Gustavo's favorite Git commands (∩ᄑ_ᄑ)⊃━☆ﾟ*･｡*･:

> git ouvir um saxon
> git fazer um sexon

Now seriously:

## Commands for when shit's ready to go

```
git add --all
git commit -m "commit message"
git push --set-upstream origin $(git_current_branch)
```

Usually I set some aliases to deal with this flow

```
alias gaa="git add --all"
alias gcam="git commit -m"
alias gpsup="git push --set-upstream origin $(git_current_branch)"
```

