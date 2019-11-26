# This is our Git cheat sheet ☆*:.｡.o(≧▽≦)o.｡.:*☆

Git cheat sheet is a collaborative document created by Aline (Lyly) and Gustavo Krajuska as a way to help each other (and why not you too?) on getting better and more proficient using Git - a system that looks scary, but is not (trust us, we were afraid too!).

The main goal with this sheet is to make it as simple and straightforward as possible, so you can quickly run your eyes through it and get the information you're looking for. We are also going to work on a more detailed version of it, to be read when you're just starting with Git and want further explanations, not a refreshment for our weak memories.

Please, have in mind that this is a work-in-progress document and consider collaborating with it if you have a secret handy command you think someone could benefit from.

___

# Git basic commands (∩ᄑ_ᄑ)⊃━☆ﾟ*･｡*･:

Looking for the essentials only? Say no more.

```
git add <filename>
```
* adds the file named \<filename> into the staging area

```
git commit -m "message"
```
* commits the staged files with the message between the double quotes
> I (gkrajuska) personally don't like the "-m" flag because it doesn't open Vim (the most feared text editor on Earth) with the **diff** (differences) between staged files. I only use this commit method if I'm 350% sure of the changes included in the commit.

```
git push origin <branchname>
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
git reset --soft <commithash>
```
* goes back to the state of the commit identified as \<commithash>

* also: using _'git reset --soft ...'_ goes back to a specific commit and puts the changes commited after that into the code again. If you want to go back to a specific commit and **discard** the changes done, use 'git reset --hard ...'
```
git checkout -b <branchname>
```
* creates a branch called \<branchname> and then sets it as the current branch

```
git checkout -m <newbranchname>
```
* resets the name of the current branch to \<newbranchname>

```
git checkout --orphan <branchname>
```
* creates a new **empty** branch called \<branchname>
> gkrajuska's notes:
>> by **empty**, krajuska meant that the branch will be created with no history attached to the root of the branch you were checked out before running the --orphan flagged command

```
git branch -D <branchname>
```
* deletes the branch called \<branchname>
> gkrajuska's notes:
>> the **-D** flag forces deletion if the branch was not merged to another branch. If you want to be notified in case your branch's changes weren't merged, use the lowercase **-d** flag

```
git stash [push]
```
* saves all of the unstaged changes into a stash.
* executing **stash** without any further arguments is the same as executing **stash push**

```
git stash list
```
* lists all of your stashed changes
* note that the important thing to get from here is the identification of each stash (usually identified as **"stash@{N}"**

```
git stash apply
```
* applies the latest created stash into the current branch without removing the entry from the stashlist (great to check if your stashed changes fit the current branch)

```
git stash drop <stashID>
```
* deletes the stash identified as \<stashID>

```
git stash pop
```
* removes the latest created stash and applies it on the current branch

___

# Gustavo's favorite Git commands (∩ᄑ_ᄑ)⊃━☆ﾟ*･｡*･:

## Commands for when shit's ready to go

```
git add --all
```
* add every change to the staged area

```
git commit -m "commit message"
```
* commit to the staged area's changes

```
git push --set-upstream origin $(git_current_branch)
```
* push to the remote branch even if it doesn't exists yet

  * Usually I set some aliases to deal with this flow

  ```
  alias gaa="git add --all"
  alias gcam="git commit -m"
  alias gpsup="git push --set-upstream origin $(git_current_branch)"
  ```

## Complex commands that are really helpful and not as much explored by tutorials

```
git ls-files
```
* now this is an interesting one, it lists all the files in the repository's index (index is the "place" where all references to tracked files are)

* you can do a lot of cool stuff with this command, like using pipes to open all the modified files in a working tree

```
git ls-files -m | xargs code
```
* the command above uses the **-m** flag to list only modified files and passes the list to **xargs** which will pass every line separately to the command you provide after xargs (in this case, **code**)
  * setting up an alias to this command is really nice, so you can go like "cm" and open every modified file in your favorite text editor
  ```
  alias cm='git ls-files -m | xargs code'
  ```

**prepare for the LIT MACHINE**
```
git add $(fzf)
```
* opens up fuzzy find (you may need to install it) and the file you type is going to be staged, REALLY useful when you want to stage a single file on your tree and thinks that typing the relative path is a fucking chore

```
git add $(git ls-files -m|fzf)
```
* opens up fuzzy find ONLY with modified files, it's a dream coming true, my dudes
  * you can also use this **fzf** approach to **git restore** commands, so you can restore selected files easily

---

