# Prerequisites

The workshop lasts 50 minutes, which is very little to understand the basics of Git and GitHub and how to use them for WordPress theme development.
There won't be time to help you with setup and preparation: you should show up ready to start.

Also, be aware that you will need to register to join the workshop.
The WordCamp Europe Content Team and the volunteers will check that you have prerequisites in place before they give you the special ticket to get to the workshop.

If that scares you a little, don't worry: here is a detailed list of all the things you must prepare in advance: be sure to check through it, and you'll have no problem.

## Computer and software

It might seem obvious, but you should bring your computer for this hands-on workshop.
Not only that, but you should also have a few programs installed on it.

### Git

The main piece of software is, of course, Git.
If you don't already have it on your computer, you have to install it; if you already have it, it's better to update it (possibly to the latest version, but at least to version 2.35.2, which addresses a security issue).

Depending on your operating system, you can:
- install it as a package (the go-to solution if you use Linux or Unix, and a good option if you use macOS);
- use an installer (another possibility for macOS users and the best one for Windows users);
- download the source code and compile it yourself (not the best choice unless you're familiar with it).

The Git downloads page describes all these options in detail: it automatically detects your operating system, so it'll guide you in your choice.
Follow the setup steps, and you'll have Git installed on your system.
If, during the installation, you don't understand all available options, don't worry: you can change all settings at a later time (or, at worst, repeat the install).

To check that Git is ready for use, open the terminal (if you're new to it, you can find more information below in the section about getting started with the [command line](/Prerequisites.md#command-line)) and type the following command.
```
git version
```
The terminal output should be something like `git version 2.36.1`: if so, Git is now available on your computer.

### (Local) testing environment

Since you'll be editing WordPress themes during the workshop, you need a testing environment to check your changes.
You can use an online staging website or a local development environment: my suggestion is to go for the latter option and, in case you don't have one yet, take this workshop as an opportunity to get started.
In any case, don't use a live website!

If you already have a local development environment you're familiar with, go for it, and don't worry.
If you don't, the easiest option is probably to use Local: it's a free tool that allows you to set up a development WordPress site on your computer in minutes.
You can download it from the [Local website](https://localwp.com/).
Just follow the instructions, and you're ready to start.

Note: I have no affiliation with Local or WPEngine, Inc., the company behind Local.
To download Local, you have to sign up using a work email, accept the [WP Engine Terms of Service](https://localwp.com/legal/terms-of-service/) and acknowledge the [Local Privacy Policy](https://localwp.com/legal/privacy-policy/).

### IDE, code editor, or text editor

Finally, you'll need a tool to write code.
You probably already have a favorite Integrated Development Environment (IDE) or a favorite code editor: if so, stick to it.
If not, even the default text editor of your operating system will do the work.
A tool created specifically to write code is probably the best solution, but you should use what you know, as you won't have time to get familiar with something new during the workshop.

Many IDEs and code editors have Git and GitHub integrations or extensions: each of them is different, and, as such, I won't use them during the workshop.
Once you learn the basics of how Git and GitHub work, you'll be able to explore them on your own later and get the most out of them.

## Configuration

Now that you installed all the required software, you have to go through a few extra configuration steps so that all software will work as expected.

### Git

You not only have to install Git on your system, but you also have to set up your Git environment.
You should do this only once on any given computer, as Git keeps settings between upgrades (at worst, you can also change them anytime by re-running the commands below).

First, you should configure your identity by setting your username and email address, as Git adds them to every commit you create.
Open the terminal and type the following commands.

```
git config --global user.name "[your username]"
```
Insert your username in the command above: you can use your proper name, a username, or whatever identifier you'd like.
If your username contains spaces, remember to add double quotes before and after it.

```
git config --global user.email [your email address]
```
Insert your email in the command above.
If you'd like to keep your email address private, you can use the no-reply email address from GitHub (in the form of `ID`+`username`@users.noreply.github.com, where `ID` is a seven-digit ID number and `username` is your username). Once you have created a GitHub account (more on this in the next section), you can find it in the [emails settings of your account](https://github.com/settings/emails).

Once you set up your identity, you have to configure the text editor opened by Git when it needs you to type a message.
Choose your favorite text editor, look for it in the list available in the ["git config core.editor commands" section in Appendix C of the Pro Git book](https://git-scm.com/book/en/v2/Appendix-C%3A-Git-Commands-Setup-and-Config#ch_core_editor), and type the corresponding command in the terminal.
If you don't do this, Git might decide to opt for an unusual text editor (such as Vim) for you: unless you are familiar with it, please don't choose Vim, as it'll be hard to close once you open it.

Finally, set the default branch name to `main` using the following command.
```
git config --global init.defaultBranch main
```

### GitHub

GitHub is an online service, so you have to create an account before using it.
Head to the [GitHub homepage](https://github.com/) to sign up: enter your email, create a password, and enter a username.
Then, choose if you want to receive product updates and announcements via email and verify that you're not a robot.
That's it: now, you have a GitHub account.
You only have to check your inbox for the verification email needed to secure your newly created GitHub account and allow you access to all of GitHub's features.

You can find more details about [getting started with your GitHub account](https://docs.github.com/en/get-started/onboarding/getting-started-with-your-github-account) in their documentation.

Note: I have no affiliation with GitHub. By creating a GitHub account, you agree to their [Terms of Service](https://github.com/site/terms).
For more information about GitHub's privacy practices, see the [GitHub Privacy Statement](https://github.com/site/privacy).

## Previous knowledge

Once you have prepared your computer, it's time for you to get ready!
There are a few topics you should know about to get the most out of the workshop: here they are!

### Command line

You can use Git through both a Command-Line Interface (CLI) and a Graphical User Interface (GUI): during the workshop, you'll be working mainly with the command line.
If you're a Linux or Unix user, you're probably familiar with it; if you are a macOS or a Windows user, maybe not.

To make things more complicated, you should know that some commands are the same across different command lines and operating systems, but others are not.

If you are a Linux, Unix, or macOS user, your native terminal should accept all commands that you will use during the workshop.
If you are a Windows user, you don't have to worry either: when installing Git for Windows, you'll also get a Bash emulation, where you'll be able to use all Git commands as if you were in a Linux or Unix environment.

If you're not familiar with using a terminal (or need to refresh your knowledge), you can find a [command line for beginners tutorial](https://ubuntu.com/tutorials/command-line-for-beginners) on the Ubuntu website.

To follow the workshop effectively, you should understand the concept of working directory and how to change it, and how to create, move, and manipulate folders and files.
It is the content of sections 3, 4, and 5 of the tutorial above: it should take you only about 30 minutes to learn all the basic commands.

### WordPress themes

The workshop is about Git and GitHub for theme development, so you need to know how a WordPress theme works under the hood.
If you need a refresher, you can check the [page about theme development in the WordPress Codex](https://codex.wordpress.org/Theme_Development).
More information is available in the [WordPress Theme Developer Handbook](https://developer.wordpress.org/themes/).
You should only be familiar with classic themes, but you should know about child themes (you can find all information on the [related page in the WordPress Theme Developer Handbook](https://developer.wordpress.org/themes/advanced-topics/child-themes/)).
There won't be time to work with block themes during the workshop, but I'm preparing a bonus exercise where you will experiment with more advanced Git topics using a Full Site Editing theme.

### HTML, CSS, and PHP

Some basic knowledge of HTML, CSS, and PHP might help you understand the code used, but you can also copy-paste all code snippets needed for the workshop without knowing their meaning, so don't worry too much about this.
