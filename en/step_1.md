# Running batch operations on a files using bash

## What are batch operations

Renaming a file using *bash* is fairly easy. You could use the `mv` command for instance.

~~~bash
mv original_file_name.txt new_file_name.txt
~~~

However, what if you needed to rename a thousand files?

A *batch* operation is when you use a command or a set of commands on multiple files.

## Basic batch operations.

To begin with you're going to need some files to work with.

1. To begin, open up a terminal and then create a new directory to hold the files.

	~~~bash
	mkdir batch_test
	~~~

1. Switch into the new directory

	~~~bash
	cd batch_test
	~~~

1. Now you can create 10 new empty text files with this simple command

	~~~bash
	touch {0..9}.txt
	~~~
	
1. Type `ls` to see your new files. You should see the following.

	~~~bash
	0.txt  10.txt  1.txt  2.txt  3.txt  4.txt  5.txt  6.txt  7.txt  8.txt  9.txt
	~~~
	
1. Now that you have a bunch of files, you can have a go at your first basic batch operation. The first thing to try is something trivial. For instance, you can recreate the `ls` command so that;
   - for every file in the directory,
   - the name of the file is output to the terminal.

1. The first part is to tell bash you want to operate on all files in the directory.

	~~~bash
	for f in *;
	~~~

1. `f` will represent each file name in the directory one after another. Notice the `;` at the end of the line. Bash will ignore *cariage returns* so you need to use a `;` to seperate different commands.

1. Next you need to tell bash what to do with each file name. In this case you want to `echo` the file name to standard output.

	~~~bash
	do echo $f;
	~~~
	
1. Here the `$` sign is used to state that you're talking about the variable `f`. Lastly you need to tell bash that you're done.

	~~~bash
	done
	~~~

1. You can hit *enter* after each command if you like, and bash won't run the whole loop until you type `done`, so the command would look like this in your terminal window:

	~~~bash
	for f in *.txt;
	> do echo $f;
	> done
	~~~
	
1. Alternately, as bash doesn't care about carriage returns, you can just type it all on one line:

	~~~bash
	for f in *.txt; do echo $f; done
	~~~
	
## More complex commands
