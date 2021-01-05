# git_chi_sea_ds

# Task 1: Fork and clone remote repository.  

Why Fork?
> Forking a repo creates a personal copy of the repository for you to do with as you wish. 
You can make changes to files and save the changes on Github via your local fork.  

> You will be forking various repos, for example lecture repos, to follow along with on your computer. 
By forking lectures and activities, you can write code in the jupyter notebooks associated with each lecture, then save these notes on the cloud by pushing to your fork.

> If you simply cloned the lecture repo, you would still be able to save your work locally on your computer, but you would not be able to push to the cloud.
That is because you would be attempting to push changes to the original lecture repo, and the next time Greg went to give that lecture, he would see your notes. He therefore does not give you the necessary permissions to push.

- For the first task, fork this repo: https://github.com/learn-co-students/ds-west-github_activity_011120

- In the upper right portion of the window, you will see a button which reads `Fork`. 
Click on that button, and fork the repo. 
 
- You will be redirected to your copy of the repo, with a url which now has your name inserted:
> https://github.com/<your_github_username>/ds-west-github_activity_011120 

- Copy that url to your clip board.  
- Open a terminal window, and navigate to Documents, or wherever it is that you store your Flatiron material.
    - To do so, type `cd ~/Documents` after the command prompt.
    - The ~ represents the home directory, i.e. the folder associated with your User.
    - All the GUI stuff you are used to - Documents, Desktop, Downloads - are located after the ~/
    - Try typing cd ~, followed by ls.  Make sure you can locate your Downloads, Documents, and Desktop.
    
- Once you have cd'ed into ~/Documents, type `git clone`, and paste the url of your Fork.
    - git clone  https://github.com/<your_github_username>/ds-west-github_activity_011120  
    - You just created a copy of the repository on your computer.
    - run `ls`, and you will now see the folder name: ds-west-github_activity_011120
    - run `cd ds-west-github_activity_011120` to change into the newly created folder.

- Once inside the folder, run the following command: 
    - git remote -v
    - the -v option stands for verbose, and outputs the url associated with your remote.
    - the origin remote should be linked to your fork: https://github.com/<your_github_username>/ds-west-github_activity_011120 
    - Copy the output of git remote -v, and slack the results out to the Slack thread.
   
# Task 2: create a new file and push it to your fork.

To complete this task, you have to be familiar with the essential Github workflow: add/commit/push.

But before you start down the add/commit/push process, you need to have changes that you want to save in Github's memory.

  - create a copy of the my_intro.txt called <your_name_intro>.txt
    - to do so, use the copy command `cp` which takes two arguments: 1: the file to copy 2: the name of the new file
    - in your terminal, type `cp my_intro_text.txt <your_name_intro>.txt
    - type `ls` to confirm you can see the new file. 
  - open that file in an editor and change the content
    - For most of you, you should be able to type `open <your_name_intro>.txt`, and Text Edit will boot up.
    - If that doesn't work, you can type `open .` to open up the finder window, then double click the file.
    - If you are feeling adventurous, type `vim <your_name_intro>.txt`, and try to edit it using VIM.  

Now that you have created a new file, add/commit/push.
  - Type `git status`
    - you should see your new file listed in red.
    - that tells you the file has been changed
  - Type `add <your_name_intro>.txt`
    - doing so stages your change.  
    - Now type `git status`.  You should see your file in green.  Green means your file has been staged, and is ready to commit.
  - Type `commit -m <meaningful_message_here>`
    - the -m option allows you to type in a message which describes what change you are making. These messages should be short and descriptive.  The convention is to use the imperitive tense: Add, change, fix, etc.
    - Add a message like, `commit -m "Add personal intro file"`
Once a commit has been made, you can type `git log`, and you will see the record of the commit, including the message.

Now, push your commit to the fork.
  
    - Type git push
      - by default, git will push to the origin.  Because your personal, forked copy is associated to the origin remote, you can just write git push.
      - You could also be explicit, and write git push origin master
      - Navigate to the Github url of your fork, and make sure you can see your new file
    
# Task 3: Fetch/Merge or Pull new content from the upstream repository.

In order to retrieve new content from Github, you can use `git pull`.
By default, the `git pull` command retrieves content from the `origin` remote.  
Remotes are variables which link your local version of a repository to the cloud, and there can be multiple links.
I will push a new file called 'zen_of_python.txt' to the original repo. 

In order to get the `zen_of_python.txt` onto your computer, you now have to set up a new remote pointing to the original repo.
    - To do so, run the command `git remote add upstream `
    - Notice that the url is the original repo, not your fork.
    - Now, when you type, `git remote -v` you should see two remotes, one pointing to your fork, and one pointing to the original repo.
    
If you successfully added the remote, you can pull the new content:
    - Run the command, `git pull upstream main` 
    - You will see some output

















The Zen of Python, by Tim Peters

Beautiful is better than ugly.
Explicit is better than implicit.
Simple is better than complex.
Complex is better than complicated.
Flat is better than nested.
Sparse is better than dense.
Readability counts.
Special cases aren't special enough to break the rules.
Although practicality beats purity.
Errors should never pass silently.
Unless explicitly silenced.
In the face of ambiguity, refuse the temptation to guess.
There should be one-- and preferably only one --obvious way to do it.
Although that way may not be obvious at first unless you're Dutch.
Now is better than never.
Although never is often better than *right* now.
If the implementation is hard to explain, it's a bad idea.
If the implementation is easy to explain, it may be a good idea.
Namespaces are one honking great idea -- let's do more of those!


