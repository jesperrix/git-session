# Guideline for git branching 

Try to keep your master branch clean and create branches. The [feature-branch-workflow](https://www.atlassian.com/git/tutorials/comparing-workflows/feature-branch-workflow) is a good compromise between all novel as well as experienced git users.

## Basic usage examples
- I need a new feature in myproject: `git checkout -b fea/new-cool-feature`
- I need to fix a bug: `git checkout -b fix/weird-error`
- I need to do a quick workaround for a bug: `git checkout -b hot/weird-error`

### allowed branch prefixes
- fea (feature)
- fix (bug fix)
- hot (workaround)

## How to commit on your own branch
- [Keep your first commit line short](https://commit.style/) 
- use imperative *update* instead of *updated*
- use familiar keywords such as: `add, update, remove, fix, refactor`

### How to keep your branch up to date
#### initial situation
```
master  *---*---*---*
             \
my branch     *---*---*
```
    
### Do not merge! We hate merge bubbles
think, before you pull changes from origin or you're [getting into trouble](http://randyfay.com/node/89).
stop using the standardized merge strategy for `git pull`

#### this is wrong
```
master   *---*---*---*---*
              \         /
my branch      *---*---*
```

if you need an update from master or any other branch, [try to *rebase* your branch instead of
merging](http://www.randyfay.com/node/91). try to keep your branch history separated from master, so others can easily follow one
straight line of commits.

#### this is what we want to do
    master   *---*---*---*
                          \
    my branch       -->    *---*---*

So, if you want to pull, try
> git pull --rebase

    
if you want to update your work with stuff from master
> git fetch -a && git rebase master

#### use merge if rebasing is wasting too much time
if you're running into thousand of merge conflicts, try to merge, but do not merge in case of laziness!

if all hope is gone, use cherry pick as your last hope to get back to work.
but use with wisdom! this is only for advanced users: [further reading: cherry-pick vs. merge workflow][http://stackoverflow.com/questions/1241720/git-cherry-pick-vs-merge-workflow]


#### if you finished rebasing, push before somebody else does
if you try to push your rebased branch, your remote will reject your command, because you changed the
history of your branch. you need to do a force push and this is not exactly brilliant.
if other people work on that branch too, inform them about your rebase and check, before pushing.
be patient to your programmer mates!
### I'm done with my work



# TODO: PR workflow


