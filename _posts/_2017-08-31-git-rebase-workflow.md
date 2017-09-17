---
layout: post
title:  "My Git Workflow with Rebase"
date:   2017-08-31
categories: git
---
Just my 2 cents for anyone who is interested in using Github for feature branching, pull requests, a rebase workflow, and as a bonus- an online backup of your work. This process has treated me pretty well over the past few years across multiple teams and projects.

First , why this workflow and bothering with pull requests and rebase?
* By using a branch I keep all my work on a feature/story in one place until I know it's ready to go back into the master branch. I can use the branch test it out locally or in a remote environment without mucking up master.
* By creating a pull request on Github I get:
    * a place for my team to see my work and either offer advice or at least get some context on how I'm doing something.
    * I increase the 'bus factor' on my work so that if I was unable to complete the story my team could pick up from the PR.
    * A nice visual notification telling me if something I'm working on conflicts with the latest chnages to master
    ![Github conflict notification](/assets/img/no_conflicts.jpg){:class="img-responsive"}

  * online backups
* By regularly rebasing master into my branch, using `git pull --rebate origin master`, I make sure that my branch regularly has all changes from master and I can resolve conflicts before they get out of control
* By using rebase my branch has a history identical to master, with all of my commits applied at the end of that history. When I merge in my PR all of my commits are in a nice, tight grouping (great in those cases when I need to revert or cherry-pick)

The workflow itself is pretty straightforward:
* create a local branch for my new story
* commit changes to my local branch
* push my branch to github
* grab latest changes from master using `git pull –rebase origin master` either when I'm done with my work, when I know there's a conflict, or at the very least, at the end of the day.
* fix any conflicts from the latest changes and use `git add path/to/fixed_conflict_file.txt` and`git rebase –continue` (or `git rebase –abort` if something is out of whack)
* push my branch up, and force push if I’ve rewritten the history of my branch since I last pushed (this can happen with rebase and is now much SAFER now since Github allows you to disable force pushes to master)
* Use github.com to manage the merge of my PR when I’m done

So, that's what works for me- what other workflows do people have for version control and collaboration? Hit me up at [@mikeebert](https://www.twitter.com/mikeebert)
