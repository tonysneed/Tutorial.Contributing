# Contributing Tutorial

Tutorial on how to contribute to a GitHub repository with a pull request

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
        git clone https://github.com/hilticandidate/Tutorial.Contributing.git
        ```

   - Change to the repository folder.

        ```
        cd Tutorial.Contributing
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

        ```git commit -m "Update ReadMe"

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

9. If it is likely others have made changes to the original repo, you should pull down their commits and rebase your own commits on top of them.
   - List the current configured remote repository for your fork.

    ```
    git remote -v
    ```

    > Note that `origin` should point to your forked repo:

    ```
    > origin https://github.com/hilticandidate/Tutorial.Contributing.git (fetch)
    > origin https://github.com/hilticandidate/Tutorial.Contributing.git (push)
    ```

    - Specify a new remote `upstream` repository that will be synced with the fork.

    ```
    git remote add upstream https://github.com/tonysneed/Tutorial.Contributing.git
    ```

    > Note that `upstream` is the clone URL from the  repository you *originally* forked.

    - Verify the new upstream repository you've specified for your fork.

    ```
    git remote -v
    ```

    > The output now includes both `origin` and `upstream`:

    ```
    > origin https://github.com/hilticandidate/Tutorial.Contributing.git (fetch)
    > origin https://github.com/hilticandidate/Tutorial.Contributing.git (push)
    > upstream https://github.com/tonysneed/Tutorial.Contributing.git (fetch)
    > upstream https://github.com/tonysneed/Tutorial.Contributing.git (push)
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

    - Lastly rebase your commits on top of those pulled from `upstream/master`.

    ```
    git checkout my-new-feature
    git rebase master
    ```

    - If there are any conflicts, you will need to resolve them. In Visual Studio Code you can select `Accept Current Change`, `Accept Incoming Change`, `Accept Incoming Change`, `Accept Both Changes`, or `Compare Changes`.

    <img width="1076" alt="resolve-conflicts" src="https://user-images.githubusercontent.com/2836367/69071545-ba8f2b00-09ef-11ea-8847-b04cfb25614a.png">

    - Then save the file, stage changes and continue rebase.

    ```
    git add .
    git rebase --continue
    ```

    - Lastly, because rebase re-writes history, you need to **force push** your feature branch to bring your pull request up-to-date with changes from other users.

    ```
    git push --force
    ```

10. After making other requested changes, you can clean up your history by using **interactive rebase** to squash multiple commits into a single commit, then force push again.
    - When reviewers are satisfied, they will merge your pull request into the original repo's master branch.
    - Then you can switch to master, pull changes, and delete your local feature branch.

    ```
    git checkout master
    git fetch upstream
    git merge upstream/master
    git branch -d my-new-feature
    ```


