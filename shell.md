# Shell

- ZSH is a lot nicer than bash.
  - oh-my-zsh: makes zsh config easy


## Zsh Scripting

### Refresh commands

To refresh tab completion for commands when there is a new command installed.

	rehash

### ZSH expansion & glob

	man zsh<tab>  # Will show all man sections
	man zshexpn  # Gives full expansion info

### ZSH multi move

mmv is defined in my aliases.

    mmv *.txt *.mk  # move all .txt to .md

### Referenes

- [ZSH quick ref card](http://www.bash2zsh.com/zsh_refcard/refcard.pdf)
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

Modifiers

	echo $f
	README.md
	echo $f:r
	README


	h
	Remove a trailing pathname component, leaving the head.
	r
	Remove a trailing suffix of the form .xxx , leaving the basename.
	e
	Remove all but the suffix.
	t
	Remove all leading pathname components, leaving the tail.
	&
	Repeat the previous substitution.
	g
	Apply the change to the first occurrence of a match in each word, by prefixing the above (for example, g& ).
	p
	Print the new command but do not execute it.
	q
	Quote the substituted words, escaping further substitutions.
	x
	Like q , but break into words at each blank.
	l
	Convert the words to all lowercase.
	u
	Convert the words to all uppercase.
	f
	Repeats the immediately-following (without a colon) modifier until the resulting word doesn't change any more. This modifier and the following four only work with parameter and filename expansion.
	F:expr:
	Like f , but repeats only n times if the expression expr evaluates to n. Any character can be used instead of the : , with the exception that if ( , [ , or { is used as the opening delimiter, the closing delimiter must be ) , ] , or } respectively.
	w
	Makes the immediately-following modifier work on each word in the string.
	W:sep:
	Like w , but words are considered to be the parts of the string that are separated by sep. Delimiters are handled as in F above.
	s/l/r[/]
	Substitute r for l.
	Unless preceded by a g , the substitution is done only for the first string that matches l.

	The left-hand side of substitutions are not regular expressions, but character strings. Any character can be used as the delimiter in place of / . A backslash quotes the delimiter character. The character & , in the right-hand side, is replaced by the text from the left-hand side. The & can be quoted with a backslash. A null l uses the previous string either from a l or from a contextual scan string s from !?s . You can omit the rightmost delimiter if a newline immediately follows r; the rightmost ? in a context scan can similarly be omitted.