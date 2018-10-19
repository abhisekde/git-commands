# Comparing Differences


We're going to compare differences with the "diff" command.
I'm going to use my newly created "hist" alias to show my 
history, at least thus far.
If I wanted to see the differences between two commit points,

I could use the "git diff" command to do so.
I'm going to select the any commit, and then the second point, 
I'm going to use the special pointer called "HEAD",

* git diff "Commit_name " HEAD

Note : "" should be replaced by any commit that you want to 
check the diffrence.
then press enter. 
-> Now we get a difference between the "HEAD", 
which is the last commit on the current branch, which is master, 
and that 
specific commit.
We could use the same command,
except using the "difftool" command,again, the same parameters,
and Git will launch the configured 
diff tool,

* git difftool "Commit_name " HEAD

Note : The same note applies here as well

-> Since I have multiple files that are associated with this 
diff,
I'm going to cycle through each one of them ,
Once we've cycled through all the files that are associated with 
the diff,
Git returns us back to the terminal.

I'm going to modify the "README.md" file.
in order to cycle to the next file involved in the diff.

I've saved those changes, and now I know I have a modified 
Readme file,
but I don't know what those changes are.
Again, "git diff" to 
the rescue.
If I just type "git diff",

* git diff

-> I get a difference between
what's recently changed in the working directory,
versus the "HEAD" position in the Git repository, which is the 
last commit on this branch.

In the same fashion, if we type "git difftool",
we do the same thing
Once you're done looking at the differences between "HEAD" and 
the working directory,

The "diff" command is actually extremely powerful;
I recommend that you look at the help page for the "diff" 
command.
There are many many different options,
and it's extremely flexible and can be used in a number of 
cases.

And, for the most part, anything that can be passed into the 
"diff" command can also be passed into the "difftool" command.



# More about Head and pointers


-> In addition to branches, tags, and other labels for commits
Git has special markers or pointers. 
One popular marker is 
called HEAD.
* HEAD is normally the last commit of the current branch.
That means that, as we switch branches, the location of HEAD moves
to match the last commit location of that branch.
While this is generally true, it is also possible to manually 
move the head location someplace other than the last commit
For now, HEAD points to the last commit of the current branch.


# Branching and Merge Types


Branching and merging are important 
concepts in Git.
Git makes doing both branching and merging 
a lot easier than previous tools,
and thus, many workflows rely upon them.
 a branch is just a timeline of commits.

More accurately, branches are the names or 
labels we give timelines in Git.
We can create and delete branches without 
affecting timelines;
all we are doing is creating or deleting 
labels of commit rages in Git.

So far, we have been working on the 
default master branch.
Now, we can create a new branch to do a 
bit of work, and then rejoin the master 
branch by merging in any changes that 
occurred on 
the new branch.
While merging, Git tries it's best to 
automatically merge when possible,
which leads to several types of merge 
scenarios possible.

-> First, the fast-forward merge; this 
happens in the simplest of cases,
when no additional work has been detected 
on the parent branch, or in our case 
master.
Git will simply apply all commits from the 
other branch directly onto the parent 
branch,
as if we never branched off to begin with.
Of course, we can disable the fast-forward 
merges if they are undesired for some 
reason.

-> Secondly, automatic merges; this 
happens 
when Git detects
non-conflicting changes in the parent 
branch.
Git is able to automatically resolve any conflicts.
In doing so, the old branch's timeline is 
preserved, and a new merge commit
is created to show the merging of the two 
branches. 

-> Thirdly, manual merge
this happens when Git is unable to 
automatically resolve any conflicts.
Git enters a special conflicting merge 
state, which means that
all merge conflicts must be resolved prior 
to moving forward with a commit.
Once all conflicts have been resolved, 
those changes are saved as a merge commit.



# Simple Branching Example


We have a modified "README.md" file.
And that's ok; maybe we intended that this 
file should be modified experimentally,
or as part of a feature of a next update.
Either way, we can use feature or topic 
branches
in order to separate out changes that we 
want to make off of master.
If we use the "git branch" command,

* git branch

-> we can 
see that we have a single branch named 
master.
And, right now, it's highlighted green, 
and with an asterisk,
which denotes that that's the current 
branch.
Now, I could create another branch by 
using the "branch" command
and then separately switching to that 
branch, but I can accomplish both
by using the checkout command with a "-b" 
option.

Type "git checkout -b", for creating the 
branch; space;
and then the name of the branch you wish 
to create and switch to,
I'm calling it "updates";

* git checkout -b updates

then press enter.
-> Now, a couple things have happened. 
One: 
it created a new branch called "updates",
then it switched to that new branch and, 
since there were modifications
pending in the working directory, it 
carried those modifications forward into 
that new branch.
This is a technique you can use when you 
start working on master,
and you decide later that, before 
committing, that these changes really 
should be isolated
into their own feature or topic branch. 

Alright, let's continue,
and I'm going to add some changes to the 
readme; save 
and close.

Back at the terminal, we're going to add 
those changes.

And now, let's commit: "Adding updates 
from branch".

Great, so if I do a "git status", it shows 
that I'm on branch "updates",
and I'm in a clean working directory with 
nothing to commit.

If I do a "git hist". Something that 
should be noted, we have the latest 
commit,
which is on head and updates, but if we go 
one back,
we see that is the commit that "master" is 
associated with.

We can see what the changes are by using 
our "diff" command.
And, the "diff" command will allow us to 
pass in the names of branches instead of 
commit IDs.
So, I'm using "git diff updates master", 
and it shows us what's different.

Alright, let's say that I'm finished with 
whatever updates I needed on the "updates" 
branch.
In order to integrate any changes on my 
branch,
I need to first switch to my parent 
branch, which is master.
In order to switch branches, we use the 
checkout command
"git checkout", branch name; in this case 
"master",

* git checkout master

and press enter.
-> Great now let's look at our history 
from 
the master perspective.
Again, it shows that HEAD is now on 
"master",
since head typically means the last commit 
on the current branch.
And, since the current branch is "master", 
HEAD and "master" are sharing the same 
commit id.
Since our "hist" command specifies the 
"--all" parameter to our log command,
we also notice the commit id associated 
with the "updates" branch.Well, let's go 
ahead and merge in those changes. Type 
"git merge"; space;
and then the name of the branch you wish 
to merge into the current branch,

* git merge updates

then press enter. 
-> For this merge, it's 
such a simple merge
that it's able to do something called a 
fast-forward,
which means that we're going to pretend 
that you never really
switched away from "master" in order to 
make those updates.
So, we're going to apply those commits 
directly to the master branch.
Now, if we do a "git hist", we see that 
HEAD, "updates", and "master",
all point to the same commit id; that's 
the effect of a fast-forward merge.
There are options to disable fast-forward 
merges from happening,
even though they may be possible, but most 
of the time, you'll want this behavior.
Once we have completed merging in our 
changes, we no longer need the updates 
branch.
Effectively, branches in Git are just 
labels of timelines
and, once they've been integrated into the 
main timeline, there's no need for them 
anymore.

Let's use the "git branch" command: "git 
branch -d", for delete;
followed by the name of the branch that we 
wish to delete,
in this case, "updates"; 

* git branch -d updates

press enter.
-> Great, we've deleted that branch;
we're back to just the "master" branch.
We do a "git hist"; we see we no longer 
have the "updates" branch associated with 
that  commit id.
Note: the history didn't go away, just the 
label, "updates", did.
