# Git: Editing your commits

The more I work with git, more I realize how powerful it is. I discovered that there is a way to organize/edit your commits. For what? Some useful cases:

- the commit message is wrong or it doesn’t make sense.
- the order of the commits is not nice regarding to GitHub history.
- there are more than one commit which make similar changes (or even the same thing).
- a commit grouped a lot of different code and it makes sense divide it in smaller commits.

## A quick example

A simple example: let’s imagine that in your project you did a change and made a commit:

```
git commit -m 'CSS and JS adjusments in slideshow.'
```
So, you just remembered that you needed to update the README.

```
git commit -m 'Updates README.'
```
So, you went to get a cup of coffee and when you were returning to your desk, you remembered a last CSS adjustment that you have to do. So you do it, and make a new commit:

```
git commit -m 'More CSS adjustments in slideshow.'
```
A simple log to see the commits would show something like that (the last 3):

```
git log --oneline
74e6f3e More CSS adjustments in slideshow.
1ee9572 Updates README.
9afe987 CSS and JS adjusments in slideshow.
```
If it’s a small or even personal project, we could say that is okay to let the commits this way. However, if you are working with other people in a big project, it could be weird three commits for the same and small change. For help us, there is the interactive rebase: using it we could change the commits in a branch.

## How I do it?
```
git rebase -i HEAD~3
```
About the code above:

- -i => interactive mode
- -3 =>number of commits we want to target.

Running that comand, a screen like this below will show (it will open in your default editor like Atom):

```
pick 74e6f3e More CSS adjustments in slideshow.
pick 1ee9572 Updates README.
pick 9afe987 CSS and JS adjusments in slideshow.


# Rebase 5644bdd..74e6f3e onto 5644bdd
#
# Commands:
#  p, pick = use commit
#  r, reword = use commit, but edit the commit message
#  e, edit = use commit, but stop for amending
#  s, squash = use commit, but meld into previous commit
#  f, fixup = like "squash", but discard this commit's log message
#  x, exec = run command (the rest of the line) using shell
```

## Reordering commits
In example above we could change the commits’ order.
```
pick 1ee9572 Updates README.
pick 74e6f3e More CSS adjustments in slideshow.
pick 9afe987 CSS and JS adjusments in slideshow.
And.. it’s done! If everything is ok, a message like that will appear:
```

Successfully rebased and updated refs/heads/develop.
Some conflicts could happen, and in this case the rebase command will stop untill you resolve the conflicts. After that you only need to run git rebase --continue to continue or git rebase --abort to quite and abort the process.

## Editing messages
Other thing really cool is the possibility to edit the message of the commit. In the previous examples, now we want to change message of the commit which updates the README file.

So, we run again the rebase.

```
git rebase -i HEAD~3
And the same screen with the commits list will show for us. Now we change the pick word to reword in the commit which we want to change the message.

pick 1ee9572 Updates README.
pick 74e6f3e More CSS adjustments in slideshow.
pick 9afe987 CSS and JS adjusments in slideshow.
Doing that, a new screen will show for us:

Updates the README.

# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
#
# Date:      Mon Dec 15 19:09:30 2014 -0200
#
# rebase in progress; onto 5644bdd
# You are currently editing a commit while rebasing branch 'develop' on '5644bdd'.
#
# Changes to be committed:
#       modified:   README.md
#
```
We just need to type the new message.

Updates README with JS dependencies.
...
And it’s done! If we run a simple log, we will see the commits list with the message updated:

```
1ee9572 Updates README with JS dependencies.
74e6f3e More CSS adjustments in slideshow.
9afe987 CSS and JS adjusments in slideshow.
```
Forcing the push
As reminded by Cicero Pablo, when we use the interactive rebase, if you already have a repository with a history of commits, you will have to use the push command with the --force flag.

There is more…
You can read the second part of this article that we talk about merge and split commits.

Some points:

- The names/structure of the files and message of commits are only for example.
- I used the word screen to make reference to every return of terminal after a command.
