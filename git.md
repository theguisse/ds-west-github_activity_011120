# Intro

Github has a learning curve, but once the curve flattens, your ability to create well organized DS projects will be substantial.  In this code along, we will walk through how we interact with the git API from the command line, as well as connect repos to Github.  If you want, you can try to follow along with me, or you can just watch and ask questions. 

# Part I: 
## Creating a repo and making a first commit.

Load up a terminal window using whatever method you like.  
We will create a new project folder in documents.  

  + cd ~/Documents/  
  + mkdir `ds_example_project` 

Navigate into that directory.  

  + cd `ds_example_project`
  
We can look at the contents of the folder with ls. There is nothing there, as we just created it.
We see it is not a git repo when we run

  +  git status

Next step, we transform the directory into a git directory.

  + git init

Now, when we run git status, we see that it is now a git repo.  However, when we run ls, nothing looks different. 

> Question 1: How we can see what changed?  

Now, let's go about getting used to the basic git workflow. 

Create a file called README.md using the touch command.  

  + touch README.md
  
Let's add one line to it using echo and >

  + echo 'Scifi Book Recommender' > README.md
  
Add one more line using echo and >> 

  + echo 'An app which uses machine learning to recommend lesser known scifi books to scifi enthusiasts'
  
Use cat README.md to make sure the content is there.  Now it's time to add and commit.  Run git status.  README.md will be red.  We generally want to add files one by one.  That will make it so that our commits can be linked to specific file changes.  We could also use git add . or git add -A. See this [stackoverflow](https://stackoverflow.com/questions/572549/difference-between-git-add-a-and-git-add)

  + git add README.md
   fs
Now if we run git status, README.md is green. It has been staged, and is ready to commit.

Now run git commit -m "Message here". The general concensus is to use the imperative, i.e. 'Add README.md', 'Change file', 'Add first simple model' 
  
  + git commit -m "Add README.md"
  
# Part II: 
## Create Project Directory Structure

Now we will pick up the pace a bit, and add some more repo content.

.gitignore is a crucial file.  You can initialize a repo with a Python specific .gitigore [python gitignore](https://github.com/github/gitignore/blob/master/Python.gitignore).  We will just make an empty one, and tell it to ignore all csv files.

  + touch .gitignore
  + echo '*.csv' > .gitignore

Let's add a data folder and put a csv file in it.
  + mkdir data
  + touch data/outcomes.csv
  + echo '1,2,3,4' > outcomes.csv

Make sure the outcomes.csv file has the data in it.
Now, create an empty python file.

  + touch model.py
  
Run git status.  Notice what is there and what is not. Add each file and commit.

# Part III: 
## Work through a branch workflow

Branches allow effective collaboration with teammates.  You can work on a section of the code without affecting code that other people rely on.  Deployable code should live on the master branch.  Run git branch, and you should see only the master branch.  

Let's create a branch called logistic, which we will use to work on a simple classification model.  

  + git checkout -b logistic
  
No, create a new file called logistic.py 

  + touch logistic.py
  
Add and commit logistic.py. 

Now run 
  
  + git checkout master
  
then run 

  + ls
  
The logistic.py file is gone.  If you checkout the logistic branch, it reappears. 

Imagine you finished working on your logist c model, and want to itegrate it into the master branch.  Make sure you are on the master branch. Then merge:
  
  + git merge logistic
  
Use ls to confirm logistic.py shows up.  
Now, no new code lives on the logistic branch, so you delete it.

  + git branch -d logistic
  
# Part III:
## Staging, unstaging, and checking out old commits

Imagine you have a giant csv file that you accidentally staged.  We will use tsv, because we already have ignored csv.

  + touch data/giant.tsv
  + git add -A

You realize that committing a giant file will cause problems when pusing to Github, so you want to undo it. Git reset unstages all staged files.

  + git reset
  
Now run git status, and see that giant.tsv has been unstaged.

But say you added giant.tsv and committed it.
  + git add data/giant.tsv
  + git commit -m "Add giant.tsv"

Now reset won't do anything.  You can, however, revert to a previous commit. If we run git log, you will see a commit history.  Each commit has a unique identifier called a SHA. Run:

  + git log
  
Copy the first 6 or so characters of the sha of a commit before the most recent, where giant.tsv wasn't commited yet. Then run

  + git checkout <SHA>
  
You are now in a detached head state.  You can look at the repo's state back in time.  If the repo looks accebtable, i.e., you won't loose work by reverting (which is permanent), then you can use git reset -hard.
First, checkout master.  Then run 

  + git reset -hard <sha>
  
Your repo should be back as it was before the commit.

# Part IV
## Github

So far, we have been working locally, but the power of git is in the cloud.  
Assuming you have a Git account, navigate to github.com/your_username.

Create an empty reposistory named `sci_fi_book_recommender`
Initiate it without a README.md or .gitignore.

If we wanted to start from scratch, we could copy the url, navigate to Documents, and run

  + git clone sci_fi_book_recommender
  
A directory appears of the same name.  cd into it. Then run

  + git remote -v
  
You will see origin has the url of the remote repo.  Add a  README.md file, commit the file, then run 
  
  + git push origin master
  
Navigate to the repo at github.com, and see that the file is there.

Now, on github.com, manually change the README file and commit.  The cloud version of the repo is different from the local. You want your local to be current with the cloud. Go back to your terminal, navigate to the project repo, then run:

  + git fetch origin master

This brings the changes down to your computer, but you won't be able to see them yet. To do so, run 
  
  + git merge origin/master
  
Now the changes show up.  You could accomplish the same thing with the command git pull, which runs a git fetch followed by a git merge, but it's safer to run the commands separately. 
The other way to establish a connection with the cloud is to add a remote to an existing repo.  Navigate to the directory we worked on earlier.  If you run git remote -v, you won't see any remotes. Copy the address of the remote repository, then run:

  + git remote add origin <remote_url>
  
Now run git remote -v and you will see the origin remote url.

You can add many remotes.  A common use is to fork a repository, then set one remote (the origin) to the copy related to your personal account, and one remote (the upstream) to the original account. You can then fetch and merge from the upstream to update your local system with newly pushed material. You can then alter files, create new files, and push to the forked branch. 






Question Answers:  
Question 1: If we use ls -a, we will see the .git folder.
