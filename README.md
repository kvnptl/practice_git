# Version control and Git - Hands-on

### Overall topics:

- Git add
- Git commit
- Git push
- Git pull
- Git log
- Git restore --staged
- Git reset --soft
- Git status
- Git branch
- Git checkout
- Git merge
- Git diff
- Git remote
- Git clone
- Git fetch
- Fork
- Pull request
- Github issues
- .gitignore file

### Requirements and commands to install:

1. Create an account on [GitHub](github.com)
- Use your personal email address and then link your university email address to your GitHub account

2. Create a new repository on GitHub

3. Install Git on your computer (if you don't have it already) using the following command:

```bash
sudo apt install git
```

4. [Optional] If you want to see the active branch name in your terminal, something like this:
        
```bash
user@computer:~/path/to/your/project (branch-name)$
```

Then, you can add the following lines to your bashrc file:

Note: What is a bashrc file? It is a file that is executed every time you open a terminal. It is used to set up your terminal environment.

- Open the bashrc file using the following command:

```bash
gedit ~/.bashrc
```

- Add the following lines at the end of the file:

    
```bash
# Show git branch name
force_color_prompt=yes
color_prompt=yes
parse_git_branch() {
 git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/(\1)/'
}
if [ "$color_prompt" = yes ]; then
 PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[01;31m\]$(parse_git_branch)\[\033[00m\]\$ '
else
 PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w$(parse_git_branch)\$ '
fi
unset color_prompt force_color_prompt
```


5. From today onwards, use git to manage all your projects

6. Also, put all the foundation course files on your GitHub account

7. Get the Git cheatsheet from Github Education | [Git cheat sheet](https://education.github.com/git-cheat-sheet-education.pdf)

### Basic git workflow:

1. Configure Git on your computer using the following commands:

- First check if you have Git configured on your computer using the following command:

```bash
git config --list
```

- If you don't have Git configured on your computer, then configure it using the following commands:


```bash
git config --global user.name "Your Name"
git config --global user.email "dontcopythis@whatever.com"
```

2. Create a new directory on your computer and clone the repository you created on GitHub using the following command:

```bash
git clone <repo-link>
cd <repo-name>
ls -a
```

3. Create a readme file and add some text to it using the following command:

```bash
touch README.md # md stands for markdown
gedit README.md # or use your favorite text editor (e.g. vim, nano, etc.)
```

4. Check the status of the repository using the following command:

```bash
git status
``` 

- You should see that the readme file is untracked and that you have one untracked file

5. Add the readme file to the staging area using the following command:

```bash
git add README.md
```

6. Check the status of the repository using the following command:

```bash
git status
```

- You should see that the readme file is staged and that you have one staged file (in green)

7. Commit the readme file to the repository using the following command:

```bash
git commit -m "Add README.md" # -m stands for message
```

8. Check the status of the repository using the following command:

```bash
git status
```

- You should see that the readme file is committed and that you have one committed file (in green)

9. Check the log of the repository using the following command:

```bash
git log
```

- Git log shows the history of the repository
- It shows the commit hash, the author, the date, and the commit message
- It also shows the HEAD (the current commit) and the branch name (main)
- You can exit the log by pressing `q`

```bash
git log --oneline
```

- Git log oneline shows the history of the repository in a compact way
- It shows the commit hash and the commit message
- You can exit the log by pressing `q`

10. Push the changes to the remote repository using the following command:

```bash
git push <remote-name> <branch-name>
```

- How to get the remote name and branch name on terminal:

```bash
git remote -v # -v stands for verbose
git branch
```

11. Check the status of the repository using the following command:

```bash
git status
```

- You should see that the readme file is up to date and that you have nothing to commit

12. Make some changes to the readme file and save them

13. Check the status of the repository using the following command:

```bash
git status
```

- You should see that the readme file is modified and that you have one modified file

14. Add the readme file to the staging area using the following command:

```bash
git add README.md
```

15. Check the status of the repository using the following command:

```bash
git status
```

- You should see that the readme file is staged and that you have one staged file (in green)

16. Commit the readme file to the repository using the following command:

```bash
git commit -m "Update README.md"
```

17. Check the status of the repository using the following command:

```bash
git status
```

- You should see that the readme file is committed and that you have one committed file (in green)

18. Check the log of the repository using the following command:

```bash
git log
```

- You should see the history of the repository

19. Push the changes to the remote repository using the following command:

```bash
git push <remote-name> <branch-name>
```

20. Check the status of the repository using the following command:

```bash
git status
```

- You should see that the readme file is up to date and that you have nothing to commit

Note: a few numbers are missing, but you can still follow the tutorial

### Now that you know the basic commands, we'll go through some more advanced commands

24. Add some changes to the readme file and save them

25. Check the status of the repository using the following command:

```bash
git status
```

26. Add the readme file to the staging area using the following command:

```bash
git add README.md
```

27. Check the status of the repository using the following command:

```bash
git status
```

28. Now that you have some changes in the staging area, and for some reason you want to undo the changes, you can use the following command:

```bash
git restore --staged README.md
```

- This command will undo the changes in the staging area
- You can see the same command in the git status output

29. Check the status of the repository using the following command:

```bash
git status
```

30. Now for example, you committed some changes and you want to undo the commit, you can use the following command:

```bash
git reset --soft HEAD~1 # --soft means that the changes will be in the staging area
```

or 

```bash
git reset --soft <commit-hash> 
```

- The difference between the two commands is that the first one will undo the last commit, and the second one will undo the commit with the specified commit hash
- `reset --soft` means that the changes will be in the staging area

- There are different types of reset, like `reset --mixed` and `reset --hard`, that you can read about [here](https://git-scm.com/docs/git-reset)

31. Check the status of the repository using the following command:

```bash
git status
```

- You should see that the changes are in the staging area and that you have one staged file (in green)

32. You can also change the commit message of the last commit using the following command:

```bash
git commit --amend -m "new Update README.md"
```

33. Check the log of the repository using the following command:

```bash
git log
```

- You should see the history of the repository

34. Push the changes to the remote repository using the following command:

```bash
git push <remote-name> <branch-name>
```

35. Check the status of the repository using the following command:

```bash
git status
```

- You should see that the readme file is up to date and that you have nothing to commit

36. Now we'll see how to compare the changes between two commits

```bash
git diff <commit-hash> <commit-hash>
```

- You can only compare two commits at a time
- You can also compare the changes between the working directory and the staging area of a a specific file using the following command:

```bash
git diff --staged <file-name>
```

# Git Branches
### Now we'll see how to create a new branch

- Branches are used to develop features isolated from each other
- The master branch is the default branch when you create a repository
- Generally, on real projects, you should never work on the master branch, and you should always create a new branch for each feature you want to develop
- Master branch is used to deploy the application to production

37. List down all the branches using the following command:

```bash
git branch
```

- You should see that you are on the main branch

38. Create a new branch using the following command:

```bash
git branch <branch-name>
```

39. List down all the branches using the following command:

```bash
git branch
```

- You should see that you are on the main branch and that you have a new branch

40. Switch to the new branch using the following command:

```bash
git checkout <branch-name>
```

or 

you can merge two commands into one using the following command:

```bash
git checkout -b <branch-name>
```

- This command will create a new branch and switch to it at the same time

41. List down all the branches using the following command:

```bash
git branch
```

- You should see that you are on the new branch

42. Add some changes to the readme file and save them

43. Check the status of the repository using the following command:

```bash
git status
```

44. Add the readme file to the staging area and commit the changes using the following commands:

```bash
git add README.md
git commit -m "put some changes in the readme file"
```

45. Check the status of the repository using the following command:

```bash
git status
```

46. Switch to the main branch using the following command:

```bash
git checkout main
```

47. List down all the branches using the following command:

```bash
git branch
```

- You should see that you are on the main branch

48. Check the readme file and you will see that the changes are not there

49. Switch to the new branch using the following command:

```bash
git checkout <branch-name>
```

50. List down all the branches using the following command:

```bash
git branch
```

- You should see that you are on the new branch

51. Check the readme file and you will see that the changes are there

52. Push the changes to the remote repository using the following command:

```bash
git push <remote-name> <branch-name>
```

- This command will push the changes to the remote repository, but it will not merge the changes to the main branch
- It will only create a new branch in the remote repository with the same name as the local branch

#### Now we'll see how to merge the changes from the new branch to the main branch

53. Switch to the main branch using the following command:

```bash
git checkout main
```

54. List down all the branches using the following command:

```bash
git branch
```

- You should see that you are on the main branch

55. Merge the changes from the new branch to the main branch using the following command:

```bash
git merge <branch-name> # this branch should be the branch that you want to merge to the main branch
```

- By default, git will use the fast-forward merge, which means that it will move the main branch to the last commit of the new branch without creating a new commit
- Other types of merge are the no-ff merge and the squash merge, and you can read more about them [here](https://git-scm.com/docs/git-merge)
- If you want to create a new commit, you can use the following command:

```bash
git merge --no-ff <branch-name> # --no-ff means no fast-forward
```

- This command will create a new commit that will contain the changes from the new branch


56. Check the readme file and you will see that the changes are there

57. Push the changes to the remote repository using the following command:

```bash
git push <remote-name> <branch-name>
```

- Don't forget to put the correct branch name

#### Now we'll see how to delete a branch

58. List down all the branches using the following command:

```bash
git branch
```

- You should see that you are on the main branch and that you have a new branch

59. Delete the new branch using the following command:

```bash
git branch -d <branch-name>
```

60. List down all the branches using the following command:

```bash 
git branch
```

- You should see that you are on the main branch and that you don't have that branch anymore

NOTE: If you want to update the remote repository with the deleted branch, you can use the following command:

```bash
git push <remote-name> --delete <branch-name> # enter the name of the branch that you want to delete
```


### Merge conflicts

- Merge conflicts happen when you try to merge two branches that have different changes in the same line of the same file
- You can read more about merge conflicts [here](https://www.atlassian.com/git/tutorials/using-branches/merge-conflicts)

61. Create a new branch using the following command:

```bash
git checkout -b <branch-name>
```

62. Add some changes to the readme file and save them

63. Check the status of the repository using the following command:

```bash
git status
```

64. Add the readme file to the staging area and commit the changes using the following commands:

```bash
git add README.md
git commit -m "put some changes in the readme file"
```

65. Switch to the main branch using the following command:

```bash 
git checkout main
```

66. Add some changes to the readme file and save them

67. Check the status of the repository using the following command:

```bash
git status
```

68. Add the readme file to the staging area and commit the changes using the following commands:

```bash
git add README.md
git commit -m "put some changes in the readme file"
```

69. Switch to the new branch using the following command:

```bash
git checkout <branch-name>
```

70. Check the readme file and you will see that the both branches have different changes

71. Checkout the main branch using the following command:

```bash
git checkout main
```

74. Merge the changes from the new branch to the main branch using the following command:

```bash
git merge <branch-name>
```

- You will get a merge conflict

75. Check the readme file and you will see that the changes are not there

76. Check the status of the repository using the following command:

```bash
git status
```

- You will see that you have a merge conflict

77. Open the readme file and you will see that you have a merge conflict 

78. How to solve a merge conflict:

- You can solve a merge conflict by editing the file and removing the conflict markers ex. 
    
```bash
<<<<<< HEAD
main branch changes 123 
=======
new branch changes one 23
>>>>>> <branch-name>
```

- Remove the conflict markers and keep the changes that you want to keep
- It should look like this (if you kept the changes from the new branch):

```bash
new branch changes one 23
```


79. Add the readme file to the staging area and commit the changes using the following commands:

```bash
git add README.md
git commit -m "put some changes in the readme file"
```

80. Push the changes to the remote repository using the following command:

```bash
git push <remote-name> <branch-name>
```

- Don't forget to update the branch name

### Git pull

- Git pull is a combination of git fetch and git merge
- Suppose that you have a local repository and a remote repository, and you made some changes to the remote repository, so if you want to get the changes from the remote repository to the local repository

81. Use the following command:

```bash
git pull <remote-name> <branch-name>
```

- This command will fetch the changes from the remote repository and merge them to the local repository

#### Now we'll see git fetch and git merge

82. Create a new branch using the following command:

```bash
git branch <branch-name>
```

83. Check the list of branches:

```bash
git branch
```

- You should see that you have a new branch but you are still on the main branch

84. Add some changes to the readme file and save them

85. Add the readme file to the staging area and commit the changes using the following commands:

```bash
git add README.md
git commit -m "put some changes in the readme file"
```

86. Push the changes to the remote repository using the following command:

```bash
git push <remote-name> <branch-name>
```

- Check on the github website and you will see that the changes are there

87. Now switch to the new branch that you just created before:

```bash
git checkout <branch-name>
```

88. Run the following command to fetch the changes from the remote repository:

```bash
git fetch <remote-name> <branch-name>
```

example: `git fetch origin main`

- This command will fetch the changes from the remote repository but it won't merge them to the local repository (you can check the readme file and you will see that the changes are not there)

89. You can review the changes that you fetched from the remote repository using the following command:

```bash
git checkout <remote-name>/<branch-name>
```

example: `git checkout origin/main`

- This command will create a new branch that is a copy of the remote branch and you can review the changes that you fetched from the remote repository
- Note that you are on the detached HEAD state

90. If you are ok with the changes that you fetched from the remote repository, you can merge them to the local repository but before that switch back to the new branch that you created before:

```bash
git checkout <branch-name>
git merge <remote-name>/<branch-name>
```

example: `git merge origin/main`

- This command will merge the changes to the local active branch
- You can check the readme file and you will see that the changes are there

Note: a few numbers are missing, but you can still follow the tutorial

## !!! ALWAYS REMEMBER TO 'PULL' CHANGES BEFORE YOU 'PUSH' CHANGES !!!

### Git pull request

- A pull request is a way to tell others about changes you've pushed to a branch in a repository on GitHub

103. Fork the repository that you want to contribute to (you can fork it from the GitHub website)

104. Clone the forked repository using the following command:

```bash
git clone <repository-url>
```

105. Create a new branch using the following command:

```bash
git checkout -b <branch-name>
```

106. Add some changes to some file and save them

107. Check the status of the repository using the following command:

```bash
git status
```

108. Add the file to the staging area and commit the changes using the following commands:

```bash
git add <file-name>
git commit -m "put some changes in the readme file"
```

109. Push the changes to the remote repository using the following command:

```bash
git push <remote-name> <branch-name>
```

- This command will push the changes to the forked repository, not to the original repository that you forked from

110. Go to the forked repository on the GitHub website and you will see that you have a new branch

111. Click on the 'Compare & pull request' button or 'Contribute' button

112. Add a title and a description and click on the 'Create pull request' button

113. Check the status of the pull request and you will see that it's waiting for approval

114. Go to the original repository on the GitHub website and you will see that you have a new pull request

Note: Only the owner of the original repository can merge the pull request

115. Click on the 'Merge pull request' button

116. Click on the 'Confirm merge' button

117. Check the status of the pull request and you will see that it's merged

118. Go to the forked repository on the GitHub website and you will see that the changes are there

119. If you want, you can delete the branch that you created before

### Git stash

- Suppose that you have some changes that you don't want to commit, but you want to switch to another branch
- You can use the stash command to save the changes and apply them later

120. Create a new branch using the following command:

```bash
git checkout -b stash_test
```

121. Add some changes to the readme file and save them

122. Add the readme file to the staging area and commit the changes using the following commands:

```bash
git add README.md
git commit -m "put some changes in the readme file"
```

123. Switch to the main branch using the following command:

```bash
git checkout <branch-name>
```

124. Add some changes to the readme file and save them

125. Try to switch to the `stash_test` branch:

- You will get an error

```bash
error: Your local changes to the following files would be overwritten by checkout:
        README.md
Please commit your changes or stash them before you switch branches.
Aborting
```

126. Use the following command to stash the changes:

```bash
git stash save "<some stash name>"
```

127. Now you can switch to the new branch:

```bash
git checkout <branch-name>
```

128. Switch back to the main branch:

```bash
git checkout main
```

129. Use the following command to list down all the stashes:

```bash
git stash list
```

130. Use the following command to apply the changes:

```bash
git stash apply <stash-name>
```
or

- You can pop the changes using the following command:

```bash
git stash pop <stash-name>
```

- The difference between the two commands is that the first one will apply the changes and keep the stash, and the second one will apply the changes and delete the stash

131. Delete the stash using the following command:

```bash
git stash drop <stash-name>
```

### Advance git commands

- Git rebase
    - Used for changing the base commit of a branch
- Git cherry-pick
    - Used for picking a commit from a branch and applying it to another branch
- Git tag
    - Used for marking a specific commit with a tag


### Small Git quiz

1. You and your team are working on a project using Git. One of your team members has made some changes to a file, but they're not sure if they want to keep them or not. What Git command can they use to see the changes they've made and decide whether to keep them?

- Answer: `git diff`

2. You've been working on a project using Git, and you accidentally deleted a file that was important. What command can you use to restore the file to the state it was in before it was deleted?

- Answer: `git checkout -- <file-name>`

3. You've been working on a feature branch in Git, and you're ready to merge your changes back into the main branch. What command should you use to create a new merge commit that incorporates your changes?

- Answer: `git merge <branch-name>`, from the branch you want to merge into (ex. `git merge feature` from the main branch)

4. You've been working on a project using Git, and you've made some changes to a file. You want to commit those changes, but you don't want to commit all the changes you've made. What command can you use to add only the changes you want to commit?

- Answer: `git add <file-name>`

5. You're working on a project using Git, and you want to see a list of all the commits that have been made to the repository. What command can you use to see this list?

- Answer: `git log`

6. Your team is working on a project using Git, and you want to make sure that everyone is using the latest version of the code. What command can you use to update your local repository with the latest changes from the remote repository?

- Answer: `git pull <remote-name> <branch-name>`

7. Your team is working on a project using Git, and you want to create a new branch to work on a new feature. What command can you use to create a new branch?

- Answer: `git checkout -b <branch-name>`

### Some online resources

- Github | [Git cheat sheet](https://education.github.com/git-cheat-sheet-education.pdf)
- Atlassian | [Git cheat sheet](https://www.atlassian.com/git/tutorials/atlassian-git-cheatsheet)
- Udacity course | [Version Control with Git](https://www.udacity.com/course/version-control-with-git--ud123)
- Atlassian | Coursera course: [Version Control with Git](https://www.coursera.org/learn/version-control-with-git#syllabus)
- Free Code Camp | [Git and GitHub for Beginners - Crash Course](https://youtu.be/RGOj5yH7evk)
- IBM edx course: [Introduction to git and github](https://www.edx.org/course/introduction-to-git-and-github)

## Small projects for practice

**1. Project title: Calculator Application with Git and Version Control**

Description: Create a calculator application using Python and use Git and GitHub for version control

No. of students: 3

Time: 2 hours

Start with

- Only one student should fork this repository: [fc-ss23-git](https://github.com/kvnptl/fc-ss23-git)
- Add the other 2 students as collaborators to the repository (On GitHub, go to Settings > Collaborators > Add people)
- Everyone should clone the forked repository
- Each student should create a new branch for his/her task
- Work on the `calculator_application.py` file

Tasks:
- Create first commit for your task description only
- Develop a separate function for each functionality
- The code should take user input(if applicable) and display the result
- After completing the task, create a pull request to the `fc-ss23-git` repository's `main` branch


Student 1
- Arithmetic operations (addition, subtraction, multiplication, division)
- Trigonometric operations (sin, cos, tan)

Student 2
- Logarithmic operations (log, ln)
- Exponential operations (exp, sqrt)
- Degree to radian conversion, radian to degree conversion

Student 3
- Area of a circle, area of a triangle, area of a rectangle
- Volume of a sphere, volume of a cylinder, volume of a cone
- Find pythagorean triplets

**2. Project title: IRIS data plotting with Git and Version Control**

Download dataset: [Iris dataset](https://archive.ics.uci.edu/ml/datasets/iris)

Description: Create a data plotting application using Python and use Git and GitHub for version control

No. of students: 3

Time: 2 hours

Start with:

- Only one student should fork this repository: [fc-ss23-git](https://github.com/kvnptl/fc-ss23-git)
- Add the other 2 students as collaborators to the repository (On GitHub, go to Settings > Collaborators > Add people)
- Everyone should clone the forked repository
- Each student should create a new branch for his/her task
- Work on the `iris_data_plotting.py` file

Tasks:

- Create first commit for your task description only
- Develop a separate function for each functionality
- The code should take user input(if applicable) and display the result
- After completing the task, create a pull request to the `fc-ss23-git` repository's `main` branch

Student 1
- Plot the data using a scatter plot
- Plot the data using a line plot
- Find the mean, median, mode, standard deviation, variance, and range of the data

Student 2
- Plot the data using a bar plot
- Plot the data using a histogram

Student 3
- Plot the data using a box plot
- Plot the data using a violin plot


**3. Project title: Basic image processing application with Git and Version Control**

Requirements:
- Python
- OpenCV
- Numpy

Description: Create a basic image processing application using Python and use Git and GitHub for version control

Resources: find sample images [here](https://github.com/kvnptl/fc-ss23-git/tree/main/basic_image_processing/images)

No. of students: 3 (group 1)

No. of students: 3 (group 2)

Time: 2 hours

Start with:

- Only one student should fork this repository: [fc-ss23-git](https://github.com/kvnptl/fc-ss23-git)
- Add the other 2 students as collaborators to the repository (On GitHub, go to Settings > Collaborators > Add people)
- Everyone should clone the forked repository
- Each student should create a new branch for his/her task
- Work on the `basic_image_processing_application.py` file

Tasks:

- Create first commit for your task description only
- Develop a separate function for each functionality
- The code should take user input(if applicable) and display the result
- After completing the task, create a pull request to the `fc-ss23-git` repository's `main` branch

Student 1
- Read an image
- Display the image
- Save the image
- Convert the image to grayscale
- Convert the image to binary
- Convert the image to HSV

Student 2

- Read an image
- Display the image
- Save the image
- Resize the image
- Crop the image
- Rotate the image

Student 3
- Read an image
- Display the image
- Save the image
- Blur the image
- Sharpen the image
- Edge detection


**4. Project title: validating credit card numbers with Git and Version Control**

Description: Create a program to validate credit card numbers using Python and use Git and GitHub for version control

Resources: find the instructions [here](https://github.com/kvnptl/fc-ss23-git/blob/main/validating_credit_card_numbers/instructions/validating_credit_card_numbers.pdf)

No. of students: 2

Time: 2 hours

Start with:

- Only one student should fork this repository: [fc-ss23-git](https://github.com/kvnptl/fc-ss23-git)
- Add the other 2 students as collaborators to the repository (On GitHub, go to Settings > Collaborators > Add people)
- Everyone should clone the forked repository
- Each student should create a new branch for his/her task
- Work on the `validating_credit_card_numbers.py` file

Tasks:

- Create first commit for your task description only
- Develop a separate function for each functionality
- The code should take user input(if applicable) and display the result
- After completing the task, create a pull request to the `fc-ss23-git` repository's `main` branch

Student 1 & 2: divide the check conditions into two parts

**5. Project title: Validating email addresses with Git and Version Control**

Description: Create a program to validate email addresses using Python and use Git and GitHub for version control

Resources: find the instructions [here](https://github.com/kvnptl/fc-ss23-git/blob/main/validating_email_addresses/instructions/validating_email_addresses.pdf)

No. of students: 2

Time: 2 hours

Start with:

- Only one student should fork this repository: [fc-ss23-git](https://github.com/kvnptl/fc-ss23-git)
- Add the other 2 students as collaborators to the repository (On GitHub, go to Settings > Collaborators > Add people)
- Everyone should clone the forked repository
- Each student should create a new branch for his/her task
- Work on the `validating_email_addresses.py` file

Tasks:

- Create first commit for your task description only
- Develop a separate function for each functionality
- The code should take user input(if applicable) and display the result
- After completing the task, create a pull request to the `fc-ss23-git` repository's `main` branch

Student 1 & 2: divide the check conditions into two parts
