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

0. If others have made changes to master