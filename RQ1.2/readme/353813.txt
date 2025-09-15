Arnold Worldwide git and GitHub training
========================================

This is the readme file in markdown format.

## Step 1: Sign up ##
*Once you've done this step, you never have to do it again!*

Sign up on github.com if you haven’t already. You can use your personal
email address, but add your Arnold address too (click the wrench icon in
the top right and go to the Email Addresses section).

If you're already on github (and added your Arnold email as described above),
continue to step 1a.

### Step 1a: Join the organization ###
*Once you've done this step, you only have to do it again if joining another
github organization, e.g. a vendor's org)*

Request to join the ArnoldWorldwide organization.
Go to:

> https://github.com/ArnoldWorldwide/git-training/issues/1

and post a message to the thread.

## Step 2: Install and configure git on your computer ##
*You only have to do this once per computer.*

Download git, create an SSH key, connect your computer to github. You only
need to do this once per computer so just follow the appropriate guide
below, call me over if you need help.

* OSX -- http://help.github.com/mac-set-up-git/
* Win -- http://help.github.com/win-set-up-git/

## Step 3: Fork the repository ##
*You will do this for every git repository you work on if it's on GitHub*

Fork the training repository -- go to this page:

> https://github.com/ArnoldWorldwide/git-training

and click the "Fork" button to the right of the repository name.
This will create a copy of the repository in YOUR GitHub account - e.g.,

> https://github.com/davidosomething/git-training

see the username in there?
You can see who's forked the repository here:

> https://github.com/ArnoldWorldwide/git-training/network/members

## Step 4: Clone the repository ##
*You will do this for every git repository you work on*

"Cloning" is making a copy of all the files in the repository to work
on. It's like doing an SVN checkout, but you're checking out an entire
repository (for the Arnold SVN you've been checking out only folders
from the repository as you need them).

To clone the git training repository, use the terminal to go to the folder
where you keep your source code (use "cd" to change directories" and
"ls" to list directory contents) and type

    git clone git@github.com:ArnoldWorldwide/git-training.git

The first part: "git" is the program we're running - git. The second part is
the command argument, clone. The third part is the url to the repository.
You can get this from the github page:

> https://github.com/ArnoldWorldwide/git-training

It's the URL in the text box at the top of the page.

## Step 5: Create a training file ##

After you've cloned the repository, cd into it:

    cd git-training

Now that you're in the training folder, create a new file using your
text editor (save into this folder if you use a gui program like BBEdit
or Eclipse). Name the file with your first initial last name with an html
extension -- e.g., "dotrakoun.html"
You can put whatever you want into it.

## Step 6: Check the status of the git repository ##

You just created a new file but git doesn't know about it. In your open
terminal at the git training folder, type the following:

    git status

This command tells you about the git repository status. It tells you
what branch you're in first -- "master." We'll deal with that later.

It also tells you that your file is currently untracked. That means it's
new and not under version control. Let's put in into the repository.

## Step 7: Stage the file on the git index ##

Type the following command (Change dotrakoun to your file name).

    git add dotrakoun.html

This adds your file to the index. This is called "staging" a file. This
basically marks the file, saying that if you make a commit, this file
will be committed. Git does this so you can have files optionally in the
repository, and if you accidentally add a file you can remove it before
it is committed to the repository.

If you do a *git status* at this point you'll see the file is marked as
"new file."

Think of this this way: you just put the file in an envelope, but didn't
mail it yet.

## Step 8: Unstage the file from the index ##

Just for pracitce, lets unstage the file. You do that using this
command:

    git reset HEAD dotrakoun.html

The "HEAD" part is the revision you want to go back to, in this case
it's the latest one which is referred to as "HEAD." If you do a *git
status* at this point, you'll see the file is "untracked" again.

You just took the file out of the envelope.

## Step 9: Commit the file to your local repository ##

Add the file to the index again. Now commit it to the repository using this
command:

    git commit -m "added my file"

The "-m" means with a message. If you don't include that you'll probably
end up in the VIM text editor (type ":q!" to quit vim).

The text in quotes after the "-m" is the commit message. Add something
informative talking about what updates you made. For example, if you
edited the title of your HTML file, that should be in the commit
message.

Think of committing as putting your envelope of files in the mailbox.

## Step 10: Push the updates to GitHub ##

You've committed your files, now push them to GitHub:

    git push

Pushing means the envelope is been sent to the Post Office, and
recipients can pick it up! Anyone with access to your repository on
GitHub can now view your new file at

> https://github.com/davidosomething/git-training

(with your username instead of mine).

## Step 10a: Set the correct default upstream ##

Ok so you guys won’t be able to push into the repository because the one I
told you to clone is the main repository owned by ArnoldWorldwide (trying to
take the letter to an unauthorized post office).
Instead you’ll have to tell git about your forked repository:

    git remote add upstream git@github.com:davidosomething/git-training.git

Replace “davidosomething” with your own username on GitHub. This tells git to
add a remote repository and refer to it as “upstream.”
Now that git knows about your fork, you can push to it:

    git push –u upstream master

That will push the stuff in the last commit (letters in the mailbox) to the
remote repository (the correct post office).
The “-u” means to set this remote repository (upstream) as the default
upstream (future “git push”es will automatically go here).

I'll check on your repositories to see when you've gotten here.
