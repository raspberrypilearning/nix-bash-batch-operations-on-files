<<<<<<< HEAD
### Running batch operations on a files using bash

#### What are batch operations
=======
# Running batch operations on files using bash

## What are batch operations?
>>>>>>> 4f67008e32ea7d205cf64b3d8f5cb69e88d6c6e9

Renaming a file using *bash* is fairly easy. You could use the `mv` command for instance.

```bash
mv original_file_name.txt new_file_name.txt
```

<<<<<<< HEAD
What if you needed to rename a thousand files though?
=======
However, what if you needed to rename a thousand files? In that case, you would use a **batch** operation.
>>>>>>> 4f67008e32ea7d205cf64b3d8f5cb69e88d6c6e9

You perform a batch operation when you use a command or a set of commands on multiple files.

<<<<<<< HEAD
- Have a go at your first basic batch operation, using any directory that contains a few files. The first thing to try is something trivial. For instance, you can recreate the `ls` command so that;
   - for every file in the directory,
   - the name of the file is output to the terminal.
=======
## Basic batch operations

To begin with, you're going to need some files to work with.

1. Open up a terminal and then create a new directory to hold the files.

	~~~bash
	mkdir batch_test
	~~~

1. Switch to the new directory.

	~~~bash
	cd batch_test
	~~~

1. Create ten empty text files with this simple command:

	~~~bash
	touch {0..9}.txt
	~~~
	
1. Type `ls` to see your new files. You should see the following:

	~~~bash
	0.txt  10.txt  1.txt  2.txt  3.txt  4.txt  5.txt  6.txt  7.txt  8.txt  9.txt
	~~~
	
Now that you have a bunch of files, you can have a go at your first basic batch operation. Try something trivial first. For instance, you can recreate the `ls` command so that, for every file in the directory, the name of the file appears in the terminal.
>>>>>>> 4f67008e32ea7d205cf64b3d8f5cb69e88d6c6e9

- The first part is to tell bash you want to operate on all files in the directory.

<<<<<<< HEAD
	```bash
	for f in *
	```

- `f` will represent each file name in the directory one after another.

- Next you need to tell bash what to do with each file name. In this case you want to `echo` the file name to standard output.
=======
	~~~bash
	for f in *.txt
	~~~

1. `f` will represent each file in the directory.

1. Next you need to tell bash what to do with each file. In this case, you want to `echo` the file name to standard output.
>>>>>>> 4f67008e32ea7d205cf64b3d8f5cb69e88d6c6e9

	```bash
	do
	echo $f
	```
	
<<<<<<< HEAD
- Here the `$` sign is used to state that you're talking about the variable `f`. Lastly you need to tell bash that you're done.
=======
1. The `$` sign is used to state that you're talking about the variable `f`. Finally, you need to tell bash that you're done.
>>>>>>> 4f67008e32ea7d205cf64b3d8f5cb69e88d6c6e9

	```bash
	done
	```

<<<<<<< HEAD
- You can hit *enter* after each command if you like, and bash won't run the whole loop until you type `done`, so the command would look like this in your terminal window:

	```bash
	for f in *.txt
=======
1. You can hit `Enter` after each command if you like - bash won't run the whole loop until you type `done`. So the command would look like this in your terminal window:

	~~~bash
	for f in *
>>>>>>> 4f67008e32ea7d205cf64b3d8f5cb69e88d6c6e9
	> do
	> echo $f
	> done
	```
	
<<<<<<< HEAD
- Alternately, instead of hitting *Enter* after each line, you could use a `;` to seperate the commands.

	```bash
	for f in *.txt; do echo $f; done
	```
	
#### Manipulating strings.

That last command was a little pointless, but you can do much more with batch operations. For instance, what if you wanted to change the name of each of the files, so instead of being called `0.txt` for instance, they get called `0.md`.
=======
1. Alternately, instead of hitting `Enter` after each line, you could use a `;` to separate the commands.

	~~~bash
	for f in *; do echo $f; done
	~~~
	
## Manipulating strings

That last command was a little pointless, but you can do much more with batch operations. For instance, what if you wanted to change the name of each of the `.txt` files so that they end in `.md`?
>>>>>>> 4f67008e32ea7d205cf64b3d8f5cb69e88d6c6e9

- Try this command:

	```bash
	for f in *.txt; do mv $f ${f%.txt}.md; done
	```

<<<<<<< HEAD
- If you `ls` the contents of the directory, you'll see all the files have been renamed. So how did this work?

- The first part `for f in *.txt` tells bash to run the operation on every file (`$f`) with a `.txt.` extension.

- Next, `do mv $f` is telling bash to *move* each of those files. Next you need to provide bash with the moved file's new name. To do this you need to remove the `.txt` and replace it with `.md`. Luckily bash has an inbuilt operator to remove the endings of strings. You can use the `%` operator. Try this example to see how it works
=======
1. If you `ls` the contents of the directory, you'll see all the files have been renamed. How did this work?

1. `for f in *.txt` tells bash to run the operation on every file with a `.txt` extension.

1. Next, `do mv $f` tells bash to move each file (`$f`). Next you need to provide bash with the moved file's new name. To do this you need to remove the `.txt` and replace it with `.md`. Luckily, bash has an inbuilt operator to remove the endings of strings: the `%` operator. Try this example to see how it works:
>>>>>>> 4f67008e32ea7d205cf64b3d8f5cb69e88d6c6e9

	```bash
	words="Hello World"
	echo ${words%World}
	```

<<<<<<< HEAD
- You could now end something else onto the end of the string.
=======
1. You could now add something else to the end of the `words` string.
>>>>>>> 4f67008e32ea7d205cf64b3d8f5cb69e88d6c6e9

	```bash
	echo ${words%World)Moon
	```

<<<<<<< HEAD
- So the syntax `${f%.txt}.md` replaces all the `.txt` strings with `.md` strings. Incidently, if you use the `#` operator instead of the `%` it will remove a string from the start instead of the end.
=======
1. So the syntax `${f%.txt}.md` replaces all the `.txt` strings with `.md` strings. Incidently, if you use the `#` operator instead of the `%`, the command will remove a string from the start instead of the end.
>>>>>>> 4f67008e32ea7d205cf64b3d8f5cb69e88d6c6e9

