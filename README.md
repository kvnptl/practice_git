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
- Git rebase
- Git stash
- Git diff
- Git remote
- Git clone
- Git fetch


### Requirements and commands to install:

1. Create an account on [GitHub](github.com)
- Use your personal email address and then link your university email address to your GitHub account

2. Create a new repository on GitHub

3. Install Git on your computer (if you don't have it already) using the following command:

```bash
sudo apt install git
```

### Basic git workflow:

4. Configure Git on your computer using the following commands:

```bash
git config --global user.name "Your Name"
git config --global user.email "dontcopythis@whatever.com"
```

5. Create a new directory on your computer and clone the repository you created on GitHub using the following command:

```bash
git clone <repo-link>
cd <repo-name>
ls -a
```

6. Create a readme file and add some text to it using the following command:

```bash
touch README.md # md stands for markdown
gedit README.md # or use your favorite text editor (e.g. vim, nano, etc.)
```

7. Check the status of the repository using the following command:

```bash
git status
``` 

- You should see that the readme file is untracked and that you have one untracked file

8. Add the readme file to the staging area using the following command:

```bash
git add README.md
```

9. Check the status of the repository using the following command:

```bash
git status
```

- You should see that the readme file is staged and that you have one staged file (in green)

10. Commit the readme file to the repository using the following command:

```bash
git commit -m "Add README.md" # -m stands for message
```

11. Check the status of the repository using the following command:

```bash
git status
```

- You should see that the readme file is committed and that you have one committed file (in green)

12. Check the log of the repository using the following command:

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

13. Push the changes to the remote repository using the following command:

```bash
git push <remote-name> <branch-name>
```

- How to get the remote name and branch name on terminal:

```bash
git remote -v # -v stands for verbose
git branch
```

14. Check the status of the repository using the following command:

```bash
git status
```

- You should see that the readme file is up to date and that you have nothing to commit

15. Make some changes to the readme file and save them

16. Check the status of the repository using the following command:

```bash
git status
```

- You should see that the readme file is modified and that you have one modified file

17. Add the readme file to the staging area using the following command:

```bash
git add README.md
```

18. Check the status of the repository using the following command:

```bash
git status
```

- You should see that the readme file is staged and that you have one staged file (in green)

19. Commit the readme file to the repository using the following command:

```bash
git commit -m "Update README.md"
```

20. Check the status of the repository using the following command:

```bash
git status
```

- You should see that the readme file is committed and that you have one committed file (in green)

21. Check the log of the repository using the following command:

```bash
git log
```

- You should see the history of the repository

22. Push the changes to the remote repository using the following command:

```bash
git push <remote-name> <branch-name>
```

23. Check the status of the repository using the following command:

```bash
git status
```

- You should see that the readme file is up to date and that you have nothing to commit

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
- You can see the command on your terminal when check the status of the repository

- You can also use the following command (optional):

```bash
git reset HEAD README.md
```

- The difference between the two commands is that `git restore` is a newer command and it's more intuitive

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

- There are different types of reset, and you can read more about them [here](https://git-scm.com/docs/git-reset)

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

#### Note: you created a new branch and you made some changes to the readme file, but you didn't push the changes to the remote repository, so if you switch to the main branch, you will see that the readme file is not updated

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

- Don't forget to update the branch name

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

- You should see that you are on the main branch and that you don't have a new branch

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

70. Add some changes to the readme file and save them

71. Check the status of the repository using the following command:

```bash
git status
```

72. Add the readme file to the staging area and commit the changes using the following commands:

```bash
git add README.md
git commit -m "put some changes in the readme file"
```

73. Switch to the main branch using the following command:

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
put some changes in the readme file
=======
put some changes in the readme file
>>>>>> <branch-name>
```

- Remove the conflict markers and keep the changes that you want to keep

79. Add the readme file to the staging area and commit the changes using the following commands:

```bash
git add README.md
git commit -m "put some changes in the readme file"
```

80. Push the changes to the remote repository using the following command:

```bash
git push <remote-name> <branch-name>
```

















