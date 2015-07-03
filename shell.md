# Shell

- ZSH is a lot nicer than bash.
  - oh-my-zsh: makes zsh config easy


## Zsh Scripting

### ZSH expansion & glob

    man zshexpn  # Gives full expansion info

### ZSH multi move

mmv is defined in my aliases.

    mmv *.txt *.mk  # move all .txt to .md

### Referenes

- [Zsh Tips](http://reasoniamhere.com/2014/01/11/outrageously-useful-tips-to-master-your-z-shell/) Good info on globbing


### Snippets

- [great examples](http://zsh.sourceforge.net/Intro/intro_2.html)

globbing

    ls **/*.txt       # Find txt at any depth
    ls *.<000-999>    # Find all files with extensions between 000 and 999.
    ls *.<-999>       # Same as above, shorter
    ls *.<500->       # All file extensions 500 or greater
    ls -l *(.L-50)    # list file size less than 50 bytes (the . ignores directories)
    ls -l *(Lm+50)    # list file size larger/greater than 50 mb
    ls -l *(m1)       # list files modified exactly 1 day ago
    ls -l *(.m4)      # as above but ignoring the directory.
    # list 20 newest python (.py) files anywhere in directory hierarchy
    ls -lt  **/*.py(.om[1,20])
    ls *(.)            # list just regular files
    ls *(/)            # list just directories
    ls -ld *(/om[1,3]) # Show three newest directories. "om" orders by modification. "[1,3]" works like Python slice.
    rm -i *(.L0)       # Remove zero length files, prompt for each file
    ls *(^m0)          # Files not modified today.
    emacs **/main.py   # Edit main.py, wherever it is in this directory tree. ** is great.
    ls **/*(.x)        # List all executable files in this tree
    ls *~*.*(.)        # List all files that does not have a dot in the filename
    ls -l */**(Lk+100) # List all files larger than 100kb in this tree
    ls DATA_[0-9](#c4,7).csv # List DATA_nnnn.csv to DATA_nnnnnnn.csv

killing:

    kill <tab>  # fills in process names


loops & file lists:

    # For each txt file starting with a or f, run process
    for f in [af]*.txt; process $f

Moving around

    cd    # Goes to Home
    cd -  # Goes to previous dir
