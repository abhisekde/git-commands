# GIT Commands with Explanations

Configuration after installing git from the official website.

All the commands shown are to be typed in  the git bash.

Basic commands like ls , cd , pwd , dir are also used per preference.

# To initialise the git to your name and Email :

#In git bash:

* git config --global user.name "Your Name"

* git config --global user.email "Your Email"

Note: " " in the above code is required. Change your name and your email 
to desired values.

#Git Initialisation :

Create a new folder for your project and using a git command we can 
initialise it.

* git init demo

->Use the "git init" command to create a new repository within the 
projects folder.
Type "git init"; space; and then the name of your project,
or working folder that you want to create, for this example I'm going to 
use "demo".
Git responded by saying it initialized an empty Git repository within 
the "demo" folder.



#Git Status check :

* git status

->This command is used to check status of the repo.

#Create a new file : 

* touch file.txt

->This creates a new file with the name file .You can change these 
values to like readme.txt and others.Since it is created in the repo it 
will be untracked by git.

#Edit your Newly created file :
 
* nano file.txt

->This opens a text editor for us to edit the contents of the file.After 
editing we can exit by Pressing Ctrl + X and then pressing Y to confirm 
.

#To add file to staging area : 

*git add file.txt

->This moves the file from simply bieng in the working directory to git 
staging area.

#To commit the file :


* git commit -m "First file in the Repo "

->use the "-m" option followed by, in double quotes, a commit message,
using the commit message, "First file in  Repo"


#Git log to view history of commits : 

* git log


-> Git responds with all the commits that are part of this repository.It 
starts off with the commit id. So we have "commit"; space; and then this 
long identifier,that's the SHA-1 identifier that's used to uniquely 
identify commits within a repository.After the commit id, we have the 
authorfollowed by the date, then our commit message.

We can get similar information by using the "show" command.


* git show
 

-> It will show the last commit and a diff containing all the changes.
To get out of the show command, press 'q' 


# Git express commit :
 

-> We use the "git commit", passing the "-a" parameter,the "-a" 
parameter 
tells Git to first add modified files to the Git staging area,and then 
directly proceed to committing.

* git commit -a 

-> We can accomplish this with basically a 
single command with this option.
Now, you might be wondering, "hey, why are we adding a modified file?"
Well, it's just the way that Git works.
So, basically, the way I look at 
it is that I'm adding , the modifications to the Git staging area, and 
then committing those changes.
Let's proceed forward by also specifying our "-m" parameter,that we can 
actually combine together, into a single "-am" parameter.
So, we have "git commit -am", then space, and then the commit 
message:"Updating README", then press enter.

* git commit -am "Updating README"

 Great, the commit's 
completed.


# Backing Out changes : 


-> So, let's get started. I'm going to modify the Readme file 
again,
Save 
and then close;
back at the terminal we see that we have our modified 
Readme file.
What if I determine that I really don't want those changes?
Well, what I could do to unstage those changes,
is I could use the "git 
reset" commandas outlined in the "git status" command; so let's do that 
now.
It tells us to use "git reset", space, and the special pointer "HEAD" in 
all caps,space, and then the file to be unstaged: in my case 
"README.md".

* git reset HEAD README.md


-> Let's press enter; great, Git responds with saying that the 
stages have 
been reset.

-> If we open up our Readme file, that text is still there; it's 
just been 
unstaged.
Now If I want to revert back to the last known good state of that 
file,
which is back in the Git repository.
To do that, let's follow the 
instructions provided, which tells us to use"git checkout --" and then 
the filename: alright "git checkout -- README.md".

* git checkout --README.md

-> Press enter,
We're back to a clean working directory, what about the contents of that 
file ?
 When we open up that file, our changes are gone.


   
# Creating New Alias for git log : 


-> If I type the standard "git log" command, I see that I have 
two commits.

So, let's use "git log --oneline", which will provide a simplified 
commit entry,
providing a lot of that information on a single line, instead of 
multiple lines ,
"--graph", which will provide an asterisk based graph denoting our 
branching hierarchy,
"--decorate", which will tell us which commits are a part of which 
branches,and other labels within the Git repository ,
 and then "--all",which will provide the history for all the branches 
that are available in this repository.

* git log --oneline --graph --decorate --all

-> Let's press enter; now we have a radically different view of 
our "git 
log" command.

To create a Git alias, which is basically a new command that is a 
shortened representation 
of an existing longer command, we're going to piggyback off of Git's 
"config" command.

At the user level, not at the repo level; space; and then the config key 
"alias."
then whatever name you want to use for your new command, in my case 
"hist"
space; and then, in double quotes, the command, leaving out the leading 
"git" command
so, instead of "git log", you just start with "log",
so in double quotes, I have "log --oneline --graph --decorate --all".

* git config --global alias.hist "log --oneline --graph 
--decorate --all"

-> Double check that line, and then press enter.
We can double check this entry made it in by listing Git's “config” 
entries
"git config --global --list", 

*git config --global --list

then press enter.
-> And, at the very end, you see "alias.hist=log --oneline 
--graph 
--decorate --all".

Alright, let's test that out; to use an alias, just type "git"; space; 
and then the alias name,in my case "hist", then press enter. If you were 
successful,
you should have the exact same output as the "log" command that we had 
previously.
Using aliases does not preclude you from passing additional parameters
to the underlying command. So, in this case, if I type "git hist", 
space,
and then the option "--", space, and then a file, 

* git hist

-> then press enter, If sucessfull it will display the same 
results as we 
had above.



# Renaming file


-> I'm going to create a file called "example.txt".
Once I've saved and closed and returned back to the terminal, 
you see we have a new file.

Now, let's add the file, 
And, now let's commit: "adding example 
file".
Currently I have the "example.txt" file in my file system.
What if I decide that I don't like the name of that file?
Well,
I can actually change it using the Git commands, and doing 
so provides some extra advantages over just changing the file 
within the operating system.
If I type "git mv" for move, we're going to move the file to its 
new name.
So, I'm moving it from "example.txt" to "demo.txt", effectively 
renaming the file.

* git mv example.txt demo.txt

-> Press enter
let's do a "git status".
Git shows that it's going to rename "example.txt" to "demo.txt",
but this change is actually staged, indicated by "Changes to be 
committed".
If we do an "ls", we can see that the file has already been 
renamed.

on the operating system. Well, to finish the task, we need to 
actually commit :"git commit -m", with the commit message 
"renaming example".

Great, and within the commit it shows that we renamed the file, 
"example.txt",
to "demo.txt", with, in parenthesis, a "(100%)" confidence 
level.
If we would have made modifications to the "demo.txt" file prior 
to committing,
then that level would have been lower than 100%.


# Deleting The file


-> But, what if we didn't want that file at all? Well, we could 
remove it.
Instead of removing it using the facilities provided by the 
operating system,
if we use Git to do the removal, then we get the extra benefit
of Git automatically tracking the deletion.

Doing an "ls", we have our "demo.txt".
We type "git rm" 
for remove,
then our file that we want removed,

* git rm demo.txt

-> then we can press enter.
It tells us that the "demo.txt" file has been removed.
If we do an ls, we see that we no longer have our "demo.txt" 
file.
However, if we do our "git status", we can see that our deletion 
has only been staged.
To complete the deletion, we need to actually do the commit: 
"git commit -m "deleting demo file" "




