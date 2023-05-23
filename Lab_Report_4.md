# Lab Report 4
## Step 4:
I pressed `<up><up><up><up><up><enter>` (the following command was fifth up in the history) for
`ssh cs15lsp23nl@ieng6.ucsd.edu`, which simply logs into ieng6.
![Image](https://hdgehrke.github.io/cse15l-lab-reports/Screen%20Shot%202023-05-22%20at%2020.02.33.png)
## Step 5:
I typed `git<space>clone<space><cmd-V><enter>` as I copied the link from the github page, creating
`$ git clone git@github.com:hdgehrke/lab7.git`, cloning the github repository to be able to run tests, and edit code. 
![Image](https://raw.githubusercontent.com/hdgehrke/cse15l-lab-reports/main/Screen%20Shot%202023-05-22%20at%2021.43.43.png)
## Step 6:
Then I pressed `cd<space>l<tab><enter>` for `$ cd lab7/`, then `<up>` 24 times (then `<enter>`) for `javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java` 
and `<up>` 23 times (then `<enter>`) for `java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests`.
These commands first enter into the correct directory for editing files and running tests. Then, the commands compile and run several different files, 
compiling files necessary for junit and all java files, and running the specific test file and necessary junit files.
![Image](https://raw.githubusercontent.com/hdgehrke/cse15l-lab-reports/main/Screen%20Shot%202023-05-22%20at%2021.48.45.png)
## Step 7:
I then typed `vim<space>List<tab>.j<tab><enter>` for `vim ListExamples.java`, opening vim, where I entered
`/1<enter>NNli<delete>2<esc>:wq<enter>`, fixing the error.
These commands first open vim, straightforwardly, then begin editing in vim. The first step is searching for the character `1`, and then moving from the 
first instance in the file (which appears by default) up (findng previous occurences), reaching the desired spot with two "find previous" keystrokes. 
Then the cursor is adjusted, the command enters insert mode, deletes and then fixes the error, finally returning to normal mode and saving and exiting.
![Image](https://raw.githubusercontent.com/hdgehrke/cse15l-lab-reports/main/Screen%20Shot%202023-05-22%20at%2021.59.49.png)
## Step 8:
Then I pressed `<up><up><up><up><enter>` for `javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java` 
and then `<up><up><up><up><enter>` again for `java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests`,
as both were four commands up in history.
These commands are pretty straightforward, they simply compile and run the same way as in step 6, this time with successful passing of the tests!
![Image](https://raw.githubusercontent.com/hdgehrke/cse15l-lab-reports/main/Screen%20Shot%202023-05-22%20at%2021.57.43.png)
## Step 9:
I then pressed `<up>` 27 times (then `<enter>`) and `<up>` 26 times (then `<enter>`) for `$ git add ListExamples.java` and `$ git commit`, 
respectively, then pressing `<iHere is a commit!<esc>:wq<enter>` to create the commit message.
These commands add the edited file to the staging area, and then commit the change. Then there is some more vim typing, but much simpler, entering
insert mode, typing a message, then leaving and saving, finishing the commit.
![Image](https://raw.githubusercontent.com/hdgehrke/cse15l-lab-reports/main/Screen%20Shot%202023-05-22%20at%2022.11.54.png)
Then I typed `git<space>push<space><cmd-V><space>main<enter>` for `$ git push git@github.com:hdgehrke/lab7.git main`.
This command pushes the commit made just above, and leads to the fixed code appearing on github!
![Image](https://raw.githubusercontent.com/hdgehrke/cse15l-lab-reports/main/Screen%20Shot%202023-05-22%20at%2022.12.13.png)
