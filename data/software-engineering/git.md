# Achieve Agile development using Git

Agile development is both loved and hated within software engineering industry.
However, in many top successful stories, the development team followed the Agile methodology.
They didn't have to match ritual described in the Agile textbooks.
What it matters is to deliver value as soon as possible.

Doing Git in certain ways enables the team to add value into main branch as soon as possible.

## Ultimately, Configure Pull Request (PR) to use Squash Merge by Default

This is your ultimate goal. Whatever the challenges you faced, you should ask yourself,
why couldn't you resolve those challenges and achieve this goal.
Because more than likely, you are doing waterfall, which is in conflict with this goal.

## Practice Agile Nano Waterfall Git Commit

If you identified a typo in a file that already has 30 lines of code
changes, you can `STASH` and commit the typo, which is only a single line of change,
not 30 lines of change. This is highly recommended because you are likely going to forget about it.
The sooner you commit and push it into remote, the sooner you add values. This is why
PR Squash Merge is so important because it enables you to iterate as Agile as possible.
There is absolutely nothing wrong with 300 nano waterfall git commits in a single PR.
It is a similar mindset of saving the file as often as possible. Instead of hording the changes
in RAM, people commit the changes into persistent storage as soon as possible. Committing
changes into local/remote repo as soon as possible is just an extension to what people have
been doing all the time. Whatever is preventing you from doing this, that is a tech debt.
Imagine you cannot save the file every single second, that is a tech debt.

## Practice Agile Small Pull Request (PR)

A PR should be small. Be honest, no one is going to read a large PR. It is a blind approval.
You want PR to be small, thus, when squash merged, it is still easy to understand its goal.
This also promotes smaller Agile sub-tasks that can be completed quickly instead of a
waterfall sized PR.

## Stop using Git CLI, use Git GUI (Learning Curve)

This upsets a lot of people. Use Git CLI has a steeper learning curve than Git GUI.
A lot of times, they don't understands the basics because they are too busy to
figure out how the commands works. Using GUI, the process is simple, reliable, and
low stress. Sure, you can use Git CLI later and there will be time to use it, but
the chance is pretty low. Even for commandline environment like SSH, Visual Studio Code's
built-in Git GUI works perfectly.

## Stop using Git CLI, use Git GUI (STASH)

This upsets a lot of people. Using Git CLI is not necessary and often too cumbersome.
For a simple example, people using Git CLI highly unlikely used Git `STAGE`.
Yes, Git `STAGE`. If you haven't heard of it, you likely already fall pray to Git CLI mindset.
Git `STAGE` is one of the most important feature that anyone should use every time they
make a git commit. For example, if you are testing 30 lines of code changes and discovered
a typo or a poorly phrased comment on the same file, you can `STAGE` that single line of
fix instead of adding other 30 lines of code in the git commit. The same thing can be
achieved using Git CLI, but it is so cumbersome, most people ignored it. Too many times
I have seen Jr developers committing `accidental changes` because they didn't use `STAGE`.
Obviously people makes mistakes, but their frequency of `accidental changes`
is a lot higher when not using `STAGE`.

## Stop using advanced Git commands such as Rebase

This upsets a lot of people. Rebase is bad, just don't do it.
A lot of self-proclaimed git experts will tell you Rebase is fine, it is not.
It is also not the same as PR Squash Merge despite what they tell you.
Rebase tempers your own timeline, it destroy it and build a new one.
PR Squash Merge did not temper your own timeline, it is still the same.
Upon merging, it simply adds a single commit to describe what's new on the main branch.
Why this matters? Because if you made a mistake on Rebase, you may completely
destroy your timeline. Yes, sure, there are ways to recover your mistakes, but
why set yourself up for mistakes anyway? PR Squash Merge is completely reliable and
zero risk and it makes a clean main branch.

The following Git actions are more than enough to get the job done using simple Git GUI.
1. Fetch
1. Pull
1. Branch
1. Stash (not as important)
1. Stage (important)
1. Commit
1. Push
1. Merge latest main branch into current branch
1. Create PR

## Recap

This is how a Corgian develop software and use Git as a simple tool to achieve their goal.
Corgian uses simple to use GUI to interact with Git in an easy and reliable manner.
The changes are freely committed using `STASH`, commit, and push to add value as soon as possible.
Once ready, merge in the latest main branch using the most basic merge strategy to avoid
catastrophic mistakes. A bite sized PR is created, reviewed, approved, and squash merged into
main branch as soon as possible.

