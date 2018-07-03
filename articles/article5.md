[< Back](../README.md)

# Git: Update your fork

Contribute in open source projects is one of the coolest things in development area. It’s common to be ashamed to contribute with some project, and one of the reasons for it is because you don’t think you have something to contribute. And that’s the point: you can start with anything: a simple revision of code or even a translation.

## The proccess
As you get used to contribute, the proccess becomes automatic. But for a person who is going to contribute for the first time, some parts could be confusing.

A simple step by step could be something like that:

1. Fork of the project to your Github user.
2. Clone of the project forked in your machine.
3. Your magic contribution.
4. Updating of your project version with the original project.
5. Send your commits to your GitHub.
6. Open a pull request to the original project.

Believe it: doing is easier than writing. The step four was the most confuse for me. And that’s why I decided to show here.

## The upstream
Let’s suppose that we foked a project to our GitHub user account. So, at this moment, the original project and your fork are at the same point and equal.

So, we start to make a lot of changes in our version of the project and we commit them. Simultaneously, you realize that the original project merged a pull request. Now, the projects aren’t equal: actually they have a lot of diferences.

Your local project has all your changes.
The original project has new changes from the pull request merged.
If you send your changes to GitHub and try to open a pull request, you are going to realize that it wouldn’t be possible. For do that, we have update our local project with the original; and that’s when the upstream will help us.

Let’s say you are contributing with a project of mine. We add a remote based on the original version of the blog:
```
$ git remote add upstream https://github.com/yoeripasmans/weekly-nerd
```
After that, we have to update the upstream:
```
$ git fetch upstream
```
With the upstream updated, we have to merge/rebase our local version (supposing you’re on the master branch):
```
$ git merge upstream/master master
```
Now if you want to update your Github repository with your local repository before making your changes and commit them, we do:
```
$ git push origin master
```
And that’s it! Now our local project is sync and updated with the original version, and if you send the changes to GitHub, the pull request will be enabled.

## Sources
- [https://help.github.com/](https://help.github.com/)
- [https://stackoverflow.com/questions/9257533/what-is-the-difference-between-origin-and-upstream-on-github](https://stackoverflow.com/questions/9257533/what-is-the-difference-between-origin-and-upstream-on-github)
