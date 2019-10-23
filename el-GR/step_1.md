### Running batch operations on a files using bash

#### What are batch operations

Renaming a file using *bash* is fairly easy. You could use the `mv` command for instance.

```bash
mv original_file_name.txt new_file_name.txt
```

What if you needed to rename a thousand files though?

A *batch* operation is when you use a command or a set of commands on multiple files.

- Have a go at your first basic batch operation, using any directory that contains a few files. The first thing to try is something trivial. For instance, you can recreate the `ls` command so that;
   - for every file in the directory,
   - the name of the file is output to the terminal.

- The first part is to tell bash you want to operate on all files in the directory.

    ```bash
    for f in *
    ```

- `f` will represent each file name in the directory one after another.

- Next you need to tell bash what to do with each file name. In this case you want to `echo` the file name to standard output.

    ```bash
    do
    echo $f
    ```

- Here the `$` sign is used to state that you're talking about the variable `f`. Lastly you need to tell bash that you're done.

    ```bash
    done
    ```

- You can hit *enter* after each command if you like, and bash won't run the whole loop until you type `done`, so the command would look like this in your terminal window:

    ```bash
    for f in *.txt
    > do
    > echo $f
    > done
    ```

- Alternately, instead of hitting *Enter* after each line, you could use a `;` to seperate the commands.

    ```bash
    for f in *.txt; do echo $f; done
    ```

#### Manipulating strings.

That last command was a little pointless, but you can do much more with batch operations. For instance, what if you wanted to change the name of each of the files, so instead of being called `0.txt` for instance, they get called `0.md`.

- Try this command:

    ```bash
    for f in *.txt; do mv "$f" "${f%.txt}.md"; done
    ```

- If you `ls` the contents of the directory, you'll see all the files have been renamed. So how did this work?

- The first part `for f in *.txt` tells bash to run the operation on every file (`$f`) with a `.txt.` extension.

- Next, `do mv $f` is telling bash to *move* each of those files. Next you need to provide bash with the moved file's new name. To do this you need to remove the `.txt` and replace it with `.md`. Luckily bash has an inbuilt operator to remove the endings of strings. You can use the `%` operator. Try this example to see how it works

    ```bash
    words="Hello World"
    echo ${words%World}
    ```

- You could now end something else onto the end of the string.

    ```bash
    echo ${words%World)Moon
    ```

- So the syntax `${f%.txt}.md` replaces all the `.txt` strings with `.md` strings. Incidently, if you use the `#` operator instead of the `%` it will remove a string from the start instead of the end.

