-   [Cloning](#cloning)
    -   [How to Clone a Repo on Github:](#how-to-clone-a-repo-on-github)
    -   [Cloning Example: Spoon-Knife](#cloning-example-spoon-knife)
-   [Forking](#forking)
    -   [How to Fork a Repo on Github:](#how-to-fork-a-repo-on-github)
    -   [How to Clone a Repo on Github:](#how-to-clone-a-repo-on-github-1)
    -   [Forking Example: Spoon-Knife](#forking-example-spoon-knife)
    -   [Syncing a Fork](#syncing-a-fork)
        -   [Configuring an Upstream Remote for the clone of a fork](#configuring-an-upstream-remote-for-the-clone-of-a-fork)
        -   [Sync a Fork with its Upstream](#sync-a-fork-with-its-upstream)
-   [Challenge](#challenge)
    -   [Avoiding Merge Conflicts](#avoiding-merge-conflicts)
        -   [Rename the copy](#rename-the-copy)
        -   [Directory for editted copies](#directory-for-editted-copies)
-   [References](#references)
    -   [Additional References](#additional-references)

Cloning
=======

Cloning a repository creates a local copy of a repository. Usually one clones from a remote repository (e.g. GitHub, Gitlab, Bitbucket). You can clone a remote repository that you own, a remote repository that you are contributing to, and any other remote repository that is public. You generally clone remote repositories that you own or are contributing to so that you you can work on them - adding material, fixing bugs, or otherwise updating. A common reason to clone public remote repositories is to install software that is published as a repository.

How to Clone a Repo on Github:
------------------------------

1.  On GitHub, navigate to the main page of the repository.
2.  Under the repository name, click the *Clone or download* button.
3.  A dialog box will pop up that says "Clone with HTTPS" or "Clone with SSH". For a repo that you own or are contributing to you will want to use SSH, so if the dialog doesn't say "Clone with SSH", click on "Use SSH".
4.  Click on the clipboard icon to copy the URL.
5.  In RStudio use the New Project command (from the Project menu)
6.  Choose "Version Control" in the *Create Project* dialog box
7.  Choose Git
8.  Paste the repo URL you just copied into the *Repository URL*.
9.  For *Project directory name* you will generally want to use the repo name.
10. Leave *Create project as subdirectory of* as "~"
11. Click Create Project.

Cloning Example: Spoon-Knife
----------------------------

Go to the [octocat/Spoon-Knife](https://github.com/octocat/Spoon-Knife) example repo and try the instructions for [cloning a repo on GitHub](#how-to-clone-a-repo-on-github)

Forking
=======

The big limitation of cloning a public repo that you do not own or collaborate on is that you can't push to it. This means that you can't publish or backup your changes to the remote repository. There is good reason for this limitation - most projects don't want random people to make changes to their projects. There is a solution to this problem GitHub (and other remote repository hosts) allow repositories to be forked. Forking a repo on GitHub makes a copy of the original repository in your account. A forked repository is pretty much just like any other repository you own.

You can test this yourself: 1. Add a new file to the Spoon-Knife repo we just cloned. 2. Commit your new file. 3. Try to push. You should get an error:

    ERROR: Permission to octocat/Spoon-Knife.git denied to USERNAME.
    fatal: Could not read from remote repository.

    Please make sure you have the correct access rights
    and the repository exists.

How to Fork a Repo on Github:
-----------------------------

Forking a repository is a simple two-step process.

How to Clone a Repo on Github:
------------------------------

1.  On GitHub, navigate to the main page of the repository.
2.  In the top-right corner of the page, click the *Fork* button. GitHub will take a few seconds to fork the repo, then open the main page for your fork of the repo.
3.  You can now [cloning your forked repo](#how-to-clone-a-repo-on-github) the same as you would any other repo GitHub, except you own this one, so you can push to it!

On GitHub, navigate to the octocat/Spoon-Knife repository. In the top-right corner of the page, click Fork. Fork button That's it! Now, you have a fork of the original octocat/Spoon-Knife repository.

Forking Example: Spoon-Knife
----------------------------

1.  Go to the [octocat/Spoon-Knife](https://github.com/octocat/Spoon-Knife) example repo
2.  Try the instructions for [forking a repo on GitHub](#how-to-fork-a-repo-on-github)
3.  Now [clone your forked repo](#how-to-clone-a-repo-on-github). Note that for *Project directory name* you will need to call it something besides "Spoon-Knife" since we already used this for our clone of [octocat/Spoon-Knife](https://github.com/octocat/Spoon-Knife), instead we can call it "Spoon-Knife-Fork"
4.  Now we can test pushing:
    1.  Add a new file to the Spoon-Knife-Fork repo we just cloned.
    2.  Commit your new file.
    3.  Try to push. It should work.

Syncing a Fork
--------------

There is one potential problem with our fork. When you fork a repo and clone the fork, the fork no longer has a connection with the original repo (often called the "upstream" repo). Sometimes this is exactly what you want, but sometimes it isn't. If you want to break all ties with the upstream you are all set. However, if you want your fork to receive updates (e.g. bug fixes) that are made to the upstream repo, then you need to re-establish a connection with the upstream. There are two parts to this:

1.  Setting the original repo as an upstream remote for the fork. This only needs to be done once.
2.  Syncing the fork with its upstream. This needs to be done anytime you want to update your fork.

### Configuring an Upstream Remote for the clone of a fork

Do the following in the terminal. Be sure you are in the directory of the forked repo.

1.  Specify a new remote upstream repository that will be synced with the fork by running the command `git remote add upstream UPSTREAM_URL`, where `UPSTREAM_URL` is the URL of the parent repository (upstream) for your fork. You can get this from the "Clone with SSH" dialog on GitHub.
2.  Verify the new upstream repository you've specified for your fork with the command `git remote -v`, which should output something like:

        origin  git@github.com:granek/Spoon-Knife.git (fetch)
        origin  git@github.com:granek/Spoon-Knife.git (push)
        upstream        git@github.com:octocat/Spoon-Knife.git (fetch)
        upstream        git@github.com:octocat/Spoon-Knife.git (push)

### Sync a Fork with its Upstream

Do the following in the terminal. Be sure you are in the directory of the forked repo.

1.  Fetch the new commits from the upstream repository with `git fetch upstream`
2.  Check out your fork's local master branch with `git checkout master`
3.  Run `git merge upstream/master` to merge the changes from upstream/master into your local master branch. This brings your fork's master branch into sync with the upstream repository, without losing your local changes.

Note that if you have made changes to files in your fork that have also been changed in the upstream repo, there may be [merge conflicts that need to be resolved](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging#_basic_merge_conflicts).

Challenge
=========

1.  Fork the [IBIEM Course Material Repo](https://github.com/ibiem-2019/ibiem_2019_material).
2.  Clone your fork into your IBIEM container.
3.  Configure the [IBIEM Course Material Repo](https://github.com/ibiem-2019/ibiem_2019_material) as the upstream remote for your fork clone.
4.  Make a new file in your forked repo, commit it, and push it.

Avoiding Merge Conflicts
------------------------

To avoid merge conflicts, if you want to edit a file in your fork I recommend that you copy the file, and either rename the copy so that you can distinguish if from the original, or keep a separate directory for the copies that you edit.

### Rename the copy

If you wanted to edit this file, you could rename the orginal `git_cloning_and_forking.Rmd` to `git_cloning_and_forking_MINE.Rmd`.

### Directory for editted copies

You could make a new directory in your fork called `my_edits` and put a copy of this file in `my_edits`.

References
==========

This lesson borrows heavily from [Github Help](https://help.github.com/en) and [GitHub Community Forum](https://github.community), specifically: - [Cloning a repository](https://help.github.com/en/articles/cloning-a-repository) - [Fork a repo](https://help.github.com/en/articles/fork-a-repo) - [Configuring a remote for a fork](https://help.github.com/en/articles/configuring-a-remote-for-a-fork) - [Syncing a fork](https://help.github.com/en/articles/syncing-a-fork) - [The difference between forking and cloning a repository](https://github.community/t5/Support-Protips/The-difference-between-forking-and-cloning-a-repository/ba-p/1372)

Additional References
---------------------

-   [Pro Git: GitHub - Contributing to a Project](https://git-scm.com/book/en/v2/GitHub-Contributing-to-a-Project)
-   [Pro Git: Cloning an Existing Repository](https://git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository#_git_cloning)
