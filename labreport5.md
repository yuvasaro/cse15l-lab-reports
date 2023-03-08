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
the line to match the indentation of the code but for this purpose it doesn't matter.)

### 5. Run the tests, demonstrating that they now succeed

```bash
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples
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
