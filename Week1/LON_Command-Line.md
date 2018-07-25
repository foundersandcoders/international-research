# FAC 14 - Week 1 Research - Command Line 

Your dream team :heart:

* Martin Gaston
* Armand Lluka
* Emily Rever
* Artemis

## Command Line Cheat Sheet
* Ctrl + alt + t - open terminal
* Ctrl + shift + w or exit - exit terminal
* F11 - full screen window
* Ctrl +/- zoom in/out
* Ctrl + 0 - resets window to default size
* Ctrl + l or clear - clear terminal
* Tab - auto completes file or command
* Up Arrow - scrolls through previous inputs to command line
* pwd - prints full pathname of current working directory
* ls - list files and directories
* cd - change directory
* mkdir - make directory
* rmdir - remove directory
* touch - make empty file

## Navigate Command Line Quicker
* Ctrl + A - Move cursor to start of line
* Ctrl + E - Move cursor to end of line
* Ctrl + U - Delete left of cursor
* Ctrl + K - Delete right of cursor
* Shift + Page Up/Down - Shift view of terminal up/down


## Customise the Command Line
Why might you need that?
* To improve contrast and thus legibility, by changing the colour configuration, 
* To assign a colour to specific elements
* To perform specific actions. For examples, see the table at 
https://www.computerhope.com/issues/ch001645.htm

### Method 1: through the command line
**NB**: The following does not apply to the Windows Command Prompt

*How to change colours*:

1. Access the Command Line's configuration. **NB**: to configure the `bashrc` file, you need to access the Bash prompt with elevated privileges.
If your username is User: 
`/home/User/.bashrc`

2.  An example: `~PS1="[\u@\H \W \!]\$"`
    `\u:` The current user's username
    `\h:` the hostname 
    `\W:` the current working directory, whre $HOME abbreviated with a tilde (~)
    `\$:` If the current user is root, display #, otherwise it'll display $ (see note on elevated privileges further up)

3. To change the colour of the prompt, locate:
    `force_color_prompt=yes`
If the line is commented out, uncomment it. The `\e` and final `m` indicate that the code in between configures colour.
E.g. blue text against yellow background:
`PS1="\e[33;4;44m[\u@\h \W]$"`

### Method 2
**For Linux Mint users**:
You can also modify certain aspects of your Terminal, including colours and font family, through the GUI, through `Edit` --> `Profile Preferences`


## Git Tree Visualization 

You can view all the changes and branches that have been issued since your initial commit using `git log`. The layout can be quite confusing however, especially if you are already quite far into your project, so there are alternatives to make it easier to visualise your commit tree.

One solution is using the `git log --graph` OR `git log --graph --decorate --oneline` command. This creates a visual representaton within the command line from the initial commit, branching across in the relavent places.

Another way of visualizing the git tree is through installing a package via the command line.

**Package installation**

You are able to install packages(programs) via the the command line. Since you are doing this through the command line there is no UI to visualise what packages there are out there or what they do. 

To that end you can use `apt-cache search [search term 1]` to search for packages to install. 

`sudo apt-get update` will update your repos aswell as their depedencies automatically. 

Since we are focusing on *Git Tree Visualization* we will be installing a package called `gitk`. In your terminal window type out `sudo apt-get install gitk`. This will install a git tree visualization tool. Once you navigate to the local repo on your system, simply type out `gitk`.

## Cool Scripts

### [Git Aliases](https://git-scm.com/book/en/v2/Git-Basics-Git-Aliases)
* Add & Commit with add-commit: `$ git config --global alias.add-commit '!git add -A && git commit'`
* Quick Checkout: `$ git config --global alias.co checkout`
* Simple One-Line Log: `$ git config --global alias.ls 'log --graph --all --decorate --oneline'`
* Quick Origin Master Pull: `$ git config --global alias.mpull 'pull origin master'`

### .bashrc/.bash_aliases scripts
* Go Straight to FAC Directory: `alias fac14='cd home/path/to/fac_directory'`
* Update Everything: `alias upgrade='sudo apt-get update && sudo apt-get upgrade && sudo apt-get autoremove'`
* Change and List Directory:
```bash
alias lcd=changeListDirectory
function changeListDirectory {
 cd $1 ; ls -la
}
