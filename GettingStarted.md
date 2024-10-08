# Getting Started Guide

## Introduction

There is a lot of material covered at the beginning of this course that may seem unfamiliar, or scary. In the sage words of Douglas Adams, **Don't panic.**

<img src="https://octodex.github.com/images/femalecodertocat.png" width="25%" />

The aim of this course is to introduce you to industry-standard tools and practices, so that you will be prepared to deliver professional-grade work to colleagues. 
Much like reading and writing, computer literacy is becoming indispensible. 
Easily solved problems are largely solved already. 
The challenging problems that still remain are often too complex for traditional analytical methods to make substantial progress. 
Computational methods help augment other problem-solving methods and increase their effective scope; as a result, they have become increasingly necessary for progress. 
The rise in popularity of "Data Science" and "Big Data" is a symptom of this trend: Computational power enables novel problem solutions.

Being familiar with modern computational tools and techniques will give you an edge in the job market, and make transitioning out of college to the next chapter of your life more smooth. The material of the course may seem daunting---perhaps even overwhelming---at first, but rest assured that practice makes perfect. What is initially unfamiliar and strange will become second nature by the end of the course, and you will have gained a powerful set of new skills that can continue to evolve with the rapid pace of technology. Be patient with yourself, for polishing these new skills will only help you to be a valuable and competitive colleague in the future.

## Account Setup

