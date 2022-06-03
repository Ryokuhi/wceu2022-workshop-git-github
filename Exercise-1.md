# Exercise 1

In this exercise, you'll learn to use Git and GitHub by creating a child theme to the Twenty Twenty-One default theme.

There are six parts, and each builds on what you did before.
1. In the first part, you'll create a local repository, add the style.css file, and commit it.
2. In the second part, you'll edit the style.css and commit the changes.
3. Next, you'll create a branch to load the parent theme's styles, make the needed changes, and merge the newly created branch with the original one.
4. After that, you'll create a remote repository on GitHub and push your local changes to the remote repository.
5. You'll continue by editing the style.css file remotely and then pulling these changes.
6. Finally, we'll have a look at the commit history both locally and remotely.

You can try and do the exercise on your own, or you can follow along. If you get lost, are stuck, or don't know what to do, you should be able to find a way out.

If you need a list of all (and more) commands that you will use, you can find them in the [Git Cheat Sheets](https://training.github.com/) by Github: in the left column (the one with the "Using Git" header), you can find a list of cheat sheets in many different languages, available both online and as PDF to download.

## Part 1

Let's begin with creating a local repository, adding the `style.css` file, and committing it.

1.  In the `wp-content/themes` folder of your development environment, create a new folder for the theme. I'll name it `wceu-exercise-one`.
    ```
    mkdir wceu-exercise-one
    ```
2.  Enter the newly created folder.
    ```
    cd wceu-exercise-one
    ```
3.  Turn the current directory into a Git repository.
    ```
    git init
    ```
    This will create the hidden folder `.git` that contains all the information about the repository.
4.  When inside a Git repository, you can always check the current status of the repository.
    ```
    git status
    ```
5.  At the moment, your repository is empty. Let's create a `style.css` file with the following content.
    ```
    /*
    Theme Name: WCEU Exercise One
    */
    ```
6.  Since the `style.css` file didn't exist before, it isn't part of the Git repository and, as such, it's untracked, as you can check with `git status`.
    You can add it using `git add` followed by the name of the file.
    ```
    git add style.css
    ```
7.  The `style.css` file is staged, now you can commit it.
    The `git commit` command alone will open your default text editor, where you can write your commit message.
    This is especially useful when you commit complex changes which need both a subject and a description.
    If you can describe the changes using only a summary (i.e. using less than 50 characters),
    you can use the `-m` option to write the commit message directly from the command line.
    In this case, as this is the initial commit, I would use the following command.
    ```
    git commit -m "Initial commit"
    ```
8.  If you type `git status` now, you'll see that the working tree is clean, as you have committed all files.

## Part 2

We want the theme to be the child theme of the Twenty Twenty-One default theme, so you have to add it as the parent theme.

1.  Edit the `style.css` file: it should look as follows (you only have to add the second header).
    ```
    /*
    Theme Name: WCEU Exercise One
    Template: twentytwentyone
    */
    ```
2.  The `style.css` file is still tracked, but now there are uncommitted changes, so its status is now modified.
    Let's prepare the changes for commit using, as before, the `git add` command.
    ```
    git add style.css
    ```
    * The `style.css file is now staged, so let's commit it using `git commit`.
    ```
    git commit -m "Make the theme a child of Twenty TwentyOne"
    ```
3.  Now, you have a theme that can be activated in the WordPress backend.

## Part 3

Until now, the changes you made were little and easy to follow, but sometimes you make big changes that require a lot of work (and time).
In such cases, having the possibility to work on different features becomes very important.
Here is where Git branches come into help.
Git branches are pointers to single commits that allow you to quickly retrieve the status of the repository at a certain point in time.
Let's see how you can use them.

1.  Once more, use the `git status` command.
    You'll see that the first information printed on the screen is the name of the current branch.
    Common names are `main`, `trunk`, or `master` (avoid the last one please!).
2.  First, let's make sure that the name of your current branch is `main` using the following command.
    ```
    git branch -M main
    ```
3.  We not only want to enqueue the templates from the parent theme but also the styles.
    To do so, let's create a new branch to do this and switch to it. The command to switch to another branch is `git checkout`;
    you can use this command to create a new branch by using the `-b` option followed by the name of the branch you want to create.
    ```
    git checkout -b enqueue-parent-styles
    ```
4.  You are now on the `enqueue-parent-styles` branch: all changes made here are independent of changes made to the `main` branch (or any other branch).
    Let's enqueue the parent theme's styles: create a `functions.php` file inside the child theme folder with the following content.
    ```
    <?php
    function wceu_exercise_one_scripts() {
        wp_enqueue_style(
            'wceu-exercise-one-style',
            get_stylesheet_uri(),
            array( 'twenty-twenty-one-style' )
        );
    }
    add_action( 'wp_enqueue_scripts', 'wceu_exercise_one_scripts' );
    ```
5.  It's time to add and commit the `functions.php` file. A nice commit message might be "Enqueue parent styles".
    ```
    git add functions.php
    git commit -m "Enqueue parent styles"
    ```
6.  Now that you made changes to the `enqueue-parent-styles` branch, you want to port these changes to the `main` branch.
    To do so, let's first switch back to the `main` branch.
    ```
    git checkout main
    ```
7.  It's time to merge the `enqueue-parents-styles` branch back into the `main` branch.
    As you are on the `main` branch, you can use the `git merge` with the name of the branch you want to merge.
    ```
    git merge enqueue-parent-styles
    ```
8. The `main` branch is now the same as the `enqueue-parent-styles`, so you can delete the `enqueue-parent-styles` branch.
    ```
    git branch -d enqueue-parent-styles
    ```
9.  At this point, if you visit your local WordPress testing environment, you will see that the content of the website is displayed just as if Twenty Twenty-One was the active theme.


## Part 4

It's now time to "share" your repository by pushing in on a shared server, which in this case is GitHub.

1.  First, head to the [GitHub homepage](https://github.com) and log in case you haven't already.

2.  In the upper-right corner of the page, use the **plus symbol** drop-down menu, and select **New repository**.

    ![Drop-down with the option to create a new repository](https://docs.github.com/assets/cb-11427/images/help/repository/repo-create.png)

3.  Type a name for your repository. The best option is to match the name of the theme directory (i.e. "wceu-exercise-one").

    ![Field for entering a repository name](https://docs.github.com/assets/cb-25139/images/help/repository/create-repository-name.png)

4.  Choose repository visibility. You can go with either "Public" or "Private".

    ![Radio buttons to select repository visibility](https://docs.github.com/assets/cb-20877/images/help/repository/create-repository-public-private.png)

5.  Click **Create repository**.

    ![Button to create repository](https://docs.github.com/assets/cb-19887/images/help/repository/create-repository-button.png)

6.  Now you have a new remote repository, that can be accessed at the address shown at top of the page.
    It will be something like `https://github.com/your_username/wceu-exercise-one.git`
    It's time to link the local repository on your computer to the remote one on GitHub.
    To do so, head to the command line and type the following command
    (remember to change `https://github.com/your_username/wceu-exercise-one.git` with the actual address of your repository).
    ```
    git remote add origin https://github.com/your_username/wceu-exercise-one.git
    ```

7.  Finally, you can synchronize the remote repository with your local repository by pushing changes to the remote repository.
    The `-u` option allows you to automatically link the local branch with the remote branch.
    This will make you save time in the future when you have to push and pull changes to and from the remote repository.
    ```
    git push -u origin main
    ```

8.  Now, if you visit `https://github.com/your_username/wceu-exercise-one`, you will see all files in your repository nicely and easily displayed.

## Step 5

Now, let's make a small change directly on GitHub and pull it from the remote repository to the local one.

1.  Click on the **`style.css`** file in your remote GitHub repository.

2.  Next, click the **edit icon** (the one with the pencil shape) to edit the file.

3.  On the **Edit file** tab, add the following lines at the bottom of the file.
    This will make the entry title of each post stand a bit more, by changing the background color and rounding the border.
    ```
    .entry-title {
        background-color: #65a48d;
        border-radius: 3px;
    }
    ```

4.  In the Commit changes box, write a commit message that describes your changes (for example, "Change entry-title class").

5.  Click **Commit changes**. This will commit changes directly to the `main` branch (the alternative is to create a new branch and open a Pull Request).

    ![Commit example](https://docs.github.com/assets/cb-75044/images/help/repository/first-commit.png)

6.  The changes you made are now saved in the remote repository, but we want to check them out in our local testing environment.
    To do so, we have to pull changes made in the remote repository.
    If you used the `-u` option with the `git push` command before, you know only have to type the following command.
    ```
    git pull
    ```

7. You can now check that the change made on GitHub is also available in your local testing environment.

## Part 6

Before we end, we can have a look back to what we have done by checking the commit history both locally and remotely.

1.  First, head once more to the command line to list the version history of the current branch.
    You can use the following command.
    ```
    git log
    ```
2.  You can also navigate directly to the commits page of your remote repository on GitHub, clicking on the **history icon** (the one with the clock with arrow around shape).
