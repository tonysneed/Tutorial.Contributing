# Contributing Tutorial

Tutorial on how to contribute to a GitHub repository with a pull request

> The idea behind creating a pull request is to propose changes to a repository that is _owned by someone else_. The contribution is made using a **fork** of the owner's repository. A fork is simply a _copy_ of their repository that resides in your own GitHub account. So instead of cloing the owner's respository, you **clone your fork**, or copy, of the owner's respository.

> After cloning your forked repository, you need to create a local feature branch, commit changes, then **push the feature branch** to your own forked repository. After pushing the branch, you will create a **pull request**, where you will have a conversation with the owner of the target repository. If changes are requested by the owner, you will commit those changes on your local feature branch and then push them.

> Optionally, you can ammend commits, or you can consolidate commits by squashing them into a single commit using **interactive rebase**. In both these cases, you will need to **force push** your changes to your remote feature branch.

> Once the owneris satisfied with your changes and approves your pull request, the _owner_ will **merge** your pull request into the master branch on their repository.  If you have no more contributions to make, _you don't need to do anything more_.

> If you plan to make another contribution, or your original pull request is open for a long time, you will need to **sync** the master branch of your forked repository with the owner's repository by adding an **upstream** remote that points to the owner's repository. Lastly, you can **rebase** changes in a long-lived pull request or feature branch, so that they appear after upstream commits. Again, because you are re-writing history, you will need to **force push** your feature branch, and these will appear in your pull request.

1. Fork the repository you wish to contribute to.
   - Log into github.com.
   - Locate the repository you wish to contribute to.
   - Click the **Fork** button.

    <img width="1101" alt="fork-repo" src="https://user-images.githubusercontent.com/2836367/69062043-f1f5db80-09df-11ea-8d98-344eec442ad5.png">

2. Clone the forked repository.
   - Copy the clone URL of your forked repository.

    <img width="1081" alt="clone-fork" src="https://user-images.githubusercontent.com/2836367/69062506-a68ffd00-09e0-11ea-931f-cf271444fec1.png">

   - Open a terminal and enter the `git clone` command.

        ```
        git clone https://github.com/yourusername/TheGitHubRepo.git
        ```

   - Change to the repository folder.

        ```
        cd TheGitHubRepo
        ```

3. Create a feature branch.

    ```
    git checkout -b my-new-feature
    ```

4. Open the project with a code editor.

    ```
    code .
    ```

    - Change or add files.
    - Stage your changes.

        ```
        git add .
        ```

    - Commit your changes

        ```
        git commit -m "Update ReadMe"
        ```

5. Push your feature branch.
   - Enter username and password when prompted.

        ```
        git push -u origin my-new-feature
        ```

6. Click **Compare & pull request** for your pushed feature branch.

    <img width="1113" alt="compare-pull-request" src="https://user-images.githubusercontent.com/2836367/69063915-ed7ef200-09e2-11ea-924e-21b171f1a584.png">

    - Add description and click **Create pull request**.

    <img width="1064" alt="create-pull-request" src="https://user-images.githubusercontent.com/2836367/69064115-477fb780-09e3-11ea-951e-7658581b6fd9.png">

7. At this point reviewers may comment on your changes.

    <img width="1067" alt="add-comment" src="https://user-images.githubusercontent.com/2836367/69064639-19e73e00-09e4-11ea-89c9-5a48cbf624de.png">

8. Make requested changes, commit them and push your feature branch.

    ```
    git add .
    git commit -m "Make a more descriptive addition"
    git push
    ```

    > **Note**: Once the owner of the repository has reviewed and approved your changes, _there is nothing else you need to do_. The owner will then merge your pull request into the master branch of their repository.

9. Whenever changes are made to the `master` branch of the **owner's** repository, you will need to sync it with the `master` branch of your **forked** repository.
    - This will be the case when the owner merges your pull request, and also when the owner merges other pull requests into the master branch of the owner's repository.
    - Start by listing the remotes for your local forked repository.

    ```
    git remote -v
    ```

    > **Note**: `origin` should point to your forked repository. If it does not, make sure you have followed Step 2 correctly by cloning your **fork** of the owner's repository, not the owner's repository itself.

    ```
    > origin https://github.com/yourusername/TheGitHubRepo.git (fetch)
    > origin https://github.com/yourusername/TheGitHubRepo.git (push)
    ```

    - Specify a new remote `upstream` repository that will be synced with the fork.

    ```
    git remote add upstream https://github.com/theirusername/TheGitHubRepo.git
    ```

    > Note that `upstream` is the clone URL from the **owner's** repository.

    - Verify the new upstream repository you've specified for your fork.

    ```
    git remote -v
    ```

    > The output now includes both `origin` and `upstream`:

    ```
    > origin https://github.com/yourusername/TheGitHubRepo.git (fetch)
    > origin https://github.com/yourusername/TheGitHubRepo.git (push)
    > upstream https://github.com/theirusername/TheGitHubRepo.git (fetch)
    > upstream https://github.com/theirusername/TheGitHubRepo.git (push)
    ```

    - Fetch the branches and their respective commits from the upstream repository.

    ```
    git fetch upstream
    ```

    - Commits to master will be stored in a local branch `upstream/master`.
    - Merge the changes from `upstream/master` into your local `master` branch.

    ```
    git checkout master
    git merge upstream/master
    ```

    > **Note**: If your pull request has been merged, there is _nothing else you need to do_. You can create a new feature branch and pull request if you wish to make another contribution to the owner's repository.

10. If your original pull request has not yet been merged, you bring changes from other users into your local feature branch.
    - After performing Step 9, you can **rebase** commits in your feature branch on top of those pulled from `upstream/master`. This has the effect of placing your commits _after_ those from other users.

    ```
    git checkout my-new-feature
    git rebase master
    ```

    - If there are any conflicts, you will need to resolve them. Using [Visual Studio Code](https://code.visualstudio.com), you can select `Accept Current Change`, `Accept Incoming Change`, `Accept Incoming Change`, `Accept Both Changes`, or `Compare Changes`.

    <img width="1076" alt="resolve-conflicts" src="https://user-images.githubusercontent.com/2836367/69071545-ba8f2b00-09ef-11ea-8847-b04cfb25614a.png">

    - Once you resolve conflicts in a file, make sure to **save** the file. Then **stage** changes and **continue** rebase.

    ```
    git add .
    git rebase --continue
    ```

    - Lastly, because rebase re-writes history, you need to **force push** your feature branch in order to bring your pull request up-to-date with changes from other users.

    ```
    git push --force
    ```

11. After making other requested changes, you can clean up your history by using **interactive rebase** to squash multiple commits into a single commit, then force push again.
    - Follow these instructions: http://gitready.com/advanced/2009/02/10/squashing-commits-with-rebase.html

12. When reviewers are satisfied, they will merge your pull request into the original repo's master branch.
    - Then you can switch to master, pull changes, and delete your local feature branch.

    ```
    git checkout master
    git fetch upstream
    git merge upstream/master # Update in original repo
    git branch -d my-new-feature # Change by fork.
    ```
