![image](http://orefalo.github.com/g2/images/G2.jpg)#IntroductionI see it every day, beginners have a hard time picking up **git**. Aside from the DSCM concepts, the command line is not easy: it is aimed at people who know git.. advanced nerds, not beginners.This project is an attempt to make the git command line a friendly place: it eases the learning process by providing guidance and high level commands.##Benefits* **g2** is generally safer than git as it prompts before destructive actions.* **g2** helps setup git settings : sshkeys, username, email and tools.* **g2** provides two letter acronyms for most commands.* **g2** eases the merge process.* **g2** provides a reduced set of commands which give guidance on what to do next.* **g2** enhances command line experience with TAB completion and a smart prompt.* **g2** warns when a branch history was changed on the server (forced pushed).* **g2** checks the freshness of the branch prior to merging and warns accordingly.* **g2** enforces a clean linear history by introducing new commands.* **g2** requires a clean state before rebasing, checking out, branching or merging.* **g2** provides guidance when it cannot perform an operation.* **g2** brings a number of friendly commands such as : panic, sync, freeze, wip.* **g2** eases branch creation.* **g2** is just easier at undoing things.###What G2 is not* A replacement for **git**. Rather, g2 is a layer on top of git* A magic way to learn GIT. It will help by providing guidance but you still need to understand how git works.#Installation**PRE-REQUISITES**: * **g2** is a layer on top of git, If you are doing a manual install, a recent version of git must be pre-installed.* Please backup your favorite ~/.gitconfig as g2 with recreate it from scratch.* For now G2 only runs on **bash**###Linux (RedHat/Ubuntu):Please clone the repository, edit either **/etc/bashrc**, **/etc/bash.bashrc** or **~/.bashrc** and add the following code:    [[ $PS1 && -f /path/to/g2-install.sh ]] && \         . /path/to/g2-install.sh###MacOS:Same as Linux, make the change in `~/.bash_profile`The software will soon be available via a [HomeBrew](http://mxcl.github.com/homebrew/) package, stay tuned.###Solaris (Partially tested):Add the following script to **/etc/bashrc** or **~/.bashrc** (or any other file sourcing those).    PATH=/usr/xpg4/bin:$PATH    export PATH    [[ $PS1 && -f /path/to/g2-install.sh ]] && \         . /path/to/g2-install.sh###Windows:Git is not a prerequisit on windows as the installer comes bundled with it.Please download the Windows native installer from [this link](https://github.com/orefalo/g2/downloads).#How to useThe project introduces the `g` alias. Taken without parameters it displays the following output.```$ gUsage:	abort - aborts any rebase/merge	am <?-f> - amends last commit with staging area	br <?-D> <?-M> <?branch> - list or create branches	bs - bisect	co <branch> - switches branch (either local/remote)	continue - resumes a conflict resolution	cp <commit> - cherry-pick	ci <?params...> - commit	clone <url> - clone a remote repository	df/dt <?params...> - compares files	fetch - synchronizes remote branches	freeze/unfreeze <?-m comment> <?file> - freeze/unfreeze files	gc - garbage collects: run fsck & gc	gp - grep	gui - launches the GUI	ig <file> - adds to gitignore & removes from source control	init <folder> - init a repository	key <?-gen> - displays/generates your ssh public key	mg <?params...> <branch> - merge	mt <?params...> - fixes conflicts by opening a visual mergetool	mv - move (rename) a file	lg - displays commit log	ls <?params...> - list files under source control	panic - gets you back on HEAD, cleans all untracked files	pull/push <?opts> <remote> <branch> - deals with other branches	rb <?params...> <branch> - rebase	rm <params...> - remove	rs <params...> - reset	rs 'upstream' - resets branch to upstream state	rt <?params...> - remote	rv <commit> - revert	setup - configures user, key, editor, tools	sh <?-deep> - show commit contents	sm <?params...> - submodule	ss <?params> - stash	st <?params...> - status	sync - syncs working branch: fetch, rebase & push	tg - tag	track <?upstream_branch> - shows/set tracking	undo file|'commit'|'merge'	wip/unwip - save/restore work in progress to branch```On top of providing two letters acronyms for most git commands, **g2** has interesting features which enhance command line experience.## The PromptTODO##SetupSo here you go, you downloaded git for the first time and I bet you are stuck on the ssh key generation. git is so lame and user unfriendly.allright, with **g2** this is how it works: type `g setup`, answers the questions.and **that's it**! ![image](http://orefalo.github.com/g2/images/setup.png)At anytime in the future, you may display your ssh public key with: `g key`. copy/paste it into github. You are done.```$ git keyssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDDYUTgzU9zjsdda9WBEED5bH+SVMq5bYoIxPSzop2IqUBoyyOlRdHt4dy2r/MWiB2eKQOQmPRE7SeawhFWYbCwEdi6BtEe8m4PiZd3OIRV13TlPj54Hi6Q1Ab8emEAH026L4kwef46+j0aJf/7tZzUw/uZW9Wrnf1VN+J1VlWvmYaG9JpPBuatAlTV9rhCeQ2WO39KYWVYJxH1mO0zPEpuTBojji7HYJtlS4OCKgY9mCVBPiUzzLfmrlIhZz+k5rMWv6i4tQtats23qtHEOi9GxJm4+TSGLwM89/C186CJ+8Yx0g/c2DIbVtPm2VMwUayu8wU4GfBHtOwin4cLWsvT orefalo@dummy.com```Should you need to regenerate the key pair, the process is equally user friendly: use `g key -gen````$ git key -genRegenerate SSH Key (y/n)? yGenerating SSH keys...Generating public/private rsa key pair./Users/orefalo/.ssh/id_rsa already exists.Overwrite (y/n)? yYour identification has been saved in /Users/orefalo/.ssh/id_rsa.Your public key has been saved in /Users/orefalo/.ssh/id_rsa.pub.The key fingerprint is:57:60:84:fa:0e:3b:96:12:15:2e:f3:d5:30:ce:aa:4f orefalo@yahoo.comThe key's randomart image is:+--[ RSA 2048]----+|         o+      ||      . +. .     ||     . = +  .    ||    o + + ..     ||     = +S .      ||    . + ..       ||     oE=         ||    o.= .        ||     +..         |+-----------------+ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDDYUTgzU9zjsdda9WBEED5bH+SVMq5bYoIxPSzop2IqUBoyyOlRdHt4dy2r/MWiB2eKQOQmPRE7SeawhFWYbCwEdi6BtEe8m4PiZd3OIRV13TlPj54Hi6Q1Ab8emEAH026L4kwef46+j0aJf/7tZzUw/uZW9Wrnf1VN+J1VlWvmYaG9JpPBuatAlTV9rhCeQ2WO39KYWVYJxH1mO0zPEpuTBojji7HYJtlS4OCKgY9mCVBPiUzzLfmrlIhZz+k5rMWv6i4tQtats23qtHEOi9GxJm4+TSGLwM89/C186CJ+8Yx0g/c2DIbVtPm2VMwUayu8wU4GfBHtOwin4cLWsvT orefalo@yahoo.com```##Basic commandsGit is often referenced as a content SCM that freezes the state of a repository on every commit. So rather than providing the rather granular commands `git add` and `git rm` commands, **g2** introduces `freeze` and `unfreeze`.Without arguments, `g freeze` literally freezes the state of the workspace into the staging area. Should you need to freeze just one file, or one folder, use `g freeze <path>`.There is also a handy one way command `g freeze -m "msg"`, that skips the staging area and commits directly.Equally straightforward is the `g unfreeze` command, which un stages the files form the index back into the workspace.The contents of the staging area can be committed with the `g ci -m "msg"` command. No rocket science here, you may however like the `g undo commit` command that reverts the last commit##HistoryBeginners are lost when they start git, I found out that an easy way to keep them focused is to provide something visual. Now this is not the github network graph, but it's close enough to get them focused. Type `g lg` and enjoy the enhanced colorized output.![image](http://orefalo.github.com/g2/images/lg.png)Learn to read that tree, it's important: it's the history of the commits in the current branch.--REWORKThe power of git comes from the fact that many super commands can rewrite history.**g2** will **ALWAYS** prompt before running any destructive actions.--##Undoing**g2** comes with the following undo scenarios:`g undo commit` - undo the last commit, put changes back into the staging area`g undo merge` - reverts all commits up to the state before the last merge`g undo myfile.txt` - reverts the changes in myfile.txt with the version from the repository.##Panic!It happened to all of us. You try a new command (like a rebase) and things don't work as expected. Suddenly, you feel the urgency to hunt an expert advise. So you start looking for the closed git-master: bad luck he's not around! there no-one to help you! "Damn it ! I wish I never run that command!", you start pulling your hairs and screaming… "CVS is so much betttter!"Well, you are panicking… and we built a command especially for you: `g panic``panic` checks out the last good state (HEAD) and removes all files not under source control, leaving a clean workspace to resume from. It's the easiest way to get you back on track and ready to work. No more cold sweats and your git-master ##BranchingDisplaying the list of branches is achieved with the branch `g br` command. Note how it provides details not only about the local and remote branches, but also about the state of these branches when compared to the status on the server.```$ g br  gh-pages* master  remotes/origin/HEAD -> origin/master  remotes/origin/gh-pages  remotes/origin/master---gh-pages (ahead 0) | (behind 0) origin/gh-pagesmaster (ahead 0) | (behind 0) origin/master```Given a parameter, the command creates a new branch. **g2** walks you though the steps that will typically take git 3 to 4 commands.TODO:ScreenshotUse checkout `g co NEW_branch` to switch to that branch.```$ g br  NEW_branch  gh-pages* master  remotes/origin/HEAD -> origin/master  remotes/origin/gh-pages  remotes/origin/master---gh-pages (ahead 0) | (behind 0) origin/gh-pagesmaster (ahead 0) | (behind 0) origin/master$ g co NEW_branch Switched to branch 'NEW_branch'$ ```If you are familiar with git, this is no rocket science. There is however a hidden gem which might save you headaches going forward: **g2** is extremely strict when it comes to switching branches: it only works from a stable state.A _stable state_ means: **no modified files, no staged files**. Should you have any changes, **g2** will complain with the following message:    fatal: some files were changed on this branch, either commit <ci>, <wip> or <panic>.##Merging**g2** is based on git, merging with g2 is similar as merging with git. However, g2 does a lot of validations on your behalf. For instance before merging, it will check if your branch is in the past. To make the merge process even easier and consistant, g2 introduces two new commands:`g continue` - resumes a merge or a rebase`g abort` - stops a ongoing merge/rebase##TrackingThe whole concept of _tracking_ is broken in git. It's not so much the feature, it's the way these nerds explained it. All beginers are wondering "What the hell is a **tracking branch** and how is it different from a regular branch?"Backup… let's start from the beginning, the **g2** way:Type the following command: `g track`, you should see something like:![image](http://orefalo.github.com/g2/images/track.png)That's the tracking table. the first sections, shows how each local branch is _linked_ to a remote/branch. "Linked" in git terms is called **tracking**.So how to use it? When you synchronize on that branch, it automatically pushes and pulls to the remote branch that it is connected with.**g2** provides a handy command to display and set tracking: `g track`Now, this example, is actually a bad example. It may happen that a local branch has no remote to sync with. In which case, you would use `g track remote/branch` to set tracking.##SynchingBefore introducing one of the main **g2** features, let me talk about what **NOT** to do when merging with git.    Look at these graphs taken from various projects on github. Note how the branches overlap and how these loops make the graphic extremely difficult to read as the number of commiters increases.![image](http://orefalo.github.com/g2/images/h2.jpg)![image](http://orefalo.github.com/g2/images/h3.jpg)Looks familiar? Wouldn't it be nicer to have straight lines, with segments showing only when feature branches are merged in? As such...![image](http://orefalo.github.com/g2/images/good_branching.png)The above graph is 30+ developers working together on about 20 active feature branches. Note how the graph is clean an easy to read.In order to achieve this result, **g2** enforces two different merging scenarios, each backed by a different command.1. Saving the code into its working branch, that's what we do most of the time2. Merging features branches, like merging the latest changes from production.The matching commands are `g sync` and `g pull`, here is how to use them:* Use `g sync` to synchronize the current branch. The command doesn't take any parameters because it uses the tracking table to figure the remote/branch. To enforce a clean linear history, the changes are always appended to the end of the branch. Once completed, the changes are sent back to the server.For the git expert, the command issues a _fetch, a rebase and a push_ with a multitude of validations in between. For instance, it will block if the remote history was force updated; also it won't push a wip commit (see below).* Use `g pull` when merging contents from a feature branches.##Saving the Work In Progress (WIP)Saving the _work in progress_ is a common task: Typically, git _stash_ comes to the rescue. The issue with stashing is that you typically loose track of which branch the stash was created from. Stashing is indeed a short term solution to save the work in progress.**g2** introduces `wip` and `unwip`. Two handy commands that you will learn to love. Unlike stashing, wip commits the work in progress as a regular commit.```$ g st## masterMM README.mdM  g2-prompt.sh(M=000f0 +2 *1) orefalo@OLIVIERS-IMAC $ g wip[master 0dcbfb3] wip 2 files changed, 31 insertions(+), 13 deletions(-)(M=0dcbf) orefalo@OLIVIERS-IMAC $ g lg* 0dcbfb3 - (HEAD, master) wip (5 seconds ago) <Olivier Refalo>* 000f060 - (origin/master, origin/HEAD) fix freeze and wip (5 hours ago) <Olivier Refalo>* b44487e - adding gui & freeze -m (6 hours ago) <Olivier Refalo>* 7acd770 - documentation, removed undo (24 hours ago) <Olivier Refalo>* a248217 - first commit (3 days ago) <Olivier Refalo>* 5fa2c06 - initial commit (3 days ago) <Olivier Refalo>$ g unwipUnstaged changes after reset:M	README.mdM	g2-prompt.sh$```But unlike commits, wip commits **CANNOT** be **merged, pushed or synched**. You **cannot commit** on top of them either. In orther words, a wip commit in meant to stay at the tip of the branch until you are ready to `unwip` and resume your development.##List of CommandsPlease refer to the [cheatsheet](http://orefalo.github.com/g2/)#FAQ###Why "g2" ?* `g` is the command, and it obviously comes from **git*** `2` because most of the actions are two letters long.###Is it a new git-flow ?No, **g2** doesn't enforce any branching policy.  ###What if my favorite command is missing?Please notify us via the project issue tracker. For the time being, please use `$GIT_EXE`#CreditsAuthor: [Olivier Refalo](https://github.com/orefalo)* Contains a modified version of [git-prompt](http://volnitsky.com/project/git-prompt/) - Leonid Volnitsky* Contains a modified version of git-completion.bash - Shawn O. Pearce* [GUM](https://github.com/saintsjd/gum) by saintsjd. Wonder why this project feelt short on delivery.* Andrew Peterson/ NDP Software for their cool interactive Cheatsheet##LicenseDistributed under the GNU General Public License, version 2.0.##TODO* some completions are not properly working - git push origin <TAB> not working ?* completion, rename __git to avoid conflicts* g mode - for advanced users* g as - aliasing* g undo file* g undo commit* g undo commit -f* g ss/stash* g undo merge = reset --hard ORIG_HEAD* g undo needs more validations## FIXED* sm - not working