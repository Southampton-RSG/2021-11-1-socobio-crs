---
layout: page
title: Exercise Answers
subtitle: Exercise Answers
minutes: 0
---

## Files and Directories



## Creating Things

## Pipes and Filters



## Shell Scripts

Variables in shell scripts

1. Incorrect, since `-1` is passed to `head` in the script it will output the first line of each `.pdb` file, whilst the `-1` passed to `tail` will output the last line of each `.pdb` file.
2. Correct.
3. Incorrect, since `*.pdb` is passed into the script and used by `head` and `tail`, so only `.pdb` files will be used.
4. Incorrect, since the quotes only mean that `*.pdb` will be passed into the script without expansion.

Script reading comprehension

 - Script 1 will output a list of files that match the `*.*` pattern, i.e. `fructose.dat`, `glucose.dat`, and `sucrose.dat`.
 - Script 2 will take in three arguments on the command line, and for each of them, print out their contents.
 - Script 3 will print out all arguments as passed to the script on a single line and append `.dat` to that output.

## Loops

Variables in Loops

 - The first loop will present "fructose.dat glucose.dat  sucrose.dat" three times, since we are running `ls *.dat` three separate times - we're not making use of the loop variable `$datafile`. The second loop will produce "fructose.dat", "glucose.dat", and "sucrose.dat" (each on a separate line) since we're passing `$datafile` to `ls`.

Saving to a File in a Loop - Part One

1. Correct.
2. Incorrect, since we're using the `>` redirect operator, which will overwrite any previous contents of `xylose.dat`.
3. Incorrect, since the file `xylose.dat` would not have existed when `*.dat` would have been expanded.
4. Incorrect.

Saving to a File in a Loop - Part Two

1. Correct.
2. Incorrect, since we're looping through each of the other `.dat` files (`fructose.dat` and `glucose.dat`) whose contents would also be included.
3. Incorrect, since `maltose.txt` has a `.txt` extension and not a `.dat` extension, so won't match on `*.dat` and won't be included in the loop.
4. Incorrect, since the `>>` operator redirects all output to the `sugar.dat` file, so we won't see any screen output.

Doing a dry run

- Version 2 is the one that successfully acts as a dry run. In version 1, since the `>` file redirect is not within quotes, the script will create three files `analyzed-basilisk.dat`, `analyzed-minotaur.dat`, and `analyzed-unicorn.dat` which is not what we want.

## Finding Things

Using grep

1. Incorrect, since it will find lines that contain `of` including those that are not a complete word, including "Software is like that."
2. Incorrect, `-E` (which enables extended regular expressions in `grep`), won't change the behaviour since the given pattern is not a regular expression. So the results will be the same as 1.
3. Correct, since we have supplied `-w` to indicate that we are looking for a complete word, hence only "and the presence of absence:" is found.
4. Incorrect. `-i` indicates we wish to do a case insensitive search which isn't required. The results are the same as 1.

find pipeline reading comprehension

- Find all files (in this directory and all subdirectories) that have a filename that ends in `.dat`, count the number of files found, and sort the result. Note that the `sort` here is unnecessary, since it is only sorting one number.

Matching ose.dat but not temp {}:

1. Incorrect, since the first `grep` will find all filenames that contain `ose` wherever it may occur, and also because the use of `grep` as a following pipe command will only match on filenames output from `find` and not their contents.
2. Incorrect, since it will only find those files than match `ose.dat` exactly, and also because the use of `grep` as a following pipe command will only match on filenames output from `find` and not their contents.
3. Correct answer. It first executes the `find` command to find those files matching the '*ose.dat' pattern, which will match on exactly those that end in `ose.dat`, and then `grep` will search those files for "temp" and only report those that don't contain it, since it's using the `-v` flag to invert the results.
4. Incorrect.

