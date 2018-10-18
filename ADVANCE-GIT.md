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
