Title: Using Git
Category: Resources
Author: Kevin Zheng
Date: 2015-01-11

Updated on 2015-01-11 with new clone URLs, clarification on Git commands,
and a new 'Further Reading' subsection.

### Installation
[Download Git](http://www.git-scm.com/downloads) for your operating system.
Run the installer. The default settings work fine.

You probably want credit for the changes you made. Right-click anywhere
(your desktop is fine) and open Git Bash. Run the following commands:

- `git config --global user.name "Your Fantastic Name Here"`
- `git config --global user.email "yfnh@some.mail.domain.com"`

### Cloning Repositories
Open the folder that you want to store your local Git repositories in. Right
click in that folder and open Git Bash. At the prompt, type (or copy/paste)
one or more of the following commands:

- Robot Program: `git clone https://github.com/Partmedia/ftc-2014.git`
- Website: `git clone https://github.com/Partmedia/robotics-www.git`

Alternatively, if you have an account on GitHub and prefer to clone via SSH:

- Robot Program: `git clone git@github.com:Partmedia/ftc-2014.git`
- Website: `git clone git@github.com:Partmedia/robotics-www.git`

You never have to clone the repository ever again.

### Making Changes
Make sure you are running Git Bash **inside** the repository you just cloned.
You can close the original Git Bash and open another inside the newly-created
folder. More adventurous people who think they're "tech-savvy" may attempt to
use the `cd` command. This is left as an exercise to the reader.

Here are some common tasks and their commands, in no particular order:

- Check the status of your working copy: `git status`
- Check what modifications you made: `git diff`
- Revert uncommitted changes in a file: `git checkout -- <file>`
- _Stage_ your changes in a file to be committed: `git add <file>`

### Committing Changes (and using vim)
Make sure you have added the changes you want committed using `git add`. Then
run `git commit` when you are satisfied.

Vim is a modal text editor. You start in _command_ mode. To insert text, you
need to enter _insert_ mode by hitting `i` or `a`. Once your are finished,
return to _command_ mode by hitting `ESC`.

Remember that the first line of your commit message should be 72 characters or
less and summarize your changes.

If you are satisfied with your commit message, save and quit. Make sure you
are in _command_ mode and type `:wq`, followed by `ENTER`. Git should now
happily commit your changes into your local repository.

### Submitting Changes
By now your changes should have been committed to your local repository, which
lives on **your** computer inside the folder you cloned earlier. At this point
you have two options:

#### Generating Patches
You must use this option if you do not have write access to the repository.
Run `git format-patch origin/master`. This will create several files (one for
each commit you made) in the folder you have open. Attach these files to an
email and send them to someone with write access for review. Once your email
is sent, you can (and should) delete these files.

Generally, you should start out by sending patches. Once you've sent in a
number of good, high-quality patches (there is no magic number) someone will
offer you write access. Pat yourself on the back!

#### Pushing Yourself
If you have write access to the repository, life is easy: `git push`.

This operation can fail: if so Git will tell you. Most likely someone else
committed and pushed a change before you did. Take a deep breath and run `git
rebase`. If the rebase operation is successful, `git push` again.

The rebase operation can also fail. If it does, this means that somebody else
committed and pushed a change that stomps on yours. **Ask for help.**
Remember, if you have write access you can **seriously break things.**

### Keeping Up-to-Date
Git does not automatically keep your local repository in-sync (if it did that,
your changes could be lost). Instead, you must run this often:

`git fetch; git rebase`

### Further Reading
- [Pro Git](http://www.git-scm.com/book/en/v2) by Scott Chacon
  (highly recommended)