## Counter Arguments
### Argument 1: Jokes on You, I don't use PR

Not much to response here. You must have a PR. Doesn't matter what you are doing,
you must have a PR. A PR is meant to review your actions, doesn't matter how
confident you are, there is always a chance of mistake and you want catch it
before merging the changes into main branch.

### Argument 2: I have a long running feature branch with PRs, it was already "reviewed"

Not much to response here. You must have a PR. Just because the long running branch has
commits that were reviewed, doesn't mean it is correct. The main branch can change and
may have conflicts that wasn't caught by the Git merge. You must review everything before
merging into main branch.

### Argument 3: I have a long running feature branch, I don't want to squash commits because each commit is big

Don't use long running feature branch, period. This is not new. The industry prefers
feature flags. Not only this feature flags makes testing more flexible, the bugs can
be caught sooner. Hoarding the bugs in a long running feature branch doesn't kill the
bugs. It only delays the bugs to be identified, which means it increases the chances
that the bugs going into production due to shorter amount of time for testing.

### Argument 4: I don't have a long running feature branch, but I  don't want to squash commits because each commit is big

This means your PR is too large. If a PR include too many changes, it needs to be split up.
Using bathroom for an example. Assume client want their Home (overall software) to have
a bathroom (a software capability). Having a PR for the entire bathroom would be too big.
You want a PR to setup the pipes. A PR to setup electrical. A PR to water proof the bath area.
A PR to place the tiles. A PR to touch up the tiles. A PR to install toilet. And more PRs
for each small a sub-task.

### Argument 5: I can't split up the PR because I have a rule to say the PR must satisfy all acceptance criteria

Please re-evaluate why is that so important, because that is a waterfall approval process.
This is also a very bad inspection process for building a bathroom. For example, if the
Acceptance Criteria is to remodel the bathroom, you absolutely cannot wait for everything
is done. When taking down the tiles and walls during remodeling, it is imperative to check
for toxic mold, you cannot continue work until toxic mold is inspected.
Meaning, there should be a PR called `Inspect and treat toxic mold` and have inspectors
review the walls and approve it. Same for building a pipe, electrical, you need to
review the work before covering them with walls.

### Argument 6: I can't squash the commits because I enforce conventional commit

Please re-evaluate why is that so important, because that is a waterfall git commit requirement.
First of all, git commit message is literally a `message`, NOT CODE.
Conventional Commit has been a trendy pattern for many years and it is wrong.
The git commit message is designed for informational purpose only, period.
It is really that simple. A message/comment is not meant to be used as logic control, period.
Why I am saying this? Because conventional commit has been enforced by CICD team to automate
the version increment during a build. And that is wrong.
Just because it is trendy doesn't make it right.
Incidentally, the industry has been waking up to this problem and started to use file based
logic to control version increment. And that makes whole lot of sense because you can
actually review the configuration in a file instead of reading individual commit messages.
And let's be honest here, who actually go review the commit messages? No one.

### Argument 7: I enforce conventional commit because I want quality commit

Please re-evaluate why is that so important, because that is a waterfall git commit requirement.
What exactly is `quality commit`? Is such definition objective or subjective?
I have seen this mentioned carelessly as it that is a fact.
That is an opinion and overbearing as well. The actual value added into main branch is the PR.
Why should you care someone took 300 git commits to fix typos, give variable a better name,
iterate its solutions many times, flip flop on their own solution internally, and etc.?
The quality of commit doesn't matter as long as the quality of PR is good, period.
Commit the change immediate after fixing a typo or rephrasing a comment adds value.
That is a true spirit of Agile. Adding value as small as possible.
The longer you hold the changes on your local storage and not committed into git and push it
onto the cloud, those value can be lost.
What is worse, when you have so many code to commit at once, you become sloppy and commit
code that is used for debugging purpose only. When doing an Agile tiny commit, you can
`STAGE` the code easily and while your memory is still fresh. People doing large commit
often skip the critical `STAGE` stage and blindly commit everything.

### Argument 8: I don't care, I want to see the original commits

If you must, you can see the original commit in the PR.
