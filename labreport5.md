# Lab Report 5 - Favorite Lab Activity

## A revamp of CLDQ using a bash script

For this lab report, I will create a bash script that will accomplish the tasks of CLDQ in 
[Lab 7](https://ucsd-cse15l-w23.github.io/week/week7/) very quickly. It will include the steps 
post-setup.

### 1. Log in to ieng6

```bash
ssh cs15lwi23amt@ieng6.ucsd.edu
```

This line logs in to my account on `ieng6`.

### 2. Clone my fork of the lab7 repository

```bash
git clone git@github.com:yuvasaro/lab7.git
cd lab7
```

These lines of code first clone the git repository onto my computer in the current working directory, 
then change directory into the repository.

### 3. Run the tests, demonstrating that they fail

```bash
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples
```

These lines of code first compile the Java code files using the classpath with the JUnit related `.jar`
files, then run the JUnit tests in the compiled `TestListExamples` class file.

### 4. Edit the code file to fix the failing test

```bash
sed -i "43s/.*/index2 += 1;/" ListExamples.java
```

This command does an inline edit in the `ListExamples.java` file at line 43, where the error is. It
replaces the entire line with the fixed code, which is `index2 += 1;`. (This command does not indent
the line to match the indentation of the code but for this purpose it doesn't matter.) In the command,
`-i` means inline editing and the string passed in contains the line number (43), the pattern to
replace (in this case, the entire line, so `.*`), and the string to replace the line with
(`index2 += 1`).

### 5. Run the tests, demonstrating that they now succeed

```bash
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar 
                     org.junit.runner.JUnitCore TestListExamples
```

This will recompile the Java code files and rerun the tests on `TestListExamples`. This time, the tests
will pass.

### 6. Commit and push changes to Github

```bash
git add .
git commit -m "i win"
git push
```

These lines of code add the changes I made to the Java code, commit it to my local repository, and push
it to the remote repository on Github.

### The Script

Altogether, the script will look like this:

`cldq.sh`

```bash
ssh cs15lwi23amt@ieng6.ucsd.edu
git clone git@github.com:yuvasaro/lab7.git
cd lab7
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar 
                     org.junit.runner.JUnitCore TestListExamples
sed -i "43s/.*/index2 += 1;/" ListExamples.java
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar 
                     org.junit.runner.JUnitCore TestListExamples
git add .
git commit -m "i win"
git push
```

This script should theoretically accomplish all the tasks of CLDQ.

However, I immediately ran into a bug when I tried to run it:

```
~/Downloads/UCSD/CSE 15L/CLDQ ❯ bash cldq.sh
Last login: Wed Mar  8 17:17:19 2023 from 128.54.191.101
Hello cs15lwi23amt, you are currently logged into ieng6-202.ucsd.edu

You are using 0% CPU on this system

Cluster Status 
Hostname     Time    #Users  Load  Averages  
ieng6-201   17:15:01   11  0.64,  0.29,  0.25
ieng6-202   17:15:01   14  0.03,  0.05,  0.13
ieng6-203   17:15:01   12  0.15,  0.26,  0.39


        *** SDSC Core Network Upgrade ***
        2023-03-07 19:00 - 2023-03-08 03:00
This work is now complete. If there were any disruptions to your
work or notice any problems that may have been caused by the network
upgrades please report them to the service desk.

https://support.ucsd.edu/its


 
Wed Mar 08, 2023  5:18pm - Prepping cs15lwi23
[cs15lwi23amt@ieng6-202]:~:416$ 
```

It successfully logs in to `ieng6`, but then does nothing afterwards. After logging out of `ieng6`,
the rest of the script ran locally on my computer. I realized that after the script logs in to
`ieng6`, it waits for me to log out before executing the rest of the commands.

I searched the internet for a solution to this issue and found a fix 
[here](https://stackoverflow.com/questions/305035/how-to-use-ssh-to-run-a-local-shell-script-on-a-remote-machine).
A user posted this method of running commands on a remote ssh connection within a bash script:

```bash
ssh user@host <<'ENDSSH'
#commands to run on remote host
ENDSSH
```

From what I understand, these lines of code log in remotely with `ssh` and then set `ENDSSH` as 
the command that would terminate the `ssh` connection. All I have to do is replace `user@host`
with my `ieng6` address and `#commands to run on remote host` with all the commands I need to run.

Here is my resulting script:

```bash
ssh cs15lwi23amt@ieng6.ucsd.edu <<'ENDSSH'
git clone git@github.com:yuvasaro/lab7.git
cd lab7
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar 
                     org.junit.runner.JUnitCore ListExamplesTests
sed -i "43s/.*/index2 += 1;/" ListExamples.java
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar 
                     org.junit.runner.JUnitCore ListExamplesTests
git add .
git commit -m "i win"
git push
ENDSSH
```

Now, the script will `ssh` into `ieng6`, and until the `ENDSSH` command is executed, the commands that
are in the script will be run on `ieng6`.

Here is the result:

```
~/Downloads/UCSD/CSE 15L/CLDQ ❯ bash cldq.sh
Pseudo-terminal will not be allocated because stdin is not a terminal.
stdin: is not a tty
Hello cs15lwi23amt, you are currently logged into ieng6-202.ucsd.edu

You are using 0% CPU on this system

tput: No value for $TERM and no -T specified
Cluster Status
tput: No value for $TERM and no -T specified
tput: No value for $TERM and no -T specified
Hostname    Time    #Users  Load  Averages
tput: No value for $TERM and no -T specified
tput: No value for $TERM and no -T specified
tput: No value for $TERM and no -T specified
tput: No value for $TERM and no -T specified
tput: No value for $TERM and no -T specified
tput: No value for $TERM and no -T specified
tput: No value for $TERM and no -T specified
ieng6-201  18:00:01  7   0.57,  0.18,  0.19
ieng6-202  18:00:01  15  0.18,  0.18,  0.28
ieng6-203  18:00:01  15  0.12,  0.27,  0.35

tput: No value for $TERM and no -T specified

        *** SDSC Core Network Upgrade ***
        2023-03-07 19:00 - 2023-03-08 03:00
This work is now complete. If there were any disruptions to your
work or notice any problems that may have been caused by the network
upgrades please report them to the service desk.

https://support.ucsd.edu/its

tput: No value for $TERM and no -T specified

 
Wed Mar 08, 2023  6:02pm - Prepping cs15lwi23
Cloning into 'lab7'...
JUnit version 4.13.2
..E
Time: 0.532
There was 1 failure:
1) testMerge2(ListExamplesTests)
org.junit.runners.model.TestTimedOutException: test timed out after 500 milliseconds
        at java.util.Arrays.copyOf(Arrays.java:3210)
        at java.util.Arrays.copyOf(Arrays.java:3181)
        at java.util.ArrayList.grow(ArrayList.java:267)
        at java.util.ArrayList.ensureExplicitCapacity(ArrayList.java:241)
        at java.util.ArrayList.ensureCapacityInternal(ArrayList.java:233)
        at java.util.ArrayList.add(ArrayList.java:464)
        at ListExamples.merge(ListExamples.java:42)
        at ListExamplesTests.testMerge2(ListExamplesTests.java:19)

FAILURES!!!
Tests run: 2,  Failures: 1

JUnit version 4.13.2
..
Time: 0.015

OK (2 tests)

[main 6feab7c] i win
 Committer: Yuvanand Saravanan <cs15lwi23amt@ieng6-202.ucsd.edu>
Your name and email address were configured automatically based
on your username and hostname. Please check that they are accurate.
You can suppress this message by setting them explicitly. Run the
following command and follow the instructions in your editor to edit
your configuration file:

    git config --global --edit

After doing this, you may fix the identity used for this commit with:

    git commit --amend --reset-author

 4 files changed, 1 insertion(+), 1 deletion(-)
 create mode 100644 ListExamples.class
 create mode 100644 ListExamplesTests.class
 create mode 100644 StringChecker.class
To github.com:yuvasaro/lab7.git
   f750e52..6feab7c  main -> main
```

Success! The script successfully logged in to `ieng6`, ran the tests and showed that they
failed, edited the file to fix the buggy line of code, recompiled and reran the tests, and
committed the changes to my remote repository.

I decided to make a minor change to my script to improve its readability. The classpath to
the files in `lib` are used several times, so it would make sense to store it in a variable.
I also stored the ssh url of the repository in a variable.

Here is the finished product:

```bash
ssh cs15lwi23amt@ieng6.ucsd.edu <<'ENDSSH'

REPO="git@github.com:yuvasaro/lab7.git"
CPATH=".:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar"

git clone $REPO
cd lab7
javac -cp $CPATH *.java
java -cp $CPATH org.junit.runner.JUnitCore ListExamplesTests
sed -i "43s/.*/index2 += 1;/" ListExamples.java
javac -cp $CPATH *.java
java -cp $CPATH org.junit.runner.JUnitCore ListExamplesTests
git add .
git commit -m "i win"
git push

ENDSSH
```

Absolutely beautiful. 

(Note that I had to create the variables *after* the remote login because otherwise the variables 
will be stored locally on my computer and the remote computer's bash will not find them.)