Our class will be centered around a cloud-based piece of technology: 
 1. [GitHub](https://github.com), a central hub for sharing code that has become standard in the open-source community. 

 - **Task 1:** Use your Chapman email to create a GitHub account, if you don't already have one linked to your Chapman email. Use your full, real name when making the accounts so that you can be easily found. The instructor should have invited you to the course GitHub Organization using your student email, so look for the invite emails to accelerate account creation.
 
Our class will also teach you how to use your own personal computer as a scientific workstation. To do this, you will need to set up two more pieces of software on your personal computer:
 1. [Anaconda Python](https://www.anaconda.com/distribution/), a distribution of python together with a useful collection of scientific and data-processing packages.
 1. [Git](https://git-scm.com/download), a distributed change control for managing code and sharing it with other programmers.

 - **Task 2:** Go to the Anaconda site linked above and download the Anaconda distribution for Python 3 (i.e., **not** Python 2). Make sure you choose the correct operating system (Windows, Mac, or Linux). Launch the installation and follow the instructions. (When it asks questions, pick the recommended options.)
 - **Task 3:** Go to the Git site linked above and download the Git installer (for Windows or Mac - it's likely already installed if you are using Linux). Run the installation and follow the instructions. If it asks, be sure to enable git integration with your file browser.
 
## Setting up the Terminal (a.k.a. Bash Shell) and SSH

After you have the software installed, we need to connect your computer to GitHub via **s**ecure **sh**ell keys (ssh keys). To do this, first open a **Terminal**. On a Mac you can find the bash terminal under Applications/Utilities/Terminal. In Linux you have your choice of terminal applications running bash. In Windows, a bash terminal is included with Git for Windows - you can open it from the Start menu under Git/Git Bash or from Windows Explorer by right clicking inside a folder and selecting "Git Bash Here". Remember how you open a Terminal, because you will be using it frequently in this course.

On Git for Windows, it should look something like this:

```
username@COMPUTER MINGW64 ~
 
$  
```
On Mac or Linux it more likely looks like this:
```
username@COMPUTER ~$
```
As a quick orientation, the `~` symbol means "home directory" and indicates where you currently are in the file system. The `$` symbol is the "bash prompt" and indicates that you are able to type a command to run, then hit enter to run it. Be sure to browse the many resources for learning the bash shell that are listed in the README of this `info` repository. For a quick introduction, see also the [Linux/Bash Overview Slides](http://slides.com/profdressel/linux-bash-overview). Chapter 1 of your textbook covers the essentials of using the bash shell as well.

### Creating SSH Keys

To connect to GitHub, we first need to create `ssh` keys for your computer. You can think of these like keys to a house that allow people to access it. Instead, they are keys for your computer that allow people to remotely log into it using the **s**ecure **sh**ell (or ssh) protocol. There are two kinds of ssh key: public and private. A "public" key acts like a lock that you give to someone else, while its corresponding "private" key acts as a physical key used to unlock the lock. For example, if a computer knows your public key, then you can use your private key to access that computer. 

To create new `ssh` keys, type the command `ssh-keygen -t rsa` into the terminal, and hit `Enter` four times. It should look similar to what is below. (Note, the *prompt* characters `~$` simply let you know that you may type a command, and that you are in your `~` directory, known as "home" and equivalent to `/home/user`.)
```
 ~$ ssh-keygen -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (/home/user/.ssh/id_rsa):
Created directory '/home/user/.ssh'.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/user/.ssh/id_rsa.
Your public key has been saved in /home/user/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:9f4vJzDrftWXdG8Jo60UsqEd0yDd4mq3orslN9Ju/UQ user@project-1c8479d1-dc82-4b59-be53-b8f4bfb0b917
The key's randomart image is:
+---[RSA 2048]----+
|        . .      |
|       . + .     |
|        o =      |
|         B + o ..|
|        S *E= + *|
|      .+ +.+o. o*|
|     o.=o o.o+ o.|
|      *o.o....+ .|
|     +=.. .+o..=.|
+----[SHA256]-----+
~$
```
This command has generated keys in the directory `~/.ssh/` (which is normally "hidden" from view since it starts with a `.`). 

### Adding your public SSH key to GitHub

You can now add to your newly generated "public key" to your GitHub account so that it knows who you are when you try to connect. To do this, run the command `cat ~/.ssh/id_rsa.pub` in the terminal (which con**cat**enates the contents of the file and prints it to the screen), which will produce something like the following:
```
~$ cat ~/.ssh/id_rsa.pub
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDiZS980QbZ1T+GYJky8QbKDngbH9UxPNKOencPT8rtk6PgBuk7DQrNladts32isd49LpHDgbFJhV/UqY9JvTn9xPXEaGRcgJurbbuE6YKWmKQ5Xl6rl3nLrK+zv4/VL+v4p0wRit/JFbjqSHBE
ni/TcO6dty3EaXH3o8eU/FCk+8kimoQqTnj/P8U/EHDySP0RvAC1k9LxrwKY22Az0J9kiZW7Mb6QJIZqu2mlVSpXQKcpiTEBUfOyWj9WyMiCPhtD0j/500CCAwwlQ2gNH8b3UGZpvxzlkT+wurvKknNGFKej/APpk/ehxbNzrni1oBFzCq/PVItq
gaJMG9B6HgvH user@project-1c8479d1-dc82-4b59-be53-b8f4bfb0b917
~$
```
The string beginning with `ssh-rsa` and ending with (in this case) `917` is your "public RSA key". Highlight this string with the mouse and copy it (with the right-click menu). Go into your GitHub Account Settings (upper right corner menu on GitHub), then go to the settings tab "SSH and GPG Keys". Click on the button "New SSH Key" in the upper right, and paste your RSA key into the field labeled "Key". In the field labeled "Title", give your key a descriptive name so you know which key it is, for example, "PHYS220 Key". Then click the confirmation button "Add SSH Key".

To confirm that your public key is installed correctly, go back to your Terminal and type the command `ssh git@github.com`. This tries to log into GitHub using your private key via secure shell (ssh), assuming the account name `git` at the address `github.com`. You should see something like the following:
```
~$ ssh git@github.com
PTY allocation request failed on channel 0
Hi YOUR_GITHUB_USERNAME_HERE! You've successfully authenticated, but GitHub does not provide shell access.
Connection to github.com closed.
~$
```
The important statement to find here is `You've successfully authenticated`. This means that GitHub understands your key properly, and you can communicate between your computer and the GitHub server via `ssh`.  If you refresh your "SSH and GPG Keys" settings page in GitHub, you will now see your key has a green light next to it to indicate that the connection has been successfully confirmed.

## Cloning the Information Repository

As a check for the connection to GitHub and a demonstration that it works, using the Linux Terminal let's **m**a**k**e a new **dir**ectory to store `git` repositories using `mkdir`.
```
 ~$ mkdir ~/PHYS323/
 ~$
```
Now **c**hange into that **d**irectory using `cd` and **l**i**s**t its contents with `ls`.
```
 ~$ cd PHYS323
 ~/PHYS323$ ls
 ~/PHYS323$
```
Since the directory is initially empty, nothing interesting should be listed, so the prompt returns immediately.

Go to your GitHub account in a different tab/window and find the information repository main page. In the upper right corner, you should see a green "Clone or Download" button. Click the button and it will open up a sub-panel with a clone link. There are two possible links, HTTPS or SSH. Make sure you choose SSH. Click on the copy button to copy the repository clone link to your clipboard.

Return to your terminal and use `git clone` to clone the information repository to your directory "PHYS323". It should look something like:
```
 ~/PHYS323$ git clone git@github.com:chapman-phys323-2024f/info.git
Cloning into 'info'...
remote: Counting objects: 20, done.
remote: Compressing objects: 100% (19/19), done.
remote: Total 20 (delta 6), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (20/20), 131.57 KiB | 0 bytes/s, done.
Resolving deltas: 100% (6/6), done.
Checking connectivity... done.
~/PHYS323$ ls
info
~/PHYS323$
``` 
Now the list command `ls` shows that there is a new directory `info` that has been cloned from GitHub. You can confirm that it exists outside the terminal by going to your usual File Manager and browsing around. The cloned files are now local inside your computer and can be viewed (or edited) directly.

The above procedure will be how you clone all classwork and homework repositories for the class. For more information about how GitHub works, see the [Git and GitHub Overview Slides](http://slides.com/profdressel/git-overview). Chapters 15 and 16 of your textbook also give a detailed overview of how to use both `git` and GitHub productively.

