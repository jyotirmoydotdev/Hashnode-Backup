# Git for Termux

Holla 🤠 my Friend, let me first introduce myself my name **Jyotirmoy barman ** a tech nerd from the west part of India 🇮🇳 (Meghalaya). In this article, I am going to tell about git and how to install it in termux, as I know many beginners may be using the phone to do some light development or don't have money to buy a laptop.

Do follow me on Twitter to get all the latest updates [@jyotirmoydotdev](https://twitter.com/jyotirmoydotdev)

## Git
As the internet says git is a version control to track the code changes and there is not any second thought. I am not going to explain it in detail, If you want to read more about it you can go to [Wikipedia](https://en.wikipedia.org/wiki/Git).

## Installation
Installation of Termux on a phone is simple, just follow these steps.

### step 1
If you want to install git on your phone then you must install the termux app first. As the termux app updated version is not available in play you must use the third party website to install it.

There are two places from where we can download the latest version of Termux.
>F-droid : [Termux](https://f-droid.org/en/packages/com.termux/)  ✅<br>
>Github : [Termux](https://github.com/termux/termux-app/releases)

### step 2
After you have successfully installed termux on your phone, now you need to run some commands to update the packages and install git.


- First, update the packages, this will update all the packages in Termux
<code>pkg update && pkg upgrade</code><be>

- Run this command to install git in termux<br>
<code>pkg install git</code>

- I also recommend to install <code>gh</code>, it is a command line tool by github.<br>
<code>pkg install gh</code>

Recently Github announced that it will no longer accept account passwords when authenticating Git operations, that's why we need gh (Github command-line tool) to push our code in Github.

> ### What is Github?
> Github is a code hosting platform, owned by Microsoft.<br>
>For more information visit [Github-wikipedia](https://en.wikipedia.org/wiki/GitHub)<br>
>Follow me on Github [@jyotirmoydotdev](https://github.com/jyotirmyodotdev)

## Learn
Till now you must install git and gh in termux, now it's time to learn it. First of all, we need to set up our git and gh to work flawlessly

write the following command to set up.<br>
- <code>gh auth login</code> Login to your Github account.
- After you log in to your Github account, now setup your git
- <code>git config --global user.name "name"</code>
- <code> git config --global user.email "email"</code>
- Now you are all set

### Make Repository
If you want to track a folder you need need to init a folder. I recommended you first go to your Github account and make a repository.
![Screenshot 2022-01-26 at 9.29.30 PM.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1643213018791/RqnaOBIcG.jpeg)

After that clone it in your local environment <code>git clone "repository link"</code>

or 

run this code<br>
<code>gh create repo create</code> and follow the command.

### Push and Pull
After you have written some code in your repository and wish to upload it to your GitHub account then run this command.
- <code>git add .</code> this will add all the code or if you want to upload a single file <br><code>git add "file name"</code><br>
- <code>git commit -m "Message"</code> write what you have done in "Message"
- <code>git push</code> this will upload all the code.

If you have done any change in your repository from Github or any other local machine and push it to your repository, then you can run<br>
- <code>git pull</code> <br>

this will pull all the latest code and keep you up-to-date.

## Command table
Here are the commands and their action for git and gh.

- <code>git --help</code>
- <code>gh --help</code>

| Command  | Action |
| --- | --- |
| git --version | to see what version of git you are using  |
| git clone <repository link> | to clone the repository in the local environment |
| git add . | to add all the files |
| git commit -m “message” | to commit with message |
| git commit -m “title” -m “description” | to commit with message and description |
| git push | to push code to the origine |
| git pull | to pull the code from the online repo. |
| git config --global user.name "name" | to set the name |
| git config --global user.email "email" | to set email |
| git branch --list | to see what branch we have |
| git branch <branch> | to create branch |
| git branch -d <branch> | safe branch delete |
| git branch -D <branch> | Force delete |
| git branch -m <branch> | merge branch |
| git status | To see the changes |
| git switch <existing_branch> | to change existing branch |
| git switch -c <new_branch> | to change to new branch |
| git log | Show commit logs |

| Command | Action |
| --- | --- |
| gh auth login | to login in Github |
| git auth logout | Log out of a GitHub host |
| git auth status | View authentication status |
| Install git  | brew install git |
| Install gh | brew install gh |

## Thanks
Thanks for reading this far, don't forget to follow in [Twitter - @jyotirmoydotdev](https://twitter.com/jyotirmoydotdev) and [Github - @jyotirmoydotdev](https://github.com/jyotirmyodotdev).

I am always open to your suggestion 😄 [jyotirmoydotdev@gmail.com](mailto:jyotirmoydotdev@gmail.com)