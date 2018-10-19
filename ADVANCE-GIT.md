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
